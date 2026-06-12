---
title: "Internal Error"
date: 2013-09-16
forum: Ubuntu Studio
---

### Post by Rick St. George on 2013-09-16
Question;  It seems that the below Error may be a security risk. It keeps coming up on every startup / logon.
Any ideas suggestions? I've already run Update.

Thanks!

------------------  BEGIN ---------------------

Ubuntu 12.04 Experienced an Internal Error

 

 Title
    accounts-daemon crashed with SIGSEGV in dbus_connection_send()
 

 ProcCmdline
    /usr/lib/accountsservice/accounts-daemon
 

 Package
    accountsservice 0.6.15-2ubuntu9.6
 

 Dependencies  (partial list)
    adduser

    base-passwd
    busybox-initramfs
 

 MarkForUpload
    True
 

 ProcStatus
    State:  S (sleeping)
 

 SegvReason
    reading NULL VMA
 

 UnreportableReason
     You have some obsolete package versions installed.  

     Please upgrade the following packages and check if the problem still occurs.
 

     Dbus, initramfs-tools, initramfs-tools-bin, tzdata
 

 UpgradeStatus
     Upgraded to Precise on 2012-05-07
 

 -------------------------------  END P/O ------------------

---

### Post by Iowan on 2013-09-16
Closed-duplicate:
[http://ubuntuforums.org/showthread.php?t=2174877](http://ubuntuforums.org/showthread.php?t=2174877)

---

