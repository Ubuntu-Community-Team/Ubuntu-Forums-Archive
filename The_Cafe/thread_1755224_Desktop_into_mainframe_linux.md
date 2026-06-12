---
title: "Desktop into mainframe linux"
date: 2011-05-10
forum: The Cafe
---

### Post by vehemoth on 2011-05-10
Does anybody know of any tools to turn a desktop into a mainframe server. I'd be interested in trying it out but if I can't I'll just make some other sort of server.

---

### Post by earthpigg on 2011-05-10
Mainframes are defined by their size and power, not just the software on them.

An example of a mainframe without the size and power would be your desktop with ubuntu server edition and some other stuff installed on it.

---

### Post by vehemoth on 2011-05-11
I thought a mainframe was when you had a powerful computer that was used for processing and many much less powerful computers that connected to it on a network and used it to process everything. So you basically have your "computer system" run elsewhere and you just see the input and output to it.

---

### Post by earthpigg on 2011-05-11
I could be mistaken, but I believe that would be called a cluster.

I see lots of goole results for "Ubuntu Cluster", but I'm not knowledgeable enough to tell high quality from poor quality documentation so I cannot recommend any of them. Based on my faith in Wikipedia, though, I offer:

[http://en.wikipedia.org/wiki/Mainframe_computer](http://en.wikipedia.org/wiki/Mainframe_computer)
[http://en.wikipedia.org/wiki/Computing_cluster](http://en.wikipedia.org/wiki/Computing_cluster)

---

### Post by earthpigg on 2011-05-11
Neat.

[http://en.wikipedia.org/wiki/Beowulf_%28computing%29](http://en.wikipedia.org/wiki/Beowulf_%28computing%29)

> A cluster can be set up by using Knoppix bootable CDs in combination with OpenMosix. The computers will automatically link together, without need for complex configurations, to form a Beowulf cluster using all CPUs and RAM in the cluster. A Beowulf cluster is scalable to a nearly unlimited number of computers, limited only by the overhead of the network.

[http://en.wikipedia.org/wiki/LinuxPMI](http://en.wikipedia.org/wiki/LinuxPMI)

> LinuxPMI (Linux Process Migration Infrastructure) is a Linux Kernel extension for multi-system-image (in contrast to a single-system image) clustering. The project is a continuation of the abandoned openMosix clustering project.

...


How LinuxPMI works is perhaps best described by an example. You may have a network of ten computers (nodes) and there is one user working on each node. Nine users are working on simple tasks that do not necessarily use their machine to the full potential. One user is working on a program that spawns a lot of jobs that would overload his computer. Since we have nine nodes on the network that have a lot of free resources, they can basically take over some of the jobs from the one computer that would otherwise be overloaded. In other words, LinuxPMI will migrate jobs from busy computers to computers that are able to perform the same task faster. Even if all ten users were using their machines for heavy tasks, it could be that not all machines are fully occupied at the same time, and LinuxPMI will use these to reduce the load on other machines.

---

### Post by boydrice on 2011-05-11
> **vehemoth said:**
> Does anybody know of any tools to turn a desktop into a mainframe server. I'd be interested in trying it out but if I can't I'll just make some other sort of server.

check these links out.

[http://en.wikipedia.org/wiki/Mainframe_computer]("http://en.wikipedia.org/wiki/Mainframe_computer")

[http://www.hercules-390.org/]("http://www.hercules-390.org/")

---

