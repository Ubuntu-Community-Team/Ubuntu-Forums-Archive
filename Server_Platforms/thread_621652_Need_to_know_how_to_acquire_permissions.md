---
title: "Need to know how to acquire permissions"
date: 2007-11-23
forum: Server Platforms
---

### Post by greatnugget on 2007-11-23
I'm having a bit of trouble with Permissions. For some reason my computer will not allow me to add a new folder to an already existing folder, telling me that I don't have permission to write to it. I would like to have open access to everything since I am the owner of my computer. Can anyone help me? What do I need to do to give myself all permissions?

---

### Post by mikeyrb on 2007-11-23
Information about root and sudo: [RootSudo]("https://help.ubuntu.com/community/RootSudo")

Your user only owns what is inside your home directory.  You can either use a terminal to create directories outside of there, or run "gksudo nautilus" to open an instance of nautilus as the root user.  Be careful what you do as root!

---

### Post by wolfear on 2007-11-24
> **greatnugget said:**
> I'm having a bit of trouble with Permissions. For some reason my computer will not allow me to add a new folder to an already existing folder, telling me that I don't have permission to write to it. I would like to have open access to everything since I am the owner of my computer. Can anyone help me? What do I need to do to give myself all permissions?

There is a reason for that...security.
I run into this a lot when people have recently switched from M$ and suddenly can't get in and mess around in areas they have no reason to be in.

Like mikeyrb said, you only have general access in areas your user controls. Anything else requires using "sudo" for a very good reason.

If your system is telling you you don't have acess to create a folder in a certain area (unless its your /var/www folder if you are running a local server..which is a PITA), then you probably don;t need to be creating a folder there.

Going in a changing permissions on a widescale "willy-nilly" fashion" is a bad bad bad bad bad thing.

---

