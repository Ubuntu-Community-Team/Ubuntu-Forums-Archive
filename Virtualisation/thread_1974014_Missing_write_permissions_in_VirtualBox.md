---
title: "Missing write permissions in VirtualBox"
date: 2012-05-05
forum: Virtualisation
---

### Post by Thev on 2012-05-05
Hi folks,

I've been setting up a persistent Ubuntu 12.04 on my USB-Device. Whenever I boot it directly on my hardware, it's persistent, I can access all linked harddisks and it works perfectly well.
But I want to use it in my VirtualBox (Windows 7 host) aswell, because sometimes it's a bit stressing to switch the entire OS for using a tool, I've got installed on my Ubuntu. Therefor I created *.vmdk-files which link my USB-Device AND my harddisk directly to the VM (ye, linking your running system to a VM is dangerous and stuff, I know, but it makes a lot of things easier if you know what you're doing).
With that setup I can boot my USB-Ubuntu and read my harddisk without having to shut down Win7.
It works quite well just to the point, where I want to save just ANYTHING. I can create new folders/files etc. anywhere and write/execute whatever I want, BUT it all remains virtualized. If I create a new folder on my harddisk, it doesn't exist in my Win7 and Ubuntu becomes inpersistent, as it fails to write changed on the USB while shutting down. So my entire VM is useless, as I can't use whatever progress I get.
btw. I can't change chmod on any files on my harddisk (not even as root).

Hope you guys can help me out on that one

Greetings, Thev

---

