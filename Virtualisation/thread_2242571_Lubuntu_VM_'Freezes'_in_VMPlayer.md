---
title: "Lubuntu VM 'Freezes' in VMPlayer"
date: 2014-09-02
forum: Virtualisation
---

### Post by graylinux on 2014-09-02
Hi

I have a Lubuntu (14.04) O/S running as a virtual machine in VMWare's VMPlayer. It is hosted on a Windows 7 machine. I am using it as a LAMP web server so it will run largely unattended.

All works great apart from the fact that, after a period of inactivity, Lubuntu's desktop 'freezes' up. That is to say it does not accept input from the mouse or keyboard. I can, however, ssh into it. I can 'restore' the desktop back to the login prompt by stopping and starting the lightdm service via ssh.

I thought it may be due to default power settings in the Lubuntu image so I have the power-manager set to start at startup and configured to 'never sleep'. I have added a line to GRUB to set the console to never go 'blank'. I have set the windows host to 'never-sleep' and reloaded VMWare's tools so I am just about out of ideas.

I know this is compounded by the fact it's a VM (and may add this to VMware's forum) but I wonder if there's a pointer given that a simple lightdm stop and start cures it?

Any ideas anyone please?

---

### Post by holtalanm on 2014-09-25
I have the exact same issue.  It is definitely frustrating, to say the least.

---

### Post by slickymaster on 2014-09-25
*Moved to the ***Virtualisation*** sub-forum*

---

