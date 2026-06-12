---
title: "Visual glitch in VirtualBox VM using resolutions with 768"
date: 2019-02-13
forum: Virtualisation
---

### Post by wrootw on 2019-02-13
The problem is that if i set resolution for my Ubuntu 18.10 VM (same  with 18.04.1) to 1024x768 or 1280x768 some objects only appear on screen  when hovering with mouse cursor. 800x600, 1280x800 work fine.
Xubuntu 18.10 works ok with 1024x768, as well as Fedora 29 which also  uses Gnome. As i can’t get solution for this in VirtualBox forums, maybe  someone here would have a hint.

 The host is on Windows 7.

More detailed information is in VirtualBox forums post: [https://forums.virtualbox.org/viewtopic.php?f=3&t=91734](https://forums.virtualbox.org/viewtopic.php?f=3&t=91734)

---

### Post by howefield on 2019-02-13
Moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2019-02-13
Have you installed the [Extension Pack]("https://www.virtualbox.org/wiki/Downloads#VirtualBox6.0.4OracleVMVirtualBoxExtensionPack")?  It has a video driver with some proprietary features which can work better in some cases.

---

### Post by wrootw on 2019-03-20
Sorry for a late reply. I expected this forum to send an email notification (can't find a way to enabled them either).. I have tried to install the Extension pack now. The issue still persists.

---

### Post by wrootw on 2019-04-19
Update: in 19.04 i can use 768 resolutions again. Seems to be fixed.

---

