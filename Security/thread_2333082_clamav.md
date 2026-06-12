---
title: "clamav"
date: 2016-08-06
forum: Security
---

### Post by Reddoug on 2016-08-06
Hi All

Just updated to 16.04 server and now clamav will not update. I tried removing and reinstalling clamav, n/c.
Did not have any problem before upgrade from 14.10 LTS
Anyone else run into this?

Thanks, Doug

sudo freshclam
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

Sat Aug  6 17:12:53 2016 -> --------------------------------------
Sat Aug  6 17:12:53 2016 -> freshclam daemon 0.99 (OS: linux-gnu, ARCH: x86_64, CPU: x86_64)
Sat Aug  6 17:12:53 2016 -> ClamAV update process started at Sat Aug  6 17:12:53 2016
Sat Aug  6 17:12:53 2016 -> WARNING: Can't query current.cvd.clamav.net
Sat Aug  6 17:12:53 2016 -> WARNING: Invalid DNS reply. Falling back to HTTP mode.
Sat Aug  6 17:12:53 2016 -> Reading CVD header (main.cvd): Sat Aug  6 17:12:53 2016 -> WARNING: Can't get information about db.local.clamav.net: Temporary failure in name resolution
Sat Aug  6 17:12:53 2016 -> WARNING: Can't read main.cvd header from db.local.clamav.net (IP: )
Sat Aug  6 17:12:53 2016 -> Trying again in 5 secs...
Sat Aug  6 17:12:58 2016 -> ClamAV update process started at Sat Aug  6 17:12:58 2016
Sat Aug  6 17:12:58 2016 -> WARNING: Can't query current.cvd.clamav.net
Sat Aug  6 17:12:58 2016 -> WARNING: Invalid DNS reply. Falling back to HTTP mode.
Sat Aug  6 17:12:58 2016 -> Reading CVD header (main.cvd): Sat Aug  6 17:12:58 2016 -> WARNING: Can't get information about db.local.clamav.net: Temporary failure in name resolution
Sat Aug  6 17:12:58 2016 -> WARNING: Can't read main.cvd header from db.local.clamav.net (IP: )
Sat Aug  6 17:12:58 2016 -> Trying again in 5 secs...
Sat Aug  6 17:13:03 2016 -> ClamAV update process started at Sat Aug  6 17:13:03 2016
Sat Aug  6 17:13:03 2016 -> WARNING: Your ClamAV installation is OUTDATED!
Sat Aug  6 17:13:03 2016 -> WARNING: Local version: 0.99 Recommended version: 0.99.2
Sat Aug  6 17:13:03 2016 -> DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
Sat Aug  6 17:13:03 2016 -> main.cvd is up to date (version: 57, sigs: 4218790, f-level: 60, builder: amishhammer)
Sat Aug  6 17:13:07 2016 -> Downloading daily-22036.cdiff [100%]
Sat Aug  6 17:13:08 2016 -> Downloading daily-22037.cdiff [100%]
Sat Aug  6 17:13:08 2016 -> Downloading daily-22038.cdiff [100%]
Sat Aug  6 17:13:08 2016 -> Downloading daily-22039.cdiff [100%]
Sat Aug  6 17:13:09 2016 -> Downloading daily-22040.cdiff [100%]
Sat Aug  6 17:13:11 2016 -> daily.cld updated (version: 22040, sigs: 486199, f-level: 63, builder: neo)
Sat Aug  6 17:13:11 2016 -> bytecode.cld is up to date (version: 283, sigs: 53, f-level: 63, builder: neo)
Sat Aug  6 17:13:20 2016 -> Database updated (4705042 signatures) from db.local.clamav.net (IP: 193.1.193.64)
Sat Aug  6 17:13:20 2016 -> --------------------------------------

---

### Post by SeijiSensei on 2016-08-06
Are you worried about the version being "outdated?" This happens all the time with clamav across multiple platforms.  Usually these updates reflect some revision to the scanning code in response to an arcane piece of malware that exploits some hole in clamav.  Chances are likely you'll never see anything like this.  More importantly, though, the signature database was completely updated and should work properly with the installed scanner.

Do you have something you can scan with clamscan to make sure it's working properly?  For testing, it's often valuable to keep a copy of "[eicar.com]("http://www.eicar.org/85-0-Download.html")", the official test "virus" that all scanners recognize, on your hard drive so a clamav scan will see it.

At some point the maintainers will upgrade clamav to the current version number and this problem will go away for a while.

---

### Post by Reddoug on 2016-08-06
Thanks for the reply, I was trying to find out why it was getting the error message, I was not getting it before I upgraded to 16.04. I can run a scan. 

Doug

---

### Post by sed_faster on 2016-09-06
> **Reddoug said:**
> Thanks for the reply, I was trying to find out why it was getting the error message, I was not getting it before I upgraded to 16.04. I can run a scan. 

Doug

Hello,
See my description on this topic, [https://ubuntuforums.org/showthread.php?t=2336144&p=13540435#post13540435](https://ubuntuforums.org/showthread.php?t=2336144&p=13540435#post13540435), I have the same error than you and I resolved stoping the clamav.

SeijiSensei

You suggest which I download the virus for my pc for test clamav software? I understood right? I am a newbie on this matter and this suggest scare me :)

Thanks

---

### Post by SeijiSensei on 2016-09-06
Eicar.com is not a virus.  It is a harmless test file that all virus scanners recognize so you can make sure your scanner is working properly.

---

