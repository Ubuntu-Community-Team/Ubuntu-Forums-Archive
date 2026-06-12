---
title: "Pooched a server, need to ressurect."
date: 2008-07-07
forum: Server Platforms
---

### Post by itzpapalotl on 2008-07-07
Okay, so I pooched my LAMP stack, and I need it back.

I was playing around trying to get some scripts working, and I accidentally was in the wrong place when I hit it with mv * /bax

So, I was in / when I did that.

So I moved Linux in to a folder in itself, and it doesn't like that as it turns out. 

I already did the part where I cursed, and kicked myself repeatedly. I have already chastised myself playing fast and loose as root. Neither of those things seemed to help. 

ssh is out of the question.
telnet, or really anything that relies on a working machine to catch the command is pretty much out.

I'm guessing my situation is not actually that bad. Nothing really should have gotten lost in the process I wouldn't think.

Are either of these options going to make my machine work?

1) maybe I can mount the drive from another machine in the network, and move all the critical files back to where they need to be.

2) physically attach the drive to another machine and again, move stuff back to /

if not, do I have any options, or am I just hosed and going from the latest backup...?

---

### Post by windependence on 2008-07-07
Your best best is to boot from a recovery CD or live CD, and mount the file system under something like say /mnt/filesystem, then move things back where they should be. If you need help, let me know. Remounting the file systems can be tricky sometimes.

-Tim

---

### Post by itzpapalotl on 2008-07-09
Yay!!!

Used a Hardy live cd.
Worked just fine..
Thank you 
thank you
thank you

---

