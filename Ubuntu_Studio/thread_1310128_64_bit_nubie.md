---
title: "64 bit nubie"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by togo59 on 2009-11-01
I have a 64 bit AMD PC but I've always run in 32 bit mode until now. But I am tempted to go for the 64 bit version of 9.10. (Because it's there.)

I assume all the applications (e.g. LMMS, Jack, ZynAddSubFX etc) will run OK but I'm worried about my Terratec DMX6fire sound card. Will the 64 bit drivers work? (I have my doubts.)

The trouble is, this will of course be a fresh install and I will loose everything (yes I've already backed up all my files onto another disk).

The 64b Ubuntu Studio 9.10 ISO isn't a live CD, so I can't try it out -- it's all or nothing. I have a 32 bit Ubuntu live CD, which checks out OK, but I haven't created a 64 bit live CD (non-Studio version) -- maybe I should.

I don't have a partition as such because Ubuntu Studio is on a separate hard disk. Though what that has to do with anything, I don't rightly know.

Any advice would be welcome. :D

Rog.

---

### Post by lavadisco on 2009-11-23
I would also like to see the answer to this.

---

### Post by bluesscream on 2009-11-23
If you have enough free disk space I'd recommend a parallel install. It's not so hard as you might think about. The tool gparted will help you. On one of my machines I made a fresh partition only for the system files, mounted the old swap partition and applied my new user into the old home directory. So I kept full user access to my old files.

---

### Post by mango42 on 2009-11-25
> **bluesscream said:**
> If you have enough free disk space I'd recommend a parallel install. It's not so hard as you might think about. The tool gparted will help you. On one of my machines I made a fresh partition only for the system files, mounted the old swap partition and applied my new user into the old home directory. So I kept full user access to my old files.

It may not be hard and yes it's my preferred option to run parallel systems (mainly owing to video driver issues) BUT not everyone (me included) knows how to do this successfully without destroying GRUB. If one wipes a partition (including its swap file) using that truly excellent piece of programming, GParted, you end up with Grub error 22. Not a problem if you have a LiveCD but how to avoid this situation?

I have yet to fully understand how to read and write to another partition from the command line...Would you be prepared to expand on your post, bluesscream, perhaps with links to the relevant 'howto's' for us newcomers to Linux?

@togo59 - I've been running the AMD versions on my Turion-based machine since 7.10 (Gutsy Gibbon) without problems, but not as yet for UbuntuStudio64, where the biggest issue seems to be conflict between the realtime kernel and nVidia hardware.

---

### Post by bluesscream on 2009-11-26
> not everyone (me included) knows how to do this successfully without destroying GRUB
This might be a problem as long as different grub versions are on the same system. But after having successfully installed karmic (32bit similar 64bit) into  free partition(s) it's grub2 will look system wide and give access for all kernels/osses. Default boot version can be changed by editing /etc/default/grub as root in the new install. I see no need for a fall back to use the old grub, but if this might be required there is competent help in these forums.

Please forget this thing with shared use of /swap and /home, because I only tested this successfully with both 64bit installs, not with one 32bit and one 64bit.

Some links: [http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=howto+gparted](http://ubuntuforums.org/showthread.php?t=282018&highlight=howto+gparted)

> If one wipes a partition (including its swap file) ... end up with Grub error 22 had this swap before wiping it been unintendedly used by more then one install? I'm used to give swap an extra partition and use it systemwide as long as I'm not dependent of hibernate (suspend to disk), because this by default stores its informations there. These informations will be lost at reboot into another os and a fsck will be forced. But this will lead us to far away and might be discussed in other threads.

> I have yet to fully understand how to read and write to another partition from the command line... 
might become another separated thread.

> the biggest issue seems to be conflict between the realtime kernel and nVidia hardware 
for my card - old fx5200 - driver 173.14.20 is fixed. It it's not with your driver you might try this: 
[http://ubuntuforums.org/showthread.php?t=1287967](http://ubuntuforums.org/showthread.php?t=1287967)

---

### Post by mango42 on 2009-11-26
bluesscream, many thanks for your considered reply. 

I agree there are more suitable threads for my queries and I really should try and commit the gParted manual to memory - just not mine right now...;-)

---

### Post by prosigna on 2009-11-26
Could you fire up a 64-bit Ubuntu Live CD (not ubuntu studio) and see if the driver works?

---

