---
title: "Dual monitors w/ Lemur"
date: 2010-11-20
forum: System76 Support
---

### Post by mjumbewu on 2010-11-20
Hi all,

I am considering purchasing a Lemur, as I work in many different locations and I'd like something that's lightweight, but still a real computer.  Often while at my desk, I use my laptop and an external 20" monitor in a dual-screen setup.  With my current nVidia card I can set the two displays to different resolutions (1280x800 and 1440x900), but I have a few questions about the Lemur:

1) Is it possible with the Lemur graphics to have dual monitors with different resolutions?  Can I do it without worrying about what's in my xorg.conf?

2) Is this setup well within the Lemur's capabilities, or would it cause strain such that the fan would have to run more than normal?

3) Is this an easy setup?  Ideally, I'd like it to be smart enough to remember that I want my 20" as my primary when it's plugged in, and switch to my laptop as primary when it's not.

Thanks for your time,
- Mjumbe

---

### Post by isantop on 2010-11-22
> 1) Is it possible with the Lemur graphics to have dual monitors with different resolutions? Can I do it without worrying about what's in my xorg.conf?

It should be possible, barring a hardware problem. I believe it uses what Ubuntu uses for HAL now, so it should be done without xorg.conf.

> 2) Is this setup well within the Lemur's capabilities, or would it cause strain such that the fan would have to run more than normal?

The Lemur is plenty capable of driving both screens at once. You won't have an issue there.

> 3) Is this an easy setup? Ideally, I'd like it to be smart enough to remember that I want my 20" as my primary when it's plugged in, and switch to my laptop as primary when it's not.

I'm not sure about this one. I believe Ubuntu uses whichever display is on the left as the primary, so if that would work, you'd be fine. However, if you need something more robust, things could get complicated.

---

### Post by Flyers2391 on 2010-11-23
> **mjumbewu said:**
> Hi all,

I am considering purchasing a Lemur, as I work in many different locations and I'd like something that's lightweight, but still a real computer.  Often while at my desk, I use my laptop and an external 20" monitor in a dual-screen setup.  With my current nVidia card I can set the two displays to different resolutions (1280x800 and 1440x900), but I have a few questions about the Lemur:
...
3) Is this an easy setup?  Ideally, I'd like it to be smart enough to remember that I want my 20" as my primary when it's plugged in, and switch to my laptop as primary when it's not.

Thanks for your time,
- Mjumbe

I move my laptop between work, home and travel all the time.  If I am going to be in the same place I can suspend or reboot and my second monitor settings will stick.  That is for a docking station at work, usb cable and vga at home or neither when traveling.  If I need to change it is quick and simple through system > preferences > display* ... you can also add the display icon to your panel if you are going to need to change it often.  

I always have my external monitor as primary ... at work it is on the left, at home it is on the right.  I don't know if ubuntu decided this for me or not but it is my preference :).  

*May be named something else now, I'm still running 9.10

---

### Post by isantop on 2010-11-23
It has been changed to Montiors, rather than display.

Actually, if you prefer, you can hold down Alt and drag the Panels to any edge of any screen. Including your other monitor.

---

### Post by mjumbewu on 2010-11-29
Thanks for the replies folks.  Very helpful.

---

### Post by John Peschken on 2010-11-30
I don't have System 76 right now, but on my little ASUS netbook, there is a FN key to toggle between internal and external monitors.  When I hit that, it toggle between different modes.  Both displays at the lesser resolution - External display Only - Small on-board Only.     There is also a position for both displays at the same time at the higher resolution, but that cuts the bottom off the low res display.

I can also switch in the Preferences-Monitors dialogs in Ubuntu.

If I set it for the big display at the higher resolution, it will come back up that way.  If it does not find the big display at the next boot, it reverts back to the on-board one.

Others have confirmed the Lemur's capabilities, but I would expect that any laptop with an external VGA connector would be able to duplicate this trick.  Otherwise, it seems like the external connector would be a little pointless.

---

### Post by isantop on 2010-11-30
It's similar to the above experience, though more fine grained.

Pressing Fn+F7 cycles through the different configurations. Lets say you had a 1920x1080 external display connected. In no particular order, by pressing Fn+F7 you would get:

[LIST=1]
[*]The same image on both monitors, with both at 1366x768 (The Lemur's default resolution.)
[*]One large, multi-monitor desktop with the Lemur at 1366x768 and the external monitor at 1920x1080.
[*]An image on the external display only at 1920x1080.
[*]An image on the Lemur display only at 1866x768 (This is the default factory configuration.)
[/LIST]

Each time you pressed the hotkey, the computer would go to the next item in the list, returning to the top when it got to the bottom.

---

