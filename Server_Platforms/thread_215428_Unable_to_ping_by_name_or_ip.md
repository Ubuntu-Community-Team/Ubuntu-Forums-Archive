---
title: "Unable to ping by name or ip"
date: 2006-07-13
forum: Server Platforms
---

### Post by Zikona on 2006-07-13
I have installed server version of Ubuntu several times to resolve this issue without any luck. What happens is when I am logged in as a normal user and ping by name then I get 4 replies and it times out. If I login as root then I am unable to ping either by name or ip completely. My resolv.conf is set to commercial RR dns and my router same way. I have even setup server to a static without any success. This machine is using 950 MHz Athlon with 1 nic. My other test was to install on a different machine using same cd and everything worked just fine. Another thing I want add is that I have attempted also to disable ipv6 and still did not work. Did anybody have a same issue as me?

---

### Post by Zikona on 2006-07-14
I found my problem. I had to go to /etc/modprobe.d/ and modify blacklist file by adding a line of "blacklist ipv6". After rebooting server I was succefully able to use apt-get and ping by name. :D :D :D :D :D :D

---

