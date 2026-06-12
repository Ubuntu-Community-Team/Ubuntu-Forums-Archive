---
title: "Ubuntu &amp; SPARC HPC cluster possible?"
date: 2007-11-20
forum: Sun Sparc Users
---

### Post by jcastill on 2007-11-20
Hi,

I got a lot of Ultra60 lying around. I've been searching around and find little information about building a cluster in Linux. My idea is to build a cluster using some of this ultra60 as to make them do more than look nice on the rack they are right now. I've seen about openmosix etc but I must ask first if anybody has done this (if it's even possible) and if not, if you got any tips to save me some time. I promise to publish my results on this when I get it running (if I ever get it).

Thanks

Jose

---

### Post by mercedcollege on 2007-11-20
Yes we have a main and 19 nodes 

I would search around sourceforge.net. I have sun blades 100  install with Unbuntu 6.06 I am using CDS cluster I dont have the clustering program set up for the class  but when i do I will post.

---

### Post by jcastill on 2007-11-21
Thanks for the information. I will try to install cds and read about it. Thanks for the heads up!

Jose

---

### Post by mercedcollege on 2007-11-21
Unbutu 6.06 LTS its a easy install. But we had a diffcult time installing 7.07 or it's to new for that processor so we have Ubuntu 6.06 You might want to double the ram on the main node.

To Install the OS 

Press stop-a 

ok? boot cdrom 

Hope you have fun setting up your cluster

---

### Post by jcastill on 2007-11-21
I have them already runnin ubuntu, the main question is how to setup CDS to work among all of them. I've been trying to find some documentation but even the sf page has empty folders in the documentation zone.

Any ideas on that side?

Thanks a lot for the help!!!

---

### Post by mercedcollege on 2007-11-21
yes I am playing with that program as we speak 
i will post asap

---

### Post by mercedcollege on 2007-11-21
I dont have a clustering program to work with sprac proccessor. I thought i had one but it not working. Any suggested cluster program with documention. I am having problems connecting to the network It seem I add the dns sever once i added the dns it still doesn't work 

But I am still working and waiting.

---

### Post by netztier on 2007-11-22
> **mercedcollege said:**
> I dont have a clustering program to work with sprac proccessor. I thought i had one but it not working. Any suggested cluster program with documention. I am having problems connecting to the network It seem I add the dns sever once i added the dns it still doesn't work 


If the DNS server you are using is BIND version 9 and runs on a multiprocessor Sparc machine, you have to modify it's configuration so that it uses obly one CPU: 

See this thread: [http://ubuntuforums.org/showthread.php?t=458271](http://ubuntuforums.org/showthread.php?t=458271)

regards

Marc

---

### Post by jcastill on 2007-11-27
Did you fix the dns issues? I've been looking around and it looks like almost all HPC clusters are made for 2.4.x series of Kernels. There is a Knoppix distribution for HPC but it's only for x86; yet as Knoppix and Ubuntu are based on Debian I still have hope to find something.

---

### Post by netztier on 2007-11-27
> **jcastill said:**
> Did you fix the dns issues? 

No, I just worked around it by restricting bind9 to one CPU. Worked as intended.

best regards

Marc

---

### Post by moe_syzlak on 2007-12-08
Hey I don't want to start another thread just to ask a question, so I'll just ask it here.

Does Linux run faster on a SPARC processor vs a multicore system with the same number of cores and processor clock speed?

---

### Post by jcastill on 2008-02-07
I really don't know.... Also, anybody has something new on the topic? I've tried a lot of alternatives with cero positive results.

---

