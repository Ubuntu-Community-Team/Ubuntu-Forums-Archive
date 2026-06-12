---
title: "Perf: interrupt took too long"
date: 2017-05-08
forum: Server Platforms
---

### Post by darek88 on 2017-05-08
I have Ubuntu 16.04 LTS. This computer is running as a simple server and works all time. Recenlty, Ubuntu freezes. Last logs before freeze looks like that:

```

May  2 22:28:35 mseoserv kernel: [ 6491.061361] perf: interrupt took too long (6650 > 6452), lowering kernel.perf_event_max_sample_rate to 30000
May  4 22:11:29 mseoserv kernel: [ 2881.915601] perf: interrupt took too long (5231 > 3910), lowering kernel.perf_event_max_sample_rate to 38000
May  5 23:43:07 mseoserv kernel: [ 7978.072292] perf: interrupt took too long (6587 > 4921), lowering kernel.perf_event_max_sample_rate to 30250

```

What is wrong? Is it a hardware problem?

---

### Post by exhile on 2017-05-08
Ubuntu 16.04 desktop freezes on a variety of hardware configurations but this is the first I've read where Ubuntu 16.04 server has frozen.

---

### Post by slickymaster on 2017-05-08
*Thread moved to **Server Platforms*** for a better fit

---

### Post by darek88 on 2017-05-08
It is a normal deskop version of Ubuntu but I using also as a server (HTTP, FTP).

I found one solution, but I'm not sure for it'll solve this problem. In /proc/sys/kernel/perf_cpu_time_max_percent I've change 25 to 0, and I disabled this mechanism. Can it change anything?

---

### Post by Doug S on 2017-05-08
Typically, those warning messages are a symptom of something else causing troubles in the system, not the cause of the troubles. Anyway, what you have done should be fine, as long as you do not want to do any traces.

---

