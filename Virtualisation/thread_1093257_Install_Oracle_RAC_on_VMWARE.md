---
title: "Install Oracle RAC on VMWARE"
date: 2009-03-11
forum: Virtualisation
---

### Post by lucotuslim on 2009-03-11
I tried to install Oracle RAC using VMWARE using this guideline [http://startoracle.com/2007/09/30/so-you-want-to-play-with-oracle-11gs-rac-heres-how/](http://startoracle.com/2007/09/30/so-you-want-to-play-with-oracle-11gs-rac-heres-how/) 

But when I about to install Oracle database software, it will fail at Remote Operation cause one of the Virtual Machine will fail.

I manually scp the Oracle Software from Machine 1 to Machine 2, I noticed that I will also cause one of the Virtual Machine to fail (automatic power off).

Has anyone encounter the same problem ?

---

### Post by in5urg3n7 on 2009-03-12
OP,

I followed this [one]("http://oracle-base.com/articles/10g/OracleDB10gR2RACInstallationOnCentos4UsingVMware.php") when installing RAC on VMWare. Basically, you need to have ssh connectivity (no password prompts) between the virtual nodes. You should also install the clusterware from one node and during the install, Oracle will install the software to the other nodes automatically.

hth,

---

### Post by lucotuslim on 2009-03-12
Thanks, I will it over the weekend and let you know the results. Thanks.

---

### Post by lucotuslim on 2009-03-18
:D 
Hi , I finally managed to run RAC using VMWARE, I install the software on one cluster first. Then use addNodes.sh to install on the other cluster.

---

### Post by in5urg3n7 on 2009-03-20
OP, that would work as well. Keep exploring your RAC.

---

### Post by tedchyn on 2010-01-05
what os did you use red hat or ubunto ?

---

### Post by lucotuslim on 2010-01-05
I am using ubuntu.

---

### Post by tluo on 2011-01-03
[http://oracleabc.com/b/archives/2534]("http://oracleabc.com/b/archives/2534")

I just installed Oracle 11g R1 RAC on Ubuntu with 2 Virtualbox VMs of both CentOS and Oracle Enterprise Linux

VMs kept crashing when I had 2 VMs running the same host. I had to run two VMs on two machines.
If your VM host has enough RAM, you may want to increase the RAM of each VM.

---

