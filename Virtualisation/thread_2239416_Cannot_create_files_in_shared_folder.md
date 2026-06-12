---
title: "Cannot create files in shared folder"
date: 2014-08-13
forum: Virtualisation
---

### Post by skewray2 on 2014-08-13
I have a shared folder for Fedora 9, running on top of Xubuntu 14.04. The virtual Fedora can read files, edit files, and delete files, but is unable to create files or directories. Being root does not help. Any suggestions?

Update: After a reboot, I now get a popup from SELinux after an attempt to create a file.  I am guessing that the NSA is the root cause here.

---

### Post by slooksterpsv on 2014-08-13
You say it's on a virtual? So is it shared folders via virtualbox or are you using Samba, NFS, etc. etc etc. for network transfer, or how specifically are you sharing a folder?

---

### Post by steve7777777 on 2014-08-14
> **skewray2 said:**
> I have a shared folder for Fedora 9, running on top of Xubuntu 14.04. The virtual Fedora can read files, edit files, and delete files, but is unable to create files or directories. Being root does not help. Any suggestions?

Update: After a reboot, I now get a popup from SELinux after an attempt to create a file.  I am guessing that the NSA is the root cause here.

VMware or VB? Can you add the shared folder to a SMB share to test?

---

