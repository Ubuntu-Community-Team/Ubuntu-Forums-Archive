---
title: "Kernel 3.8.0-13 boots to a black screen OR messes up resolution"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by fantab on 2013-03-18
Today I updated my 13.04. There is new Kernel 3.8.0.13.27. I ran update through "Software Updater", the update went fine and I had to restart my machine.

After restart Ubuntu booted to a black screen. I could hear the login-ready sound, after waiting for some more time I restarted again. Again Ubuntu boots to a black screen, nothing else; I typed my password on the black screen and I could hear login-successful sound. Still a black screen. I shut down my machine and rebooted with my older kernel 3.8.0-12-generic and Ubuntu boots fine.

I was wondering if any one else had similar issue with the said kernel 3.8.0.13 upon update...

---

### Post by serdotlinecho on 2013-03-18
> **fantab said:**
> Today I updated my 13.04. There is new Kernel 3.8.0.13.27. I ran update through "Software Updater", the update went fine and I had to restart my machine.

After restart Ubuntu booted to a black screen. I could hear the login-ready sound, after waiting for some more time I restarted again. Again Ubuntu boots to a black screen, nothing else; I typed my password on the black screen and I could hear login-successful sound. Still a black screen. I shut down my machine and rebooted with my older kernel 3.8.0-12-generic and Ubuntu boots fine.

I was wondering if any one else had similar issue with the said kernel 3.8.0.13 upon update...

Please share your video card model :)

```
lspci | grep VGA
```

---

### Post by fantab on 2013-03-18
Its INTEL G45 integrated Graphics. :)

---

### Post by JMB74 on 2013-03-18
There were a few bad commits in 3.8.3 which that kernel is based on. Some people reporting the same thing as you as a result.

There is a new raring kernel building now that reverts those changes.

[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-13.23](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-13.23)

---

### Post by Harry33 on 2013-03-19
> **fantab said:**
> Today I updated my 13.04. There is new Kernel 3.8.0.13.27.
...

Your kernel numbering is incorrect. Perhaps you meant 3.8.0-13.22.
The newest (as of today) kernel is 3.8.0-13.23.
Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-13.23](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-13.23)

---

### Post by fantab on 2013-03-19
Kernel numbering is correct AFAIK.
 [https://launchpad.net/ubuntu/+source/linux-meta/3.8.0.13.27](https://launchpad.net/ubuntu/+source/linux-meta/3.8.0.13.27)


... see the attached screenshot of Synaptic.


[ATTACH=CONFIG]240337[/ATTACH]

---

### Post by dino99 on 2013-03-19
You does not boot with meta-package (linux-image), but with the related image (which is not the same numbering, as said by Harry above)

---

### Post by djuliette on 2013-03-19
I had a similar problem with intel integrated graphics.  With the new kernel my laptop boots into an incorrect resolution and when I go to settings it won't detect the proper resolution. Booting to a previous kernel works fine though.

---

### Post by dino99 on 2013-03-19
you might report such kernel bug regression  (ubuntu-bug linux)

---

### Post by fantab on 2013-03-19
> **dino99 said:**
> You does not boot with meta-package (linux-image), but with the related image (which is not the same numbering, as said by Harry above)

Thanks **dino99** for the clarification. However, I don't have Kernel 3.8.0-13.23 in my Synaptic but the Meta-Package 3.8.0.13.27 including linux-generic (complete) 3.8.0.13.27.


[ATTACH=CONFIG]240339[/ATTACH]

---

### Post by JMB74 on 2013-03-19
> **fantab said:**
> Thanks **dino99** for the clarification. However, I don't have Kernel 3.8.0-13.23 in my Synaptic but the Meta-Package 3.8.0.13.27 including linux-generic (complete) 3.8.0.13.27.




3.8.0-13.23 hasn't finished building for all architectures yet, and it won't hit the main repos and show up in synatptic until it does.

3.8.0.13.27 is a meta package. It's not an actual kernel. Forget about that. It has a slightly different numbering scheme to the actual kernel to allow upgrades to be pulled in on a dist upgrade.

---

### Post by philinux on 2013-03-19
Reverting to 3.8.0-12 I get my correct display. 1366 x 768.

The max I can get with 3.8.0-13 is 1024 x 768.This is an acer aspire 1410.

Anyone else get this? Before I raise a bug.

---

### Post by dino99 on 2013-03-19
If your graphic is related to nvidia, then that bug is about a broken link installation:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-310/+bug/1157120](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-310/+bug/1157120)

