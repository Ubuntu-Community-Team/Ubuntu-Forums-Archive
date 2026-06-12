---
title: "Node Controller not working on UEC"
date: 2011-06-01
forum: Ubuntu Cloud and Juju
---

### Post by fbcyborg on 2011-06-01
Hello everybody.

I've recently installed UEC using the Install CD and following this guide.
I've used two servers and the first one has the 192.168.108.22 IP (uec1) whereas the node controller has got the 192.168.108.60 (uec2) IP address.

During the node controller setup, the CLC has been detected without any problem but when I perform the following command on uec1, it gives me always the same result:

```
euca-describe-availability-zones verbose
``````
AVAILABILITYZONE        cluster1        192.168.108.22
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20
```I also tried the solution explained [here]("http://open.eucalyptus.com/forum/node-not-recognized-and-no-avalibility-resources"), deregistering the node, the cluster and registering them again but having no success. Anyway it seems the node controller is correctly detected but the resources are still zero!
The instructions were:
> - de-register the node
- de-register the cluster from command line (web GUI re-registration gave same problem)
- restart the cluster controller and the cloud
- register cluster again
- discover node and add itAnd this is what I've done on uec1:
```
euca_conf --deregister-nodes 192.168.108.60
euca_conf --deregister-cluster cluster1
service eucalyptus-cc restart
service eucalyptus-cloud restart
euca_conf --register-cluster cluster1 192.168.108.22
euca_conf --register-nodes 192.168.108.60
```It didn't work for me.

```

# euca_conf --list-clusters
registered clusters:
   cluster1  192.168.108.22

# euca_conf --list-nodes
registered nodes:
   192.168.108.60  cluster1

# euca_conf --list-walruses
registered walruses:
   walrus  192.168.108.22

```How can I solve this problem?

---

### Post by lemon1707 on 2011-06-01
> **fbcyborg said:**
> Hello everybody.

I've recently installed UEC using the Install CD and following this guide.
I've used two servers and the first one has the 192.168.108.22 IP (uec1) whereas the node controller has got the 192.168.108.60 (uec2) IP address.

During the node controller setup, the CLC has been detected without any problem but when I perform the following command on uec1, it gives me always the same result:

```
euca-describe-availability-zones verbose
``````
AVAILABILITYZONE        cluster1        192.168.108.22
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20
```I also tried the solution explained [here]("http://open.eucalyptus.com/forum/node-not-recognized-and-no-avalibility-resources"), deregistering the node, the cluster and registering them again but having no success. Anyway it seems the node controller is correctly detected but the resources are still zero!
The instructions were:
And this is what I've done on uec1:
```
euca_conf --deregister-nodes 192.168.108.60
euca_conf --deregister-cluster cluster1
service eucalyptus-cc restart
service eucalyptus-cloud restart
euca_conf --register-cluster cluster1 192.168.108.22
euca_conf --register-nodes 192.168.108.60
```It didn't work for me.

```

# euca_conf --list-clusters
registered clusters:
   cluster1  192.168.108.22

# euca_conf --list-nodes
registered nodes:
   192.168.108.60  cluster1

# euca_conf --list-walruses
registered walruses:
   walrus  192.168.108.22

```How can I solve this problem?

[LEFT]    It doesn't effact. You should try :
    euca_conf --deregister-cluster cluster1
    service eucalyptus-cc stop CLEAN=1
    service eucalyptus-cloud stop CLEAN=1
    service eucalyptus-cc start CLEAN=1
    service eucalyptus-cloud start CLEAN=1
    euca_conf --register-cluster cluster1 192.168.108.22

    Should you CLEAN=1 affter command to make affect. Good luck[/LEFT]

---

### Post by fbcyborg on 2011-06-02
Thank you for replying. Yes, 

