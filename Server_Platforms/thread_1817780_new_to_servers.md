---
title: "new to servers"
date: 2011-08-03
forum: Server Platforms
---

### Post by moorjam on 2011-08-03
Hello everyone,

Im quite new to the world of servers and still trying to learn the basics. Anyways, I got a free server that's power supply blew the seconded i turned it on and im curious to know what on the HDD's.

I was wondering if you can take HDD's from say server 1 and put them in server 2 to find out whats on them? Or maybe even run server 2 off of the HDD's from server 1?

Thanks

---

### Post by bakegoodz on 2011-08-04
If you have done just a simple one drive setup, it is pretty easy to move the drive to another system. You just put the drive in the system and it works. One problem I have run into is that the network interface in the second system will be assigned eth1 instead of eth0. It's usually not a problem if you not using a static IP address. The interface numbering can be fixed up in /etc/udev/rules.d/70-persistent-net.rules file were it assigns interface number to network interface hardware address (MAC addresss)

---

### Post by WhiteHorse on 2011-08-04
No, the drive will refuse to load the foreign data onto a local array.

---

