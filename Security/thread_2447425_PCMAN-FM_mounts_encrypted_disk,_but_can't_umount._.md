---
title: "PCMAN-FM mounts encrypted disk, but can't umount. Why?"
date: 2020-07-18
forum: Security
---

### Post by spamhog on 2020-07-18
**Why? **

Lubuntu 18.04  LTS.
Extra SSD is on fstab as:
[INDENT]/dev/mapper/sdb1_crypt /home/fcc/polje ext4 noauto,user,noatime 0 2[/INDENT]

It mounts/umounts perfectly by unprivileged user.
[INDENT]mount /dev/mapper/sdb1_crypt
umount /dev/mapper/sdb1_crypt[/INDENT]

However PCMAN-FM can ONLY mount.
Dismounting by PCMAN-FM produces a dialog asking for user's password.

OK, mounting by file manager and umounting by user via CLI is also not permitted and requires sudo.
It doesn't matter if the drive is displayed in the file manager or not. Not a "drive busy" issue.

** BUT WHY DOESN'T PCMAN-FM HAVE THE SAME PRIVILEGES MOUNTING AND UNMOUNTING?**

Not a practical problem!
I solved it with a couple of desktop shortcuts.

[INDENT][Desktop Entry]
Name=MOUNT CRYPT
Exec=lxterminal  -e "mount /dev/mapper/sdb1_crypt; df -h;read"
Type=Application
StartupNotify=true
Icon=......

Desktop Entry]
Name=close crypt
Exec=lxterminal  -e "umount /dev/mapper/sdb1_crypt; df -h;read"
Type=Application
StartupNotify=true
Icon=...... [/INDENT]

---

