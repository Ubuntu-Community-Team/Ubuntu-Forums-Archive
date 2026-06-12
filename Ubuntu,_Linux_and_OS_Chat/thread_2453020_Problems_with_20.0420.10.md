---
title: "Problems with 20.04/20.10"
date: 2020-11-01
forum: Ubuntu, Linux and OS Chat
---

### Post by crip720 on 2020-11-01
Is it just me or does 20.04/20.10 seem to add problems to stuff just worked in 18.04?  Seen quite a few questions recently here and on askUbuntu that stuff/hardware that worked well on 18.04 or earlier seems to break with 20.04.

---

### Post by CelticWarrior on 2020-11-01
I would say that there are issues with some printers and webcams that previously worked.

---

### Post by Deep_Peasant on 2020-11-01
I have several pc's that were running Xubuntu 18.04 LTS just fine.

I upgraded them in several ways,

from command line, this gave the old 18.04 whisker menu.
from live usb, this gave the new 20.04 whisker menu. (switched panes).

upgrading with live usb needed on 1 pc several tries, ended up with no gui etc.

at boot 'initramfs unpacking failed: Decoding failed' changing initramfs.conf the compress=lz4 to gzip fixed that.
later installs/upgrades did not seem to have that error. On all pc's.

then the [could not detach dm]("https://ubuntuforums.org/showthread.php?t=2452565") problem, even with many new reinstall still bugging me.

Printers, showing up installed twice or even 3 times, installing linux drivers from the vendors made everything even more worse.

20.04 pushes the snap store on your system and removes gnome software.

And yes, there's a lot more problems left and right on the internet and almost no solutions, I hate to use workarounds that are meant for other linux distro's.

There's a reason for using LTS versions, the keyword being stable. This is not.

---

### Post by guiverc on 2020-11-01
Things seem to always advance & move on.

Python2 was removed in 2019, thus anything that relied on it may have problems in 20.04 & 20.10.  The same applies to Qt4 (some printer software relied on Qt4; Qt5 came out in 2012 but still many printer people didn't re-build the printer packages supplying the Qt4 built ones that the new had worked for years).

Kernels change & this can have issues.  I noted a few issues (graphics) reported by Lubuntu users on old thinkpads. The issue is with 5.4 kernel it turns out, 5.3 (as used in 18.04.4) was good, but not so 18.04.5 with HWE or Ubuntu 20.04 using 5.4.  For those x86 Lubuntu users the 20.04 won't run, and on 18.04 the GA kernel still worked flawlessly so i'm not worried. I didn't experience the issue on any amd64 box, but have noted users reporting it an issue there too.

The *groovy* ISOs are different to prior releases, so I'd rather *forget* the *development* cycle, all issues discovered during *alpha* stage were fixed, only one issue discovered at release, or hours before may still remain. I understand the reason for the change, and given all discovered bugs during the *development* were fixed I'm happy (*only exception is if a amd64 groovy is booted on an i386 box, the kernel message doesn't get shown any longer, just blinking cursor... would require a lot of effort to allow that for extremely few users making that wrong architectrure error*).

I don't see it any different to prior cycles, stuff changes, & advances. Not everyone likes it.  (*I for one, was perfectly happy with my Ubuntu 11.04 using GNOME Classic)*

---

### Post by CatKiller on 2020-11-01
To the OP: people don't generally post about things that are tickety-boo. You can't make any conclusions about the relative proportions of people with problems to people without, since you never hear from the people without. 

> **Deep_Peasant said:**
> There's a reason for using LTS versions, the keyword being stable. This is not.

None of the letters in LTS are for stable, except that the first one is "Long."

Stable in software means that it *doesn't change*. And LTS releases don't. The software only changes through the Hardware Enablement Stack, or the Stable Release Updates mechanism, and it gets security updates and bugfixes, for five years. You've chosen *not* to stay with the LTS release.

---

### Post by MartyBuntu on 2020-11-01
I find that during every version release there's equal parts:

1) "I can't believe my hardware is FINALLY supported!"

2) "I can't believe that hardware that was working just fine is broken now!"


I'm still glad I use Linux as my daily.

---

### Post by crip720 on 2020-11-02
I had both 2 and 1 in that order with an old P4.  Everything work well with 12.04, but graphics problem from 12.10 to 15.10.  16.04 every distro worked except for the Linux Lite I was was using.

---

### Post by sdsurfer on 2020-11-02
My list:

- On the first boot it was something I'd never seen before, wouldn't boot, couldn't access command line, seemed to go into a loop of black screen, cursor, black screen cursor. I could get into bios. I found a System 76 article that demonstrated how to repair/reinstall GRUB. Once it fixed GRUB, loaded fine (mostly.)

- App based issues: I have a thread in General about "black panels" in Slack. Turns out hardware acceleration needs to be disabled (Nvidia GPU, of course.) They are "working on it." As time went on I also noticed black-panel weirdness in Chrome as well, disabling hardware acceleration in Chrome also fixed that. I'm using latest versions of everything, tried reverting the Nvidia driver, no love. So there appears to be a hardware acceleration issue in some apps for the Nvidia GPU.

- In 18.04 I had a terrible time mapping print screen. Sometimes it worked, sometimes it didn't, I resolved to pinning the screen cap icon to my task bar. The problem that creates is when I need to communicate the state of a web page drop down list in a capture, clicking away to launch the app lost focus on the drop down list and it closed, making it useless. That seems to have been fixed, FN+Print Screen appears to be working normally.

- Not seeing a lot of other negatives or positives. Don't dig some of the icon changes, but ok, I'll get used to them.

---

### Post by Deep_Peasant on 2020-11-02
> **CatKiller said:**
> To the OP: people don't generally post about things that are tickety-boo. You can't make any conclusions about the relative proportions of people with problems to people without, since you never hear from the people without. 

Nice downplay, now count the number of threads appearing in the last month.

> **CatKiller said:**
> 
None of the letters in LTS are for stable, except that the first one is "Long."

Stable in software means that it *doesn't change*. And LTS releases don't. The software only changes through the Hardware Enablement Stack, or the Stable Release Updates mechanism, and it gets security updates and bugfixes, for five years. **You've chosen *not* to stay with the LTS release.**

Come again?

[Xubuntu help]("https://xubuntu.org/help/")

   >  Xubuntu 20.10 (Groovy Gorilla), supported until July 2021
    Xubuntu 20.04 (Focal Fossa), supported until April 2023
    Xubuntu 18.04 (Bionic Beaver), supported until April 2021

[Xubuntu migrating upgrading]("https://docs.xubuntu.org/current/user/C/migrating-upgrading.html")

> New regular releases of Xubuntu are released every 6 months and Long Term Support (LTS) releases every 2 years. Currently, regular releases are supported for 9 months and LTS releases for 3 years.

the Software Updater will inform you when a new version for your upgrade path is available for download.

I'm 'due' for upgrading and so far I'm not a 'happy camper'.

---

