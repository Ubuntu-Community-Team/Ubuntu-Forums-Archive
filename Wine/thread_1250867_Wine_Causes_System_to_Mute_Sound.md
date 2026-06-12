---
title: "Wine Causes System to Mute Sound"
date: 2009-08-27
forum: Wine
---

### Post by Cov3r70ps on 2009-08-27
Hi,
Whenever I start a program using wine, my ubuntu (9.04) mutes the 'PCM' sound, which mutes all volume. While I can simply minimize and turn the volume back on, it turns out to be a hassle due to alt-tabbing issues with many wine apps. This originally happened when I started World of Warcraft, and now seems to happen upon the launch of all wine apps I have tested (even though they had not done this before). I have searched google and several forums, but to no avail. Any help would be greatly appreciated.

Thanks!
Chris

---

### Post by lvlo on 2009-08-27
I have such issue with "Live For Speed". Try to set in Audio tab "OSS Driver" and "Emulation" in "Hardware Acceleration" menu.

---

### Post by lordwolf on 2009-08-27
hi all,

i'd like to add that i have a similar problem on ubuntu 9.04. but, it's worse because now i absolutely have no sound at all after that - even after a system restart. the weird thing is, other accounts are having no such issue. so, this could be some settings in this particular user account. by the way, anybody knows where the user audio configuration file is? :)

some help, please?

---

### Post by Cov3r70ps on 2009-08-27
> **lvlo said:**
> I have such issue with "Live For Speed". Try to set in Audio tab "OSS Driver" and "Emulation" in "Hardware Acceleration" menu.

I had already had wine set to use OSS, but I didn't think having the Hardware Acceleration set to emulation would fix this (it did by the way). The strangest part is that it used to work while on full. Though, I suppose that I'm not complaining, since it is indeed working.

Thanks! :)

---

### Post by lvlo on 2009-08-27
Well, I didn't think it will help neither, but since Wine 1.1* this workaround helps to find some peace between Wine and PulseAduio.

:)

---

### Post by Rogerborg on 2010-01-28
> **lvlo said:**
> I have such issue with "Live For Speed". Try to set in Audio tab "OSS Driver" and "Emulation" in "Hardware Acceleration" menu.

\\:D/

Thanks, changing from Full to Emulation fixed this problem for me in 9.10 using wine 1.136

---

### Post by NightwishFan on 2010-01-28
I am using Wine 1.1 on Ubuntu Karmic, as I have found it to work better on the games that I use.

I fixed some audio dropouts and buffer overflows by setting Wine to use direct audio access. It did not fix the volume issues though. I think without pulseaudio this option might monopolize the sound device. (Not sure)

Open wine regedit:
```
Software -> Wine -> Alsa Driver -> UseDirectHw
set to "y"
```

The volume issues may not be entirely related to Wine. I use a icewm session to use Virtualbox, and sometimes it is muted then too.

Perhaps gather some data and file a bug report.

---