as matter of fact I also tried to add CLEAN=1 clause in one of my previous attempt, and I forgot to tell you here. 
Anyway I tried the steps you recommended but the situation is still the same:
```
AVAILABILITYZONE        cluster1        192.168.108.22
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20
```Could it be that the disk space is too low? Indeed, I installed UEC1 on a 10 GB Hard disk :(
whereas the UEC2 has a 40 GB hard disk.

---

### Post by lemon1707 on 2011-06-02
> **fbcyborg said:**
> Thank you for replying. Yes, 

as matter of fact I also tried to add CLEAN=1 clause in one of my previous attempt, and I forgot to tell you here. 
Anyway I tried the steps you recommended but the situation is still the same:
```
AVAILABILITYZONE        cluster1        192.168.108.22
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20
```Could it be that the disk space is too low? Indeed, I installed UEC1 on a 10 GB Hard disk :(
whereas the UEC2 has a 40 GB hard disk.

Every Eucalyptus's services are started ? You should talk a look at /registration.log to find out the problem. It should be work if all services start.

---

### Post by fbcyborg on 2011-06-02
Here's the last 100 lines of /var/log/eucalyptus/registration.log: [LINK]("http://pastebin.com/jYasGGRN").
It seems all right to me! :confused:

---

### Post by lemon1707 on 2011-06-02
> **fbcyborg said:**
> Here's the last 100 lines of /var/log/eucalyptus/registration.log: [LINK]("http://pastebin.com/jYasGGRN").
It seems all right to me! :confused:

Hi, You should find more information at [http://open.eucalyptus.com/book/export/html/4263](http://open.eucalyptus.com/book/export/html/4263). I think It will help you. Actually I had a problem when i trying to install UEC with Ubuntu 10.04 LTS and I must find out the problem. Good look guy.

---

### Post by fbcyborg on 2011-06-02
Wow! I'm very lucky! 

Thank you anyway!

---

### Post by heartsbane on 2011-06-02
I had the same issue with the same symptoms. I would go int the lengthy story. But, what solved it for me was I noticed that I was running 2 different versions of eucalyptus-common.

One was newer than the other. So after discovering that I just upgraded all controllers and nodes involved:

```
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude full-upgrade && sudo aptitude remove `sudo deborphan` && sudo apt-get autoclean && sudo aptitude purge '~c'
```

Everything came right back up. Let me know if you see any change when you ```
cat /var/log/eucalyptus/registration.log 

```

---

### Post by fbcyborg on 2011-06-03
Thank you very much.

The version of Eucalyptus was 2.0+bzr1241-0ubuntu4.2 on both servers. So it already was the same version.

I performed the upgrade using the command line you posted.
I restarted all the eucalyptus services and the log file is the following:
```
2011-06-03 17:06:11+02:00 | 20015 -> Calling walrus Walrus 192.168.108.22
2011-06-03 17:06:11+02:00 | 20016 -> Calling storage cluster1 storage 192.168.108.22
2011-06-03 17:06:11+02:00 | 20017 -> Calling cluster cluster1 192.168.108.22
2011-06-03 17:06:11+02:00 | 20165 -> Calling node cluster1 node 192.168.108.60
2011-06-03 17:06:11+02:00 | 20165 -> Node 192.168.108.60 is already registered.
2011-06-03 17:06:11+02:00 | 20016 -> SC for cluster1 is already registered.
2011-06-03 17:06:11+02:00 | 20017 -> Cluster cluster1 is already registered.
2011-06-03 17:06:11+02:00 | 20015 -> Walrus 192.168.108.22 is already registered.
2011-06-03 17:07:25+02:00 | 20484 -> Calling node cluster1 node 192.168.108.60
2011-06-03 17:07:25+02:00 | 20484 -> Node 192.168.108.60 is already registered.
```I didn't reboot the machines, I simply performed:
```
service eucalyptus restart CLEAN=1
service eucalyptus-cc restart CLEAN=1
service eucalyptus-cc-publication restart CLEAN=1
service eucalyptus-cloud restart CLEAN=1
service eucalyptus-cloud-publication restart CLEAN=1
service eucalyptus-network restart CLEAN=1
service eucalyptus-sc restart CLEAN=1
service eucalyptus-sc-publication restart CLEAN=1
service eucalyptus-walrus restart CLEAN=1
service eucalyptus-walrus-publication restart CLEAN=1
```on uec1 and

```
service eucalyptus restart CLEAN=1
service eucalyptus-nc-publication restart CLEAN=1
service eucalyptus-network restart CLEAN=1
service eucalyptus-nc restart CLEAN=1
```on uec2, even if I got some error messages like:

[I]eucalyptus start/running, process 19288
eucalyptus-cc start/running, process 19366
eucalyptus-cc-publication start/running, process 19401
eucalyptus-cloud start/running
[B]restart: Unknown instance: 
restart: Unknown parameter: IFACE[/B]
eucalyptus-sc start/running
eucalyptus-sc-publication start/running, process 19839
eucalyptus-walrus start/running
eucalyptus-walrus-publication start/running, process 19858[/I]
on uec1, 

and 
[I]eucalyptus start/running, process 19956
eucalyptus-nc-publication start/running, process 19960
**restart: Unknown parameter: IFACE**
eucalyptus-nc start/running, process 19983[/I]

on uec2.

Finally these are the availability zones:
```
# euca-describe-availability-zones verbose
AVAILABILITYZONE        cluster1        192.168.108.22
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20
```Unless a reboot is suggested/required, the problem seems to be still unsolved.

---

### Post by fbcyborg on 2011-06-03
I tried also to reboot: nothing changed.

```
2011-06-03 17:25:21+02:00 | 3880 -> Calling storage cluster1 storage 192.168.108.22
2011-06-03 17:25:21+02:00 | 3878 -> Calling cluster cluster1 192.168.108.22
2011-06-03 17:25:21+02:00 | 3879 -> Calling walrus Walrus 192.168.108.22
2011-06-03 17:25:21+02:00 | 3923 -> Calling node cluster1 node 192.168.108.60
2011-06-03 17:25:21+02:00 | 3923 -> Node 192.168.108.60 is already registered.
2011-06-03 17:25:21+02:00 | 3879 -> Walrus 192.168.108.22 is already registered.
2011-06-03 17:25:21+02:00 | 3878 -> Cluster cluster1 is already registered.
2011-06-03 17:25:21+02:00 | 3880 -> SC for cluster1 is already registered.
```

---

### Post by fbcyborg on 2011-06-08
> **fbcyborg said:**
> Could it be that the disk space is too low? Indeed, I installed UEC1 on a 10 GB Hard disk :(
whereas the UEC2 has a 40 GB hard disk.
Nobody answered to this question. Could that be the cause of the problem?
I think that at least one virtual machine should be runnable because of the disk space, even if the RAM is enough and the CPU supports VT-x.

**EDIT**: by the way, should [this procedure]("https://help.ubuntu.com/community/UEC/CDInstall#STEP%205:%20Obtain%20Credentials") be done also on the Node Controller?

---

### Post by ldg on 2011-07-13
Was a solution ever found to this problem? 

I believe I have the same issue. I too installed UEC from CD. My NC is registered and it shows in the CC's register log. If I run euca_conf --list-nodes my node appears as registered. However, like you when I run euca-describe-availability-zones verbose my free/max is 0/0.

I would greatly appreciate if you figured out how to fix this or anyone else did. Thank you.

---

### Post by fbcyborg on 2011-07-13
To be honest I gave up! :(
Nobody helped me so far.

---

### Post by ldg on 2011-07-13
Oh man that sucks! I have no option to give up it must be completed.

I seem to be seeing similar issues with other people, but as of yet none have provided a solution.

You can follow a thread of mine to see if it goes anywhere... 
[http://open.eucalyptus.com/forum/run-instances-error](http://open.eucalyptus.com/forum/run-instances-error)

I'm getting pretty close to just reinstalling everything but this time from source to see if I can get somewhere actually. I'll let you know.

---

### Post by fbcyborg on 2011-07-13
Unfortunately I'm also not able to try anything on those machines where I installed UEC. Actually they are located far from my location at the moment. Furthermore, the machines are powered down now and I can't do anything. 

Just for information: do your machines respect all of the UEC hardware requirements? I ask this because in my case there something missing (e.g. the HHDD memory).

---

### Post by ldg on 2011-07-13
Yes, I remember you saying something in previous posts about a 10g hd. Yeah, I have 1000gig still same. 

Possibly we have different issues but for all I see they are the same.

---

### Post by fbcyborg on 2011-07-13
This sounds me very strange actually. Unless the iso image we downloaded is corrupted, but this is not so probable.

---

### Post by ldg on 2011-07-14
Hey man I ditched the installation from CD and installed from package and just followed these steps [https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

IT WORKS!!

So I suggest next time you can maybe try package installation.

The joy I felt when I saw
```
AVAILABILITYZONE	cluster1	192.168.1.173
AVAILABILITYZONE	|- vm types	free / max   cpu   ram  disk
AVAILABILITYZONE	|- m1.small	0012 / 0012   1    192     2
AVAILABILITYZONE	|- c1.medium	0012 / 0012   1    256     5
AVAILABILITYZONE	|- m1.large	0006 / 0006   2    512    10
AVAILABILITYZONE	|- m1.xlarge	0006 / 0006   2   1024    20
AVAILABILITYZONE	|- c1.xlarge	0003 / 0003   4   2048    20

```

---

### Post by fbcyborg on 2011-07-18
Woow! Good to know that it worked! I will try as soon as possible.

Thank you.

---

### Post by tonymaro on 2011-08-02
I've got a cloud that just up and died with this exact symptom. What sucks is that it was working fine until about three hours ago, so it's not the install.  I've tried everything suggested here to no avail.  Sure, a reinstall might fix it but I really can't do that right now.

---

### Post by strychn9ne on 2011-09-13
> **tonymaro said:**
> I've got a cloud that just up and died with this exact symptom. What sucks is that it was working fine until about three hours ago, so it's not the install.  I've tried everything suggested here to no avail.  Sure, a reinstall might fix it but I really can't do that right now.


I'm experiencing simular issues. I could start my own thread..but this seems to be the same issue.

The thing that bugs me, is the availability-zones come and go as the please. One or two nodes will work at any given time, but they never stay up for long. 


> registered nodes:
   x.x.x.x  cluster1
   x.x.x.x  cluster1
   x.x.x.x  cluster1
   x.x.x.x  cluster1


> AVAILABILITYZONE        cluster1        x.x.x.x
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512     5
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    10
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    15


and 3 mins later

> AVAILABILITYZONE        cluster1        x.x.x.x
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0008 / 0008   1    192     2
AVAILABILITYZONE        |- c1.medium    0008 / 0008   1    256     5
AVAILABILITYZONE        |- m1.large     0004 / 0004   2    512     5
AVAILABILITYZONE        |- m1.xlarge    0004 / 0004   2   1024    10
AVAILABILITYZONE        |- c1.xlarge    0002 / 0002   4   2048    15


another 3 mins

> AVAILABILITYZONE        cluster1        x.x.x.x
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0000 / 0000   1    192     2
AVAILABILITYZONE        |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512     5
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    10
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    15

Its very fustrating, seems so damn close, but never sticks around.

I have been able to get a VM up and running and SSH it. However I keep losing availability-zones...:mad:

---

### Post by invernizzi on 2011-10-06
Eucalyptus require a precise time synchronization between all the physical hosts it runs on. If time synchronization is lost, the symptom is the one you're describing.
Install the ntp server on all the machines, and wait for a  little while (~1h) until the time adjustments complete. You should be fine then.

---

