---
title: "Upgrade from 10.04 to 11.10 with software raid"
date: 2011-11-08
forum: Server Platforms
---

### Post by vraulet on 2011-11-08
Hi,

I recently upgraded my server running Ubuntu 10.04 to 11.10. The upgrade seems to have gone "smoothly" but after restarting the system, I was welcomed with:

```
error: incompatible license.
grub rescue> _
```

My server runs in Raid 1 mode using software raid.

I can boot from the CD and chroot to it.
I tried to reinstall GRUB but to no avail.

Do you have any idea what I should do to either:
* Reinstall GRUB properly with RAID support;
* or at least create a USB boot loader that will boot on the disk and let me get going for now.

Thanks,
Valéry

---

### Post by kbdlc on 2011-11-09
Hi Valéry,
 
Same problem here exactly... 
 
In my case, it was an **11.04** to 11.10 upgrade, mdadm using RAID 1, and I am running 32 bit not 64.
 
Each reboot after this unsuccessful upgrade results in a black screen with the cryptic message:
 
```
error: incompatible license.
grub rescue> _
```
 
 
I can boot from Live CD (and see my unmounted RAID drive sitting there looking useless). Everything was working fine under 10.04. What possessed me to finally give in to those incessant "Upgrade Now to 11.10" screen pops... :confused:
 
Thanks in advance if anyone can help - this is crippling me...
 
KB

---

### Post by arrrghhh on 2011-11-09
I'm curious, why aren't you guys keeping your **servers** on LTS releases?

Unless there's a specific reason to go to 11.10, I see no reason to upgrade my 10.04 server until 12.04 comes out.

Also, screen pops?  On a server?  :p

Do you guys boot from the RAID?  I always thought RAID was more for big volumes to prevent failures, but you shouldn't put RAID as your /boot or your 'main drive'.

---

### Post by kbdlc on 2011-11-09
Hi arrrghhh and thanks for your interest.
 
This is not a server, but rather one of my desktop machines. Personally I use Debian comand line-only on my servers and Ubuntu on my desktops.
 
I'm not sure what your comments on RAID are based on - it is a common practice to RAID all drives including boot. With the high rate of hard disk failures, it is an inexpensive way to dramatically increase reliabilty...
 
KB

---

### Post by arrrghhh on 2011-11-09
RAID on a desktop machine?  Wow.

I'm not super-experienced with PC's, but I have been building and supporting them for ~10 years.  Disks do fail, but I'd say it's fairly infrequent (assuming environmentals are good and the disk is quality) - besides, if your boot drive goes just grab a new one and reinstall... shouldn't be any personal info there anyways.

As for why I say you shouldn't put it on boot - what if for any reason the RAID fails, and you're stuck in a situation where the machine won't boot...?  Ring any bells?  ;)

---

### Post by kbdlc on 2011-11-09
Well the good news is that in this case I have not lost the contents of the disk(s) and if some other expert here can focus on the actual issue at hand and guide Valéry and I on how to troubleshoot the GRUB error that we are encountering, then hopefully we can both quickly get back up and running.
 
Any useful suggestions related to the issue as reported are very welcome   :D

---

### Post by arrrghhh on 2011-11-09
> **kbdlc said:**
> Well the good news is that in this case I have not lost the contents of the disk(s) and if some other expert here can focus on the actual issue at hand and guide Valéry and I on how to troubleshoot the GRUB error that we are encountering, then hopefully we can both quickly get back up and running.
 
Any useful suggestions related to the issue as reported are very welcome   :D

Well, I would suggest reinstalling GRUB.  The OP said that failed - why?  Details.

Edit - based on [this thread](http://ubuntuforums.org/showthread.php?p=11405131) it appears that perhaps your RAID array has fallen apart, and it's trying to boot without the array.  Unfortunately there's no resolution in that thread.

My point is still valid - if you didn't have a RAID array on your boot disks, you would not be in this situation.  I'm not trying to be a ****, or point out the obvious... but sometimes the obvious needs to be pointed out... :rolleyes:.

Edit 2 - [This thread](http://ubuntuforums.org/showthread.php?p=11407208) might help too.

Is a reinstall out of the question?  That'll fix it for sure.

---

### Post by kbdlc on 2011-11-10
Valéry,
 
I have some information that hopefully will be of help to you. The reason that I encountered the GRUB error after upgrading to 11.10 was that my RAID array was degraded. Whether it was degraded before or became degraded during the 11.10 upgrade I can't say for sure. What I can confirm is that once I restored the health of the array, my 11.10 upgrade booted normally and life is good again...
 
Rebuilding an mdadm array is easy. If you are a command line type like me, you can use mdadm commands. Note that mdadm is not typically installed as part of a Live CD, but you can install it after booting up from the Live CD.
 
```
sudo apt-get install mdadm
```
 
In my case however, I found a much easier/more intuitive way to manage the array, just go to System> Sytem Administration> Disk Utility. This graphical tool includes support for RAID arrays, and figuring out what was wrong (in my case one partition had become detached) and fixing it was very intuitive. (Took a couple of hours to rebuild a 1 TB partition).
 
Now the big question is why won't GRUB2/11.10 boot from a degraded RAID array??? This is bound to cause others grief.
 
Finally, I have added my email address after the MAILADDR parameter in the /etc/mdadm/mdadm.conf file and now I will be the first to know next time my array goes wonky...
 
Good luck,
KB

---

### Post by kbdlc on 2011-11-10
arrrghhh,
 
Your nick says it all! Perhaps you don't understand the benefits of software raid. Of course I could format the hard disk and spend an afternoon reinstalling Ubuntu and all of my applications and settings (or restoring latest backup) but that is not the point. I do however agree that hardware RAID controllers can be problematic - I have encountered a failure of a hardware RAID controller where we could not recover any of the data until we found an identical controller card.
 
mdadm is not hardware RAID though. It is software RAID - try it before you knock it. If things are working correctly you will be able to use your computer normally (including rebooting) with your boot disks setup as RAID 1 even if your array is degraded, including if one of your disks is damaged or even removed from the PC altogether.
 
The reason that Valéry and I reported this issue is that something is not working correctly with GRUB2/11.10 - GRUB errors out unexpectedly when it encounters a degraded RAID array. This was not seen using 10.04, so hopefully someone can discover why and fix it.
 
Maybe you have some ideas?
 
KB

---

### Post by kuritsubaji on 2011-11-12
Hello,

Sorry, not here to offer a solution, but merely to chime in on the benefits of RAID on a desktop machine.

While running a RAID1 array may give you a increased sense of reliability, the real plus to a RAID is increased drive speed. I've been running a RAID0 array on four 500Mb SATA drives for the past three years, and I'll never go back to the seemingly slow world of a single drive. The major drawback is that the RAID0 'wastes' quite a bit of overall space (I end up with a 1.6Tb partition), but the write speeds are around 760Mb/sec:o! Can't beat that with a stick;).

---

