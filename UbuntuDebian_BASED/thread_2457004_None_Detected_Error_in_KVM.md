---
title: "None Detected Error in KVM"
date: 2021-01-23
forum: Ubuntu/Debian BASED
---

### Post by Crsh on 2021-01-23
Trying to assist someone with setting up a Windows virtual machine with KVM on Pop! OS 20.04. Every time she selects the Windows iso in virt-manager GUI it gives the error "None detected." Virt-manager CLI gives an unrecognized arguments error, and I don't have the exact commands used to know why that isn't working.

Versions:

libvirt 0.5.5-1
virt-manager 1:2.2.1-4ubuntu2

---

### Post by QIII on 2021-01-23
Where did the iso come from?  How was the iso prepared?  What medium contains the iso?

---

### Post by Crsh on 2021-01-26
Iso came from the Windows Media Creation Tool. It was stored on the desktop, but copying it to other directories gives the same issue.

---

### Post by CelticWarrior on 2021-01-26
> **Crsh said:**
> Iso came from the Windows Media Creation Tool. It was stored on the desktop, but copying it to other directories gives the same issue.
When downloading from any non-Windows system the webpage only gives you the option to download the ISO and that has nothing to do with the Windows Media Creation tool. It's purely the web browser doing a download like any other and like any other it can be corrupt, partial download, etc. Rare nowadays but still happen.

When downloading from a Windows system then, and only then, the Windows Media Creation tool is involved/called and, if I remember correctly its default is to to automatically "burn" an USB. Maybe it has some option to only download the ISO, not sure.

So, please describe exactly how the ISO was obtained. If you created an USB and then imaged it that's likely the problem. The ISOs Microsoft currently distributes don't follow standards and normal imaging tools are known not to work: [https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

---

### Post by TheFu on 2021-01-26
What are the major settings for the VM you are trying to install into? For example, a 32-bit VM can't accept a 64-bit OS. I'd expect a different error than "None detected.", but if there isn't a disk controller configured and connected to the CD/DVD virtual device, then ISO can't be accessed.

Posting the xml file for the VM would be helpful.
$ virsh dumpxml {vm name}
Please use code tags so it is readable. How: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
Make it easy for us to help, please.

---

### Post by Crsh on 2021-02-09
> **CelticWarrior said:**
> When downloading from any non-Windows system the webpage only gives you the option to download the ISO and that has nothing to do with the Windows Media Creation tool. It's purely the web browser doing a download like any other and like any other it can be corrupt, partial download, etc. Rare nowadays but still happen.

When downloading from a Windows system then, and only then, the Windows Media Creation tool is involved/called and, if I remember correctly its default is to to automatically "burn" an USB. Maybe it has some option to only download the ISO, not sure.

So, please describe exactly how the ISO was obtained. If you created an USB and then imaged it that's likely the problem. The ISOs Microsoft currently distributes don't follow standards and normal imaging tools are known not to work: [https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

It turned out to be the ISO. After re-downloading from MS, the issue did not re-occur.

---

