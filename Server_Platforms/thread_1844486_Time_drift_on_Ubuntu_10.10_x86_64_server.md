---
title: "Time drift on Ubuntu 10.10 x86_64 server"
date: 2011-09-15
forum: Server Platforms
---

### Post by alcaudon66 on 2011-09-15
Hello there,

Afte the update to kernel version linux-image-2.6.35-30-server 2.6.35-30.59 the system clock begins to drift heavily. I realized the problem when th ntp daemon cannot get synchronized with any time server.

In order to verify the issue, I synchronized the system clock with the hardware clock with a hwclock -w and checked the output of 'date' and 'hwclock -r'

This is a sample of the obtained data:
jue sep 15 12:44:41 CEST 2011 | jue 15 sep 2011 12:44:42 CEST -0.494068 segundos
jue sep 15 12:45:42 CEST 2011 | jue 15 sep 2011 12:45:44 CEST -0.617572 segundos
jue sep 15 12:46:13 CEST 2011 | jue 15 sep 2011 12:46:15 CEST -0.622215 segundos
jue sep 15 12:47:14 CEST 2011 | jue 15 sep 2011 12:47:17 CEST -0.617594 segundos
jue sep 15 12:48:15 CEST 2011 | jue 15 sep 2011 12:48:19 CEST -0.617521 segundos
...

Hourly a cron job synchronizes de system clock with an external source to minimize the drift of the clock. Before the las upgrade there were no problems at all with the system clock...

Is this a known bug?

The output of uname -a is
Linux redmine 2.6.35-30-server #59-Ubuntu SMP Tue Aug 30 19:16:40 UTC 2011 x86_64 GNU/Linux

Thanks in advance,

Jordi

---

