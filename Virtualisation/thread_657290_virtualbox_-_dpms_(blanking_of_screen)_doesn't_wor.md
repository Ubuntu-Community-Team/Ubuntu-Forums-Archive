---
title: "virtualbox - dpms (blanking of screen) doesn't work anymore even after VB is closed"
date: 2008-01-03
forum: Virtualisation
---

### Post by jetpeach on 2008-01-03
Has anyone else seen a problem with Virtualbox where, if it is running OR even after it is completely closed, the DPMS functionality (the ability for the monitor to go into sleep mode/go blank) stops functioning?  For me, if I have run virtualbox since rebooting, from then on my monitor will not sleep automatically (it can still be made to sleep using the command line, but will not after the 15 minutes when it is suppose to). The auto sleep functionality is not returned until I reboot the computer.

I am running Kubuntu 7.10 - I suspect the problem *might* be specific to KDE, but am not sure.

A monitor that won't go to sleep is pretty annoying to me, especially since a lot of people besides myself use my computer (and they won't always turn the monitor off after using it) so any advice is much appreciated!

Thanks,
jet

---

### Post by fracklaus on 2008-02-29
Hi,

I have the same problem here on Debian testing with KDE. xset q states that DPMS is disabled if VirtualBox is running and that it is re-enabled after VB is closed. However it fails to work in that state. Resetting the dpms values with xset helps to enable dpms again. I think this is a strange bug in virtualbox.

Regards
fracklaus

---

### Post by medicdave on 2008-02-29
I'm experiencing the same problem, also on Kubuntu 7.10, with virtualbox 1.5.4.

dpms works fine from reboot up until virtualbox is run, but after this (even though xset -q indicates dpms is enabled) the monitor never shuts off. I've done a `grep -rH dpms /var/log/*` and dpms doesn't seem to be generating any entries in any log files.

I can help out in testing any ideas/workarounds that anyone has on this...

Thanks,
medicdave

---

### Post by jetpeach on 2008-03-05
i've discovered that when i run mythtv (which disables dpms) and then close it (which says it re-enables dpms) then dpms also stays off. and like fracklaus, if i manual reset dpms using xset it works.
so i think the problem must be with this xset command, i'm trying to debug by looking at my setting before and after (using xset -q)  running virtualbox or mythtv

---

### Post by medicdave on 2008-03-11
Another twist:

It seems that locking (and optionally unlocking) the screen will restore dpms functionality. When I use virtualbox, then close it, dpms doesn't work. But if I then lock the screen, monitor sleep once again works.

-MedicDave

---

### Post by Hero of Time on 2008-03-16
I have the same issue, while I don't run KDE but XFCE. So it has something to do with VirtualBox and Xorg settings.

I did manage to get it working again by entering 'xset +dpms' in a terminal (while the VM was running), but it didn't turn off the monitor while the VM was running, only after the VM shut down, it worked again. I also saw a change in the screensaver timeout. I have DPMS set to 10 minutes, the screensaver timeout was set to 0 when the VM was running, it changed to 600 when it closed.

---

### Post by ablu on 2008-04-08
Has anyone figured out how to prevent VirtualBox from modifying the host machine's DPMS setting?  This problem is very annoying... 

I don't think VirtualBox should be changing that setting at all!

I can understand the intent, but when you really think about it-- it doesn't make any sense to do this.

At least there should be an option somewhere for it! (maybe there is...)

---

### Post by jetpeach on 2008-06-08
yes, i absolutely agree that virtualbox should allow dpms to remain enabled. i'm unaware of a way to disable vb's disabling of dpms though.

although there intent is clear (if the keyboard and mouse were captured by virtualbox and dpms became enabled, to someone not knowing the "host key" (control-home by default) it may seem impossible to bring the monitor out of sleep! but still, this needs to be an option since it's incredibly annoying in it's current state...

---

