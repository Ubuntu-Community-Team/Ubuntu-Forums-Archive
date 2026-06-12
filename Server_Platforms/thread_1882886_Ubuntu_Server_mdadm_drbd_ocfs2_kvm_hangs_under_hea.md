---
title: "Ubuntu Server mdadm drbd ocfs2 kvm hangs under heavy file reading"
date: 2011-11-18
forum: Server Platforms
---

### Post by fretto79 on 2011-11-18
I have deployed four ubuntu 10.04 server. They are coupled  two by two in a cluster scenario. on both sides we have software raid1  disks, drbd8 and OCFS2 and on top of it some kvm machines run with qcow2  disks.
  

I followed this: [https://wiki.ubuntu.com/ClusterStack/LucidTesting#Pacemaker.2C_drbd8_and_OCFS2_or_GFS2](https://wiki.ubuntu.com/ClusterStack/LucidTesting#Pacemaker.2C_drbd8_and_OCFS2_or_GFS2)
  

corosync is just used for DRBD and OCFS, the kvm machines are run "manually"
  When it works is fine: good performances, good I/O, but at a given  time one of the two cluster started hanging. Then we tried with just one  server turned on and it hangs the same. 



All we can do is force shutdown (hold the button) and restart and when it turns on again the raid on which relay drbd is resyncing. All the time it hangs we see such fact



It seems to happen when an  heavy READ in one of the virtual machines occurs, that is during rsyn  backup. When the fact occurs the virtual machines are not reachable any  more and the real server responds with good delay to the ping but no  screen and no ssh is available.
  

After a couple of week of pain on one side this morning also the  other cluster hung, but it has different motherboard, ram, kvm  instances. What is similar is reading for rsync scenario and Western  Digital RAID Edistion disks on both side.
  Can anybody give me some input to solve such issue? 



Thanks in advance
Stefano

---

