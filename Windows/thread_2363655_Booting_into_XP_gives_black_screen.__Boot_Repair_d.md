---
title: "Booting into XP gives black screen.  Boot Repair doesn't fix it"
date: 2017-06-12
forum: Windows
---

### Post by Docfxit on 2017-06-12
I'm trying to boot into XP.  I get a black screen. (No cursor) 
I tried Boot Repair and it doesn't fix the problem.
[http://paste.ubuntu.com/24844899/](http://paste.ubuntu.com/24844899/)

XP is installed (and was running) in the second partition.  Win7 is installed (and was running) in the first partition.
I have tried:
Hide all other partitions.
Remove all other hard drives.
Make XP partition active.
In Partition Magic repair MBR.
With the XP install disk running Startup Repair:
ATTRIB -H C:\boot.ini
ATTRIB -S C:\boot.ini
ATTRIB -R C:\boot.ini
Ren boot.ini Boot.ini.Old
BOOTCFG /Rebuild

    Set the Load Identifier to: Microsoft Windows XP Professional
    Set the OS Load Options to: /noexecute=optin /fastdetect

CHKDSK /R
FIXMBR C:
FIXBOOT C:
COPY CDDrive:\I386\NTLDR C:\
COPY CDDrive:\I386\NTDETECT.COM C:\

Can anyone help me get XP running?

Thank you,

Docfxit

---

### Post by oldos2er on 2017-06-12
Moved to Other OS, Windows.

---

### Post by yancek on 2017-06-13
First of all, I think you would get more help if you posted your question at a windows support forum because it has nothing to do with Ubuntu/Linux.

You indicate that both xp and win 7 were working but failed to mention what happened/changed that resulted in this problem. 
 The windows 7 bootloader should detect xp and create an entry for it.  I think you might be better off trying to boot 7 since7  you will need to manually configure the xp boot.ini file to boot 7.  If you can boot 7, try running bcdedit to create an entry for xp.  Read up on bcd first.

---

### Post by Docfxit on 2017-06-13
Thanks for the reply...

I have been trying to boot into Win7 since February. When I do I get a BSOD 0x7b in normal or safemode.  I have performed many things trying to get Win7 running.  I found a program called Boot Repair that claims to repair windows boot up problems.  After using the software and emailing them they said they can only help the people resolve boot up issues that give a contribution. I gave them a contribution and I haven't heard back since.  It says they either help people through email or here in the Ubuntu forums.  It's sounding like a scam to me.

Thanks,
Docfxit

---

### Post by yancek on 2017-06-13
Did you have xp installed and then installed windows 7 with it's bootloader?
Were you then able to boot both xp and windows 7?
Did you install xp after windows 7?  Windows bootloaders are backward compatible which means that in your case, if you installed 7 after xp, you should have seen boot entries when booting windows for windows 7 and xp.  If you installed xp after 7, good luck because you will have to manually configure the xp bootloader including the boot.ini file and I expect you will need advice from experienced windows users.

The boot repair software is free to download and use although I'm sure they take contributions.  There are hundred (maybe thousands) of posts here from people who have used it and posted the link and got help.  I think it can make minor repairs to boot a windows system but I'm not sure it can help in your situation.

It isn't clear from you post whether you can boot windows 7, can you?  If so, you will have much better luck creating a menuentry with bcdedit for xp in windows 7.  If you were able to modify the xp files to get it to boot, I'm not sure you would be able to boot windows 7.  The link below is to the microsoft site explaining using bcdedit.

[https://docs.microsoft.com/en-us/windows-hardware/drivers/devtest/adding-boot-entries](https://docs.microsoft.com/en-us/windows-hardware/drivers/devtest/adding-boot-entries)

What are you using to run the command you mention in your post?  XP CD, windows 7?
Without answers to the above questions there isn't much anyone here can tell you.

---

