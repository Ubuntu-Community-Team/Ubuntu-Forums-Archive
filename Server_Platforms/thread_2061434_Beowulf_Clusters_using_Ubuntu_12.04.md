---
title: "Beowulf Clusters using Ubuntu 12.04"
date: 2012-09-22
forum: Server Platforms
---

### Post by curious9 on 2012-09-22
from the past few days, i was trying to build a Beowulf cluster out of three machines.
i installed Ubuntu 12.04 server ed. for the master node and Ubuntu 12.04 Desktop ed. for other nodes.
i followed this website step by step: [http://byobu.info/wiki/Building_a_simple_Beowulf_Like_Cluster_with_Ubuntu](http://byobu.info/wiki/Building_a_simple_Beowulf_Like_Cluster_with_Ubuntu)

Every thing when smoothly until i encountered problem while setting up mpd. I tried several other blogs to trouble shoot the problem and i figured out that mpich2 doesnt come with mpd deamon rather there is another called  Hydra. (i am not sure about this.) i tried to use Hydra (mpiexec ) but it not working 
it is giving error such as no routes from host to nodes.

upto this step i followed everything on the blog and it worked fine (like setting up  ssh and login to nodes from master node without password)

---

### Post by figure002 on 2013-05-12
Hello curious9,

I'm the author of that tutorial. After reading your post I decided to revise the tutorial. I just finished updating it for Ubuntu 12.10.

You are correct that new versions of MPICH2 no longer come with MPD, but with Hydra instead. The MPICH Wiki explains this nicely:

> MPD has been the traditional default process manager for MPICH till the 1.2.x release series. Starting the 1.3.x series, Hydra is the default process manager. - [Frequently Asked Questions - Mpich]("http://wiki.mpich.org/mpich/index.php/Frequently_Asked_Questions")

So I revised the entire tutorial and included steps for configuring Hydra. I also made other changes throughout the tutorial, so you might want to read through the tutorial again. The URL for the tutorial has changed as well: [http://byobu.info/article/Building_a_simple_Beowulf_cluster_with_Ubuntu/](http://byobu.info/article/Building_a_simple_Beowulf_cluster_with_Ubuntu/)

---

### Post by patrick-wood29 on 2014-01-14
> **figure002 said:**
> 
So I revised the entire tutorial and included steps for configuring Hydra. I also made other changes throughout the tutorial, so you might want to read through the tutorial again. The URL for the tutorial has changed as well: [http://byobu.info/article/Building_a_simple_Beowulf_cluster_with_Ubuntu/](http://byobu.info/article/Building_a_simple_Beowulf_cluster_with_Ubuntu/)


I am new to the clustering world and I followed your tutorial step by step, but once I get to the point of running mpdboot everything works great.  At that point it tells me mpdboot command not found.  Any help would be greatly appreciated.

---

### Post by serrano-pereira on 2014-01-14
> **patrick-wood29 said:**
> I am new to the clustering world and I followed your tutorial step by step, but once I get to the point of running mpdboot everything works great.  At that point it tells me mpdboot command not found.  Any help would be greatly appreciated.

From the tutorial:

> MPD has been the traditional default process manager for MPICH till the 1.2.x release series. Starting the 1.3.x series, [Hydra]("http://wiki.mpich.org/mpich/index.php/Hydra")  is the default process manager.(10) So depending on the version of  MPICH you are using, you should either use MPD or Hydra for process  management. You can check the MPICH version by running mpich2version in the terminal. Then follow either the steps for MPD **or** Hydra in the following sub sections.

It seems you followed the steps for MPD, while you should be using Hydra instead.

---

