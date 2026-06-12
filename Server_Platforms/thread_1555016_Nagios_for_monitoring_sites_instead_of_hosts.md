---
title: "Nagios for monitoring sites instead of hosts"
date: 2010-08-17
forum: Server Platforms
---

### Post by Mr_G on 2010-08-17
Hey,

I have installed nagios successfully, But I need it to monitor sites instead of servers.

So is there any shell script or open source php script I can use to add sites to the configuration file.

Thanks

---

### Post by arrrghhh on 2010-08-17
It's the same concept - just put in the hostname and IP of the site instead of the server hostname & IP...

---

### Post by Mr_G on 2010-08-19
> **arrrghhh said:**
> It's the same concept - just put in the hostname and IP of the site instead of the server hostname & IP...

I know, But that needs to be done manually, any script that can be used by other users ?

---

### Post by arrrghhh on 2010-08-19
Oh... well each environment is special, you'd probably be better just writing a script for your environment...

It's a hassle, but I've had to add all network devices to a network monitoring system more than once.  Somehow I have a feeling I'm not done either.

---

### Post by Mr_G on 2010-08-20
Thanks for helping out but I finally got ready made scripts

You can try it, it's based on PHP, MYSQL

[http://sourceforge.net/projects/nagiosweb/](http://sourceforge.net/projects/nagiosweb/)

---

### Post by arrrghhh on 2010-08-20
Oh you just wanted a pretty front-end?  Sorry.  I thought you wanted a custom script that would add all of your devices for you.

Glad you got something that works tho.  Please use the "Thread Tools" drop-down menu and mark this topic [SOLVED] if you think it is!

---

