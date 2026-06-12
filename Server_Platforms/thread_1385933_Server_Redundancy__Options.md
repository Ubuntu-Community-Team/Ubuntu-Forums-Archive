---
title: "Server Redundancy  Options"
date: 2010-01-20
forum: Server Platforms
---

### Post by Jasonx86 on 2010-01-20
Morning all,

Can anyone please list options available for server redundancy? (i.e. fault tolerance methods so that if a server goes down another server can take over).

Also is it possible to implement RAID1/disk mirroring across servers?

thanks all.

---

### Post by iponeverything on 2010-01-20
Something like this?:

[http://wiki.samba.org/index.php/CTDB_Project](http://wiki.samba.org/index.php/CTDB_Project)

---

### Post by Jasonx86 on 2010-01-20
Thanks but not what I'm looking for.

LOL what's clustered samba? (The project definition doesn't even clarify what the thing does!) Just looking for a simple solution for server redundancy.

More suggestions are welcome...

---

### Post by koenn on 2010-01-20
> **Jasonx86 said:**
> Thanks but not what I'm looking for.

LOL what's clustered samba? .

lol, it's distributed  storage ([http://ctdb.samba.org/](http://ctdb.samba.org/) ), and therefor a solution for what you call "disk mirroring across servers"


For the other question, look up Linux High Availability

---

### Post by steven.jones on 2010-01-20
> **Jasonx86 said:**
> Morning all,

Can anyone please list options available for server redundancy? (i.e. fault tolerance methods so that if a server goes down another server can take over).

Also is it possible to implement RAID1/disk mirroring across servers?

thanks all.

1) Virtualisation.
2) Virtualisation.
3) Virtualisation.

;]

I have looked at and used clustering technologies over the last decade....complex, hard to maintain and flaky...and often less stable and reliable than a single box. If you have to get that availability the you will need to cough up some $.

The simplest by far is virtualisation....you can get VMware's ESXi for free to try, or use the open source ones, or MS's hyperV...

regards

---

### Post by steven.jones on 2010-01-20
"Also is it possible to implement RAID1/disk mirroring across servers?"

Hmm not easily...you need common storage at the backend...trying to get disk i/o synchronized over a network just makes my hair stand on end at the thought...Most technologies to do this are asychronus using quite complex and expensive tech/software to do it. Maybe if you tell us what services / applications?

---

### Post by koenn on 2010-01-20
> **steven.jones said:**
> 1) Virtualisation.
2) Virtualisation.
3) Virtualisation.

;]



You're right that virtualization makes a lot of things a lot easier, and it's pretty solid technology.

However, seeing that the OP wants load balancing, we may assume that 1 machine is not up to the job. Adding a hypervisor in the mix isn't going to change that.
If he's aiming for redundancy (also mentioned in the OP), again, 1 machine ain't going to cut it, with or without hypervisor. 

So what do you think virtualisation has to offer here ?

---

### Post by gombadi on 2010-01-20
> 
Can anyone please list options available for server redundancy? (i.e. fault tolerance methods so that if a server goes down another server can take over).

Also is it possible to implement RAID1/disk mirroring across servers?


There are lots of options depending on what you want to protect.

This is a how we did it (your situation may vary) -

We have a large number of environments that we needed to run. i.e. php4, php5, php5.2, mysql 4 and mysql 5. All done with high availability of some sort.

We configured four physical machines with between 4 and 15 virtual environments on each using OpenVZ to keep things separate and two nfs servers.

We currently have 5 ip addresses that we send different sites to. They go to a firewall/load balancer that sends the connection to one of the virtual environments sitting on one of the four physical servers. This means we can shutdown one of the physical machines and the traffic will be sent to the remaining VE's on the other physical machines.

To keep all the websites reading from the same page so to speak we have two nfs servers. They use the ha package for failover if the main system stops. We also use drbd to create a raid 1 array between the two nfs servers. 

During normal operation the the web VE's read from the master nfs server. If it fails then ha will swing the virtual ip address over to the standby, activate the drbd partition and start nfs. It normally takes between 15 and 30 seconds to fail over from master to standby.


As I said this is just how we did it and your situation may differ. Can you tell us more about what you are trying to do?

---

### Post by Xianath on 2010-01-21
I hope [this]("http://www.drbd.org/") will get you started.

Cheers,
Peter

---

