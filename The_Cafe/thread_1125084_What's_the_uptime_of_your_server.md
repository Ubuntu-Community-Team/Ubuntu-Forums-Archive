---
title: "What's the uptime of your server?"
date: 2009-04-14
forum: The Cafe
---

### Post by MaxIBoy on 2009-04-14
My home LAN server has a 76-day uptime and counting-- I've never restarted it since that one time I had to reseat the ethernet card!

---

### Post by hyper_ch on 2009-04-14
not that long as I moved from etch to lenny about 2 months ago.

---

### Post by binbash on 2009-04-14
at home my torrent downloader one is around 36 days uptime.
one of my server is around 110 days, the other one is 230 :)

---

### Post by toupeiro on 2009-04-14
I've had a a Solaris 8 and RHEL4 server run for near 500 days.  I literally only rebooted them to apply Daylight savings patches.

---

### Post by ghindo on 2009-04-14
B-b-but...what about kernel updates?

---

### Post by Anthon on 2009-04-14
Close to 1000 days running SuSE 9.0 (that was before I switched to using Ubuntu on newly installed machines).
The machine is not connected to the Internet, and primarily runs some some virtual machines. No need to upgrade the host.

---

### Post by cariboo on 2009-04-14
It's only been up since the last power outage that was longer than the ups battery capacity:

```
uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
->   1    79 days, 22:47:13 | Linux 2.6.27-9-server     Sat Jan 24 00:58:56 2009
     2     7 days, 09:05:52 | Linux 2.6.27-9-server     Fri Jan 16 15:35:40 2009
----------------------------+---------------------------------------------------
NewRec    72 days, 13:41:20 | since                     Sat Jan 31 10:04:47 2009

```

Jim

---

### Post by MaxIBoy on 2009-04-14
> **ghindo said:**
> B-b-but...what about kernel updates?

[LIST]
[*]Do you have unworking hardware?
[*]Is your computer unstable?
[*]Is your computer too slow?
[*]Does your computer lack other features that you really need?
[/LIST]
If you answered "no" to all of these questions, you do not need to update your kernel!

I could go to the kernel archives and pull a 2.2 kernel from FTP. Apply ext3 and reiserFS patches, and it would work just fine for use on my server (which is an ancient NEC Ready-series computer and doesn't use any recent hardware.)

---

### Post by FuturePilot on 2009-04-14
> **MaxIBoy said:**
> [LIST]
[*]Do you have unworking hardware?
[*]Is your computer unstable?
[*]Is your computer too slow?
[*]Does your computer lack other features that you really need?
[/LIST]
If you answered "no" to all of these questions, you do not need to update your kernel!

I could go to the kernel archives and pull a 2.2 kernel from FTP. Apply ext3 and reiserFS patches, and it would work just fine for use on my server (which is an ancient NEC Ready-series computer and doesn't use any recent hardware.)

Kernel updates include more than just bug fixes and performance improvements. They often times include multiple security updates. IMO it's best to have the latest security updates, *especially* on a server.

My server hasn't been doing too great with uptime lately
```
#               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    28 days, 11:36:00 | Linux 2.6.27-11-server    Fri Feb 27 12:39:10 2009
     2     4 days, 13:53:00 | Linux 2.6.28-11-server    Fri Apr  3 22:52:46 2009
     3     3 days, 08:45:24 | Linux 2.6.27-11-server    Sat Mar 28 08:12:41 2009
     4     3 days, 07:27:58 | Linux 2.6.28-11-server    Wed Apr  8 12:46:20 2009
->   5     2 days, 07:28:31 | Linux 2.6.28-11-server    Sat Apr 11 20:14:51 2009
     6     1 day , 17:03:51 | Linux 2.6.28-11-server    Tue Mar 31 20:57:14 2009
     7     1 day , 08:50:34 | Linux 2.6.28-11-server    Thu Apr  2 14:01:39 2009
     8     0 days, 03:03:50 | Linux 2.6.27-11-server    Tue Mar 31 17:30:49 2009
     9     0 days, 00:21:28 | Linux 2.6.28-11-server    Tue Mar 31 20:35:15 2009
----------------------------+---------------------------------------------------
1up in     0 days, 23:59:28 | at                        Wed Apr 15 03:42:48 2009
no1 in    26 days, 04:07:30 | at                        Sun May 10 07:50:50 2009

```

---

### Post by ghindo on 2009-04-14
> **MaxIBoy said:**
> [LIST]
[*]Do you have unworking hardware?
[*]Is your computer unstable?
[*]Is your computer too slow?
[*]Does your computer lack other features that you really need?
[/LIST]
If you answered "no" to all of these questions, you do not need to update your kernel!

I could go to the kernel archives and pull a 2.2 kernel from FTP. Apply ext3 and reiserFS patches, and it would work just fine for use on my server (which is an ancient NEC Ready-series computer and doesn't use any recent hardware.)Like the above poster said, a lot of security updates are included in kernel updates as well.  I would think that having a more recent kernel would be beneficial for numerous reasons.

---

### Post by billgoldberg on 2009-04-14
-24h

Damn Slitaz!

---

