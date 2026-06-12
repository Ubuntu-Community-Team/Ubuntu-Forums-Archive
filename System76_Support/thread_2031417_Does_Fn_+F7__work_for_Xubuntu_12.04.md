---
title: "Does Fn +F7  work for Xubuntu 12.04"
date: 2012-07-21
forum: System76 Support
---

### Post by oplicity on 2012-07-21
HI,

I have simple dual screen layout, Primary screen is Lemur Laptop and secondary screen a simple 17" Monitor connected via VGA port on my laptop. I have pressed the Fn+F7 and nothing happens. Is there something I am missing here or is this key combination not supported on Xubuntu?

I have installed System76 Deb Package v3 and nothing is logged in "dmesg" either.

---

### Post by brdmn on 2012-07-22
> **oplicity said:**
> HI,

I have simple dual screen layout, Primary screen is Lemur Laptop and secondary screen a simple 17" Monitor connected via VGA port on my laptop. I have pressed the Fn+F7 and nothing happens. Is there something I am missing here or is this key combination not supported on Xubuntu?

I have installed System76 Deb Package v3 and nothing is logged in "dmesg" either.

My lemU4 is running Xubuntu 12.04 as well.  I installed ARandR, and I can use that to set up multiple displays.   You do have to hit Fn+F7 *after* configuring with ARandR.

For audio, run pavucontrol from a terminal.  Go to the configuration tab, and you can choose HDMI output.

One thing I would say is to set up the external display as an extended display rather than simultaneous.  This is easy to do with ARandR, just drag the HDMI outline to the right of the one showing the laptop screen (denoted LVDS1 on my desktop.)

I have a video playing on my TV now, as I'm browsing the forum on my laptop screen, so I'm pleased to say this actually works!

---

### Post by oplicity on 2012-07-23
HI,
Thanks for the feedback. So you are saying Fn+F7 does work for you after you have configured the Screens with arandr. I actually used xrandr and set up a simple shell script to get the external monitor active after login. I have tried pressing Fn+F7 and nothing happens. Though I will try arandr and see how that goes.

---

### Post by oplicity on 2012-07-23
HI,

Just added arandr application and no joy. Nothing happens with Fn+F7. I even tried re-installing system76 Drivers again, did a reboot and function key Fn+F7 does not work. The application is just a front end for xrandr.

---

### Post by brdmn on 2012-07-23
> **oplicity said:**
> HI,
Thanks for the feedback. So you are saying Fn+F7 does work for you after you have configured the Screens with arandr. I actually used xrandr and set up a simple shell script to get the external monitor active after login. I have tried pressing Fn+F7 and nothing happens. Though I will try arandr and see how that goes.

At first I thought Fn+F7 was doing nothing.  But after connecting my TV via HDMI and configuring with ARandR, I saw that the TV screen was blank.  I hit Fn+F7, and hey presto, my extended desktop appeared on the TV screen.

I tried the simultaneous display, but because my TV resolution is lower than that of the lemU4's screen, I was only getting part of the desktop.  Maybe if I had a newer TV, this would not be an issue.  Also, since you are using VGA, this may not be applicable.

---

