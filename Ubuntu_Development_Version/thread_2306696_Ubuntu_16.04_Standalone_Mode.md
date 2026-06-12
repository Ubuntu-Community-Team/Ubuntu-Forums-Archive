---
title: "Ubuntu 16.04 Standalone Mode"
date: 2015-12-17
forum: Ubuntu Development Version
---

### Post by mikeincousa on 2015-12-17
I've been running 15.04 and 15.10 without an Internet connection.

I upgraded to 16.04, using a temporary connection to the web

Now on restart I cannot get past the splash/ polling page.

Is there any way to run 16.04 without an Internet connection? AKA Standalone.

If so how?

How can I get past the splash/ polling screen?

Thanks.

---

### Post by QIII on 2015-12-17
*Moved to **Ubuntu Development Version***

---

### Post by yancek on 2015-12-17
Since 16.04 won't actually be released for four months, by installing it you have volunteered to test a development version.  You can't expect a pre-release version to work well, that's the reason for testing.  Yes, you can use Ubuntu or any Linux system without an internet connection.  Did you reboot after you installed with your temporary internet connection to test it?

---

### Post by deepakdeshp on 2015-12-17
Ubuntu 14.04 is the LTS version which will have updates available till 2019. Hence it is advisable to install this version.

---

### Post by mikeincousa on 2015-12-20
I have not been using Linux very much of late. 
Whenever I have a need to go there I always plug that box directly into the modem. 
Then I run apt-get dist-upgrade. 
It seemed odd to me that I ended up with 16.04, but did not give it a thought. 
Guess I missed something in the process and my haste?

Whatever. 

I may have rebooted on finishing, but I cannot say for sure. 

This machine does not have a DVD drive and I do not have one I can port over. I  would prefer not to add one to it at this point.

Is it possible to now roll 16.04 back to 15.10 without a reinstall?

Any other easy way out?

---

### Post by deadflowr on 2015-12-20
> [COLOR=#000000]Is it possible to now roll 16.04 back to 15.10 without a reinstall?[/COLOR]
No, or at least not in anyway where anyone can fully guarantee it will in anyway function properly. 

> [COLOR=#000000]Any other easy way out?[/COLOR]
Yes, keep running periodic updates.
You have a 90%+ chance of fixing your current issues by simply keeping up with the Jones'.

---

### Post by sudodus on 2015-12-20
It is often easiest to save all personal files to another drive, and after that re-install. It is not possible to roll back after upgrading to a new version. Maybe you could do it with a lot of tweaking, but it would take ten times or more effort and time compared to a re-install. (I would never do it.)

-o-

If your computer is less than 12 years old, it can probably boot from a USB drive instead of booting from DVD. So you can clone your iso file to a USB pendrive and boot that way to re-install.

If you tell us details about your computer, we can give more detailed advice:

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by grahammechanical on 2015-12-20
We should not need an internet connection to get to a working desktop. This command will not upgrade to the next release of Ubuntu

```
sudo apt-get dist-upgrade
```

It will only upgrade the existing install by downloading and installing held back packages. It will avoid package conflicts by removing packages if necessary. So, with dist-upgrade there is always a possibility (small with released versions) of something breaking). This is the command that will upgrade 15.10 to 16.04 development version.

```
sudo do-release-upgrade -d
```

It is the -d switch that upgrades to development version. Are you sure that you are on Xenial Xerus? If you upgraded from 15.10 there should still be at least one kernel from 15.10 available. And we can select, at the Grub boot menu, Advanced options for Ubuntu and then select an earlier kernel. That may get us to a working desktop. Or

At the Advanced options sub-menu we can select recovery mode and at the recovery menu select Resume. That may get us to a working desktop. You may need to use Additional Drivers to select another video driver. That will require an internet connection and a little patience while the utility looks for appropriate proprietary video drivers.

If you can get Xenial Xerus working as a stable OS you will need to update to convert it into the released version of 16.04. But you do not need to do that every day as some of us do.

Regards.

---

### Post by mikeincousa on 2015-12-23
Thanks for all the comments and thoughts. 

All very informative.


It sounds like keeping up with upgrades is the first place to start.

Stay tuned for late breaking news! :)

---

### Post by mikeincousa on 2015-12-25
I updated. Rebooted. Shutdown. Unplugged the Internet connection. 

It took a bit over six minutes for the poling to stop and get to the login screen. (Older machine, FYI).

Next i repeated the start up with the box plugged into the Internet: that way,  about a minute and half  minutes from power on to log-in. 

This echoes my experiences with 14.10, but not 15.10.

Otherwise it looks everything I was running under 15.10 will work, but i did not go too deep.

Only problem now is the extra time to get going, a minor one.

I'll  try the GRUB kernel selection path mentioned about next. Curious. 


A different track.
Once I had it running I tried to install a IPA Keyboard (my immediate goal), but that bombed. 
I suspect a package error. I'll put up the error separately.

But maybe this install is an OS problem? 

If someone could point me to touch-type IPA keyboard for Ubuntu 15.10 or 16.04 please feel free direct me to a solution.

Thanks again.

---

### Post by ventrical on 2015-12-25
You said 'older hardware' . Can you tell us how old and what type of graphics adapter?
Thanks.

---

