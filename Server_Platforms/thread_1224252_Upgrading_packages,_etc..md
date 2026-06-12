---
title: "Upgrading packages, etc."
date: 2009-07-27
forum: Server Platforms
---

### Post by happyhacker on 2009-07-27
I have 8.10 and it seems to work OK. I am keen on keeping it up to date. I also run SAMBA which I think is built in to the server so an update will cover this?

I also use webmin because the server does not have a console and keyboard. Webmin needs some package updates.

I am just a bit nervous about going for gold as although I have a binary copy of the server (tar) I do not have a lot of time to reinstall should it an upgrade fail.

1. Is there a restore facility like windows which will take me back to an earlier version?

2. Does the Ubuntu package upgrade do the lot including Webmin and is this the best way to do it?

3. What are the relevant commands to do this?

---

### Post by grantemsley on 2009-07-27
Upgrading with out a GUI is fairly simple:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

The last one installs kernel updates, the middle one won't.

Usually, everything works just fine.  The most common exception is if you have something like VMware installed, which installs its own kernel modules.

However, sometimes things do break.  You should be prepared to restore your backup, though you probably won't have to.

---

