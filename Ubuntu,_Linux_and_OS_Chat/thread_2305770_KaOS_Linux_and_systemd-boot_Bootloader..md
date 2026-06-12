---
title: "KaOS Linux and systemd-boot Bootloader."
date: 2015-12-09
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2015-12-09
Recently I tried [KaOS Linux]("http://kaosx.us/") which is a lean KDE Plasma Distribution built from scratch. When I installed it on my Lenovo G50-24 which has UEFI, the Bootloader of KaOS did not detect the Ubuntu installation on another partition. When I updated grub2 on Ubuntu it did not detect the KaOS installation. I was curious.

It seems that UEFI install of KaOS uses [systemd-boot Bootloader]("http://www.freedesktop.org/wiki/Software/systemd/systemd-boot/") which puts the vmlinuz-linux and initramfs-linux.img files on EFI partition and checks for similar files for other Linux Distributions on this partition and does not find any.

When I update grub2 on Ubuntu it does not find these files on KaOS partition (since they are on EFI) and hence does not detect it.

However I could edit /etc/grub.d/40_custom and put the following lines to boot KaOS from grub2.
```
menuentry "KaOS 2015.11 GNU/Linux" {
set root='(hd0,gpt2)'
linux   /vmlinuz-linux root=UUID=78286359-59ce-4351-add9-7c5f4e899958 quiet systemd.show_status=0 resume=UUID=ea92b2ae-b20b-48c2-a7c5-4198e57a5653 rw
initrd  /initramfs-linux.img
}
```

But there is no way to boot Ubuntu from systemd-boot by editing any file on KaOS since this Bootloader can't access any partition other than EFI.

I am not a fan of KDE Plasma Desktop but trying KaOS added to my knowledge.

Kamalakar

---

### Post by grahammechanical on 2015-12-09
When the Debian developers were discussing changing from upstart to systemd as the init system some of the Debian developers did not like the way systemd was turning into something more than an init system. And now we get an idea just how far reaching the systemd developers want to go.

Is anybody going to complain about Redhat fracturing the ecosystem by bringing out an alternative to Grub? If this was Canonical doing something like this we would need a special section on the forum for trolls. Such would be the amount of complaints.

Regards.

---

### Post by kagashe on 2015-12-09
> **grahammechanical said:**
> When the Debian developers were discussing changing from upstart to systemd as the init system some of the Debian developers did not like the way systemd was turning into something more than an init system. And now we get an idea just how far reaching the systemd developers want to go.

Is anybody going to complain about Redhat fracturing the ecosystem by bringing out an alternative to Grub? If this was Canonical doing something like this we would need a special section on the forum for trolls. Such would be the amount of complaints.

Regards.systemd-boot Bootloader is NOT a part of systemd as init system.
systemd-boot is a new name for a Bootloader previously called gummiboot.

[gummiboot]("http://manpages.ubuntu.com/manpages/utopic/man8/gummiboot.8.html") also exists on Ubuntu as an alternative Bootloader.

[systemd-boot]("http://www.freedesktop.org/wiki/Software/systemd/systemd-boot/") is a UEFI Bootloader as per [specifications of freedesktop.org]("http://www.freedesktop.org/wiki/Specifications/BootLoaderSpec/").


Kamalakar

---

