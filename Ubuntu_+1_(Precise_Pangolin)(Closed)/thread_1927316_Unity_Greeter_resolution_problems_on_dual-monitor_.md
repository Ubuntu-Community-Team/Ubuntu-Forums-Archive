---
title: "Unity Greeter resolution problems on dual-monitor setup"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by go7Ul1ai on 2012-02-17
I am using a laptop with a lower resolution monitor hooked up to it. Everything is fine when I set the right resolution for each screen in the system settings, I wish these would be applied somehow for the unity greeter.

When I log in to Ubuntu, unity greeter shows a low resolution on the monitor as well as the laptop screen. I'm not the best at explaining so when I can I'll upload a picture of what I mean. I don't know whether anyone else is having similar problems and wouldn't know how to report it as a bug.

[[IMG]http://i.imgur.com/p9asj.jpg[/IMG]](http://imgur.com/p9asj)

Sorry for the crappy pic but I hope you can see what I'm trying to say.

---

### Post by go7Ul1ai on 2012-02-18
Thanks guys

---

### Post by fabricator4 on 2012-02-18
> **lee.jarratt said:**
> I am using a laptop with a lower resolution monitor hooked up to it. Everything is fine when I set the right resolution for each screen in the system settings, I wish these would be applied somehow for the unity greeter.

Dual monitor support was actually one of the things that got worse with the changes in 11.04 and 11.10, especially when using monitors of different resolutions. I got a real shock when I tried 11.04 on my laptop and found it had a real problem resolving resolution issues with another monitor plugged in.

Have another look when 12.04 LTS comes out and see if it's been improved further - especially wrt different resolutions in the greeter.

I do know that Unity will probably have a launcher on every monitor by then, and that they are working on getting good all round dual monitor support ready for the LTS.

Chris

---

### Post by Nick Payne on 2012-02-18
On my dual monitor setup the 12.04 login screen resolution is crap. Once I'm logged in I get the correct resolution and orientation that I've set for the monitors, with the desktop spanning both monitors, but the login screen has the monitors mirrored with the resolution lower than the native resolution of either monitor. Any way of changing this. It looks pretty crappy, particularly as one of the monitors is in portrait orientation, so the login screen on that monitor shows up sideways.

---

### Post by xerosis on 2012-02-19
There's a bug report floating around somewhere about this. In a nutshell, for mirrored monitors, it has to find a common resolution supported by both monitors which is what is happening here.

---

### Post by Nick Payne on 2012-02-19
> **xerosis said:**
> There's a bug report floating around somewhere about this. In a nutshell, for mirrored monitors, it has to find a common resolution supported by both monitors which is what is happening here.

Except that the maximum resolution common to both monitors is 1920x1080, whereas the resolution shown by the greeter is only 1152x864.

The Ubuntu 10.04 I have installed on the same machine can show the login screen with both monitors at their native resolution and correct orientation, though that is using the closed source nVidia driver.

---

### Post by prusswan on 2012-02-20
dual view is slightly better, btw a tip is to align the top side of the screens if you want to do that. I couldn't see the notifications popup when I aligned by the bottom edge, so stupid

---

### Post by Hanine on 2012-04-02
Here is the bug. 
Please if you are concerned, mark yoursef as being affected.
If you don't have a Launchpad accound, create it.

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874241](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874241)

---

