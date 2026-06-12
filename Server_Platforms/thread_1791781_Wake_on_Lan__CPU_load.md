---
title: "Wake on Lan  CPU load"
date: 2011-06-27
forum: Server Platforms
---

### Post by carachi on 2011-06-27
Hello everybody,
I have this problem:
I have a web server that sometimes has a lot of traffic so I put a load balance to route traffic on 2/or more web servers.
Because the traffic to these sites is not uniform during the day, I'm searching for a program/script that when the CPU load is high (ex 70% ) this program turn on the other servers via Wake On Lan .
When the main server CPU drops below a limit (ex 40%) the other servers power off.

Is there something like that?

Thank you
Bye

---

### Post by Lars Noodén on 2011-06-27
You'll probably want to look at overall server response time rather than CPU, because that's where your bottleneck will be for most web sites.

---

