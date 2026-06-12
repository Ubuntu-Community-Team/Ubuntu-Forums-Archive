---
title: "Cloud - Newbie Questions"
date: 2010-11-07
forum: Ubuntu Cloud and Juju
---

### Post by cevo on 2010-11-07
Hi All,

I'm new to cloud computing as i'm sure most people are and I'm trying to get my head around the distribution of resources.

Now I understand you have a "Controller Node" and "Slave Nodes" much like a traditional cluster

Assuming I have 
Server 1: Controller with 500GB Storage
Server 2: Node with 1TB Storage
Server 3: Node with 500GB Storage

I would like to know

A) Is the storage of Server 2 and Server 3 available to the Controller (and thus it's users)
If this is the case is it seemless? (ie would a user only talk to the controller and it would dictate what the user could access)

B) Say I want to Run an apache server and a mysql server - how do these run? do they run on the nodes or the controller?

C) If the answer to B is the Node - do users who want to access a particular service presented by a node access the node directly or the controller?

So if apache is running on Server 2 port 80, and the user connects to Server 1 Port 80 - is the request relayed to Server 2?

D) If the answer to B is the Controller - is this similar to a normal cluster where as the "processing" it just pushed onto the relevant machines?

----------------

In Summary I want to build a scalable "Cluster" / "Cloud" solution where the primary services are Samba, Apache, mySQL, FTP and also VMWare Server

I would prefer a solution where I can also scale the disk space so instead of upgrading a single machine I can attach dedicated storage servers and the available space includes this

Sorry if this seems a bit thick i'm trying to get my head around it and so far documentation and other forums have been little to no help - only telling me how great it is and how it does this or that but not actually telling me how this or that are achieved and the end result for my users.

Kind regards
James

---

### Post by kim0 on 2010-11-07
A) Is the storage of Server 2 and Server 3 available to the Controller (and thus it's users)
If this is the case is it seemless? (ie would a user only talk to the controller and it would dictate what the user could access)

A: No .. the "Storage Controller" typically Server1 for you, will be available to S2 and S3. Having seamlessly scalable storage is "hard"

B) Say I want to Run an apache server and a mysql server - how do these run? do they run on the nodes or the controller?

A: On Nodes

C) If the answer to B is the Node - do users who want to access a particular service presented by a node access the node directly or the controller?

A: They access the controller, well actually a specific IP on the controller which automatically forwards  the connection to the correct backend virtual server

So if apache is running on Server 2 port 80, and the user connects to Server 1 Port 80 - is the request relayed to Server 2?

Yep

----------------

In Summary I want to build a scalable "Cluster" / "Cloud" solution where the primary services are Samba, Apache, mySQL, FTP and also VMWare Server

I would prefer a solution where I can also scale the disk space so instead of upgrading a single machine I can attach dedicated storage servers and the available space includes this


A: Horizontally scaling storage is not so easy, I'd recommend you look at ceph or glusterfs, or nfs4 and offer networked storage. Almost all solutions are kinda too new and not quite ready for prime time

---

### Post by cevo on 2010-11-07
Hi there,

Thank you so much for your answers it helps me greatly, 

so i've set up the Cloud Controller (just waiting on additional hardware to complete the nodes)

Am I right in saying once I set these up as "nodes" any services their running will be automatically mapped by the Cloud Controller? 
or could you point me to the docs so i know how I would achieve this mapping 

So for example if the Cloud Controller is 192.168.0.100 and the node running apache is on 192.168.0.101 when a user tries to request port 80 on 192.168.0.100 it forwards the request to the node 192.168.0.101

With regards to the distributed storage, I'm assuming if I use NFS mounts i can mount storage of a node onto the controller or vice versa?

Kind regards
James

---

### Post by MilneCat on 2010-11-09
Typically, the Cloud Controller controls the nodes, assigning both internal IPs and public IPs...(you give the cloud controller control over a range of public IPs).  Thus, when you bring up a LAMP server on a node, it gets it's own public IP.  

So while the CC is at 192.168.1.100, the LAMP server might be accessed at 192.168.1.201 (depending on the range of addresses you gave the CC).

The users only see a set of IP addresses (or machine names, via the DNS)...they don't know/care if the machines are hardware or virtual (as they would be in this case)....

You can create persistent storage and connect it to a particular instance (in the case above, the LAMP server on 192.168.1.201).  The SC controls the storage (that's where you'd map your NFS vols, I believe) for the instances.

---

### Post by cevo on 2010-11-09
If they can be accessed normally, have their own resources and don't distribute processing or resources unless explicitly mapped
i'm then further confused as to the point of a cloud vs having just separate servers to do different tasks - obviously with a traditional  cluster the nodes would sharing the processing jobs but with a cloud it just sounds like it's a Buzz word for a bunch of servers running separate services and a central controller which apparently does nothing?

Kind regards
James

> **MilneCat said:**
> Typically, the Cloud Controller controls the nodes, assigning both internal IPs and public IPs...(you give the cloud controller control over a range of public IPs).  Thus, when you bring up a LAMP server on a node, it gets it's own public IP.  

So while the CC is at 192.168.1.100, the LAMP server might be accessed at 192.168.1.201 (depending on the range of addresses you gave the CC).

The users only see a set of IP addresses (or machine names, via the DNS)...they don't know/care if the machines are hardware or virtual (as they would be in this case)....

---

### Post by kim0 on 2010-11-10
That's kinda true, a private cloud IaaS will only offer you VMs ondemand, nothing more, which is yes like a server farm. That is useful when you have lots (hundreds maybe) of physical servers, and thousands of customers. The value being the automatic management and allocation of resources. As well as being multi-tenant (user) creating separate networking per user ...etc. In a simple case of 2 servers, it looses much of its value. However, one value that remains, is the ability to auto-scale, which indeed the cloud IaaS doesn't offer much help here except give you fresh VMs when you ask for them. You still have to deploy your software on top.

---

