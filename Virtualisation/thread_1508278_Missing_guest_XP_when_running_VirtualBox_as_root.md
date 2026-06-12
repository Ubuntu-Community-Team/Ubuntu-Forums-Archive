---
title: "Missing guest XP when running VirtualBox as root"
date: 2010-06-12
forum: Virtualisation
---

### Post by Happycamper374 on 2010-06-12
Hi all,

I'm running VirtualBox (not OSE) in Crunchbang built off of Ubuntu 9.04. I'm having trouble accessing my USB drive and I've tried several fixes. They're visible but greyed out. A common theme I've discovered in my internet searches is that if you run Virtualbox as root, people are able to access USB drives. I have no qualms about running a program as root regularly, so I'd like to try this as a fix. 

The problem is that when I run VirtualBox as root, (sudo VirtualBox), my XP install doesn't show up. When I run it as a normal user, the XP guest is there. What's up with that?

---

### Post by JKyleOKC on 2010-06-12
VirtualBox stores all of its data -- drives, machines, and logs -- in the hidden directory .VirtualBox in your home directory. When you run it as root, you're switched to root's home directory instead of your own, so you don't see any of your VMs.

You can "solve" the problem in several ways. Simplest is to copy the entire hidden VBox directory from your own home directory to a new one with the same name in root's home directory. The downside of this is that anything you do as root won't be stored in the same VM as the one you get when not running as root.

A better solution would be to determine why USB isn't working for you when logged in as yourself, not as root, and fix it. You might check the "users and groups" settings to make sure that you're a member of the usb users group, and also check the VM settings to be sure that the VM has its USB drivers enabled. I have no problem here, using USB in VBox when logged in normally, so I'm sure that the programs themselves can do it -- it almost HAS to be a configuration problem somewhere along the way!

EDIT: Also, check the way the USB drive is mounted. It's quite common for such drives to be mounted with root as the owner, and owner-only read and write permissions. This would produce the exact symptoms you're seeing. The cure is to configure the mounting parameters so that your UID (which is probably 1000) is the owner, or alternatively set the permissions to 777 to give everyone read and write permission.

---

