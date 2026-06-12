---
title: "SD Card not recognized after multiple suspends"
date: 2009-07-04
forum: System76 Support
---

### Post by drewbenn on 2009-07-04
I have a panv3, and have started using suspend fairly frequently since doing a clean install of 9.04.  A few minutes ago, I tried inserting an SD card but nothing happened. 'dmesg | tail' didn't report anything, and 'ls -rtaFl /var/log' showed that no logfiles were being updated when I inserted the SD card.  I tried with two known good SD cards.  I had probably suspended and resumed a dozen or more times since I last rebooted my computer yesterday evening, and it had been back and forth a few times between AC and battery power.  After rebooting my laptop, the SD card was recognized immediately.

I don't use SD cards all that often, but I don't want to have to reboot every time I have to use them!  Does anyone have any suggestions of what to look for if this happens again, to try to debug the problem?

---

### Post by thomasaaron on 2009-07-06
Yeah, suspend is coming along nicely in Linux, but multiple cycles can still be problematic from time to time.

It's probably a module-loading problem after suspend.

Reboot your computer and post the output of...

lsmod

...and we'll try to work it out.

---

### Post by drewbenn on 2009-07-06
I just rebooted and ran lsmod. Can I assume you will want to see the output of lsmod the next time I can't access my SD card?

---

### Post by thomasaaron on 2009-07-07
OK, good. So, next time it fails try running these commands...

sudo modprobe -r ricoh_mmc
sudo modprobe ricoh_mmc

The first one *might* throw an error. Just ignore it. Does that fix it? If so, we can probably fix the problem permanently.

And, yes, include lsmod next time it fails. It could be that ricoh_mmc is being loaded in the wrong order, or it could be that it isn't getting loaded at all. We will need to know which.

---

### Post by drewbenn on 2009-07-10
Hi Thomas,

I've kept an SD card around and tried it after every few suspend/resumes, but I haven't run into the problem yet.  I guess that's good :).  I'll keep trying.

I also wanted to say Thank You: my sister's card reader (on a Toshiba Portege) hadn't worked since upgrading to 9.04, and the hints from this thread and a recent Starling SD reader thread gave me the search terms I needed to get her card reader working!  So if nothing else, you've fixed another random Ubuntu user's computer :guitar:.

---

