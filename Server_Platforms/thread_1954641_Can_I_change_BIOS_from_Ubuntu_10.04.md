---
title: "Can I change BIOS from Ubuntu 10.04?"
date: 2012-04-08
forum: Server Platforms
---

### Post by deepakdeshp on 2012-04-08
I need to disable the all the USB and IDE ports in the BIOS from the os .  Is it possible?

---

### Post by darkod on 2012-04-08
Why from the OS?

BIOS is usually independent of OS. When you turn on your computer enter into BIOS and disable what you want to disable. If you disable something in BIOS, the OS is acting like it never existed.

---

### Post by deepakdeshp on 2012-04-08
> **darkod said:**
> Why from the OS?


I want to automate the BIOS set up. If I have many servers to set up, I would have the same BIOS set up by just executing a script from the OS rather than manually checfking and changing each BIOS value.

What is the way to automate uniform BIOs settings across many machines?

---

### Post by darkod on 2012-04-08
If they are identical, configure one BIOS as you want it, make a backup file (the option should be available with any newer board), and simply restore on the other machines.

I have never heard configuring BIOS from the OS, especially linux. Not to remind you that if anything goes wrong, you can make your board (machine) unusable.

That is why I never use the windows software for BIOS updates, prefer to do it on BIOS level. It's risky to me to let windows touch it and kill my board.

I haven't heard of programs for linux/ubuntu that can do BIOS updates/modifications.

---

### Post by CharlesA on 2012-04-08
You can only change settings in the BIOS from the bios.

---

### Post by Cheesemill on 2012-04-08
> **CharlesA said:**
> You can only change settings in the BIOS from the bios.

Not strictly true, I can change my BIOS overclocking settings using Linux software.

It is also possible to change all settings in the BIOS of some HP machines, but this uses VB scripts. I don't think it can be done from Linux.

---

### Post by roelforg on 2012-04-08
If all you want to do is disable ports, plugs and hw...
Just put the kernel modules for those components on the blacklist,
if they don't get loaded (or even completely removed) the kernel doesn't know what to do so you get the same effect.
If you have identical systems there's a even better way!
Just make the kernel module directories a share from a master server and have the blacklist/whitelist/modulelist on a share as well. Just dis/enable the right files and modules, reboot the server (with your bios thing you can't get around that so it shouldn't matter) and enjoy.

---

### Post by CharlesA on 2012-04-08
> **Cheesemill said:**
> Not strictly true, I can change my BIOS overclocking settings using Linux software.

It is also possible to change all settings in the BIOS of some HP machines, but this uses VB scripts. I don't think it can be done from Linux.
Ah. I haven't messed with overclocking in a long while.

I suppose the kernel module route would be the easiest, but it still wouldn't prevent someone from booting off a livecd and accessing whatever.

A better way to do it would be to have the servers some place where they can by physically secured because physical access = root access.

---

### Post by roelforg on 2012-04-08
> **CharlesA said:**
> Ah. I haven't messed with overclocking in a long while.

I suppose the kernel module route would be the easiest, but it still wouldn't prevent someone from booting off a livecd and accessing whatever.

A better way to do it would be to have the servers some place where they can by physically secured because physical access = root access.

Indeed,
I don't think disabling IDE and USB can really secure a lot, if you can access it physically you can init=/bin/sh it.

---

