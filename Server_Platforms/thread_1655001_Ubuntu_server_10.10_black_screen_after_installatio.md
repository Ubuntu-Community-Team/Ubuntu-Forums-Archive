---
title: "Ubuntu server 10.10 black screen after installation"
date: 2010-12-29
forum: Server Platforms
---

### Post by W13tje on 2010-12-29
Hi all,

I just installed the Ubuntu server 10.10...
afterwards i was trying to boot but i just got a black screen...
I also have windows7 on this laptop "Acer Aspire 5741"
I tought when it's trying to startup i see an error but inpossible to see wich error ;)

grtz

---

### Post by sgoran on 2010-12-29
Try with external monitor. Or if you installed shh with installation try to connect from diferent computer. Maybe it is not error. My gess its another framebuffer problem.

---

### Post by W13tje on 2010-12-29
So just try aother monitor then it should be fine? xD

---

### Post by IWantFroyo on 2010-12-29
If that doesn't work, it might be an acpi problem, though I thought those only happened to Toshibas.
Go into the command line, and find something that looks sorta like this:
kernel /boot/vmlinuz-2.6.18-3amd64 root=/dev/sda1
change it to:
kernel /boot/vmlinuz-2.6.18-3amd64 root=/dev/sda1 ro acpi=off noapic

If this lets you boot, set up linux and then open a terminal and type this command:
gksudo gedit /etc/default/grub

Look for a line that looks like this in the gediter window it just opened:
GRUB_CMDLINE_LINUX=""
Change it to:
GRUB_CMDLINE_LINUX="noapic acpi=off"

Hope that helps.

---

### Post by W13tje on 2010-12-29
sounds like an stupid question... how do it look for that line in the command line?? (totally a shame for me) (and new to ubuntu)

---

### Post by W13tje on 2010-12-29
I'm just wondering how do i look for that line in the command line thing... cus i can't find it anywhere (i'm just new in linux btw)

EDIT: posted twice cus forum was abit laggy

---

### Post by W13tje on 2010-12-29
When i press "e"
i have this 
```
recordfail
insmd part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 86ba9dce-5f15-44ce-8f48-79a6abe\726
linux /boot/vmlinuz-2.6.35-22-server root=UUID=86ba9dce-5f15-44ce-8f\48-794a6ab7e726 ro     quiet
initrd /boot/initrd/img-2.6.35-22-server
```

---

