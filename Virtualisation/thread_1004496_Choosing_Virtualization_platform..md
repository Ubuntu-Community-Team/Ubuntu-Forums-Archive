---
title: "Choosing Virtualization platform."
date: 2008-12-07
forum: Virtualisation
---

### Post by sopsaare on 2008-12-07
Hi guys!

I'm choosing a virtualization platform now. I have been thinking of like 3 to 4 servers / workstations as cluster. Making it to go MAX 3k€. 

I have come to decision about the hardware alrdy and it will feature 3 Phenom/Opteron based 4core 8gb/ram servers. The storage is not yet decided however. This is because the Virtualization softwares wary in terms of fail-over protection and how the storage should have done. Some of them, like VMware and Hyper-V would like to have external and shared storage, like some NAS or iSCSI device. Xen can use build-in storage on servers and make fail-over work via TCP/IP raid-1?

Now I'm asking You dear community, what software You would recommend me to use?

Some things that it should be able to do:
Clustering via network.
Host Linux/Windows clients.
Have decent fail-over protection. 
Have decent client side GUI to edit and create virtual machines. 

The ones I have been thinking are VMware EXSi and Xen. I also thought about Hyper-V but it has proven to be worse choice than VMware. I'm still not sure about Xen and it abilites, but if someone from the community could help me :)

---

