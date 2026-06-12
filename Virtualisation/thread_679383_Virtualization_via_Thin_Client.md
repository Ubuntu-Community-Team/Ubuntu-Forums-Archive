---
title: "Virtualization via Thin Client"
date: 2008-01-26
forum: Virtualisation
---

### Post by JoshuaRL on 2008-01-26
I have plans to set up a networked house in the near future and would like a little advice.  I don't know much yet, but I'm willing to learn.  Here's what I have planned.

AMD Athlon 64bit X2 4200+, 160GB SATA HD, 2gb RAM, Nvidia 8400GS 256MB on a CLI Ubuntu server.
26 port ethernet switch.
Maybe as many as 6 computers networked in.

The server will eventually be set up as:
A mail server.
FTP
VPN
Samba (?)
File/media for the network
Secure remote login
MythTV
And maybe games

And with all this, I want to see what you guys think the best way to do something more is.  I would like to set up a thin client in the living room to connect to the television.  I would like to run the free app Joost on the TV.  The problem is that I will need to virtualize XP because it doesn't run in Wine.  So how would I go about doing that?  And I don't have this set up yet, but I am planning on doing it soon.

Thanks for the help.

---

### Post by JoshuaRL on 2008-01-27
Okay, just to be sure everyone understands, I am not asking for help with all the setup of the server.  I just want a few suggestions about how to run a virtual XP machine through a thin client to hook up to a TV.  That's it.

Thanks guys.

---

### Post by seaq on 2008-01-27
i would recommend you to use for example,

edubuntu (for ltsp setup)
virtualbox PEL edition (with usb support) 
Semaless windows from virtualbox in order to start easily your sw.

The virtual machine would be running at your server so it won't affect your thin client setup.

If you digg a litle bit you would also use rdesktop to use xp directly from the thin client (logging directly to xp with rdesktop)

---

### Post by JoshuaRL on 2008-01-27
Cool man.  I have another question, can I use both Ubuntu and XP directly from the thin client?  I would like to only use XP for Joost, and use Ubuntu for everything else.

---

### Post by JoshuaRL on 2008-01-29
Sorry to do this, but

bump.

---

### Post by JoshuaRL on 2008-02-02
Bump.

---

