---
title: "vmbuilder libvirt bridge networking"
date: 2009-01-24
forum: Server Platforms
---

### Post by thesheff17 on 2009-01-24
I want to get bridge networking to work with vmbuilder.  I have read and read and can't seem to find what is wrong with my setup.  Here is my /etc/network/interfaces file.  So I'm bridging eth0 to br0 no problem.  

auto br0
iface br0 inet static
       address 192.168.1.10
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.1.255
       gateway 192.168.1.2
       bridge_ports eth0
       bridge_fd 9
       bridge_hello 2
       bridge_maxage 12
       bridge_stp off 

Then I tell the default file to bridge /etc/vmbuilder/libvirt/libvirtxml.tmpl

<interface type='bridge'>
      <source bridge='br0'/>
    </interface>
 

When the virtual machine comes up I don't have an ip.  I try to redo the ip through DHCP and nothing.  I also assign it a static ip and unable to ping anything.  Any suggestions? :(

I also have been reading this document with no luck.

[http://doc.ubuntu.com/ubuntu/serverguide/C/jeos-and-vmbuilder.html](http://doc.ubuntu.com/ubuntu/serverguide/C/jeos-and-vmbuilder.html)

---

### Post by thesheff17 on 2009-05-07
I am no longer having this problem with ubuntu 8.10 and ubuntu 9.04.

auto eth0
iface eth0 inet manual
auto br0
iface br0 inet static
       address 192.168.x.x
       netmask 255.255.255.0
       network 192.168.X.0
       broadcast 192.168.X.255
       gateway 192.168.x.x
       bridge_ports eth0
       bridge_fd 9
       bridge_hello 2
       bridge_maxage 12
       bridge_stp off

---

