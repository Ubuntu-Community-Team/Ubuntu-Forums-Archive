---
title: "ltsp-build-image --chroot option don't associates nbd image name"
date: 2016-06-15
forum: Server Platforms
---

### Post by vanya2803 on 2016-06-15
I use xubuntu 16.04
I need ltsp thin+fat clients
I build 2 ltsp clients
[FONT=arial]1) fst client without option --chroot
chroot /opt/ltsp/i386; img /opt/ltsp/images/i386.img; tftp /var/lib/tftpboot/ltsp/i386[/FONT]
[FONT=arial]2) thin client with option --chroot i386thin
/opt/ltsp/i386thin;  img /opt/ltsp/images/i386thin.img; tftp /var/lib/tftpboot/ltsp/i386thin

fat and thin clients use nbdroot /opt/ltsp/images/i386.img

How to change nbdroot in initrd

for all x86_64 arch nbdroot = /opt/ltsp/images/amd64.img for all i386 arch nbdroot = /opt/ltsp/images/i386.img [FONT=Verdana]whatever setting --chroot[/FONT][/FONT]

---

