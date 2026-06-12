---
title: "Automatic Server Mirror"
date: 2010-10-22
forum: Server Platforms
---

### Post by iaw4 on 2010-10-22
Dear ubuntu server experts---given how cheap computers are, I am wondering if there is now a seamless server mirroring solution available.

in a perfect world, I would purchase the same hardware twice, and everything that happens on one server is replicated on the other server over the network.  (this can be done modestly asynchronously.  I would like this, because it would allow me to locate the servers in two different locations.  if one building burns down, the other server is still there.)  there should be one exception---the two servers should be able to respond to apache in a coordinated fashion.  that is, either should be able to respond to a request for a web page.  this is important.  I want both servers to be usefully active.

when one server goes down, the second should take over completely.  when it comes back up, it knows to sync itself again.

I do know about RAID on disks but this would presumably keep the disks in one location  if the building burns down, the disks will be gone.  besides, having disks locally mirrored would also make read-access faster than if the disks have to be accessed over network, too.

it would be cool to pull the plug on one server, then reattach it, and users never noticing it.

is there an easy turnkey solution?

/iaw

---

### Post by psusi on 2010-10-22
> **iaw4 said:**
> 
is there an easy turnkey solution?


No.

For a web server you can set up the DNS so that the host name will point to both servers, then make sure you keep both configured the same ( you might want to use rsync for this ) and then if you use a database backend, set up the database servers to synchronize with each other.

---

### Post by iaw4 on 2010-10-22
thanks.  time for someone to invent a distro that does this...

/iaw

---

### Post by BkkBonanza on 2010-10-23
You can use a distributed file system to do this.
GlusterFS comes to mind and is in the repos. For a general overview and further links see, [wiki article.]("http://en.wikipedia.org/wiki/Distributed_file_system") You would configure in mirror mode and anything written to one system is auto-replicated to the mirrors.

Of course, you still need to handle failover properly. This involves monitoring and DNS failover. Also, your web app software (or at least config) needs to be aware as it would need to proxy POST requests to the master server. I've done that (without using GlusterFS) and it works (using just MySql replication).

---

### Post by pneumatic on 2010-10-23
[http://www.drbd.org/](http://www.drbd.org/)

Use DRBD with asynchronous replication in active-passive mode.  The passive server will replicate the first server and function as a hot standby.

---

### Post by nutznboltz on 2010-10-26
> **BkkBonanza said:**
> Y
GlusterFS comes to mind

Hi,

I saw you mention GlusterFS.  Do you use it?

I reported this bug yesterday:

"Data Corruption bug in GlusterFS 3.0.2"
[https://bugs.launchpad.net/ubuntu/+source/glusterfs/+bug/666494](https://bugs.launchpad.net/ubuntu/+source/glusterfs/+bug/666494)

So the current long term "support" version of Ubuntu can destroy your data if you use GlusterFS on it.

Close your eyes and visualize a airplane in a tailspin while the passengers are reading the instruction manuals because the bureaucratic airline crew doesn't think it's any of their business that the airplane is in a tailspin and if you have a concern, merely spend a few days learning how to function in their bureaucracy so that you become savvy enough to submit a report exactly the way they want it to be.

So here I am studying how to make a debdiff, meanwhile you are promoting the use of GlusterFS despite the fact that people could lose data using it.

At least I found the manual on how here:

[https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff#Creating%20A%20Debdiff](https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff#Creating%20A%20Debdiff)

and my KVM guest that I'm using to experiment has been patched so it's time to get busy again.  But I'm glad I took the time to scribble this.

---

### Post by nutznboltz on 2010-10-26
> **nutznboltz said:**
> Hi,

I saw you mention GlusterFS.  Do you use it?

I reported this bug yesterday:

"Data Corruption bug in GlusterFS 3.0.2"
[https://bugs.launchpad.net/ubuntu/+source/glusterfs/+bug/666494](https://bugs.launchpad.net/ubuntu/+source/glusterfs/+bug/666494)

So the current long term "support" version of Ubuntu can destroy your data if you use GlusterFS on it.

Close your eyes and visualize a airplane in a tailspin while the passengers are reading the instruction manuals because the bureaucratic airline crew doesn't think it's any of their business that the airplane is in a tailspin and if you have a concern, merely spend a few days learning how to function in their bureaucracy so that you become savvy enough to submit a report exactly the way they want it to be.

So here I am studying how to make a debdiff, meanwhile you are promoting the use of GlusterFS despite the fact that people could lose data using it.

At least I found the manual on how here:

[https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff#Creating%20A%20Debdiff](https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff#Creating%20A%20Debdiff)

and my KVM guest that I'm using to experiment has been patched so it's time to get busy again.  But I'm glad I took the time to scribble this.

OMG! Ubuntu *is* British, isn't it?

---

### Post by HermanAB on 2010-10-26
Rsync is your friend.

---

### Post by SeijiSensei on 2010-10-26
> **BkkBonanza said:**
> it works (using just MySql replication).

I've always seen the database as the single point-of-failure in most systems with replicated webservers.  How quickly does MySQL replicate changes in one database instance to another?  If I'm making a transaction, I need the database to update essentially immediately.  Also, how do you handle sessions? Since web requests are stateless, and round-robin DNS offers servers at random, how do I make sure that a session created on server 1 is available when the user navigates to a different page and lands on server 2?  (I realize things like DNS caching reduce the probability of such an event, but the chances are certainly not zero.)

I'm sure there are solutions to all these issues, but I suspect they're not easy to implement.  Am I wrong?

Rsync would work for static content, but most modern sites are database-driven and the content is created on the fly.

[I can't recall the last time I built a web site that didn't have a database backend and use session cookies.]

---

### Post by BkkBonanza on 2010-10-27
I've generally noticed replication happens almost immediately, within seconds.

I had a site setup on two servers, one in UK and one in Texas. I used geo-directed DNS via a TinyDNS patch I created. Users from Europe would get directed to the UK and from other places to Texas. Since I wasn't using round robin I didn't have sessions change on users. Even from Texas -> UK updates were within seconds.

One way to handle the sessions is to use mysql for the session data and it gets replicated along with other data. I think there is a handler for that. I tried this but didn't get the desired result and ended up manually handling the session data in mysql, which wasn't too tricky either. Once the session data is in mysql the session can be used on any of the servers.

Users on the UK server who edited/added data (it was a photo gallery type app) would get proxied onto Texas by intercepting POST requests on the UK server. I use Nginx and this was just an extra line if I recall. Then the mysql replication would update the UK db within a few seconds. It did mean that updates may lag a few seconds but in this application I decided that wasn't a problem.

I think using DRBD is a good idea and would be faster and maybe more reliable than mysql replication. I haven't tried it yet though.

---

### Post by HermanAB on 2010-10-27
Look at the Heartbeat project:
[http://www.linux-ha.org/wiki/Main_Page](http://www.linux-ha.org/wiki/Main_Page)

---

### Post by hawk2010 on 2010-10-27
Why not simply use Duplicity to do the replication ?

---

### Post by psusi on 2010-10-27
> **hawk2010 said:**
> Why not simply use Duplicity to do the replication ?

Duplicity is a backup program.

---

