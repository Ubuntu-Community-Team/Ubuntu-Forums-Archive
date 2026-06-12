---
title: "Create Ubuntu DNS Server into existing Windows Domain"
date: 2011-05-02
forum: Server Platforms
---

### Post by werdna5225 on 2011-05-02
I have an existing windows domain set up, Server 2008 R2.  My active directory server doubles as my DNS server.  I would like to add an Ubuntu DNS server to the domain.  

So far, I have installed the server and installed bind9, webmin, and a static IP.  However, I'm not sure where to go from there, I would really like to find a way for all of the information on my Windows server to replicate to my Ubuntu server.  Is that possible?

I am using Natty, but I have no problems going to an LTS.

---

### Post by koenn on 2011-05-02
look in your Microsoft DNS for a setting that says "allow zone transfers to ..." and allow zone transfers to your bind9 host. Configure bind9 as a "slave". 
That'll probably work. 

Also, ask yourself what you're trying to achieve with this setup. The 'how' usually follows from that

---

### Post by werdna5225 on 2011-05-03
Do I need to have and configure samba?  Do I need to have the Ubuntu server added to the domain?

---

### Post by koenn on 2011-05-03
theoretically, no, not for basic stuff like this.

---

