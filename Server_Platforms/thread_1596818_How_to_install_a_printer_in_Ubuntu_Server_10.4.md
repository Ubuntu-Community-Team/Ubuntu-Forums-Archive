---
title: "How to install a printer in Ubuntu Server 10.4"
date: 2010-10-14
forum: Server Platforms
---

### Post by windows lover on 2010-10-14
I could really use some help here; How do I install a printer on Ubuntu server? I have a Cannon MP250 that i need to install so I have a print server but being as I am reluctantly new to Linux I am at a loss. Any help would be duly appreciated

---

### Post by arrrghhh on 2010-10-14
If the printer has a NIC, that would be the easiest method.

If not, you only have USB or LPT, then you'll have to plug the printer into your server & set it up with CUPS.  I know HP printers have pretty good Linux support, but I don't think Canon's do.  Good luck.

---

### Post by windows lover on 2010-10-14
I followed the steps for configuring cups that were in the Ubuntu documentation but something must be wrong as the web management page doesn't work, I've tried both the router i.p address and the i.p address that my computer are using but nothing works, I think i need to settle this before i do anything else.

---

### Post by arrrghhh on 2010-10-14
So what have you tried to troubleshoot...?

---

### Post by windows lover on 2010-10-14
ummm how?

---

### Post by arrrghhh on 2010-10-14
Ok, let's start over at square one.

Have you read [NetworkPrinting with Ubuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)?  It's an offical Ubuntu doc.

You may also want to peruse thru the [Server Guide](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Update - more links

[CUPS](https://help.ubuntu.com/10.04/serverguide/C/cups.html)

[Samba Print Server](https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html)

---

### Post by windows lover on 2010-10-17
Therein lies the problem i cannot access that website, regardless of the fact that I have followed the guide.

The "listen" section of the configuration file is as follows:

Listen localhost:631                      # this was set by default
Listen /var/run/cups/cups/cups.sock       # left as the default
Listen 192.168.0.8:631          # The i.p. address of this computer

Not certain what to do or if this is configured correctly, however, i can browse to printers folder on the server from my windows computers

---

### Post by windows lover on 2010-10-17
Ok now I've changed that default localhost:631 to MoweryHomeNetwork:631 but that didn't work either

---

### Post by windows lover on 2010-10-17
nothing works its this stupid Linux its the worst OS in the world they should just destroy everything Linux i give up i win

---

### Post by cariboo on 2010-10-17
The way cups is setup by default, you can only access it from the computer it is running on. If you are running a default install with no gui, install links and access the management page with it. Once you have accessed the page you can set it to accessed from any other system. See screenshot.

Remember to turn the option off, after you have finished, because if you leave it on, anyone can go in and make changes at any time.

---

### Post by arrrghhh on 2010-10-18
> **windows lover said:**
> nothing works its this stupid Linux its the worst OS in the world they should just destroy everything Linux i give up i win

Wow... Don't think you're going to get much help acting like this dude.

---

### Post by windows lover on 2010-10-18
Yes i apologize for that I was very frustrated when I wrote that and still frustrated, Linux is just so annoying especially using only the command line

---

### Post by arrrghhh on 2010-10-18
> **windows lover said:**
> Yes i apologize for that I was very frustrated when I wrote that and still frustrated, Linux is just so annoying especially using only the command line

Some prefer the command line - I personally do.  But I have always, ALWAYS been an advocate of 'use what works for you' - if you want a GUI, install ubuntu-desktop.  You can run ALL of the same services you can on ubuntu-server, and you have a friendly desktop environment to use.

I run a pretty paltry server, and to squeeze all of the performance out of it that I can, I try to only install what I need.  A GUI interface takes a lot out of a machine - all the updates, unnecessary processor overhead, etc.  It's all very overkill for my little file server.

Anyhoo, are you still trying to get this fixed?  We are here to help :D

---

