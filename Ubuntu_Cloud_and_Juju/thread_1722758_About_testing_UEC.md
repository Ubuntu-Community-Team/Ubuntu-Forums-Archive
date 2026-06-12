---
title: "About testing UEC"
date: 2011-04-06
forum: Ubuntu Cloud and Juju
---

### Post by satimis on 2011-04-06
Hi folks,

I'm testing UEC by following the steps on "UEC CDInstall" to proceed;
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

I don't have a spare box for this testing therefore I install the Controller and Node on 2 VMs respectively on the virtual machine;

Host - Ubuntu 1010 desktop 64bit
Virtualizer - VirtualBox, Oracle
CPU - AMD Athlon x4
RAM - 8G

Controller installation went through without complaint.  However on installing the node following complaint popup```

Warning:
(Configuring eucalyptus-nc)
This hardware doesn't support virtualization acceleration.  This system's CPU does not have support for virtualization acceleration, which is strongly recommended for Eucalyptus Nodes.  Eucalyptus running on this hardware will be unaccelerated.
-> Continue

```

To my understanding the hardware virtualization has been utilized by the host.  I can't forward it to the Controller, the VM.  Finally installation was completed.  I can login the Node with the user and password on the Controller.

Now my question is "Can I proceed the testing on this virtual machine?  Please advise.  Thanks.


Today to build a new box for this testing is NOT very expensive.  I have an idea to build an AMD x6 PC with 16G RAM or even an 8-core Opteron server.  However my room is full of old PCs without much space left.

Furthermore I'm NOT clear of following steps;```

The Cloud Controller's eucalyptus user needs to have SSH access to the Walrus Controller, Cluster Controller, and Storage Controller as the eucalyptus user. 
```

I have only ONE Controller, the Cluster Controller.  Where shall I run the commands on the "target controller"?  Where is it?  What is Walrus Controller?

Shall I install additional controller/controllers on other VMs?

TIA

B.R.
satimis

---

### Post by kim0 on 2011-04-07
Hi,
For testing UEC, you need at least 2 physical machines. While the controller machine "might" work in a VM, I'm sure NC will not work. The controller machine contains multiple controller software components namely (CLC: Cloud controller, CC: Cluster Controller, Walrus: S3 like controller, Volume controller)
The NC machine is separate and is used to run VMs. The CPU of the NC machine needs to have VT extensions to be able to run kvm

---

### Post by satimis on 2011-04-07
Hi kim0,

Thanks for your advice.

I have an old AMD Athlon dual core PC with 4G RAM onboard.  I'll find a spare HD installing NC there.  The said PC supports hardware virtualization.  However the NC is running on Ubuntu 1010 server edition without GUI.  Shall I add X and then install VirtualBox there?  I haven't run KVM sometimes.  All virtual machines here are running VirtualBox.

A further question what shall I use the VMs for on testing UEC"?  Thanks.

 

> **kim0 said:**
> ... The controller machine contains multiple controller software components namely (CLC: Cloud controller, CC: Cluster Controller, Walrus: S3 like controller, Volume controller)
Whether following thread are relevant for adding CLC, Walrus etc.

* UEC
* PackageInstallSeparate
[https://help.ubuntu.com/community/UEC/PackageInstallSeparate](https://help.ubuntu.com/community/UEC/PackageInstallSeparate)

eucalyptus-cloud 
eucalyptus-cc 
eucalyptus-walrus 
eucalyptus-sc

Any further document suggested?  TIA

B.R.
satimis

---

### Post by kim0 on 2011-04-08
Hi,
No need for X nor virtualbox. Yes you should follow 
[https://help.ubuntu.com/community/UEC/PackageInstallSeparate](https://help.ubuntu.com/community/UEC/PackageInstallSeparate)
to install UEC from packages. If you would like to install a fresh Ubuntu with UEC preconfigured (recommended, but you'd have to wipe your current PCs) try this guide
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Also, I'm not really sure if UEC is the best option for you. If you're looking for a desktop virtualization solution, indeed virtualbox would be great. UEC on the other hand is designed to handle a large number of clusters (says 10 clusters, each with 10 nodes ..etc) and offer ec2 API compatibility which could be advantageous to companies looking to unify their cloud strategy with Amazon ec2. If however you're strictly a home user, then other simpler options might be more appropriate. Regards

---

### Post by satimis on 2011-04-08
> **kim0 said:**
> Hi,
No need for X nor virtualbox. Yes you should follow 
[https://help.ubuntu.com/community/UEC/PackageInstallSeparate](https://help.ubuntu.com/community/UEC/PackageInstallSeparate)
to install UEC from packages. If you would like to install a fresh Ubuntu with UEC preconfigured (recommended, but you'd have to wipe your current PCs) try this guide
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Also, I'm not really sure if UEC is the best option for you. If you're looking for a desktop virtualization solution, indeed virtualbox would be great. UEC on the other hand is designed to handle a large number of clusters (says 10 clusters, each with 10 nodes ..etc) and offer ec2 API compatibility which could be advantageous to companies looking to unify their cloud strategy with Amazon ec2. If however you're strictly a home user, then other simpler options might be more appropriate. Regards

Hi kimO,

Noted and thanks.  

I will follow above document to install other packages.  But shall I install all packages on the same UEC which is now running on a VM.  Or install each package on one VM?  I can create new VM to do the job.  But I don't have so many PCs to install each package.


My question is whether I can install other(additional) nodes on VM?  My planning is to install VirtualBox on the node(First node).  Then install VirtualBox on the node.  Afterwards install additional nodes on VMs.  Can I do it.  If each node needs a PC then I don't have so many PCs to perform this test.  Max I can add another node on a new PC, i.e. only 2 nodes for this test.  

I'm NOT going to run UEC for production.  It is only a test.

Furthermore I have some confusing on UEC.  Whether I need one PC for each cluster?  If YES I can't perform this test.


B.R.
satimis

---

### Post by kim0 on 2011-04-08
You can run a UEC Cloud using no less than 2 physical PCs
PC1 running CLC+CC+Walrus+Volume
PC2 running NC (which runs VMs)

---

### Post by satimis on 2011-04-08
Hi

Please advise

> **kim0 said:**
> You can run a UEC Cloud using no less than 2 physical PCs
PC1 running CLC+CC+Walrus+Volume

1)
Shall I install all CLC+CC+Walrus+Volume on the same OS?  Or each of them needs to run on separate OS?

2)
Can run CLC+CC+Walrus+Volume on VM of PC1?


> 
PC2 running NC (which runs VMs)

I'll install NC on PC2.  Then I'll add VirtualBox running the OS of NC as host.  

Can I add further nodes on the VM?  OR each node need a PC?

TIA

B.R.
satimis

---

### Post by kim0 on 2011-04-11
Man, check my previous reply. I already answered that. You need 2 physical PCs. I suggest following this guide
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

### Post by satimis on 2011-04-11
> **kim0 said:**
> Man, check my previous reply. I already answered that. You need 2 physical PCs. I suggest following this guide
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Hi kim0,

I noted your previous answer that it needs at least 2 physical PCs for testing UEC.  I'm ready to go.

PC1 (a virtual machine) - CC already installed on a VM
PC2 - for installing the Node

I wonder whether I can add another(addition) node on PC2 running on a VM, instead of installing the new/addition node on PC3 (another PC)?

Yes, I was/am following the link mentioned on your late posting.  Thanks

B.R.
satimis

---

### Post by kim0 on 2011-04-12
Just to be clear .. Physical machine means it is NOT a virtual machine, rather a computer made of iron (not software emulating a PC)

---

