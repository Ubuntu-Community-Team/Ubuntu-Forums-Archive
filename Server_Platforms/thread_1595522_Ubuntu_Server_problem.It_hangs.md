---
title: "Ubuntu Server problem.It hangs"
date: 2010-10-13
forum: Server Platforms
---

### Post by anirup on 2010-10-13
**I am currently using ubuntu server 10.04.The ubuntu server hangs after few minutes in usage.However when I go through the recovery mode and login through the fail safe mode there is no problem and the server works fine.However the shared resources cannot be accessed through another computer inspite of the fact that i am able to see shared resources on that computer.Please help....**

---

### Post by arrrghhh on 2010-10-13
What does it hang on?  Can you still SSH to it?  How about local/physical access to the box?

---

### Post by anirup on 2010-10-15
It just hangs after few minutes in usage.Not able to access anything.

---

### Post by James78 on 2010-10-15
Possible points to check out.

1. Where you are trying to access it from is blocked. E.g. You can't access it from there. Solution: See point 2.
2. Information is not reaching the server. Make sure all relevant ports are open and forwarded. Often the cause of many things, definitely "slowdown".
3. Check your error logs, do they list anything useful? Check, Apache error log, system log, any other relevant logs. I cannot stress enough that logs are very useful to find problems! I'm sure Apache has a debug log that can be enabled. Filysystem location: /var/log
4. Your host blocks the ports, e.g. port 80 incoming, because you are on a dynamic account and they don't need to allow that port. (This also means you are trying to access the server from an external source)
5. Your server is setup incorrectly, try checking the configuration, MAKE SURE it's setup right, because this is also a very common cause of problems.
6. Are you running your server externally, with a url? If so, and you're running your own nameservers, you need to be using BIND, and port 53 incoming needs to be allowed, otherwise there will be slowdown and timeouts even though there's nothing wrong.

---

