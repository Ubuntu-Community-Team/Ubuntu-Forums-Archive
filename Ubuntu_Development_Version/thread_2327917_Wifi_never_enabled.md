---
title: "Wifi never enabled"
date: 2016-06-15
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-06-15
Hi,
I created a bug report before I've thought I should ask here, sorry.

The wifi network worked fine while installing yakkety 16.10 from the 10  June's daily ISO.  Now it doesn't work at all. The "enable Wifi" option  in the indicator (top bar) has not the tick, but if I tick that option  the wifi cards on the list still show "Wifi is not enabled"
Can anyone help me? It's really annoying when the wifi never works :confused:


[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1591725](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1591725)

---

### Post by jimmy-frydkaer on 2016-06-16
I've had the same problem With that iso for Ubuntu GNOME - Wifi worked during installation but never after. Back to Ubuntu on an older iso for yakkety that just works.

---

### Post by enricobe on 2016-06-16
> **jimmy-frydkaer said:**
> I've had the same problem With that iso for Ubuntu GNOME - Wifi worked during installation but never after. Back to Ubuntu on an older iso for yakkety that just works.

Thank you! Can you please confirm the bug by adding "this bug affect me" vote?

---

### Post by rrnbtter on 2016-06-16
Greetings,
This problem has happened before with Network-Manager. The usual problem is installing an updated version of nm with an older libnm0. This should fix itself with this morning's updates which has a new libnm0 along with nm updates. I think you installed a daily iso that was in the middle of an update. You should be aware that 1610 is a development version and can be a problem from time to time. Having "Proposed" enabled in the software updates can also result in this same problem even though Cananical has tried to limit incomplete packages from being shown there for update. At any rate they have it fixed as of today. Or not!

---

### Post by enricobe on 2016-06-16
> **rrnbtter said:**
> Greetings,
This problem has happened before with Network-Manager. The usual problem is installing an updated version of nm with an older libnm0. This should fix itself with this morning's updates which has a new libnm0 along with nm updates. I think you installed a daily iso that was in the middle of an update. You should be aware that 1610 is a development version and can be a problem from time to time. Having "Proposed" enabled in the software updates can also result in this same problem even though Cananical has tried to limit incomplete packages from being shown there for update. At any rate they have it fixed as of today. Or not!

I've updated libnm today, but it still doesnt work :(
I know that 16.10 is a development version, but i don't use the PC so much and I can test it ;) I'm not afraid about bugs, but this wifi bug is REALLY annoying... I hope it will be fixed soon, otherwise I will have to reinstall a new daily image or a stable release

---

### Post by rrnbtter on 2016-06-16
Greetings,  
My suggestion is that you open "Software & Updates" from the DASH and choose "Developer Options" and then check off "Pre-released updates" for yakkety.
When you exit or close Software & Updates let the system refresh your apt cache when you are asked. Then open a terminal and run "sudo apt-get dist-upgrade". 
Allow it to upgrade all available software. Reboot so that any unattended upgrades can finish. If you still don't have wifi open a terminal and run "sudo apt-get install network-manager and see if you get any dependency errors. If yes copy and paste back the read out.

---

### Post by jimmy-frydkaer on 2016-06-17
Just fetched the iso today burned it to my USB and installed it - Network manager works just perfect

---

### Post by enricobe on 2016-06-17
I've enabled the pre-release update but it still doesn't work... Network manager is up to date.

I've run a "sud apt-get purge network-manager && sudo apt-get autoremove" thinking that I can install it again after the reboot:lolflag:
  [CENTER][COLOR=#000000]
=d> [/COLOR][COLOR=#000000]=d>
[/COLOR][/CENTER]


Now I really need to reinstall Ubuntu from a most recent daily

---

