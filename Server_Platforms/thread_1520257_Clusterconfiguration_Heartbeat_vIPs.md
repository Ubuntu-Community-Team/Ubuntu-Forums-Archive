---
title: "Clusterconfiguration Heartbeat vIPs"
date: 2010-06-29
forum: Server Platforms
---

### Post by Timo2500 on 2010-06-29
Hi,

I am currently trying to setup a cluster using heartbeat. Unfortunatly it does not do what I want to do. I am using heartbeat 2.1.4-11 on a readhat system. I am using the the cib for configuration.

What I want to do is the following:
I have two Nodes. I want to run a clone resource on both nodes. It's named I want to run as a clone. This works fine.
Additionally I want to have two virtual IP adresses. One should be set on Node 1 the other on Node 2. This works fine as well.
I want to set dependencies between the resources. And this is where I have problems.
What I want to achive:
In case named is not able to run on a node, the vIP should switch to the other node (which then will have both vIPs). In case both nodes are able to run named, there should be one vIP on each node. Sounds simple, but does not work.
Accourding to the heartbeat docu this an be achieved by using
'<rsc_colocation id=&#8221;stats-with-clone1&#8221; from=&#8221;vIP-1&#8221; to=&#8221;named-clone&#8221;/>'
'<rsc_colocation id=&#8221;stats-with-clone2&#8221; from=&#8221;vIP-2&#8221; to=&#8221;named-clone&#8221;/>'
Even if I set a score it does not work as expected.

But this does not work. It does not conform to the dtd and so is not possible to set.

Any ideas how to achive the result I am looking for?

Cheers
Timo

---

### Post by Timo2500 on 2010-06-30
No ideas? Does anyone know a forum specialized to heartbeat/cluster?

Timo

---

