---
title: "I needs a lotta help please q.q"
date: 2010-11-23
forum: Ubuntu Cloud and Juju
---

### Post by wardrive on 2010-11-23
**UEC** ( cloud and whatever you call it )
First off, I'm not a real wiz with linux, I just use linux to help out friends in configuring and installing it in their computers. For the pas few days I've been trying to make UEC work out. I've manage to get everything right (I think?) so there I came when running the instance, and this message came out. = FinishedVerify: Not enough resources (0 < 1: vm instances.Not enough resources (0 < 1: vm instances.

I know, I fail so what I did next was:
$:euca_conf --no-rsync --discover-nodes
message: INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.

So basically I don't know what I needa do, I've tried to google this but nothing helped with the documentations. I'm a total newbie, please help me out and please... bare with me x_x...
thank you.

---

### Post by kim0 on 2010-11-24
hey there
Most likely the node are not registered. Can you run the command

euca-describe-availability-zones verbose

and post the output

---

