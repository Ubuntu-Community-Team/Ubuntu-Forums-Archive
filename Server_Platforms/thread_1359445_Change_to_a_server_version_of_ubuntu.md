---
title: "Change to a server version of ubuntu"
date: 2009-12-19
forum: Server Platforms
---

### Post by olimones on 2009-12-19
Hello, I use ubuntu 9.10 and want to change to a server version. Can i do it without uninstalling my actual version? 


Using:
Ubuntu 9.10
HP dv7-2185dx
64 bits

thanks

---

### Post by Cheesemill on 2009-12-19
You can install any of the server packages - Apache, Bind, MySQL, etc. onto a standard desktop install.

---

### Post by olimones on 2009-12-19
Cheesimill,
Is there any list of server applications I should install? the things is that I work with Windo$ servers at work and want to start a lab with ubuntu server to see if I can implenet it litle by little and want to have all the advantages of it.

Thanks,

---

### Post by Cheesemill on 2009-12-19
This all depends on what functions you wish to implement.

For file and printer sharing you can use Samba.
For DNS you can use Bind.
For DHCP you can use dhcpd.

The main question is what are you trying to achieve?

---

### Post by olimones on 2009-12-19
I need to virtualise machines, store and share data, email server, and host the organisation's applications among other tipical administration services in the organisation.

Thanks,

---

### Post by Cheesemill on 2009-12-19
You should check out the Server links sticky:
[http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

For virtualization I use VMware Server.

For email I use this excellent how-to (it's for debian but I've used it successfully on Ubuntu):
[http://workaround.org/ispmail](http://workaround.org/ispmail)

Also most configuration of a Ubuntu server is done by editing text files, this is why the server edition doesn't come with a GUI, it's command line only by default.
If this sounds like too much work you can look into using something like Webmin which will give you a WebUI for alot of the standard server functions.

---

### Post by olimones on 2009-12-19
I will take a look at them.

Thanks,

---

