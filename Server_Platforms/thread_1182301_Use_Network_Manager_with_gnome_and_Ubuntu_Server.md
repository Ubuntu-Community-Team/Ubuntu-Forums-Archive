---
title: "Use Network Manager with gnome and Ubuntu Server"
date: 2009-06-08
forum: Server Platforms
---

### Post by werdna5225 on 2009-06-08
I recently installed Ubuntu Server 9.04 and then installed the gnome desktop manager on top.  Everything is working great except that I cannot enable the gnome/ubuntu network manager.  When I click on the icon on the menu, there are no networks showing up.  However, I do have internet access on the server.

Is there any way to enable the network manager to be the default networking program?

---

### Post by lensman3 on 2009-06-09
From a command prompt do: "/etc/init.d/network restart"

or "/sbin/ifdown eth0"

and then "/sbin/ifup eth0".  If you do this command across the network be sure the last two are written "sbin/ifdown eth0; /sbin/ifup eth0".  Note the semicolon.  It is possible and very likely that the network will go down and you will have to restart it on the command console. (It is impossible to send a command across a network when the network is down). 

Your request is confusing.  I hope I guessed right!

---

### Post by werdna5225 on 2009-06-09
Well that kind of worked.  The Network Manager now sees my wireless card and I can join a wireless network, but my wired Ethernet is still not being picked up by the Network Manager.

I'm sorry for making my first post so confusing.  What I am wanting to do is control both the wireless and wired Ethernet with the Network Manager that comes default with gnome.

---

### Post by cariboo on 2009-06-09
With 9.04 because of the way Network Manager works you can't use both interfaces at the same time. If you want to use both interfaces at the same time and you need a gui to do it, uninstall network-manager-gnome and install gnome-network-admin. You will only get a small connected bar graph in the notification area and to setup the network interfaces go to System-->Administration-->Network.

---

### Post by Iowan on 2009-06-10
> **cariboo907 said:**
> With 9.04 because of the way Network Manager works you can't use both interfaces at the same time. Thanks - I've been wondering if Jaunty's NM could handle wired/wireless concurrently.

---

### Post by cariboo on 2009-06-10
I've tried several times, and haven't been able to get it to work with Network Manager. I can do it using an iptables script, and I found I could do it using gnome-network-admin.

---

