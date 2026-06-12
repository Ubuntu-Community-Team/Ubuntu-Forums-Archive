---
title: "Debootstrapping a server?"
date: 2007-03-28
forum: Server Platforms
---

### Post by tomplast on 2007-03-28
Hi.

One of our webservers at school got hacked a time ago and I as I'm partially responsible for the servers I have decided to replan for a fresh install which will be quite locked down so hackers will get a tough time hacking it.

My question (though not directly security related, but I would love to hear some tips from you) is whether I can debootstrap a server system on my computer at home and then recreate the same partition layout on the IRL server and then move over the data from the debootstrapped system to the server.

Am I making myself clear here? At least have some difficulties understanding myself here so please bare with me if I'm a bit unclear on the topic.


Thank you for your help

---

### Post by tomplast on 2007-03-28
*bump*

---

### Post by psusi on 2007-03-28
Sure you can... but why bother?  It would be simpler to just install normally.

---

### Post by Frosty Cold Drink on 2007-03-28
> **tomplast said:**
> Hi.

One of our webservers at school got hacked a time ago and I as I'm partially responsible for the servers I have decided to replan for a fresh install which will be quite locked down so hackers will get a tough time hacking it.

My question (though not directly security related, but I would love to hear some tips from you) is whether I can debootstrap a server system on my computer at home and then recreate the same partition layout on the IRL server and then move over the data from the debootstrapped system to the server.

Am I making myself clear here? At least have some difficulties understanding myself here so please bare with me if I'm a bit unclear on the topic.


Thank you for your help

This gets you no gain whatsoever. Its not uncomon to run multiple servers in paralell, for a backup for developmer server though. Anything important on a web server should be reasonably easy to back up (files served up, special configuration, etc...) which you can easily dump to a live server.

There is no reason you should ever need to backup/copy/move your binaries, libraries, or anything of the sort.

---

