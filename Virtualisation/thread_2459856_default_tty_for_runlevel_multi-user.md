---
title: "default tty for runlevel multi-user"
date: 2021-03-27
forum: Virtualisation
---

### Post by luca31 on 2021-03-27
I installed a brand-new vm in qemu using the net installer [http://archive.ubuntu.com/.../focal/main/installer-amd64]("http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64?fbclid=IwAR0_uR4WKFC8UIrCQ0he33O5zvllHhHNXdOS7_YNC75EV-dIE9WYeiKW_QI") 

I've just pulled the base system
After that I changed the systemd runlevel from graphical to multi-user, the vm console was hooked to tty7 no matter the default runlevel (i had to send the keyboard interrupt to change terminal).

I solved modifying the following line in /etc/grub/default
GRUB_CMDLINE_LINUX_DEFAULT="text"

not found what systemd services is in charge of setting the default virtual terminal in case there's no windows manager installed
Obviousilly systemd-login is loaded and in charge of spawning getty when new vt is accessed from console 1-6 in the default confguration, but where is set up that the default virtual terminal is 7?

---

