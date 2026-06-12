---
title: "/boot/efi at 96%"
date: 2023-08-31
forum: System76 Support
---

### Post by kevinstevens on 2023-08-31
[COLOR=#000000]My /boot/efi is at 96% full and getting a warning I need to examine that directory.


[/COLOR]
[HR][/HR][COLOR=#000000]root@system76-pc:/boot/efi/EFI# df -kh /boot/efi[/COLOR]
[HR][/HR][COLOR=#000000]/dev/nvme0n1p1 487M 464M 23M 96% /boot/efi[/COLOR]
[HR][/HR][HR][/HR][COLOR=#000000]root@system76-pc:/boot/efi/EFI# du -skh *[/COLOR]
[HR][/HR][COLOR=#000000]100K BOOT[/COLOR]
[HR][/HR][COLOR=#000000]306M Pop_OS-10e07064-28b2-44f0-bfff-74712952d5f6[/COLOR]
[HR][/HR][COLOR=#000000]139M Recovery-E172-484E[/COLOR]
[HR][/HR][COLOR=#000000]100K systemd[/COLOR]
[HR][/HR][HR][/HR][COLOR=#000000]root@system76-pc:/boot/efi/EFI# cd Pop_OS-10e07064-28b2-44f0-bfff-74712952d5f6/[/COLOR]
[HR][/HR][HR][/HR][COLOR=#000000]root@system76-pc:/boot/efi/EFI/Pop_OS-10e07064-28b2-44f0-bfff-74712952d5f6# du -skh *[/COLOR]
[HR][/HR][COLOR=#000000]4.0K cmdline[/COLOR]
[HR][/HR][COLOR=#000000]152M initrd.img[/COLOR]
[HR][/HR][COLOR=#000000]133M initrd.img-previous[/COLOR]
[HR][/HR][COLOR=#000000]11M vmlinuz.efi[/COLOR]
[HR][/HR][COLOR=#000000]11M vmlinuz-previous.efi[/COLOR]
[HR][/HR][HR][/HR][COLOR=#000000]root@system76-pc:/boot/efi/EFI/Pop_OS-10e07064-28b2-44f0-bfff-74712952d5f6# lsblk[/COLOR]
[HR][/HR][COLOR=#000000]nvme0n1 259:0 0 465.8G 0 disk[/COLOR]
[HR][/HR][COLOR=#000000]&#9500;&#9472;nvme0n1p1 259:1 0 487M 0 part /boot/efi[/COLOR]
[HR][/HR][COLOR=#000000]&#9500;&#9472;nvme0n1p2 259:2 0 3.8G 0 part /recovery[/COLOR]
[HR][/HR][COLOR=#000000]&#9492;&#9472;nvme0n1p3 259:3 0 461.5G 0 part /[/COLOR]
[HR][/HR]Is it safe to remove these files or is there any other way to clear the space in /boot/efi?

---

