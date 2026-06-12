---
title: "Ubuntu: intelligent assist OS"
date: 2007-03-24
forum: Server Platforms
---

### Post by FeraTech on 2007-03-24
After hearing about how it is possible to have networked computers work in unison. I forget the name of the software but what if this was incorporated into the Ubuntu core?

For example there are two computers with Ubuntu on the same network. One of them is idle while the other is running a full processor load. What if both computers when set up have the option of working together when one is idle. 

Especially in an office with a server there can be a lot of strain on the server at certain time of the day. 

Also, this can be the easiest way to lessen server load. All you would have to do is find a couple old PC and hook them up anywhere in the network. They don't even need a keyboard and monitor and since they would always be idle the server could utilize them at any time along with other idle PCs on the network.

Also to make sure the idle host PC can still be usable all information sent to it can be in packets small enough to where as soon as the user logs on it would take only a couple seconds to free up the PC.

My company works in schools and small businesses with a lot of older PCs which could easily be used in this fashion. I guarantee that if this was incorporated into Ubuntu it would be the number #1 operating system we would use.

For those with any experience in the matter please comment on the idea. My company might even want to fund this project if it is plausible due to it's marketability for our clients.

Robert Stolorz
Fera Tech, Inc.

---

### Post by adam.tropics on 2007-03-24
It's pretty interesting stuff, though for the average 'me', am not sure how practically useful it would be. Fun project though! A couple interesting reads for you.
[http://www.ubuntuforums.org/showthread.php?t=377835&highlight=cluster+computer](http://www.ubuntuforums.org/showthread.php?t=377835&highlight=cluster+computer)
[http://pareto.uab.es/mcreel/ParallelKnoppix/Tutorial/Tutorial.html](http://pareto.uab.es/mcreel/ParallelKnoppix/Tutorial/Tutorial.html)

---

### Post by Icidic on 2007-03-24
Generally speaking though, most programs need to be redeveloped to incorporate Cluster Computing features as they were never meant for doing their 'stuff' with more than one computer.

Having said that, Video and Image rendering and encoding is just the type of stuff that DOES support Cluster Computing - and yes, there are significant gains in productivity and otherwise.

However, I'm not sure how plausible or even how possible it is to use Network Computers' CPUs as extra 'beef' for one main, central computer or server.  I imagine it has been attempted somewhere, just I've never heard of people being able to harvest the unused CPU cycles of older computers to make one central computer faster.

Hope this helps.  I can see much Googling in the near future for you :D.

---

### Post by elst on 2007-03-25
Many types of database software (LDAP, DNS, SQL) include their own features to maintain multiple synchronised copies of a single database, so that you can split the load between a master and multiple slaves. Often a server is actually limited by I/O, rather than CPU, so running additional slave services on other machines can solve performance issues.

I think that the Ubuntu repositories have packages for the Red Hat clustering products used in RHEL, but I haven't really looked into it.

EDIT: On Edgy, the package is "redhat-cluster-suite", and the "system-config-cluster" package provides a graphical management tool. AIUI, this is a general-purpose load-balancing and failover system, and can be extended to support many types of service.

---

