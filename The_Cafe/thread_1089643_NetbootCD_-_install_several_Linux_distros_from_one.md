---
title: "NetbootCD - install several Linux distros from one CD"
date: 2009-03-07
forum: The Cafe
---

### Post by maybeway36 on 2009-03-07
NetbootCD is my live CD that can install many Linux distros. It boots into a slightly modified Tiny Core in text-mode and pops up a few dialogs asking you which distro and version to install. Then, it downloads the kernel and initrd and uses kexec to load them, replacing itself in memory with the new distro's installer. The installer then proceeds to install the rest of the distribution as normal.

It can also load the latest version of GRUB4DOS. (This is mostly to show off.)

You can get it at: [http://netbootcd.tuxfamily.org/](http://netbootcd.tuxfamily.org/)

The newest version is 3.0, based on Tiny Core.

---

### Post by doorknob60 on 2009-03-07
Add Arch?

---

### Post by maybeway36 on 2009-03-07
Unfortunately, the way in which the Arch FTP installer works makes this impossible; in order for NetbootCD to boot something with kexec, everything needs to be in the kernel or initrd and loaded to RAM.

---

### Post by bsharp on 2009-03-07
That's pretty awesome, how long did you work on this?

---

### Post by doorknob60 on 2009-03-08
> **maybeway36 said:**
> Unfortunately, the way in which the Arch FTP installer works makes this impossible; in order for NetbootCD to boot something with kexec, everything needs to be in the kernel or initrd and loaded to RAM.

Kinda thought that might be a problem. Oh well, still looks like a great project. I'll try it out soon.

---

### Post by maybeway36 on 2009-04-10
My new version, 3.0, is based on Tiny Core Linux with X11 removed. It weighs in at only 6.1 MB! You can get it at the website in the original post.

---

### Post by init1 on 2009-04-10
Nice, I've got a CD similar to that. It has the netinstall images for Debian and Ubuntu, as well as Slitaz, TTYLinux, and FreeDOS. It's very useful.

---

### Post by shamurshamur on 2009-09-13
Can somebody tell me  .....how to set proxy server settings in netbootcd.
I am behind a proxy server and have to enter proxy server address to access internet.

---

### Post by Mehall on 2009-09-13
[img]http://www.blogcdn.com/www.wow.com/media/2007/09/forumnecromancy.jpg[/img]

---

