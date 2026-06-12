---
title: "Static Network Issue trying to move Hardy to a new VMWare Server hardware"
date: 2009-05-28
forum: Virtualisation
---

### Post by Sparkypine on 2009-05-28
I have two Win2k3 server boxes.  Each is running VMWare Server.  One VMWare server is hosting a Hardy guest install that is being used as our Joomla intranet site with a static IP bridge: 192.168.0.7 on eth0. 

Here's my ifconfig:

eth0 Link encap: Ethernet HWaddr 00:0c:29:f3:ec:13
inet addr:192.168.0.7 bcast:192.168.0.255 mask:255.255.255.0

Here's my CAT: 
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0 
gateway 192.168.0.61 

The other VMWare server is brand new and I want to migrate the existing intranet to a new hardware platform.  I thought all I would need to do is copy all the *.vmdk files to the new machine...which I did.  Everything works but now my network is set up as 192.168.0.177 on eth1 and mysql won't light up and thus Joomla won't work.  So I probably didn't do something simple...just not sure what.

Here's the ifconfig on the migrated instance on the new box:

eth1 Link encap:ethernet hwaddr 00:0c:29:7f:68:8f
inet addr:192.168.0.177 bcast:192.168.0.255 mask:255.255.255.0


The cat is exactly the same.

It's picking up a DHCP address on eth1 and using that, and the static eth0 is still there but I'm not quite sure how to make/force it to use the correct interface...which is why I'm suspecting mysqld fails to start.  I made sure the old vmware instance was off so there'd be no ip conflict but I bet that probably doesn't matter.

---

### Post by dcstar on 2009-05-31
> **Sparkypine said:**
> I have two Win2k3 server boxes.  Each is running VMWare Server.  One VMWare server is hosting a Hardy guest install that is being used as our Joomla intranet site with a static IP bridge: 192.168.0.7 on eth0. 

Here's my ifconfig:

**eth0** Link encap: Ethernet HWaddr 00:0c:29:f3:ec:13
inet addr:192.168.0.7 bcast:192.168.0.255 mask:255.255.255.0

Here's my CAT: 
auto lo
iface lo inet loopback

iface **eth0 **inet static
address 192.168.0.7
netmask 255.255.255.0 
gateway 192.168.0.61 

The other VMWare server is brand new and I want to migrate the existing intranet to a new hardware platform.  I thought all I would need to do is copy all the *.vmdk files to the new machine...which I did.  Everything works but now my network is set up as 192.168.0.177 on eth1 and mysql won't light up and thus Joomla won't work.  So I probably didn't do something simple...just not sure what.

Here's the ifconfig on the migrated instance on the new box:

**eth1** Link encap:ethernet hwaddr 00:0c:29:7f:68:8f
inet addr:192.168.0.177 bcast:192.168.0.255 mask:255.255.255.0


**The cat is exactly the same.**

It's picking up a DHCP address on eth1 and using that, and the static eth0 is still there but I'm not quite sure how to make/force it to use the correct interface...which is why I'm suspecting mysqld fails to start.  I made sure the old vmware instance was off so there'd be no ip conflict but I bet that probably doesn't matter.

So you have one system with eth0 set everywhere working and another with eth0 and eth1 mixed up and its not working? - I wonder why....

---

### Post by Sparkypine on 2009-06-01
David - 

If all I did was copy the vmdk files from one machine to another, and the VMWare setting are identical on both servers, how did that happen?  Or, more importantly, what would be your recommendation as a fix?

Thank you for your time.

---

### Post by Sparkypine on 2009-06-23
In case anyone else bumps into this and needs help:

All I had to do was run - 

**cat /etc/network/interfaces**

and determine what interface was trying to be used.  Then I ran - 

**sudo nano -w /etc/network/interfaces** 

and edited the interface to match what Ubuntu was using.  Rebooting got mysql and Joomla to fire back up and everything was fine.

Thanks for the "help," dcstar

---

