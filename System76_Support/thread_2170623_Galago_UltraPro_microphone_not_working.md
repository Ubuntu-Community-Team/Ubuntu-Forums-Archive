---
title: "Galago UltraPro microphone not working"
date: 2013-08-26
forum: System76 Support
---

### Post by treyhunner on 2013-08-26
I received this computer today and the internal microphone hasn't worked so far.

I have tried Google hangouts, Skype, Audacity, and just running ```
arecord test.wav
``` to record audio.  All I hear from the microphone is silence with an occasional crackle.

When I plug in a USB headset with microphone and select the external microphone in the Sound Input tab I can record sound just fine.

I currently suspect this is a hardware problem.  Is there anything else I should do to further test this hypothesis?

---

### Post by isantop on 2013-08-27
There appears to be an Alsa bug in the current Galago and Gazelle that prevents the microphone from working until you plug something into the external microphone jack. It can be a pair of headphones; just any kind of 3.5 mm headphone plug. Try plugging one in, then unplugging it, and see if that fixes it.

If it does, I can get you set up so that it does this automatically when you log in.

---

### Post by treyhunner on 2013-08-27
I tried plugging a microphone into the microphone jack and then unplugging it.

Plugging in a microphone allows the microphone to work (when speaking directly into it, my voice is recorded).

Unplugging the microphone does not result in the internal microphone working.

This still looks like a hardware issue to me.

---

### Post by isantop on 2013-08-28
It does indeed. Go ahead and open a support ticket on our website: [https://www.system76.com/my-account](https://www.system76.com/my-account)

We'll be able to bring your system in and have the microphone replaced.

---

### Post by jkossis on 2013-08-28
I am experiencing the same issue with my galago...It doesn't record at all, if anything just a crackling sound. Any way to resolve it?

---

### Post by treyhunner on 2013-08-29
Per the suggestion of System76 support, I tried the microphone on a live CD (xubuntu live CD on a flash drive) and confirmed that the microphone works.

So this appears to be a software/driver issue.  I don't know whether this is due to System76-installed drivers or whether this is a generic Ubuntu/Linux problem.

---

### Post by keith5 on 2013-08-30
It works in xubuntu, but not Ubuntu?  Whether it's the System76 driver or Ubuntu, you would think that if you bought a computer from a vendor that specializes in Ubuntu that the hardware would work out of the box...

---

### Post by isantop on 2013-08-30
We're aware of this issue, and we believe it's a bug introduced in an update to Ubuntu. Any users experiencing this issue should open support tickets on our website, and we'll notify you as soon as we have a solution available.

---

### Post by JayArby on 2013-09-14
Yes, this is definitely a software issue. I'm dual booting with Windows and the mic works fine when I'm running Windows.

---

### Post by Sarai the Geek on 2013-09-23
> **isantop said:**
> There appears to be an Alsa bug in the current Galago and Gazelle that prevents the microphone from working until you plug something into the external microphone jack. It can be a pair of headphones; just any kind of 3.5 mm headphone plug. Try plugging one in, then unplugging it, and see if that fixes it.

If it does, I can get you set up so that it does this automatically when you log in.

This fixed it for *me*- at least for the time being. Can you help me set it up so it does it automatically when I log in?

---

### Post by treyhunner on 2013-10-21
This was finally fixed for me after updating to Ubuntu 13.10.

I had to:

1. Update to Ubuntu 13.10
2. Re-install the System76 ppa and then update the System76 drivers
3. Reboot

---

### Post by moschops on 2013-10-21
Had the same problem myself and I'm already on 13.10 and have reinstall the drivers and rebooted (many times).

The first time I went to use an audio app - Skype - I got nothing.  I opened the system sound settings and it wasn't showing any input from the microphones.  I installed the Pulse Audio Preserences manager, opened it and seeing nothing relevant to the problem I closed it. Then I fired up Google Hangouts which installs its own browser plugin, and audio in it worked.  So I launched the system settings again and audio was showing input now.  I fired up skype again and it was okay.

So, not sure what fixed it - I suspect it could have been the Google talk plugin for Hangouts.  Or maybe it was installing the Pulse preferences app...

I've never understood why Linux audio has to be so complicated - wasn't everything going with ALSA, so what now is Pulse?  Or is Pulse just a layer on top of ALSA...

Oh yes, and while you are at it, if you find you don't have video either remember to turn on your video cam with Fn-10 - I've never had a laptop with a cam on-off setting but I guess that's kind of nice.

> **treyhunner said:**
> This was finally fixed for me after updating to Ubuntu 13.10.

I had to:

1. Update to Ubuntu 13.10
2. Re-install the System76 ppa and then update the System76 drivers
3. Reboot

---

### Post by isantop on 2013-10-21
> **moschops said:**
> Oh yes, and while you are at it, if you find you don't have video either remember to turn on your video cam with Fn-10 - I've never had a laptop with a cam on-off setting but I guess that's kind of nice.

It's a hardware-off, too. The only thing that will accept that signal is the BIOS, and the only way to send it is by pressing Fn+F10, so if it's off, it's *off*

Just a security feature. It's been around for years on our laptops; joining it this iteration is the status light next to the camera.

---

