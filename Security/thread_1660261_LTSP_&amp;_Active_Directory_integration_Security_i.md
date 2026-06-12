---
title: "LTSP &amp; Active Directory integration: Security issues ?"
date: 2011-01-05
forum: Security
---

### Post by Herazio on 2011-01-05
Dear all

I've been experimenting with the LTSP project and just tried to implement Active Directory access to a Windows 2008 Server R2. This has been succesful to me however I am stuck with one question concerning security and that is the following:

We all know the problem with UID and SID or RID mapping, I have not been able to do this yet but due to this it's a lot harder to implement security on the server.

Suppose that I have a user at work who logs into the terminal server and gets his/her own home directory. The problem here is that the user can just browse around the whole filesystem including / and folders such as opt and etc. Now I am aware that a user should have read access and all but I'm just curious if this doesn't pose a threat seeing as a user can browse around the whole filesystem.

Now some of you might find this a stupid question but please don't get me wrong I'm merely a networking student and well, I've got to learn some way !

Also if this is the wrong forum I sincerely apoligize. Seeing as it's more security related I figured it should be posted here.

In any case I would like to thank all for your help and I hope to hear from you soon !

Regards

Herazio

---

### Post by Johann-1.0 on 2011-01-05
Hello. I'm looking for help too. Do you know a way to control the server with the terminal? I don't want the server to have a monitor, but I want to control it with the thin client. Can you help me with it? Thanks in advance.

---

### Post by Herazio on 2011-01-05
> **Johann-1.0 said:**
> Hello. I'm looking for help too. Do you know a way to control the server with the terminal? I don't want the server to have a monitor, but I want to control it with the thin client. Can you help me with it? Thanks in advance.

I possibly can. Normally if I'm not mistaken you can use Secure SHell to monitor your server remotely. I believe you can install an instance of openssh-server and configure it to work on a port which ISN'T port 22 seeing as port 22 is used for LTSP. I'd say use port 2200 or so if it's not in use ofcourse !

When you have installed it you can normally SSH into the server with 
***ssh -l <username> -p <port>*** [B]<ip Terminal Server>

[/B]I hope that this helps you a bit. I'm just trying here ^^

---

### Post by Johann-1.0 on 2011-01-05
> **Herazio said:**
> I possibly can. Normally if I'm not mistaken you can use Secure SHell to monitor your server remotely. I believe you can install an instance of openssh-server and configure it to work on a port which ISN'T port 22 seeing as port 22 is used for LTSP. I'd say use port 2200 or so if it's not in use ofcourse !

When you have installed it you can normally SSH into the server with 
***ssh -l <username> -p <port>*** [B]<ip Terminal Server>

[/B]I hope that this helps you a bit. I'm just trying here ^^
Thank you...I will try that solution maybe next week, when my computer come back again, lol.
The way you propose allows me to graphically control the server? I mean, I want the server to work like a normal desktop installation and the thin client to be its monitor. I hope you can understand me, because my english skill is not very good, lol.

---

### Post by cariboo on 2011-01-05
You can use X-forwarding with ssh the command would look like this:

```
ssh -X user@server
```

then once at the prompt just type the name of the application you want to run.

---

### Post by HermanAB on 2011-01-06
```
$ ssh -C -c blowfish -X user@server gnome-panel

```
then go click happy.

However, that assumes that all the graphical schtuff are actually installed on the server, which if you installed the Ubuntu server distro will not be.

If you really want a server with a graphical UI, install regular Ubuntu or OpenSuse.

---

### Post by Johann-1.0 on 2011-01-06
Thank you...I will try that the next week, when my computer returns to me, lol.

---

