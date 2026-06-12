---
title: "Is same to install gnome in Ubuntu Server?"
date: 2009-03-07
forum: Server Platforms
---

### Post by MicroBoy on 2009-03-07
**I want to start my own webserver from ubuntu server. I saw here that I can install gnome in my server, would it be the same thing like without gnome, or with gnome the server would be slowly?**

---

### Post by hictio on 2009-03-07
I think I can re-ask you, do you really need Ubuntu Server? :)
That is, are you going to use your Ubuntu box more as a server -with Apache specifically-, or as a desktop with Gnome?

The reason I ask you its because enabling an Apache webserver on a Ubuntu Desktop install is really easy: 

. [How do I serve websites from my desktop?](http://swiss.ubuntuforums.org/showthread.php?p=6374829)
. [Simple Web Server on PC](http://ubuntuforums.org/showpost.php?p=6327257&postcount=6)
. [Apache + MySQL + PHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by MicroBoy on 2009-03-10
> **hictio said:**
> I think I can re-ask you, do you really need Ubuntu Server? :)
That is, are you going to use your Ubuntu box more as a server -with Apache specifically-, or as a desktop with Gnome?

The reason I ask you its because enabling an Apache webserver on a Ubuntu Desktop install is really easy: 

. [How do I serve websites from my desktop?](http://swiss.ubuntuforums.org/showthread.php?p=6374829)
. [Simple Web Server on PC](http://ubuntuforums.org/showpost.php?p=6327257&postcount=6)
. [Apache + MySQL + PHP](https://help.ubuntu.com/community/ApacheMySQLPHP)I need to use more as a server with apache, but I think that is to hard to work without Gnome? But I want to know if my server will be more efective, and faster without Gnome?

---

### Post by Simian Man on 2009-03-10
> **MicroBoy said:**
> I need to use more as a server with apache, but I think that is to hard to work without Gnome? But I want to know if my server will be more efective, and faster without Gnome?

Install Gnome but keep the init level set to 3.  This will only start a command line vt when you power on the machine.  If you need to run Gnome to do anything, type 'sudo gdm start' at the prompt.  Then, when you are done with Gnome, exit out to the command line.

Having Gnome won't hurt performance when it isn't running.

---

### Post by cariboo on 2009-03-10
Seeing as this question is asked over and over again. @netztier has provided a link that should answer your [questions]("http:///help.ubuntu.com/community/ServerGUI").

Jim

---

### Post by MicroBoy on 2009-03-11
**Thnx to all, you we're very heplfull.**

---

### Post by internalkernel on 2009-03-11
This is probably a little late to the game... but, I had a similar problem. I have a VPS that I do not have physical access to, most things can be accomplished via the comman line. However, Funambol proved to be a little difficult. My solution was:

```
apt-get install fluxbox
apt-get install tightvncserver
```

set your tightvnc password, then start tightvncserver. It will launch on desktop :1, so in order to get a graphical interface:

```
vnc my.server.com:1
```

I prefer this method as it is really lightweight in resources... I end up using maybe 15megs of RAM between vnc and fluxbox.

---

