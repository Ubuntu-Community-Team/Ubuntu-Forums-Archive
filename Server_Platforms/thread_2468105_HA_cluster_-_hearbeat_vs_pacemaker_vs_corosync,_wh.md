---
title: "HA cluster - hearbeat vs pacemaker vs corosync, what combo is official?"
date: 2021-10-18
forum: Server Platforms
---

### Post by SergeiFranco on 2021-10-18
A bit of preface:

I have been using pure heartbeat as my HA solution for almost two decades. I like the simplicity of resource managing scripts, the simplicity of its config and and simplicity of the tools.
I have been avoiding the whole pacemaker/corosync thing, as it brings in verbose configs (corosync) and very hard to automate CLI interactive configuration tool (pacemaker/crm).

It got to a point where I had to install heartbeat with "apt-get install heartbeat --no-install-recommends" since it would bring the whole stack in otherwise, that would waste CPU at 100% (probably because it didn't like the manual /etc/ha.d/ha.cf).

I decided to stop being a Luddite and revisit the HA clustering stacks.
My issue is that the documentation is all over the place and it is hard to figure out how all those moving parts come together.

My starting point is:
[https://ubuntu.com/server/docs/ubuntu-ha-introduction](https://ubuntu.com/server/docs/ubuntu-ha-introduction)

I have been reading this document on pacemaker:
[https://clusterlabs.org/pacemaker/doc/deprecated/en-US/Pacemaker/2.0/html-single/Clusters_from_Scratch/index.html](https://clusterlabs.org/pacemaker/doc/deprecated/en-US/Pacemaker/2.0/html-single/Clusters_from_Scratch/index.html)
It seems that the pacemaker is resource manager just like heartbeat, and corosync is ???:
> 
Cluster Membership Layer, provides reliable messaging, membership and quorum information about the cluster

As I understand the documentation the corosync config defines the members of the clusters, and pacemaker defines resources and fencing?

The biggest gripe against pacemaker is that the tool is interactive. It makes it hard to automate and backup the configuration.

The stuff I was building are exclusively two node cluster, some might utilize the SBD fencing (via watchdog, heartbeat has no configuration for the SBD).
One of the reason I decided to look into the pacemaker/corosync is because it seems that configuration for SBD is more flexible with that stack.

---

### Post by LHammonds on 2021-10-19
You can achieve HA in a variety of ways with various levels of HA.

Take for example a database-driven web server.  You could have the database and website on a single server and have a 2nd one laying in wait to take over if the other goes dark.

Or you could go super-nova in your system to make sure it can handle millions of users and break apart each service so the database is on its own dedicated server and break it down to a cluster of dedicated database servers and then create multiple database proxies on top of that which are used by multiple web servers which are behind multiple web proxies. I created such a system for an ISP and here is how I did it with HAProxy and Keepalived:
[How to Load Balance Apache Web Server on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260")
[How to Load Balance Galera/MariaDB Servers on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=264")

The above system utilizes almost a dozen servers at minimum but has redundancy built in at each layer.  If a proxy server goes dark, another can take over, if a web server goes dark, another can take over, if a database server goes dark, another can take over.  HA doesn't stop there either...if you are running a virtual environment, you'd need to make sure there are at least two different host machines with two different network storage systems, each with their own (different power circuit and internet connection).

HA is not just software, it is also hardware and location design...making sure you can survive a single point of failure.   Such as failed hard drive(s), failed server, failed UPS, failed circuit breaker, failed Internet, failed hardware firewall, flooded server room, city-wide power outage, tornado, denial-of-service attack, etc.

The more HA you have at various levels, the less risk you have of your service going down if disaster strikes....but with each level of redundancy comes cost.  So there has to be a cost/risk balance.  You need to present a risk/cost tradeoff to your stakeholders and let them decide how much risk they want to afford.  It usually isn't to the level I just described though but the ability to survive an onsite disaster such as a fire is something that backups can help mitigate but is not an instant-on scenario...but many sacrafice those additional high-costs for always-online scenarios for a "we can eventually recover" backup scenario.   But like I said, you need to strike a balance and make sure EVERYONE is aware of the HA design and its limitations that you end up with.

HA should also take into account for service maintenance at every level.  Allow for the system to stay online even if you need to apply BIOS updates to a server, OS patches, database upgrades, web server updates, etc.

LHammonds

---

### Post by SergeiFranco on 2021-10-19
I am well aware what HA is ;). I have built hundreds HA setups utilizing different architectures (from IPVS to F5 for layer4+ balancing, and from heartbeat to BGP for failover).

The question was specifically around pacemaker/corosync replacing plain old heartbeat, and path forward for the pacemaker/corosync.
The tangential question was how to handle the automation regarding pacemaker config, since it is the command driven (as opposed to config file driven).

Due to inertia, and "don't fix what is not broken" I have actively been avoiding using pacemaker/corosync, by using heartbeat on its own and using my scripts to do the service checks etc.
I am revisiting the pacemaker/corosync stack because it seems that plain old heartbeat is no longer a supported use case.

For clarity my question should have been:

As for ubuntu community (and canonical), is the pacemaker/corosync stack a technology that will be supported in the future and one of the supported clustering solution?
How one would approach automating pacemaker configuration, for example with something like Ansible? 

I suspect this requires a shell script that dumps the running config into a file, and ansible compares the file with stored config and if different it applies the correct config? This seems to be a massive cludge (I wish pacemaker was config file driven and not interactive).

---

### Post by LHammonds on 2021-10-20
I cannot answer that question because I'm just a person that uses the various operating systems to accomplish what is needed (and many times I no say in what platform was used).

But if that system is command-driven, then it seems to me that scripts can be written to issue the commands you need and you could create a config file those scripts would utilize as global variables/functions.  Then you could roll out a server with those scripts, crontab schedules and the imported config file for those scripts.  If done right, you could control how those scripts are run with just the settings in your config file...assuming the commands you are talking about can be run in batch mode and not truly "interactive" that requires keyboard input (which seems like a very bad idea considering this system needs handle its issues when humans are not present.

Many of the [scripts I have created](https://github.com/LHammonds/ubuntu-bash) utilize a standardized config file that is imported into each script so that every script knows where to store their log files, how many days archive files should be retained before being purged, etc.  I'll back out of this thread and leave it to those that can answer your question.

LHammonds

---

### Post by SergeiFranco on 2021-11-07
After a bit of reading and experiments I have stumbled upon this bug:

[https://bugs.launchpad.net/ubuntu/+source/watchdog/+bug/1891801](https://bugs.launchpad.net/ubuntu/+source/watchdog/+bug/1891801)

It is a bit alarming that the bug is more than 1 year old.

The solution to this issue is following:
```
systemctl edit --full watchdog.service
```

and replace:
```
After=multi-user.target
```
 with 
```
After=basic.target
```

The actual issue was around watchdog services starting too late (it needs start before sbd) and ultimately causing pacemaker to fail to start due dependency on the sbd service (sbd relies on the watchdog to start).

---

