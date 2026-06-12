---
title: "Upgraded to karmic - no 'third party software' tab"
date: 2009-10-31
forum: System76 Support
---

### Post by jprainey on 2009-10-31
I upgraded my Darter ultra to Karmic last night - now there is no 'third party software' tab on my software sources window.  I did have some hiccups during the install, and, as a newbie may have been the cause.  

Any suggestions on how to get it back?

Thanks

Jack Rainey

---

### Post by HotShotDJ on 2009-10-31
It is now called "Other Software."  Do you have that tab?

---

### Post by jprainey on 2009-10-31
Yes, I have that tab, but it does not have the 'planet76' entry as depicted on theKarmic Upgrade.  Also note that I do have the appropriate System76 driver installed already. My concern is that I will not receive automatic updates.  

Can I just add this entry?

Thanks

---

### Post by HotShotDJ on 2009-10-31
> **jprainey said:**
> Can I just add this entry?No.  Don't do that.  Download the latest System76 driver from [http://planet76.com/repositories/](http://planet76.com/repositories/) ([http://planet76.com/repositories/sys...iver-2.3.9.deb](http://planet76.com/repositories/sys...iver-2.3.9.deb)). Just double click on it to install. Once it is installed, go to System -> Administration -> System76 Driver, click on the "Restore System" tab and then click on the "Restore" button.  That should get you fixed up.

---

### Post by tomasterisk on 2009-11-01
I still have no sound, still have no change from "dummy speaker".

I have no access to graphics card (I assume) because a) I can no longer have those more-involved screensavers and b) I cannot activate it in "Hardware Drivers". FWIW, it is an "ATI/AMB proprietary FGLRX graphics driver".

At boot-up the newest choice I have is 9.04. Why can't I see 9.10???

I upgraded for hours for this??

On a related note:How hard is it to just downgrade to Jaunty again (but keeping my personal data intact)?

---

### Post by thomasaaron on 2009-11-02
Tom,

Go to System > Administration > Hardware Driver. Disable the driver for "Modem Software." Reboot.

Did that fix your sound?

---

### Post by tomasterisk on 2009-11-02
> **thomasaaron said:**
> Tom,

Go to System > Administration > Hardware Driver. Disable the driver for "Modem Software." Reboot.

Did that fix your sound?

I tried this just now, Tom. I think I tried that earlier also. I do not seem to have a disable option, the driver listed as "not activated". Here is the screenshot:

---

### Post by tomasterisk on 2009-11-02
BTW, I am not even able to get 9.10 to show up on the boot; just 9.04.

---

### Post by tschlemmer on 2009-11-02
I removed the software modem from the the list of hardware drivers, rebooted, and that got my sound working on my Pangolin Performance laptop.

Tony

---

### Post by thomasaaron on 2009-11-03
Tom, it sounds like you may not have given the upgrade process permission to update your grub menu.

When you boot up and see the grub countdown (grub...3...2...1...) can you press escape and get to a boot menu? At the menu, do you see the 2.6.31 kernel that you upgraded to?

Can you boot into that kernel? If so, do you have sound in that kernel?

Also, you don't have your ATI driver activated. But let's deal with this kernel issue before activating it. First thing's first.

---

### Post by tomasterisk on 2009-11-03
> **thomasaaron said:**
> Tom, it sounds like you may not have given the upgrade process permission to update your grub menu.

When you boot up and see the grub countdown (grub...3...2...1...) can you press escape and get to a boot menu? At the menu, do you see the 2.6.31 kernel that you upgraded to?

Can you boot into that kernel? If so, do you have sound in that kernel?

Also, you don't have your ATI driver activated. But let's deal with this kernel issue before activating it. First thing's first.

AFAIK, I don't have access to grub that way. The newest option I have showing on the black screen is 9.04, but then I get the brown 9.10 splash screen.

---

### Post by tomasterisk on 2009-11-03
> **tomasterisk said:**
> AFAIK, I don't have access to grub that way. The newest option I have showing on the black screen is 9.04, but then I get the brown 9.10 splash screen.

I decided that I just don't have the time to do this. I went back to Jaunty.  I'll just wait for the next stable long-term version.

---

### Post by thomasaaron on 2009-11-04
Okay.

That definitely sounds like a thoroughly mucked up upgrade.

---

### Post by tomasterisk on 2009-11-04
> **thomasaaron said:**
> Okay.

That definitely sounds like a thoroughly mucked up upgrade.

I don't mind waiting.

Now I am  back to frequent window freezes. Any ideas? I have window effects at basic level. I don't have the System76 driver installed. WHich one do I need?

---

### Post by ctsdownloads on 2009-11-04
> **tomasterisk said:**
> I don't mind waiting.

Now I am  back to frequent window freezes. Any ideas? I have window effects at basic level. I don't have the System76 driver installed. WHich one do I need?

Not going to call this a "solution", rather simply point out that a dedicated /Home/ partition and always doing clean installs is the only way to go in my household. If it was me, I'd backup the home partition from the terminal so you get EVERYTHING, then do a clean install with advanced partitioning.

Just remember to backup before doing a[nything with the partitions]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by thomasaaron on 2009-11-05
Hi, Tom.

You're in Jaunty now, right? Make sure you have the swat ATI drivers installed. That should take care of the freezes...

> Please run these commands from a terminal...
echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list
echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade

---

### Post by tomasterisk on 2009-11-05
> **thomasaaron said:**
> Hi, Tom.

You're in Jaunty now, right? Make sure you have the swat ATI drivers installed. That should take care of the freezes...

OK. Thanks, Tom. I did all the above just now.

---

### Post by tomasterisk on 2009-11-14
> **tomasterisk said:**
> OK. Thanks, Tom. I did all the above just now.

For the record: This did not solve the problem. I finally "solved" it by just going back to good old Hardy Heron. 

I went ahead and dual-booted my Ratel Value (Hardy and Jaunty). No freezes, no glitches, nothing. There are hardly any differences in the features that I need so I think I will just stick here until the next long-term version comes (and even then I'll wait some).

I have learned a valuable lesson about upgrades. At the same time I still appreciate Ubuntu - Hardy does all the things i need.

---

