---
title: "file system check fails"
date: 2018-03-01
forum: Ubuntu Development Version
---

### Post by brisch on 2018-03-01
I have a problem with ubuntu 1804, file system check starts but will not CTRL-C to stop and it locks up the computer. I have reinstalled the daily build but same problem.

---

### Post by cariboo on 2018-03-02
Maybe let the drive check continue until it's finished. I that still fails, boot from a live CD/usb, then run gmone-disks and select Smart Data & Self Tests from the hamburger menu. This is what mine looks like on my SSD:

---

### Post by brisch on 2018-03-02
I did the disk system check and it was ok. The problem is still the file system check which lock up and I can't use CNTRL-c to stop it. Once it starts it locks up hard and nothing I can do is but reboot. I can install from a live USB and it installs correctly and the first boot is ok however after that it will not work again as it tries file system check.

---

