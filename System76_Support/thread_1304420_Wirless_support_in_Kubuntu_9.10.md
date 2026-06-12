---
title: "Wirless support in Kubuntu 9.10"
date: 2009-10-29
forum: System76 Support
---

### Post by robtg on 2009-10-29
Has anyone installed Kubuntu 9.10 on his or her s76 laptop and verified that wireless support is working?  I couldn't get it to work at all on 9.04 (nor could many other people).  I'd like to give Kubuntu a try but wireless needs to work.

Thanks.

Rob

---

### Post by imhavoc on 2009-10-29
Before I installed Ubuntu 9.10 on my Daru2, I downloaded the ISO and created a bootable USB drive. I booted, everything went fine. A few days later, I went ahead with the upgrade.

You can do the same test with Kubuntu -- either burn a CD and boot into the live desktop, or create a bootable USB device to do the same (provided your computer supports booting from USB).

---

### Post by jdayrutherord on 2010-02-02
I have kubuntu 64 running on a daru s76 laptop, that I
have had a bit of grief trying to run ubuntu 9.10 on
(mainly the memory issues with pulseaudio/udev). wireless seems
to work, no memory issues, though I am not a fan of the interface,
but am getting used to it. One other plus is that power management
features seem to work better on Kubuntu. I never really got
them to work on ubuntu, any version, even with the system 76 drivers,
which I am not running now.

---

### Post by black_ice=cream on 2010-02-02
Just install K9.10 In synaptic, so if it doesn't work you can still boot into GNOME. That's what I'm doing with Xubuntu, works like a charm. The easiest way to do this is by typing: 'apt-get install kubuntu-desktop'. Reboot, and you can choose from Kubuntu, or Ubuntu at log in screen. I have **not tested this w/ kubuntu, but it works fine w/ xubuntu, so I'm assuming it will work w/ kubuntu**.

---

### Post by thomasaaron on 2010-02-03
robtg, which computer do you have?

---

### Post by macabrem on 2010-02-07
> **robtg said:**
> Has anyone installed Kubuntu 9.10 on his or her s76 laptop and verified that wireless support is working?  I couldn't get it to work at all on 9.04 (nor could many other people).  I'd like to give Kubuntu a try but wireless needs to work.

Thanks.

Rob

Yes, my wireless works with Kubuntu 9.10.

---

### Post by robtg on 2010-02-07
> **thomasaaron said:**
> robtg, which computer do you have?

Tom:  It's a panp5.  I think the problem is that I don't broadcast my ssid.  GNOME seems to handle that well ("Connect to Hidden Wireless Network") while I can't find anything in KDE that allows me to do that.  SuSE running KDE couldn't find the network while Pardus Linux (a very cool distro) found it with no problems.  I guess it's a crapshoot.

Rob

---

### Post by thomasaaron on 2010-02-08
Yeah, I'm not sure what's going on there. Can you try installing wicd and using it as your network management program?

---

### Post by robtg on 2010-02-08
> **thomasaaron said:**
> Yeah, I'm not sure what's going on there. Can you try installing wicd and using it as your network management program?

I'll give that a try.  I'm somewhat of a Linux hobbyist (read:dangerous) and the last time I tried to install wicd I completely blew my configuration out of the water and had to reinstall Ubuntu.  

Rob

---

### Post by wrender on 2010-02-08
Most wifi problems for kubuntu are resolved by installing wicd. 

I did a fresh install of kubuntu with backports enabled with kde 4.3.5 which seems to have a wicd backend and works with the Knetwork manager. So I am now using the Knetworkmanager.

---

