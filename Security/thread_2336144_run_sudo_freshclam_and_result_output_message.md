---
title: "run sudo freshclam and result output message"
date: 2016-09-05
forum: Security
---

### Post by sed_faster on 2016-09-05
Hello everyone,

I install "sudo apt-get install clamav" through terminal. And, according to the manual I try run this command:
```

**sudo freshclam**
and receive this output:
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

```

I google for the answer and I found this commands 
```

sudo /etc/init.d/clamav-freshclam stop
sudo freshclam -v
sudo /etc/init.d/clamav-freshclam start

```

The output was
```

**user@user:~$ sudo /etc/init.d/clamav-freshclam stop**
[ ok ] Stopping clamav-freshclam (via systemctl): clamav-freshclam.service.
**user@user:~$ sudo freshclam -v**
Current working dir is /var/lib/clamav
Max retries == 5
ClamAV update process started at Mon Sep  5 10:12:00 2016
Using IPv6 aware code
Querying current.cvd.clamav.net
TTL: 80
Software version from DNS: 0.99.2
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.99 Recommended version: 0.99.2
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd version from DNS: 57
main.cvd is up to date (version: 57, sigs: 4218790, f-level: 60, builder: amishhammer)
daily.cvd version from DNS: 22189
daily.cld is up to date (version: 22189, sigs: 587779, f-level: 63, builder: neo)
bytecode.cvd version from DNS: 283
bytecode.cvd is up to date (version: 283, sigs: 53, f-level: 63, builder: neo)
**user@user:~$ sudo /etc/init.d/clamav-freshclam start**
[ ok ] Starting clamav-freshclam (via systemctl): clamav-freshclam.service.

```

According to the output my version of clamav is outdate. How can I fix this? Should I bother me?
I tried access the manual, through "man clamav" but I didn't make it, the output was: No manual entry for clamav

Just in case, I upgraded and did update to my system.
My enviornment is: [B]Linux 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 GNU/Linux

[UPDATE]
[/B]I found this link [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV), but I can't get more information
Also installed sudo apt-get install clamdscan, according manual is anti-virus utility for Unix - scanner client, I don't know if is necessary but I installed. 
Also installed sudo apt-get install clamtk -> graphical front-end for ClamAV. In this front-end I updated the program and executed the scan all my files, including the hidden files. But I want learn install, update and execute through terminal.

Thanks

---

### Post by howefield on 2016-09-05
> **Edgar_Oliveira said:**
> According to the output my version of clamav is outdate. How can I fix this? Should I bother me?

As long as you keep the definitions files up to date with "sudo freshclam" you have nothing to worry about even if the application itself is slightly out of date.

---

### Post by SeijiSensei on 2016-09-05
See this: [https://ubuntuforums.org/showthread.php?t=2333082&p=13528043&viewfull=1#post13528043](https://ubuntuforums.org/showthread.php?t=2333082&p=13528043&viewfull=1#post13528043)

---

### Post by sed_faster on 2016-09-06
Hello,

Thanks for yours help. I response in another article, that suggested  by DeijiSensei, [https://ubuntuforums.org/showthread.php?t=2333082&p=13540902#post13540902](https://ubuntuforums.org/showthread.php?t=2333082&p=13540902#post13540902)

---

