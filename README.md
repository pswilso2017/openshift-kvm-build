# openshift-kvm-build
My journey to create a openshift cluster under KVM

This is my attempt to add additonal info to the work done by Felipe Miranda (ocpkvmdocument.pdf) contained within the added ocpkvmdocument for those not as experienced with Linux.


Following Felipe's document a few things that tripped me up.

1.  On page 8 number 3.  <virsh net-create macvtap.xml> should be <virsh net-define macvtap.xml>

2.  In creating my bastion I ran into a lot of problems using the command lines.  I believe SELiunux or some other
    permissions were tripping me up.  After creating the macvtap interface on the KVM host, I used the cockpit web interface to create a guest with the rhel83.iso mounted without starting.  Removed the default network interface and replaced it with the macvtap interface and proceeded.

3.  I needed to spend a good amount of time understanding how to configure a forwarding DNS to properly set up for page 12.
    I found a lot of good links and used this one the most:  https://www.linuxtechi.com/setup-bind-server-centos-8-rhel-8/ 

4.  When enabling the httpd server for the bastion I ran into a port problem for port 443.  I changed the 
    /etc/httpd/conf.d/ssl.conf file to have the standard https port to be 4443.

5.  On page 18 I added the --log-level=debug parameter to the openshift-install just because I wanted to see more of what was
    going on.

6.  I need to add an EXPORT to make the openshift client work properly for my install. I found this in the openshift 
    export KUBECONFIG=<installation_directory>/auth/kubeconfig


    