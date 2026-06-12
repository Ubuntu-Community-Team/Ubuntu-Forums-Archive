---
title: "Changing Number of Runlevel Links"
date: 2010-01-22
forum: Server Platforms
---

### Post by ICEB3AR on 2010-01-22
Hi there

I would like to change the number of the runlevel links:
 /etc/rc<runlevel>.d/S**<NUMBER>**<service>

My question is now if there are any defualt/reserved Numbers for Services or if i can take any number i want to. So for example if i change it to S45<service>, but this is by default used by nfs server - or anything like that - and the nfs-server wouldn't take another number it would be a problem.

best regards

---

### Post by BkkBonanza on 2010-01-22
The nmber just determines the order they run and there can be duplicates. The program that actually does this is called run-parts so if you want more details on how it is handled then,

man run-parts

---

### Post by ICEB3AR on 2010-01-22
Thank you for your answer. :D

I exactly wanted to change the order, but didn't know if there are any defaults. 
Have a nice day.

---

