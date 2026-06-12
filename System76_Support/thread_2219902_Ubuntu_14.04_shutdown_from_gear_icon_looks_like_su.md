---
title: "Ubuntu 14.04 shutdown from gear icon looks like suspend but doesn't wake up"
date: 2014-04-25
forum: System76 Support
---

### Post by apdobaj on 2014-04-25
[LEFT][COLOR=#333333][FONT=UbuntuRegular]Old Darter Ultra - When I select the Shutdown option from the gear icon the computer goes through the motions of shutting down but then gets stuck in what appears to be suspend (power LED blinks), but the wake from suspend key (Fn F4) doesn't work. The only way to wake it up is to hold the power button until the power light goes off, then use the power button to boot like normal. Same result with sudo shutdown -h now. Suspend mode works as expected. My Phoenix BIOS has no "wake on lan" feature.[/FONT][/COLOR][/LEFT]

---

### Post by apdobaj on 2014-04-28
I was able to capture the shutdown messages using the esc key (see attached)

---

### Post by Newbunto on 2014-04-28
Did you do a fresh install of 14.04 or did you upgrade?

I didn't have any problems with shutdown or hibernate (the only modes that I use) after my 14.04 upgrade but I have in the past had similar funny behaviour immediately after an upgrade. The problems have generally gone away fairly quickly, meaning I have no idea what actually sorted out the problem.

Perhaps check the relevant power management scripts. However as a vanilla shutdown command doesn't work, I doubt that that will help.

---

### Post by apdobaj on 2014-04-28
I just did the upgrade, I've got way too much installed (and all the subsequent tweaks) to start over. I'll look at the ACPI settings, any guidance on that would be appreciated.

---

### Post by apdobaj on 2014-04-29
I just tried changing the grub file to turn acpi off at boot, didn't help. Furthermore, the computer wouldn't boot.

---

### Post by Newbunto on 2014-04-29
Does

[SIZE=4][FONT=courier new]shutdown -P now[/FONT][/SIZE]

work?

---

### Post by apdobaj on 2014-04-29
No, nor does the -h flag.

---

### Post by apdobaj on 2014-05-15
Anybody have any wild ideas?

---

