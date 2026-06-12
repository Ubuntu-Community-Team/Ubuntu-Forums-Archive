---
title: "Poor man's super computer"
date: 2008-08-02
forum: Server Platforms
---

### Post by cann0nf0dder on 2008-08-02
I am currently researching joining mulitiple servers to have shared CPUs, RAM and other resources to create a "poor man's super computer" style setup (for a data center i am planning), when i was studying IT a number of years ago we touched on this subject (so i know that it can be done) but i can't remember the terminology or the tools used to achive it (i have tried searching but keep getting pages about sharing printers etc).
I know this can be done with Citrix Metaframe but i would prefer to use Linux (Ubuntu Server) as the DBs, applications and interface are currently being developed on Ubuntu Server (with XAMPP).
The basic concept is to take any number of servers and share the processing between them (from the network it looks and preforms like one single server with heaps of system resources).

Can someone help me with the terminology (so i can search) and/or the name of the tools... or any other information that may be useful.

Thanks
cann0nf0dder

---

### Post by windependence on 2008-08-02
Clustering is what you are looking for.

I'll post some links in a few minutes. :)

-Tim

---

### Post by stinger30au on 2008-08-02
its called a "cluster"

---

### Post by scragar on 2008-08-02
I know rocks is a red hat clustering tool that's apparantly very helpfull, can't say more than that though, not to clued up on clustering

[http://www.rocksclusters.org](http://www.rocksclusters.org)

---

### Post by windependence on 2008-08-02
[https://wiki.ubuntu.com/UbuntuClusters](https://wiki.ubuntu.com/UbuntuClusters)

[http://freshmeat.net/projects/linux-ha/](http://freshmeat.net/projects/linux-ha/)

[http://oreilly.com/catalog/9780596005702/index.html](http://oreilly.com/catalog/9780596005702/index.html)

From one our members here, Koenn:

> Here's a 'showcase' of a guy that build a cluster out of several XBoxes :
[http://tweakers.net/nieuws/35025/lin...c-cluster.html](http://tweakers.net/nieuws/35025/lin...c-cluster.html)

The Beowulf project is al about serious clusters for/with Linux : 
[http://www.phy.duke.edu/~rgb/Beowulf...ook/node9.html](http://www.phy.duke.edu/~rgb/Beowulf...ook/node9.html)
[http://www.beowulf.org/overview/index.html](http://www.beowulf.org/overview/index.html)


There seem to be some people who experimented with Ubuntu and clustering : 
[http://useopensource.blogspot.com/20...ns-ubuntu.html](http://useopensource.blogspot.com/20...ns-ubuntu.html)


Google's search engine uses a combination of DNS-based load balancing and parrallel processing on clusters of "PC" hardware to get massive performance out of "cheap" hardware 
[http://www.scribd.com/doc/312186/THE...R-ARCHITECTURE](http://www.scribd.com/doc/312186/THE...R-ARCHITECTURE)

-Tim

---

### Post by tamoneya on 2008-08-02
all hail helmer: [http://helmer.sfe.se/](http://helmer.sfe.se/)

---

### Post by cann0nf0dder on 2008-08-03
Ahh "Clustering", yeh now i remember.

Thanks for the help and the links guys, it really makes my life easier.
I am sure I'll be asking plenty more questions as this project progresses. ;)

cann0nf0dder

---

