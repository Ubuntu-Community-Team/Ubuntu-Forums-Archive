---
title: "Legacy graphics cards: proprietary driver hell"
date: 2013-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by R33D3M33R on 2013-05-03
I just installed Kubuntu 13.04 on various systems. One of them has AMD HD4670. It has no driver included and AMD legacy website driver doesn't support this kernel yet. I tried using a PPA, but it didn't work. I can use the Radeon driver, but a lot of cards potential is lost.

Next computer has an nVidia 6600GT. The first problem is that there are tons of drivers in the repository, which have highly misleading infos. For everyone it says:** GPUs such as Geforce 6 or newer are supported**. Really? I installed 310.44 and this was in dmesg:

```

139.823179] NVRM: The NVIDIA GeForce 6600 GT GPU installed in this system is
[  139.823179] NVRM:  supported through the NVIDIA 304.xx Legacy drivers. Please
[  139.823179] NVRM:  visit http://www.nvidia.com/object/unix.html for more
[  139.823179] NVRM:  information.  The 310.44 NVIDIA driver will ignore
[  139.823179] NVRM:  this GPU.  Continuing probe...

```

It appears only 304.xx work with this card. But do they? They provide 3D acceleration, but kill wireless and plymouth-upstart-bridge on startup. The boot takes several minutes now since the computer is waiting for network configuration, which fails at the end. This means non-root users cannot use the internet nor they can't shutdown/reboot the box normally. On the other hand noveau driver works perfectly, but again a lot of potential is lost.

I'm pretty disappointed. I knew there are problems with legacy AMD, but nVidia's problems are new to me. Ofcourse, I can install the 12.04 and both cards will probably work perfectly with proprietary drivers. 

So, what are your experiences with legacy graphics cards and their proprietary drivers?

---

### Post by codingman on 2013-05-04
NVIDIA Geforce MX3 
NVIDIA Geforce 7600 GT 

Both running fine with proprietary.

---

### Post by R33D3M33R on 2013-05-08
I just tried to install Ubuntu 12.04 on an ancient computer with Geforce 2 MX. It just dies right before the Login window is shown with 96 drivers. Also, Noveau works horrible as the terminal font at boot is few pixels big and login window crashes. No luck for me :(.

---

### Post by MadmanRB on 2013-05-08
This has always been an issue with linux, but the companies are more to blame for not opening the source code for older cards.
Honestly if the card is old why not release their source code for its drivers?
They are not making money off it anymore.

Hopefully in the near future this sort of crap will be a thing of the past.

---

### Post by R33D3M33R on 2013-05-13
Yeah, AMD is on the right path, but the performance is not there yet. As for the GF2 MX i had no other option than to install Windows XP :(.

So back to the proprietary driver situation:
I can always install Windows XP + drivers and have excellent hw acceleration + have most recent programs (this might change in years that are coming)
I can install an old Linux distribution + drivers and have hw acceleration but must compile programs myself to be up-to-date (this will probably consume tons of time)

I just don't understand why kernel and xorg updates break the proprietary drivers ...

---

### Post by mastablasta on 2013-05-13
> **R33D3M33R said:**
> 
I just don't understand why kernel and xorg updates break the proprietary drivers ...

linux has poor backward support for all programmes not just drivers. you can still install win95 programmes on widnows XP or maybe even Windows 7. we use DOS based programme (well it was made in win 3.11 era) in windows 7 (no dosbox). works fine. Not possible in linux or very difficult at best (dependencies and such).

---

### Post by QIII on 2013-05-13
The proprietors of Linux distros have exactly nothing to do with the problems encountered when using old OEM hardware when the proprietary drivers are no longer supported or maintained by the OEM -- especially when the source is not open.

Why will old drivers work in Windows? 

The graphics layer of Windows has changed very little over 30 years.

But you will certainly encounter problems if an app requires a version of Direct X that the card cannot work with.  So...  Same same.

---

### Post by mastablasta on 2013-05-14
> **QIII said:**
> But you will certainly encounter problems if an app requires a version of Direct X that the card cannot work with. So... Same same.

In linux you do not even get to that point.

If you have some 10 year old hardware with enough ram and let's say 64 bit CPU - can you install Windows 8 on it? you definatelly can windows 7, but windows 7 is now quite "old" if i am not mistaking.

so windows has old layer. but linux has only new. which makes windows work with older hw while linux usually goes medium range only. well not always. sometimes it does work on something really old.:-s

---

### Post by QIII on 2013-05-14
> **mastablasta said:**
> In linux you do not even get to that point.

It is frustrating, no doubt.

But the relationship must be understood:  Those products will not work with Linux because the OEMs have either dropped development on the drivers or have not updated them.

That is really a matter to be taken up with the OEMs whose drivers do not work with current Linux distros.  The Linux community has no power over the OEMs.  The OEMs will bow down and scrape to please Microsoft -- a smart move, since they don't want to die.  Linux doesn't have the weight of market share to do that.

Again, this is not to diminish the frustration or to say it is not a problem.  But the nature of the problem must be properly identified.

---

