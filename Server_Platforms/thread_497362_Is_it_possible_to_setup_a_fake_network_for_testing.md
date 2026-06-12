---
title: "Is it possible to setup a fake network for testing?"
date: 2007-07-10
forum: Server Platforms
---

### Post by Elijah on 2007-07-10
Hi, 

I would like to setup a thin-client network but with no test nodes to play around with... do you think it's possible to setup some sort of virtual network? :confused: will something like OS'es opened up with virtualbox work?

---

### Post by Maxtorm on 2007-07-10
I've never used Virtualbox, but I know you can certainly do this in VMWare.  Install the server in one virtual session and the client in the other.  When you're configuring networking, use bridged networking and just assign addresses to the virtual sessions that are not already in use on your network.  I believe you can also specifically configure the sessions with NAT or a private network range so that there is limited (or zero) impact on the "real" network interfaces.

---

### Post by rickyjones on 2007-07-10
> **Maxtorm said:**
> I've never used Virtualbox, but I know you can certainly do this in VMWare.  Install the server in one virtual session and the client in the other.  When you're configuring networking, use bridged networking and just assign addresses to the virtual sessions that are not already in use on your network.  I believe you can also specifically configure the sessions with NAT or a private network range so that there is limited (or zero) impact on the "real" network interfaces.

Quoted For Truth.

This is what I do all the time for testing things at home. Very simple and elegant. :)

-Richard

---

### Post by Elijah on 2007-07-13
Thanks , I will try that one. So far I've failed on virtualbox.. I guess I need to learn more about thin clients

---

