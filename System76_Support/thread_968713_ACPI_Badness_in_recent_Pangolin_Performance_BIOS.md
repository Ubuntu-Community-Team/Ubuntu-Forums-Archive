---
title: "ACPI Badness in recent Pangolin Performance BIOS?"
date: 2008-11-02
forum: System76 Support
---

### Post by bssteph on 2008-11-02
Disclaimer: I am a Gentoo user but I feel that, regardless of whatever versions of the kernel are shipping with Ubuntu, that this is a global issue. I bought from system76 as I love what you all are doing, but I'm a Gentoo guy all the way down. Regardless, this is not a request for support so much as it is more information. Moving on...

My Gnome power manager applet dealy never seems to activate the "On Battery Power" settings (e.g. what to do when the lid is closed when on battery, and so on).

With some digging, I'm pretty convinced that the applet uses on_ac_power to determine the state it's in. Thing is, mine always returns 0 (which is "true" in this context). It notices that the battery is discharging and all that other fun stuff, but never considers itself off of AC.

Further digging and I found this in my kernel log:

```
...
Nov  2 12:36:05 rydia ACPI Error (psargs-0358): [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND
Nov  2 12:36:05 rydia ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.ADP0.ADJP] (Node ffff88013f819500), AE_NOT_FOUND
Nov  2 12:36:05 rydia ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.ADP0._PSR] (Node ffff88013f8194c0), AE_NOT_FOUND
Nov  2 12:36:05 rydia ACPI Exception (ac-0136): AE_NOT_FOUND, Error reading AC Adapter state [20080609]
Nov  2 12:36:05 rydia power_supply BAT0: uevent
Nov  2 12:36:05 rydia power_supply BAT0: No power supply yet
Nov  2 12:36:05 rydia power_supply BAT0: power_supply_changed
Nov  2 12:36:05 rydia power_supply BAT0: power_supply_changed_work
Nov  2 12:36:05 rydia ACPI: Battery Slot [BAT0] (battery present)
Nov  2 12:36:05 rydia input: Power Button (FF) as /class/input/input0
Nov  2 12:36:05 rydia ACPI: Power Button (FF) [PWRF]
Nov  2 12:36:05 rydia input: Lid Switch as /class/input/input1
...
```

Now, I don't speak ACPI very well, but that looks like a problem. Also, my ACPI area for the ac_adapter is empty:

```
cthulhu@rydia ~ % ls -la /proc/acpi/ac_adapter
total 0
dr-xr-xr-x  2 root root 0 2008-11-02 21:27 .
dr-xr-xr-x 10 root root 0 2008-11-02 12:36 ..
```

Basically, I'd like to confirm/compare with other recent Pangolin Performance users and techs.

Model: Pangolin Performance panp4n
Kernels tried: 2.6.27 series
BIOS version: This is interesting, it's newer than advertised on the wiki (1.00.12b):

```
rydia ~ # dmidecode -s bios-version
1.00.13 
```

Again, this isn't necessarily a plea for help, but if someone can confirm one of:

* this does happen to new models w/Ubuntu
* I shouldn't have that BIOS version
* it works for whatever the normal Ubuntu version is and it's broke because I'm using Gentoo and therefore I get to keep both pieces

that'd be great. Thanks. :)

---

### Post by Lee_Machine on 2008-11-03
I too have the new Pangolins: panp4n

upon upgrading to 8.10 I get random system freeze that requires reboot. happens from every 10 minutes to a few hours.

Also i have found that my Ethernet port does not work but at least wireless does.

upon looking at my system logs right before the crashes there is the same ACPI error along with nvidia errors.

Ubuntu needs to up their standards for the laptop support.

Any help please?

---

### Post by thomasaaron on 2008-11-03
Lee_Machine, 

Please, let's stick to the original post you placed this in. Ideally, each thread should focus on one issue. Otherwise they become less useful to others trying to research various issues.

---

### Post by thomasaaron on 2008-11-03
bssteph,

I think this might actually be a gentoo issue. There was a point early on in out testing that lid-closed actions didn't work in Ubuntu. However, an upgrade came down that fixed it. So, my guess is that this fix hasn't appeared in Gentoo yet.

---

### Post by bssteph on 2008-11-03
thomasaaron, thanks for the reply, but I think I introduced a red herring. The lid events themselves work fine. I can write a shell script to run whatever command on close, and acpid will run said script and log the appropriate lid events and everything. The problem seems to be entirely with the AC adapter, which is why I picked that out of the log.

For example, the /proc interface for ac_adapter is empty. I never see ac_adapter events logged by acpid (if it does log those -- I can't really confirm that one :). When I mouseover the Gnome power manager applet, it will say I'm still on AC power when not.

So, the lid, I think, is fine. The question is if the off AC power events work (with my BIOS version)? Because if so then something is horked on my end, I won't deny it. But I'm kind of concerned about the BIOS version since it sounds newer than what the knowledge base is aware of.

(Alternatively, is there somewhere I can get past BIOSes (and how are they applied?)? I'd be willing to just try the known one and see what happens, if my version is indeed a surprise to everyone.)

All of the above not to sound contrary of course. Thanks for the help so far.

---

### Post by thomasaaron on 2008-11-03
Yeah, it's sounding more familiar. That's definitely the same issue we encountered. I'll have to ask R&D about it.

As I mentioned, it was definitely fixed by a proposed Ubuntu update, not by a bios update. We actually tried the bios-update avenue at first, and that had no effect.

I don't know if it was a kernel module update or a script. I'll see what I can dig up and report back.

---

### Post by bssteph on 2008-11-03
Cool, thanks a bunch.

---

### Post by bssteph on 2008-11-12
Any luck? Alternatively, can anyone point me towards where Ubuntu keeps the user-sanitized version of their kernel patches? I'd be willing to dig through a tarball or something for things that seem relevant.

Unless we're talking about the system76 drivers, because I might be wrong but I don't remember seeing anything relevant in there.

Thanks.

---

### Post by thomasaaron on 2008-11-13
Yeah, sorry. I forgot to report back. 

Talked to R&D. There are no bios updates to fix this. It was definitely an update that fixed it. But nobody is sure which one. This was pretty early on in the testing process, and we don't really record what updates fix what problems.

But maybe we should. Could be of service to our non-Ubuntu customers.

---

### Post by bssteph on 2008-11-13
That's cool. I'll poke around more, thanks!

---

### Post by bssteph on 2009-04-02
Sorry for the thread necromancy, but I'm on Linux 2.6.29 and still having the same problem with my AC adapter as quoted. I was wondering if someone with a Pangolin Performance could post/send me a dmesg log of them booting? I'm wondering if the problem could be because I'm using "Vista mode" and AHCI...

Anyway, sorry, and thanks. :)

---

### Post by bssteph on 2009-04-03
Never mind! I found a Sabayon forum post where the guy had the same generic problem and fixed it by building the ACPI AC adapter support as a module. That solved it for me too.

Nevertheless, thanks for the help thomasaaron.

---

### Post by CylnZ on 2009-05-25
Sorry to resurrect, but I have exactly the same error in dmesg. bssteph, do you by chance have the link for how you fixed it? I tried searching @ sabayonlinux but just got 1 hit for ati video. Any help or pointers appreciated. Thanks.

---

### Post by thomasaaron on 2009-05-26
See...
[http://ubuntuforums.org/showthread.php?t=1155641&highlight=pangolin+battery](http://ubuntuforums.org/showthread.php?t=1155641&highlight=pangolin+battery)

---

