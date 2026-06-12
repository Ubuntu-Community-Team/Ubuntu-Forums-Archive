---
title: "Share the same disk on 2 machines"
date: 2008-02-21
forum: Server Platforms
---

### Post by Alekc on 2008-02-21
Hi, 

In my current situation i need to set up 2 Apache Servers which will be using the same scsi storage (probably HP msa500).

Apache servers will fetch data from the same source (load balancing), which file system should i use? 

Currently i've looked into Gfs, Gpfs, Ocfs2 unfortunatly there is a huge lack of documentation on the internet. 

Ideas?

Btw i use Ubuntu 6.06LTS which will be upgraded only in april for the 8.04lts.

Thx in advance.

---

### Post by faulkes on 2008-02-21
> **Alekc said:**
> Hi, 

In my current situation i need to set up 2 Apache Servers which will be using the same scsi storage (probably HP msa500).

Apache servers will fetch data from the same source (load balancing), which file system should i use? 

Currently i've looked into Gfs, Gpfs, Ocfs2 unfortunatly there is a huge lack of documentation on the internet. 

Ideas?

Btw i use Ubuntu 6.06LTS which will be upgraded only in april for the 8.04lts.

Thx in advance.

There are several options you could choose.

NFS 
Samba

That isn't an entire list but they are two of the more common ways to
do what you are thinking about.

Faulkes

---

### Post by Alekc on 2008-02-21
> **faulkes said:**
> There are several options you could choose.

NFS 
Samba

That isn't an entire list but they are two of the more common ways to
do what you are thinking about.

Faulkes

Probably i was not clear enough.Raid over storage is connected _physically _ to both servers by using scsi cables, and samba is not filesystem (and Nfs is _Network_ file system). 

I'm looking something which permit to use the same block data from different sources at the same time without risk of collisions (so ext3 is out of option because it permits shared access in "read only mode").

---

### Post by faulkes on 2008-02-21
> **Alekc said:**
> Probably i was not clear enough.Raid over storage is connected _physically _ to both servers by using scsi cables, and samba is not filesystem (and Nfs is _Network_ file system).

True, Samba isn't a filesystem but it can share a mounted volumes across
multiple machines.

> 
I'm looking something which permit to use the same block data from different sources at the same time without risk of collisions (so ext3 is out of option because it permits shared access in "read only mode").


IIRC 8.04 will have iSCSI functionality.  I believe it is currently in the
latest alpha as a boot option addition.

Alternatively and I'm not aware of this being supported by ubuntu there
is fibre channel over ethernet available at [http://www.open-fcoe.org/](http://www.open-fcoe.org/)

Faulkes

---

### Post by astrotech226 on 2008-02-21
I've tried this with Gfs, Gfs2 and Ocfs2.  The only one I could get to actually work was Ocfs2.  I quit using it after a few months because the servers would lock up and do other weird things.  But I found it to be the easiest to set up.

---

### Post by Alekc on 2008-02-22
> **astrotech226 said:**
> I've tried this with Gfs, Gfs2 and Ocfs2.  The only one I could get to actually work was Ocfs2.  I quit using it after a few months because the servers would lock up and do other weird things.  But I found it to be the easiest to set up.

Thx for the tip, by any case do you have any tutorial on installing ocfs2 under ubuntu?

---

### Post by syadnom on 2008-06-15
Thought I'd chime in here. (edit: this got a little long and veered off-topic but i'll post it anyway in case it helps anyone)

GFS2 is probably your simplest bet.  I would guess that your ocfs problems are from2 things.  
1)ocfs is not a good general purpose filesystem.  it is best for oracle databases. 
2)you probably had a lot of locking issues

with gfs2, you just need to create your filesystem with the locking method you want to use (lock_dlm) and configure dlm so that you can have consistant locking on the filesystem.  other things to consider is the maximum number of nodes you will connect as this will effect the number of journals should create.  other than that, you can just mount the gfs filesystems up just like any other filesystem (mount /dev/sdd2 /mnt/apachestorage) or something like that.

I currently have an ATA-over-Ethernet setup that serves out LVM volumes.  I have a few of these volumes formatted gfs2 and they hold my apt cache for 7.10 and now 8.04, yum cache for my centos5 machines, common spool directories, and common script directories.

I am running a XEN cluster using convirt to manage the VMs and AoE to provide consistant storage for live migration and quick deployment.  I also configure many of my VMs to have 1 private filesystem(i like ext3) and also access to my gfs2 filesystems.  

the dom0 on each node does all of the AoE work and I have AoE split up with 1 shelf per SAN and /dev/etherd/ has e0.x, e1.x, e2.0 with the 1,2,3,etc representing each SAN.  I get 90%-wire speeds with this setup.  I have some smaller nodes that are using 100MB ethernet at I get 11.25MB/s on that on gfs2 formatted volumes with hdparm -Tt /dev/disk and 108MB/s on gigabit nodes(with an intel nic, less with a broadcom, maybe 92MB/s).  

the SANs are just a linux machine(ubuntu 7.10) using vblade with a 6 disk SATA md raid5 with LVM sitting on top of that and vblade serving up AoE on the LVs.

I was running an older retired server but had to move up to a modern machine to get SATA controllers on PCI-E as I was having trouble with PCI bandwidth and gigabit.  only have 132MB/s available and had to share that with SATA and gigabit, giving only 66MB/s to each, limiting me to ~50MB/s!  Also needed some intel V/T tech for virtualization!

I have 3 SAN devices, and 6 XEN servers which consolidates 28 servers onto down to 9, with live migration capabilities!  I admit that I do not need 28 servers but with the ease of live migration I have network accelerators running on each server to share load, and on-line backups of a number of services.   

I am now on a fairly modern cluster also, all machines are at least an opteron 2GHz or Core2 Duo 2.4Ghz or higher though I do have some lesser machines that are technically part of the cluster but are not 'active services' on my network so I dont count them.  XEN runs quite will on these old P4 era Xeon systems but they dont have V/T so I can only run paravirtualization enables OSs like linux.

excuse the long winded post here.  I'd also like to say that this is an incredibly easy system to maintain.  just a few file servers(SANs) that I can do most of my work on with webmin(LVM stuff) and add a line to a shell script-turned-daemon to keep vblade up, a quick install and setup script to take a bare bones ubuntu server install up to a XEN node and convirt to handle all the vms. and yes, tell you friends that live vm migration rocks!

all of this is done with 100% genuine OSS.  This network rivals and often exceeds what can be done with very very expensive commercial offerings!

---

### Post by Victormd on 2008-06-15
Very informative and thorough, but did you notice this was a 4 month old thread? :)

---

### Post by syadnom on 2008-06-15
ha! no I didn't.  sorry for the thread resurection.

---

