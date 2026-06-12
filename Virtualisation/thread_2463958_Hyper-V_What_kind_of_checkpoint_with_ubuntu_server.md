---
title: "Hyper-V: What kind of checkpoint with ubuntu server vm"
date: 2021-06-22
forum: Virtualisation
---

### Post by kathrin-huber on 2021-06-22
Hi,

for a long time I user Hyper-V (Windows Server 2012) with Ubuntu VMs.
Now I have a new Server (Windows 2019) which distinguishes between standard and production checkpoints. 
What kind of checkpoints does Ubuntu (20.04 and 18.04) support and do I need to install anything to support this?
Is there anyone who has experience with Ubuntu VMs and Production checkpoints?

Thank you,

---

### Post by MAFoElffen on 2021-06-22
> **kathrin-huber said:**
> ...for a long time I user Hyper-V (Windows Server 2012) with Ubuntu VMs.
Now I have a new Server (Windows 2019) which distinguishes between standard and production checkpoints. 
What kind of checkpoints does Ubuntu (20.04 and 18.04) support and do I need to install anything to support this?
Is there anyone who has experience with Ubuntu VMs and Production checkpoints?
Well.. I think you are talking about a lot of technologies and strategies...

What you are talking about with two types of checkpoints started in Hyper-V in Win Server 2016. In Hyper-V in Win Server 2016, 2019 and 2022... The difference in standard and production checkpoints is that standard checkpoints (aka snapshots) are the traditional "this is what was when" there at a specific point of time, with it's state, data and hardware configuration. The production checkpoint is new, and uses "the backup technology within the guest" to make a checkpoint.

Production Checkpoints, in the new Doc's say's
> *"Only Production Checkpoints are supported on guests that run Active Directory Domain Services role (Domain Controller) or Active Directory Lightweight Directory Services role."*

They imply that the server is their own branding. 

In the real, overall world, outside of MS Branding... Any Linux or UNIX Server can be a Domain Controller and/or be running LDAP, DNS and KDC services (on one server or as separate entities).
```

[SIZE=3][FONT=courier new]+------------------------------------------------+[/FONT]
[FONT=courier new]|              Active Directory                  |[/FONT]
[FONT=courier new]+-------------+----------------+-----------------+[/FONT]
[FONT=courier new]|     LDAP    |      KDS       |       DNS       |[/FONT]
[FONT=courier new]| (Identities)|(Authentication)|(Name Resolution)|[/FONT]
[FONT=courier new]+-------------+----------------+-----------------+[/FONT][/SIZE]

```
But as that relates back to your question, MS assumes it's own structure and branding is in control.... That the Linux server is joined to a MS Domain with a MS DTC and it's ADDS service in control. So for a production checkpoint to work in that infrastructure scheme, LDAP, KDC and DNS integration with ADDS, under MS and MS as DTC. The individual Linux Servers checkpoints as a Standard Checkpoints, with the connected MS DTC and ADDS server using Production checkpoints. (Production checkpoints work with their own branding). Then it roles back through the cooperative overall scheme. All those checkpoints of the major players have to be rolled back for that to work out.

Just a note. Linux and UNIX gets along well with most anything. But Win does not play well with others. It thinks, and assumes it's own branding is in charge. For it to pass control over to anything else, it has to be tricked (by replicating it's own structure and API's) into thinking the other it is joining is it's own branded Domain. But if it did that, in relation to Hyper-V production check points, that new, specific, special MS feature would not work. 

Just how I see that. Does that answer your question?

---

### Post by kathrin-huber on 2021-06-29
Thank you for your answer. I'm not sure if this answers my question as the server is not part of an active directory or anything like that. It is just a Windows host and a linux vm. My first ubuntu vm I installed on it runs a wekan with mongo-db on it. The other linux vms will host other web services like apache+mysql, etherpad, gitlab, apache+tomcat and so on. Do you suggest to switch to standard checkpoints then? To me - not having much idea of checkpoints - it sounded that production checkpoints work better with databases but I'm not sure what is more stable with linux hosts. 

Thank you

---

### Post by CharlesA on 2021-06-29
> **kathrin-huber said:**
> Thank you for your answer. I'm not sure if this answers my question as the server is not part of an active directory or anything like that. It is just a Windows host and a linux vm. My first ubuntu vm I installed on it runs a wekan with mongo-db on it. The other linux vms will host other web services like apache+mysql, etherpad, gitlab, apache+tomcat and so on. Do you suggest to switch to standard checkpoints then? To me - not having much idea of checkpoints - it sounded that production checkpoints work better with databases but I'm not sure what is more stable with linux hosts. 

Thank you

The default is to use production checkpoints on the newer versions of Windows.

