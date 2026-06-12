---
title: "VMware ESXi / Shared Storage"
date: 2009-07-22
forum: Virtualisation
---

### Post by TheGameAh on 2009-07-22
Hi guys.

Once again after about a year dipping a toe into where we've gone with VMware and shared storage, trying to see if anything new has developed.

Have got a CentOS box running VMware using local storage.  I would love to get into the shared storage / ESXi game, and virtualize a lot more than I have.

However a lot of people, and I guess rightfully so, have said you should not really use solutions such as Openfiler, Freenas, in a production environment.

I've also heard mixed stories about straight Linux exported NFS.  Most say the performance is the weakest out of all the shared storage options.  Is this still the case?  Is it possible to put Debian or CentOS on a box, export an NFS share, and use it as a solid shared storage for 1-2 ESXi servers?

---

### Post by bacil on 2009-07-22
have you considered iscsi ? where you get offload engine to actual iscsi card and hence lower cpu overhead ?

---

### Post by TheGameAh on 2009-07-22
Yeah I've studied up on that.  Was kinda hoping to stick with NFS though just cause of the simplicity factor.

---

### Post by JamieMG on 2009-07-23
I agree with &#8220;bacil&#8221;, you should take a look at the iSCSI solutions like for example the StarWind Server or alike. So far so well it has been a great solution for me.

---

### Post by PilotJLR on 2009-07-24
NFS is excellent... there's nothing at all wrong with exporting an NFS datastore to ESX. Performance will, in almost every case, be bottlenecked by the storage disk subsystem (number and type of spindles).

I've used NFS exports from RHEL5 on ESX, and it has always worked well.

Note that NFS on RHEL, OpenFiler, etc, are not supported storage systems... but I'm assuming you don't want to purchase an EMC, Netapp, etc disk array.

---

### Post by TheGameAh on 2009-07-24
Yeah, a Netapp is out of the question right now.

Maybe my whole crazy ideas are out of the question, but I'd just love to implement ESXi and shared storage.  But I admit I'm afraid to put it into production.

I'm gonna go ahead and setup some stuff in the lab.  CentOS NFS with 2 ESXi servers running.  Just want to see how it works.

In my head, I'd love to have 2 NFS datastores (mirrored, one for redundancy), and just have 2-3 ESXi servers pointing at it.  We have such little data, less than one terrabyte across 5 servers.  You'd think this would be doable.  But I haven't found any success stories in the wild that didn't include Netapp, expensive SANs, etc.

I've looked at a lot of options.  EMC/Netapp - too expensive.  Iomega - not quite beefy enough (they suggest 25 or less users with their stuff).

---

### Post by PilotJLR on 2009-07-25
A pilot/lab deployment is a good idea. With the mirroring, just be sure to do block level mirroring (like DRDB), since file-level mirroring won't work... data will always be in-flight, provided VM's are running.

You won't find any published success stories of this - just forum posts. Since these homemade setups are not supposed, none of the vendors would publish such a story.

I agree that Iomega is simply not up to this task. Personally, I have a strong affinity toward EMC, though I've used Netapp and IBM and HP in production with good results as well.

---

### Post by TheGameAh on 2009-07-27
Yeah I'm kinda pulling back a little on the whole idea.  I don't think we're in any position at all to implement "proper" shared storage and ESXi.  So I'm gonna stick with the my old proven method of local storage/CentOS servers/VMWare Servers.  They are very solid.

That was another question I had, and am glad was answered, about mirroring running VMs.  Good to hear DRBD can handle it at least.  Maybe I'll implement that for my existing setup, instead of suspending/stopping VMs, and tarring.

---

### Post by redbrain on 2009-07-27
Don't worry too much about iscsi, its actually not as complicated as it sounds, and it works really well for virtulized environments. 

Because you could make an iscsi target and partition it a bit and then those partitions are now your virtual disks! And then your sorted :) + its pretty fast in my experience instead of:

VM -> Virtual disk -> format -> storage. Your going straight to disk over network. So you can host your virtual machines on any host and it makes cold/live migration work pretty good. NFS is a total no-no its far too slow. Its ok if your VM isn't going to be doing much File I/O but its still just not great.

---

### Post by PilotJLR on 2009-07-28
Now that is simply not true. NFS can push performance at least as far as iSCSI, and that's been illustrated by many vendors. Consider this Netapp fella's reasons:
[http://storagefoo.blogspot.com/2007/09/vmware-over-nfs.html](http://storagefoo.blogspot.com/2007/09/vmware-over-nfs.html)

and:
[http://www.netapp.com/go/techontap/matl/downloads/NAS-presentation.pdf](http://www.netapp.com/go/techontap/matl/downloads/NAS-presentation.pdf)


What is really important is the disk subsystem's sizing. If we're only talking about one shelf of disk on the backend, then it doesn't matter if we're looking at 4 Gb FC, 1 Gb iSCSI, or 1 Gb NFS. The bottleneck remains the disk itself, in many cases.

---

