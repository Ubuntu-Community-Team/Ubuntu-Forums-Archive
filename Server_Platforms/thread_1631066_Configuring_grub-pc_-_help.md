---
title: "Configuring grub-pc - help"
date: 2010-11-26
forum: Server Platforms
---

### Post by ponsfrilus on 2010-11-26
Hi all,
   on an ubuntu 10.04 LTS server (standard install but on a virtual machien vmware) I launch a sudo aptitude upgrade and then I get this message:
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                                                                                                     &#9474; 
 &#9474; You chose not to install GRUB to any devices.  If you continue, the boot loader may not be properly configured, and when your computer next starts  &#9474; 
 &#9474; up it will use whatever was previously in the boot sector.  If there is an earlier version of GRUB 2 in the boot sector, it may be unable to load   &#9474; 
 &#9474; modules or handle the current configuration file.                                                                                                   &#9474; 
 &#9474;                                                                                                                                                     &#9474; 
 &#9474; If you are already running a different boot loader and want to carry on doing so, or if this is a special environment where you do not need a boot  &#9474; 
 &#9474; loader, then you should continue anyway.  Otherwise, you should install GRUB somewhere.                                                             &#9474; 
 &#9474;                                                                                                                                                     &#9474; 
 &#9474; Continue without installing GRUB?                                                                                                                   &#9474; 
 &#9474;                                                                                                                                                     &#9474; 
 &#9474;                                             <Yes>                                                <No>                                               &#9474; 
 &#9474;                                                                                                                                                     &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

What should I do ?

Thank for any help!

---

### Post by ponsfrilus on 2010-11-26
Finally th <no> options not allows me to do something, so I choose the <yes> one
```
Setting up linux-headers-generic-pae (2.6.32.26.28) ...
Setting up linux-image-2.6.32-26-generic-pae (2.6.32-26.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-26-generic-pae
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-26-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

