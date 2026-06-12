---
title: "Desktop Shutdown"
date: 2019-04-26
forum: Virtualisation
---

### Post by flerbinderbin on 2019-04-26
Hello Friends
 I run a couple virtual machines from my home computer, and I noticed at work today that I couldn’t access my file server.
 Came home to find my computer had turned off.
 Started looking through the logs and I noticed a log gap from 12pm until 5 sometime when i got home and turned it on.
 Could anyone dummy check these logs for me to see why it might have  been shut down? I don’t see any obvious reasons so I’m guessing a power  outage. Although I’m also wondering if one of my roomates came in and  shut off my computer lol.
 I’ll paste a portion of the logs below.
you all are saints and gods
 

```
Apr 25 11:19:46 linux-MS-7693 wpa_supplicant[1069]: wlp3s0: WPA: Group rekeying completed with 9c:5c:8e:8b:26:ac [GTK=CCMP]
Apr 25 11:45:00 linux-MS-7693  Nextcloud-2.5.1-x86_64.AppImage.desktop[2423]:  [2423:3687:0425/114500.267850:ERROR:cert_verify_proc_nss.cc(944)]  CERT_PKIXVerifyCert for 73.231.233.59 failed err=-8172
Apr 25 11:59:37 linux-MS-7693 wpa_supplicant[1069]: wlp3s0: WPA: Group rekeying completed with 9c:5c:8e:8b:26:ac [GTK=CCMP]
Apr 25 12:01:08 linux-MS-7693 systemd[1]: Started Run anacron jobs.
Apr 25 12:01:08 linux-MS-7693 anacron[9054]: Anacron 2.3 started on 2019-04-25
Apr 25 12:01:08 linux-MS-7693 anacron[9054]: Normal exit (0 jobs run)
Apr 25 12:02:39 linux-MS-7693 systemd[1]:  dev-disk-by\x2duuid-F07AFB197AFADB74.device: Job  dev-disk-by\x2duuid-F07AFB197AFADB74.device/start timed out.
Apr 25 12:02:39 linux-MS-7693 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-F07AFB197AFADB74.device.
Apr 25 12:02:39 linux-MS-7693 systemd[1]: Dependency failed for /mnt/F07AFB197AFADB74.
Apr 25 12:02:39 linux-MS-7693 systemd[1]:  mnt-F07AFB197AFADB74.mount: Job mnt-F07AFB197AFADB74.mount/start failed  with result ‘dependency’.
Apr 25 12:02:39 linux-MS-7693 systemd[1]:  dev-disk-by\x2duuid-F07AFB197AFADB74.device: Job  dev-disk-by\x2duuid-F07AFB197AFADB74.device/start failed with result  ‘timeout’.
Apr 25 12:02:39 linux-MS-7693 systemd[1]:  dev-disk-by\x2duuid-22F09203F091DD7B.device: Job  dev-disk-by\x2duuid-22F09203F091DD7B.device/start timed out.
Apr 25 12:02:39 linux-MS-7693 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-22F09203F091DD7B.device.
Apr 25 12:02:39 linux-MS-7693 systemd[1]: Dependency failed for /mnt/22F09203F091DD7B.
Apr 25 12:02:39 linux-MS-7693 systemd[1]:  mnt-22F09203F091DD7B.mount: Job mnt-22F09203F091DD7B.mount/start failed  with result ‘dependency’.
Apr 25 12:02:39 linux-MS-7693 systemd[1]:  dev-disk-by\x2duuid-22F09203F091DD7B.device: Job  dev-disk-by\x2duuid-22F09203F091DD7B.device/start failed with result  ‘timeout’.
Apr 25 12:05:51 linux-MS-7693 wpa_supplicant[1069]: wlp3s0: WPA: Group rekeying completed with 9c:5c:8e:8b:26:ac [GTK=CCMP]
Apr 25 12:17:01 linux-MS-7693 CRON[9097]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 25 17:43:08 linux-MS-7693 systemd-modules-load[316]: Inserted module 'lp’
Apr 25 17:43:08 linux-MS-7693 kernel: [    0.000000] Linux  version 4.18.0-18-generic (buildd@lcy01-amd64-006) (gcc version 7.3.0  (Ubuntu 7.3.0-16ubuntu3)) #19~18.04.1-Ubuntu SMP Fri Apr 5 10:22:13 UTC  2019$
Apr 25 17:43:08 linux-MS-7693 systemd-modules-load[316]: Inserted module 'ppdev’
```

---

### Post by wildmanne39 on 2019-04-26
Hello and welcome to the forum.

*Thread moved to **Virtualisation a more appropriate sub-forum**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

Thanks!
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by flerbinderbin on 2019-04-26
> **wildmanne39 said:**
> Hello and welcome to the forum.

*Thread moved to **Virtualisation a more appropriate sub-forum**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

Thanks!
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Roger, sorry about that.

---

### Post by wildmanne39 on 2019-04-26
No worries.:)

---

