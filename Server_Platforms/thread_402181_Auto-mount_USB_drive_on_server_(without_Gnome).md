---
title: "Auto-mount USB drive on server? (without Gnome)"
date: 2007-04-05
forum: Server Platforms
---

### Post by Abdi110 on 2007-04-05
Hi there. I'm building a new server that'll have a large amount of storage. This server will be headless without Gnome. I'd like to be able to plug in a USB hard drive into this server, then remotely through SSH, copy stuff from the home directory to this drive. I'd like to do this often so at the moment I'm guessing the only way to get the drive to mount is by running a script/command every time I plug the drive in. Is there any command line based app that keep tabs on when drives get connected and disconnected, mounting and unmounting accordingly? Thanks.

---

### Post by jackocleebrown on 2007-04-05
Hi Abdi110,

I had an issue that I wanted my drive to mount automatically on system power up - default behavior is to mount removable as user logs in with Ubuntu desktop. Solution for me is here & might be useful if you want certain things to happen when you plug in drives.

[http://ubuntuforums.org/showthread.php?t=339178](http://ubuntuforums.org/showthread.php?t=339178)

Hope you find what you need!

Jack.

---

