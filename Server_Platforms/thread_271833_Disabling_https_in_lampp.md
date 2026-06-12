---
title: "Disabling https in lampp"
date: 2006-10-05
forum: Server Platforms
---

### Post by Keymaster on 2006-10-05
I use something called lampp.  (Xampp for Linux).  It automatically adds https to apache, and a bunch of other things as well.  If anyone if familiar with lampp, please help me!  I need to know how to disable the https in apache from lampp, because I am going to be using the https port (443) for an ssh server.  I am going to be using it for an ssh server for my own reason, and I know it makes little sense, but for me I need it that way. (Reason is private).  In lampp's apache config how could I disable ssl?  Thanks

---

### Post by Keymaster on 2006-10-15
Nevermind.  I figured out that I can simply type ```
/opt/lampp/lampp stopssl
``` to disable https

---

