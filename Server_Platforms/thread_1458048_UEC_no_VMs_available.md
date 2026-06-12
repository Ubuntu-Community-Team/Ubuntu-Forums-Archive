---
title: "UEC no VMs available"
date: 2010-04-19
forum: Server Platforms
---

### Post by gzmask on 2010-04-19
Hi guys, got a question with eucalyptus with Ubuntu enterprise cloud: 

My node/could/cluster controllers are all in one server, but looks like my node controller isn't talking to the cluster controller.

When I check "euca-describe-availability-zones verbose" there is none free/max available. 

I check the "/etc/eucalyptus/eucalyptus-ipaddr.conf", the node ID should be correct. 

In the "/var/log/eucalyptus/registration.log" shows that  "2010-04-19 10:39:08-06:00 | 3245 -> Node 142.3.31.158 is already registered." 

I ran "sudo euca_conf --no-rsync --discover-nodes" couple times and all I got is "INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.
"

So what does this mean? Is my node server talking to the cluster controller? If not, what would I do to fix this?

---

### Post by gzmask on 2010-04-19
I found a SOLUTION! If anyone is looking at this problem, here's how I got it fixed:

euca_conf --deregister-cluster <cluster-name>
euca_conf --register-cluster <cluster-name> <ip-address>


and mine is working after these two commands:
euca-describe-availability-zones verbose
AVAILABILITYZONE	xxx 142.xxx.xxx.xxx
AVAILABILITYZONE	|- vm types	free / max   cpu   ram  disk
AVAILABILITYZONE	|- m1.small	0002 / 0002   1    192     8
AVAILABILITYZONE	|- c1.medium	0002 / 0002   1    256     8
AVAILABILITYZONE	|- m1.large	0000 / 0000   2    512    15
AVAILABILITYZONE	|- m1.xlarge	0000 / 0000   2   1024    20
AVAILABILITYZONE	|- c1.xlarge	0000 / 0000   4   2048    20

Hope this helps.

---

### Post by MilneCat on 2010-11-09
Kudos, GZMask!!!

I installed UEC 10.10 on a single machine and spent the whole night going over everything I could think of, but couldn't get the nc to talk to the rest of the cloud.  Your idea to deregister and re-register the cluster worked like a charm!

Now I'm watching my first instance come up.  Thank you! :popcorn:

---

