---
title: "Help please with setting up a domain name on my 6.06 lamp server"
date: 2008-04-26
forum: Server Platforms
---

### Post by ianb72 on 2008-04-26
Hi
Can anyone tell me what I have to do to add a domain name to my server?

I know I have to dyndns as I have a dynamic ip address, but I am not sure how I configure my server for my domain name, lets say its mysite.me.uk

The system I have running is a 6.06 Lamp Server with Webmin,phpmyadmin and proftd, I have not set up an email as of yet.

Also do I need to install SSH??

Many thanks
Ian

---

### Post by cdtech on 2008-04-28
This is how I set mine.
**Adding a hostname:**
```
hostname server.name.name.com (I'm also running dyndns (hense the name.name.com))
```

**SSH:**
If you want to securely connect to your machine from a remote computer.
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

I use putty from a remote windows computer and slogin from my Ubuntu box using ssh.

I also use dyndns as my domain (name.name.com) so my server is "server.name.name.com".

I can log into my server with (command line) slogin [email]user@name.name.com[/email] to log in as a selected user. From putty, I login to name.name.com using ssh port 22.

---

