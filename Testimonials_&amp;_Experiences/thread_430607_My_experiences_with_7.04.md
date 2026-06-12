---
title: "My experiences with 7.04"
date: 2007-05-02
forum: Testimonials &amp; Experiences
---

### Post by mach777 on 2007-05-02
I installed Feisty 7.04:

Issues:
- Couldn't boot liveCD with my SATA drive active, had to disable autodetection in the BIOS. This is where 50% of all users give up.
- Couldn't install liveCD to hard disk without dismounting all drives and USB drives. This is where another 20% give up.
- Couldn't boot from my SATA drive. Had to add "irqpoll" to kernel options, and boy before I found that.... This is where another 25% give up.
- Broken nvidia drivers with some kernel/driver mismatch version something. Had to make a reinstall of the whole system and use the great little app "envy" to setup my dual screen. This is where the last %4 give up.
- Tried to dual boot windows. First Ubuntu then windows, but windows overwrote the mbr so I had to reinstall everything doing Windows first then Ubuntu.
- Windows works for 4 boots, then it breaks complaining about NTLDR something. Scrapped the idea of dual booting or even keeping windows on the same computer.

Other issues:
- Couldn't write to my external NTFS drives by default, had to install some ntfs-3 driver (why?!?).
- Beryl didn't install, gave me no window borders/titles.
- Terminal window just suddenly stopped working. Had to add some obscure option to a startup script to get it back working.
- WoW doesn't work in WINE. I can't see inventory icons which is a must. Same problem with Crossover.
- Photoshop doesn't work in WINE, at least what I tried.

All in all, I reinstalled Ubuntu at least 4 times, tried Kubuntu once, and am now running on my second fresh install of Xubuntu. Trimmed down the system to just one dedicated Linux drive and a CD Rom, to get it to work.

Took me roughly a week of installation and tuning and eternal reboots to get a system up running dual screen without errors. My system isn't special:

NVIDIA 7600GS card with 2 monitors.
Core2Duo with 2 gig memory.
1 SATA drive and 1 CDTW drive.

Ubuntu is not ready for the masses. Maybe 1 out of 50 will be able to follow through the hoops and actually get it installed. Too many bugs. Too much configuration and odd behaviour.

That said....

I absolutely love my Xubuntu. It is fast, nimble, non-bloated, apps do what they should.

* Its fast. Super. Fast. Responsive.

* The gnome media player is totally awesome. It is fast-fast-fast.

* I love the file manager (thunar?). It is fast. Actually everything is fast. No hassle no hangups, just speedy.

* It looks absolutely fantastic. I got it themed pretty much like MacOS.

* Running 4 screens is pure GUI bliss.

* Apps are simple and stable. I don't have a billion unnecessary options. No bloat.

* I am hard pressed to use up more than 500 meg of ram. I don't really know what to do with the 2 gigs I have installed lol. 

* Synaptic/Apt-get is great. I need a program? I just install it and its just there, without any adware or registry bloat, or eternal wizards.

* I have to say again: X windows apps in general are great. No eternal wizards or thousand buttons. They just do what I want them to do. I did some backups of files to DVD yesterday. So easy to use, so fast.

* Did I mention XFCE is fast? It is. I'm getting amiga flashbacks. The computer is a pleasure to work with. Its a zen like experience. No bloat. Phew.

* Its free.

* I'm using a perfect 13px system font and its so much easier on the eyes. Looks absolutely fantastic as well.


Having used X for 2 days now, I can't see myself going back to XP. Ever. But it took alot of work to get the system to where it is. Need to figure out how to make a backup of it all.

---

### Post by Sef on 2007-05-02
Almost all of your problems are because of proprietary hardware/software.   NTFS is one example of being locked in/out.  Though now there is software for Linux that will read NTFS.

---

### Post by mach777 on 2007-05-02
I am using a quite common system though, no raid, only 1 sata drive and a not-too-old-not-too-new nvidia card.

Most of my problems had to do with the new kernel SATA changes. I had the exact same problem when I tried to install the latest PCLinuxOS rc4. So nothing to do with Ubuntu in particular, just with the latest linux kernel in general.

Actually, it would be nice if there was a recommended system spec with ubuntu. I'm not interested in a list of supported hardware, but an actual specified system rig. A complete rig that every release would be tested on before release with this and that motherboard, gfx card, cpu etc.

I don't mind getting a new computer if I know the OS will install and run on it 100% guaranteed. It would be similar to getting a mac.

Still, I do love my xubuntu and thank you all again for making it happen.

---

### Post by TheMono on 2007-05-04
How odd. I also have a 7600GS with two monitors, a core 2 duo, and the like. The only problem I had was that Feisty wouldn't install, and I had to install edgy and then upgrade it to feisty. Please bear in mind though that when I did the installing, Feisty was at Herd 4, certainly not final, and I gather the issue has been fixed with respect to the one bit of hardware that was sticking.

---

