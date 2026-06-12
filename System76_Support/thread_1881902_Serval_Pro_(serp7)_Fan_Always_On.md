---
title: "Serval Pro (serp7) Fan Always On"
date: 2011-11-16
forum: System76 Support
---

### Post by tjlytle on 2011-11-16
For the past few days I've noticed that my laptop (serp7) seems to run slowly after the screen saver is on for a while (and the screen saver starts to 'judder' when on). 

After my most recent few boots, the fan has been running non-stop (but the system seems as responsive as normal). 

I'm wondering if this is video card related.

I'm behind 2 distributions now, running 10.10 (which shipped with the laptop).

---

### Post by isantop on 2011-11-17
I almost wonder if there was a bad update that caused something to go wrong with the screensaver package. I'm wondering if you could back up your data and try installing 11.10?

---

### Post by airtonix on 2011-12-28
I doubt it's a bad update, I purchased the Serval Pro i7 with the gtx560 and 12gb of ram.

It came with ubuntu 11.10 64bit and after installing the gnome-shell packages from the repo, that's what I've been using ever since.

Sometimes when I spam some keys the fans just start going nuts and I have no way to turn them off.

As I'm writing this the fan just went on full blast by itself...

Also the fingerprint reader STILL does not work.! :<

---

### Post by isantop on 2011-12-29
Are you using the proprietary Nvidia driver? There are power management changes in it that allow for better fan control.

Also, try blowing out the vents on the system with compressed air, to ensure that there is no dust or debris blocking them.

---

### Post by wi! on 2012-01-10
come up with any solution? Mine is doing the same thing... I have not had an update anything in the past 2 days and iv shut off my machine since then so I doubt it would have to do with any uipdates. About an hour ago all of a sudden the track pad became unresponsive, I did a force reboot and now the fan will not turn off. It is at full power.

I am using the nvidia drivers, in the nvidia server settings, the thermal settings look good, sensor is reading at about 30C

---

### Post by Idyll on 2012-01-15
FYI, concerning the touchpad becoming unresponsive...

I've only had my Serval Pro less than a month and generally I really like it.  I did notice the trackpad locking up and becoming unresponsive and I discovered that if I uncheck in System Settings under Mouse and Touchpad the option
"Disable touchpad while typing"
The track pad has never again become unresponsive for days now so I'm guessing there must be a driver issue with that option enabled.

I also unchecked
"Enable mouse clicks with touchpad", to avoid any accidental clicks while I'm typing and I've found this works very well for me actually and I no longer accidently click by tapping the touchpad with my palm as I'm typing.

My fan seems to work fine and never gets that loud.  I run 11.10 with Unity (and must be one of the few people who really likes Unity), and my notebook has these options: the Core i7-2860QM Processor ( 8MB L3 Cache, 2.50GHz) and GTX 560M GPU with 1866 Mhz RAM, and 600GB SSD, so I don't know if that would make it run cooler or warmer than other option combinations/GUI.

tjlytle, why don't you upgrade to the latest 11.10 and see if running Unity fixes the issue?  What version of Gnome are you running?

airtonix, Since you mentioned you are running Gnome that is what makes me think that perhaps is where the issue is coming from since tjlytle is probably running Gnome too if still on Ubuntu 10.10.  If you are running Gnome, what version?

Mike

---

