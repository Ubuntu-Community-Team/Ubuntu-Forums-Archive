---
title: "UEFI boot"
date: 2020-05-11
forum: Ubuntu, Linux and OS Chat
---

### Post by P-I H on 2020-05-11
I find it more convenient to use the UEFI boot menu from the motherboard instead of grub, in a multiboot computer with the systems on different disks.
There are at least three advantages
- You don't need hit CR when the grub menu is shown
- You can define your primary system in BIOS instead with updates in grub.
- When there is a kernel upgrade in your secondary system, you don't need to do sudo update-grub in your primary system.
One problem though is to hide the grub menu. I googled an found some ways, but none worked.
However I got some ideas and used GRUB_TIMEOUT=0.1 which worked.
This works fine on a computer with Ubuntu, Fedora and Windows.

---

### Post by vicsar on 2020-05-13
Completely agree. I actually hadn't thought of even using Grub for this before.

---

### Post by mastablasta on 2020-05-14
i don't know how is this on UEFI, but on MBR setup i set a shortcut to boot to windows once. so when they wanted to play a windows only game, they would click on widnows icon and the computer would reboot to windows (XP). when they are done, they would hit reboot in windows and be back to Linux. 

if UEFI is as similar to BIOS as i think it is you probably won't be able to do that there.

as for having multiple linux systems - i find it easier to use virtual machines for that. i used to have 5 test servers, a desktop and some live sessions setup in virtualbox. even my old single core machine could take it. let alone the modern multicore machines with plenty GB ram ...

---

### Post by CatKiller on 2020-05-14
> **mastablasta said:**
> if UEFI is as similar to BIOS as i think it is you probably won't be able to do that there.

You can use ```
systemctl reboot --boot-loader-entry=
``` to reboot into whichever EFI entry, as well as ```
systemctl reboot --firmware-setup
systemctl reboot --boot-loader-menu=
```
to reboot into the setup or boot menu, respectively.

---

