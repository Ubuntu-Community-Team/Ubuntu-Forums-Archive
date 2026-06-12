---
title: "daru2 + 9.10 &lt; 3"
date: 2009-10-17
forum: System76 Support
---

### Post by TheBuzzSaw on 2009-10-17
Translation: Ubuntu 9.10 beta on daru2 is **incredible**.

I read about the new Intel graphics architecture and thought, "Hmmm. Sounds interesting. I'll give it a shot." Holy cow, now my laptop behaves like my desktop, which boasts an Nvidia 8500 card. Granted, I'm sure my daru2's gaming ability is still pathetic, but GNOME and various apps run beautifully under the new drivers.

I'm not sure that I'll upgrade my Wild Dog to 9.10 (unless TA comes in and gives a good reason to). The 9.10 enhancements seem fairly laptop-centric, and I have everything running the way I want it to right now. :-/

---

### Post by thomasaaron on 2009-10-19
Yeah, I'd wait. We're still testing, and there are still a few kinks to work out. We've not gotten to the Wild Dog yet, though.

---

### Post by TheBuzzSaw on 2009-10-19
Is there going to be a driver update for Windows 7 drivers for the Wild Dog? I'm not guaranteed to install it. I currently dual boot XP just for gaming purposes. My wife has Windows 7. It is fantastic as far as Windows goes, but it's no rush. I boot into Windows probably once every two weeks.

---

### Post by thomasaaron on 2009-10-19
I can't imagine us *not* having them. But we've not received them yet.

---

### Post by flyingsquirrel625 on 2009-10-19
I've been running Karmic on my daru2 since alpha 6.  Definitely a few kinks, but I'm happy to report that my battery indicator seems to work properly again, and the video driver issues seem to be fixed from Jaunty.

On the downside, my bluetooth mouse doesn't work anymore, cheese no longer sees my webcam, and I started getting speaker hiss after an update sometime last week.  And suspend still doesn't work.

I realize I'm running unsupported here, but I'm reasonably happy with how it's turning out, overall.

---

### Post by ackey on 2009-10-26
I'm happy to see that there are still plenty of Daru2 users out there!  Have you all done clean installs?  Is there evidence that things work ok with the upgrade?  I'd be much quicker to jump on the karmic bandwagon if I knew I could do it through update manager without any huge problems...

As for the power management improvements, do you know how changes were made?  A while ago I was trying to use the patch that changed settings if it determined that the computer was MSI.  It never worked for me, possibly because I have a different bios version from other people.

---

### Post by TheBuzzSaw on 2009-10-26
I did a fresh install. I can't speak for the upgrade, but it shouldn't cause any major problems.

---

### Post by flyingsquirrel625 on 2009-11-04
> **ackey said:**
> I'm happy to see that there are still plenty of Daru2 users out there!  Have you all done clean installs?  Is there evidence that things work ok with the upgrade?  I'd be much quicker to jump on the karmic bandwagon if I knew I could do it through update manager without any huge problems...

I got a new SSD and did a clean install to that.  So I can't say anything about the upgrade experience, sorry.

> **ackey said:**
> As for the power management improvements, do you know how changes were made?  A while ago I was trying to use the patch that changed settings if it determined that the computer was MSI.  It never worked for me, possibly because I have a different bios version from other people.

No idea. All I know is the battery indicator works flawlessly for me.  I didn't have to do anything to make it work.

---

### Post by ackey on 2009-11-04
My upgrade ended up having a ton of issues, but all were fixed by:

1) Editing menu.lst to boot with the new kernel rather than the jaunty one
2) Installing wicd and removing NetworkManager
3) Booting in GNOME rather than failsafe gnome mode (failsafe had become the default and I can't figure out how to switch it back)

My powermanagement is the same as it was in jaunty, but the bios flash I am going to do tonight should fix that. Right now I don't have access to the System76 driver, so the amount to which things are working is quite excellent.

---

