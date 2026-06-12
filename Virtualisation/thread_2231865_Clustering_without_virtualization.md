---
title: "Clustering without virtualization"
date: 2014-06-28
forum: Virtualisation
---

### Post by komppa97 on 2014-06-28
Hi! I have lot of IBM servers and I want to make cluster. But Ibm´s motherboard didn´t support virtualization, only hyper threading. I checked few way to do cluster for example proxmox and beowulf. 
Proxmox require virtualization , but if I understand right beowulf didtn´t need that? How it can be possible btw? :D

So, I´m wondering what is easiest to cluster all my servers? Can I cluster them with vmware or virtualbox,, Help me :D and thanx a lot :)

---

### Post by tgalati4 on 2014-06-28
What problem are you trying to solve?  What model of IBM server?  How much power do they draw at idle?

[Beowulf]("http://en.wikipedia.org/wiki/Beowulf_cluster") cluster has been around a long time, before modern virtualization.

---

### Post by komppa97 on 2014-06-28
My model is Ibm Xseries 345 and I am thinking how I can cluster mine servers easiest way. 
I tried beowulf with ubuntu server and I lost my mind with that :mad:

What do you think could this implement with VMware solutions?
Wmware ESX 2.5 is supported with ibm 345, but I cant find 2.5 version anymore :(

Thanks a lot and I apologize for the bad English :D

---

### Post by tgalati4 on 2014-06-28
Those servers (2003 vintage Xeon's) burn a lot of power:

 > Heat output

Approximate heat output in British thermal units (Btu) per hour

    Minimum configuration: 341 Btu/hour (100 watts)
    Maximum configuration: 2200 Btu/hour (645.2 watts)

They probably average 300 watts each.  

When setting up a cluster for multiprocessing, you need to think about what problem you are trying to solve.  How you set up the cluster will depend on what software you plan on running.

Beowulf is not easy to set up, but it is appropriate for the age of your servers.  A more modern approach would be to use MAAS--metal-as-a-service--configuring your machines to spin up instances of software on demand.

If you thought beowulf was hard, MAAS redefines hard:  [https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure)

What is the Use Case for these machines?  What is your goal?  Other than spend a lot on electricity will little to show for it.

---

### Post by TheFu on 2014-06-28
There are many different sorts of clustering. None require virtualization, but it is usually what current-gen systems deploy since they are very CPU powerful and easily handle most workloads.

I've used clustering for HA of DBs in an Active-Standby and Active-Failover configuration, but I get the feeling you aren't interested in that.

Beowulf is used for solving large scientific problems that can be easily split up into thousands of tiny tasks. If the workload you have can be split like that - great.  Most normal workloads cannot be split like that and if they can, lots of people these days are choosing to write their custom apps using GPU pipelines. For many workloads, this is higher performance, much less cost in hardware and less electricity.

The workload matters most. Determine that before deciding how to move forward.

I've had the option of getting old servers cheap - I always pass for the reasons stated by tgalati4.  Heck, with PaaS offerings, it is relatively cheap to rent CPU time from Amazon, Rackspace, or the 500 other PaaS guys for a day to try new stuff out.

---

