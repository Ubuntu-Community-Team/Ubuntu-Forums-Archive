---
title: "ubuntu 14.04 server: Problem with libvirt and public bridges."
date: 2014-08-06
forum: Virtualisation
---

### Post by Kais3rvlc on 2014-08-06
Hi all,

First at all, excuse if this is not the right place for posting this.
I'm using ubuntu 14.04 server edition and i'm trying to deploy some virtual machines in a server in such a way that they are visible in the same network that the host machine.

The tools I'm using are the uvtool package and libvirt.
The error I'm getting is the following:
"uvt-kvm: error: libvirt domain 'newtest' has no NIC MACs available."

Here I'm providing the quickest way (I think) of reproducing my problem. The steps to follow would be:

1) Creating a bridge. This is my /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto em1
iface em1 inet manual

auto br0
iface br0 inet static
  address 9.109.124.62
  network 9.109.124.0
  netmask 255.255.255.0
  broadcast 9.109.124.255
  gateway 9.109.124.1
#iface br0 inet dhcp
  bridge_ports em1
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0
  dns-search xx.xx.xx.xx
  dns-nameservers 192.168.122.1 9.0.146.50 9.0.148.50

 2) downloading a trusty tahr cloud image and run it
 uvt-simplestreams-libvirt sync release=precise arch=amd64
 uvt-kvm create test release=trusty
 
 3) duplicate the xml generated when running the machine in order to modify the network interface by the bridge one. In the XML I also remove the uuid and change the VM name.
 sudo mv /etc/libvirt/qemu/test.xml  /etc/libvirt/qemu/test2.xml
 In test 2 the most relevant change is replacing
 
    <interface type='network'>
      <mac address='52:54:00:86:7a:31'/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

by    
    <interface type='bridge'>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>

 4) Once I have my new XML, I define and start the new machine
  uvt-kvm destroy test
  virsh undefine test
  sudo virsh define  /etc/libvirt/qemu/test2.xml
  virsh start newtest  (newtest is the name provided in test2.xml)

 5) Up to this point everything seems to be fine, but if i run a wait command i get the error
  uvt-kvm wait newtest --insecure
  uvt-kvm: error: libvirt domain 'newtest' has no NIC MACs available.
 
 
I have checked the xml generated when defining newtest and there is a MAC in there, so it is not a problem generating a MAC address. Also the interface br0 is visible for virsh: 
 virsh iface-list
 Name                 State      MAC Address
---------------------------------------------------
 br0                  active     xx:xx:xx:xx:xx:xx
 lo                   active     00:00:00:00:00:00

 I have been googling for a while and couldn't find anything but this:
 [http://pastebin.com/em0hmy4t](http://pastebin.com/em0hmy4t)
 That tries something similar and falls in the same error.
 
 Any help will be very much appreciated!! Please, if you need me to provide any other info, tell me.
 
 Thanks!

---

### Post by TheFu on 2014-08-06
I use virt-manager from a remote desktop to manage my KVM/libvirt VMs - it supports ssh tunneling.

The only trick I know about this is being certain that my userid is part of the libvirtd group on the KVM server and ensuring the VM settings use the correct bridge. Besides that, it sorta "just works."

BTW, TL;DR  The bridge seems reasonable, though I don't use a few of the settings you did ... like "network".

---

### Post by Doug S on 2014-08-06
My Virtual computers get their IP address from my main LAN pool and are on that subnet.
My /etc/network/interfaces file:```
doug@s15:~/temp/dirk/cpuload3/cpuload$ [COLOR=#ff0000]cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Local network interface
auto eth1
iface eth1 inet static
  address 192.168.222.1
  network 192.168.222.0
  netmask 255.255.255.0
  broadcast 192.168.222.255

# The primary network interface and bridge
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
```And an example area from an .xml file:```
    <interface type='bridge'>
      <mac address='52:54:00:06:aa:8f'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
```

---

### Post by Kais3rvlc on 2014-08-07
I am gonna try and come back to you. However, i have the feeling that the problem is not with the bridge itself.

---

### Post by Kais3rvlc on 2014-08-07
No, it didn't work.
One possible reason for this failure is that the virtual NIC is not getting virtual MACS. That could be the reason for the "NIC MACs available"... however I don't know how to solve it yet.

The curious thing is that if i login into the VM (virsh console nameOfVM) and run ifconfig I see that the VM has a MAC, but it is not getting any IP.

---

### Post by TheFu on 2014-08-07
Perhaps this is a dumb question, but why not just set a static IP?

---

### Post by Kais3rvlc on 2014-08-07
It is not dumb at all :)

However the problem is that i need to be automatic because i have to be creating and destroying VM remotely and in an automated manner. Moreover, there are more machines in the network and I will need the ips to be assigned through dhcp, because i don't know which ips will be free or not at each moment :)

---

### Post by TheFu on 2014-08-07
Perhaps as a troubleshooting method then?  Does the static IP work?  DHCP issues may be completely outside the VM arena.

---

### Post by Kais3rvlc on 2014-08-08
OK guys, forget the problem. As i had feared at the very beginning, the problem had to be something stupid and not related to the bridge itself.
Someone told me the network this server was in was a dhcp network, but it is a static one.... so the main problem here was that the VM was not being associated to any valid ip because it was not getting any IP. Great 

So, if any of you had this error, check whether your network is a DHCP network or not.

---

### Post by TheFu on 2014-08-08
a) thanks for explaining the issue.
b) please mark the thread as solved so that others will look here and know to check like you did for DHCP.

---

