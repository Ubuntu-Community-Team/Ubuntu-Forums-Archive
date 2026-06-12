---
title: "virtual machines configuration: help with drbd+ha+???"
date: 2009-12-06
forum: Server Platforms
---

### Post by senor_smile on 2009-12-06
I am looking to change things around a bit at my office.  We are finally ready to adopt some more FOSS solutions, but I'm a little unsure which one would suit my needs the best.  Here's what the set up and what I need:

Two virtual machines-
    -(1) running windows 2003 that has AD and the main file share
    -(1) running windows 2008 that has MS SQL and a few other programs that tie into MS SQL.  

My office is in a flood valley which is affected by a river that has a greater than 30% chance of flooding this winter.  We would like the ability to have the live servers duplicated across the city over the internet.  What we need is at a minimum a server running as the virtual machine host with both 2003 & 2008 servers going.  We then need another server offsite, around 10-20 miles away, that is syncing live the images/partitions of these two VM's so that in the instance that the first server goes down, the VM's can be started from the remote location and we can be live again.  

I have looked into proxmox, xenserver, vmware, but none of them seem to be able to do exactly what I need to do.  It looks like we might need at least three to four servers to accomplish what we actually want to do.

---

### Post by kkcv on 2009-12-09
I'm looking for a similar solution.
I've been playing with drbd and ha myself.
My theory (this is only a theory) is drbd and using sun virtual box to run the vms and store them on LVM that is synced with drbd.
Google drbd+xen to give you some info on configuring drbd.  
I'm pretty new myself and looking for info so please let me know how you decide to go.
 
I will tell you that Double Take and other commercial solutions are out there for what you are looking to do and there are also appliances with similar solutions.

---

### Post by senor_smile on 2009-12-09
So, here's what I have found so far: 

[http://www.asplund.nu/xencluster/xen-cluster-howto.html](http://www.asplund.nu/xencluster/xen-cluster-howto.html)

That seems to be a fairly straight forward tutorial.  


I have read everywhere that DRBD over wan(the internet) causes corruption.  Linbit, the makers of DRBD, have something called DRBD proxy, which is apparently supposed to solve this problem.  It costs some unknown amount.  I wasn't able to see anywhere on their website an actual price.  I assume you have to contact them to get a quote.  An alternative to drbd proxy that was reliable yet open source would be great!

Another concern is disk access times.  I don't want the vm's to have their hard drives as images, but to have direct access to the hard drives.  

I am not sure if [using LVM to give a VM disk access with the "partition" being formatted as NTFS] allows the volume to have snapshots taken and then be synchronized.  If I could do that, I wouldn't have to worry about drbd offsite, I could just rsync the snapshot volumes offsite.  Any suggestions on if these things are even possible?

---

