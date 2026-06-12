---
title: "Server stops respoding - goes to sleep(power save)?"
date: 2012-01-17
forum: Server Platforms
---

### Post by borudev on 2012-01-17
Hi,

I have poweredge 1435SC and I just installed Ubnutu and after a while 5h+ it stops responding. The way I see it i can not SSH to it anymore, i get connection timed out. When I had debian installed I didn't have this problem, so I'm assuming there's a setting of some kind? Can someone point me to the right direction where to disable it?

Thanks

Server info:
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-12-server x86_64)

---

### Post by borudev on 2012-01-18
anyone?

---

### Post by yves030 on 2013-01-19
I have exactly the same problem on a dell 1950... fresh install 12.04 minimal system plus openssh-server... did no apt-get upgrade yet (the server is down again, its weekend and i have no access...)
it is surely some kind of sleep, because when a colleague enters the noc, he just needs to hit a key and ssh access is possible again ... during "sleep", the server is still pingable...
i surely have not activated / setup any sleep or hibernate features.. the dell bios does not
even has a setting for this and other dell-servers (r3xx, r6xx) do not have this problem with 12.04...
any hint would be highly appretiated,
thanx so far,
yves

---

