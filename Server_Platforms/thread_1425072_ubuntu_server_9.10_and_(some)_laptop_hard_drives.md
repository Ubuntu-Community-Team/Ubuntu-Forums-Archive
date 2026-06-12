---
title: "ubuntu server 9.10 and (some) laptop hard drives"
date: 2010-03-08
forum: Server Platforms
---

### Post by nikclev on 2010-03-08
I've recently been putting together a curiously expensive home NAS+ (the plus is that it's going to have many other duties foisted on it as I learn how!) At any rate, I came across this while playing with smartctl:

```

~$ sudo smartctl -a /dev/sde|grep "\(Load_Cycle_Count\|Power_On_Hours\)"
[sudo] password for nick:
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       [COLOR=Red]38[/COLOR]
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       [COLOR=Red]4197[/COLOR]

```Sure to kill the poor little laptop hard drive I have / mounted on, quicker than it should. It's only rated for (as near as I can find out) somewhere in the order of 600,000 or so load/unload cycles, this rate would exceed that in much less than a year.

Yikes! anyway, it's not a bug in Ubuntu, although it shows the same symptoms as [Bug #59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695"). It's nothing more than me using a drive for something other than western digital (in my case) intended it for. Aggressive power savings leading to wear and tear I don't want.

Solution was the same as the referenced bug, also. ```
sudo hdparm -B 255 /dev/sdX
```NOTE: this will -disable- power saving on that drive, which is what I want. If you want power saving but want less wear and tear, read through the bug report and pick a sane value for your setup. numbers between 128 and 254 seem to give a decent balance of power saving and load cycles, results vary by your setup and your hard drive vendor/firmware/etc.

I guess this is more of a FYI post rather than anything else, I think there are a lot of newbies like myself, but that may not have noticed this. I only noticed it because it currently sits directly on top of my home computer, and the case is open. (I heard it click quite often)

long story short, if you have a laptop hard drive, check to see if your load cycle count is much higher than it should be!

---

