---
title: "how to disable CPU via command line"
date: 2012-03-22
forum: The Cafe
---

### Post by dan0804smith on 2012-03-22
disable first core 

echo 0 | sudo tee /sys/devices/system/cpu/cpu0/online

enable first core 

echo 1 | sudo tee /sys/devices/system/cpu/cpu0/online

disable second core 

echo 0 | sudo tee /sys/devices/system/cpu/cpu1/online

enable second core 

echo 1 | sudo tee /sys/devices/system/cpu/cpu1/online

disable third core 

echo 0 | sudo tee /sys/devices/system/cpu/cpu2/online

enable third core 

echo 1 | sudo tee /sys/devices/system/cpu/cpu2/online

disable fourth core 

echo 0 | sudo tee /sys/devices/system/cpu/cpu3/online

enable fourth core 

echo 1 | sudo tee /sys/devices/system/cpu/cpu3/online

great way to improve battery life when using doing non intensive work

i thought that disableing core would reduce power,however upon testing my battery life went from 2:10 to 1:40

i apologize 

i just wanted to contrubute to the ubuntu community because they have been so helpful to me and this command took me a really long time to find

i just wanted to make it easier for people to find so that they could use it for what ever reason.

thank you all for addressing your concerns and correcting me on my false information about improving battery life

once again i will state that by going from 4 cores to 1 core i noticed a significant decrease in my battery life

the command works nevertheless

---

### Post by sffvba[e0rt on 2012-03-22
*Thread moved to **The Community Cafe**.*

Not a support question.


404

---

### Post by 3rdalbum on 2012-03-22
Have you actually noticed a battery life improvement?

Intel says that a core or CPU disabled in this way actually uses more power than if you hadn't disabled it. Maybe AMD CPUs are different.

The whole "disable a core" function was intended for testing purposes, and also for CPU hotplugging (which is done on server systems, where it's possible to physically remove a CPU while the computer is turned on).

---

### Post by Drenriza on 2012-03-22
In theory it's silly to disable a CPU core to improve the battery life. By the very fact, that you add more cores to improve the battery life. Can you see the dilemma:KS?

---

### Post by dan0804smith on 2012-03-22
this is just meant to be guide or 'how to'  for people who want to do this for whichever reason.

just trying to contribute

---

### Post by 3rdalbum on 2012-03-22
> **Drenriza said:**
> In theory it's silly to disable a CPU core to improve the battery life. By the very fact, that you add more cores to improve the battery life. Can you see the dilemma:KS?

Adding more slower cores can improve performance-per-watt over fewer, faster cores.

However, six cores will use more power than 2 identical cores.

---

### Post by CharlesA on 2012-03-22
> **dan0804smith said:**
> this is just meant to be guide or 'how to'  for people who want to do this for whichever reason.

just trying to contribute
Sounds like something that would be good on the wiki.

---

