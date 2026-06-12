---
title: "Windows on Xen in ubuntu 8.04"
date: 2008-07-09
forum: Virtualisation
---

### Post by neptunix on 2008-07-09
Hi! I'm trying to install winXP as a guest os on Xen ubuntu 8.04 server.
I already have one guest ubuntu machine working like a charm and wish to run winXP as another one.

I've experienced two problems: 
[LIST]
[*]winXP can not see cdrom connected from iso image
[*]guest is not even created if I specify vif in the configuration file.
[/LIST]

What is the right way to connect cdrom from iso image? "file:/" and "tap:aio:/" aren't working at all.
tap:aio "writes" to the bios boot screen: could not read the boot disc.

Does anyone have a working windows installation in Hardy xen 3.2?

---

