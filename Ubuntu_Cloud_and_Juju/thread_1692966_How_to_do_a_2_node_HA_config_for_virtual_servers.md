---
title: "How to do a 2 node HA config for virtual servers"
date: 2011-02-22
forum: Ubuntu Cloud and Juju
---

### Post by tdhfox21 on 2011-02-22
Hi folks, I am a new linux user. I have been looking at using ubuntu to create a 2 node HA server platform to support a Windows SBS. But I getting a mixed up on heartbeat and DRBD and UEC.
Can anyone help me with a best practice config to accomplish what I am trying to do? If you have proven experience in this field, we are looking for consultation on this configuration.

---

### Post by raymdt on 2011-02-22
Hi tdhfox21 and welcome to the ubuntu forum.
Please don't use abreviation when you try to explain your Problem since since not every body understand what your mean.
Please try to give more details about your purpose and your topology

---

### Post by kim0 on 2011-02-23
Are you only planning on using Ubuntu as a hypervisor (clustered) for running Windows SBS ? Have you guys considered replacing your windows servers with a full Ubuntu server stack

If you're only interested in windows, perhaps you should go with hyperv instead if it better fits the rest of your needs. Let us know more info about your setup and needs

---

### Post by tdhfox21 on 2011-02-23
OK, to rephrase my question...
I have been looking at using ubuntu to create a 2 node High Availability server platform to support a Windows Small Business Server. But I getting a mixed up on Heartbeat and Distributed Replicated Block Device and Ubuntu Enterprise Cloud config.
 
The reason I am doing it on a linux platform is purely one of cost. SBS delivers a suite of products that are demanded from my usual client-base, but to deliver that in a failover style scenario using microsoft as a platform is prohibitively expensive, especially considering that we are only wishing to create a platform upon which to then run virtual machines.
 
What I am ideally looking to create as a "Node+1" failover environment upon which we can install virtual machines. That if any particular node fails, the cluster can "pick up the load" and keep the virtual machines running.
 
I know this can be done. I have read enough about the tools that are available to see it can be put together, but I am looking for someone with experience to assist me in pulling this project together.

---

### Post by kim0 on 2011-02-25
What you describe is definitely possible. The usual problem in such scenarios would be presenting the same storage to all nodes and ensuring storage is not out-of-sync (not by 1 second)

If your target is having two physical servers, then as you mentioned, I'd recommend you use drbd across the 2 boxes to replicate storage instantly. Any VM can be started on any of the two hosts. Cluster scripts can check host health, and reboot VMs on the other healthy nodes.

If your target is having more than two physical servers (say 10), the easy way is to split them into pairs (5 pairs in that case)! This is easy and wasteful, since basically half the machines are on standby

The other more elaborate solution, would be to have shared storage (expensive SAN?) or some other high throughput NFS share and store VMs on that (or iscsi, or fcoe ...). In that case any of the 10 physical servers can start any VM in case of failure. Of course in that case, the shared storage needs to be made redundant itself (SAN replication, drbd or whatever). You're also advised to perform regular backups (perhaps through shared storage instant snapshots). I had built systems that utilized Sun Solaris as the backing store for large scale VM clusters, the idea was using zfs's snapshotting capabilities. Anyway, I think I've shed light on the available options and compromises

All the best

---

### Post by yanaek on 2012-01-13
I have the similar project. I have 3 servers, and I want to use at least 2 as redundant nodes, for Ubuntu database server, mail server (postfix), file server and web server.

I also have Symantec NetApp, which I want to use as a store for virtual machines, available on all nodes.

Question is, if cluster controller goes down, will second node automatically startup virtual machines? Or do I have to have redundant controller then?

In this case I could actually save one of the three servers, because as far as I remember I can use one host as a node and controller.

---

