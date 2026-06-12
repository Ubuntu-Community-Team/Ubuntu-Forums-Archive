---
title: "Safe to install Print Server to LAMP on 10.04.1"
date: 2011-01-20
forum: Server Platforms
---

### Post by TheGreatBunghole on 2011-01-20
Hello, I need to first point out that I am a complete n00b when it comes to Ubuntu Server, and I managed to install Ubuntu Server 10.04.1 (on a screen-less Acer Aspire 5100 laptop) with Apache2, MySQL, OpenSSH, & PHP5... I currently have this server (hosting my website) behind a linksys router with only port 22, and 80 forwarded to its ip address. Now my question is: Would it be safe to configure a print server on the same machine in order to print from the 3 other computers on my router to one printer, or are there security risks involved (like what I have heard with LAMP servers and Samba on the same machine)? I am also wondering if it is safe the way I configured port 80 & 22?   It has extremely long passwords, and I also went through the secure installation of one of the programs setting a root password too...   But can somebody please help me with my server? I am very surprised I have gone this far in my first 2 weeks of my Web Scripting class too! haha

---

### Post by Jive Turkey on 2011-01-20
I don't see a big problem with running a print server on there.  There is always a (small) possibility of getting your ssh password cracked but that has nothing to do with your print server.  I wouldn't recommend using this setup for production use but you could certainly use it for learning/testing/development and if you want to put up a live site get a real web host i.e. a shared hosting solution or a VPS.

---

