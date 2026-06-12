---
title: "Snapshot a running physical host"
date: 2013-03-20
forum: Server Platforms
---

### Post by RoosterHam on 2013-03-20
Late last year I began a new job. I am responsible for about 80 physical servers. There are 3 roles amongst these, the primary role, a storage role, and 2 hosts are CnC servers for all 78 hosts that spread over 3 locations.

The primary and storage roles both have an install image available for building/rebuilding them, even though all software (bar some custom scripts for administration) is opensource and available to the world. The CnC role is performed by a custom internal (closed source) set of applications, for which there are no .deb packages, source code, or system-install-image.

If one goes down, I have no way to rebuild the host. So what DR options are available? What is available to snapshot the system to allow a makeshift recovery?

I know a snapshot is less than ideal, but in this environment I don't have a great deal of options.

Also note that the servers all run hardware RAID1 arrays. One of my (terrible) ideas is, with some planned downtime, remove a drive from the array, sync the disks, then return the original disk to the array and store the freshly synced disk as a kind of snapshot.

Thanks guys.

---

### Post by TheFu on 2013-03-20
"Snapshot" usually means a specific LVM command. It can be taken on running systems.
If you are not using LVM, then a backup is the answer. There are many backup tools.  Running backups is usually not an issue unless files are open and being written - this usually only happens with databases.  That means you backup everything using normal backup methods, then take extra steps to backup a consistent DB. There are lots of ways to ensure a consistent DB backup.
* shutdown the DB while the backup is going on
* dump the db to CSV or some other format that can be backed up easily
* use a DB backup tool specific to the DB being run.

Simple.  Of course, things can be as simple or complex as you choose.  For example, I do not backup entire OSes here. I backup 
* data
* configurations and
* lists of packages installed
* any extra programs installed outside the package manager.

I know many places will not load programs unless a package has been created - PERIOD.  If it doesn't already exist, they make the package themselves. From what I understand, it isn't too difficult to do this.  I've used a tool called epkg myself, but since switching to APT, haven't needed that.

RAID1 is great for HA, but doesn't help at all for backups.  Backups are the most important thing that any admin can accomplish. The only thing more important is the restore.