---

### Post by philinux on 2013-03-19
Cheers Dino but not nvidia.

Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by macstevejb on 2013-03-19
I can confirm this behaviour with my laptop with onboard Intel graphics.

Resolution defaults on boot to 1024x768 in both in GDM and desktop.

Only happened after updating to Kernel 3.8.0-13.

If I revert to older kernel, the problem disappears.

---

### Post by scradock on 2013-03-19
launchpad bug #1156130

---

### Post by philinux on 2013-03-20
Solved for me now this morning with update to 3.8.0-13.

---

### Post by macstevejb on 2013-03-20
Ditto.

3.8.0-13.27 to be precise.

:p

---

### Post by Harry33 on 2013-03-20
> **macstevejb said:**
> Ditto.

3.8.0-13.27 to be precise.

:p

No, that is the version number of a simple meta package, not the kernel. :guitar:

---

### Post by philinux on 2013-03-20
> **macstevejb said:**
> Ditto.

3.8.0-13.27 to be precise.

:p

As Harry says above.

It's >
linux-image-3.8.0-13-generic:
  Installed: 3.8.0-13.23
  Candidate: 3.8.0-13.23

---

### Post by macstevejb on 2013-03-20
Agreed...I stand corrected! 

;)

---

### Post by Ibrahim717 on 2013-03-20
I was having the same issue with my intell 4500 graphics card. The screen isn't black it is just that the back light is off....I can still see the images if I put a flashlight then the screen, then I have the run the setpci script a turn the backlight back on....  When first installing  13.04 I had all sorts of issues with the backlight and I modified the grub and create a file to fix these issues however after installing the update all those changes went away.. I had to do an install from my original CD and then do all then up dates first then after that make my modicatations. I still cant get the boot command to workm as far as running the setpci script that i put in the local file, however the backlight does come on out of suspend mode (so I just make sure I suspend rather then shut it down). See my Original thread 

[http://ubuntuforums.org/showthread.php?t=2123750&page=2](http://ubuntuforums.org/showthread.php?t=2123750&page=2)

---

### Post by Ibrahim717 on 2013-03-20
> **philinux said:**
> Reverting to 3.8.0-12 I get my correct display. 1366 x 768.

The max I can get with 3.8.0-13 is 1024 x 768.This is an acer aspire 1410.

Anyone else get this? Before I raise a bug.



Yes .. Same deal ACER aspire 5746-4460

intel chipset 4500

see thread ... And I havent seen a bug report but a few other ACER owners have had this issue and other similar..see thread 

[http://ubuntuforums.org/showthread.php?t=2123750&page=2](http://ubuntuforums.org/showthread.php?t=2123750&page=2)

---

### Post by cariboo on 2013-03-20
If there isn't a bug report, why haven't you created one. After all, that's what we are here for.

---

### Post by fantab on 2013-03-21
I confirm that the latest update has fixed the 'black-screen' issue for me. 

However, after reading #22 and on a second thought, it was not just a 'black screen'... actually the display was being put in standby mode after the kernel boot earlier.
My new kernel 3.8.0.13.23, after update boots fine. No issues so far.

---

### Post by Ibrahim717 on 2013-03-24
> **cariboo907 said:**
> If there isn't a bug report, why haven't you created one. After all, that's what we are here for.



I've only been doing this (Ubuntu thing) for a few weeks. I didn't know how to file a bug report.

---

### Post by kevpan815 on 2013-03-24
Try Updating to Today's Build, it contains 3.8.0.14!

---

### Post by cariboo on 2013-03-24
> **Ibrahim717 said:**
> I've only been doing this (Ubuntu thing) for a few weeks. I didn't know how to file a bug report.

Reporting bugs is pretty simple, first you need a [launchpad account]("https://login.launchpad.net/+new_account"), then when you want to report a bug, like in this case, open a terminal and type:

```
ubuntu-bug linux
```

For more helpful info, check out my [sticky]("http://ubuntuforums.org/showthread.php?t=2073477"), located at the top of the first page of this sub-forum.

---

