---
title: "iRedMail-0.8.5 unable to connect to the database!"
date: 2013-08-16
forum: Server Platforms
---

### Post by George_IsintheComputer on 2013-08-16
I installed iRedMail-0.8.5 on my VPS but when I try to visit it, I get:

>   [h=3]DATABASE ERROR: CONNECTION FAILED![/h] Unable to connect to the database!
Please contact your server-administrator.
 
 


I went to /root/iRedMail-0.8.5/config

and I can see the logins to phpmyadmin are correct.

What can I do here?

---

### Post by nerdtron on 2013-08-16
Have you installed iRedMail in a FRESH install of ubuntu server 12.04? Also, please post to the iredmail forum [http://www.iredmail.org/forum/](http://www.iredmail.org/forum/) the main developers usually responds within a few hours for the free support.

---

### Post by George_IsintheComputer on 2013-08-17
No, I did not install it on a FRESH server. Is that a must?

---

### Post by nerdtron on 2013-08-18
> **George_IsintheComputer said:**
> No, I did not install it on a FRESH server. Is that a must?

It is very much recommended on the installation notes. Install it on a FRESH server install (you should only choose OpenSSH when you are in tasksel part of the installation) and let the iRedMail script install it's own components.

---

### Post by CharlesA on 2013-08-18
> **George_IsintheComputer said:**
> No, I did not install it on a FRESH server. Is that a must?

To expand a bit on what  nerdtron said, iRedMail assuming you are installing it on a fresh/clean install, so anything that you have installed previously has the potential for being broken.

I ended up doing it the "hard" way and just installing everything on my email server manually and configuring it and stuff, but I know these all-in-one packages can be quite handy when you don't have to time/feel like configuring everything from scratch.

---

