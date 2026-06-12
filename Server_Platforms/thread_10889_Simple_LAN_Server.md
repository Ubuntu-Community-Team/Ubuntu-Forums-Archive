---
title: "Simple LAN Server"
date: 2005-01-12
forum: Server Platforms
---

### Post by richbayliss on 2005-01-12
Hi,

I am new to ubuntu, so stick with me.  :D 

I have a LAN server running at the moment, for sharing my net and serving as a file server for my network.

We have a 10 computer network, and we all use routers for our net, and just use our  own router for net access. All is fine and works.

But!!! My server is Windows 2003, and I want Linux.

So, my question is, How can I setup PPPoE in Ubuntu, to auto connect, and use NAT for my PC. Are there any wizards, tools etc to help??

If there isnt, maybe ill write one, if someone cant help me get the setup right first.

Thanks. 8)

---

### Post by kstrat on 2005-01-14
Hi, it is definitely possible to do with ubuntu, but I don't think that there are any wizards to do the work. 

This thread may help a bit:
[http://ubuntuforums.org/showthread.php?t=10131](http://ubuntuforums.org/showthread.php?t=10131) 
(ubuntu gateway howto) 
You would just need to figure out how to tell ubuntu to use pppoe for your network connection. 
To act as a LAN server (to share files, etc on the LAN), you need to use SAMBA.

Hope this helps.

Kevin

---

### Post by kstrat on 2005-01-14
Hi, 
I found that there is a utility called pppoeconf, you might give that a try.

Kevin

---

