---
title: "Clustered Cloud Storage"
date: 2010-04-12
forum: Server Platforms
---

### Post by nightmare0 on 2010-04-12
I'm attempting to use a lot of older computers to create a large unit of clustered storage with Eucalyptus and other components of it. I've read many articles pertaining to the installation and using of virtual instances in the cloud, but not much regarding the storage. I have a feeling I'm missing something somewhere. Can anyone help or point me in the right direction?


Here’s what I have running:

--Karmic Koala x86 (9.10)
3 Nodes (each have multiple hard drives which still need to be config'd and formatted too)
1 Node Controller (also with multiple hard drives)

Thanks!

PS: If you need any clarification or something just ask/add, this is my first time dealing with cloud storage/clustered storage, all help and ideas are welcomed :)

---

### Post by nightmare0 on 2010-05-07
Bump!

---

### Post by Vegan on 2010-05-07
What do you want to achieve with the cluster, except for a bigger power biil when a new machine will cost less to operate and be able to do more.

---

### Post by kingpoiuy on 2010-05-07
I'm hoping to set up the same thing, but my purpose is for redundancy. I have a friend down the street who I would like to cloud with using a VPN tunnel between our firewalls. I arrived here because I'm looking for more technical detail of the cloud server setup. Will it cause redundancy between our systems, or double our storage space, or is this configurable? If it's not redundancy then would certain files live on one server and others on the other? If that is the case then a large file being accessed would need to travel over my VPN tunnel to reach the local location in some instances.

I was hoping I could just throttle it to sync at about 10 - 20 kbps so if a hard drive crashes or an airplane hits my house I will still have my data at the remote location!

Hope I didn't hijack your thread, nightmare, but I think you have the same questions I have.

---

### Post by nightmare0 on 2010-05-08
@kingpoiuy: Not at all I do believe we are both looking at similar interests :)

This is actually somewhat of a pilot program at our school, I'm demonstrating and will hopefully succeed in convincing my Systems Administrator to begin to use cloud computing and cloud storage as the base for our network storage and also for virtual servers.

It is irrelevant that the amount of computers and the energy that it would take to run these would equal the price of a single server, that would defeat the purpose of having a cloud. I want to demonstrate, like I said before, distributed file systems and also virtual servers as in a cloud.

---

