---
title: "Problem with grub"
date: 2015-03-27
forum: Ubuntu/Debian BASED
---

### Post by john163 on 2015-03-27
Software Up To Date installed a new kernel for me today ( Ubuntu 12.04, kernel 3.13.0-48-generic)  After rebooting I ran grub customizer and got an error.  Same from update-grub:

```

joliver@JOHN-DEV:~$ !66
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found Windows Vista (loader) on /dev/sda1
Found CentOS release 6.6 (Final) on /dev/sdb1
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found Windows Vista (loader) on /dev/sda1
Found CentOS release 6.6 (Final) on /dev/sdb1
Found memtest86+ image: /boot/memtest86+.bin
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 146
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
```

Line 146 of /boot/grub/grub.cfg is:

```
menuentry "CentOS release 6.6 (Final) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set=root 3bc75d12-4328-4e95-9274-8a825181d0d2 **<<-Line 146**
        linux /boot/vmlinuz-2.6.32-504.12.2.el6.x86_64 root=/dev/sdb1
        initrd /boot/initramfs-2.6.32-504.12.2.el6.x86_64.img
}
```

Line 146 of /boot/grub/grub.cfg.new is:

```

menuentry "Ubuntu, with Linux 3.13.0-46-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root 105996f5-ba7e-46f4-b0de-eb5299a19563
        echo    'Loading Linux 3.13.0-46-generic ...'
        linux   /boot/vmlinuz-3.13.0-46-generic root=UUID=105996f5-ba7e-46f4-b0de-eb5299a19563 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.13.0-46-generic
}
function gfxmode {  **<<- Line 146**
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}
```

I have absolutely no idea if there are errors in /etc/default/grub or /etc/grub.d/*  I don't know what belongs in them.

How can I sort this out?

---

### Post by bardo2 on 2015-03-31
maybe not very helpful: i ran into failures as well after trying grub-customizer. The difference was: i had a backup to restore from afterwards.
and since, i ALWAYS check unknown software inside a virtual machine BEFORE introducing it into my main OS!

---

