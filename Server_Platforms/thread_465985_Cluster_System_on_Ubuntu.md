---
title: "Cluster System on Ubuntu"
date: 2007-06-06
forum: Server Platforms
---

### Post by dini on 2007-06-06
Hi everybody !

First, sorry i'm French :).

I post here, because on the French Forums of ubuntu, nobody  could help me 

Studying in data processing, and being currently in training period my problem is as follows: 

I must set up a system of clusterisation on  5-6 “nodes” (maybe more).
The cluster must be used in order to "load balancing" during use of office applications, on Ubuntu, such as OpenOffice, Firefox… 

The requests for connections to the cluster should border the 150-200 per day, which could increase in the future, for that it is necessary to envisage to be able to add 1 or several “nodes” in the future

 I want know which were the software solutions in order to answer my problem, and which would be architecture corresponding network.

---

### Post by Chayak on 2007-06-06
There are several cluster systems for Linux.  The one I'm most familiar with is [openmosix]("http://openmosix.sourceforge.net/") I've played around with it in the past and it's worked fairly well for me.  I haven't looked at it lately though.

---

### Post by dini on 2007-06-07
Thanks Chayak ;)

I found OpenMosix and i will try it soon.

Is there someone who have others solutions?

Thanks !

---

### Post by Cheese Sandwich on 2007-06-07
I've though of the load balancing issue before, and a "low-tech" approach might be to write "job request" files to a central directory, and have all machines in the cluster run loops in a shell, looking for job requests in that directory. Then when it sees a job request file, it could grab that job & move or delete the job request file, execute the job, then when it's idle again resume watching the central job directory.

I've never done this before, mind you - hopefully there are no collision issues, for example if two machines try to grab the same job file at the same time.

---

### Post by tutomlin on 2007-06-11
Hi,

I've seen some other threads looking at clustering with ubuntu, and most of the time OpenMosix does not work because it requires the 2.4 kernels, and something in ubuntu (the x server I think) requires the 2.6 kernels.

As far as I know the only really basic 2.6 kernel, load sharing cluster ap for what you want to do is the kerrighed cluster (the project is run by a bunch of French people in fact) this is the link to their english pages: [http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)
As far as I can tell the Kerrighed group is updating their software much more frequently than the OpenMosix group so you may get better support from them too.

I've never used kerrighed personally but I suspect that your best bet for a load sharing cluster that people need to log into, would be to run a kerrighed cluster and then have people remote log in using ssh.

If you don't need the X environment then OpenMosix is a much more established solution than Kerrighed.

Hope that helps

Tucker

---

### Post by dini on 2007-06-13
Thanks for your help tutomlin ;)

i hope that it helps me in my work.

Maybe, i'll repost here in few days if i need help XD.

---

