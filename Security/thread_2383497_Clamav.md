---
title: "Clamav"
date: 2018-01-25
forum: Security
---

### Post by espectro2 on 2018-01-25
this error persecutes me in all the versions that I already installed of the ubuntu
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

how do i upgrade it in the version of ubuntu i am using i upgrade ubuntu to another version so the clamav up version
thanks for listening.

clamav is already the newest version (0.99.2+dfsg-0ubuntu0.16.04.2).
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.

sudo freshclam
ClamAV update process started at Thu Jan 25 22:41:53 2018
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.99.2 Recommended version: 0.99.3
DON'T PANIC! Read [http://www.clamav.net/documents/upgrading-clamav](http://www.clamav.net/documents/upgrading-clamav)
main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
daily.cvd is up to date (version: 24255, sigs: 1835431, f-level: 63, builder: neo)
bytecode.cld is up to date (version: 319, sigs: 75, f-level: 63, builder: neo)

---

### Post by ajgreeny on 2018-01-25
You have no reason for worry at all.

The version nof the clamav scanning application will not make a lot of difference to the efficacy of the scan; what matters is the version of the database that clamav uses to detect viruses and malware and as you can see from your last three lines of text
> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
daily.cvd is up to date (version: 24255, sigs: 1835431, f-level: 63, builder: neo)
bytecode.cld is up to date (version: 319, sigs: 75, f-level: 63, builder: neo) 
they are all up to date.

The other question to ask is, do you need a virus scanner if using a normal desktop version of Ubuntu?
I suspect not, but it is your choice.
See [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security) and 
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
and you will find much more info if you search for the subject.

---

### Post by marcel-pokrandt on 2018-01-29
> **ajgreeny said:**
> You have no reason for worry at all.

The version nof the clamav scanning application will not make a lot of difference to the efficacy of the scan; what matters is the version of the database that clamav uses to detect viruses and malware and as you can see from your last three lines of text


In THIS case this is simply not true. Clam AV 0.99.2 has a remote code execution flaw
[http://blog.clamav.net/2018/01/clamav-0993-has-been-released.html](http://blog.clamav.net/2018/01/clamav-0993-has-been-released.html)

I´m checking every day for the new 0.99.3...

---

### Post by TheFu on 2018-01-30
Often, Canonical will back-port security issues into prior versions.
[https://people.canonical.com/~ubuntu-security/cve/2017/CVE-2017-12374.html](https://people.canonical.com/~ubuntu-security/cve/2017/CVE-2017-12374.html)
[https://bugs.launchpad.net/ubuntu/%2Bsource/clamav/%2Bbug/1745635](https://bugs.launchpad.net/ubuntu/%2Bsource/clamav/%2Bbug/1745635)

According to Launchpad, Debian released their fix 20 hrs ago, so the upstream did their part. Canonical should pick it up.

My debian email gateway got the fix a few minutes ago.
They backported the fix into 0.99.2+dfsg-0+deb8u3. ;)  So don't look for 0.99.3.

---

### Post by deadflowr on 2018-01-30
They actually have, in a rare move, updated to the new upstream release 0.99.3.
[https://usn.ubuntu.com/usn/usn-3550-1/]("https://usn.ubuntu.com/usn/usn-3550-1/")

---

### Post by espectro2 on 2018-01-30
Thanks for the attention already made update as recommended in usn ubuntu I always have problems with clamav in ubuntu as well that they released this update.this error accompanies me all the versions are running dpkg-reconfigure clamav-freshclam if it is not done it does not update and it tends to be configured in manual in daemon or automatic never managed to update the clamavThanks for listening.
clamav 0.99.3+addedllvm-0ubu

ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

---

