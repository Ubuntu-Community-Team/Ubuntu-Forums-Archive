---
title: "restore windows 7 through ubuntu"
date: 2013-12-20
forum: Windows
---

### Post by ojasgu on 2013-12-20
hi there ,
i have deleted a file file from the registry edit in windows and now its not booting .how can i restore my windows using ubuntu ofcourse.

---

### Post by ojasgu on 2013-12-20
Kindly help me

---

### Post by fantab on 2013-12-20
> **ojasgu said:**
> hi there ,
i have deleted a file file from the registry edit in windows and now its not booting .how can i restore my windows using ubuntu ofcourse.

I don't think you can fix Windows from Ubuntu. 
You will need either Windows Repair Disc or Windows Install Disc to perform Repairs in Windows.

---

### Post by holycow131415 on 2013-12-20
Youll have to do a system restore, or a repair. Then youll have to update grub from a livecd

---

### Post by Impavidus on 2013-12-20
How Windows works exactly is a secret kept my Microsoft. Apparently, that allows them to make more money. As a result it's already difficult for open source developers to let their software coöperate with a properly functioning Windows and other MS software. Fixing a broken Windows system is even harder. Still, Ubuntu may help you by allowing you to get your files of the affected Windows computer and onto a backup drive.

---

### Post by Mark Phelps on 2013-12-21
> how can i restore my windows using ubuntu ofcourse. Basically, you can't.

There are two ways to do a Windows restore, depending on what you have available:
1) If there is a Recovery partition on the drive, and the PC provides a way to boot into a Recovery mode -- that will completely replace the existing Windows install with a brand new one -- as the machine came first installed.  There is no common Recovery boot mode, so you will have to look into the documentation for your PC to see how this is done.
2) If you made an Image Backup of the PC to another drive or an external drive, you can boot from the restore media and do a restore that way -- but my guess is that you did NOT make such a backup.

You should seriously consider posting your question to the Windows Seven forums (sevenforums.com), as they may be able to help you do the restore.

---

### Post by gordintoronto on 2013-12-21
If the problem was a registry edit, this might help:
[http://www.linuxquestions.org/questions/linux-mint-84/windows-registry-editing-tool-for-linux-872370/](http://www.linuxquestions.org/questions/linux-mint-84/windows-registry-editing-tool-for-linux-872370/)

---

