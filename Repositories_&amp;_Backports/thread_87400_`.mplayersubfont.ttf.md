---
title: "`/.mplayer/subfont.ttf"
date: 2005-11-08
forum: Repositories &amp; Backports
---

### Post by EvilBill on 2005-11-08
My MPlayer that I got thru S P Mgr, asks for this. It still works fine, but I think I will get sick of being asked for this stupid thing, eventually. 

How or where can I find it. (I looked)

or

How can I get it to stop asking me for this?

---

### Post by Xian on 2005-11-08
[QUOTE=EvilBill]How can I get it to stop asking me for this?[/QUOTE]

Install one of the versions in the Ubuntu repos:

:)

```
$ sudo apt-cache policy mplayer-386
mplayer-386:
  Installed: 1:1.0-pre7cvs20050716-0.1ubuntu9
  Candidate: 1:1.0-pre7cvs20050716-0.1ubuntu9
  Version table:
 *** 1:1.0-pre7cvs20050716-0.1ubuntu9 0
        500 http://us.archive.ubuntu.com breezy/multiverse Packages
        100 /var/lib/dpkg/status
```

I got that message at startup with mplayer when I installed it from source a while back, and after googling the error message I think it was just a matter of symlinking a font type. You might peek around a bit and see if you uncover the same information.

---

### Post by EvilBill on 2005-11-08
> Install one of the versions in the Ubuntu repos:


I can't seem to find the fonts.:( 

I googles this, & came up with a site that said something about installing xFree86-truetype

I can't find them. Will continue to look. :smile:

---

### Post by rasgward on 2005-11-08
I have been having issues with apt-get and my synaptic. Here's an example below of what I got when I did the above mentioned of downloading the mplayer from apt-get... Any thoughts? -Greg







W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by jeremy on 2005-11-08
apt-get mplayer-fonts

---

