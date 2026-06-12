---
title: "windows 10 necessary in Virtualbox?"
date: 2020-12-28
forum: Virtualisation
---

### Post by boffin5 on 2020-12-28
Hi,
I installed Virtualbox hosted on Windows 10 on my laptop in order to run ubuntu.  In the help videos, I saw that they had Windows 10 also installed on Virtualbox, so I downloaded a Windows 10 iso file, and created a Windows 10 installation in Virtualbox.  However, since my Virtualbox is hosted on Windows, I'm not sure if it was necessary to do that.
Since my disc space is getting cramped, I'd like to remove the Windows 10 instl in Virtualbox, and delete the corresponding iso file.  But so far, ubuntu is working, and I'm scared to change anything.  Can I safely remove the Windows 10 instl from Virtualbox and delete the iso file?

---

### Post by howefield on 2020-12-28
Thread moved to the "*Virtualisation*" forum.

---

### Post by spjackson on 2020-12-28
If your sole objective is to run Ubuntu inside Virtualbox as per your first sentence, then there is no need to install Windows in a separate Virtualbox VM. There can be reasons for choosing to do that but that's nothing to do with your stated objective of running Ubuntu. You can safely remove the Windows VM and the associated iso without affecting the Ubuntu VM.

---

### Post by SeijiSensei on 2020-12-28
If you open the VirtualBox Manager application, you can right-click on a virtual machine icon in the left column and choose "Remove."  However you might first consider keeping a backup copy of the VM since you've already gone to the trouble of installing Windows.  Right-click the Windows VM icon in the Manager and choose "Clone." Put the cloned copy in a safe place in case you want to use it again someday. If you're extra fastidious you can check the copy by creating a new VM using the clone and File > Import Applicance from the Manager's menu.

---

### Post by boffin5 on 2020-12-28
Thanks for the help!
boffin5

---

