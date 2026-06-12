---
title: "Hits on port 15785"
date: 2009-10-09
forum: Security
---

### Post by sopadeajo on 2009-10-09
Since yesterday a turkish computer:  85.108.241.122 is hiting my 15785 port in 3 coups at an interval of 0,3,9 seconds every 21 or 22 minutes. I wonder is there is a known windows vulnerability on port 15785 and what this moron is trying to do on my machine.
Though i am not scared ;just would like to know if this is a zombie machine or a hack attack.

PS: I did not use Fiestarter to get these firewall logs.

---

### Post by lovinglinux on 2009-10-09
> **sopadeajo said:**
> PS: I did not use Fiestarter to get these firewall logs.

:lol:

---

### Post by sopadeajo on 2009-10-09
And these are only a part


Oct 07 18:29:05 SRC=85.103.47.180 DPT=15785
Oct 07 18:29:08 SRC=85.103.47.180 DPT=15785
Oct 07 18:29:14 SRC=85.103.47.180 DPT=15785
Oct 07 18:50:08 SRC=85.103.47.180 DPT=15785
Oct 07 18:50:11 SRC=85.103.47.180 DPT=15785
Oct 07 18:50:17 SRC=85.103.47.180 DPT=15785
Oct 07 19:11:04 SRC=85.103.47.180 DPT=15785
Oct 07 19:11:07 SRC=85.103.47.180 DPT=15785
Oct 07 19:11:13 SRC=85.103.47.180 DPT=15785
Oct 07 19:32:08 SRC=85.103.47.180 DPT=15785
Oct 07 19:32:11 SRC=85.103.47.180 DPT=15785
Oct 07 19:32:17 SRC=85.103.47.180 DPT=15785
Oct 07 19:53:19 SRC=85.103.47.180 DPT=15785
Oct 07 19:53:22 SRC=85.103.47.180 DPT=15785
Oct 07 19:53:28 SRC=85.103.47.180 DPT=15785
Oct 07 20:13:56 SRC=85.103.47.180 DPT=15785
Oct 07 20:13:59 SRC=85.103.47.180 DPT=15785
Oct 07 20:14:05 SRC=85.103.47.180 DPT=15785
Oct 07 20:34:58 SRC=85.103.47.180 DPT=15785
Oct 07 20:35:01 SRC=85.103.47.180 DPT=15785
Oct 07 20:35:07 SRC=85.103.47.180 DPT=15785
Oct 08 08:24:06 SRC=85.103.47.180 DPT=15785
Oct 08 08:24:09 SRC=85.103.47.180 DPT=15785
Oct 08 08:24:15 SRC=85.103.47.180 DPT=15785
Oct 08 08:47:27 SRC=85.103.47.180 DPT=15785
Oct 08 08:47:30 SRC=85.103.47.180 DPT=15785
Oct 08 08:47:36 SRC=85.103.47.180 DPT=15785
Oct 08 09:10:09 SRC=85.103.47.180 DPT=15785
Oct 08 09:10:12 SRC=85.103.47.180 DPT=15785
Oct 08 09:10:18 SRC=85.103.47.180 DPT=15785
Oct 08 09:33:51 SRC=85.103.47.180 DPT=15785
Oct 08 09:33:54 SRC=85.103.47.180 DPT=15785
Oct 08 09:34:00 SRC=85.103.47.180 DPT=15785
Oct 07 07:38:49 SRC=85.108.204.16 DPT=15785
Oct 07 07:38:52 SRC=85.108.204.16 DPT=15785
Oct 07 07:38:58 SRC=85.108.204.16 DPT=15785
Oct 07 08:00:22 SRC=85.108.204.16 DPT=15785
Oct 07 08:00:25 SRC=85.108.204.16 DPT=15785
Oct 07 08:00:31 SRC=85.108.204.16 DPT=15785
Oct 07 08:22:01 SRC=85.108.204.16 DPT=15785
Oct 07 08:22:04 SRC=85.108.204.16 DPT=15785
Oct 07 08:22:10 SRC=85.108.204.16 DPT=15785
Oct 08 19:50:41 SRC=85.108.240.208 DPT=15785
Oct 08 19:50:44 SRC=85.108.240.208 DPT=15785
Oct 08 19:50:50 SRC=85.108.240.208 DPT=15785
Oct 08 20:11:14 SRC=85.108.240.208 DPT=15785
Oct 08 20:11:17 SRC=85.108.240.208 DPT=15785
Oct 08 20:11:23 SRC=85.108.240.208 DPT=15785
Oct 08 20:31:55 SRC=85.108.240.208 DPT=15785
Oct 08 20:31:58 SRC=85.108.240.208 DPT=15785
Oct 08 20:32:04 SRC=85.108.240.208 DPT=15785
Oct 08 20:53:07 SRC=85.108.240.208 DPT=15785
Oct 08 20:53:10 SRC=85.108.240.208 DPT=15785
Oct 08 20:53:16 SRC=85.108.240.208 DPT=15785
Oct 08 21:13:39 SRC=85.108.240.208 DPT=15785
Oct 08 21:13:42 SRC=85.108.240.208 DPT=15785
Oct 08 21:13:48 SRC=85.108.240.208 DPT=15785
Oct 08 21:34:37 SRC=85.108.240.208 DPT=15785
Oct 08 21:34:40 SRC=85.108.240.208 DPT=15785
Oct 08 21:34:46 SRC=85.108.240.208 DPT=15785

---

### Post by Kinstonian on 2009-10-10
[Dshield](http://www.dshield.org/port.html?port=15785) shows hardly any traffic for that port, or any other details.  While I don't know the reason for the traffic based on those logs, I wouldn't be too worried about it.

---

### Post by GuyCorngood on 2009-10-10
If your ISP gives you a dynamic IP address, you probably just inherited one whose previous user had P2P or server software running on 15785. This Turkish computer is just unnaturally persistent in trying to connect to the relocated server. I'd ignore it; there's no harm it could possibly do as long as you don't have any servers listening on that port.

---

