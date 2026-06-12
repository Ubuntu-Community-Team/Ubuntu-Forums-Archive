---
title: "DLM not working on GFS2/pacemaker servers"
date: 2016-01-18
forum: Server Platforms
---

### Post by daniel-benoy on 2016-01-18
One of my clusters is having a problem. It's no longer able to set up its GFS2 mounts. I've narrowed the problem down a bit. Here's the output when I try to start the DLM daemon (Normally this is something corosync/pacemaker starts up for me, but here it is for the debug output):
```
# dlm_controld -D -q 04561 dlm_controld 4.0.1 started
4561 our_nodeid 168528918
4561 found /dev/misc/dlm-control minor 56
4561 found /dev/misc/dlm-monitor minor 55
4561 found /dev/misc/dlm_plock minor 54
4561 /sys/kernel/config/dlm/cluster/comms: opendir failed: 2
4561 /sys/kernel/config/dlm/cluster/spaces: opendir failed: 2
4561 cmap totem.rrp_mode = 'none'
4561 set protocol 0
4561 set recover_callbacks 1
4561 cmap totem.cluster_name = 'cwwba'
4561 set cluster_name cwwba
4561 /dev/misc/dlm-monitor fd 11
4561 cluster quorum 1 seq 672 nodes 2
4561 cluster node 168528918 added seq 672
4561 set_configfs_node 168528918 10.11.140.22 local 1
4561 /sys/kernel/config/dlm/cluster/comms/168528918/addr: open failed: 1
4561 cluster node 168528919 added seq 672
4561 set_configfs_node 168528919 10.11.140.23 local 0
4561 /sys/kernel/config/dlm/cluster/comms/168528919/addr: open failed: 1
4561 cpg_join dlm:controld ...
4561 setup_cpg_daemon 13
4561 dlm:controld conf 1 1 0 memb 168528918 join 168528918 left
4561 daemon joined 168528918
4561 fence work wait for cluster ringid
4561 dlm:controld ring 168528918:672 2 memb 168528918 168528919
4561 fence_in_progress_unknown 0 startup
4561 receive_protocol 168528918 max 3.1.1.0 run 0.0.0.0
4561 daemon node 168528918 prot max 0.0.0.0 run 0.0.0.0
4561 daemon node 168528918 save max 3.1.1.0 run 0.0.0.0
4561 set_protocol member_count 1 propose daemon 3.1.1 kernel 1.1.1
4561 receive_protocol 168528918 max 3.1.1.0 run 3.1.1.0
4561 daemon node 168528918 prot max 3.1.1.0 run 0.0.0.0
4561 daemon node 168528918 save max 3.1.1.0 run 3.1.1.0
4561 run protocol from nodeid 168528918
4561 daemon run 3.1.1 max 3.1.1 kernel run 1.1.1 max 1.1.1
4561 plocks 14
4561 receive_protocol 168528918 max 3.1.1.0 run 3.1.1.0

```

As you can see, it's trying to configure the node addresses, but it's unable to write to the 'addr' file under the /sys/kernel/config configfs tree (See the 'open failed' lines above). I have no idea why. dmesg isn't saying anything. Nothing is telling me why it doesn't want me writing there. And I can confirm this behavior on the prompt as well.

Trying to start CLVM results in complaints about the node not having an address set, which makes sense given the 

Here's the exact same command run twice. First, on a very similarly configured cluster (which is currently running):
```
# cat /sys/kernel/config/dlm/cluster/comms/169446438/addrcat: /sys/kernel/config/dlm/cluster/comms/169446438/addr: Permission denied
```
(That's what I expect to see. It's a write-only file.)

And now on this messed up cluster:
```
# cat /sys/kernel/config/dlm/cluster/comms/168528918/addr
cat: /sys/kernel/config/dlm/cluster/comms/168528918/addr: Operation not permitted
```

Why 'operation not permitted'? dmesg isn't telling me anything at all, and I don't see any way to get the kernel to spit out some kind of explanation for why it's blocking me. Can anyone help? At least point me in a direction where I can get the system to give me some indication why it's behaving this way?

I'm running Ubuntu 14.04

---

### Post by daniel-benoy on 2016-01-19
Figured it out. This was caused by McAfee Antivirus.

---

