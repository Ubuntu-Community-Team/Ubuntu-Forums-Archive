---
title: "Debmirror type software for Windows?"
date: 2005-09-15
forum: Repositories &amp; Backports
---

### Post by henrypootel on 2005-09-15
I've been using Ramon Acedo's howto on building a local mirror of the ubuntu repository, and i'm really excited about it. I have Breezy installed on my home PC, but i only have dial-up there, so i can't get all the stuff i need(kernel sources etc..) as it takes way to long.

We do however have a nice thick pipe at work, so i would like to download the MAIN repo there, and burn it to a DVD and take it home. The problem is, our office is entirely Windows based, so i need to be able to download the repo somehow from a Windows box.

Does anybody know of a way to do this? i know that i could just grab the whole 'main' folder from the repo ftp, but then i get the files from all 3 architectures(64bit, ppc & i386), when i only want i386, and i would also get the source and hoary versions, which i also don't want.

Please help me.

---

### Post by BoyOfDestiny on 2005-09-15
wget (works with http and ftp) would totally do the trick. Here is a link to the win32 port:

[http://xoomer.virgilio.it/hherold/](http://xoomer.virgilio.it/hherold/)

I recommend reading the readme... basically you can make it dl the sub dirs (recursive), and files that contain *i386* let's say. 

Other nice thing is you can make it auto resume, schedule the download, even set the speed at which it gets each file.

All done in one line... no joke =)

---

### Post by UbuWu on 2005-09-30
If you only want main, it is easier to download the dvd edition, which contains the whole main repository (and it is live cd/installer in one). You can find it here for hoary as well as breezy: [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

---

### Post by BobSongs on 2008-03-25
[Here's a spot]("http://ubuntuforums.org/showthread.php?t=352460").

---

