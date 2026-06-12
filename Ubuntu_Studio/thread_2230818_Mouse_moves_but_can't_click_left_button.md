---
title: "Mouse moves but can't click left button"
date: 2014-06-21
forum: Ubuntu Studio
---

### Post by HugoJJ on 2014-06-21
Am using US 14.04 but this issue has been playing also on previous releases. Generally 10-20 secs after I launch my session I can't click and have to do a Ctrl-Alt-F1 followed by Ctrl-Alt-F7 to restart Xserver and the issue disappears although it occasionally reappears later on in the session and I have to repeat the operation.

Suspect this is not strictly UbuntuStudio related but probably more general. Interestingly it also occurred when I use the live CD. I've tried to use a different mouse but no change. Appreciate any ideas how I can find cause and solve this. I have US 14.04 64 installed on a GA-970A-UD3 with AMD FX-6199 CPU.

Otherwise the latest US release is superb ! Congratulations to the development team !

Hugo

---

### Post by uudruid74 on 2014-06-21
> **HugoJJ said:**
> Am using US 14.04 but this issue has been playing also on previous releases. Generally 10-20 secs after I launch my session I can't click and have to do a Ctrl-Alt-F1 followed by Ctrl-Alt-F7 to restart Xserver and the issue disappears although it occasionally reappears later on in the session and I have to repeat the operation.

Suspect this is not strictly UbuntuStudio related but probably more general. Interestingly it also occurred when I use the live CD. I've tried to use a different mouse but no change. Appreciate any ideas how I can find cause and solve this. I have US 14.04 64 installed on a GA-970A-UD3 with AMD FX-6199 CPU.

Otherwise the latest US release is superb ! Congratulations to the development team !

Hugo

Have you checked your syslog for any warning messages?  Also look in /var/log/Xorg.0.log for clues.   Is this a laptop?  Sometimes laptops get more problems and power management could be causing your issue since X will stop and restart drivers when you change consoles, so you should have some errors somewhere about whats going on with the drivers (dmesg, logs, etc).

---

### Post by HugoJJ on 2014-06-21
Thanks Uudruid74 ! Checked both syslog and Xorg.0.log but see no error messages. FYI am using the open source Radeon driver.

Hugo

---

### Post by HugoJJ on 2014-06-21
Forgot to mention my PC is not a laptop so would think unlikely that issue is related to powermanagemt.

---

### Post by uudruid74 on 2014-06-21
> **HugoJJ said:**
> Thanks Uudruid74 ! Checked both syslog and Xorg.0.log but see no error messages. FYI am using the open source Radeon driver.

Hugo

Hmmm ... which mouse driver is Xorg using?  I would check for things like shared interrupts (cat /proc/interrupts) - maybe the mouse's IRQ is being shared and freaking out X?  Or the installer may be using a driver that doesn't match the mouse exactly.

FYI - I'm using the open source Radeon driver, too.  The AMD proprietary one is really buggy and caused me all sorts of grief.  I went right back to the open source one.  But ... its not related to my problems.   Somehow I had a billion fonts installed (well, 1380 or something) and X would occasionally tell every app to reload its fonts.  Imagine a dozen processes all loading and rendering 1380 fonts at once.

---

### Post by HugoJJ on 2014-06-24
My wireless Mouse is identified as Logitech (unifying ?) Receiver and I think this could be the issue. I ran into some other issues and reinstalled US this time with a normal wired USB mouse. This seems to work better. Will try install the Logitech receiver again and see what happens. I've read recommendation to use Solaar package to configure so will try this as well.

---

### Post by HugoJJ on 2014-06-27
Confirm issue is linked to install with Logitech Receiver wireless mouse, even if mouse is swapped later. Fresh install with standard USB mouse is problem free. Thanks uudruid74. Issue solved.

---

