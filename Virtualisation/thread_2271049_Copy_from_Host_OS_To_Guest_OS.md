---
title: "Copy from Host OS To Guest OS"
date: 2015-03-27
forum: Virtualisation
---

### Post by programmer2 on 2015-03-27
I use virtualbox for run windows7 .  i want to copy some file from my main OS (ubuntu) to Guest OS (windows7)  ! how must do it ?!

---

### Post by howefield on 2015-03-27
Thread moved to the "*Virtualisation*" forum.

One way would be to use the "Shared Folders" option in Virtualbox ?

---

### Post by ajgreeny on 2015-03-27
It's in the settings for the Windows 7 VM Shared Folders, but in order to work you must install the VBox Guest Additions from [http://download.virtualbox.org/virtualbox/4.3.26/Oracle_VM_VirtualBox_Extension_Pack-4.3.26-98988.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.26/Oracle_VM_VirtualBox_Extension_Pack-4.3.26-98988.vbox-extpack)

---

### Post by TheFu on 2015-03-28
There are a few different ways. All network-based file sharing solutions work. You can pull or push or you can use the guestOS-to-hostOS file system connection method like ajgreeny pointed out.

So - pick which side you want to use to cause the transfer from and setup the server on the other side. Servers can be CIFS, ssh/sftp/scp - or some other, less good methods.

If I were doing it, I'd already have an ssh server running and use sftp/scp from the Windows VM to pull the files over. WinSCP is a nice client for Widnows - there are others.

---

