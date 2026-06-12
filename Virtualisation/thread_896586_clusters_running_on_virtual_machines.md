---
title: "clusters running on virtual machines"
date: 2008-08-21
forum: Virtualisation
---

### Post by sinaalabi on 2008-08-21
Please can anyone help me... I have four computers running window xp and vmware workstations 6.0, I want to have a cluster running on the virtual machines using cilk or mpich... 

I installed ubuntu 8.04 as the guest OS on the computers and used bridged networking. After the installation nothing seems to work, I cant install vmware tools successfully, networking my virtual machines seems to be impossible and installing mpich or cilk is difficult and immpossible...
Please I need directions and codes on how to go about these task.

---

### Post by KatBuntu on 2008-08-21
I suppose you want to virtualize a cluster for settings and testing purposes. I also installed a virtual cluster but it is running, rockscluster distro, i'm using a vmware-workstation virtualization platform, to connect the nodes with the frontend i used host-only networking. In rockscluster you also have the message passing mpi, and all those cluster stuff, mpich, sge, condor, etc etc. I use my virtual cluster just for testing settings.

---

### Post by sinaalabi on 2008-08-22
Thank you, I have got my virtual machines connected to one another but installing mpich on my guest OS (ubuntu 8.04 desktop) is giving me errors, please do any one know commands that will work for my installation. I am using the cluster for testing purposes

---

