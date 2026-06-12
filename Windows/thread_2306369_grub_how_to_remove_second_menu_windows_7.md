---
title: "grub how to remove second menu windows 7"
date: 2015-12-15
forum: Windows
---

### Post by Alistair George on 2015-12-15
Hi there I installed Debian Mint/Grub then later Windows 7.
Get nice Grub boot with correct O/S Mint/Windows
but when I select Windows I get the second boot menu shown in picture with 2 Windows options. I want to be able to select Windows under Grub2 and not have the second menu at all is this possible? EG if I select Windows under grub I want to bypass the Windows boot manager and directly boot into Windows.
Thank you.
Alistair.

---

### Post by howefield on 2015-12-15
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2015-12-15
> I want to be able to select Windows under Grub2 and not have the second menu at all is this possible? 

No.  Grub chainloads windows systems and does not directly boot the proprietary windows filesystems so it basically points to where the windows boot files are and turns the booting over to the windows bootloader.

---

### Post by MikeMecanic on 2015-12-16
> **Alistair George said:**
>  I want to be able to select Windows under Grub2 and not have the second menu at all is this possible? 

You must do a fresh install of Win 7 to get rid of the second screen. If you upgrade to Win Ten, you'll boot directly in Win Ten.  What do you see in the terminal there?:

```
[LEFT][FONT=Courier New, serif]sudolsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL[/FONT][/LEFT]
```

---

