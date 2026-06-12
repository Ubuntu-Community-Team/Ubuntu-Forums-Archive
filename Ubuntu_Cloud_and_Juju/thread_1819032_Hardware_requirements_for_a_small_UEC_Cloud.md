---
title: "Hardware requirements for a small UEC Cloud"
date: 2011-08-05
forum: Ubuntu Cloud and Juju
---

### Post by itfreaksnet on 2011-08-05
Hi there,

I'm in a phase of picking cloud solution. One choice so far preferred is OnApp solution. I'm also considering UEC as another options. 

Hardware that I have is suitable for OnApp. It's the following:

2 Nodes with this conf:
six core AMD 
16 GB RAM
32 GB SSD drive
3 NICs

1 Control Panel with this conf:
Dual core intel
4 GB RAM
cca 1 TB of storage
3 NICs

Iscsi RS810+ storage with 4 TB raw capacity
2x1 1 GB NIC

as I read in technical white paper, node controller also needs around 200 GB of space to run VMs. That can be arranged.

So what concerns me is following:
1) can UEC use iSCSI for sharing EBS volumes between nodes
2) can I shut down i start again instances not just terminate them
3) will follow ...

Thanks in advance for feedback, hope will get some.

---

### Post by kim0 on 2011-08-06
Hi,
I don't think UEC is related to OnApp, so here is probably not the best place to ask for onapp support. Ubuntu is building "Ubuntu Cloud" the next generation official Ubuntu cloud solution based on the openstack project. This will be supported in 12.04 LTS release, so you may want to start experimenting with that

---

### Post by itfreaksnet on 2011-08-06
> **kim0 said:**
> Hi,
I don't think UEC is related to OnApp, so here is probably not the best place to ask for onapp support. Ubuntu is building "Ubuntu Cloud" the next generation official Ubuntu cloud solution based on the openstack project. This will be supported in 12.04 LTS release, so you may want to start experimenting with that

Hi Kim, I was not asking for OnApp support. They've got 24/7 support. I'm thinking of using current version of UEC with Eucalyptus instead of OnApp. Questions are still the same.

best regards

---

### Post by itfreaksnet on 2011-08-06
> **kim0 said:**
> Hi,
I don't think UEC is related to OnApp, so here is probably not the best place to ask for onapp support. Ubuntu is building "Ubuntu Cloud" the next generation official Ubuntu cloud solution based on the openstack project. This will be supported in 12.04 LTS release, so you may want to start experimenting with that

thanks for openstack tip, reading it right now :P

---

### Post by kim0 on 2011-08-08
AFAIK, iscsi cannot be shared between multiple machines. This is independant of UEC! The second point, UEC does not have EBS based instances, so if you stop an instance it terminates and disappears. Eucalyptus v3 I hear is adding EBS instances, but I'm not so sure of that

---

