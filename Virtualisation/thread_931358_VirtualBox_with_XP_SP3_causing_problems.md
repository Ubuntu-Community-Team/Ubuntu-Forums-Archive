---
title: "VirtualBox with XP SP3 causing problems"
date: 2008-09-27
forum: Virtualisation
---

### Post by FokkerCharlie on 2008-09-27
Hello!

I have been running VirtualBox fine for a while on my Hardy laptop- runs very smoothly in general.  However, since accepting the automatic update to SP3, the setup becomes quite unstable.

In particular, I have seen screen corruption (I am using compiz, otherwise that works well) pretty much every time I shut down the virtual machine- resulting in an unusable system for around 5 mins.  After that, sometimes my lappy springs back to life, sometimes I see an uncommanded X restart.  There are also problems resizing the guest display.

Anyone else seen something like this since 'upgrading' to SP3?  Any way I can start to try to debug what's going on?

Cheers
Charlie

---

### Post by skunkTrader on 2008-09-27
Try reinstalling the guest additions.  Maybe the SP3 update scribbled over something

---

### Post by FokkerCharlie on 2008-09-27
Hi, SkunkTrader

Thanks for you input.  I followed your advice, and re-installed the guest additions, but it didn't seem to make a difference.  One more thing to note- I only see the display corruption if I switch to a different virtual desktop while the virtual machine is shutting down.  Very strange.

If it comes to it, I have an old .vdi image that I can revert to from before the SP3 update.

Any more tips gratefully received.

Charlie

---

### Post by starcannon on 2008-09-27
I slipstreamed sp3 into my xp install disk, and sp3 works excellently in virtualbox for me that way. I've never tried updating to sp3 in VB though so not sure about that. Anyway, if you'd like sp3 on your vb install I can verify that slipstreaming and remastering your xp install disk works just fine for VB.

GL and have fun(as a side note, for us VB users its a pointless service pack really)

---

### Post by WWSmith36 on 2008-09-27
I had a slip streamed copy of SP3 running in my virtual box and I also had some problems.  Since reinstalling with SP2, no more problems

---

