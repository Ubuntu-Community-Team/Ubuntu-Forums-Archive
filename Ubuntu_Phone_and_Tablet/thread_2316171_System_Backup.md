---
title: "System Backup?"
date: 2016-03-05
forum: Ubuntu Phone and Tablet
---

### Post by WD_SeaSerpent on 2016-03-05
How do you perform ubuntu touch system backup? I mean, without developers tools enabled you only see /home folder mounted on mtp:/<yourdevice>
Is there anything like "adb" for android?

---

### Post by ales-horak on 2016-03-06
You can access the phone very easily via SSH/SCP, see [http://askubuntu.com/questions/601910/ssh-ubuntu-touch](http://askubuntu.com/questions/601910/ssh-ubuntu-touch)

---

### Post by grahammechanical on 2016-03-06
The person providing the answer to a similar question on AskUbuntu is a Canonical employee who has written phone apps and works with community developers who are developing the core apps. So, he knows a thing or two.

[http://askubuntu.com/questions/602850/how-do-i-backup-my-ubuntu-phone](http://askubuntu.com/questions/602850/how-do-i-backup-my-ubuntu-phone)

Another link that might prove useful to those interested in this subject

[http://ubuntuforums.org/showthread.php?t=2271884](http://ubuntuforums.org/showthread.php?t=2271884)

[http://www.nrtm.org/index.php/2015/04/25/phone-book-backup-ubuntu-phone-aquaris-e-4-5/](http://www.nrtm.org/index.php/2015/04/25/phone-book-backup-ubuntu-phone-aquaris-e-4-5/)

Regards

---

### Post by WD_SeaSerpent on 2016-03-06
Thank you all. But how is SSH different from enabling "developer tools"?

---

### Post by handaxe on 2016-03-07
Enabling "developer tools" allows users to access the device by "adb" or ssh (secure shell). SSH (or "phablet-shell" from the phablet-tools package) is a way of working remotely and securely (it is encrypted) on 'nix type systems and has a long, distinguished pedigree. Major attraction is that you can ssh into your phone over wifi and run commands as if in the terminal app. To use "adb", you need an usb cable connected between device and laptop etc.

---

