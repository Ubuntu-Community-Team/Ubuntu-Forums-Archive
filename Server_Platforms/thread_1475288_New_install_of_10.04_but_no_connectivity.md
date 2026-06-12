---
title: "New install of 10.04 but no connectivity"
date: 2010-05-06
forum: Server Platforms
---

### Post by wxman on 2010-05-06
I just tried a new install of 10.04 server on my test machine. I had 8.04 running on it before the install. I used all the same IP addresses as before, but when installing 10.04 I noticed no Internet connection. I've searched around, but I haven't found any others saying problems like this. Has anyone noticed something different with 10.04 that could be messing my connections up? After installing, I can't even ping my firewall.

---

### Post by foxmulder881 on 2010-05-06
Have you tried

```
ifconfig ethx up
```

where x is your ethernet device.

---

### Post by Iowan on 2010-05-06
Have you checked **ifconfig -a** to see if it has an IP address? If not, the above technique *might* help...

---

### Post by wxman on 2010-05-07
This is a lesson in being too familiar with your computer.
After reading your posts, I first thought that I would never miss something as simple as that. Needless to say, I was wrong. I had installed a second NIC to use as a crossover. When I was installing Ubuntu, I kept telling the install to use eth0 instead of eth1, which is the correct network card. What a waste of two days trying to figure out what was wrong with the software, when it was just operator error. Thanks for the help.

By the way - it works fine now. I'm experimenting using xen LM's on two LV's. One will be a load balancer with nginx for SSL, and haproxy for the rest. The backend will be a LAMP server running apache. I'm trying to LV's so I can do snapshots. Thanks again for the help.

---

### Post by Iowan on 2010-05-07
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

### Post by foxmulder881 on 2010-05-07
Glad we could help and you got it sorted. ;-)

---

