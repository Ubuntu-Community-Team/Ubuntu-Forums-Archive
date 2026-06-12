---
title: "MySQL Load Balanced and High Available Solution?"
date: 2011-03-11
forum: Server Platforms
---

### Post by CyberAngel on 2011-03-11
Hello,

I am reading lately information on how to setup an Active/Active Load Balanced and High Available (If one of the nodes is down the system still runs) MySQL cluster.
I have found quite a few howto's but I have some things unclear in my mind.

I found a few solutions like this one: [http://www.howtoforge.com/loadbalanced_mysql_cluster_debian](http://www.howtoforge.com/loadbalanced_mysql_cluster_debian)
or this:
[http://techgurulive.com/2011/02/03/how-to-install-and-configure-multi-master-replication-manager-for-mysql/](http://techgurulive.com/2011/02/03/how-to-install-and-configure-multi-master-replication-manager-for-mysql/)

Those are using two or four MySQL nodes, two Load Balancers to avoid a single point of failure but only one MySQL cluster management server.
What happens if the MySQL cluster management fails?

I have also found a "MySQL Master-Master Circular Replication" technique but from what I read, with this option there is a chance that conflicts will arise if node A and node B both insert an auto-incrementing key on the same table.

Any suggestion and a tutorial on how to setup such a system correctly?

---

### Post by BkkBonanza on 2011-03-11
I can't comment on the cluster mgmt failure aspect though it makes sense you may want to consider what happens in that event.

Regarding the auto-incrementing key on multiple masters the usual practice is to specify an increment step equal to the server count, (eg. 2) and have them start with an offset. For 2, the 1st server starts at 1 and adds 2 each insert, the second server starts at 2 and adds 2 each insert, they are odd/even. This way each insert causes an exclusive set of records that get propagated to the other server and are not possible to conflict.

If your application is read intensive (as most web apps are, they write much less than they read), then you may find it much much simpler to go with a single master (and failover) and N number of read only servers. In this common case the reads get load balanced and have less issues to worry about. And the writes get directed only to the master. One simple way to do this is to configure the web server to direct all POST requests to the master and all GET requests to the slaves. I did this for an image DB application I wrote.

Aside: Properly designed web apps should only update the DB during a POST and only read during a GET. And when data returned from a POST is needed, the POST redirects to a GET to return data to the user. "PRG" [(POST returns GET)]("http://www.theserverside.com/news/1365146/Redirect-After-Post") for more info on that method (presuming you don't already know about that). Done correctly POST is write-only, GET read-only.

---

