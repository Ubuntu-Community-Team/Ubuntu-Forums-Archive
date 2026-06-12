---
title: "clean windows via ubuntu"
date: 2010-01-29
forum: Security
---

### Post by TheShabz on 2010-01-29
Hi everyone,

I am dualbooting XP and Jaunty. I discovered some malware on XP which I am trying to eliminate. I have been able to keep it from starting up, but one of its effects is that it wont let me install new software. I used Avast to clean things up but though its finding it, it cant remove it. I downloaded hijackthis but now cant install it.

My question. Is there any software I can use from within Ubuntu to clean out my Windows partition? I already have the NTFS driver, if that helps any.

Please and Thanks.

---

### Post by wojox on 2010-01-29
Have you tried starting Windows in safe-mode by pressing the F8 key?

---

### Post by cdenley on 2010-01-29
If you can identify the malicious file, you can delete it (or move it) with ubuntu. I wouldn't count on any ubuntu utilities being able to identify malicious file, but there are virus scanners you can try (clamav, avast, etc).

---

### Post by wilee-nilee on 2010-01-29
> **cdenley said:**
> If you can identify the malicious file, you can delete it (or move it) with ubuntu. I wouldn't count on any ubuntu utilities being able to identify malicious file, but there are virus scanners you can try (clamav, avast, etc).

This is good information, if you install these in Ubuntu you can scan the windows files.

A very good malware remover to have in windows is malwarebytes as well. Get the free version and update whenever you scan.
[http://www.malwarebytes.org/](http://www.malwarebytes.org/)
Microsoft security essentials is a light persistent antivirus program with a small cpu use as well.

You also might want to have ccleaner as well to clean the windows temp files and other cleaning.
[http://www.ccleaner.com/](http://www.ccleaner.com/)

---

### Post by Sir Jasper on 2010-01-30
Hi,

Did you use the Debian version of Avast or the Windows version (see below)?

The best and surest way to fix the problem is to download a-squared free then 
go to:
[http://support.emsisoft.com/](http://support.emsisoft.com/)
and become a Forum member there. Then read the instructions carefully before posting for help in the Malware Removal section.
That may take some time, but I doubt there is a better free option (nor even a better paid option).

My regards

A-squared generally has the highest detection rates (for all malware), but the free version only has on-demand scanning.

The free Windows version of Avast provides active protection and is consistently among the top 5 with detection rates close behind a-squared.

---

### Post by Moozillaaa on 2010-01-30
I've attempted this before - modifying files in the Windows partition to eliminate unwanted processes from starting up (Norton/Symantec processes).

In the case of this software, it was tied somehow to Windows install/startup files, and I caused a small problem with Windows startup.

Problem is - you have to identify the files/data that are associated with the unwanted process, and EVEN THEN, if they have somehow integrated themselves with the Windows startup processes, you're jammed.

Another factor is does the unwanted process have to be running to be identified by removal programs - antivirus.

Moving around some files, and changing the filepaths of malware startup files might help, but then again, has the process integrated itself with Windows startup? And the processes/data for the malware even then must be identified.

Moving files around might be the safest of trial and error attempts, because it's easily reversible.




and too bad that some are clogging up the thread with responses that don't even address the question: 
> Is there any software I can use from within Ubuntu to clean out my Windows partition?
Booting up Windows is not work done from WITHIN Ubuntu.

---

