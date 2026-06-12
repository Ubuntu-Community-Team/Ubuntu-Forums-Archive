---
title: "RTC issue"
date: 2009-04-02
forum: Server Platforms
---

### Post by Dubaschu on 2009-04-02
Hi everyone,

First to clearify the system we use is:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
Kernel: Linux srvdubuat 2.6.27-7-server #1 SMP Tue Nov 4 20:18:35 UTC 2008 i686 GNU/Linux

Hardware: HP ProLiant ML310 G4 - Dual-Core 3Ghz X64 - 8G mem.
Env:  Server is running as a UAT Server for the company.
Issue: /var/log/messages get an error message ever few seconds, example:
```
Apr  2 07:12:47 srvdubuat kernel: [1445492.940656] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:12:51 srvdubuat kernel: [1445496.870693] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:12:51 srvdubuat kernel: [1445497.000549] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:12:54 srvdubuat kernel: [1445500.041317] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:12:55 srvdubuat kernel: [1445500.920475] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:12:55 srvdubuat kernel: [1445501.060246] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:13:06 srvdubuat kernel: [1445511.941246] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:13:06 srvdubuat kernel: [1445511.941281] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:13:07 srvdubuat kernel: [1445513.220449] /dev/vmmon[5022]: /dev/rtc open failed: -2
Apr  2 07:13:10 srvdubuat kernel: [1445515.242118] /dev/vmmon[5022]: /dev/rtc open failed: -2
```


I am presuming from this error that an application is unable to access the Real Time Clock. I've searched though Google and many other forum but unable to get a solution.  We did compile onto the server VMWare and all our UAT testing is then performed on it using VMWare images. On VMWare it says it is important for VMWare to have access to RTC but I've been told on the Ubuntu IRC Chat that it can be ignored. This does not change the fact that the event logs are filling up and killing needed HD space and that VMWware is running at a lower performance rate.

[EDIT]Is ther any other information I can provide?[/EDIT]
Please help to resolve this server issue?
Could you please advise?

Thanks 

Dubaschu

---

### Post by Dubaschu on 2009-04-03
I tryed this [http://mediakey.dk/~cc/devrtc-error-with-ubuntu-and-linux-kernel-26/](http://mediakey.dk/~cc/devrtc-error-with-ubuntu-and-linux-kernel-26/)  but also didnot resolve the issue.

Dubaschu

---

