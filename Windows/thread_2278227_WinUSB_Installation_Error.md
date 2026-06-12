---
title: "WinUSB Installation Error"
date: 2015-05-14
forum: Windows
---

### Post by jelanithompson on 2015-05-14
[COLOR=#111111][FONT=Ubuntu]I'm trying to create a bootable windows USB stick, but when I get to the installation process, it gives me this error:[/FONT][/COLOR]
```
Installation failed !
Exit code: 512
Log:
Formating device...
Mounting...
mount: block device /home/jelani/Downloads/en_windows_embedded_8.1_industry_pro_with_update_x64_dvd_4065122.iso is write-protected, mounting read-only
Copying...
Installing grub...
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
Error occured !
Syncing...
/usr/bin/winusb: line 78: 12032 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Cleaning...
/usr/bin/winusb: line 78: 29682 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Umounting and removing '/media/winusb_iso_1431635224_2922'...
Umounting and removing '/media/winusb_target_1431635224_2922'...

```

[COLOR=#111111][FONT=Ubuntu]Anyone know how I might be able to solve this error? Thanks!
[/FONT][/COLOR]

---

### Post by jelanithompson on 2015-05-15
Bump.

---

### Post by jelanithompson on 2015-05-16
Bumpity bump bump.

---

### Post by gordintoronto on 2015-05-17
Sorry, I don't understand what you are trying to do. Perhaps you are trying to make Windows 8.1 embedded boot from a USB stick? This is the wrong place to find the answer to that question.

---

### Post by Vladlenin5000 on 2015-05-17
The project WinUSB is as good as dead, as it seems.

Use a Windows machine, install the Microsoft USB tool, follow instructions, done.

---

### Post by bapoumba on 2015-05-17
*Thread moved to **Windows**.*

---

