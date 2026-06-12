---
title: "System won't wake up after sleep"
date: 2016-03-22
forum: Ubuntu Development Version
---

### Post by Joo_Alves on 2016-03-22
Hello,

I've been experiencing this issue since I've installed the version 16.04 LTS (fresh install, updated today), basically the system won't boot up after it has been put to sleep (black screen, laptop lights on).

What can I do to help me understand what is causing this?

@ My Current Specs:
- HP ZBook 14 2015
- Intel Core i5 5200U
- Intel HD Graphics 5500
- SSD Drive
- 64 bits OS

Thanks.

---

### Post by Doug S on 2016-03-22
Do you have another computer on your local network? One thing I like to do is install Open-SSH server on the problem computer and then attempt to SSH to it from another computer so that I can determine if the issue is just a graphics / display issue, or if the computer is really not working. And if it is just a graphics / display issue (which typically, it is), then I can do a proper re-boot instead of a "hold the power button" forced power off.

---

### Post by Joo_Alves on 2016-03-22
Yes I do have another machine, although I think the problem happens when it is beginning to sleep, which never happens.

I have noticed now that the led is always on, and the computer never enters in sleep mode. Although some services are disabled (like networking since I lose the ssh connection and the router isn't detecting it anymore) and the screen is black.

Any thoughts? Thanks.

---

### Post by Doug S on 2016-03-23
> **Joo_Alves said:**
> Any thoughts? Thanks.Not really. Is there anything useful in any log file in /var/log? Perhaps /var/log/pm-suspend.log?

---

### Post by Joo_Alves on 2016-03-23
> **Doug S said:**
> Not really. Is there anything useful in any log file in /var/log? Perhaps /var/log/pm-suspend.log?

Nothing worth mention.. I've also removed and switched all the files from the /sleep.d/ directory but it solved nothing. :(

---

