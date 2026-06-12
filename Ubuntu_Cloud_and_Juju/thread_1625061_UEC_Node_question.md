---
title: "UEC Node question"
date: 2010-11-18
forum: Ubuntu Cloud and Juju
---

### Post by Nix82 on 2010-11-18
Say you have 10 servers in a cloud (1 master, 9 nodes) and you're running 40 VM's within this cloud. Say a node that's running 5 VM's has a hardware failure, will those VM's be automatically moved to another node by the master? If not can that VM be moved to another node without restoring the downed node?

I'm not 100% sure on how the cloud functions in certain aspects but I assume the master keeps copies of all VM's within the cloud, am I mistaken on this?

Any input on this would be greatly appreciated.

---

### Post by I'mGeorge on 2010-11-18
you had way too much ubuntu

---

### Post by Nix82 on 2010-11-18
> **I'mGeorge said:**
> you had way too much ubuntu

That was very helpful...

---

### Post by kim0 on 2010-11-18
Hey nix82,
Clouds are a bit different than traditional servers. In clouds, virtual servers are regarded as disposable. i.e. in traditional thought, you fought very hard to avoid a server crashing (HA and clusters), while in cloud world, if a server wants to crash, it's welcome to, I can replace it within seconds!

So basically, a server (say mysql server) consists of 2 parts. The running root image, and one or more EBS volumes. Root images are volatile, while EBS volumes are persistent and they hold your precious data. To answer your specific question, once the physical node fails, all VMs on that node will fail, all VMs are stored locally on that node, so they are gone forever!! However! What you do is, you start a fresh new virtual server, through an initialization script (cloud-init, or puppet or chef, or even custom script) you install mysql, mount the persistent EBS volume with your precious data/database, and start mysql, et voila you have your mysql server back. Note that even on ec2, if an instance dies/terminates .. it's gone forever, the magic is being able to recreate it within seconds which mandates full automation and configuration management

I hope that was helpful :)

---

### Post by Nix82 on 2010-11-19
> **kim0 said:**
> Hey nix82,
Clouds are a bit different than traditional servers. In clouds, virtual servers are regarded as disposable. i.e. in traditional thought, you fought very hard to avoid a server crashing (HA and clusters), while in cloud world, if a server wants to crash, it's welcome to, I can replace it within seconds!

So basically, a server (say mysql server) consists of 2 parts. The running root image, and one or more EBS volumes. Root images are volatile, while EBS volumes are persistent and they hold your precious data. To answer your specific question, once the physical node fails, all VMs on that node will fail, all VMs are stored locally on that node, so they are gone forever!! However! What you do is, you start a fresh new virtual server, through an initialization script (cloud-init, or puppet or chef, or even custom script) you install mysql, mount the persistent EBS volume with your precious data/database, and start mysql, et voila you have your mysql server back. Note that even on ec2, if an instance dies/terminates .. it's gone forever, the magic is being able to recreate it within seconds which mandates full automation and configuration management

I hope that was helpful :)

kim0, 

That was very helpful. What I'm confused about is why your master server doesn't keep backups of the VM's running within the cloud (similar to XenServer or 3Tera AppLogic). If it in fact doesn't, are you able to make a snapshot of a VM while the VM is running? If so it should be pretty simple to create a script for backing up all VM's within the cloud.

---

### Post by kim0 on 2010-11-22
Yes it doesn't, because as mentioned your data (what matters) should live on an EBS volume, the machine itself should be disposable, that's the cloud way. So out of the box, machines are not backed up. That said, it's all KVM virtualization, so you may be able to configure that to use LVM and configure snapshots and backups on your own, but out of the box it doesn't/shouldn't and it won't be super easy. Instead I would invest my time using a configuration management system to automate deployments and change management so I don't have to worry about backups again :)

---

### Post by wardrive on 2010-11-23
Hi Nix, Hi Kim0, since you guys are talking about UEC, can I ask this question, when running an instance I always get this error.. FinishedVerify: Not enough resources (0 < 1: vm instances.Not enough resources (0 < 1: vm instances.) Am I doing something wrong? Thanks :)

---

### Post by ro8inmorgan on 2011-02-27
> **kim0 said:**
> Hey nix82,
Clouds are a bit different than traditional servers. In clouds, virtual servers are regarded as disposable. i.e. in traditional thought, you fought very hard to avoid a server crashing (HA and clusters), while in cloud world, if a server wants to crash, it's welcome to, I can replace it within seconds!

