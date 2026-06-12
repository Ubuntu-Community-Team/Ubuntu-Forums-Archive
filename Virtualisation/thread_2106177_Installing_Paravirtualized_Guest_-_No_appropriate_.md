---
title: "Installing Paravirtualized Guest - No appropriate installer"
date: 2013-01-18
forum: Virtualisation
---

### Post by sdpagent on 2013-01-18
Dear all,
It appears that using:
[[COLOR=#1155cc][FONT=Arial]_http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/xen/vmlinuz_[/FONT][/COLOR]]("http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/xen/vmlinuz")
[[COLOR=#1155cc][FONT=Arial]_http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/xen/initrd.gz_[/FONT][/COLOR]]("http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/xen/initrd.gz")


Or using:
[[COLOR=#1155cc][FONT=Arial]_http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot-xen/netboot/xen/vmlinuz_[/FONT][/COLOR]]("http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot-xen/netboot/xen/vmlinuz")
[[COLOR=#1155cc][FONT=Arial]_http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot-xen/netboot/xen/_[/FONT][/COLOR]]("http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot-xen/netboot/xen/vmlinuz")[COLOR=#000000][FONT=Arial]initrd.gz[/FONT][/COLOR]

Both result in the exact same install process. (The links may appear the same but one is netboot-xen/ and one is netboot/). Installing from either one both result in defaulting to the ext4 format instead of ext3 for virtual guests, and also installing the 'generic' kernel instead of the 'virtual' one. 

According [to this question]("http://askubuntu.com/questions/57336/minimal-system-or-minimal-virtual-machine-on-install") there is the option of a virtual machine install for ubuntu server, though I am unable to find it. Perhaps he is talking of an older version (Im using 12.04), or perhaps that applies only to a cd install instead of netboot? (I'm pretty sure I cant install from cd as that would require HVM which I cant have on a fully paravirtualized guest)

Does anybody know of an initrd.gz and vmlinuz pair that will just install the virtual kernel and default to ext3 format when partitioning so there are no pygrub bootloader issues? Perhaps I can somehow make a pair? Using apt to manually remove the generic kernel and add the virtual one is a pain. It works but am concerned about the occasional error message that flys by in text.

As always any help/info/advice is appreciated.

---

