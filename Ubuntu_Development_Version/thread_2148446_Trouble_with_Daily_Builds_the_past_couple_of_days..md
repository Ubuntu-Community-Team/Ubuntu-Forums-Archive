---
title: "Trouble with Daily Builds the past couple of days..."
date: 2013-05-25
forum: Ubuntu Development Version
---

### Post by sgage on 2013-05-25
I've been trying to make a new install of Saucy, but the Daily Builds of the past few days haven't been working for me. The plymouth splash comes up, the dots churn around for a while and then it fails with the error message 'unable to find a medium containing a live file system'.

This is the 64-bit iso - perhaps I'll give 32-bit a try. I used unetbootin to make a USB as I have been doing for years without a problem.

Is anyone else running into this? Any insights/workarounds?

TIA

---

### Post by craig10x on 2013-05-25
I had that problem on the daily builds of 13.04 when i was going to first install it during development a few months ago...later in the cycle they started to work properly, and the live isos of 13.10 were also working properly until now...

Try this (this worked for me when they were bad) as soon as the plymouth splash comes up, don't wait for the dots to appear...immediately hit your enter key which should bring up the language screen and then press any key and you should get a selection that asks you if you want to go to live session or install...i would select live session first, then it should go into the live session and install from there...

I'd be curious to know if this works for you...let me know...and this should work with the 64 bit iso, so try that first...

---

### Post by grahammechanical on 2013-05-25
I also had this from the first days of the Raring cycle. It was months before I could get a Raring daily image that would run a live session. I tried all sorts, even ticking every F6 option. That worked but very slowly. I still have a Raring DVD that I marked with acpi=off and irqpoll to boot parameters. Making those two changes was the only way I could a Raring image to load to a live session for months.

Regards.

---

### Post by VMC on 2013-05-25
This is one of those "its your hardware issues". I have been able to run the livecd and install into my system. See my hardware below. Usually I'm just the opposite, and can't install.

edit: also, I'm zsync'ing to this amd64 : "http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-amd64.iso.zsync"

---

### Post by ventrical on 2013-05-25
> **sgage said:**
> I've been trying to make a new install of Saucy, but the Daily Builds of the past few days haven't been working for me. The plymouth splash comes up, the dots churn around for a while and then it fails with the error message 'unable to find a medium containing a live file system'.

This is the 64-bit iso - perhaps I'll give 32-bit a try. I used unetbootin to make a USB as I have been doing for years without a problem.

Is anyone else running into this? Any insights/workarounds?

TIA


Yep .. it's foobared on one of my ATi sets. A first time for me!! This olde workhorse has never failed with <nomodeset>.

same error message.

---

### Post by sgage on 2013-05-25
> **craig10x said:**
> I had that problem on the daily builds of 13.04 when i was going to first install it during development a few months ago...later in the cycle they started to work properly, and the live isos of 13.10 were also working properly until now...

Try this (this worked for me when they were bad) as soon as the plynouth splash comes up, don't wait for the dots to appear...immediately hit your enter key which should bring up the language screen and then press any key and you should get a selection that asks you if you want to go to live session or install...i would select live session first, then it should go into the live session and install from there...

I'd be curious to know if this works for you...let me know...and this should work with the 64 bit iso, so try that first...

I will give it a try a little later, and let you know...

---

### Post by cpatrick08 on 2013-05-25
> **sgage said:**
> I've been trying to make a new install of Saucy, but the Daily Builds of the past few days haven't been working for me. The plymouth splash comes up, the dots churn around for a while and then it fails with the error message 'unable to find a medium containing a live file system'.

This is the 64-bit iso - perhaps I'll give 32-bit a try. I used unetbootin to make a USB as I have been doing for years without a problem.

Is anyone else running into this? Any insights/workarounds?

TIA
i filed a bug anout it on lunchpad [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1184066](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1184066) if you have the problem mark it as affecting you

---

### Post by sgage on 2013-05-25
> **cpatrick08 said:**
> i filed a bug anout it on lunchpad [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1184066](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1184066) if you have the problem mark it as affecting you

