---
title: "serial8250 too much work for irq4 in rsyslogd in ubuntu 14.04"
date: 2016-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by kailashkkd on 2016-10-19
Hi All,

I am working on a case, where the user is running a Ubuntu 14.04 Version and have installed Apache,Varnish and MySQL in the OS disk.
The user is complaining that he is facing performance issue.
Also in his syslog file I could see multiple error like the below one.
kernel: [30576.726661] serial8250: too much work for irq4

Oct 13 07:21:12 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6540
Oct 13 07:21:23 localhost kernel: [30665.233699] serial8250: too much work for irq4
Oct 13 07:22:43 localhost kernel: [30745.632932] serial8250: too much work for irq4
Oct 13 07:22:47 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6560
Oct 13 07:23:01 localhost kernel: [30763.663764] serial8250: too much work for irq4
Oct 13 07:23:37 localhost kernel: [30799.299551] serial8250: too much work for irq4
Oct 13 07:23:49 localhost sd.collector[2246]: message repeated 9 times: [ WARNING (util.py:144): Hostname: localhost is local]
Oct 13 07:23:55 localhost sd.collector[2246]: INFO (collector.py:555): Finished run #470. Collection time: 6.86s. Emit time: 0.01s
Oct 13 07:24:03 localhost kernel: [30826.089836] serial8250: too much work for irq4
Oct 13 07:24:17 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6580
Oct 13 07:24:57 localhost sd.collector[2246]: WARNING (util.py:144): Hostname: localhost is local
Oct 13 07:25:01 localhost CRON[35335]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 13 07:25:52 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6600
Oct 13 07:27:22 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6620
Oct 13 07:27:39 localhost kernel: [31042.087192] serial8250: too much work for irq4
Oct 13 07:28:57 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6640
Oct 13 07:30:29 localhost sd.forwarder[2245]: INFO (transaction.py:156): Flushing 1 transaction during flush #6660
Oct 13 07:32:02 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6680
Oct 13 07:33:37 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6700
Oct 13 07:34:46 localhost sd.collector[2246]: message repeated 9 times: [ WARNING (util.py:144): Hostname: localhost is local]
Oct 13 07:34:51 localhost sd.collector[2246]: INFO (collector.py:555): Finished run #480. Collection time: 6.01s. Emit time: 0.01s
Oct 13 07:35:01 localhost CRON[35758]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 13 07:35:12 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6720
Oct 13 07:35:34 localhost kernel: [31515.636017] serial8250: too much work for irq4
Oct 13 07:35:52 localhost sd.collector[2246]: WARNING (util.py:144): Hostname: localhost is local
Oct 13 07:36:27 localhost kernel: [31570.228027] serial8250: too much work for irq4
Oct 13 07:36:47 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6740
Oct 13 07:38:22 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6760
Oct 13 07:39:01 localhost CRON[35921]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Oct 13 07:39:57 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6780
Oct 13 07:41:27 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6800
Oct 13 07:42:17 localhost kernel: [31919.504028] serial8250: too much work for irq4
Oct 13 07:42:43 localhost kernel: [31945.846291] serial8250: too much work for irq4
Oct 13 07:43:02 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6820
Oct 13 07:43:10 localhost kernel: [31972.455633] serial8250: too much work for irq4
Oct 13 07:44:16 localhost kernel: [32038.216041] serial8250: too much work for irq4
Oct 13 07:44:37 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6840
Oct 13 07:45:01 localhost CRON[36247]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 13 07:45:41 localhost sd.collector[2246]: message repeated 9 times: [ WARNING (util.py:144): Hostname: localhost is local]
Oct 13 07:45:45 localhost sd.collector[2246]: INFO (collector.py:555): Finished run #490. Collection time: 5.2s. Emit time: 0.01s
Oct 13 07:46:04 localhost kernel: [32146.270671] serial8250: too much work for irq4
Oct 13 07:46:07 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6860
Oct 13 07:46:18 localhost kernel: [32160.314024] serial8250: too much work for irq4
Oct 13 07:46:31 localhost kernel: [32173.193493] serial8250: too much work for irq4
Oct 13 07:46:46 localhost sd.collector[2246]: WARNING (util.py:144): Hostname: localhost is local
Oct 13 07:47:11 localhost kernel: [32213.583529] serial8250: too much work for irq4
Oct 13 07:47:42 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6880
Oct 13 07:48:18 localhost kernel: [32280.924097] serial8250: too much work for irq4
Oct 13 07:49:12 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6900
Oct 13 07:50:47 localhost sd.forwarder[2245]: INFO (transaction.py:164): No transaction to flush during flush #6920
Oct 13 07:50:59 localhost kernel: [32441.394442] serial8250: too much work for irq4
Oct 13 07:51:40 localhost kernel: [32482.372029] serial8250: too much work for irq4
Oct 13 07:52:20 localhost kernel: [32521.652021] serial8250: too much work for irq4

In Redhat this error is treated as bug, i want to is it a bug in Ubuntu also?
Also if you provide any insight on the issue. I mean like , what could be the reason for this error?


I want your help in overcoming this issue.

Thanks & Regards,

Kailash B


Oct 13 07:52:20 localhost sd.forwarder[2245]: INFO (transaction.py:156): Flushing 1 transaction during flush #6940
Oct 13 07:53:00 localhost kernel: [32562.744874] serial8250: too much work for irq4

---