I found a pretty good explanation on how this works here (basically production checkpoints rely on VSS to ensure no data is lost, but not everything supports VSS):
[https://www.altaro.com/hyper-v/standard-production-checkpoints-hyper-v/](https://www.altaro.com/hyper-v/standard-production-checkpoints-hyper-v/)

Please note: Snapshots/Checkpoints are not backups.

---

### Post by MAFoElffen on 2021-06-29
@CharlesA

But, for example, from that article...
> What are the Characteristics of Production Checkpoints?
[LEFT]Start with the initial &#8220;What are  Checkpoints&#8221; section. Everything there applies to production  checkpoints. Unlike standard checkpoints, production checkpoints do not  capture anything else. Instead, they trigger VSS in the guest. Any  application operating within that has registered a VSS writer will then  carry out whatever operations the writer is designed to perform. For  example, Microsoft Exchange will commit its logs to the store. Windows  will also stop in-flight I/Os from occurring and flush file system  queues.[/LEFT]
 
Linux and UNIX do not have VSS, so doing a production checkpoint on a Linux or UNIX guest does nothing but takes a snapshot while not triggering any commits and loosing the state.

I've been in Sys Admin discussions on what is equivalent to VSS in Linux and UNIX... Something I held back from answering... Using LVM to take snapshots. It's not the same, but is another layer of fallback.

As you said, even that is not a replacement for Backups.

---

### Post by CharlesA on 2021-06-29
> **MAFoElffen said:**
> 
Linux and UNIX do not have VSS, so doing a production checkpoint on a Linux or UNIX guest does nothing but takes a snapshot while not triggering any commits and loosing the state.

I've been in Sys Admin discussions on what is equivalent to VSS in Linux and UNIX... Something I held back from answering... Using LVM to take snapshots. It's not the same, but is another layer of fallback.


I've seen that behavior in production too and it's part of the reason I will shut down a Linux VM before taking a snapshot.

---

### Post by MAFoElffen on 2021-06-29
@CharlesA.: Agreed, Me also. Just to ensure that the commits where done when the snapshot is taken. I'm very paranoid about that... But some systems, the priority is  on uptime and availability. (so scheduled during maintenance) 

As disaster recovery policies, it's a balance figuring out what actually happens while you are doing things, and how to get back to that point. especially when databases are involved.

---

### Post by TheFu on 2021-06-29
No clue about Windows. Haven't used or even logged into a Windows Server since 2008.

btrfs, lvm and zfs all support block level freezing - that's a "snapshot" in the historical terms used for decades.  There are other implementations which don't freeze blocks, rather they create a new overlay filesystem where all new writes get written.  Functionally, it is the same.  qcow, qcow2 and other VM data files support this method - so vdi, vdkm, etc.

Volume manager snapshots have been around for decades.  It made Veritas Volume Manager the must-have addon for almost every Unix, until each Unix vendor decided to either buy a license to be included in all their servers (and rebrand it) or the vendor created their own implementation.  Veritas Volume Manager and Veritas File System where usually paired together.  They were quite handy to get a backup of huge DBs while the DB kept running full speed.  That's still the "killer app" for these snapshots, though VM snapshots used by QA teams would disagree.  I wasn't a real sys admin during those times, so my direct knowledge is limited.

In 20.04, the ZFS experimental support appears to create a snapshot whenever a package upgrade happens.  I saw that for only a few hours on a fresh 20.04 system about a year ago.  Confirmed by this article: [https://arstechnica.com/gadgets/2020/03/ubuntu-20-04s-zsys-adds-zfs-snapshots-to-package-management/](https://arstechnica.com/gadgets/2020/03/ubuntu-20-04s-zsys-adds-zfs-snapshots-to-package-management/)

---

### Post by kathrin-huber on 2021-06-30
> 
Linux and UNIX do not have VSS, so doing a production checkpoint on a  Linux or UNIX guest does nothing but takes a snapshot while not  triggering any commits and loosing the state.

Thank you, that was what I was woundering about.

With the standard snapshots which I use for many years now, I din't have any bad experiences yet. At the beginning I did also shut down the linux machines but now I do it without shutting down for years. 
The only problems I ever experienced with the combination Windows Hyper-V + ubuntu where destroy of the file system of the vm when shutting down the host and one (Windows) vm took too long to shut down. I still have no real idea what  exactly happened there. Anyway, in that case, the snapshot I took before the shutdown was a perfect backup for me. 

Of course I have an alternative Backup strategy but I use snapshots e.g. before updates or changes I want to "test".

---

### Post by kathrin-huber on 2021-06-30
Okay, I just wanted to change the configuration of the vm but there is written: 
 (*) - production checkpoint
   [x] create standard checkpoints if the guest does not support creation of production checkpoints

so this sounds to me as if either ubuntu supports production checkpoints or the checkpoints are standard checkpoints no matter what I configured. ;-) 
I feel really confused about that.

---

### Post by TheFu on 2021-06-30
Snapshots are not backups.  They are frozen points in time, but on the same storage, so a disk failure takes the snapshot with it.
Snapshots quiesce specific blocks and provide a name for those blocks so they can be mounted (read-only) and a perfect backup can be made while the system keeps running full speed.

Since we are all pros here, we need to ensure that lurkers in 2-5 yrs don't get confused.  Even a "backup" on other storage really isn't a backup until it is verified as consistent and tested to ensure it can actually be restored.  Nobody does these things, but we all should validate (or have a backup validation tool) check that the non-live storage isn't corrupted AND we should test a full restore at least once a year to ensure we didn't forget the egg with the chicken.  

The first 5 attempts to restore a backup will likely fail, so whenever setting up a new backup process, be prepared to test multiple times to ensure critical information is available and understood for the guy paged at 2am to do the restore while half asleep.  I've inherited some terrible restore processes and I've inherited some fantastic processes.  These days, I can restore any system here, usually in under 30 minutes, but no longer than 45 minutes.  The restored system can run on completely different CPUs, different storage architectures, with nearly completely different hardware.  If the building is a crater and the offsite backups are available, we can restore to a VPS the most business critical stuff, if needed, while we search for a replacement building to lease and order hardware.  Our backups feed into a DR plan. Fortunately, it wouldn't be the end of the world if the systems were down a day or two.  I've worked places were 1 hour of unavailable systems would kill people. Those had DR plans with live replication to alternative DCs and we'd test the failover 2x a month.  The client wasn't interested in all the testing until there was a corrupted DB at 10am one day. The client still didn't make it a priority until their bosses-bosses MADE it a priority for them.

---

### Post by MAFoElffen on 2021-06-30
LMAO... PTSD moments for me also. ](*,)](*,)](*,) 

