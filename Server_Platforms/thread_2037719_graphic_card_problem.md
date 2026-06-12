---
title: "graphic card problem"
date: 2012-08-05
forum: Server Platforms
---

### Post by satimis on 2012-08-05
Hi all,

Ubuntu 12.04 server 64bit, newly installed.
$ lspci | grep VGA```

07:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev al)

```

On booting it popup:```

error: fd0 read error

```

after a while it continued to boot with white rectangle blocks displayed on screen.  Text scrolling couldn't be read.  After booting finished I can login.  But the characters were tiny, very small.


Disable floppy drive on BIOS
and
Installing nvidia-current

didn't help, even becoming worser.  A white screen with symbols, such as ( { ) } etc were displayed finally.


I have to start at booting;
Recover mode
-> Resume normal boot

Then finally I can read normal size characters on screen.

I suppose it is the problem of nVidia driver.  Please help how to sort out the problem.  TIA

B.R.
satimis

---

### Post by trundlenut on 2012-08-05
Could this be a problem with the monitor and graphics card?  Do you have another monitor you could try?

---

### Post by robbie 348 on 2012-08-05
*I  had a similar problem in Linux mint 12 after enabling nvidia driver*. Went to additional drivers,de-activated the driver and all was OK.

---

### Post by satimis on 2012-08-05
> **trundlenut said:**
> Could this be a problem with the monitor and graphics card?  Do you have another monitor you could try?
There is no problem on the monitor and graphics card.  I have another hd running Debian 6.0.5 desktop 64bit.  There is no problem either at booting or after boot up.

I recall that this hd was previously running Ubuntu 12.04 desktop. It also had problem at booting with white screen displayed. Text scrolling could not be read. But there was no problem after boot up. I didn't need installing the nVidia driver.

(remark: only one hd is connected each time)

B.R.
satimis

---

### Post by satimis on 2012-08-05
> **robbie 348 said:**
> *I  had a similar problem in Linux mint 12 after enabling nvidia driver*. Went to additional drivers,de-activated the driver and all was OK.
Hi,

This is Ubuntu 12.04 server without GUI.

B.R.
satimis

---

### Post by trundlenut on 2012-08-06
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1387542") thread and [this]("http://askubuntu.com/questions/29328/how-do-i-increase-the-text-size-of-the-text-on-a-console") one.

---

### Post by satimis on 2012-08-06
> **trundlenut said:**
> Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1387542") thread and [this]("http://askubuntu.com/questions/29328/how-do-i-increase-the-text-size-of-the-text-on-a-console") one.
Thanks for your links.  Unfortunately none of the suggestions there solved my problem.

I have wiped out the hd and reinstall Ubuntu 12.04 server, 64bit.  Problem still remains.  I also tested installing it on another hd without any breakthrough.

I have to start "recovery mode" -> "resume normal boot".  Then it works without problem, text scrolling and with normal size fonts displayed after boot up.   I also tested installing Ubuntu 12.04 desktop, 64bit.  Text scrolling at booting still had problem, only symbols on white screen.  But the OS worked normally after boot up.

However Debian 6.0.5 desktop, both 32 and 64bit, works without problem on this box.

It looks very strange to me.

B.R.
satimis

---

### Post by satimis on 2012-08-07
Hi all,

Problem has been solved through pain and difficulty.


Steps performed as follows;

1)
Change the nVidia vedio card
Now;
# lspci -v | grep VGA```

07:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV610 video [Radeon HD2400 PRO] (prog-if 00 [VGA controller])

```

2)
Edit /etc/default/grub
as follow:
GRUB_GFXMODE=800x600
GRUB_CMDLINE_LINUX_DEFAULT="915.modeset=0 nomodeset"

$ sudo update-grub
$ sudo reboot

Now no white screen on text scrolling.  The fonts on the screen are easy to read, not so tiny as before.

I suppose there is a conflict of nVidia driver and Ubuntu 12.04.  Debian 6.0.5 is running on this box on previous video card with nVidia chip without problem.

Thanks

B.R.
satimis

---

### Post by trundlenut on 2012-08-07
If it is the nomodeset option that works then it is a kernel modesetting problem which caused your issues.  I think you should be able to remove the 915.modeset=0 option.

---

### Post by satimis on 2012-08-07
> **trundlenut said:**
> If it is the nomodeset option that works then it is a kernel modesetting problem which caused your issues.

How to correct it?  Wait for another kernel


> 
I think you should be able to remove the 915.modeset=0 option.
Yes.

"nomodeset" works

Thanks

B.R.
satimis

---

### Post by trundlenut on 2012-08-07
> **satimis said:**
> How to correct it?  Wait for another kernel



Yes.

"nomodeset" works

Thanks

B.R.
satimis

I would just live with it.  You don't have a gui so you don't really need the extra bells and whistles of the propriety driver.

The 915.modeset relates to intel graphics I think, so you don't need it.

---

