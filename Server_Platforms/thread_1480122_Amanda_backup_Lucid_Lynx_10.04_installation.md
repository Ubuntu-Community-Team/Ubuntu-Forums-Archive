---
title: "Amanda backup Lucid Lynx 10.04 installation"
date: 2010-05-11
forum: Server Platforms
---

### Post by wbrb on 2010-05-11
Amanda and Lucid Lynx

After my 8.04 debacle here: [http://ubuntuforums.org/showthread.php?t=1231387](http://ubuntuforums.org/showthread.php?t=1231387), I basically gave up on trying to write an install guide for Hardy and Amanda. Others had done it better and with how muddled I was by the end of getting a working server, I wasn't sure I could repeat it.

Now in Lucid, I've managed to get another working amanda server going, I'm fairly sure I can repeat it and but I question:

Installation with 'apt-get install amanda-server' uses the user backup in the group backup.
Installation of the ZWC client uses the user amandabackup. while thankfully ZWC has included reg keys:

HKEY_LOCAL_MACHINE\SOFTWARE\Zmanda\ZWC\1.0\Install\BackupUser
HKEY_LOCAL_MACHINE\SOFTWARE\Zmanda\ZWC\1.0\Install\RecoveryUser

to change the user on the client, this is messy, requires regedit (which normally is locked out by group policy), editing the service in service.msc and creation of a new user account named backup in addition to the installer's default **on each client**.

The actual question is: 
1) Is there a reason for the use of backup:backup? (rather than amandabackup:disk or amandabackup:backup)  
2) Is there any sort of flag that could be set, script to change the user within the repo at install time.

Or generally an easier way of doing this than compiling each time I do an install.

---

### Post by stanleytberry on 2010-05-27
Did you ever find out?

**Could I just add the amandabackup user(s)** and delete the backup created by the install?

I've not used Amanda before but it appears to be what I want for a small network.  So I used 10.04 desktop and installed with Symantic.  That's as far as I've gotten.

---