LOL! Bravo! Well said.

The problem is too late when it occurred 8 months previous and no-one noticed... (Experience from being brought into someone else's raging bonfires)

---

### Post by kathrin-huber on 2021-07-05
okay.... it was mentioned several times that a snapshot is not a backup now ;-) - I have a backup strategy but that was not the question - the question was, what kind of snapshot I should use so I do not need a backup when I use it ;-)

---

### Post by CharlesA on 2021-07-05
> **kathrin-huber said:**
> okay.... it was mentioned several times that a snapshot is not a backup now ;-) - I have a backup strategy but that was not the question - the question was, what kind of snapshot I should use so I do not need a backup when I use it ;-)

Standard checkpoint would be ideal in this case.

---

### Post by TheFu on 2021-07-05
> **kathrin-huber said:**
> okay.... it was mentioned several times that a snapshot is not a backup now ;-) - I have a backup strategy but that was not the question - the question was, what kind of snapshot I should use so I do not need a backup when I use it ;-)

Nevermind.  The hostOS is Windows.

---

### Post by MAFoElffen on 2021-07-05
Terminology: Snapshot (Other than Windows = Checkpoint (In Windows)... Microsoft just can't use the name "Snapshot" because they lost a suit from Apple over that. Just a trivial pursuit question.

If you are taking a Checkpoint from Hyper-V of a VM Guest containing anyhting other than a Microsoft Host, use "Standard Checkpoint".

As for Checkpoint as related to backups... Please refer to Microsofts own flagship System Center Configration Manager (SCCM) Virtual Machine Manager (VMM) Documentation. From the SCCM-VMM 2019 Doc's:
```
[B]Back up and restore VMM
[/B]...

Before you start

 - [COLOR=#ff0000]Don't use checkpoints for disaster recovery. Checkpoints do not create full duplicates of the hard disk contents, nor do they copy data to a separate volume.[/COLOR]
 - [COLOR=#ff0000]You can use a checkpoint to serve as temporary backup[/COLOR], before updating an operating system on a virtual machine. This allows you to roll back the update if it has adverse effects.
 - You should use a backup application to back up and recover your data in case of catastrophic data loss. One option is System Center Data Protection Manager (DPM).
 - Data such as Remote Access Authorization (RAA) passwords and the product key can be entered when you reinstall VMM. However, some encrypted data such as Virtual Machine Roles cannot be reentered.
 - You can't back up and restore such data if you use the Data Protection application programming interface (DPAPI) for backing up VMM.
 - The data will be lost if the VMM management server fails.


Create and implement a backup plan

Basic elements of a backup plan include a list of what needs to be backed up, and an outline of what is changed frequently (and therefore need to be backed up frequently) in your environment.

```
No one besides MS has VSS or DPM... Those are specific to Microsoft and their own branding's. So for that Checkpoint to work to get back to a specific point in time (on anything other than an MS OS), you need the "State", which for your question, means a "Standard Checkpoint"... And just because you take a Checkpoint, doesn't mean it's safe.

There where tips on how that is best done via IT "best practices", but that also falls under, and is affected by what your company policies and business priorities apply. Cloud, Server Farms, Server Clusters and replication servers, although safer, do get backed up... and if "always up" is the priority, have multiple failover/fallback locations, so that can be done. That is not to change the answer you are looking for, but just additional information to it. Those apply to your own company's Disaster Recovery Plan's Risk Impact acceptance.

I have no idea what your infrastructure is. I'm just someone who has had to support Windows, Linux, UNIX, VMware, etc... Living in Datacenters, in the same infrastructure. This is at least my understanding at this specific point in time.

So yes, the simple answer to your question does seem to be: Check the box for Standard Checkpoint...

---

