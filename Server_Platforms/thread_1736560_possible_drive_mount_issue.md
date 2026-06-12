---
title: "possible drive mount issue?"
date: 2011-04-22
forum: Server Platforms
---

### Post by nbrochu on 2011-04-22
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1            605645464   4788232 570092176   1% /
none                   1670788    456352   1214436  28% /dev
none                   1677652       332   1677320   1% /dev/shm
none                   1677652      3472   1674180   1% /var/run
none                   1677652         0   1677652   0% /var/lock
none                   1677652         0   1677652   0% /lib/init/rw
/dev/mapper/sil_bgahahbgfdca1
                     721075720 682295684   2151436 100% /home
/home/share/encrypted
                     721075720 682295684   2151436 100% /home/share/data
/home/share/encrypted
                     721075720 682295684   2151436 100% /home/share/data
/home/share/encrypted
                     721075720 682295684   2151436 100% /home/share/data
/dev/sdh1            961432072    204436 912389636   1% /media/New Volume

This is the output fro the df cmd. why is it that there is 3 mounts for the share folder. Im trying to figure this out because on the share it says 2.1 gigs free space? any ideas would be very helpfull

---

### Post by nbrochu on 2011-04-22
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1            605645464   4788232 570092176   1% /
none                   1670788    456352   1214436  28% /dev
none                   1677652       332   1677320   1% /dev/shm
none                   1677652      3472   1674180   1% /var/run
none                   1677652         0   1677652   0% /var/lock
none                   1677652         0   1677652   0% /lib/init/rw
/dev/mapper/sil_bgahahbgfdca1
                     721075720 682295684   2151436 100% /home
/home/share/encrypted
                     721075720 682295684   2151436 100% /home/share/data
/home/share/encrypted
                     721075720 682295684   2151436 100% /home/share/data
/home/share/encrypted
                     721075720 682295684   2151436 100% /home/share/data
/dev/sdh1            961432072    204436 912389636   1% /media/New Volume

This is the output fro the df cmd. why is it that there is 3 mounts for the share folder. Im trying to figure this out because on the share it says 2.1 gigs free space? any ideas would be very helpfull

---

