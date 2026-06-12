---
title: "Can't get to my cups admin page!"
date: 2006-02-26
forum: Server Platforms
---

### Post by fizgig on 2006-02-26
I keep getting the forbidden message when I browse to my servers cups page (192.168.1.234:631).  I am able to browse to the server's apache default page when I don't throw port 631 up there.  We're both on the same subnet with no routers or anything in between.

Here are the (I think) relavent sections of my /etc/cups/cupsd.conf file:

#User cupsys
#Group lpadmin
User lp
Group lp

Listen 127.0.0.1:631
Listen 192.168.1.234:631

#SystemGroup lpadmin
SystemGroup lp

<Location />
Order Deny,Allow
Deny From All
Allow From *
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From *
</Location>

---

### Post by Xian on 2006-02-26
[QUOTE=fizgig]I keep getting the forbidden message when I browse to my servers cups page....[/QUOTE]

You will most likely need to setup a root password.
$ sudo passwd root

---

### Post by fizgig on 2006-02-26
Still have the same error:

**Forbidden**

You don't have permission to access the resource on this server.

---

### Post by fizgig on 2006-02-26
I just removed the "Deny From All" from both sections, restarted cupsys and now I can browse to it.

---

### Post by Lunixfanboy on 2006-03-06
[QUOTE=fizgig]I just removed the "Deny From All" from both sections, restarted cupsys and now I can browse to it.[/QUOTE]Many thanks for that little tidbit. The Gnome System Admin menu left me using A4 sized paper REGARDLESS of the settings I entered, and so buggered up several print jobs. Your little bit allowed me to get to the Admin settings in CUPS and now I have letter size paper and the print is wonderful.

---

