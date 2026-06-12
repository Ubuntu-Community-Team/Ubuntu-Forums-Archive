---
title: "Cluster help"
date: 2015-01-30
forum: Server Platforms
---

### Post by cryptonyteteam on 2015-01-30
I have 2 of the exact same pc's and I wanted to know what are the benefits of making a cluster. Would I be able to run a lamp server and a [samp ]("http://sa-mp.com") server and stretch the work load across both pcs'?

---

### Post by lukeiamyourfather on 2015-01-30
Cluster is just a generic term. Some applications are designed to take advantage of multiple machines in a cluster scenario and some are not. Them both being identical usually doesn't matter. Can you be more specific about what you're wanting to improve the performance of?

---

### Post by cryptonyteteam on 2015-01-30
I want to run my public sa-mp server on a more powerful / reliable setup. along with a mysql server

---

### Post by nerdtron on 2015-01-31
We'll if you just want to share the load (especially web page) you don't necessarily have to "cluster".

A common setup to this is that you create two server with the same applications and web pages, but each have their own IPs, then put them behind a network load balancer. Hardware load balancer are extra devices and which you declare the IPs of the Servers. in this case you will want to load balance traffic going to port 80, and then split that traffic to the two servers. This setup is more related on the network side rather than system administration.

Another setup can be done by having another server, which you will act as the load balancer. This server will accept all HTTP request to your website, but it will not serve any webpage at all. It will redirect all traffic it receives to the other two web servers which will serve the web pages.

---

### Post by TheFu on 2015-01-31
> **cryptonyteteam said:**
> I have 2 of the exact same pc's and I wanted to know what are the benefits of making a cluster. Would I be able to run a lamp server and a [samp ]("http://sa-mp.com") server and stretch the work load across both pcs'?

The prior posts explained it well. TNSTAAFL - the overhead (processing, storage, complexity, maintenance issues) of trying to have loads split up across different servers usually isn't worth the hassle for non-critical applications to a business.  

Clustering is usually for HA - High Availability and to reduce downtime.  Application servers generally don't use clustering. They use load balancers. Smarter load balancers will see that an app server isn't responding and will remove that IP from the list it has for a DNS name.  

DBMS servers are routinely clustered.  There are a few different modes:
* Active/failover
* Active/standby
* Active/Active
* Active/replicated (sync or async)

Different DBMS tools support the different modes. Sometimes the application (i.e. the specific DBMS) use doesn't support most of these. Also, the storage architecture will limit what's possible too - most cluster setups require a SAN with the storage available to all machines in the cluster.

We don't use mysql, but I think it is common to setup an active/replicated setup.  Last time I looked, the commercial version of mysql supported master/master DBs, but that isn't free.  I'd look at MariaDB first, if I wanted commercial support.  I'd look at Postgres if I needed my data to be around and had lots of clients writing to the same records.

Synchronized writes to 2 DBMS 1,000 miles apart is slow. Some applications are willing to pay that cost, if data loss cannot be allowed.
Asynchronous writes to 2 DBMS 1,000 miles apart can lead to a small amount of data loss due to a failure - usually less than 1-2 minutes, but doesn't have the slowdown for the write. If you aren't a bank, this is probably the best trade-off.

We always looked at the cost of downtime to the business. If that cost for 1 day down was more than the cost of all the effort + networking + storage + extra servers, only then would we setup clusters for an application.  One of my clustered applications was brought down due to a corrupted DBMS at 10am. Took until 6pm to get it backup - those 8 hrs of downtime cost the company something like $10M.  What's worse is that they'd purchased everything needed to have made this at most a 1 hr outage, but hadn't deployed it.  The customer decided the order of system updates and "new features" always took priority over boring EMC BCV setup and testing.  Took us about a month to determine the root cause, convince the customer is wasn't the fault of any person on the team, and get the system setup and tested to minimize this sort of issue ever again.  Learned more than I care to know about EMC BCVs.  I should say the application had about 100 servers, spread across 3 data centers, and the Oracle DBMS ran on multiple 32-way HP-UX boxes with local failover and remote replication. About 22K employees used this system as their primary system at work, so the cost of downtime wasn't just financial, but having thousands of workers unable to do anything while still paying them is a real cost too.

Anyway - hope this helps.

---

