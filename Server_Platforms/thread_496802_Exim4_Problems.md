---
title: "Exim4 Problems"
date: 2007-07-09
forum: Server Platforms
---

### Post by borahshadow on 2007-07-09
Hi I need for cron jobs and mdadm to be able to email me after lots of searching and lots of trial and error I finally got exim configured to sent through one of my gmail accounts
I rebooted my server to make sure that I wouldn't have any surprises down the road if I needed to reboot for some reason and low and behold exim won't send anymore

What could have broke during the reboot?
and ps I don't need to send through my gmail account if someone wants to help me set up exim to send directly But I couldn't figure it out 
ps php should be able to send email too
Thanks for your help in advance

EDIT I just realised mabey I should provide my exim4 log
I set a cron job to ren /bin/echo test everyminute to see if it was working that is why my log is so full but here it is
```
2007-07-09 06:34:58 Start queue run: pid=22586
2007-07-09 06:34:58 End queue run: pid=22586
2007-07-09 07:04:58 Start queue run: pid=22597
2007-07-09 07:04:58 End queue run: pid=22597
2007-07-09 07:34:58 Start queue run: pid=22608
2007-07-09 07:34:58 End queue run: pid=22608
2007-07-09 08:04:58 Start queue run: pid=22619
2007-07-09 08:04:58 End queue run: pid=22619
2007-07-09 08:34:58 Start queue run: pid=22630
2007-07-09 08:34:58 End queue run: pid=22630
2007-07-09 09:04:58 Start queue run: pid=22641
2007-07-09 09:04:58 End queue run: pid=22641
2007-07-09 09:34:58 Start queue run: pid=22652
2007-07-09 09:34:58 End queue run: pid=22652
2007-07-09 10:04:58 Start queue run: pid=22663
2007-07-09 10:04:58 End queue run: pid=22663
2007-07-09 10:34:58 Start queue run: pid=22674
2007-07-09 10:34:58 End queue run: pid=22674
2007-07-09 11:04:58 Start queue run: pid=22686
2007-07-09 11:04:58 End queue run: pid=22686
2007-07-09 11:34:58 Start queue run: pid=22697
2007-07-09 11:34:58 End queue run: pid=22697
2007-07-09 11:44:16 exim 4.60 daemon started: pid=3965, -q30m, listening for SMTP on [127.0.0.1]:25
2007-07-09 11:44:17 Start queue run: pid=3968
2007-07-09 11:44:17 End queue run: pid=3968
2007-07-09 11:49:01 1I7xM5-00018v-G6 <= root@server-home.gateway.2wire.net U=root P=local S=627
2007-07-09 11:50:01 1I7xN3-000191-N2 <= root@server-home.gateway.2wire.net U=root P=local S=627
2007-07-09 11:51:01 1I7xO1-00019F-Qh <= root@server-home.gateway.2wire.net U=root P=local S=627
2007-07-09 11:52:02 1I7xOz-00019L-US <= root@server-home.gateway.2wire.net U=root P=local S=627
2007-07-09 11:53:01 1I7xPx-00019Q-1k <= root@server-home.gateway.2wire.net U=root P=local S=627
2007-07-09 11:54:01 1I7xQv-00019X-5g <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 11:55:01 1I7xRt-00019f-9p <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 11:56:01 1I7xSr-00019p-Dg <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 11:57:00 1I7xTo-00019t-Ft <= cody@server-home.gateway.2wire.net U=cody P=local S=455
2007-07-09 11:57:01 1I7xTp-00019y-HD <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 11:58:01 1I7xUn-0001A3-Kq <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 11:59:01 1I7xVl-0001AM-OJ <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:00:01 1I7xWj-0001AW-Sr <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:01:02 1I7xXh-0001Al-W4 <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:02:01 1I7xYf-0001Aq-40 <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:03:01 1I7xZd-0001Av-7d <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:04:01 1I7xab-0001B1-Bj <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:05:01 1I7xbZ-0001B6-FJ <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:06:01 1I7xcX-0001BB-Iq <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:07:01 1I7xdV-0001BH-MO <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:08:01 1I7xeT-0001BM-Pv <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:08:44 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (9 more tries)
2007-07-09 12:08:56 1I7xfM-0001CM-90 <= cody@server-home.gateway.2wire.net U=cody P=local S=455
2007-07-09 12:09:02 1I7xfR-0001CX-Tk <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:09:14 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (8 more tries)
2007-07-09 12:09:44 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (7 more tries)
2007-07-09 12:10:01 1I7xgP-0001Ck-23 <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:10:14 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (6 more tries)
2007-07-09 12:10:44 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (5 more tries)
2007-07-09 12:11:01 1I7xhN-0001Ct-5d <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:11:14 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (4 more tries)
2007-07-09 12:11:44 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (3 more tries)
2007-07-09 12:12:01 1I7xiL-0001D2-9B <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:12:14 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (2 more tries)
2007-07-09 12:12:44 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (1 more try)
2007-07-09 12:13:01 1I7xjJ-0001DC-Dh <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:13:14 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: daemon abandoned
2007-07-09 12:14:01 1I7xkH-0001DL-HE <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:14:17 Start queue run: pid=4674
2007-07-09 12:14:17 1I7xjJ-0001DC-Dh Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xhN-0001Ct-5d Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xcX-0001BB-Iq Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xbZ-0001B6-FJ Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xVl-0001AM-OJ Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xTp-00019y-HD Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xOz-00019L-US Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xO1-00019F-Qh Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xM5-00018v-G6 Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xN3-000191-N2 Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xPx-00019Q-1k Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xQv-00019X-5g Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xRt-00019f-9p Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xSr-00019p-Dg Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xTo-00019t-Ft Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xUn-0001A3-Kq Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xWj-0001AW-Sr Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xXh-0001Al-W4 Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xYf-0001Aq-40 Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xZd-0001Av-7d Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xab-0001B1-Bj Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xdV-0001BH-MO Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xeT-0001BM-Pv Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xfM-0001CM-90 Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xfR-0001CX-Tk Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xgP-0001Ck-23 Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xiL-0001D2-9B Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 1I7xkH-0001DL-HE Spool file is locked (another process is handling this message)
2007-07-09 12:14:17 End queue run: pid=4674
2007-07-09 12:15:01 1I7xlF-0001E5-Km <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:16:01 1I7xmD-0001EA-OL <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:17:01 1I7xnB-0001EL-Sa <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:18:02 1I7xoA-0001Ec-0u <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:19:01 1I7xp7-0001Em-4e <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:19:08 1I7xpE-0001Eq-H8 <= cody@server-home.gateway.2wire.net U=cody P=local S=483
2007-07-09 12:20:01 1I7xq5-0001Ez-8W <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:20:19 1I7xqN-0001F3-Ko <= cody@server-home.gateway.2wire.net U=cody P=local S=455
2007-07-09 12:21:01 1I7xr3-0001F9-C3 <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:22:01 1I7xs1-0001FH-Fw <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:23:01 1I7xsz-0001FP-JT <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:24:01 1I7xtx-0001GK-Mh <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:25:01 1I7xuv-0001Gf-QI <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:26:01 1I7xvt-0001Gq-U8 <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:27:01 1I7xwr-0001Gv-1P <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:28:01 1I7xxp-0001H0-50 <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:28:07 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (9 more tries)
2007-07-09 12:28:24 1I7xyC-0001JL-Uf <= cody@server-home.gateway.2wire.net U=cody P=local S=455
2007-07-09 12:28:37 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (8 more tries)
2007-07-09 12:29:01 1I7xyn-0001JQ-8W <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:29:07 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (7 more tries)
2007-07-09 12:29:37 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (6 more tries)
2007-07-09 12:30:01 1I7xzl-0001JV-CP <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:30:07 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (5 more tries)
2007-07-09 12:30:37 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (4 more tries)
2007-07-09 12:31:01 1I7y0j-0001Je-Fx <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:31:07 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (3 more tries)
2007-07-09 12:31:37 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (2 more tries)
2007-07-09 12:32:01 1I7y1h-0001Jk-Jn <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:32:07 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: waiting 30s before trying again (1 more try)
2007-07-09 12:32:37 socket bind() to port 25 for address 127.0.0.1 failed: Address already in use: daemon abandoned
2007-07-09 12:32:40 1I7y2J-0001Jp-Uw <= cody@server-home.gateway.2wire.net U=cody P=local S=455
2007-07-09 12:33:01 1I7y2f-0001Ju-NN <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:34:01 1I7y3d-0001Jz-Qz <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:35:02 1I7y4b-0001K4-US <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:36:01 1I7y5Z-0001KB-1m <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:36:14 1I7y5m-0001KF-F7 <= cody@server-home.gateway.2wire.net U=cody P=local S=456
2007-07-09 12:36:38 1I7y6A-0001KJ-GG <= cody@server-home.gateway.2wire.net U=cody P=local S=465
2007-07-09 12:37:01 1I7y6X-0001KO-5c <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:38:01 1I7y7V-0001KT-9C <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:39:01 1I7y8T-0001Ka-DW <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:40:01 1I7y9R-0001Kl-HY <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:41:01 1I7yAP-0001Kq-L5 <= root@server-home.gateway.2wire.net U=root P=local S=599
2007-07-09 12:42:02 1I7yBN-0001Kz-Oy <= root@server-home.gateway.2wire.net U=root P=local S=599

```

---

### Post by borahshadow on 2007-07-10
Never mind I guess gmail was just being slow yesterday I got on and checked my email this morning and I had 62 messages from my server :):popcorn:

---

