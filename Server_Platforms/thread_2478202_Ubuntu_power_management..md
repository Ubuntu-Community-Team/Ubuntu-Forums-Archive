---
title: "Ubuntu power management."
date: 2022-08-19
forum: Server Platforms
---

### Post by Carl_Lambert on 2022-08-19
[COLOR=#1A1A1A][FONT=&amp]If the below looks familiar, its because i originally asked this on reddit last week and got nothing ¯\_(&#12484;)_/¯ , I'm sure the ability to detect a system is idle for PM purposes can't be solely for the laptop guys? anyway read on :)

=====

I've recently resurrected my old nas and installed jammy.
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]However, being a bit of a brute of a machine that's quite power hungry ( 8 spinning disks aren't cheap to run), I've been looking for ways to reduce its power consumption. On my travels, I came across this ->[https://ubuntuforums.org/showthread.php?t=2045541](https://ubuntuforums.org/showthread.php?t=2045541) . it is quite old but I love the principle. and want to build on it (will use a pi not a router for the proxy but I've not got that far yet.)
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]The problem I have is with powernap. it looks to be defunct. I can only assume it has been superseded by something more core to the OS itself. so now I'm on the hunt for what replaced it. and how I can configure it to, firstly emulate the behaviour of powernap to detect an idle machine and suspend when not in use. and secondly review what other tweaks on options the replacement systems have. (can I spin down my disk cluster if nothing has accessed a given filesystem (zfs) but keep the machine up for instance)
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]Happy to get technical and read through docs, the problem I have is the majority of search results are either related to pushing for more performance or laptop power management in general. and almost always results in a response to use the gnome power management tools (i don't even have an x server installed)[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]any help, suggestions, or pointer in the right direction here greatly received.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-09-05
> **Carl_Lambert said:**
> [COLOR=#1A1A1A][FONT=&amp]
...[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]However, being a bit of a brute of a machine that's quite power hungry ( 8 spinning disks aren't cheap to run), I've been looking for ways to reduce its power consumption. On my travels, I came across this ->[https://ubuntuforums.org/showthread.php?t=2045541](https://ubuntuforums.org/showthread.php?t=2045541) . it is quite old but I love the principle. and want to build on it ([/FONT][/COLOR][COLOR=#ff0000]will use a pi[/COLOR][COLOR=#1A1A1A][FONT=&amp] not a router for the proxy but I've not got that far yet.)
[/FONT][/COLOR]...

The problem in your "idea" seems to be on your choice of hardware. Output from my Pi4 (using the commands fron your link)
```

mafoelffen@ubuntu:~$ pm-is-supported --suspend && echo "Suspension supported" || echo "Suspension NON supported"
Suspension NON supported

```
Which make's sense, as Pi's do not have a BIOS with ACPI and related power settings in the BIOS. In fact, in the power settings available for my Pi4 in Ubuntu, the only available have to do with screen blanking and reduced performance.

EDIT: 
My 2 cents for NAS using a headless Pi4, powered USB Hub and M.2 NVMe... And not worry about hibernation or sleep.

---

