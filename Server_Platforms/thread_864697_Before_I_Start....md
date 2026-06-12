---
title: "Before I Start..."
date: 2008-07-19
forum: Server Platforms
---

### Post by gulliccj on 2008-07-19
Hello. I want to set up a home server. I am a Windows XP/Vista user, but i would like to use Ubuntu Server for the home server software. Is there a way to set up a basic home server, with multiple logins, and have the workstations use windows XP/vista? If at all possible, can this be done without reinstalling Windows XP? Thank you so much.

-Colin Gullickson

---

### Post by freebeer on 2008-07-20
I'm not exactly clear on what you're trying to achieve, but yes, Ubuntu can defintely act as a "back-end" server to Windows clients.  I have that set up here (at home) and have also set up such arrangements in offices.

You'll want to check into Samba (on the server) to allow Windows sharing.

---

### Post by cdtech on 2008-07-20
I use the Ubuntu LAMP Server which has all the bells and whistles for my home network. I share files, run a Web server and everything else. I use three other desktops running from Windows 2000 to Vista on my Network. In short, yes to what you want to do........

---

### Post by tinny on 2008-07-20
> **cdtech said:**
> I use the Ubuntu LAMP Server which has all the bells and whistles for my home network. I share files, run a Web server and everything else. I use three other desktops running from Windows 2000 to Vista on my Network. In short, yes to what you want to do........

A LAMP server is Linux, Apache (web server), MySQL (Data base) and PHP (or sometimes the other "P" programming languages).

I dont think that MySQL or PHP (and other P's) will really help a home server. (depends on what you want to do?) 

You might not even want Apache unless your hosting web pages.

Have a look in the Ubuntu server docs.

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Things you should look into are:

DHCP - Dynamic Host Configuration Protocol
SAMBA - File server
DNS - Domain Name Service
OpenSSH - Remote access
CUPS - Print server

Hope this is what you where after...

BTW: P's = Python, Perl, PHP

---