This might be an opportunity to swap out custom C&C for something like Rex, Puppet, Chef, Salt, or one of these: [https://en.wikipedia.org/wiki/Comparison_of_open_source_configuration_management_software](https://en.wikipedia.org/wiki/Comparison_of_open_source_configuration_management_software)

If you really want DR, everything should be 500+ miles apart and easily able to switch over with a few DNS changes.  Depending on the RTO (how quickly the service needs to be available) and RPO (how old the data can be), there are hugely different requirements. [https://en.wikipedia.org/wiki/Disaster_recovery_plan](https://en.wikipedia.org/wiki/Disaster_recovery_plan) is a good introduction.  Everyone will say 5 minutes for both RTO and RPO, until you show management the budget necessary. Then magically, 24 hr RPO is fine.  Finding the correct solution for the criticality of the data is a merged responsibility for admin, process owner and the guy paying.  Where I've worked, we always asked for per-hour-of-outage costs.  When someone sees a system is estimated at $8M/hr, funding a $10M DR solution becomes easier.  If the budget doesn't let a solution be deployed that meets RTO/RPO requirements, that is a good hint to pass the buck to a corporate officer and let him/her accept the risks - IN WRITING.  Don't let them claim "nobody told me." Delivering bad news is part of being a professional.

BTW, using virtualization can really help with disaster recovery - virtual hardware is much easier to match than physical hardware. ;)

Feel free to ask more questions, however, more specifics about your setup - amount of data, which DB is used, any allowed downtime, current backup methods ... etc ... would be very helpful.

---

### Post by koenn on 2013-03-20
Yep. what TheFU says.

On the short term, a decent backup and restore procedure with a reasonable short  RPO and RTO  will buy you some peace of mind.
Virtualization is definitely something to consider, if only because it will allow you to backup the entire system as is (some applications / databases may still require some special care)


On the long therm, what you describe is a death trap for the company. (presumably mission critical) software with no fallback whatsoever ? You don't need anything even close to a disaster to put you out of business - a (ordinarlily) minor human error or an (ordinarily) insignificant hardware problem will be enough.  Unless you can devise a solid backup scheme  and recovery plan (and get management to agree on RTO and RPO), moving away from that death trap application is the only good solution.

---

### Post by RoosterHam on 2013-03-20
I certainly think that more information is in order. The majority of servers receive phone calls via isdn trunks, pass the calls to a commercial pabx, and record the calls (asterisk) taking place. The raw audio files are then copied to servers with larger arrays, from where management can browse the calls with a custom applicaiton.

While I call them CnC hosts, the two hosts I'm concerned about are responsible simply for ensuring connectivity between and health of all the other hosts and for assigning file names to recorded files that follow a particular naming scheme. They do this via custom software. Drives for these systems are 70Gb. The two are in two different locations in the same city, and are load balancing when it comes to its file naming role. So I am able to bring about downtime for a couple of hours if I make my case well.

The worst thing is that these systems are very old. 2009 was when the company stopped actively developing their custom applications, and developers either left or moved up. Now, my company have the sysadmin contract, to the major company that these systems are mission critical to. From what I can gather, when development internally ended, all backup and DR ended. My company then got the contract and have been reluctant to change anything as there is a huge resistance to change at our client.

Both my company and our client seem to want to retain the separation of jurisdiction that using physical hosts in separate racks, and with aging hardware and outdated software, there is a project to replace the entire system with a commercial one this year. 

The age of the OS (2009) makes me extremely nervous about ever adding a package, or even asking whether that is allowable from our client. The custom applications seem to have been untarred from an archive rather than installed via any packaging tools, and with additional scripts all over the shop I'd lean more to shutting down and making a backup of the entire harddrive. No LVM installed.

---

### Post by tgalati4 on 2013-03-20
+1 for changing out the custom Command and Control for an open source configuration management (CFM).  You can install a development environment using [http://devstack.org](http://devstack.org).  When the proprietary C&C dies, you will have a working CFM system in place that will act as the "backup generator" to keep the other servers going.  Over time, the "backup generator" becomes the primary system.  It's all curtains and smoke.  You are just changing the the drapes and adding a little oil to the fire.

---

### Post by TheFu on 2013-03-21
> **RoosterHam said:**
> Both my company and our client seem to want to retain the separation of jurisdiction that using physical hosts in separate racks, and with aging hardware and outdated software, there is a project to replace the entire system with a commercial one this year. 

The age of the OS (2009) makes me extremely nervous about ever adding a package, or even asking whether that is allowable from our client. The custom applications seem to have been untarred from an archive rather than installed via any packaging tools, and with additional scripts all over the shop I'd lean more to shutting down and making a backup of the entire harddrive. No LVM installed.

Given the above information, I think you should just tell your management of the risks and **let them decide** whether any work should be performed.  BTW, there is nothing wrong with installing software via tar.gz ... provided the skills to manage it exist inside the company.  Without those skills, it is only backups that will remain to recover the running processes. It is just another risk.

Often in situations such as this - especially with older hardware that is not in-warranty, the best answer is to start with fresh, current, servers, virtualize everything, put in a SAN, and deploy using current best practices. Testing of the new setup can be accomplished disconnected from the old stuff while it is still in production.  I've replaced 20+ old, unwarranteed servers with 2 new boxes running many VMs each at a client.  The power and UPS costs dropped enough to pay for the new machines after a few years. Less heat, less cooling - we sold the 20K-VA APC too and put that money towards the SAN and a smaller, right-sized UPS.  That happened 5 yrs ago and the client is ready for a server refresh now.  Migrating VMs is trivial.  Having a 100% backup of VMs is also trivial. Newer servers are 2x more capable and they are considering using enterprise-class SSDs for the high-disk IO VMs.  Clearly, there are VM best-practices that need to be known, learned, and followed too.

You can build a picture that management will love. Explain how all the current risks are addressed in the new architecture.  Build out 2 locations 500 miles apart so that DR is built-in should something bad happen in 1 location.  Being able to swap primary locations weekly means that both sides never become 2nd class locations - DR will actually work AND be tested routinely.  DR plans that get tested for 72 hours every year usually fail.  DR plans that are exercised weekly usually work perfectly when the time comes.  It also means that you'll have the vital "how to fail back" problem solved too. ;)

Asterisk doesn't require much processing usually, so hosting lots of PBXes inside VMs works well, provided enough real-time access is possible.  The local Asterisks Users Group can probably help you a bunch there.  The local one here is sponsored by C/Beyond - a huge VoIP provider in the region.

For small offices that just want to run a small PBX, a $200 dual-core Atom box, completely self contained, is hard to beat. 20-50 people can easily be handed on that.

---

### Post by Vegan on 2013-03-21
With 80 servers I would look for a better management package. I have a lot of VMs for Linux as I have been testing Ubuntu rather extensively of late after identifying some problems.

For example a 64 TB worth of hard disk, it fails to format it after partitioning

---

### Post by rubylaser on 2013-03-21
> **Vegan said:**
> For example a 64 TB worth of hard disk, it fails to format it after partitioning
Using what filesystem?

---

### Post by thnewguy on 2013-03-21
I think there should be two approaches. The first is to get snapshots of both servers. Even if it's just a quick-n-dirty file system snapshot which could be provided by a tool like Clonezilla. That way you should be able to restore the OS if something happens. Basically, as others have said, make backups. The second step should be to get off that existing system into something that would be easier to replace and/or maintain.

---

### Post by Vegan on 2013-03-21
After some more testing it seems that Ubuntu does not like Hyper-V version 3 at the moment. Guess I will have to wait for the next DVD to be released and try again.

It keeps freezing at formatting / at 33% on the setup screens

---

### Post by wirelessmonkey on 2013-03-21
> **Vegan said:**
> After some more testing it seems that Ubuntu does not like Hyper-V version 3 at the moment. Guess I will have to wait for the next DVD to be released and try again.

It keeps freezing at formatting / at 33% on the setup screens


It's a Hyper-V bug. Passing the numa=no kernel parameter to grub, and turning off NUMA in Hyper-V will allow it to work.

---

### Post by RoosterHam on 2013-03-21
Thanks guys, some really useful points from all of you. I certainly think a full backup/image of the two systems is definitely required... still not sure about the appropriateness of the dd and dump tools for copying an entire system, or whether another tool such as clonezilla would be more at home.

The 2 systems I'm concerned about are candidates for VMs, and the storage servers would easily reconfigure to a small SAN. Any tips on SAN design?

---

### Post by TheFu on 2013-03-22
With Linux, you do not need an "image" - this isn't Windows.
For a "snapshot"/mirror, use rsync.
For real backups, use something like duplicity, rdiff-backup - you know - a real, efficient, backup tool.

Image-based backups for entire systems waste huge amounts of space, unless they know about the file system. With ext4, most of the image-based tools stopped being smart. If you are still on ext2 or ext3, then I **know** partimage understands the file system and will not get all the unallocated space ... but you have to bring the machine down to use those sorts of tools.  

Backup tools do not have that limitation.  They will backup open files that might be in bad states leading to corruption. I think I said this previously - that DBs are usually the only files at risk of corruption during backups - dump the DB to a text file which can be imported later, then back that up.  

If you don't really understand this stuff - start a new thread for server backup techniques to get lots-o-help.

---

### Post by TheFu on 2013-03-22
Why use hyper-v for this?  KVM or LXC will work better for Linux VMs.  Walk away from the proprietary software ... please.

SAN design can be very simple.
* SAN need its own network; never shared (vlans do not help)
* dedicated NICs in every machine for the SAN; dual if you can't have downtime
* dedicated GigE or 10GigE networking
* Fast, enterprise, drives configured in some sort of protected RAID. RAID5 is usually a bad idea for a few reasons.  
* ZFS might be a good solution - just be certain you have enough processing power.  ZFS provides iSCSI and NFS and CIFS storage. Poor performance can happen, so do your homework.

If you want/need to build your own storage server, check out the blazeback design. They have solved some interop issues.  
EMC and NetApp are very expensive, but if you need them, then you need them.  Updating a frame can really suck, so if you do go this direction, plan to buy a new frame to replace the old one every 5 or so years. Different HBA device drivers can prevent an entire frame firmware update.
AoE can be a good choice for performance - CoRAID.
iSCSI is more standardized.

I've only designed SANs, I am not hands on at work. Other, smarter people do that stuff - plus the vendors.

---

