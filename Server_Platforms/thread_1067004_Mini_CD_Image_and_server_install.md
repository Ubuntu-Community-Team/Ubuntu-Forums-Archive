---
title: "Mini CD Image and server install"
date: 2009-02-11
forum: Server Platforms
---

### Post by MagnetiK on 2009-02-11
Hi,

I have an old computer with an "almost broked" CD and I want to install Ubuntu on it.
When I try the 'normal CD' installation, I have severals error (I can't even verify the CD).

But the "Minimal CD Installation" seems to work ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)). It is possible to get the "server edition" of the CD? 

Indded I want to use this PC as a server and I don't want Gnome and other stuff..

Thanks !

---

### Post by hyper_ch on 2009-02-11
I think it's possible...

---

### Post by MagnetiK on 2009-02-11
And.. how ?

---

### Post by hyper_ch on 2009-02-11
with the normal alternate cd you can press F6 to select minimal install... this is like the server isntall but with the generic kernel. I tend to think you should be able to do something similar with that mini install cd

---

### Post by MagnetiK on 2009-02-11
Hummm.. I haven't seen any screen where I would be able to press F6

I'll take a look tomorrow...

If anyone else have ideas...

---

### Post by cariboo on 2009-02-11
At the menu screen, type server, this will install enough from the mini.iso to get networking going, then it will connect to the internet and download the rest of the packages needed for a server installation.

Jim

---

### Post by MagnetiK on 2009-02-11
When I type "server" I have the answer : 
"Could not find kernel image: server"

Any idea ?

---

### Post by Thirtysixway on 2009-02-12
Have you tried the JeOS version of Ubuntu?

---

### Post by ugm6hr on 2009-02-12
Install the base system with the mini iso.

> Boot from the mini.iso
Select install to command line.
Follow the instructions to install a base system.
When told to reboot, reboot to the HD rather than the CD.
This boots to the tty terminal: login with your chosen username and password.

You can then install the necessary server components / kernels with apt-get (if you know what they are)

Or, to make it easier... You need someone with a fresh server install (of the same version of Ubuntu) to tell you what packages are installed.

They could just run:
```
dpkg --get-selections > installed-software
```

And then upload the installed-software file (from their home directory) to this forum.  You could then copy it to your home directory (using the command line) and install everything with:
```
dpkg --set-selections < installed-software
dselect
```

Ref: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by MagnetiK on 2009-02-13
Worked fine, thanks !

---

