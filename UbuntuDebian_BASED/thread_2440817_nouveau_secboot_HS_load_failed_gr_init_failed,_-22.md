---
title: "nouveau secboot: HS load failed gr: init failed, -22"
date: 2020-04-15
forum: Ubuntu/Debian BASED
---

### Post by VitasLoWang on 2020-04-15
Hello, I try to install or run Live ISO of KDE Neon and get to a menu with options to live run or install, and other choices.
Whatever I choose however ends with a very fast blink of an error message (had to record a video of it to be able to read it)

nouveau secboot: HS load failed
gr: init failed, -22  
and then the screen loses signal and nothing happens until I press ctrl+alt+del

I read on forums that I should enable option nomodeset, so I press F6 in that menu, check nomodeset, press escape, try install or live run and end up with the same error!

My PC is Xeon x5670 @3.2GHz GA-X58-UD3R with GeForce 1080 Ti.

There is no settings related to secure boot in BIOS.
I got the same error with KaOS distro. Now I will try Kubuntu...

VIDEO of what I try: [https://photos.app.goo.gl/L9v9KWvn7Cp69PBJ8](https://photos.app.goo.gl/L9v9KWvn7Cp69PBJ8)

---

### Post by VitasLoWang on 2020-04-15
so guess what - I tried Kubuntu and it worked!
with option nomodeset I got a little bit further - screen did not lose signal, but was filled with dmraid errors. Seems like Ubuntu does not like my RAID setup. So I figured there is another option "nodmraid", so I checked it also and did "start Kubuntu" and it worked and I could install it! Seems like I am fine with this...
what about the RAID, any ideas with this?

---

### Post by lvm on 2020-04-16
As I once discovered at a considerable waste of time, md raid device discovery takes precedence over partition table contents. Perhaps some of your disks where once used in raid and retained valid superblocks which fooled dmraid. I also would strongly recommend against using nouveau as it is prone to random lock-ups, switch to proprietary nvidia driver.

---

### Post by howefield on 2020-04-16
Moved to the "Ubuntu/Debian BASED" forum.

---

### Post by VitasLoWang on 2020-04-16
Man I DO have RAID in my system right now! Besides that one independent drive for OS. I shrunk the C: drive to make another partition for Linux.
Regarding Nouveau - I don't really care which driver is being used. I just wanted to friking install some linux and could not! :-] So if the graphics driver is to blame here, then I think the developers should be addressed and not me :)
Still I wonder why neither Neon or KaOS booted and gave me that error. What is different with Kubuntu that it worked??
And how do I see my RAID volume in Kubuntu?

---

### Post by CelticWarrior on 2020-04-17
> I don't really care which driver is being used. I just wanted to friking  install some linux and could not! :-] So if the graphics driver is to  blame here, then I think the developers should be addressed and not me :smile:
Still I wonder why neither Neon or KaOS booted and gave me that error. What is different with Kubuntu that it worked??

You SHOULD care about which driver you NEED. Your graphics card really need Nvidia proprietary drivers. The default open-source *nouveau* driver is community developed for your convenience, with ZERO help from Nvidia. It doesn't mean it has to work for everything everywhere - it really doesn't, the newer the hardware the chances of it working acceptably with the unofficial driver are less and less - but works fairly well all things considered.
I don't know the specifics about the other distros but maybe Kubuntu worked because it comes with a newer *nouveau* version?

In a nutshell, whether it (sort of) works or not, you should install Nvidia proprietary drivers. For that, if you have no GUI at all, you may use a kernel boot parameter - nomodeset - until you install the proprietary drivers. Such installation in Ubuntu is even easier than in Windows, just open Additional Drivers, select the recommended version, apply (wait) and reboot.

---

### Post by VitasLoWang on 2020-04-19
Kubuntu already installed and works fine. I checked and Nvidia driver is in use, so I don't need to install it.
The question stays - how could I install a driver in a system which fails to even start live from USB flash or to install on a disk? :-D
And about nomodeset - what should it do? As you can see in my video this option didn't make KaOS or Neon live to boot.

---

### Post by CelticWarrior on 2020-04-19
> **VitasLoWang said:**
> Kubuntu already installed and works fine. I checked and Nvidia driver is in use, so I don't need to install it.
The question stays - how could I install a driver in a system which fails to even start live from USB flash or to install on a disk? :-D
And about nomodeset - what should it do? As you can see in my video this option didn't make KaOS or Neon live to boot.


Don't know KaOS. Maybe it needs/uses different bott parameters as a workaround.
KDE Neon should have booted the graphical desktop with nomodeset.
Your video shows a BIOS/Legacy boot. Is your system BIOS? Is it from 2010 or something? If so then maybe the graphics card is too much...

---

### Post by VitasLoWang on 2020-04-24
yes it is BIOS and Xeon x5670 @3.2GHz GA-X58-UD3R
BTW Windows works just fine with it :-]

---

