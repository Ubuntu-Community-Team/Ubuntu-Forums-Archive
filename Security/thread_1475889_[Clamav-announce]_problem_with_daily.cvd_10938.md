---
title: "[Clamav-announce] problem with daily.cvd 10938"
date: 2010-05-07
forum: Security
---

### Post by dino99 on 2010-05-07
Author: Luca Gibelli
Date: 2010-05-07 13:06 +200
To: ClamAV Announce
Subject: [Clamav-announce] problem with daily.cvd 10938
Dear ClamAV users,

about 15 mins ago we released daily.cvd 10938. This update apparently
caused a segmentation fault in all ClamAV versions older than 0.96
on 32 bit systems.

We just released daily.cvd 10939 which removes the faulty signature and
we have taken measures to ensure that this problem won't happen again.

We recommend using a monitor tool like clamdwatch or clamdmon to
automatically restart clamd whenever it dies.

If you are already using a similar solution, your clamd will be
restarted automatically as soon as freshclam downloads the daily.cvd
10939 update.

We apologise for the inconvenience.

Regards,

-- 
Luca Gibelli (luca _at_ clamav.net)       ClamAV, a GPL anti-virus toolkit
[Tel] +39 0187 1851862 [Fax] +39 0187 1852252 [IM] nervous/jabber.linux.it
PGP key id 5EFC5582 @ any key-server || [http://www.clamav.net/gpg/luca.gpg](http://www.clamav.net/gpg/luca.gpg)
_______________________________________________
[http://lists.clamav.net/cgi-bin/mailman/listinfo/clamav-announce](http://lists.clamav.net/cgi-bin/mailman/listinfo/clamav-announce)

---

