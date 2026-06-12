---
title: "Getting flooded with messages from syslogd"
date: 2011-09-28
forum: Server Platforms
---

### Post by Nailox on 2011-09-28
its Ubuntu 10.04 LAMP on a VPS 
Im getting ```
Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU7: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU6: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU2: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU3: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU5: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU1: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU4: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:15:22 2011 ...
ovz-vargas kernel: CPU0: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU1: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU7: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU3: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU6: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU2: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU0: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU4: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:20:22 2011 ...
ovz-vargas kernel: CPU5: Temperature/speed normal
^CCtrl-C -- exit!
Aborted
root@server2:/#
Message from syslogd@ at Wed Sep 28 06:25:22 2011 ...
ovz-vargas kernel: CPU7: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:25:22 2011 ...
ovz-vargas kernel: CPU6: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:25:23 2011 ...
ovz-vargas kernel: CPU3: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:25:23 2011 ...
ovz-vargas kernel: CPU0: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:25:23 2011 ...
ovz-vargas kernel: CPU4: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:25:25 2011 ...
ovz-vargas kernel: CPU1: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:25:26 2011 ...
ovz-vargas kernel: CPU5: Temperature/speed normal

Message from syslogd@ at Wed Sep 28 06:25:26 2011 ...
ovz-vargas kernel: CPU2: Temperature/speed normal

```
every 5min. Load is normal, RAM is at 8%. Its a fresh install and it happened after i ran apt-get update. 

How do i stop those messages? TYIA

---

