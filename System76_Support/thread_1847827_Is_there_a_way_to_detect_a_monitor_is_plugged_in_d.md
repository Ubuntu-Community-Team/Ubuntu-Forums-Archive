---
title: "Is there a way to detect a monitor is plugged in during boot?"
date: 2011-09-21
forum: System76 Support
---

### Post by iandouglas on 2011-09-21
Hey all,

I'm curious if there's a way to detect if a second monitor is plugged into my Bonobo laptop. I currently have it configured for dual-screen at work with a lovely 2500x1400-something monitor and the 1.5GB nvidia graphics drive it at native resolution which is awesome ... until I'm at home, and Ubuntu thinks I still have the monitor attached and throws windows off the screen.

Ideally, since I always plug in the monitor before I even turn the laptop on at work, I'd love a way to tell if the monitor is plugged in and choose the current xorg.conf file. Otherwise, if no second monitor is detected, bring the system up in single-screen mode, even if that means generating a second xorg.conf.

Worst case, I suppose I could halt the boot process with a menu to choose, and have that symlink the proper xorg.conf file in place.

Thanks for any ideas!

---

### Post by isantop on 2011-09-21
Unfortunately, the Nvidia driver isn't flexible enough to allow that.

---

### Post by Dragonbite on 2011-09-22
Is that something with the Linux nVidia drivers?

My work laptop I have nVidia (admitting, on Windows) and it changes the resolution based on whether I boot up at work (2nd external monitor) or not (only laptop screen).

That sucks!

---

### Post by isantop on 2011-09-22
Yes, it's a problem with the Nvidia drivers in Linux only. The Windows drivers have a much larger user base, and thus get much more attention from developers.

---

### Post by birdsarah on 2011-09-25
On other laptops, I've never had a problem with Ubuntu detecting external monitors or not (excpet for the fact that Unity and Dual Monitors is a disaster that I haven't figured out yet). I have a Gazelle and haven't needed an external monitor really, so haven't played with it much.

However, could you not write a little shell script that runs after x has started that does something like:
a) run xranr
b) if your big monitor is listed then use it
c) if it's not listed then just use main monitor

i'm not so competent at shell scripts or xrandr that i know off the top of my head what that would look like, but it seems like it should be possible.

Good luck!

---

### Post by isantop on 2011-09-26
The problem is that the Nvidia graphics drivers don't support xrandr. So all configuration has to be done post-boot.

---

