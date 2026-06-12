---
title: "powernowd options"
date: 2004-12-08
forum: The Cafe
---

### Post by nuopus on 2004-12-08
I am using ubuntu on my laptop using powernowd to do the cpu frequency. Problem is it really slows down the performance and it is not as snappy.
 
 So I went ahead and edited the /etc/default/powernowd and added the following line: OPTIONS="-q -m 1 -p 100 -u 70 -l 10" and it seemed to make the performance go up while will having it throttle down when inactive.
 
 What do you guys think of these options? Do you think they will make my CPU scale too much and have it negatively effect battery life?

---

### Post by Holser on 2006-12-08
I have reported a bug and workaround. Just take a look at [https://bugs.launchpad.net/distros/ubuntu/+source/powernowd/+bug/74980](https://bugs.launchpad.net/distros/ubuntu/+source/powernowd/+bug/74980)
and modify startup script as shown there.

---

