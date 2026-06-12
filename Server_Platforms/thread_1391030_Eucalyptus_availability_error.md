---
title: "Eucalyptus availability error"
date: 2010-01-26
forum: Server Platforms
---

### Post by steveriddett on 2010-01-26
I am most of the way through setting up a test cloud with UEC. I have two HP ML115 quad core servers. the node has 8gb ram, the cluster controller has 1GB. Both have 320GB hard drives.

They are connected to an old hub.  I also have an EeePC 1000 running Ubunut 9.10 which I am using as the 'control'.

Everything seems to be working except that when I type 

[FONT=Courier New]euca-describe-availability-zones verbose[/FONT]

I get 

[FONT=Courier New]AVAILABILITYZONE   cluster1                   192.168.22.1
AVAILABILITYZONE   |- vm types                free / max   cpu   ram  disk
AVAILABILITYZONE   |- m1.small                0000 / 0000   1    128     2
AVAILABILITYZONE   |- c1.medium               0000 / 0000   1    256     5
AVAILABILITYZONE   |- m1.large                0000 / 0000   2    512    10
AVAILABILITYZONE   |- m1.xlarge               0000 / 0000   2   1024    20
AVAILABILITYZONE   |- c1.xlarge               0000 / 0000   4   2048    20[/FONT]If I try to start an instance of Karmic Koala (the image was installed from the store in the web control panel), I get
[FONT=Courier New]
FinishedVerify: Not enough resources: vm instances.[/FONT]

From what I've been able to glean from the interwebs it seems that the controller is not communicating properly with the node. But I can't figure out how to investigate it further. Does anyone know?

Any help would be most appreciated,

Steve

---

### Post by kiranmurari on 2010-03-24
Hi Steve,

```
AVAILABILITYZONE cluster1 192.168.22.1
AVAILABILITYZONE |- vm types free / max cpu ram disk
AVAILABILITYZONE |- m1.small 0000 / 0000 1 128 2
AVAILABILITYZONE |- c1.medium 0000 / 0000 1 256 5
AVAILABILITYZONE |- m1.large 0000 / 0000 2 512 10
AVAILABILITYZONE |- m1.xlarge 0000 / 0000 2 1024 20
AVAILABILITYZONE |- c1.xlarge 0000 / 0000 4 2048 20

```From the output it looks like you haven't registered the node with the cluster. First you need to register the node with the cluster using the command:
```
$ sudo euca_conf --no-rsync --register-nodes
```The above command will discover the nodes and prompt whether you want to add the node. Once this process is finished you would be able to see the valid capacity for instances that can be run.

For example, euca-describe-availability-zones verbose would show something like:
```
AVAILABILITYZONE        cluster1       192.168.22.1
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0002   1    128     2
AVAILABILITYZONE        |- c1.medium    0000 / 0002   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0001   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0001   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20
```Hope this helps.

---

