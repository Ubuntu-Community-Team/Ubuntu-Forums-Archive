---
title: "question about linux on old computer"
date: 2006-02-09
forum: The Cafe
---

### Post by warpigs330 on 2006-02-09
I have a really old windows laptop and I get very fed up with windows so I un-installed it and I want to put a linux based program on it. it has 64 Mb of ram and 1.6 gigs of hard disk space. I told you it is old. I want a gui interface like ubuntu but something that can run on my computer. any suggestions?

---

### Post by Master Shake on 2006-02-09
You could try a "server" install of Ubuntu, then apt-get xubuntu-desktop.  THat's a lower overhead GUI.

---

### Post by fuscia on 2006-02-09
damn small linux or puppy linux seem like they'd be good choices for you, i'm guessing. you could even try pico bsd.

---

### Post by Bone Down on 2006-02-09
ubuntu-lite I did this on a PIII 600 with 256 ram and it works nicely.

[howto  here on this forum with links and wiki.]("http://www.ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu-lite")

---

### Post by raublekick on 2006-02-09
Damn Small Linux seems like the best candidate in my opinion.

---

### Post by xequence on 2006-02-09
[QUOTE=raublekick]Damn Small Linux seems like the best candidate in my opinion.[/QUOTE]

I aggree.

---

### Post by warpigs330 on 2006-02-09
I am sorry I am completley un educated with this kind of stuff, I have no idea how to download damn small linux. I found a site with a bunch of mirror sites but it is a directory and those I know nothing about. sorry for the trouble.

---

### Post by raublekick on 2006-02-09
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
This is the official home page of Damn Small Linux, you can gather lots of info there.

[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)
Mirror pages, go to one of them (ibiblio looks good). The first file is a readme that might help. dsl-2.2.iso is probably what you want.

---

### Post by mohapi on 2006-02-09
I would suggest Damn Small Linux over Xubuntu. I've put Xubuntu on a 120Mhz/48MB/1GB laptop, and while it works, it's still too sluggish. I've also put the Fluxbox desktop on that same machine, and it works better.

Damn Small would probably be best, although I found it to be a little less "friendly" than Ubuntu. I haven't tried Puppy Linux or Pico BSD, but I might now that I have heard of them.

Damn Small runs off a CD. Download the ISO, burn it to a CD (on another computer, of course), and start up your laptop with that disc in the drive. Make sure your machine is set to boot from CD. Good luck!

---

### Post by fuscia on 2006-02-09
[QUOTE=warpigs330]I am sorry I am completley un educated with this kind of stuff, I have no idea how to download damn small linux. I found a site with a bunch of mirror sites but it is a directory and those I know nothing about. sorry for the trouble.[/QUOTE]

go to this page - [ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/)

then click on dsl-2.2-syslinux.iso (12th one down, i think. can't count, or spell)

burn the iso on a disk, etc.

---

### Post by Iandefor on 2006-02-09
Here's a direct link:

[ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-2.2.iso]("ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-2.2.iso")

If, after burning to disc, it won't boot, try this one:

[ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-2.2-syslinux.iso]("ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-2.2-syslinux.iso")

You know how to burn ISO's to disc, right?

---

### Post by TrailerTrash on 2006-02-09
Try STX Linux. Its based on Slackware and is fast and stable. 

[http://www.stibs.cc/stx/](http://www.stibs.cc/stx/)

---

### Post by warpigs330 on 2006-02-09
I do not know how to burn ISO's to disk. sorry for the utter incompetence

---

### Post by mips on 2006-02-09
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by geekphreak on 2006-02-09
Another vote for Damn Small, I was using it on a P1 200 MHz processor and 32 MB RAM very successfully.

---

### Post by warpigs330 on 2006-02-09
well I put damn small on it but once it booted I have a pretty messed up interface. it is teal and I can barely make out the icons. the graphics were fine until the gui interface came up.

---

### Post by RaiSuli on 2006-02-11
I just installed STX Linux on an old laptop (P2, 64 mb ram, 256 mHz) and it runs just fine. Reasonable speed and no problems with hardware detection. Might be an alternative, if DSL is giving you trouble.

---

### Post by K.Mandla on 2006-02-12
[QUOTE=warpigs330]well I put damn small on it but once it booted I have a pretty messed up interface. it is teal and I can barely make out the icons. the graphics were fine until the gui interface came up.[/QUOTE]
I had a problem like that. It was a shimmery turquoise color. Couldn't see a darned thing.

If I remember right, I got it working with *dsl vga=788* or *dsl vga=789*. I think it's a color depth issue. Hit F3 at the boot for all the options. Good luck!

---

### Post by drfalkor on 2006-02-12
Damn Small Linux :KS

---

### Post by The Mekon on 2006-02-12
I use Damn Small Linux installed on a USB Pen Drive.  Most machines will, after setting up, boot from the pen drive but some older ones need a floppy boot disk.

This is useful for two reasons:

One I can acces my E-mail from any computer with permanent intenet access and two I often use to retrieve files from my friends crashed Windows Systems.

It is not a replacement for Ubuntu but it is very useful to have.

---

### Post by WolfJay_83 on 2006-02-12
Xubuntu is way too much overhead for 64mb ram.  Your best bet is to do a server install of ubuntu, then, once loged into a terminal, type

sudo apt-get install gdm x-window-system-core xterm icewm menu mozilla-firefox abiword synaptic

This will set you up with a minimal system.  If firefox is too slow, you can install Dillo later.

I would suggest reading around the wiki. 
[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

I don't recomend DSL unless you plan on running of cd all the time.  It is good for testing out your machine though.  The harddrive install is not worth your time in troubles.

Puppy linux is okay, but dont try to install a wireless card or upgrade any software.  IT is, however easy to install and will work fine on your old machine.

Ubuntu is quite capable of being set up on an old machine because you can start with a server install and add whatever pieces you want simply by apt-get or synaptic.

---