Thanks for filing the bug - I have marked it as affecting me.

---

### Post by sgage on 2013-05-25
> **craig10x said:**
> I had that problem on the daily builds of 13.04 when i was going to first install it during development a few months ago...later in the cycle they started to work properly, and the live isos of 13.10 were also working properly until now...

Try this (this worked for me when they were bad) as soon as the plynouth splash comes up, don't wait for the dots to appear...immediately hit your enter key which should bring up the language screen and then press any key and you should get a selection that asks you if you want to go to live session or install...i would select live session first, then it should go into the live session and install from there...

I'd be curious to know if this works for you...let me know...and this should work with the 64 bit iso, so try that first...

Hitting 'enter' does not have any result. Hitting F6 generates the following:

/sbin/udevadm: not found
can't open /dev/sr0: No medium found

Guess we'll just have to wait until they fix it.

---

### Post by pal1965 on 2013-05-25
same problem for me too  on 64 bit iso

---

### Post by tdockery97 on 2013-05-25
I would have to go along with the hardware theory, as I have had no trouble at all booting/installing the Saucy dailies.  I'm running the build from 5/24 right now.  Perhaps in the progression of the kernels some hardware support hasn't caught up yet?  (Total guess as I'm not an expert)

---

### Post by sgage on 2013-05-25
> **tdockery97 said:**
> I would have to go along with the hardware theory, as I have had no trouble at all booting/installing the Saucy dailies.  I'm running the build from 5/24 right now.  Perhaps in the progression of the kernels some hardware support hasn't caught up yet?  (Total guess as I'm not an expert)

Could be. Had no trouble until a few days ago. Just gotta wait, I suppose. They'll fix it by and by - the bug's been filed and all who are experiencing this problem should 'me too' it...

---

### Post by craig10x on 2013-05-25
I'm still waiting for them to fix the touchpad problem in 13.04 (which has carried into 13.10 of course)  It was reviewed and about 9 people added comments or this affects me to my bug report...
Reported in early February but still no one assigned!  Yet, everyone has it on their ubuntu (main edition)...you would think they would have noticed it themselves...;)

(that's the problem that if you change a setting in there it does not lock in and goes back to the default when you close the window)....

He is probably right...probably only a problem on certain hardware...i can boot up the live sessions on 13.10 just fine...will no doubt get corrected soon...

---

### Post by jerrylamos on 2013-05-25
Oh, yeh.  saucy amd64 running firefox, started zsync of May 25 build.  Zsync ran fine.  Firefox slowed down and stopped.  Thought about doing an ubuntu-bug, maybe if this persists.

On desktop i386 saucy firefox wouldn't open a window at all.  It said to reboot and try again.  And again.  Thought about doing an ubuntu-bug, maybe if this persists.

Installed Opera, ran fine, went to Google-chrome site, tried to download.  No luck, don't know why.

Software center installed chromium (I'm not a chromium fan) at least it runs.

Let me try a dread update....

Oh, BTW, booted saucy .iso directly from hard disk with a /etc/grub.d/40_custom choice. Whole lot faster than a USB stick.   Live desktop came up, got hidden WPA protected network connected O.K., started install, got to the choose language window, selected continue.  It didn't.  Thought about doing an ubuntu-bug, maybe if this persists.

---

### Post by VMC on 2013-05-25
> **jerrylamos said:**
> 
Oh, BTW, booted saucy .iso directly from hard disk with a /etc/grub.d/40_custom choice. Whole lot faster than a USB stick.   Live desktop came up, got hidden WPA protected network connected O.K., started install, got to the choose language window, selected continue.  It didn't.  Thought about doing an ubuntu-bug, maybe if this persists.
  The usb-stick got hung up on "Plymouth Rock", and wouldn't move inland. I had to boot using the loopback method also. Then I was able to go forward. First time that has happened(to be expected). First thing I noticed is the long delay in resonse, at time. If I just wait it out, everythings comes back normal. It first appears as a freeze.

---

### Post by Mathor on 2013-05-25
It always pains me to say this, but the newest builds booted/installed just fine for me :oops:

My AMD chip has never steered me wrong. However, look out once Unity 8 comes!

---

### Post by jerrylamos on 2013-05-26
Finally (!) installed, up, and running.  zsync hasn't shown any change in the last couple days (if I'm running it right) and install attempts each day would "freeze" early in ubiquity.

For whatever reason saucy amd64 iso (I boot directly from the hard disk with a 40_custom entry) came up and installed O.K. today.  Haven't had any luck getting the /var/crash reports to report to Launchpad.

Now got quite a few "internal errors" example Compiz, Nautilus, Unity Panel Service.

BTW, since my Acer C7 Chromebook uses Google-Chrome and so does my Nook HD+, so I installed Google-Chrome-Beta (not chromium).  Why?  Last I was zsync using saucy with Firefox up, Firefox ran slower and slower and finally stopped.  zsync ran merrily on and finished.

---

### Post by jerrylamos on 2013-05-28
Am I looking in the wrong place?  It's 28 May and the Saucy Daily Build is dated 25 may.

apt-get update is still finding stuff every day, example 24 MB today, obviously not going into the daily build .iso.

?

---

### Post by sudodus on 2013-05-28
Lubuntu is from the 27th, Ubuntu from the 25th, so I think you are looking at the right place.

Edit: ... and Xubuntu from today

---

### Post by dino99 on 2013-05-28
> **jerrylamos said:**
> Am I looking in the wrong place?  It's 28 May and the Saucy Daily Build is dated 25 may.

apt-get update is still finding stuff every day, example 24 MB today, obviously not going into the daily build .iso.

?

it might be due to the prior huge week-end (where lot of builders have been down.)

---

### Post by ventrical on 2013-05-28
> **sgage said:**
> Could be. Had no trouble until a few days ago. Just gotta wait, I suppose. They'll fix it by and by - the bug's been filed and all who are experiencing this problem should 'me too' it...

With the i386 zsync .. still nothing. It hasn't budged for days. All reads 100%.  Literally it's 'bricked'!

:)

edit*

My apologies .. that is :

saucy-desktop-i386.iso

---

### Post by sgage on 2013-05-28
> **ventrical said:**
> With the i386 zsync .. still nothing. It hasn't budged for days. All reads 100%.  Literally it's 'bricked'!

:)

