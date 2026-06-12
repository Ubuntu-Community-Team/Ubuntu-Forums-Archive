---
title: "stop dropping me into a shell!"
date: 2011-08-25
forum: Server Platforms
---

### Post by leppel on 2011-08-25
SO, I just downloaded ubuntu Server, and was super stoked to get it installed.

Once grub writes to the master boot record and notfies me to take the CD out of the drive and reboot, i do that. 

BUT: when it gets past the bios screen, i get this weird error: (dell error) 0 partitions. 
I hit enter, and it tries to boot me into my OS. 

It drops me into a shell. It starts all the services and boot messages through a shell, and then leaves me in it. 

It says Welcome to Ubuntu! Then asks me for my login credentials:

(take a guess where the hostname is from :P)

g3n3s1s login: 

---HOW DO I GET UBUNTU 11.04 SERVER TO BOOT INTO GUI, NOT COMMAND LINE!?!?

---

### Post by memilanuk on 2011-08-25
By default Ubuntu Server does not have any GUI installed, by design - the GUI is considered additional overhead un-necessary for a traditional server which doesn't usually have someone sitting at it logged in.  A lot of people either have other needs, or just want an environment a little less alien to them than a CLI-only login... thus if you scroll thru the forum, or do a quick Search, you'll see any number of threads on adding a GUI to the Server install.

The other option is to do a regular desktop install, and then afterwards from the comfort of the GUI desktop, install the server application(s) you need.  Other than the lack of a GUI, [the actual differences]("https://help.ubuntu.com/community/ServerFaq#What's%20the%20difference%20between%20desktop%20and%20server?") between the Server and Desktop installs at the core are ones that most casual users will not ever notice in real world use.

---

### Post by Monolith on 2011-08-25
What the previous poster said.

Ubuntu server is just that; the mechanicals *behind* the GUI. If you want a GUI, you can either (A) install one (Gnome, KDE, XFCE, whatever) or (B) download (K/X)Ubuntu Desktop.

I would go for option (B), it's less hassle than installing a GUI on top of Ubuntu Server IMHO.

---

### Post by arrrghhh on 2011-08-25
> **Monolith said:**
> What the previous poster said.

Ubuntu server is just that; the mechanicals *behind* the GUI. If you want a GUI, you can either (A) install one (Gnome, KDE, XFCE, whatever) or (B) download (K/X)Ubuntu Desktop.

I would go for option (B), it's less hassle than installing a GUI on top of Ubuntu Server IMHO.

To the OP - please, *please* go with option B.  Do not try to install a GUI on Ubuntu Server.  It's really not worth the effort... you'll spend a lot less time and headache going straight to the Ubuntu Desktop edition.

---

### Post by Monolith on 2011-08-25
> **arrrghhh said:**
> To the OP - please, *please* go with option B.  Do not try to install a GUI on Ubuntu Server.  It's really not worth the effort... you'll spend a lot less time and headache going straight to the Ubuntu Desktop edition.

Listen to this man :)

---

