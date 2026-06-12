---
title: "NTBackup and Samba"
date: 2008-02-21
forum: Server Platforms
---

### Post by perfecttao on 2008-02-21
Hi all.  

I'm running a Windows Small Business Server/Active Directory environment and successfully got Samba and full AD integration working (the Samba server appears as an AD client), and I can access the Samba shares from the domain controller using mapped drives and via UNC path, and can successfully write to the share.  

However, when I try to run a backup using NTbackup to the Samba server it fails.  

The event log for the backup says:

```


21/02/2008 14:41

-------------------------------

Date: 21/02/2008

Time: 14:41

User: Administrator

-------------------------------



Backup Runner started.

Launching NTBackup: ntbackup.exe backup "@C:\Program Files\Microsoft Windows Small Business Server\Backup\Small Business Backup Script.bks" /d "SBS Backup created on 21/02/2008 at 14:41" /v:yes /r:no /rs:no /hc:off /m normal /j "Small Business Server Backup Job" /l:s /f "\\Rcfedora\Backup\Backup Files\Small Business Server Backup (02).bkf" /UM

NTBACKUP LOG FILE: C:\Documents and Settings\SBS Backup User\Local Settings\Application Data\Microsoft\Windows NT\NTBackup\data\backup10.log

=====================<BEGIN NTBACKUP LOG FILE>=====================

Backup Status

  The operation was not performed because the specified media cannot be found.



----------------------



=======================<END NTBACKUP LOG FILE>=====================

NTBackup finished the backup with errors.



For more information about failed backups, see the article on troubleshooting your backup at the following Web page: http://go.microsoft.com/fwlink/?LinkId=18414



Backup ended at 21 February 2008 14:41

Backup Runner finished.
```

Any ideas?

---

### Post by perfecttao on 2008-02-21
Further development - it appears to work when I start the backup manually - it just doesn't work as a scheduled task!!!

---

### Post by torgrot on 2008-02-21
Are you running the scheduled task as administrator?  Is the share mapped for the adminitstrator account?  As a side note, I believe that Samba only allows for a 2GB file size from Windows, so unless you can split the backup into multiple files NTBackup is not going to work.

torgrot

---

### Post by perfecttao on 2008-02-22
Thanks for the reply!

As mentioned, the backup works fine when manually run - so it's accepting a file size of 20Gb plus......(in .bkf format).  I've also specified the backup using UNC paths rather than a mapped drive, as I was aware this was a problem.  I've also specified the Administrator account (which can write files to the Samba server) on the scheduled task rather than the System account it defaults to.  Totally stumped.... :(

At the moment I'm having to VPN into the office at 9pm every night to run the backup.  Not a major inconvenience, but I can see it would start to wear a bit thin in the longer term.

---

### Post by yeleek on 2008-02-22
Can you get it to run as a batch job?  Try doing a net use to the share in your batch job prior to the backup just to confirm connection is there.  

Once batch job works just schedule using at or schtasks.

---

### Post by perfecttao on 2008-02-25
Thanks for that mate - kicking myself for not thinking of it myself.....

Thanks

Paul

---

