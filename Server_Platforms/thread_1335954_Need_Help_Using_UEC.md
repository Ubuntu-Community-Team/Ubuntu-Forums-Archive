---
title: "Need Help Using UEC"
date: 2009-11-24
forum: Server Platforms
---

### Post by Aux10 on 2009-11-24
Hi I'm completely new to Linux and I'm trying to setup Ubuntu Enterprise Cloud on my home network. At present I have to computers online: the cloud controller and a node.  I must say for some one who has little idea of what I'm doing I'm pretty far along, but now I'm stuck. When ever I try to run and instance whether I'm using Elasticfox or command line it give out the fallowing error: 
Not enough resources: vm instances.
When I check the cluster using
. ~/.euca/eucarc
euca-describe-availability-zones-verbose
all values return as 000/000
I did pair the node with:
sudo euca_conf --no-rsync --discover-nodes
So basically I'm stuck. Any ideas?

---

### Post by cariboo on 2009-11-28
a bump for the move.

---

### Post by Everett Toews on 2010-01-06
Any luck resolving this issue?  I'm having the exact same problem at the moment.

---

### Post by kc7slu on 2010-01-12
Same issue here as well.  I do not see many ways to fix this yet.
```

#ec2-describe-availability-zones verbose
AVAILABILITYZONE        KickBall        192.168.1.110
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    128     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20

#euca-run-instances -k /home/paul/.euca/mykey.priv emi-DFFC107E -t c1.medium
FinishedVerify: Not enough resources: vm instances.


```

---

### Post by cilbuper on 2010-01-13
Bump for more info.  Also, any good sources for info on EUC?

---

### Post by mithil on 2010-02-07
I also had the same problem.
I suppose that its the front-end CC not interacting with the node controller.
The problem was solved by restarting both the cloud setup!!!

---

### Post by kiranmurari on 2010-03-31
Hi All,

 From your output it looks like the node is not registered with the cluster. Register the node using the following command on the cluster.
```
$ sudo euca_conf --no-rsync --discover-nodes
```If the node is registered properly, you should see some numbers for free and max vms instead of zeros.      

Also please take a look at a detailed answer at the following link.
[http://kiranmurari.wordpress.com/2010/03/22/more-cores-more-vms/](http://kiranmurari.wordpress.com/2010/03/22/more-cores-more-vms/)
   
Hope this helps.

---

