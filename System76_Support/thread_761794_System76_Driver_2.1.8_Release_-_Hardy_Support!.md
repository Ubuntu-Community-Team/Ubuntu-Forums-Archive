---
title: "System76 Driver 2.1.8 Release - Hardy Support!"
date: 2008-04-21
forum: System76 Support
---

### Post by crichell on 2008-04-21
System76 has released version 2.1.8 of the System76 Driver. Most patches for sound and other devices are now supported in Ubuntu 8.04 out of the box.

We can use your help testing too. If you have upgraded to Hardy and are experiencing any bugs please report them on Launchpad:

[https://launchpad.net/system76](https://launchpad.net/system76)

If you haven't upgraded to Hardy it's only 3 days away and I suggest holding out until the code goes gold.

System76 Driver 2.1.8 Change Log

[LIST=1]
[*]Add Ubuntu 8.04 "Hardy Heron" support
[*]Restore adds gnucash, gnucash-docs, and system76-driver. nVidia driver and gsynaptics are installed if appropriate.
[*]Remove system76 repo from sources.list and add via sources.list.d/system76.list
[/LIST]

If you receive a "GPG error" "public key is not available" run the following command to install our repository signing key:

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by crichell on 2008-04-21
More info about the System76 Driver can be found at:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

And Hardy Upgrade directions:

[http://knowledge76.com/index.php/HardyUpgrade](http://knowledge76.com/index.php/HardyUpgrade)

---

### Post by Rowan187 on 2008-04-21
I'm currently on the Live CD with my Pangolin v2, so far everything is looking great with Hardy, and when the installation is finished I'll post my results with the out-of-the-box support and then install the driver!

Note: it looks like on the page it just says the driver will allow me to restore, no driver support needed, but i'll install it anyways to see if it corrupts anything (for Gutsy, sound worked out of the box, and with the driver it removed it)

---

### Post by eleach on 2008-04-23
I have a Gazelle, model gazp2 with Edgy on it. I'm a couple Ubuntu releases behind.

Would it be OK to do a clean install of Hardy from install CD?

If so, how would I then get the System76 drivers after the install?

My biggest concern is wireless connection.

I've been very pleased with my Gazelle.

Thanks.

---

### Post by thomasaaron on 2008-04-23
If you do a fresh install:

First, use update manager to completely update your new install.
Second, install and run the system76 driver as follows:

wget [http://planet76.com/repositories/system76-driver-2.1.8.deb](http://planet76.com/repositories/system76-driver-2.1.8.deb)
sudo dpkg -i system76-driver-2.1.8.deb

System > Administration > System76 Driver > Restore Tab > Restore Button

---

### Post by compholio on 2008-04-23
I have the SERP3 (32-bit), do you guys recommend upgrading or installing fresh to get the 64-bit Hardy?  I heard rumors that the 64-bit version works better...

---

### Post by thomasaaron on 2008-04-24
compholio,

What is the model number on the bottom of your computer?

---

### Post by crichell on 2008-04-24
> **compholio said:**
> I have the SERP3 (32-bit), do you guys recommend upgrading or installing fresh to get the 64-bit Hardy?  I heard rumors that the 64-bit version works better...

We do recommend and pre-install 64 bit Ubuntu. It supports the full usage of up to 4 GB on your Serval, runs faster, and now has the same tickless kernel power saving features of 32 bit.

---

### Post by compholio on 2008-04-24
> **thomasaaron said:**
> compholio,

What is the model number on the bottom of your computer?

The rating label says Model FL90, but I imagine it's the other label (that is white instead of black) that is the one you are interested in.  Hopefully not, because that label is worn down to the point that I cannot read the model number.  What exactly do you need to know?

---

### Post by eleach on 2008-04-24
thomasaaron,
  
Thanks for the reply.
  
I really should not do a fresh install from an Ubuntu CD? I wanted to start over with new users, etc.
  
Also, when I go to the update manager, I see "New distribution release 7.07". Will 8.04 show up after I install 7.07?

---

### Post by thomasaaron on 2008-04-24
Hi, eleach.

By all means, do a fresh install. That's the way I like to do it too. It give Ubuntu that "clean sheet of paper" feel.

In your current situation, you would need to completely update the version you have on there before upgrading to the next.

We generally recommend just upgrading as opposed to doing a fresh install, as you don't have to worry about possibly loosing files and configurations that you've worked so hard to create. But a fresh install is fine too.

---

### Post by eleach on 2008-04-25
That's very helpful.

Then with the fresh install how do I get the System76 drivers?

All I'm worried about is wireless connectivity. Not sure whether I need a driver from System76 for this.

---

### Post by thomasaaron on 2008-04-25
Eleach,

You just use the install cd to install Ubuntu 64-bt version 8.04.
When the install is finished go to update manager and update the install. It is best to have a wired connection for this. Then...

Download and install the system 76 driver with these commands:
wget [http://planet76.com/repositories/system76-driver-2.2.0.deb](http://planet76.com/repositories/system76-driver-2.2.0.deb)
sudo dpkg -i system76-driver-2.2.0.deb

Go to System > Administration > System 76 Driver
Run the Restore function of the driver

Reboot the computer



Compholio, your computer will run great with Ubuntu 64-bit.

---

### Post by wnmnkh on 2008-04-27
Woo, this is quite fast update ;)

---

### Post by hkarl629 on 2008-04-27
When I followed the instructions to upgrade to latest System 76 Driver I ended up with Version 2.2.0  Is this OK?  Am I missing something? I did this after a successful update to Hardly Heron on my Serval (SERP2) on April 24, 25(?).

Love the computer and the operating system. Your help is also very good.
How about the web cam, tho?

Sincerely,
Henry Karl Juelch
72 Nightingale Lane
Bluffton,SC 29909

[email]juelch@davtv.com[/email]

---

### Post by greg_g on 2008-04-27
> **hkarl629 said:**
> When I followed the instructions to upgrade to latest System 76 Driver I ended up with Version 2.2.0  Is this OK?  Am I missing something? I did this after a successful update to Hardly Heron on my Serval (SERP2) on April 24, 25(?).


Yep, 2.2.0 is out now, so that is OK.

---

### Post by greg_g on 2008-04-27
Here's the changelog for 2.2.0 if you are curious what changed so quick:
Version 2.2.0

   1. Fix nVidia installation on restore (command changed in Hardy)
   2. Version bump for Hardy release

---

