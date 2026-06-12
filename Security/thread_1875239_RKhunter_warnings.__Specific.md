---
title: "RKhunter warnings.  Specific"
date: 2011-11-04
forum: Security
---

### Post by Digi984 on 2011-11-04
I know there are alot of posts here about RKhunter warnings so forgive me for posting another but I am new to Ubuntu/Linux and alot of the advise in the other posts might as well be in Greek.


I ran rkhunter and got two warnings at the very end.  This is a copy from the log of the warning.

[13:51:04] Performing filesystem checks
[13:51:04] Info: Starting test name 'filesystem'
[13:51:04] Info: SCAN_MODE_DEV set to 'THOROUGH'
[13:51:07]   Checking /dev for suspicious file types         [ Warning ]
[13:51:07] Warning: Suspicious file types found in /dev:
[13:51:07]          /dev/shm/pulse-shm-1226644295: data
[13:51:07]          /dev/shm/pulse-shm-333104731: data
[13:51:07]          /dev/shm/pulse-shm-891528012: AmigaOS bitmap font
[13:51:07]          /dev/shm/pulse-shm-1563633527: data
[13:51:07]          /dev/shm/ecryptfs-digi984-Private: ASCII text
[13:51:07]          /dev/shm/pulse-shm-2796334262: data
[13:51:08]   Checking for hidden files and directories       [ Warning ]
[13:51:08] Warning: Hidden directory found: /dev/.udev
[13:51:08] Warning: Hidden directory found: /dev/.initramfs
-----------------

How do I fix the errors?  Are the a problem to the security of the system or is it just something that triggered a warning but isn't really a problem?


Any help would be greatly appreciated.  Thanks

---

### Post by Dangertux on 2011-11-04
This is a false positive, don't sweat it it's not something you would want to "fix"

---

### Post by Digi984 on 2011-11-04
> **Dangertux said:**
> This is a false positive, don't sweat it it's not something you would want to "fix"


Okay thanks.  Is there a way I can get it to not show up in future scans?  Also How do you tell?  I'm not second guessing but I just want to learn this stuff(Finally got sick enough of windows to switch about a week ago).

---

### Post by CharlesA on 2011-11-04
> **Digi984 said:**
> Okay thanks.  Is there a way I can get it to not show up in future scans?  Also How do you tell?  I'm not second guessing but I just want to learn this stuff(Finally got sick enough of windows to switch about a week ago).
I'm not sure if there is a way to have it ignore those specific areas.

You can always google with the file in question to see if it's a false positive or not.

rkhunter is notorious for false positives.

---

### Post by Digi984 on 2011-11-04
> **CharlesA said:**
> I'm not sure if there is a way to have it ignore those specific areas.

You can always google with the file in question to see if it's a false positive or not.

rkhunter is notorious for false positives.


Okay thanks.   Other than rkhunter and chrootkit are there other tools that should be run?  I know Linux doesn't get 'viruses' in the traditional sense.

---

### Post by CharlesA on 2011-11-04
> **Digi984 said:**
> Okay thanks.   Other than rkhunter and chrootkit are there other tools that should be run?  I know Linux doesn't get 'viruses' in the traditional sense.
Look into app armor if you want to lock stuff down.

As long as you are careful, you'll be fine.

---

### Post by Digi984 on 2011-11-04
> **CharlesA said:**
> Look into app armor if you want to lock stuff down.

As long as you are careful, you'll be fine.


Okay thanks again for all the help!

---

