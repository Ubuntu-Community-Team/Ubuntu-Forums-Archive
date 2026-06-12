---
title: "Raring is stable/fast"
date: 2013-03-17
forum: Ubuntu Development Version
---

### Post by Rukiri on 2013-03-17
Now, the installer for one needs a overhaul as it's just outright slow (Windows 8 installs faster actually windows 8 install in less than 5 minutes on my system) but it takes 5 minutes just to get to the partitioning screen...  I've heard it's been a long time issue, and I should have just partitioned with disk management but I got through it... fix it!

But now that I'm in my system I gotta say it's stable! but I don't want to try the nvidia drivers knowing that I'm on kernel 3.8 as I've know there were issue for a long time which still are not fixed to my knowledge.

I actually find 13.04 more stable than 12.04... no joke.

---

### Post by dino99 on 2013-03-17
318.26 works flawlessly  :P

---

### Post by Harry33 on 2013-03-17
RR beta1 is perhaps ATM stable.
However, it was not just the other day, when booting ended up in busybox shell due to issues with initramfs-tools and the new udev + systemd.
It is a good practice to remember a development version may break anytime. :guitar:

---

### Post by cole.mickens on 2013-03-17
> **dino99 said:**
> 318.26 works flawlessly  :P

Are you talking about nvidia-318.26 ?

---

### Post by cariboo on 2013-03-17
I'm running nvidia-current (304.84) here without any problems on kernel 3.8.0-13

---

