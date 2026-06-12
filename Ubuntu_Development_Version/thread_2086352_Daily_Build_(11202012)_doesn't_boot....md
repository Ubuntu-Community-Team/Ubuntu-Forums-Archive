---
title: "Daily Build (11/20/2012) doesn't boot..."
date: 2012-11-20
forum: Ubuntu Development Version
---

### Post by sgage on 2012-11-20
Well, I thought it was about time to check out the status of RR these days, so I installed today's build. It doesn't boot to Unity - just the wallpaper and a cursor. 

I can't get to a virtual terminal, I can't boot in FailsafeGraphics mode, I can't load the network or boot to root from Rescue mode.

Any tricks I could try? Or is it just one of those things?...

---

### Post by mc4man on 2012-11-20
If you have nvidia then you **may** be affected by nouveau/kernel bug as mentioned here
[http://ubuntuforums.org/showthread.php?t=2085800](http://ubuntuforums.org/showthread.php?t=2085800)
I've worked around here by patching & rebuilding the kernel .debs, ect.

---

### Post by sgage on 2012-11-20
> **mc4man said:**
> If you have nvidia then you **may** be affected by nouveau/kernel bug as mentioned here
[http://ubuntuforums.org/showthread.php?t=2085800](http://ubuntuforums.org/showthread.php?t=2085800)
I've worked around here by patching & rebuilding the kernel .debs, ect.

Thanks for the pointer - it seems to have been my issue. I chrooted my RR installation and installed nvidia-current, and she came right up.

---

### Post by mc4man on 2012-11-20
If more users/hardware seem to be affected then I'll comment in my bug that some consideration should be given to patching 3.7rcX. 
As it stands they seem content to just wait until it shows up in the kernel source which may be some time. Until then users will need to find a way to get nvidia-* installed to get a login, ect.
For reference current bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080389)

---

### Post by sgage on 2012-11-20
> **mc4man said:**
> If more users/hardware seem to be affected then I'll comment in my bug that some consideration should be given to patching 3.7rcX. 
As it stands they seem content to just wait until it shows up in the kernel source which may be some time. Until then users will need to find a way to get nvidia-* installed to get a login, ect.
For reference current bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080389)

I added a "me too" to the bug...

---

### Post by mc4man on 2012-11-20
> **sgage said:**
> I added a "me too" to the bug...
Thanks
If you have a chance note what nvidia card you have
(either here or bug

---

### Post by OGpmpdog on 2012-11-20
> **mc4man said:**
> Thanks
If you have a chance note what nvidia card you have
(either here or bug

Hi!!

Yes, I am also affected...I unsuccessfully tried to fresh install last night.

My cards (dont laugh):)
1) GS-8400
2) GT-210 

chroot??..hmmm, I'll try that 1st, since I havent dared much breakage lately.  Thanks!!

---

### Post by sgage on 2012-11-20
> **mc4man said:**
> Thanks
If you have a chance note what nvidia card you have
(either here or bug

My card is a GeForce 8500 GT.

---

### Post by ronacc on 2012-11-21
add myself to the bug , my card is a 7600gs

---

### Post by mc4man on 2012-11-21
> **ronacc said:**
> add myself to the bug , my card is a 7600gs
Good - there more adapters affected then a bit more chance the fix will show sooner than later.
Currently it's implied that whenever it shows it does, till then do workarounds.

(it's a pretty simple patch to fix that's shown no ill effect here though I don't look that deep..

---

### Post by P-I H on 2012-11-21
I have a Geforce GTX 660 and a Geforce GTS 250, both are affected.
I also added "me too" to the bug.

---

### Post by dino99 on 2012-11-21
> **mc4man said:**
> If more users/hardware seem to be affected then I'll comment in my bug that some consideration should be given to patching 3.7rcX. 
As it stands they seem content to just wait until it shows up in the kernel source which may be some time. Until then users will need to find a way to get nvidia-* installed to get a login, ect.
For reference current bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1080389)

it should be usefull to directly send your experiments & details  to the maintainer  (bskeggs@redhat.com)

---

### Post by mc4man on 2012-11-21
There is now a test kernel for raring, (& some indication that the commit to fix will make 3.7 kernel.
If not & people report that the commit fixes then it will be likely patched into raring kernels in the meantime.

[http://people.canonical.com/~jsalisbury/lp1080389/](http://people.canonical.com/~jsalisbury/lp1080389/)

What's to be tested is if after installing above kernel can one log in to Unity & or GS while using the **nouveau** driver

(the commit works here self built though will try jsalisbury's kernel. It is taking some amount of seconds from greeter to functional Desktop though that's nothing new on my aging & hopefully soon gone laptop..

---

