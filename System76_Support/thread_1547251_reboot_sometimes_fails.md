---
title: "reboot sometimes fails"
date: 2010-08-06
forum: System76 Support
---

### Post by robgwin on 2010-08-06
On a week old Ratel Ultra with 10.04, Ubuntu sometimes fails to load on a reboot. If I reboot after the computer's been running for a while, it pretty much always fails. If I reboot again right away, it always succeeds. Which makes it a real pain to troubleshoot.

Here's how the failure goes:

1. I close all programs, select "Restart..." from the panel, and confirm the popup.
2. Ubuntu shuts down, screen goes blank.
3. System76 splash screen displays
4. Screen goes blank again except for a non-blinking cursor in the lower left, and a single zero in the lower right.
5. After 5 seconds or so, a message flashes *really* fast in the lower left. So far all I've made out is "Failed to get kernel something something..." And then the box just shuts down.
6. I stare at it, say "wtf?", and finally push the power button, and everything starts up just fine like nothing ever happened.

Since I can't reproduce the problem right away, it's really hard to figure out what that fast message is, but if I decipher any more of it I'll add it here. The logs (syslog, messages) don't seem to have anything between the powerdown and the hard restart, presumably because it never got as far as loading the linux kernel to start writing logs.

Anybody seen behavior like this before? Any idea what else I can do to troubleshoot? Thanks.

---

### Post by paulbary on 2010-08-06
I'm running 10.04 on a Dell Dimension and see the same behavior
so it appears not to be related to a System76 hardware issue. 

Paul

---

### Post by thomasaaron on 2010-08-09
Before we start delving into this one, what happens if you *don't* push the power button for, say, 30 seconds. Does it restart?

---

### Post by robgwin on 2010-08-09
Thanks for the reply. Just tried a restart, got the failure, tried again to read the quick message ("failed to get kernal ME host configuration"???) After it powered off I went for a bathroom break, got something to drink, etc, took maybe 5 mins. Computer still off. Pushed button, booted.

---

### Post by thomasaaron on 2010-08-10
Just to clarify: Are you running 10.04 on the machine, which is what it should have come with, or did you put another version on there.

I just tested restart with a freshly turned-on machine, and it worked fine. I'll let it run for a while and try again.

---

### Post by robgwin on 2010-08-10
Yup, running the 10.04 it came with. Most drastic thing I can remember doing before discovering the problem is [trying to use the GLcells screensaver]("http://ubuntuforums.org/showthread.php?t=1543294").

---

### Post by thomasaaron on 2010-08-10
Well, I just rebooted again after running it for a while, and no problems. So, here's my best estimation of the problem:

Either...

1. You have a hokey image

...or...

2. You have a hokey hard drive

We've not had any other reports of this on Ratels, so I doubt it's a bug. So, you could try re-imaging. Or we could send you a new hard drive. Or we could bring it in and replace the hard drive.

Either way, we should handle it quickly. We can't cross-ship hard drives after 30 days. So, if we wait too long, we'll have to bring the hard drive back first before getting a new one out to you. 

Let's move this one to email. support...at...system76...dot...com.

---

