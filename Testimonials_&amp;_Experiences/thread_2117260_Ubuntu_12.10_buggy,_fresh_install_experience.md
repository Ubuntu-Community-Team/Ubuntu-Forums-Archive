---
title: "Ubuntu 12.10 buggy, fresh install experience:"
date: 2013-02-18
forum: Testimonials &amp; Experiences
---

### Post by screaminj3sus on 2013-02-18
Canonicol really, really needs to sort out their QA. Upon a fresh insall of ubuntu there is simply too many crashes and too many bugs. For example here is my latest experience with a fresh install of 12.10:

Install ubuntu 12.10, reboot.

Launch update manager, get all updates. near the end it randomly stops updating, telling me there's another package manager active, even though I've literally launched no applications but the update manager. Launch it again, finish updating, go to system menu to reboot, random compiz crash.

Boot up, random evolution-calendar crash. decide I want to setup ubuntu one. Sign in with my account, nautilus immediately crashes and ubuntu one just totally freezes. reboot and try again. ubuntu one signs in, but this time just hangs at "getting information" so I can't choose my folders to sync. was able to click next and choose them later. ubuntuone now "works" but at random it crashes on login and causes nautilus to have super high cpu usage, until I reboot again (and this is an issue I've seen on multiple clean installs).

What a mess...

---

### Post by carl4926 on 2013-02-18
> **screaminj3sus said:**
> Canonicol really, really needs to sort out their QA. Upon a fresh insall of ubuntu there is simply too many crashes and too many bugs. For example here is my latest experience with a fresh install of 12.10:

Install ubuntu 12.10, reboot.

Launch update manager, get all updates. near the end it randomly stops updating, telling me there's another package manager active, even though I've literally launched no applications but the update manager. Launch it again, finish updating, go to system menu to reboot, random compiz crash.

Boot up, random evolution-calendar crash. decide I want to setup ubuntu one. Sign in with my account, nautilus immediately crashes and ubuntu one just totally freezes. reboot and try again. ubuntu one signs in, but this time just hangs at "getting information" so I can't choose my folders to sync. was able to click next and choose them later. ubuntuone now "works" but at random it crashes on login and causes nautilus to have super high cpu usage, until I reboot again (and this is an issue I've seen on multiple clean installs).

What a mess...


Which of the two machines in your sig is this happening on?

---

### Post by screaminj3sus on 2013-02-18
the laptop

---

### Post by carl4926 on 2013-02-18
But isn't this a system 76 machine?

And did it ship with 12.04 or have you tried 12.04?

---

### Post by screaminj3sus on 2013-02-18
> **carl4926 said:**
> But isn't this a system 76 machine?

And did it ship with 12.04 or have you tried 12.04?

It shipped with 12.10. I've been an ubuntu user for a long time and just had to finally vent. I've tried 12.04, 12.10, and 13.04 multiple times, they all have their own really annoying problems (problems with 13.04 can be expected though, since its in development). 12.04 works better for the most part (no crashes and ubuntuone works fine), but has its own really annoying problems, particularly with unity's window management, such as open applications randomly disappearing from the unity launcher/alt tab switcher which I found to be a deal-breaking problem. And there's some big issues with 12.04.2 64-bit and steam/multilib.

I tried 13.04 development release too and a lot of things seem better (ubuntuone works fine here, much less crashes in general too), but some things aren't usable yet which is why I'm back on 12.10 (in 13.04 ubuntu-online-accounts is barely functional, half the plugins are broken, and pidgin just hangs after opening)

Its not a problem with the laptop, its ubuntu being buggy.

---

### Post by Tamlynmac on 2013-02-18
> carl4926
But isn't this a system 76 machine?

And did it ship with 12.04 or have you tried 12.04? 	

I know little about system 76 machines. Are they so tailored to the version they're shipped with, that they won't upgrade? Or, are you suggesting that the OP return to 12.04, due to the issues their pointing out?

My interpretation of the OP's post was that they were trying to do a fresh install in an effort to upgrade to 12.10. If the system did come with 12.04, then 12.10 is only one upgrade away from the machines original version.  :-k


To screaminj3sus:
Should you decide to try new releases, I'd suggested you do so on a separate partition or HDD. After testing and assuring your system is fully functional with the new release, you can then choose to upgrade. Assuming said upgrade is beneficial.

Just my $0.02

---

### Post by screaminj3sus on 2013-02-18
> **Tamlynmac said:**
> I know little about system 76 machines. Are they so tailored to the version they're shipped with, that they won't upgrade? Or, are you suggesting that the OP return to 12.04, due to the issues their pointing out?

My interpretation of the OP's post was that they were trying to do a fresh install in an effort to upgrade to 12.10. If the system did come with 12.04, then 12.10 is only one upgrade away from the machines original version.  :-k


To screaminj3sus:
Should you decide to try new releases, I'd suggested you do so on a separate partition or HDD. After testing and assuring your system is fully functional with the new release, you can then choose to upgrade. Assuming said upgrade is beneficial.

Just my $0.02

1. The machine came with 12.10. Only reasons I've hopped ubuntu versions (and other distros too) is because of how disappointed I was in 12.10.

2. They aren't really "specifically tailored" or locked down to specific ubuntu releases. They have very bog-standard linux compatible hardware. this machine has intel graphics, intel wireless, intel sound etc... for the most part the only thing the "system76 driver" does is workaround ubuntu bugs and occasionally add support for a piece of hardware not supported out of the box (for example on my machine everything works out of the box in every distro except for the realtek card reader, installing the driver for that and working around a lightdm bug is all the system76 driver does on this laptop).

This is not a problem with the system76 laptop, its hardware is about as linux compatible and standard as you can get. These are non-hardware related ubuntu bugs. Ubuntu simply has not been releasing very high quality releases lately. I have hopes for 13.04 though with their increased focus on QA, but 12.04 and 12.10 have really got my on my last thread of patience.

The last truly stable ubuntu release I used was 10.10. and trust me, I'm no gnome 2 fanboy, I love the unity interface and find it much more efficient, but its been a long time since I've seen an ubuntu release without so many issues.

---

### Post by carl4926 on 2013-02-18
> **screaminj3sus said:**
> It shipped with 12.10. 

Is there some official system76 support?

If it were me, I'd be splitting my HD space so I could test different options.
Try and establish if say Xubuntu works better or if different distros such as Mint.... and so on

---

### Post by Tamlynmac on 2013-02-19
> screaminj3sus
I totally agree with carl4926:
> 
If it were me, I'd be splitting my HD space so I could test different options.
Try and establish if say Xubuntu works better or if different distros such as Mint.... and so on

Maybe even try Debian stable or one of the other flavors of Ubuntu such as [Kubuntu]("http://www.kubuntu.org/") or [Xubuntu]("http://xubuntu.org/"). I've been Xubuntu "only" for about 4 months (after exclusively using Ubuntu since 7.04) and am very pleased. With all the available Linux distros, IMHO there's no reason to become fixated (not saying you are) on any one distro - especially if one's dissatisfied.

Good Luck

---

### Post by screaminj3sus on 2013-02-19
I was thinking about trying debian, but wanted to wait until wheezy became debian stable since that is supposed to happen soon.

---

