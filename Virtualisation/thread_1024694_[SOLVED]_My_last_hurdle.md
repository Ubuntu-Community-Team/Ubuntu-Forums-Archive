---
title: "[SOLVED] My last hurdle"
date: 2008-12-29
forum: Virtualisation
---

### Post by fishman78 on 2008-12-29
I installed Ubuntu 8.10 and I love it.  However, I need to run iTunes for my phone (crapy i know, but it's too late now).  I made an XP machine through Virtualbox and it runs great, even better than XP as a primary OS.  I installed iTunes and that's where the problem starts.  The software seems to run great at first and I have succesfully synced the phone, but more often than non it freezes up.  By that I mean the screan dulls out to grey and stops working.  Some times it eventually recovers, but it's a PITA.  Any ideas of how to make this stop happening??  I installed the guest additions, but not much more than that.  I maxed the video memory and assigned 1536MB RAM for the VM. Thanks for your help!!

Fishman78

---

### Post by fishman78 on 2008-12-30
I guess no one has the same problem as me?  Stinkin' crappy iPhone!  Anyway, would VMware work better in this situation.  I really like virtual box as it installed easy and is easy to work with.  I haven't had success with installing VMware.  Thoughts?

Fishman78

---

### Post by pietjanjaap on 2008-12-30
The memory shpuld be small, bigger is not better, make it standard and smaller.

Your main os will be swapping all the time, is not good and not fast.

---

### Post by SunnyRabbiera on 2008-12-30
VBOX might be your best bet indeed.
iphones= suck

---

### Post by fishman78 on 2008-12-31
> **pietjanjaap said:**
> The memory shpuld be small, bigger is not better, make it standard and smaller.

Your main os will be swapping all the time, is not good and not fast.

I tried it with 1024 and 2048 with no success either.  Should I try 512mb?

iphone=suck.....yes, yes they do....but I'm stuck with it now.

Thanks for your help

---

### Post by howefield on 2008-12-31
> **fishman78 said:**
> I tried it with 1024 and 2048 with no success either.  Should I try 512mb?

VirtualBox XP should be ok with as little as 256, I usually give mine 384 or 512 though and work fine. I am not sure why it wouldn't work with a gig or even 2 as you tried, as long as you have enough left for the host to work correctly.,

---

### Post by fishman78 on 2008-12-31
> **howefield said:**
> VirtualBox XP should be ok with as little as 256, I usually give mine 384 or 512 though and work fine. I am not sure why it wouldn't work with a gig or even 2 as you tried, as long as you have enough left for the host to work correctly.,

Well, I run ubuntu 8.10 64 bit with 4GB of mem.  512mb goes to OMB GPU so about 3.5GB left.  That should be okay right?  I'll try reducing the RAM size of the VM tonight and let you know how it works out.

---

### Post by fishman78 on 2009-01-04
Well,  It looks like this Nvidia On-Board 8200 GPU bites my butt again.  As soon as I put in an old cheaper 7300 it works fine now.  Go figure.  Hope this helps someone out there who got sucked into the iPhone thing.  Thanks for everyone's help!

---

