---
title: "Server Screen Settings"
date: 2012-01-05
forum: Server Platforms
---

### Post by SylenThunder on 2012-01-05
Ok, first off, I'm running Server edition 10.04 64-bit.

My CRT has a native resolution of 1280x1024 and the server like to choose that resolution with 130x80 text lines or something similar. 
Basically I want for it to either A. use a smaller resolution like 800x600, or B. use a larger font so it's easier to read.

It would also be nice if I could either disable, or dramatically extend the screen timeout. Even disabling ACPI in BIOS did not have any effect.

I've used Google to my hearts content and have not been able to find a viable solution that actually works. Found loads of suggestions, but so for no thread or anything that says this fixed it. Tried several myself, and in the end, had to wipe the drive and re-install the server because it fubared Grub to the point that the system was barely useable.

---

### Post by papibe on 2012-01-06
Hi SylenThunder.

The only I can think of is to use the grub option 'GRUB_GFXMODE'. Check this grub [tutorial]("https://help.ubuntu.com/community/Grub2").

Hope it helps.
Regards.

---

### Post by SylenThunder on 2012-01-06
> **papibe said:**
> Hi SylenThunder.

The only I can think of is to use the grub option 'GRUB_GFXMODE'. Check this grub [tutorial]("https://help.ubuntu.com/community/Grub2").

Hope it helps.
Regards.

Sadly, no it did not change anything. =(
I un-commented GRUB_GFXMODE and ran update-grub, then rebooted and it's still the same.

I'm sure that there's got to be a way to successfully change the command line interface, I just haven't found it yet. >.<

---

### Post by papibe on 2012-01-06
There's a way, although I haven't have success with it (mainly because I tried it on a machine with a corrupt EDID). So take this with a grain of salt.

The command 'fbset' should be able to set different resolutions and timings in a text mode console. First let's see what information is possible to get from you monitor.

Could post the result of this command?
```
sudo fbset -i
```
Regards.

---

