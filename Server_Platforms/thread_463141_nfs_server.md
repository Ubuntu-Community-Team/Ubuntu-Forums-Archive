---
title: "nfs server"
date: 2007-06-03
forum: Server Platforms
---

### Post by tj71587 on 2007-06-03
Hey there, I'm making an nfs server and following the steps on ubuntguide.org, and I was just wondering how I make a windows system see it and assign it to a letter (ie the T: drive).  Also, I am trying to even access it by giving the manual mounting command and it tells me mount:192.168.1.5: etc/export failed, reason given by server: Permission denied. (btw i did create a new folder named export inside etc just for this)

Thanks,

T.J.

---

### Post by vanadium on 2007-06-03
Windows does not work with NFS (unless there exixsts additional software to make Windows recognise nfs shares). To do file sharing with Windows machines, you are restricted to samba.

---

### Post by tj71587 on 2007-06-03
Thanks for the help

---

### Post by dmizer on 2007-06-03
you will need windows services for UNIX.  you can obtain it here: [http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx](http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx)

here are directons on how to make it work: [http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

though ... i have read that the license for that is pretty scary. and: "The product will not install on Windows 9x or Windows XP Home Edition or Windows Vista."

---

### Post by Brazen on 2007-06-03
> **dmizer said:**
> you will need windows services for UNIX.  you can obtain it here: [http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx](http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx)

here are directons on how to make it work: [http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

though ... i have read that the license for that is pretty scary.

Just to clarify, dmizer is talking about if you want to continue using NFS.  You do not need this if you use Samba.  

You could use Windows Services for Unix, but personally I find setting up Samba to be much much easier.

---

### Post by tj71587 on 2007-06-04
After I saw the first reply i looked up how to use samba and set it up, actually using dmizer's howto.  It's all up and working now, so thanks to both of ya.

---

