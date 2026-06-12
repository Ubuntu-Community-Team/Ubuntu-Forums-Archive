---
title: "Error message when computer waking up"
date: 2013-02-25
forum: System76 Support
---

### Post by etdoughe on 2013-02-25
Not sure if this is the place to ask this, but any help is greatly appreciated.

When my computer (Gazelle Professional) "wakes up", the following error message is displayed for a few seconds, then I am prompted with the normal login window. Each time the computer sleeps (say I close the lid), when it wakes up, 2 new lines with the same error are added. Everything seems to be working fine, but I would like to know what is causing these error messages and if this is a problem that I should be concerned with.

[ 656.144289] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 656.144290] PM: Device 00:08 failed to resume: error -19
[ 1298.878222] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 1298.878224] PM: Device 00:08 failed to resume: error -19
[ 1867.549503] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 1867.549504] PM: Device 00:08 failed to resume: error -19
[ 2697.668598] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 2697.668599] PM: Device 00:08 failed to resume: error -19
[ 4431.282672] usb 3-2: device not accepting address 2, error -71
[ 4468.374499] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 4468.374500] PM: Device 00:08 failed to resume: error -19


Any thoughts??

---

### Post by Kacey on 2013-02-26
```
dmidecode  | grep "0x80"
```

and you can check 

```
lsusb
```
 
I get this error when my usb wireless headset is connected.

---

### Post by isantop on 2013-02-26
> **etdoughe said:**
> Not sure if this is the place to ask this, but any help is greatly appreciated.

When my computer (Gazelle Professional) "wakes up", the following error message is displayed for a few seconds, then I am prompted with the normal login window. Each time the computer sleeps (say I close the lid), when it wakes up, 2 new lines with the same error are added. Everything seems to be working fine, but I would like to know what is causing these error messages and if this is a problem that I should be concerned with.

[ 656.144289] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 656.144290] PM: Device 00:08 failed to resume: error -19
[ 1298.878222] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 1298.878224] PM: Device 00:08 failed to resume: error -19
[ 1867.549503] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 1867.549504] PM: Device 00:08 failed to resume: error -19
[ 2697.668598] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 2697.668599] PM: Device 00:08 failed to resume: error -19
[ 4431.282672] usb 3-2: device not accepting address 2, error -71
[ 4468.374499] dpm_run_callback(): pnp_bus_resume+0x0/0x80 returns -19
[ 4468.374500] PM: Device 00:08 failed to resume: error -19


Any thoughts??

It's probably a USB device you have connected. If the system is resuming fine, then you likely don't have anything to worry about.

---

### Post by etdoughe on 2013-02-26
Kacey: dmidecode output does not contain 0x80. The highest handle is  0x0023. Could 0x80 be the same handle as 0x0008?

I'm also not sure what lsusb is telling me. 

Any other thoughts? Do you get your error even when your wireless headset is not connected?

isantop: I think it is something port/USB related because I don't recall this error until using externals (thumb drive, printer, headphones, etc.) But, with nothing connected (and after a reboot), I am still getting this error. Do you still think this is nothing to worry about?

Thanks!

---

### Post by etdoughe on 2013-02-26
This seems to eliminate the error message:

Change: GRUB_CMDLINE_LINUX=""
to: GRUB_CMDLINE_LINUX="i8042.nopnp"

in /etc/default/grub

Then a sudo update-grub, and then a restart.

Something to do with the trackpad. It has always worked. But now it still works, with no error message!

---

