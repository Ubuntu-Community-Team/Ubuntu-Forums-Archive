---
title: "More viruses part 2"
date: 2010-01-14
forum: Security
---

### Post by mdquince on 2010-01-14
ok seems like there is some confusion about if clamav is coming up with false positives or are these really viruses but what I do not understand is this. everyone told me to use clamav for anti virus now ppl are bashing clamav.  anyway I reinstalled ubuntu again and the next day which is today i had 13 viruses and over 100 files or folder that clam could not access.  here is some of the error message that clam can not even clean or fix.  
DOES ANYONE KNOW WHATS GOING ON??  PLEASE HELP ME. 

PS I HAVE NEVER INSTALLED ANY LANGUAGE PROGRAM, OR ANYTHING OTHER THEN WHAT UBUNTU UPDATES SAYS TO INSTALL.  NO CHAT OR P2P EITHER.

There was a problem quarantining /usr/lib/xulrunner-1.9.1.7/libxul.so. Check your diskspace, the permissions on your quarantine location and whether a file with the same name already exists in the quarantine.
There was a problem quarantining /usr/lib/libgsf-1.so.114.0.15
 /usr/lib/erlang/erts-5.7.2/bin/beam.smp
 /usr/lib/openoffice/basis3.1/program/libpackage2.so

ACCESS DENIED IN OVER 20 ETC,TMP,SYS FILES OR FOLDERS???

---

### Post by barnex on 2010-01-14
I believe the only reason to run clamAV (or any virus scanner) on linux would be make sure that you pass no infected files to windows computers. E.g. if you have a mail server or samba share to which windows clients connect. Your linux system can not be harmed by those windows viruses and you should not worry. 

As you appear to run clamAV in user mode, it is normal that you have no access to your linux system files. I see little reason to scan them though.

---

### Post by rookcifer on 2010-01-14
This is not Windows and few things work like they do in windows.  For one, your user account does not have free reign over the entire system as it does on a default install of windows.  This is why clamav is saying it can't access those files.  

Secondly, there is no reason whatsoever to run an AV scanner on a desktop box (this is a desktop box, right?).  All it does is result in threads such as this where newbs get confused and panic at every false positive.

Thirdly, you will need to provide more info, as you have given us nothing with either of your threads.  Is this a desktop box?  What were you doing that prompted you to run a scan?  Most importantly: have you installed any software not found in the repos?

---

### Post by running_rabbit07 on 2010-01-14
OP, you are chasing your tail with these AV scans. If you disable those xulrunner files, you will have problems. There are multiple language packs installed from the beginning, you have the ones from Ubuntu and the ones for OpenOffice amongst others. Those files that you are unable to quarantine are program library files. Xulrunner is used for Firefox and the second language pack is in an OpenOffice folder.

---

