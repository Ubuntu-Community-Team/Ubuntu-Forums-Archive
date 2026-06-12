---
title: "How do I measure load on a VM host?"
date: 2010-04-03
forum: Virtualisation
---

### Post by chronoz on 2010-04-03
[SIZE=2]It seems that load says nothing nowadays. How would you measure load on a VPS host, to know if you can add additional VM's[/SIZE][SIZE=2]?[/SIZE][SIZE=2] w right to see how much processes are awaiting a turn[/SIZE][SIZE=2]?[/SIZE]
[SIZE=2]
I have 7 VM's on my host with 64GB ram and 6xSAS RAID5. This VPS host contains 2 VM&#347; that have been allocated hardly any resources.  

Do you know what this lack of resources does to their VPS load? It goes up.
And do you know what this does to VPS host load? It also goes up.

So how do I know when a server is overloaded[/SIZE][SIZE=2]?[/SIZE]

---

### Post by HermanAB on 2010-04-03
top, htop, ntop.

---

