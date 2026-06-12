---
title: "Looking to dual boot with Slackware..."
date: 2008-08-15
forum: The Cafe
---

### Post by lovhorror on 2008-08-15
I have Ubuntu installed and working great on both my desktop and my laptop. But I've decided to play around with Slackware, as well, to see if I like it. I downloaded the iso, how do I partition the harddrive and install this other linux distribution? Do I need a dvd-r to burn it onto, first? Or can I just mount it somehow? 

Note: I wont be able to check this for a few days, gonna be out of town. Any and all advice would be great.

---

### Post by original_jamingrit on 2008-08-15
hey, slackware is cool

before doing any repartitioning, I suggest backing up any important stuff.  Then use gparted on the ubuntu disc to resize your main ubuntu partition, and then add another for slackware (Strictly speaking, it's not necessary to add more, but do partition some more if you prefer).  You may want two if you'd like to keep your slackware's /home a seperate partition. (if you'd like to make an ubuntu home and a slackware home under the same partition, you may still use the same username and just make sure to have your slackware user's $HOME set to a differently named directory while using adduser/useradd).

So, a couple of valid examples:
[Ubuntu Root][Slackware Root][swap] <--simplest, probably easiest.
[Other OS][Ubuntu Root][Slackware Root][Home][swap] <--If data separation is desirable.

If you ever like to use any hibernation features, then also give slackware its own swap space.  If you never use hibernate or suspend-to-swap, then the OSs can share a swap safely.

here's a link to a no-disc install method: [http://www.linuxquestions.org/questions/linuxanswers-discussion-27/installing-slackware-12-or-another-version-with-the-iso-images-but-without-burning-them-568173/](http://www.linuxquestions.org/questions/linuxanswers-discussion-27/installing-slackware-12-or-another-version-with-the-iso-images-but-without-burning-them-568173/).  Although it's better to have the DVD burned anyways, IMO.

For booting, it's simply easier to not install LILO and just use Ubuntu's GRUB manager.  Add this line to it ubuntu's /boot/grub/menu.lst:
```
##Slackware partition boot
  title Slackware Linux
  root (hd0,0)
  kernel /boot/vmlinuz root=/dev/XdXN ro vga=???
```
where (hd0,0) depends on how GRUB is installed (probably won't change it if you only have one hard drive) you replace XdXN with the new Slackware root partition (hda, sdb) and vga=??? with whatever it says for Ubuntu (or simply check [here](http://tuxmark.blogspot.com/2007/09/vga-boot-modes.html)).  If you would like to try using LILO instead, then just make sure to add the relevant Ubuntu boot option(s) at install.

And then, I think that's pretty much it.  Boot into Slackware, and then add yourself as a user, and then you're gold.

Other helpful links:
[http://www.slackbook.org/](http://www.slackbook.org/) <--available in several formats, good reference guide.
[http://www.vcn.bc.ca/~dugan/setting-up-slackware.html](http://www.vcn.bc.ca/~dugan/setting-up-slackware.html) <--good instructions for quickly setting up a slackware desktop (although definitely try it your own way first ;-) )
[http://www.linuxpackages.net/](http://www.linuxpackages.net/) <--quick binary .tgz install packages, install with the command 'installpkg whatever.tgz'.
[http://www.slackbuilds.org/](http://www.slackbuilds.org/) <--links to popular tarballs and build scripts for programs.  Best for if you like to tweak source code, but don't like to compile.

good luck, and happy slacking

---

### Post by lovhorror on 2008-08-19
I appreciate your response. I recently decided to dual boot it on my laptop. Should that change anything?

---

### Post by original_jamingrit on 2008-08-19
Not really.

Laptops are good for Slackware, but if you find you're aren't getting very much out of your battery, you may want to configure a new kernel.  Optimize for battery power, use a power-saving CPU manager, maybe enable hibernate (suspend to swap), that sort of thing.  But first, run Slackware for a while and see if you think it's necessary, it might not be necessary.

The only really tricky part might be wireless, but see how the rest goes first.

---

### Post by lovhorror on 2008-08-20
Well, I don't have wireless to begin with. Haha.

In any case I'm not going to be experimenting with slackware for a few weeks, waiting 'till I move into my dorm. When I do I'll post here how it went.

---

### Post by cardinals_fan on 2008-08-20
I'm a HUGE fan of Slack.  It's fast, powerful, and vanilla.  Take your time with the installation and enjoy the learning experience.

I strongly recommend installing vanilla Slack first (you'll learn more), but you can also download the SLAX live CD (only ~189 MB), install it, set up slapt-get, and sync it with the 12.1 repos for a genuine Slack experience with minimal effort/downloading.

---

