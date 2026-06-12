---
title: "Xubuntu LTSP Server installation problems"
date: 2007-04-24
forum: Server Platforms
---

### Post by secunda007 on 2007-04-24
For some reason, whenever I try to install an Xubuntu (7.04) LTSP server, the installation fails to build the LTSP chroot (with error code 1), with the command-line giving an error of "couldn't find package usplash-theme-ubuntu." Although I've setup the DHCP server, I can't boot a second PC over the network. Does anyone have any solutions? Thanks.

---

### Post by ernierasta on 2007-04-25
Ok, it looks like bug. I had the same problem. When I try to boot client TFTP error occurred. Here is solution:
delete i386 in opt directory, than run:
sudo ltsp-build-client
than configure /opt/ltsp/i386/etc/lts.conf to your needs.
EDIT: Oh I forget - maybe you will have to run  ltsp-update-sshkeys to be sure, that ssh keys are ok. BTW I am writing this from LTSP xubuntu client ;-)
Greetings!

---

