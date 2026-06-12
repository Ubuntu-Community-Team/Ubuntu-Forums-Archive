---
title: "High Availability Cluster (tweaking)"
date: 2023-03-08
forum: Server Platforms
---

### Post by joolspb on 2023-03-08
Hi All,

I've got a DRBD/Pacemaker/Corosync installation running and have a couple of snags that I'd appreciate some help with.  The cluster comprises 3 servers, drbd1, drbd2 and drbdquorum, the third server being there to solve the problem of both sides of the cluster continuing to act as if they're the only survivor if a nic goes down, creating a split brain scenario.

I'm now in the position where overall, the system does what it's meant to do though with one or two final issues to solve.  Firstly, if say drbd1 has the primary role and it suffers an instantaneous power fail, pacemaker flips the NFS service that the cluster is providing over to drbd2.  Once drbd1's been switched back on and it's booted, it'll synchronise itself from drbd2 and the whole plot carries along along as if nothing happened.  I have a VM server running off of it at the moment and it doesn't seem to care about the very short delay as it switches.   If however, I reboot drbd1 using shutdown -r or reboot, drbd1 will start to shutdown but the cluster doesn't switch to drbd2.  Pacemaker will also sit there meditating for ages while it decides what it needs to be doing and the share drops out completely leaving the VMs to go off and do their own sweet little thing, usually ending up with a corrupted VM image that needs resurrecting.

This leaves me wondering, Is it pacemaker trying to politely disconnect that stops the NFS share from switching during reboot and do I need to shorten the timeout for the system to shoot pacemaker in the head when the server is shutting down or is there some procedure I need to follow to shut the relevant services down in order to stop the server hanging on the way down.  The whole setup is running off a 2200VA UPS and at the moment, the shutdown time if done automatically, is longer than the battery life of the UPS.

Thanks in advance,

J.

---

