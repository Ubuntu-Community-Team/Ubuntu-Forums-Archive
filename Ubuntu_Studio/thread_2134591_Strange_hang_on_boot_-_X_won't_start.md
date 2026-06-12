---
title: "Strange hang on boot - X won't start"
date: 2013-04-11
forum: Ubuntu Studio
---

### Post by tonapc on 2013-04-11
Hello, I am a high school music teacher and I have been using Ubuntu studio in a dedicated music tech class for two years. I recently encountered a problem on one of the lab computers that I haven't seen before and would like any advice before I have to pull out the hard drive and save the kid's files. The system boots normally through grub (dual booted with windows) and flashes the ubuntu studio booting image, and then goes to the last shot of the terminal that always has the last check as *Checking batery state.... [OK ] and then : Setting IRQ priorities: start [rtc] ....Start [HDA-Intel]....etc. The last one it shows is Setting IRQ priorities: start [i8042] irq=12 pid=50 prio=74: OK. Then the cursor just sits there blinking,X never starts. I can switch to other terminals, and if I restart the window will show the shutdown sequence - but X never starts. The last thing in /var/log/syslog is a list of MTRR variable ranges enabled, and the very last message is x86PAT enabled:cpu 0, old 0x7040600070406. Any ideas? Sorry I cannot format this text box otherwise I would lay everything out a little better, my ENTER key does not seem to work on this forum website.Thanks! Kernel is 3.2.0-23-lowlatencey-pae. Ubuntu studio 12.04

---

### Post by zequence on 2013-04-11
What kind of graphic card do you have? Could this have something to do with drivers?

---

### Post by tonapc on 2013-04-12
It is entirely possible - but it happened out of the blue on a previously functional computer. lspci says I have an Intel 82945G/G2 integrated graphics controller. What would be the appropriate command to start X and see if i get a more precise error? "startx" just says no protocol specified.

---

### Post by zequence on 2013-04-12
Did you try booting to older kernels? Updating the system?

---

### Post by TheCoda on 2013-07-03
I'm having this exact same problem. Installed Studio 12.04 from official DVD image, everything worked. Installed updates (240 of them), everything worked. After reboot, another 6 updates appeared (looked like kernel related), and I installed and rebooted. After that, X wouldn't start, and I see the same battery/irq related messages on term #7 as posted by the OP. I switched to terminal #1 and logged in as root, then did 'startx'. A strage XFCE desktop came up. I immediately rebooted and then the login screen appeared (which is supposed to be turned off - automatic login was enabled). After trying to login, I see very briefly several messages about IRQs then the login screen reappears. I cannot log in. The update borked my brand new system. This is not uncommon, it seems to happen most times I try a new flavour of linux. First install works fine, updates break the system. Incredibly annoying.

Update: I can log in as guest ( i get the standard environment, and also as root (strange XFCE layout), but not as myself. I guess there is something somewhere I have to reset.

Update 2: Looking at .xsession-error in home directory, seems there was a problem with .ICEauthority. Found that this file was zero length and root-owned. After I chown'd it, the desktop starts okay.

@Tonapc, did you fix your issue?

---

