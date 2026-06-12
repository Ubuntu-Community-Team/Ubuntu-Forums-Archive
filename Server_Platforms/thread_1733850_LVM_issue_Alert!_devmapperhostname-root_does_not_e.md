---
title: "LVM issue: Alert! /dev/mapper/hostname-root does not exit. Dropping to a shell!"
date: 2011-04-19
forum: Server Platforms
---

### Post by ThorinOak on 2011-04-19
I have an Ubuntu  x64 server that I came in to find not working. I recently did a V2V of  it but it was working after the move then started doing this.

I  pressed "c" from the Grub menu and did set and LS to get some  information. I also did "e" to try a change but to no avail. Kinda know  what is going on but not sure how to resolve.

Attached are sanitized images from GRUB.

---

### Post by Arand on 2011-04-19
I'm not sure if there might be an "insmod lvm" missing there
Also, isn't there an aful lot fo whitespace in the menu commands?

Here is what my LVM menuentry looks like for Debian, which I resume should be rather similar:```
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-amd64' --class debian --class gnu-linux --class gnu --class os {
        insmod lvm
        insmod part_msdos
        insmod ext2
        set root='(mellu-debboot)'
        search --no-floppy --fs-uuid --set 0c3d174d-32a3-4f9d-962a-0f787a12281a
        echo    'Loading Linux 2.6.32-5-amd64 ...'
        linux   /vmlinuz-2.6.32-5-amd64 root=/dev/mapper/mellu-debroot ro  quiet
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-2.6.32-5-amd64
```

---

### Post by ThorinOak on 2011-04-20
I tried adding the insmod lvm and it did the same thing. The white space is because I removed the server name. Below is what I get when I press e from the GRUB boot menu.
```

recordfail
insmod part_msdos
insmod ext2
search --no-floppy --fs-uuid d97ac62c-54bc-4c9a-8715-bebac2720262
linux /vmlinuz-2.6.35-28-server root=/dev/mapper/servername-root ro quiet
initrd /initrd.img-2.6.35-28-server
```

I booted to a LiveCD and tried nothing was mounted. I tried vgscan, fdisk -l, lvmdiskscan and nothing was found. Nothing in /proc/partitions either.

lvmdiskscan found ram0-15 and loop0 and lshal | grep 'block.device' found dev/fd0 and /dev/sr0.

---