I tried yesterday's Ubuntu Gnome daily build, and physically burned it to a CD. This time I was able to get to the F6 options, and actually was able to complete the installation. It seemed normal, but when I rebooted, GDM would just freeze at the first click or key press. I tried fiddling with different kernels and nvidia drivers or just nouveau, but no dice. Hopefully there will be a new one to try later today. I'd like to see how Saucy is doing!

---

### Post by Cavsfan on 2013-05-28
I installed Saucy a while back but, just like Raring I could not install it with my USB drive connected. I normally leave it on and accessible.

But, the installer just hung there forever. I unmounted it, turned it off and then it installed without a hitch.

Pretty sure even when I installed Raring final release it did the same. I have gotten used to unmounting and turning off that USB drive when installing any Ubuntu iso.

Just my 2 cents.

---

### Post by ventrical on 2013-05-28
We're back in the saddle again.


reading seed file ./saucy-desktop-i386.iso: ***Read ./saucy-desktop-i386.iso. Target 88.0% complete.     
reading seed file saucy-desktop-i386.iso:

---

### Post by ventrical on 2013-05-28
Ubuntu live USB  saucy session saucy-desktop-i386.iso better than ever as usual ! Writing this from live usb of todays zsync.

regards

---

### Post by jinjorge on 2013-06-01
havent been able to get either the Ubuntu Gnome version or the regular version of 13.10 to install correctly on my desktops. For the gnome version, I get to the sign in screen and then nothing works - can't sign in, keyboard does not work and the mouse moves around but nothing is clickable.  For the regular 13.10 Ubuntu install, for some odd reason it looks like the install blows away the ubuntu partition and then the box can't find any bootable media.

Haven't had time to troubleshoot lately. I'll give it another go around with the extra desktop I have and see where things end up

---

