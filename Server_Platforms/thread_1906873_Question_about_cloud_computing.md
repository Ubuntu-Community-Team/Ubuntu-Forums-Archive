---
title: "Question about cloud computing"
date: 2012-01-10
forum: Server Platforms
---

### Post by mybb4 on 2012-01-10
Hi, I'm new to Ubuntu and i want to learn about cloud computing. I have googled about how to setup private cloud. I finally think about using Ubuntu server UEC. Before i actually setup the real system. i would like to clarify something about cloud.

Most of the time i have been using windows application such as MsOffice, our ERP system currently run on windows. will i able to run these application on cloud? I read the setup guide. i need at least 2 machines. 1st is for cloud controller. 2nd is for VM node.
The VM nodes have to be run ubuntu and use virtual box run windows only? or i can use windows os machince connect as VM node?

In case, I have to use virtual box run windows. will it reduce the performance of system? if yes, is there other alternatives(for free, it's just learning purpose)?

---

### Post by dazman19 on 2012-01-12
from my experience it is probably not a good idea to use virtual box in an enterprise environment. 

I dont know much about UEC, a guy at my work played around with it and got 5 old servers running cloud services. Yeh Ubuntu has to be used as the actual "Host" OS on each of the machines hardware. But as far as i understand it the VM's can be most other OS's (I may be wrong here, i will check with him tomorrow).

I am quite familar with ESXi by vmware. This is a debian based Host, and uses VMotion to do the server balancing, but you will need to buy a license to run it for longer than 30 days. 

I wouldn't use virtualbox... but Its not to say that all oracle products are bad.. Java and Oracle databases are great!...
:guitar:

---

