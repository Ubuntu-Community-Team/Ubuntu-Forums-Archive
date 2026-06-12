---
title: "Ubuntu Server As Proxy Trouble Recieving Mail Through Exchange"
date: 2008-03-09
forum: Server Platforms
---

### Post by cntpl89 on 2008-03-09
Hi, i have set up a Ubuntu Lamp Server, using squid / dansguardian / webmin.  It works well, but im now having issues recieving emails, either direct through outlook or through microsoft exchange server.

I have cleared all IPTables for now, i want to know if there is a way to create a 'tunnel'?

Or is there a simple way to 'unblock' certain ports?

I need access to pop3 smtp telnet (From internet to server) and rdc (From internet to server), none of which work at the moment.

Thanks for your help

---

### Post by cntpl89 on 2008-03-09
just thinking out loud...
for my email issue, would it be possible to setup maybe a "mail server" which fowards the emails onto exchange server and maybe do some scanning at the same time? or is it possible to set up some kind of vpn tunnel on port 110 etc which would point directly to the server???

---

### Post by twistedtwig on 2008-03-10
possibly daft question but does port 25 get forwarded to your windows box?

---

### Post by cntpl89 on 2008-03-10
> **twistedtwig said:**
> possibly daft question but does port 25 get forwarded to your windows box?

It's not a daft question, this is my first attempt of setting one of these up, i have recently added shorewall firewall to try and make some more sense of this all, how do i check if port 25 is fowarded? is there a method to trace route or something?:confused:

---

### Post by cntpl89 on 2008-03-12
anyone?

---

