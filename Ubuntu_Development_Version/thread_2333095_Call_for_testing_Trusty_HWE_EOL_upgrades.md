---
title: "Call for testing Trusty HWE EOL upgrades"
date: 2016-08-06
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2016-08-06
For general info please see:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

Put simply those who installed using 14.04.2, 14.04.3, or 14.04.4 images will be presented with HWE EOL notifications when this update-manager update moves from trusty-proposed to trusty-updates:

> update-manager (1:0.196.16) trusty-proposed; urgency=medium

  * HweSupportStatus/consts.py: improve messages and recommend upgrading to
    the correct release. (LP: #1498059)

 -- Brian Murray <brian@ubuntu.com>  Thu, 04 Aug 2016 15:42:06 -0700


Based on my own testing and a quick browse of the image manifests this effects Ubuntu GNOME, Lubuntu, Xubuntu, and Kubuntu as well as both the desktop and server editions of Ubuntu itself.

The following seems to work for performing these tests:

> Step #1: Install your desired flavor of Ubuntu  14.04.2, 14.04.3, or 14.04.4. Boot into the fresh installation when complete and apply all available updates via UI, then reboot when instructed. It seems important to apply the post-install updates via UI rather than using the terminal!

Step #2: Enable trusty-proposed, update the cache and run "apt-get install update-manager". (That will update the components needed to display HWE EOL notifications). Then disable trusty-proposed, set Notify me of a new release to Never, and update the apt cache again.

Step #3: Based on recent tests completing step #2 should be enough to launch the HWE EOL upgrade notification in which case you just need to choose to install the HWE upgrade and reboot when prompted.

If the HWE EOL notification fails to appear close any open update or notifier UI, then from terminal run "apt-get update" followed by "update-manager". If the HWE EOL notification still fails to appear then I'll have to go back to the drawing board.

I've so far encountered one bug which seems to be Ubuntu GNOME specific:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel-lts-xenial/+bug/1610434](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel-lts-xenial/+bug/1610434)

Note: Only installations performed using the 14.04.2, 14.04.3, and 14.04.4 media are effected! The version number changes when the package base-files is updated:

> base-files (7.2ubuntu5.5) trusty; urgency=medium

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: Bump
    version number to 14.04.5 in preparation for the point release.

 -- Adam Conrad <adconrad@ubuntu.com>  Mon, 01 Aug 2016 07:48:43 -0600


But that is no indication of what kernel and Xstack is in use. It depends solely on what installation media was used, unless someone manually updated to a different HWE stack post-install.

---

### Post by mc4man on 2016-08-07
So did a quick test on fresh 14.04.3 updated install as clearly on my used 14.04.3 something was preventing the lts-HWE upgrade from proceeding.
It seems that it's not just good enough to install the new update-manager (currently in proposed) but you need to have proposed enabled to get the hwe prompt.
So opening update-manager in screen 1 without proposed enabled, in screen 2 with it enabled.

That doesn't make much sense after the fact.. (14.04.5 released, 14.04.2 > .4 hwe eol. Is this how it works??

---

### Post by ventrical on 2016-08-07
Ahah...

> 
Notify me of a new release to Never, and update the apt cache again.


edit:

Did nothing. Still no HWE notification..

---

### Post by mc4man on 2016-08-07
> **ventrical said:**
> Ahah...



edit:

Did nothing. Still no HWE notification..
Maybe try - 
update-manager 1:0.196.16
proposed repo enabled
no changes to Software & Updates > Updates from default settings

---

### Post by kansasnoob on 2016-08-07
> **mc4man said:**
> So did a quick test on fresh 14.04.3 updated install as clearly on my used 14.04.3 something was preventing the lts-HWE upgrade from proceeding.
It seems that it's not just good enough to install the new update-manager (currently in proposed) but you need to have proposed enabled to get the hwe prompt.
So opening update-manager in screen 1 without proposed enabled, in screen 2 with it enabled.

That doesn't make much sense after the fact.. (14.04.5 released, 14.04.2 > .4 hwe eol. Is this how it works??

That's how it works. Things are not totally straight forward which is why I wanted an actual Ubuntu test procedure written and, very importantly, be given at least a week to test the procedure. They literally drop these like a bomb on the exact release date of the 5th point release - eg; August 4th :(

In the procedure I wrote above I maybe should have highlighted this:

> Step #1: Install your desired flavor of Ubuntu 14.04.2, 14.04.3, or 14.04.4. **Boot into the fresh installation when complete and [COLOR="#FF0000"]apply all available updates via UI, then reboot when instructed. It seems important to apply the post-install updates via UI rather than using the terminal![/COLOR]**

Step #2: Enable trusty-proposed, update the cache and run "apt-get install update-manager". (That will update the components needed to display HWE EOL notifications). Then [B]disable trusty-proposed, set Notify me of a new release to Never, and update the apt cache again.
[/B]
Step #3: Based on recent tests completing step #2 should be enough to launch the HWE EOL upgrade notification in which case you just need to choose to install the HWE upgrade and reboot when prompted.

If the HWE EOL notification fails to appear close any open update or notifier UI, then from terminal run "apt-get update" followed by "update-manager". If the HWE EOL notification still fails to appear then I'll have to go back to the drawing board. 

The part highlighted in red is because of [this]("https://bugs.launchpad.net/ubuntu/xenial/+source/update-manager/+bug/1498059/comments/17"):

> If I run update-manager when some updates are available, it will also offer to upgrade the stack to lts-xenial. If I run it when the system is fully updated, it won't offer that.

And it seems like the way Ubuntu handles "staged updates" there are always some updates held back (as memory serves some avahi and nautilus packages were held), but if I updated the fresh install using apt-get dist-upgrade no residual updates were available and I wouldn't get the notification.

---

### Post by kansasnoob on 2016-08-07
> **ventrical said:**
> Ahah...



edit:

Did nothing. Still no HWE notification..

You can also run:

```
hwe-support-status --verbose
```

But if you're running the 3.13 or 4.4 series kernels they're supported until April 2019.

Those who installed using 14.04.2 got the 3.16 series kernel which goes HWE EOL now.

Those who installed using 14.04.3 got the 3.19 series kernel which goes HWE EOL now.

Those who installed using 14.04.4 got the 4.2 series kernel which goes HWE EOL now.

So you can also check the kernel you're running:

```
uname -r
```

---

### Post by broadcast23 on 2016-08-07
I just tried xubuntu 14.04.5 live and it starts up with no monitor, I have a A8-3820 APU and HD6550D amd graphics it just starts up with a cursor for 5 sec or so then the monitor shuts off and stays off.  This happens with Xubuntu 16.04 and 16.04.1 also.  The only way to get it to start up is to use nomodset before booting.  I think it is because of the 4.4 kernel in ubuntu.  Fedora 24 starts up fine (kernel 4.6).  The problem with using the nomodset option is that the resolution is only 1024x768 and the monitor is 1600x900.  The graphics are distorted when started in this mode (and fuzzy).  I am getting tired of burning "coasters" for DVD roms.

---

### Post by mc4man on 2016-08-07
> Step #2: Enable trusty-proposed, update the cache and run "apt-get install update-manager". (That will update the components needed to display HWE EOL notifications). Then disable trusty-proposed, set Notify me of a new release to Never, and update the apt cache again.

Step #3: Based on recent tests completing step #2 should be enough to launch the HWE EOL upgrade notification in which case you just need to choose to install the HWE upgrade and reboot when prompted.

That isn't what I see. As mentioned the HWE prompt only appears _when then proposed repo is enabled_. That seems wrong.

---

### Post by kansasnoob on 2016-08-07
> **mc4man said:**
> That isn't what I see. As mentioned the HWE prompt only appears _when then proposed repo is enabled_. That seems wrong.

It certainly makes the test results iffy because when they release the hwe-support-status tool (via update-manager) users will be performing the HWE upgardes w/o proposed enabled. Or most users shouldn't be running with proposed enabled.

This is exactly why I wanted Ubuntu to create an actual test process that "just works" and then have a QA test cycle to check for bugs.

---

### Post by kansasnoob on 2016-08-07
I figured out why Ubuntu GNOME HWE EOL upgrades were booting to a blank black screen :)

The process is failing to install libwayland-egl1-mesa-lts-xenial so GNOME Shell and GNOME Classic can't work!

---

### Post by mc4man on 2016-08-08
> **kansasnoob said:**
> It certainly makes the test results iffy because when they release the hwe-support-status tool (via update-manager) users will be performing the HWE upgardes w/o proposed enabled. Or most users shouldn't be running with proposed enabled.

This is exactly why I wanted Ubuntu to create an actual test process that "just works" and then have a QA test cycle to check for bugs.

edit:
I see, it's not proposed enabled  per se, it's that at least 1 update must be available for the hwe prompt to appear.
As it happens the only new official updates for trusty are in proposed.

---