### Post by VinDSL on 2013-03-17
> **cariboo907 said:**
> I'm running nvidia-current (304.84) here without any problems on kernel 3.8.0-13
I've run nVidia 304.84 (the past few days) without any problems on Kernels 3.7/3.8/3.9...

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
  Installed: 304.84-0ubuntu2
  Candidate: 304.84-0ubuntu2
  Version table:
 *** 304.84-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ echo -n "Kernel Release: " || cat /etc/*release && uname -s -r
Kernel Release: Linux 3.9.0-030900rc3-generic

```

---

### Post by crepito on 2013-03-18
I find 13.04 pretty usable. 
I never used dev branches before but i was tired of the old 12.04 feel and 12.10 was jerky on my machines. 
One of the things that i find bad, related with previous releases, is the shutdown process. In 12.04 the shutdown was instantly and in 13.04 takes a while.

---

### Post by wribeiro on 2013-03-18
13.04 is really great!! 
Unfortunately I am experiencing many serious issues related to nvidia driver with my geforce 630m that were happening before with 12.10.

---

### Post by handsheldhigh on 2013-03-18
Loving Raring on both my machines. Very speedy and stable. Raring's working on my AMD C-70 netbook which it previously did not work well on (no brightness settings, etc)

---

### Post by PJs Ronin on 2013-03-18
Tonight I intend to clone my production system (12.04LTS) on to a new hard drive which I will then upgrade to 13.04.   Yep, I be impressed with Raring.

---

### Post by Baldrick_NZ on 2013-03-18
Yeah, I have to say that Raring is shaping up to be the best Ubuntu yet. Although I must admit I'm not paying too much attention to Unity this time around. My attention has definitely swung to Gnome3. I still like Unity, but I feel I can do more with Gnome3.

All three of our lappys are now on Raring, Gnome3. Even the missus likes it better than both Unity & Windows. 

Funny thing is, we bought a new laptop last week, installed Ubuntu on it as dual boot, and haven't even used the Windows7 part yet!!

Loving the stability of it!

---

### Post by jerrylamos on 2013-03-19
> **PJs Ronin said:**
> Tonight I intend to clone my production system (12.04LTS) on to a new hard drive which I will then upgrade to 13.04.   Yep, I be impressed with Raring.
I've had good luck with Clonezilla on Windows.  For ubuntu I tend to just do an install.  I back up all my changes to an Archive partition and have a semi automated setup exec to get the new one going.  That said, I don't use a whole lot of customization........recently had to do a mad scramble to recover partitions when I accidentally screwed up /dev/sda......don't do that.

---

### Post by Cavsfan on 2013-03-19
I'm running nvidia-310-updates - 310.32 and have not had any problems. Raring is way more stable than Quantal ever has been.

---

### Post by Cavsfan on 2013-03-19
Just upgraded to 313.26 myself and it runs slick. I'll have to admit that I was just in Unity long enough to install Gnome fallback. :tongue:

---

### Post by Rukiri on 2013-03-19
Don't even bother with Gnome fallback it's removed in 3.8, use mate or xfce if you want a 2 panel layout or get used to cinnamon.

---

### Post by Cavsfan on 2013-03-20
> **Rukiri said:**
> Don't even bother with Gnome fallback it's removed in 3.8, use mate or xfce if you want a 2 panel layout or get used to cinnamon.

Oh Noz! Next you'll be telling me Cairo Dock is removed. So, 13.04 ends gnome classic/shell/fallback as we knew it?  :(

---

### Post by Cavsfan on 2013-03-20
Whilest I did not use the gnome 3 ppa and I just receive regular updates, I do believe the close button on windows stopped working. I click on it and it just gets dark. 
I have to right click on the object in the bottom panel (thank goodness for gnome fallback) and click close or it will never close.

---

### Post by jerrylamos on 2013-03-20
Hopefully U+1 gets more stable as release approaches - I have had crashes at Beta 2, RC, and even release in the past.

I didn't do measurements but I had Meerkat up yesterday and it was running nice and fast.  When unity first appeared it was my opinion slow, seems to be a lot more usable now, however there are more Unity gew gaws coming hopefully not in the main line code.

When 2D worked I ran it in preference to 3D.  I'm running Unity 3D right now since I look for bugs in whatever Ubuntu throws over the fence with a rock tied to it.

---

### Post by Cavsfan on 2013-03-21
I installed lxde. Couldn't purge that fast enough! Logged into Unity and all seemed to work well. Noticed that because of the Unity bar being there you have less screen room than with Gnome Fallback which is kind of a no brainer.

What is Openbox? I tried Gnome/Openbox and it was like fallback without the top and bottom panels. Good thing I have Cairo Dock or I would not have access to logout, restart, apps, etc.

Then I tried Openbox and the screen blanked and came back to the login screen. So, I am back to fallback and the close buttons are back to not working.

[[IMG]http://ompldr.org/taHU2Nw[/IMG]]("http://ompldr.org/vaHU2Nw/raring login options2.jpg")

Raring is MUCH more stable than Quantal as far as compiz not working very much. I could not get Emerald installed in Raring using the same instructions that worked on Quantal, since it does not come from a repo.

If fallback is going away, I wonder why I got updates for it today. :P

---

### Post by zika on 2013-03-21
> **Cavsfan said:**
> If fallback is going away, I wonder why I got updates for it today. :PIt probably came from Gnome3PPA... Maybe it will survive but my fear is stronger than hope...

---

### Post by Rukiri on 2013-03-21
For those that liked gnome classic AKA Gnome 2, XFCE4.12 will start slowly moving to GTK+3 and mate will be porting to gtk3 soon as well.  I actually find Unity more productive than Gnome 2 but that's just me some may argue. 

If you liked the Gnome 2 layout (2 panels) I'd probably go for XFCE4 or Mate, both will eventually use GTK3 as they can't stay in GTK2 land forever...

---

### Post by Cavsfan on 2013-03-22
> **zika said:**
> It probably came from Gnome3PPA... Maybe it will survive but my fear is stronger than hope...

I have not installed the Gnome3PPA on this install. The only PPAs I have added are the Launchpad PPA for xorg crack pushers and the one for Opera.

[http://www.webupd8.org/2013/03/gnome-38-beta-available-in-ppa-for.html](http://www.webupd8.org/2013/03/gnome-38-beta-available-in-ppa-for.html)

If 3.8 is supposed to be released with Raring, I wonder why the above site says this:

"A while back, it was decided that Ubuntu 13.04 Raring Ringtail will ship with GNOME 3.6 for the most part instead of GNOME 3.8."

Also wondering why none of the 3 window buttons work - min, max and close...

---

### Post by roly33 on 2013-03-22
I've Installed a daily build of 13.04 that I downloaded yesterday this morning and found the Installer faster than 12.10, but the Install its self seems to take an age.

Once Installed I find it stable and fast and since upgrading to a Kodak esp1.2 Wireless AIO Printer found it so much simpler to setup the Printer than when I last tried Ubuntu with the old Canon Pixima AIO Printer.

Roland

---

### Post by Cavsfan on 2013-03-22
The button do not work in gnome fallback but, they do work in Unity. Guess I'll deal with Unity for now.

EDIT: I take that back. The window buttons do not work all the time even in Unity. They don't work at all in GF.

---

### Post by flourg on 2013-03-25
Raring is excellent so far, running a lot better than 12.10 on my ACER 5542g laptop. A bit speedier and more responsive.

---

### Post by tjeremiah on 2013-03-25
it seems fast but couldnt get Realtek wireless driver to work with 3.8 kernel so I had to reinstall 12.10 for the time being.

---

### Post by Frogs Hair on 2013-03-25
I Just installed  and Unity,  XFCE and the Gnome shell are up and running as well as 12.10 .

---

### Post by Rob Sayer on 2013-03-26
I'm downloading the kubuntu beta install as I write this.  Tried alpha 2 on my netbook but the driver for my broadcom 4313 wireless was glitchy and installing the proprietary driver borked the wireless.  Otherwise it worked very nicely.  Until the 2nd update.  I don't have the linux recovery skills to deal with it.

Frankly, I'm a bit surprised I installed an alpha OS.  I won't usually install beta app software.  But my Acer netbook has the notorious atom 2600/cedarview graphics.  It's actually running mint 13 kde because mint kde comes with an older kernel versaion.  You can install the cedarview driver packages through synaptic.  It's much easier.

However, the kernel is being held at 3.2.0-23-generic.  This is causing other problems.  This kernel version doesn't work 100% well with my HDD controller.  It hasn't failed but it's a bit slow.

And I'm not convinced the wireless works quite right either.  It works very poorly on marginal wifi networks (not signal strength, they're not maintained well or use cruddy routers).

So I figure a decently working beta should work as least as well as a compromised stable setup.  Here's hoping ...

---

### Post by Rob Sayer on 2013-03-27
Just tried the live usb of beta kubuntu.  Wireless still acts off.  Trying to install proprietary broadcom 43xx driver borked it.

When I rebooted into mint 13 kde the wireless was having trouble configuring the router.  Shut it off for a few minutes and it worked fine.  Apparently the open source driver doesn't handle power management correctly for the broadcom 4313.  I need the proprietary driver.

At this point I'm seriously considering installing kubuntu 12.04 lts and writing/finding a shell script for changing the brightness.  I don't use this netbook to  play video on anyway so I don't care if the video performance is 100%.

---

### Post by cariboo on 2013-03-27
@Rob Sayer , how are you installing the proprietary driver? I've had great luck just installing from the files included in the iso, from the command line.

---

### Post by cactus john on 2013-03-28
Installed it last night on a HP NC6220. Everything is rockin' and haven't had one problem as of yet.
It's not so much as that I am amazed on the OS, but more amazed on how well this old laptop runs it.

---

### Post by kevpan815 on 2013-03-28
NOT TRUE. KERNEL 3.9 is a Joke! All it does is Lock Up Over and Over Again!

---

### Post by VinDSL on 2013-03-29
> **kevpan815 said:**
> NOT TRUE. KERNEL 3.9 is a Joke! All it does is Lock Up Over and Over Again!
Are you experiencing hard_locks, or is it just lagging out on you?

I've noticed, when I first turn my machine on, in the morning, it lags out when it does an auto_aptget_update.

Seems like the auto_update has a mind of its own, and it can initiate itself at the most inopportune times...

---

### Post by matt_symes on 2013-03-29
> **kevpan815 said:**
> NOT TRUE. KERNEL 3.9 is a Joke! All it does is Lock Up Over and Over Again!

I'm not seeing any lockup or lag with 3.9.0.rc4.

```

matthew-S206:/home/matthew/Music % uname -r
3.9.0-030900rc4-generic
matthew-S206:/home/matthew/Music %
```

Anything in your logs ?

---

### Post by philinux on 2013-03-29
> **kevpan815 said:**
> NOT TRUE. KERNEL 3.9 is a Joke! All it does is Lock Up Over and Over Again!

Mmm. My raring is fully up to date and it's using kernel 3.8.0-15, 3.9 is **rc4**. That's why it's out for testing.

Just report the bugs. It could be hardware specific in your case.

---

### Post by kevpan815 on 2013-03-29
After the system has been on for a little while it loses the WIFI connection to my Apple IPhone 5 forcing my to reset the Internet Connection, wait a little while longer and not only does it DIE again but this time both the Keyboard and the Mouse locks up too AND then the System Fan Turns on at High Speed. FYI.

---

### Post by cariboo on 2013-03-29
@kevpan815, I'd suggest you install the openssh-server on the system that locks up, so that you can try and access it from another system when it locks up. The reason for doing this is to see if there is anything in the logs that could indicate what the problem is.

If you are unsure how to setup ssh, have a look at the [openssh-server wiki page]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html").

---

### Post by ping-wu on 2013-03-29
Yes, Raring definitely appears to be evolving as the best distro ever.  It is indeed very difficult to believe that this is not even an RC yet.  Many bugs were quickly exterminated through nightly updates and regressions are few in between.

---

### Post by kevpan815 on 2013-03-29
Cariboo907, that is NOT going to be possible at the moment because Sprint Suspended my Apple IPhone 5 Personal Hotspot for using too much Data Overnight Last Night Chicago Time Zone! I had to take the Computer over to Starbucks just so I could Update using the Command Line. I should also note that I removed 3.9 RC4 Last Night by Clean Installing Yesterday's Proposed Build of 13.04, the Machine was too Unstable to leave it as it was!

---

### Post by kevpan815 on 2013-03-29
I should also note the Lockups occur with the 3.9 Nightly Kernels as well. I should also note that even though Sprint is Unlimted for the Phone itself, it looks like they strictly Enforce the 6 GB Limit for their Personal Hotspot! :-(

---

