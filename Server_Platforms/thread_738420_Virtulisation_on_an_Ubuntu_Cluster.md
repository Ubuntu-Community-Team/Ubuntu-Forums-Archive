---
title: "Virtulisation on an Ubuntu Cluster?"
date: 2008-03-28
forum: Server Platforms
---

### Post by sitedesign on 2008-03-28
I have 5 servers setup in a rack at a data centre. We are installing more at a rate of 1 per month.

I have noticed that some of the servers get heavy use whilst others hardly get touched.

They are all Ubuntu servers. So I looked at server consolidation using VMWare solution until I got the quote for the software licenses (£12,000) using the enterprise systems and the management system.

So then I wondered if it would be easy enough and cheaper to set-up a cluster (so all the servers appear as one system) with the servers then run Virtual machines on the cluster (probably using Xen or free software etc), that way the CPU and RAM resources of the cluster could be shared and allocated as required amongst the VM's.

I would also probably look at building one of the servers into a SAN/NAS with iSCSI suing freenas ([www.freenas.org](www.freenas.org)) for the cluster to use. So each server only uses the internal drive for booting then the VM's are located on the SAN.

Am I on the right track with this?

Has anyone got some pointers for me?

Any help would be greatly appreciated.


Regards Peter King

---

### Post by PilotJLR on 2008-03-28
Virtualization (be it vmware, xen, etc) does not do this... you are talking about parallel computing, which is most definitely not a simple thing.

VMware, Xen, etc do make "resource pools." But a VM can live on only one physical machine at once. Sure, it can move from box to box... but it will never consume resources from more than one physical box at a time.

Xen is a great solution for you, but it's less user-friendly than VMware Infrastructure. So do a pilot of it, get used to using it, and it should work well. Just keep in mind that any server that is at max load now will only be worse after a switch to Xen, since you will NOT be using resources from one than one physical host per VM at any given time.

---

### Post by sitedesign on 2008-03-28
According to VMWare their ESX system is designed for this purpose, they say that it is for server consolidation.

I have read that Apple servers can do similar thing (Using Bonjour I think) that they offload processes to other servers which are not under so much load.

Are there any other ways to do what I described about the servers.

---

### Post by stroyan on 2008-03-28
What jobs are the servers performing?
How is the work distributed to particular servers?
Virtualization may help to make it easier to move configured applications from
one server to another.  But the most basic question is how you recognize
an uneven loading and rebalance loads.  That is often done more dynamically
by spreading jobs around rather than manually relocating virtual machine images.

---

### Post by PilotJLR on 2008-03-28
> **sitedesign said:**
> According to VMWare their ESX system is designed for this purpose, they say that it is for server consolidation.

I have read that Apple servers can do similar thing (Using Bonjour I think) that they offload processes to other servers which are not under so much load.

Are there any other ways to do what I described about the servers.

No, this is flat out wrong. I have been on ESX and VI3 since VI3 came out, so I am telling you first hand.

It's common to misunderstand what DRS and "load balancing" means in VMware parlance. My original post regarding a VM living on one host at a time is correct - read the Resource Mgmt documentation for the proof:
[http://www.vmware.com/pdf/vi3_35/esx_3/r35/vi3_35_25_resource_mgmt.pdf](http://www.vmware.com/pdf/vi3_35/esx_3/r35/vi3_35_25_resource_mgmt.pdf)

Unless you want to re-write all your apps for parallel processing, then running 1 VM on multiple boxes at once will  not be possible.

Buy a better server.  :-)

---

### Post by PilotJLR on 2008-03-28
Bear in mind "server consolidation" means running multiple VM's on one box.

In other words, I can P2V old Windowz machines and put them all on one modern server. That's the condolidation part.
I think your question was regarding running one over-taxed machine on multiple hosts at once... not at all the same thing.

What you CAN do with DRS is vmotiom VM's from host to host in order to best allocate resources... that is an imporant distinction.

---

### Post by mvan83 on 2008-03-31
It might be best to consolidate some of the lesser used machines as VMs running on one server. If 2 or 3 machines are hardly ever touched, virtualize them and run them on one machine. You'll just have to divide up the RAM. Data storage issues are entirely specific to your setup. I would recommend kvm assuming the servers are fairly new and have hardware-based virtualization available. The overhead should be pretty low.

---

