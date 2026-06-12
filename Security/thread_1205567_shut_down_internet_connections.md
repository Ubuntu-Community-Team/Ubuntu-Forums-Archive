---
title: "shut down internet connections"
date: 2009-07-06
forum: Security
---

### Post by marticc on 2009-07-06
Hello, I would like to ask a question:Is there any tool for Ubuntu that lets me shuto down an specific internet connection?

For example, I have the firestarter, and in the box where I can see the active connections, I see several connections to different IPs, and I want to close just one of them and I can't do that with the Firestarter (or at least I don't know how to do that with the firestarter). Is there a tool that lets me close that specific connection

And another question related to this one, I set the firestarter to block all the outbound connections except those ones related to http and https. is there a way  with this program (or with another one) to block all the outbound connections except those related to a specific program (ie Firefox, Opera...).

Thanks.

---

### Post by lovinglinux on 2009-07-06
> **marticc said:**
> Hello, I would like to ask a question:Is there any tool for Ubuntu that lets me shuto down an specific internet connection?

[iptstate](apt:iptstate) [apt-get] 

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

> **marticc said:**
> And another question related to this one, I set the firestarter to block all the outbound connections except those ones related to http and https. is there a way  with this program (or with another one) to block all the outbound connections except those related to a specific program (ie Firefox, Opera...).

[gufw](apt:gufw) [apt-get]

I guess gufw has this kind of implementation, but I'm not sure. Anyways, gufw is recommended over Firestater.

---

