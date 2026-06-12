---
title: "How to get from here to there?"
date: 2014-01-07
forum: Ubuntu Cloud and Juju
---

### Post by fingal2 on 2014-01-07
I have quite a bit of experience with Linux but I am new to the idea of setting up cloud infrastructure.  According to what I have read so far, some combination of MAAS, OpenStack and other tools should be good for my project.   The problem is that I don't see any particular instructions to get to the relatively simple things I want done.  One item is simply storage space that can by dynamically expanded. I also want to have some distributed processing power.  What I am thinking of is the ability to host virtual machines which can be backed by the whole cluster of physical machines.  Does this make sense?

In particular, the project is to support some DNA sequencing work.  The immediate problem is simply having enough storage space for our data and an environment which can access that data at a reasonable speed.  The simplest thing is the ability to open and view files with IGV (Integrated Genome Viewer) which is a JAVA application.  The files are typically about 50 to 100 GB each and we have a few hundred now but expect to have a lot more in the future.  Then the other thing is the ability to test and run a pipeline for processing the raw data.  We have a large University provided cluster to do this kind of work but it has become crowded and, at the moment, they are not giving us enough storage space within the cluster to do our work.  It would be good to be able do development and testing on our own machines before deploying to the University cluster.  So we want to see what we can put together within our own lab.  

To start with, I have a Dell Precision T7500 with 8 internal 4 TB drives.  I could just configure these as a RAID-5 but, like I said, we want dynamically expandable storage and I am expecting to add more machines.  I also want to have flexibility to do other things with the cloud in the near future.  So I install Ubuntu server with MAAS support.  Then what?  One suggestion is to use Ceph for storage.  How would I host a virtual machine?  All the stuff I get when I search the web on this topic is about incorporating virtual machines as nodes to build the cloud in the first place.  Am I missing some bit of terminology which would help distinguish what I am looking for?

---

### Post by Bashing-om on 2014-01-10
fingal2; Hi !My welcome to the forum .

This long and no reply, recon I best give ya another alternative.
Register on this ubuntu discussion forum as it directly applies to your vein of questions.
[http://discourse.ubuntu.com/](http://discourse.ubuntu.com/)

There you will find many with the knowledge that you seek.

[INDENT]I can 
[INDENT][INDENT][INDENT]pass the buck !
[/INDENT][/INDENT][/INDENT][/INDENT]

---

