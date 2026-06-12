---
title: "Virtualbox 4.1.X freezes while updating"
date: 2012-07-15
forum: Virtualisation
---

### Post by em wai zee on 2012-07-15
Hi, I'm running an Ubuntu 12.04 64 bit LTS. Previously, I never have had a problem with Virtualbox in previous version. But, after upgrading Virtualbox, I need to enable usb controller to access my usb drives, printer, and etc. So, I've downloaded the Extension Pack from Oracle and upgrading it. While upgrading, it has frozen. Since then, I could not access my usb drives. So, anyone with prior knowledge or experience, is welcomed to help me. I'm clueless!

P.S; I've uploaded three screen-shots of the mentioned Virtualbox's!

---

### Post by Cheesemill on 2012-07-15
Try installing the Extension Pack from the terminal and see if it gives you any errors.
```
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.1.18-78361.vbox-extpack
```
(You will need to run this from your ~/Downloads/Softwares directory).

---

### Post by em wai zee on 2012-07-16
> **Cheesemill said:**
> Try installing the Extension Pack from the terminal and see if it gives you any errors.
```
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.1.18-78361.vbox-extpack
```
(You will need to run this from your ~/Downloads/Softwares directory).

Ok, as you could see from the screenshot which I've attached below ... You told me to install from the terminal, I've done it (TQ for that tip), but it keeps blinking like nothing happened. I left the process for an hour, and it still blinking. It didn't give me any errors. Just keep blinking idly! Emm ... I'm scratching my head endlessly now ...

---

