---
title: "Can VB support both 8.10 and XP"
date: 2009-01-05
forum: Virtualisation
---

### Post by speed32219 on 2009-01-05
concurrently.  I have a new HTPC I put together using Nvidia 8200 chipset which supports hdmi and hd audio.  The case has a LCD, volume knob and remote.  I just spent 2 weeks getting everything working and in one kernel upgrade (Forgot to turn off automatic updates) I lost it all.  I was trying to get unencrypted BD working also at the time but that is history.  It seems that only 8.10 will support the new Nvidia chipsets (But not fully now with acceleration), so I either need to re-install or do something drastic.

I want to stay with Linux, but maybe I can have the best of both worlds.  I do not understand how V.B. really works and I have read a lot of wiki's recently.  They mostly involve different distros of Linux or Mac OSX but not much on doze.

Can I install V.B. with Ubuntu and XP or Win 2000 and have them run concurrently?

Like I put in a BD disk and Powerdvd8 takes over and displays the output.  I put in a SD dvd and Movie Player takes over and displays the output.  If that can be done than I can have doze work my remote, display stuff on the soundgraph LCD and run Anydvd for the BD suff. That would fix my problem until Ubuntu catches up with released drivers.

I am a nob when it comes to virtualization.

---

### Post by bodhi.zazen on 2009-01-05
Well yes and no ...

Good news : Yes VirtualBox (or VMWare or KVM or ... ) allows you to run multipel operating systems at the same time. You can use your usb devices and CDROM in the guest OS.

Bad news: Virtualization works by emulating hardware, so no you can not use your nvidia card or fancy graphics in your guest OS.

---

### Post by speed32219 on 2009-01-05
But if my hw supports dual monitors, then what can I do.  Or I could always put a cheap pciE card in for SD upscaled playback and use the fancy one for 1080P with Bly Ray.

Now, Can I play Blu Ray with windows and use the same DVD drive to play just SD material under Ubuntu. (Of course not at the same time.  

Or the BIG question, is it that **any guest can not** use the HW assigned to the host?

---

### Post by Dedoimedo on 2009-01-06
Hello,

You can run many different operating systems simultaneously as guest machines, provided you have enough ram. Having fast hard disks also helps. Having several hard disks also helps.

In general, you'll get about 80% performance. Additionally, you can have some 3D acceleration in Windows virtual machines, for applications that support OpenGL.

This may interest you:
[http://dedoimedo.com/computers/virtualization-3d-support-virtualbox.html](http://dedoimedo.com/computers/virtualization-3d-support-virtualbox.html)

Furthermore, direct physical access is available for some hardware, but it's not recommended for new users, because you can potentially break things.

Dedoimedo

---

### Post by speed32219 on 2009-01-06
Dedoimedo, thanks for the link.  That is what I'm going to do, and as Ibex matures and starts supporting all the HW I have in the box I will be able migrate it to one host machine, Ubuntu.

Thanks, I'm going to start following your tutorial tomorrow afternoon after work.

Ah, a few more questions.

1. Is there any problem with activation with XP?  Should I use Win2K?

2. With XP, do I need to be at SP3? And does Windows always give you those irrating ugrade messages? That would be the main reason to install Win2K, no more MS support and auto updates.

3. What OS should I install as the host?  If the Mother Bd. requires new dirvers that are only supported under XP currently (Video Acceleration, HDMI with inegrated 7.1, HDTV Card, Wireless, etc.) should that be the host?  Will I need to manually install the lastest 1.0.18 Alsa and 1.80a Nvidia drivers in Ibex to gain the hdmi and HD sound that I had to do before or will most HW work off the host?  Ubuntu right now does not fully support some of the HW I have unless I install some pre-release buggy drivers manually.  And I might run into issues with hanging, which I was having prior to the unscheduled Ibex update that wiped my custom built kernel.

---

