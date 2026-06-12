---
title: "Can't enter passphrase after install"
date: 2015-01-05
forum: Virtualisation
---

### Post by scoobi-doo on 2015-01-05
Same issue [as in [http://ubuntuforums.org/showthread.php?t=2198981]](http://ubuntuforums.org/showthread.php?t=2198981]) with Kubuntu 14.10 installed as a [Virtualbox]("http://www.virtualbox.org/") guest OS on an encrypted LVM disk.  I get an "Enter passphrase:" label followed by a rectangular box, but no keyboard presses cause anything to be displayed (password stars, etc.).  Pressing [Right-Ctrl]+[Del] reboots the VM and I get a *text* prompt for passphrase, which displays stars as I enter the passphrase, and allows me to continue booting.  To me, seems to be an issue with the graphical UI which (I guess) is downgraded to text UI after rebooting detects it didn't succeed the first time.

---

### Post by Samundra_Shrestha on 2015-01-09
Maybe removing the GUI interface from Grub boot will help. So that next restart will always give the Text Interface for login.

---