So basically, a server (say mysql server) consists of 2 parts. The running root image, and one or more EBS volumes. Root images are volatile, while EBS volumes are persistent and they hold your precious data. To answer your specific question, once the physical node fails, all VMs on that node will fail, all VMs are stored locally on that node, so they are gone forever!! However! What you do is, you start a fresh new virtual server, through an initialization script (cloud-init, or puppet or chef, or even custom script) you install mysql, mount the persistent EBS volume with your precious data/database, and start mysql, et voila you have your mysql server back. Note that even on ec2, if an instance dies/terminates .. it's gone forever, the magic is being able to recreate it within seconds which mandates full automation and configuration management

I hope that was helpful :)

Sorry for bumping such an old thread, but i'm looking into the uec myself. Your explenation is very clear, but i must say theres a little bit more to for example a database server, then installing mysql and attaching the date.. There's configurations made maybe theres some extra full text engine installed and configured etc. etc. How would one go at it? Do you need to create a init script which installs and sets up all this? This would mean that everytime you change something on the server, your init scripts needs to be changed as well :( doesn;t seem very handy to me.. 

How would you go at it?

---

### Post by Rusty au Lait on 2011-02-27
My 2¢

I just wanted to note that you can build an image exactly how you want it to work: Have a MySQL server set the way it needs to be in, let us say, an idle state, the apache server set up the same way.

Once this image is created and working the way you want it, you have the instance you launch every time there's a crash, either the VM itself or the instance that running.

Then as kim0 says
"So basically, a server (say mysql server) consists of 2 parts. The running root image, and one or more EBS volumes. Root images are volatile, while EBS volumes are persistent and they hold your precious data..."

As in any crash you can go back to the latest backup of the EBS volumes.

If your root server needs to keep updates, I would create snapshots as part of a backup routine and make that the new root image.

wardrive, check other threads, sounds like your nodes need to be reregistered.
Ciao

---

### Post by ro8inmorgan on 2011-02-28
> **Rusty au Lait said:**
> My 2¢

I just wanted to note that you can build an image exactly how you want it to work: Have a MySQL server set the way it needs to be in, let us say, an idle state, the apache server set up the same way.

Once this image is created and working the way you want it, you have the instance you launch every time there's a crash, either the VM itself or the instance that running.

Then as kim0 says
"So basically, a server (say mysql server) consists of 2 parts. The running root image, and one or more EBS volumes. Root images are volatile, while EBS volumes are persistent and they hold your precious data..."

As in any crash you can go back to the latest backup of the EBS volumes.

If your root server needs to keep updates, I would create snapshots as part of a backup routine and make that the new root image.

wardrive, check another threads, sounds like your nodes need to be reregistered.
Ciao

How can you update an image from a running instance and backup it?

---

### Post by kim0 on 2011-03-01
updating an instance, is easy just like a physical box
sudo apt-get update && sudo apt-get upgrade

for backup, create a snapshot of the ebs volume (you can use the we console to do that easily). I'd recommend stopping the instance first to get a consistent backup. Then download the backup to some other location. Google for ec2 snapshot and you'll find tons of stuff :)

---

### Post by ro8inmorgan on 2011-03-01
> **kim0 said:**
> updating an instance, is easy just like a physical box
sudo apt-get update && sudo apt-get upgrade

for backup, create a snapshot of the ebs volume (you can use the we console to do that easily). I'd recommend stopping the instance first to get a consistent backup. Then download the backup to some other location. Google for ec2 snapshot and you'll find tons of stuff :)

Thanks for your answer.

I actually ment more how to update your image, so next time you startup an instance from your image it has all the latest updates, configurations etc.

So basically how to write changes from a running instance back to your image..

---

### Post by kim0 on 2011-03-02
Perhaps this is what you're looking for (rebundling a running instance) [http://alestic.com/2009/06/ec2-ami-bundle](http://alestic.com/2009/06/ec2-ami-bundle)

However, I have to say, this wouldn't be the cloud-way of doing things. The cloud-way should be, you can always change the rootfs of the instance used (use latest released ubuntu ami), plugin an ebs volume with your data, apply your configuration on top, and that's it. i.e. you can always "manufacture" an instance from its components (image+yourdata+yourconfigs).

---

