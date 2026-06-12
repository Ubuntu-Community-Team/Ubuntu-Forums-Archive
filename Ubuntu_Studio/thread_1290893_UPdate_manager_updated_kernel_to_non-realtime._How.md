---
title: "UPdate manager updated kernel to non-realtime. How to get rt back?"
date: 2009-10-14
forum: Ubuntu Studio
---

### Post by BrianK on 2009-10-14
Via updates, I got a new kernel (this was a while ago, actually) - 2.6.28-11-generic.  I notice today that there is another kernel wanting to come down - 2.6.28-15-generic.  Now I no longer boot into the rt kernel which is still in grub - 2.6.28-3-rt.  Easy enough to fix through grub (to use the old kernel, that is), but my nvidia drivers now no longer work when selecting that old, rt kernel (it's possible that they never did - I seem to recall discovering the existence of the rt kernel after the 28-11-generic update).

So, my questions are:

1. How can I make the nvidia drivers work under the rt kernel (2.6.28-3-rt - which is now older than the more recent & currently running kernel)?

and/or

2. How can I make the newest kernel that comes from the update manager a realtime kernel?  Can I simply remake it with the rt flag turned on or something of the sort?  Any instructions for doing so?

I just recently started using this computer as my main music computer & not having that rt kernel is wreaking havoc on all things realtime related.

---

### Post by trulan on 2009-10-14
Jaunty's RT kernel was finicky for me when it came to booting up with the nvidia drivers installed.  It would boot up properly every second or third try.  AFAIK they never updated Jaunty's rt kernel, they have instead been focusing on perfecting the newer one, for Karmic.

To make your newer kernel RT you would have to actually build your own kernel, applying the Real Time patch, and I don't know how to do that.

My advice would be, hang in there until Karmic (Ubuntu 9.10) is released later this month.  It has a great RT kernel.  The nvidia drivers do work on that, except as of yet they need to be manually patched.  Hopefully by the release date this will be automated so they will work out of the box.

---

### Post by c00kie55 on 2009-10-15
well i thougth they fixed the nvidia drivers on last update on karmic  but i migth be wrong here

---

### Post by c00kie55 on 2009-10-15
:(Well seams they updated the rt-kernel again and now it not working again. again...and again hopefully there soon will be a fix

---

### Post by c00kie55 on 2009-10-15
Sorry if above dont apply to you (and it is working in karmic i just had to install nvidia driver from the rt-kernel not generic just tried)

yes it should be working in (jaunty) I had it working before
and isn't  the rt-kernel always a couple off steps behind.. I think so

2.6.28-3-rt is jaunty aint it  most admit I cant really remember 

I cut never figure out how get Nvidia hardware working in hardy

---

### Post by trulan on 2009-10-15
Yeah they fixed the NVidia drvers for Karmic RT shortly after I posted.  The devs still keep breaking things every few updates, but it looks like the final product is going to be good.  Hang in there - the release date is coming!

---

