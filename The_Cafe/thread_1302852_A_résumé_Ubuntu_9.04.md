---
title: "A résumé: Ubuntu 9.04"
date: 2009-10-27
forum: The Cafe
---

### Post by ticktricktrack on 2009-10-27
A résumé: Ubuntu 9.04 - And not a nice one, more of a rant actually.

First of I use Ubuntu professionally and on my home computer - about 90% of the time.

So far I really liked Ubuntu, every version comes with new features and new stuff working out of the box. I definitely was generally pleased with it. Well until 9.04 that was!

All I want now is a Mac! I always rejected Apple for being overpriced, but now I'm actually saving up for a Mac, to get away from Ubuntu. Sad that it has come to that.

When Brainstorm launched I hoped this would really speed things up a bit. But if you take a closer look, they implemented do close to nothing of the all ideas. And 43 of the top 50 ideas are from feb-march 2008. So it looks like the users know what they need but are willingly ignored.

9.04 came with about no additional features that I actually experienced. It didn't feel shiny and new, more like the old one with new car smell sprayed on. OK, but I can live with that.

Except for a few problems that completely ruined the experience:

1. Samba - broken, reports "Failed to retrieve server list" - so I fixed the config manually only to have it broken again by a samba update. This time irreparably"

2. The repo: Synaptic is as sluggish as usual, but much worse - a lot of packages are terribly outdated. Ruby e.g. and lots of tools I like. Firefox 3.0 instead of 3.5 also is a good example here.

3. Compiz: Did they do anything on that front? I didn't notice it - same old bugs as usual.

4. USB Drives: 9.04 keeps breaking them all the time. Whether they are formatted as FAT or as NTFS, it manages to break files and folders. Especially when unmounting. And the speeds are horrible, even my ext formatted stick reaches only about half the average speed on windows. With NTFS it's worse - like 3 hours to copy 5 GB!

5. Wubi: Well until yesterday I was happy with it. Then Ubuntu froze up and on reboot it was gone, just gone with all my days work. Completely disintegrated!

6. Printing - Lol, 2009 and an OS can't print. Still can't rely on any drivers. But that doesn't matter - it can't find the network printers anyways.

Well that should do for now. But there's a lot more.

Tick

---

### Post by Firestem4 on 2009-10-27
> **ticktricktrack said:**
> 6. Printing - Lol, 2009 and an OS can't print. Still can't rely on any drivers. But that doesn't matter - it can't find the network printers anyways.

lol, 2009 and we're still printing?

> **ticktricktrack said:**
> When Brainstorm launched I hoped this would really speed things up a bit. But if you take a closer look, they implemented do close to nothing of the all ideas. And 43 of the top 50 ideas are from feb-march 2008. So it looks like the users know what they need but are willingly ignored.

**9.04 came with about no additional features** that I actually experienced. It didn't feel shiny and new, more like the old one with new car smell sprayed on. OK, but I can live with that.

Except for a few problems that completely ruined the experience:

This was done for a reason. Brainstorm is a great idea but what is the point of continuing to build when your foundation is not solid? Why add more features when the core components are buggy?

---

### Post by TheNessus on 2009-10-27
> **ticktricktrack said:**
> 

Firefox 3.0 instead of 3.5 also is a good example here.



well, obviously you haven't checked synaptic for a while now. what, 6 months is it?

---

### Post by coolbrook on 2009-10-27
What model of printer are you working with?

---

### Post by ticktricktrack on 2009-10-27
Of course I did install 3.5 Shiretoko, and I use it of course. But without the Ubuntu AddOn it doesn't seem integrated into the system. Can't open archives directly. I have to save everything first. And sometimes Ubuntu opens files in 3.0 even I especially told it not to.

---

### Post by ajgreeny on 2009-10-27
The trolls are out and about again?

Sorry you feel this way, but I think you are in the very smallest minority, and most of the problems you talk of are unusual.  Printing is usually a case of plugging in a printer and away you go, unless of course, you happen to have one of those paperweights that don't have any drivers and for which the manufacturers won't even free up the data needed for an open source driver to be written.  I have yet to need to do anything to get a printer to work when I have plugged one in; I just do that and the system says "Printer Name-of-printer ready to print" or something similar.

I can't comment about samba or ruby as I have no need or interest in them, but have never had any problems with synaptic and the repos, compiz, which works brilliantly if you have the right hardware, nor with any of mine or other peoples usb drives.

From your final complaint, I wonder if you are using a wubi install, and if so, whether or not that has any bearing on the problems you seem to have.

---

### Post by ticktricktrack on 2009-10-27
> **coolbrook said:**
> What model of printer are you working with?

At home I use a Brother 2030 which would work fine if the network would.
At work a Ricoh something, an older lexmark, a special label printer, an older HP.

---

### Post by coolbrook on 2009-10-27
I just picked up the Brother HL-2170W.  Installation is smooth. I have an old Lexmark that didn't support Linux.  It's off to the electronics recycler in the spring.

---

### Post by NoaHall on 2009-10-27
There are other distros in the world than Ubuntu. Turning to Mac is just giving up(and quite often, a waste of money).

---

### Post by LowSky on 2009-10-27
> **ticktricktrack said:**
> 
1. Samba - broken, reports "Failed to retrieve server list" - so I fixed the config manually only to have it broken again by a samba update. This time irreparably"

   
During the update it asks to update the smb file, your supposed to say no


> **ticktricktrack said:**
> 
2. The repo: Synaptic is as sluggish as usual, but much worse - a lot of packages are terribly outdated. Ruby e.g. and lots of tools I like. Firefox 3.0 instead of 3.5 also is a good example here.

   

Newer versions of most software can be grabbed from the net if you need them, poor excuse

> **ticktricktrack said:**
> 
3. Compiz: Did they do anything on that front? I didn't notice it - same old bugs as usual.
   
Compiz isn't developed by the Ubuntu team, they just package it for the OS

> **ticktricktrack said:**
> 
4. USB Drives: 9.04 keeps breaking them all the time. Whether they are formatted as FAT or as NTFS, it manages to break files and folders. Especially when unmounting. And the speeds are horrible, even my ext formatted stick reaches only about half the average speed on windows. With NTFS it's worse - like 3 hours to copy 5 GB!

   

I have this issue as well, its a Linux issue, not specifically Ubuntu, the kernel developers have no idea that people need to transfer GB size files to a USB device. So far the only issue I think is really a problem for you.

> **ticktricktrack said:**
> 
5. Wubi: Well until yesterday I was happy with it. Then Ubuntu froze up and on reboot it was gone, just gone with all my days work. Completely disintegrated!

   
WUBI is not the way you should be installing Ubuntu, do a normal install and dual boot from GRUB

> **ticktricktrack said:**
> 
6. Printing - Lol, 2009 and an OS can't print. Still can't rely on any drivers. But that doesn't matter - it can't find the network printers anyways.
   
Are you using CUPS, it works for me.

---

