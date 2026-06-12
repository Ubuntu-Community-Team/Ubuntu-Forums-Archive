---
title: "Cluster Idea"
date: 2008-06-02
forum: Server Platforms
---

### Post by greg73654 on 2008-06-02
Hi, I was just wondering, I have about 10K saved right now (yeah, I know, it's a lot ^_^). I was wondering if I could build a cluster with AMD Phenom Quad-Core 9850's (with supporting RAM, DVD Drive, etc.) and actually use all the cores as a spectacular cluster. But I don't know if xUbuntu would be able to recognize all the cores or not, I hope to build a system with 10 PCs which is 40 cores. Any help in my venture would be much appreciated.

P.S. I forgot to mention I would like to use Beowulf as the server and a simple GUI program would be much needed also.

Thanks all! ^_^

---

### Post by windependence on 2008-06-02
Well. that's probably a lot more money than you need. What are you going to do with cluster when it's finished? 

You should probably use Opterons instead, Phenoms are more consumer than server.

I don't see why Ubuntu would not be able to see all the cores, it just has to see them on each machine and I have one running that recognizes 8 cores currently with no problems.

-Tim

---

### Post by greg73654 on 2008-06-02
Well, the Opteron might be a better choice, but the phenoms are cheaper! ^_^

But really this thing is more for s's and giggles. I'd really like to build a stable one to start and then work towards a goal that I could use it for. I'd really like to have some ideas on what it could be used for (besides scientific calculations and multi-media, cause I've heard those. ^_^)

---

### Post by btmiller on 2008-06-02
In order to use a distributed memory cluster, you need to have some sory of task that can be decomposed into many subtasks (so that eachsubtask can run on a particular processor). Most software is not written like this.

In a cluster, each node has its own operating system. Software has to be written to run on the different machines and communicate back and forth as needed. If the communication is intense, regular Ethernet may not do, which is why some cluster use 10 Gbps Ethernet or InfiniBand. If, however, the subtasks don't need to communicate a lot than regular Ethernet will do just fine. If you don't have software in mind that can use a cluster, and you don't know your networking requirements, then it's kind of pointless to go out and build one.

BTW, "Beowulf" is a type of cluster made out of commodity hardware and software. There's no signle set of beowulf software (although some software is written to work in beowulf environments). I suggest you look at [www.beowulf.org](www.beowulf.org) for more information.

---

### Post by greg73654 on 2008-06-02
Then I guess my question is, what different software CAN be clustered and what is a good OS/Program to be used as a cluster? Preferably an easy one.

And is there not a GUI that I can use for any of these that is equally as easy?

Thanks! ^_^

---

### Post by btmiller on 2008-06-02
Where I work, we run a lot of computational chemistry software on our cluster. Most clusters I know of are used for doing high endscientific research (computer simulations for physics, chemistry, biology, meterology, cosmology, etc.). The other use of clusters is fordoing a lot of multimedia encoding (but from your post above, you already know that...)..

Unfortunately most desktop type software is not particularly amenable to parallelizatio. However, if you've got complex number crunching going on in oocalc or the like, that could be split up (but I don't think there's any way to do this with current versions of OO -- I could be wrong though). But normal Web browsing type applications don't need many resources.I was thinking about games the other day,as they tend to require a lot of power. Maybe some chess engines have been parallelized?

In any case, unfortunately I don't know of any easy GUIs to set these things up. Clusters are fairly complex beasts, and if you find yourself lost on the command line then setting one up may be a tricky proposition. The point is that they don't tend to be "point and click" sort of things -- they take work and understanding to set up to run optimally.

Edit to add: of course, if you just want some mechanism for distributing projects around a bunch of boxes, look at OpenMosix. It's not really like having a parallel cluster, though, just a way to load balance work over a bunch of different boxes.

---

### Post by HunterThomson on 2008-06-02
You could use a cluster to crack encryption.....

I think OpenMosix or synergy is more what your looking for though.

---

### Post by greg73654 on 2008-06-02
OK, thanks you all, I think openMosix might be my choice of software. I have heard about the different types of clustering, but wasn't sure on which one to go with. Thanks for the help! ^_^

---

