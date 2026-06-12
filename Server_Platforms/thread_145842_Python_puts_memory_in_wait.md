---
title: "Python puts memory in wait"
date: 2006-03-17
forum: Server Platforms
---

### Post by rich on 2006-03-17
I'm having a problem with 5.10

It's my test box that sometimes gets left on for a few days at a time. It's fine for a while, but then the load average creeps up and the memory is used up in wait :

top - 08:26:04 up 5 days, 18:46,  6 users,  load average: 5.83, 4.05, 3.26
Tasks: 127 total,   1 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0% us,  0.3% sy,  0.0% ni,  0.0% id, 98.0% wa,  0.7% hi,  0.0% si
Mem:    256308k total,   252124k used,     4184k free,      564k buffers
Swap:   746980k total,   386020k used,   360960k free,    24224k cached 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8096 richardc  16   0  235m 130m 3580 D  0.3 52.2 876:51.33 python
29299 richardc  16   0  2136 1120  844 R  0.3  0.4   0:00.01 top 


When I look at this with cacti I can see a fairly smooth rise over 3 or 4 days. 

I kill python and the system returns to normal. 

What is going on ? I've got several python libs and SPE, but haven't knowingly ticked the "take over my box" setting. At the point that the top was run there were no "home made" python apps running.

Anyone have any ideas how to track this one down ?



thanks,

Rich
[PHP][/PHP]

---

