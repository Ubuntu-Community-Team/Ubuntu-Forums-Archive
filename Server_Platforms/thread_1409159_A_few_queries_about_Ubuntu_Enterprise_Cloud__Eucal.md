---
title: "A few queries about Ubuntu Enterprise Cloud / Eucalyptus"
date: 2010-02-17
forum: Server Platforms
---

### Post by john-boy on 2010-02-17
I have now set-up a private UEC with one controller and one node as a bit of a test and learning exercise. I have overcome a few problems along the way and gained a better understanding of the technology as a result. But one of the things I have found is that the resources for learning about UEC seem rather limited. The Ubuntu [white papers]("http://www.ubuntu.com/system/files/UbuntuEnterpriseCloudWP-Architecture-20090820.pdf") and [datasheets]("http://www.ubuntu.com/system/files/UEC_Brochure.pdf") are written at a good high level but the ['how to]("http://www.ubuntu.com/cloud/private")' resources are not so detailed once you get past the installation and initial configuration.

Perhaps I should be looking elsewhere, in which case please correct me, but I have a few miscellaneous questions I was hoping someone could shed some light on.   

Is it possible to take snapshots of running instances of virtual machines? I am familiar with VMWare solutions and mean a snapshot in the sense that I can rollback to the state the virtual machine was in when the snapshot was taken.

I understand the term 'bucket' to mean a container used to store and organise data. Is this an accurate understanding and do users of the cloud have their own buckets that are private from other users? How do they access them?

What happens when a node running instances of virtual machines goes offline and is there a difference if the outage is planned and if the outage is unexpected?

What exactly is elastic in UEC? Can a virtual machine running on one node take advantage of the computing resources on another node if it requires?

---

### Post by FiReSTaRT on 2010-04-26
I'd like to go a step beyond and see what UEC brings to the office drone using its resources. From what I understand, one can run packages and use the cloud storage, but I would like to see a proper implementation of that. Everything that my quite extensive googling has brought so far couldn't be any more vague. A solid cookbook for a test case would be a great resource.

---

### Post by kiranmurari on 2010-04-27
Hi,

Please check if the following links might be of some help.

[http://kiranmurari.wordpress.com/2010/04/19/introduction-to-uec-and-its-components/](http://kiranmurari.wordpress.com/2010/04/19/introduction-to-uec-and-its-components/)
[http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec/](http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec/)
[http://kiranmurari.wordpress.com/2010/03/29/uec-bundling-windows-image/](http://kiranmurari.wordpress.com/2010/03/29/uec-bundling-windows-image/)
[http://kiranmurari.wordpress.com/2010/03/26/attach-ebs-volume-to-a-running-instance/](http://kiranmurari.wordpress.com/2010/03/26/attach-ebs-volume-to-a-running-instance/)
[http://kiranmurari.wordpress.com/2010/04/27/uec-storage-management/](http://kiranmurari.wordpress.com/2010/04/27/uec-storage-management/)

---

