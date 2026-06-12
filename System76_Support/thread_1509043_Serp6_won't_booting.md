---
title: "Serp6 won't booting"
date: 2010-06-13
forum: System76 Support
---

### Post by jamesrl on 2010-06-13
Hi,

Yesterday, I ran out my battery the other day which sent my computer to sleep (via hibernate I believe, possibly it may have been set to suspend).  When I hooked it up to the power cord later, it froze at the beginning of the boot procedure: (right after the screen clears after having the option to press F2 for BIOS settings).  A black screen with a blinking cursor.  It responded to ctrl-alt-delete, but not the kernel panic responses (Ctrl-Alt-SysRq-R,E,I,S,U,B)

I downloaded a Lucid live cd and it will boot fine and everything seems fine off the live cd (I can mount the hard drive and everything looks normal).

Any advice or info?  I just got the laptop last week and the lack of debugging messages make it difficult to solve.  I'd rather not reinstall as a first option.

EDIT: Memtest was fine.  All the hardware testing in System -> Administration -> System Testing that I performed has found no hardware failures.  (Also apologize for the thread title; choosing between Serp6 won't boot / serp6 freeze during booting, lead to the mixup.  Sigh.)

---

### Post by jamesrl on 2010-06-14
So I tried updating grub from live cd; e.g.:

```
> sudo su
# mount /dev/sda1 /mnt 
# mount --bind /dev /mnt/dev
# mount --bind /proc /mnt/proc
# mount --bind /sys /mnt/sys
# chroot /mnt
# update-grub

```
and it seemed to install to the MBR fine (no error messages), but it still wouldn't boot and same error.  Now I'm not that familiar with the new grub introduced with lucid (e.g., found out today that menu.lst settings moved to /etc/defaults/grub).  If I held down shift when it was booting, it would change and I would see the "GRUB> " prompt (but couldn't type anything; nothing changed on the screen after that).

Anyhow, I repartitioned my hard drive copying my /home to a new partition and reinstall ubuntu from the live cd (and am currently in the process of reinstalling everything).  It booted fine the first time, so my problem is fine at the moment.  (Still not sure what happened though.)

---

### Post by isantop on 2010-06-14
I got similar problems after shortly after I got my computer. It may have gone to suspend by mistake, then had the battery run out on it. This can really wreak havoc on your filesystem, and can cause boot problems next time. Reinstalling fixed it right up for me, and I haven't had a problem since, so you should be in the clear too. If not, post, and we'll try to get you straightened out.

---

### Post by jamesrl on 2010-06-14
The suspend on low battery power probably was it. I was trying to cycle the battery, and the instructions said fully discharge the battery and I didn't want hibernate/shutdown to only partially discharge the battery.  

I was initially a little surprised with the battery life -- brand new battery seems to have about 55 min of battery life when not doing anything particularly CPU or graphically intensive (though I may not have charged it properly initially).  Granted in sys76 defense they never gave any indication of expected battery life, and I upgraded the video card (Nvidia), CPU (i7 Q720), RAM (8Gb), and lcd (1920x1080), while downgrading the battery energy capacity from my old machine (45 W-hr polymer vs old laptop's 72 W-hr 9-cell lithium ion).  So as expected coupling a significantly more powerful and energy-hungry machine with a smaller battery life is noticeably different.

---

### Post by isantop on 2010-06-14
That could easily be the cause of the short battery problem. Make sure that the first time you plug the system in, the battery is charged until it reports 100%. After that, discharge the battery to about 10% before plugging in. This will help to maximize your battery's service life and usage time.

---

### Post by natieo on 2010-07-27
Argh.  Me too - went to bed last night and the outlet got switched off so the thing must have died while suspended.  Is there a setting in the future I can use to help prevent that?  Something like going fully to hibernate mode or shutting down or...??

Meanwhile I'm trying to download 10.04 on another machine so I can do a reinstall, but two things occur to me here:

[LIST=1]
[*]Why doesn't System76 include a bootable recovery disk?  This would add about $0.50 to the cost and make my life a lot easier right now.
[*]Is there seriously no way to recover from this other than a reinstall??  Is there a good writeup anywhere on how to repartition, backup /home, and reinstall?  Could you maybe reinstall without formatting the partition?
[/LIST]

Thoughts?

---

### Post by isantop on 2010-07-27
If your computer has the "old" patition layout (15GB /, Swap, then /home) then all you need to do is specify partitions manually during the install. Select the 15GB partition to mount at /, the swap partition as swap, and the other partition to mount at /home. Then, make sure your username is the same as it used to be, and finish up. Your home files are restored.

If you have the new partition layout (large /, then swap), then all you need to do is set the large partition to mount at /, and the swap as swap. Reinstall with the same user name, and Ubuntu won't touch your personal files.

To make it so that the computer goes to hibernation or shuts down at critical battery, first unplug your computer (if it's plugged in), click on the battery icon, click "Preferences" and on the "On Battery Power" tab, set "When Battery Power is Critically low:" to Hibernate or Shutdown.

---

### Post by natieo on 2010-07-27
Thanks for the reply - I have the "new" layout, so I just left the partition unformatted and it kept my home folder as expected.  I wish I'd grabbed a dump of the packages I'd installed, but it hasn't been too bad to put them back together.

And yeah, I changed the setting to "shutdown" instead of hibernate when critically low on battery.  Hopefully that will avoid a repeat!  Is that maybe a setting that should be default for these laptops?  Or at least belong in the FAQ?  It seems like something most people are going to run into at least once, and it's a hassle to reinstall...

---

### Post by natieo on 2010-07-27
So... 2 for 2.  I had it set to shut down on critically low battery, but (full disclosure) I wasn't able to watch the final moments so I'm not sure if it tried or not.  When I checked back on the machine it was too late - wouldn't boot, black screen with a forever blinking cursor.

This is terrible.  As it exists right now EVERY time my battery dies I have to do a reinstall!!

I have an SSD hard drive, could that be part of the problem?  Is there anything I can do to help catch this state and shut down properly??  Or should I just either never unplug the machine or always shut it down by hand??  Arrrgh!  Is no one else having this problem??

Any tips gladly welcomed.
Nate

---

### Post by natieo on 2010-07-27
... I did the first reinstall after booting fully into Ubuntu from the CD, and it worked ok -- also on a wired network.  The one I'm trying now I didn't boot fully, I just clicked install and went for it.  Same procedure otherwise -- and here I'm on a wireless network.

Rebooted after the install and the trackpad doesn't work, wireless not recognized, and the resolution is wrong.  Trying to pull a system update from a wired connection now to see if that fixes things, but man, super, super fail for the Serval Professional.  I guess this is mostly just a power management bug, but it seems kind of like a show stopper - especially when the battery life is all of ONE hour!  Seems like you might just run out of juice, and then spend the next few hours reinstalling and looking for a wired connection to pull updates!

Sorry to snark, but I'm hoping someone from System76 has something encouraging to tell me.  This is a huge productivity drain and I'm super disappointed right now.

Nate

---

### Post by natieo on 2010-07-28
Two more reinstalls, both failing the same way -- everything goes well until I install the System76 drivers and reboot.  Then it hangs with the black screen and blinking cursor.

Should I just skip that step??  What drivers is it giving me?  Should a try a full format and just blow away my /home folder in case there's some setting in there that's interfering?

ARGH.  If I can ever get the machine back to a usable state I'll submit more info.  This is two hour-plus installs in the last 12 hours and neither of them have succeeded.  I'm heading in to work and will try again on a faster connection.

(one interesting thing: it definitely seems to behave differently depending on how I install.  If I "Try Ubuntu" first, the first reboot after installing has the right resolution and seems to know about the wireless card (although it couldn't connect).  When I skipped trying it and just "Install Ubuntu" when I reboot it comes up in crappy graphics mode and doesn't even see the wireless.  WTF?

---

### Post by natieo on 2010-07-28
I think the problem after installing the System76 drivers is the GRUB issue reported here:

[http://ubuntuforums.org/showthread.php?t=1540155](http://ubuntuforums.org/showthread.php?t=1540155)

... but hard to say since that all happens in the background?  Something in that update is applying the GRUB update to all devices automatically?

Either way, following those recovery instructions allows me to boot again.  And it looks like (at least this time) my wireless issue just needed the radio turned off and then back on.  So... back to running.  I'm going to tweak some settings on the power management and let it die again, just to see if I can successfully prevent a repeat of this nightmare.  I'll post the settings if I succeed.

Nate

---

### Post by isantop on 2010-07-28
Yes, that sounds like the GRUB problem. Big, widespread bug there. From what I can tell, it's happening on *all* 64-bit installations.

---

