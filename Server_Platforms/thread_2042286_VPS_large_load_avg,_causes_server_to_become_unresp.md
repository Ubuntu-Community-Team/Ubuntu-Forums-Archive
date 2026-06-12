---
title: "VPS large load avg, causes server to become unresponsive"
date: 2012-08-14
forum: Server Platforms
---

### Post by jamesa00789 on 2012-08-14
I have a VPS with the following:

1.5 GB RAM
Ubuntu 12.04 LTS
Quad core CPU (Intel 2.6 Ghz)

Last night while I was sleeping I had an outage which lasted 5 hours. I got locked out of SSH and HTTP. A reboot of the VPS seemed to fix the problem.

Looking back, by doing a sar command:

```

00:00:01        CPU     %user     %nice   %system   %iowait    %steal     %idle

00:28:01        all      4.82      0.00      0.84      1.92      0.00     92.42
00:29:01        all      4.96      0.00      1.03      2.10      0.00     91.91
00:30:01        all      4.27      0.00      0.94      1.45      0.00     93.33
00:31:01        all      6.29      0.00      1.60      2.09      0.00     90.01
00:32:01        all      4.54      0.00      0.89      2.19      0.00     92.38
00:33:01        all      4.41      0.00      0.81      1.75      0.00     93.04
00:34:01        all      2.89      0.00      0.56      2.03      0.00     94.52
00:35:01        all      3.57      0.00      0.65      1.51      0.00     94.27
00:36:01        all      5.20      0.00      0.82      1.46      0.00     92.52
00:37:01        all      3.94      0.00      0.77      1.46      0.00     93.82
00:38:01        all      4.12      0.00      0.88      1.61      0.00     93.39
00:39:02        all      5.35      0.38      2.57     22.16      0.00     69.55
00:40:01        all      5.61      0.13      2.38      8.74      0.00     83.15
00:41:01        all      4.56      0.00      1.39      1.76      0.00     92.29
00:42:12        all      3.77      0.00      3.39     39.31      0.00     53.53
00:43:14        all      2.41      0.00      2.71     94.71      0.00      0.17
00:44:17        all      2.53      0.00      3.08     83.73      0.00     10.65
00:45:03        all      2.68      0.00      2.98     80.22      0.00     14.13
00:46:33        all      1.72      0.00      2.89     95.39      0.00      0.01
00:47:28        all      1.68      0.00      2.86     95.46      0.00      0.00
00:48:14        all      1.95      0.00      3.18     94.56      0.00      0.31
00:49:12        all      1.17      0.00      2.78     94.77      0.00      1.27
00:50:10        all      0.61      0.00      2.89     95.58      0.00      0.92
00:51:51        all      0.38      0.00      2.99     96.48      0.00      0.15
00:52:10        all      0.84      0.00      3.72     95.44      0.00      0.00
00:53:46        all      1.65      0.00      3.11     95.24      0.00      0.00
00:54:15        all      4.52      0.00      2.92     92.55      0.00      0.00
00:55:28        all      4.34      0.00      2.43     93.23      0.00      0.00
00:56:05        all      8.83      0.00      1.84     89.33      0.00      0.00
00:57:03        all     12.09      0.00      2.68     84.33      0.00      0.90

```

You can see the CPU usage rapidly increased and disk waiting time exploded. In the logs, sendmail stopped working because of a high CPU load.

The VPS runs very smoothly, it rarely goes above load avg of 0.5 and uses around 700 MB RAM.

I mainly run:

apache2
MySQL
mod_perl
vsftpd

I also run cronjobs, but they all use ionice -c3 nice -n 19 and therefore should not effect system performance in any way.

Unfortunately I was not able to run the iostat command to see which programs were hogging the CPU or Disk I/O.

I checked the apache logs and there was no explosion of activity. Even so by using iptables I have placed limits on ports 80 and 443 to 5 page views per second. In addition to this, I have also installed DDoS deflate which bans IP addresses if they make too many connections to the server in a minute, no one was banned so no one was running DoS attacks or trying to over load my server (correct me if I am wrong with this).

I am completely stuck with where to go with this. What would be the best way to look back in time to find out what was causing the load spike?

One of my theories is that the disk I/O became so low that it built up a backlog of page views that needed to be generated with mod_perl and MySQL (in the logs some pages needed over 15 minutes to load).

However, I have been in touch with the hosts and they coundn't find any problem with the node and disk volumes. They have however moved the VPS to a different less busy node.

Any help with this issue would be fantastic.

Thanks in advance

---

### Post by thnewguy on 2012-08-14
It could be a lot of things. Cron job, DoS attack, large and unexpected surge in legitimate traffic. It's hard to tell without more logs.

---

### Post by jamesa00789 on 2012-08-14
Thanks for your reply thnewguy. However I now know the disk was being utilized to 100% capacity by a run away program - problem is I'm not sure how to find it.

Is information such as programs doing what and what time stored anywhere in Ubuntu 12.04?

Many thanks!

---

