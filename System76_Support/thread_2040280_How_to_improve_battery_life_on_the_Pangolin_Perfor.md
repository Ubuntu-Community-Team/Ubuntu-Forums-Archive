---
title: "How to improve battery life on the Pangolin Performance (and other Ubuntu laptops)"
date: 2012-08-10
forum: System76 Support
---

### Post by ShadowWraith on 2012-08-10
Using a very aggressive set of power saving tweaks, I've managed to get my base model Pangolin Performance to 4-4.5 hours of battery life from 3-3.5. (My PanP was purchased new in late summer 2012, base model - if anyone knows the exact model number, please inform me and I'll edit this)

These are common tips:

1. The first tweak is the most-repeated but also most important one: lower your screen brightness. This makes a big difference.

2. I installed Powertop, which is an Intel utility to control power usage. Just start it up after every boot with sudo powertop, move right to the Tunables with the arrow keys, and use the enter key to change all the "Bad" tunables to "Good".

Here are some less common ones:

3. Install [Jupiter]("http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html"). This is a utility which controls the system's power profile when plugged in and unplugged. It does several things, but most importantly it clocks down CPU when on battery power, saving a lot of energy (also, I noticed that the laptop runs cooler). Needless to say, this will affect performance a bit, so if you're converting a bunch of videos or something, use the Jupiter indicator in the status bar to go to high performance mode. Not that you should be converting videos when on battery power :P

4. I applied all the tweaks suggested on [the Ubuntu Wiki]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks"). These tips require things like custom kernel boot options, but for me, the extra battery life is worth the hassle. I have had no issues on my unmodified PanP, so all of the tips suggested should work okay for other PanP owners, and probably for the Lemur Ultra as well, considering that its internals are almost identical.


If and as I find more tweaks, I'll try to update this guide. Let's see if we can't get Ubuntu above 5 hours of battery life! If anyone has any further tweaks or suggestions, please reply, and I'll test them out.

---

### Post by Carborundum on 2012-08-10
If you have replaced your DVD-drive with another hard drive, one easy way to save a few watts is to make it spin down when idle. Simply add these lines to your /etc/hdparm.conf:
```
/dev/sdb {
       apm = 1
       spindown_time = 24
}

```(Assuming the hard drive is in fact sdb, of course. Find out with 'sudo blkid')
This will allow the hard drive to go into deep power saving mode after two minutes of no activity, thereby increasing your battery life by a small amount.

**WARNING!**
Do not do this to any hard drive where system files are stored! That would cause it to frequently spin up and down, thus wearing it out much faster.

---

### Post by ShadowWraith on 2012-08-10
I don't have a second hard disk installed, but I have some spares and I back up regularly, so I may just try this on my main drive.

Thank you for your suggestion!

---

### Post by ShadowWraith on 2012-08-14
I am now trying the package laptop-mode-tools. I haven't noticed any significant difference over my already installed modules, though.

EDIT: It seems that it may be doing something! My power-time-left indicator has hit 4:50 once, the highest ever, during a low-activity period. Perhaps I can now get a solid 4.5 hours on a full charge... 4:15 actual time is being optimistic, though.

---

