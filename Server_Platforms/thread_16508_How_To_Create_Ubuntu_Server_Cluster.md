---
title: "How To Create Ubuntu Server Cluster"
date: 2005-02-22
forum: Server Platforms
---

### Post by HappyBoy on 2005-02-22
Hi All,

I would like to make server cluster with Ubuntu. This is my first time to do clustering as well as with Ubuntu. 

I have the following scenario in my mind. I want to make several machines running Ubuntu as a cluster. This cluster will act as a FreeNX server and Web server so that every Ubuntu client machine request will be served by this cluster.

I was wondering what kind of Clustering Software that can distribute the workload of FreeNX and Web (Apache) into several machines.

Could someone point me out how to achieve that? 

I appreciate much any suggestion and Thanks in advance.

---

### Post by nocturn on 2005-02-22
I don't know what the goal is with FreeNX.  You want to do remote logins...
One problem with that you will have to address is common home directories.

The easiest way to cluster a group of machines is using DNS round-robin.
This way, you can assign multiple IP addresses to one DNS name.  Your DNS server will return a different result each time it is queried based on an algorithm.  

Another way to do it is load balancing.  For apache, you can look into heartbeat.

The second approach makes sure your load is even on all machines, the first one just makes sure that not one server is doing all the work, but ignores the load on it.

---

### Post by HappyBoy on 2005-02-23
Thanks for the info nocturn, regarding FreeNX, I'd like to distribute the workload of NX server into several machines so that it can handle more requests nicely.

I'm very eager to know how to do DNS round robin and apache load balancing, what kind of tools needed.

You can also point me out some resources/tutorial on this topic, I'm very eager to learn.

I appreciate much your help.

---

### Post by nocturn on 2005-02-23
[QUOTE=HappyBoy]Thanks for the info nocturn, regarding FreeNX, I'd like to distribute the workload of NX server into several machines so that it can handle more requests nicely.

I'm very eager to know how to do DNS round robin and apache load balancing, what kind of tools needed.

You can also point me out some resources/tutorial on this topic, I'm very eager to learn.

I appreciate much your help.[/QUOTE]

Here is the Freshmeat project for Heartbeat: [http://freshmeat.net/projects/linux-ha/](http://freshmeat.net/projects/linux-ha/)
It can provide loadbalancing and failover for several services.

Here is some information about round robin:
[http://www.webopedia.com/TERM/R/Round_Robin_DNS.html](http://www.webopedia.com/TERM/R/Round_Robin_DNS.html)
[http://hacks.oreilly.com/pub/h/79](http://hacks.oreilly.com/pub/h/79)

If you want to do remote desktop with FreeNX, you will require a central storage for /home.  NFS can do this, but it will be both the bottleneck and the single point of failure for your cluster.

---

### Post by nocturn on 2005-02-23
Just saw this one too:
[http://www.zytrax.com/books/dns/ch9/rr.html](http://www.zytrax.com/books/dns/ch9/rr.html)

---

### Post by HappyBoy on 2005-02-25
nocturn, Thanks very much for all those great resources. I found it very helpful to me. :grin:

---

### Post by rick_1010 on 2006-10-14
You might want to try Sshfs for making a shared home directory, then you could set up a machine that is not part of the cluster and is just a file server over the LAN to all of your machines

---

### Post by jaakan on 2006-10-21
Has someone made a "HOW TO" to make a Ubuntu Cluster?

---

### Post by rscheideman on 2006-11-22
Hi there Happyboy,

I would try ORielly for the books on it.

---

### Post by nrgtek on 2008-01-05
> **jaakan said:**
> Has someone made a "HOW TO" to make a Ubuntu Cluster?

anyone?

---

### Post by KDB9000 on 2008-01-29
Bump? 

I am very interested in using Ubuntu to make a cluster system as well, anyone have any luck doing this, or has a howto?

---

### Post by regomodo on 2008-02-04
> **nrgtek said:**
> anyone?

[http://www.oreilly.com/catalog/highperlinuxc/index.html](http://www.oreilly.com/catalog/highperlinuxc/index.html)

---

### Post by ubunt2007 on 2008-04-07
bump? 

anyone know of a guide to this? id rather not buy a book.

---

### Post by koenn on 2008-04-08
clustering is rather complex technology.
The things meantioned in this thread point to load-balancing and fail-over configurations - clustering usually means joining several physical computers together into 1 "virtual" machine - the cluster - so that processing power, memory, .... is joined into 1 "mega" computer. It's partially a load-balancing sollution because the load can be shared over the all computers that are part of the cluster? Because a cluster of computers can be made to continue working if one of the participating compute fails, it's also a fail-over sollution. Yet in implementation it's different from e.g. round robin DNS for load balancing or hartbeat for high availability. 

Here's a 'showcase' of a guy that build a cluster out of several XBoxes :
[http://tweakers.net/nieuws/35025/linux-op-de-xbox-een-goedkoop-pc-cluster.html](http://tweakers.net/nieuws/35025/linux-op-de-xbox-een-goedkoop-pc-cluster.html)

The Beowulf project is al about serious clusters for/with Linux : 
[http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node9.html](http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book/beowulf_book/node9.html)
[http://www.beowulf.org/overview/index.html](http://www.beowulf.org/overview/index.html)


There seem to be some people who experimented with Ubuntu and clustering : 
[http://useopensource.blogspot.com/2007/09/smallest-beowulf-cluster-runs-ubuntu.html](http://useopensource.blogspot.com/2007/09/smallest-beowulf-cluster-runs-ubuntu.html)


Google's search engine uses a combination of DNS-based load balancing and parrallel processing on clusters of "PC" hardware to get massive performance out of "cheap" hardware 
[http://www.scribd.com/doc/312186/THE-GOOGLE-CLUSTER-ARCHITECTURE](http://www.scribd.com/doc/312186/THE-GOOGLE-CLUSTER-ARCHITECTURE)

---

### Post by dannyauble on 2008-04-09
I have found SLURM works well with linux clusters.  It looks like it will be available as a standard package with hardy.  Here is a link to the main website...

[https://computing.llnl.gov/linux/slurm/](https://computing.llnl.gov/linux/slurm/)

There are some tutorials and such on how to get started there.

---

