---
title: "HA for virtual machines"
date: 2010-04-29
forum: Virtualisation
---

### Post by stevet20 on 2010-04-29
Hi,
 
Could anybody possible point my the right direction. I've come from a VMware background using ESX, vSphere etc where its easy to create a cluster where VM's can be vMotioned between hosts and where VM's can be automatically restarted on other members of the cluster should a host fail.
 
Being new to Linux and to Ubuntu I would like to recreate a similar setup with KVM. I've managed to get KVM up and running along with live migration using iSCSI shared storage but I dont know how to approach the HA part. 
 
I was thinking along the following lines but cannot find information on how to complete it. 
 
2 x node runing Ubuntu server & kvm
 
1 x shared storage for vm's using iSCI and ocfs2
 
Got this far for live migration but dont know how to approach the next but was thinking along the lines of
 
Packemaker and OpenASI for the clustering part and cluster messaging
 
Some for of file locking to stop vm's from being started on both node at the same time
 
And finally failover of vm if we lose a node
 
Any help/suggestion would be greatly appreciated
 
Steve

---

