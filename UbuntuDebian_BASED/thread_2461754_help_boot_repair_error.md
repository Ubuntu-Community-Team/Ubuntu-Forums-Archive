---
title: "help boot repair error"
date: 2021-05-06
forum: Ubuntu/Debian BASED
---

### Post by atliv on 2021-05-06
hi, i just installed elementary OS and i got grub error, tried to repair my boot but i still get grub error

here's the log file from paste bin

[http://paste.ubuntu.com/p/95gNCzFmHK/](http://paste.ubuntu.com/p/95gNCzFmHK/)

---

### Post by oldfred on 2021-05-06
Elementary is not an offical flavor of Ubuntu.
Moved to other OS.

You have sda as gpt partitioned for UEFI, but sdb as old MBR(msdos). 
UEFI installs in sda look ok.

What error are you getting?
What brand/model system?
Can you directly boot both systems directly from UEFI boot menu?

---

### Post by atliv on 2021-05-06
yes i can boot to the both systems directly from UEFI, but when i try to unplug the usb, i always stuck at grub screen it's said "Minimal BASH like line editing is supported. For the first word, TAB lists possible command completions. anywhere else TAB lists possible device or file completions."

the system i use is ASUS a46cm with i3 processor

---

### Post by oldfred on 2021-05-06
Is sdb also a removable drive?
If so that is the issue.

Windows requires gpt partitioning for UEFI boot.
Ubuntu & then I assume Elementary allows you have install on sdb as MBR, but have UEFI boot entry on gpt drive. Not best configuration as better to only use gpt with UEFI systems, but it still should work.

You should have sdb as gpt and have it have its own ESP - efi system partition.
Conversion from MBR to gpt normally erases a drive. And at minimum requires full reinstall of grub as UUIDs all change.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by atliv on 2021-05-06
ah i see, my second drive is MBR (i'm using hdd caddy for secon drive), i should convert it to GPT i guess.
i will try to convert it now

---

### Post by oldfred on 2021-05-06
Some systems just do not want to boot from a caddy.
Even though a caddy slot had DVD that is bootable.

But some have configured boot on internal drive & system on caddy drive.

---

