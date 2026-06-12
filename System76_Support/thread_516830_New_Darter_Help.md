---
title: "New Darter Help"
date: 2007-08-03
forum: System76 Support
---

### Post by palintheus on 2007-08-03
I have been thoroughly enjoying my new Darter since it arrived, but have ran into a few minor issues that I am sure can be resolved.

Ekiga - Video works, but the mic does not, I am not using a headset or anything, just wanted to test it out with the built in mic. Also the audio is choppy, and I have tried other sources(streaming audio) and it is ok.

Battery Icon - randomly does not recognize the battery charge, or when it is un/plugged into A/C. I have also noticed that when this happens I sometimes get disconnected from my WiFi. I attached a screenshot of the system tray showing the 0% charge and no plug on the icon, showing I am on battery. How can I be typing this without a charge?

Thanks in advance

Edit - Also sometimes it says it only has a 1/2 charge and will take up to 70 hrs to charge?

Edit - Mic works, just doesn't hear very well, had to actually run my finger over it to get anything, then moved the screen closer and was able to hear what I said.

Edit - Also added screenshot of the power history applet to show the erratic behavior.

---

### Post by shingalated on 2007-08-03
I am also having the same issue with the battery icon

---

### Post by palintheus on 2007-08-06
Is the power management issue something I should submit a bug on?

---

### Post by thomasaaron on 2007-08-06
Yes. I've been working on it all day. It looks like a BIOS problem. I'm on hold with the manufacturer now.

Best,
Tom

---

### Post by palintheus on 2007-08-06
[https://bugs.launchpad.net/system76/+bug/130739](https://bugs.launchpad.net/system76/+bug/130739)

Also, any idea on the choppy audio in Ekiga, I do not have a separate mic to plug in and have only tried the built-in mic

---

### Post by palintheus on 2007-08-09
> **palintheus said:**
> [url]Also, any idea on the choppy audio in Ekiga, I do not have a separate mic to plug in and have only tried the built-in mic

bump

---

### Post by thomasaaron on 2007-08-09
I'm not exactly sure.

There are two possibilities:
1. It is either a configuration or software problem with Ekiga. Sound Recorder and Skype both work great with the daru2.

2. That said, my above statement wasn't completely accurate. ;)
The daru2 has a bug in which the headphone and speakers both play at the same time without the capability of muting one of them.

We just found the solution to this problem. The daru needs the current ALSA release and a special model designation in the alsa-base file. Not only does this fix the headphone/speaker bug, but it changes the volume control options. It might fix the Ekiga problem too. (I'll do some testing with it later. Do you have to sign up for an account to record sound? A preliminary look didn't show me how record anything...)

The fix for the headphone/speaker bug will be coming down in the Sytem 76 driver next week. So I'd not devote too much effort into solving problems with your current ALSA version.

Best,
Tom

---

### Post by palintheus on 2007-08-09
> **thomasaaron said:**
> I'll do some testing with it later. Do you have to sign up for an account to record sound? A preliminary look didn't show me how record anything...

Yes, I think you need an Ekiga account.

> The fix for the headphone/speaker bug will be coming down in the Sytem 76 driver next week. So I'd not devote too much effort into solving problems with your current ALSA version.

I learned my lesson on fixing things for myself for awhile...:-\"

---

### Post by zacharydanger on 2007-09-03
> **thomasaaron said:**
> Yes. I've been working on it all day. It looks like a BIOS problem. I'm on hold with the manufacturer now.

Any luck with this? This is the *only* issue keeping me from being absolutely infatuated with my DarU2.

Thanks.

---

### Post by palintheus on 2007-09-03
I agree, since I have to estimate my time and don't know for sure I am hesitant to do work with out it being plugged in.

---

### Post by zacharydanger on 2007-09-03
It's just a thought, but has anyone looked at the utilities disc that comes with the DarU2? If it's BIOS issue couldn't there possibly be a BIOS update utility that might work under Windows?

Though, I did check my BIOS version (v1.30 I think) and it said it was released July of this year so there may not be a fix yet.

---

### Post by palintheus on 2007-09-03
If there is I am not going to load windows to do it, and I am not brave enough to do it through a VM I may not have set up correctly and screw up flashing my BIOS. I will patiently wait for System76 to do the dirty work with the vendor and send me instructions. :popcorn:

---

### Post by thomasaaron on 2007-09-04
No, there is nothing on the driver disk that will help.

I've already tried a BIOS update (which is still in the Beta stage) and it did not help.

---

