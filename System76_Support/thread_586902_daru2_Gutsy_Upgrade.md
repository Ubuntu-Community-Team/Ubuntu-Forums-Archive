---
title: "daru2 Gutsy Upgrade"
date: 2007-10-22
forum: System76 Support
---

### Post by palintheus on 2007-10-22
my post from this thread: [http://ubuntuforums.org/showthread.php?t=585362](http://ubuntuforums.org/showthread.php?t=585362)

> 
System Model : daru2
Upgrade Method : Update Manager (internet)
Graphics : Yes
Wireless : Yes, still will not recognize ethernet cable unless booted with it plugged in
Sound : Only on 2.6.20* kernel
Suspend : Yes
Hibernate : not tested

Power management is still buggy. I seem to have ridded myself of the blanking, I have changed the power management to nothing where ever it said blank screen. I have a message pop-up when I log in about my X settings being different than my GNOME settings in regards to my keyboard, haven't looked into it though. I cannot configure my touchpad, when I select it in System > Preferences it says "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I think thats it so far.....will update as it changes

====EDIT====

System Model : daru2
Upgrade Method : Clean Install (Alternate CD)
Graphics : Yes
Wireless : Yes, now recognizes when ethernet cable is plugged in, does not need to be plugged in on boot
Sound : Worked after install reboot, installed and ran Sys76 Drvier and now sound will not work
Suspend : Yes
Hibernate : Yes

Still have the pop-up about the keyboard settings, and still cannot configure my touchpad. Will check screen blanking, and power management

*****************************************
The main thing I am irked about is the sound, but the touchpad config issue annoys me.

---

### Post by ackey on 2007-10-22
I also updated the daru2 via the update manager...

I get the same touchpad message, though I haven't gotten anything about my X and GNOME settings being different.

When I boot I always get a message that HAL failed to initialize.  I am able to start it by running sudo hald.  I've had to manually configure my wireless, which is behaving strangely but functioning.  I'm unsure if that is related to HAL or not.  I usually use knetworkmanager (instead of nm-applet) with no problems, but I had to use the admin -> network menu to get the settings right.

I don't seem to be having problems with my sound, I'm running kernel 2.6.22-14.

I have been having problems with power management, part of which I have been attributing to HAL.  I had a brief system hangup - before which it didn't recognize the battery, and after it did.

The laptop was able to suspend without any (obvious?) problems, but I haven't tried hibernate yet.

I've installed and restored with the System6 driver.

I mostly am frustrated with HAL not working on start up.  I see in the forums that some other users have encountered this with the update, but I haven't found any solutions yet.

---

### Post by saxamo on 2007-10-22
For all my daru2's out there, here's how I got sound working on mine. After some searching, I bring your attention [Here]("http://ubuntuforums.org/showthread.php?t=530374") 

I followed the steps in order, but it was not until I did these two steps in order that sound magically worked!
> Install Ubuntu kernel back ports (linux-backports-modules-* ). You may need to run the above command (Possible conflicting driver issue). Then reboot.

And then I ran the "above commands"

```

sudo rm /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel.ko &&
sudo ln -s /lib/modules/$(uname -r)/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel.ko &&
sudo depmod -ae
```

Rebooted, and it works fine! Volume is great and it switches between heaphone and speaker flawlessly. I hope this works for everyone else!

---

### Post by palintheus on 2007-10-22
Edited my xorg.conf changed the keyboard from *105 to *104. This stopped the pop-up about the differences in the X and GNOME settings.

---

### Post by palintheus on 2007-10-22
I reinstalled to fix the sound issue and haven't ran the System76 driver yet.

Tom - 

Could the above solution be tested more thoroughly. I really don't want to reinstall again to fix this issue, its feeling to much like Windows.

---

### Post by thomasaaron on 2007-10-23
We're working on this problem right now and won't be stopping till it's fixed.

---

