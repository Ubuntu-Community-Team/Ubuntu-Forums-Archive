---
title: "GRUB2: Password Protecting specific menuentries - not by type"
date: 2017-11-14
forum: Security
---

### Post by thebacon on 2017-11-14
Hey guys,

I'm trying to set up a public-facing Ubuntu computer so that it's accessible and usable, but still secure and easy to admin. USB storage is enabled so that customers can store their projects on removable media.

The setup: Ubuntu 16.04, using Lethe to freeze the public-use partition (installed as per [this guide]("https://community.spiceworks.com/how_to/90188-install-lethe-on-ubuntu-14-04-lts")), computer boots into the frozen OS automatically. Admin Ubuntu account password protected. Using Clonezilla to image the entire disc, so that I can always ensure an absolutely clean refresh with the appropriate programs already set up.

My problem is that currently if somebody knows how GRUB works, they can easily boot into the unfrozen copy of Ubuntu and, if they can bypass the Admin account password, make changes. I imagine there are also other vulnerabilities with the public being able to access GRUB.


I want to password protect the Terminal and config functionalities within GRUB, and also password protect the unfrozen Ubuntu installation, while allowing the frozen installation to boot automatically. I've scoured several guides in trying to understand how to do this. One hitch that I've found is that somehow the necessary files mentioned by many of these guides (10_linux, 30_OS-prober) have been removed from my /grub.d/ folder and into the /grub.d/backup/etc_grub_d/ folder.

Files in /etc/grub.d/
00_header
05_debian_theme
09_lethe_proxy
40_custom_proxy
44_linux_proxy
45_linux_xen
46_memtest86+
47_os-prober
48_uefi-firmware
49_custom_proxy
50_custom


Any ideas?

---

