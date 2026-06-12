---
title: "VMWare ESXi Backups"
date: 2010-07-28
forum: Server Platforms
---

### Post by bcdudley on 2010-07-28
I am planning out a new San to go with my existing VSphere ESXi servers.  It is the purchased product and not the free version. My available  features are:
    Up to 256 GB of memory
    Up to 4-way virtual SMP
    vCenter agent for ESX Server
    vStorage APIs
    VMsafe
    dvFilter

The San I plan to build will be a Dell server with:
2x Intel Xeon 5620
6Gb memory
Dell Perc H700 (Int. Raid)
Dell Perc 6/E sas 512mb (Ext. Raid)
2x 146Gb sas 15k 2.5"  (for the os)
12x 600Gb sas 2.5" 15k drives (Raid 5 for MS Sql and MS Exchange  database)
8x 2TB sata 3.5" 7.2k (Raid 5 for file storage, sitting in an external  drive shelf)
2x Intel ET 1GB Quad Nics (Bonded/Teamed for 8Gb throughput, I like  overkill, lol)
Redundant power supplies

I will be running the latest version of Ubuntu along with iSCSI  Enterprse Target Administration. I will have 3-5 VMWare ESXi servers  connecting to this as a shared datastore.

_**What is the best way to run backups?**_ I am currently using Symantec  Backup Exec 2010 and would prefer to stick with it. I don't like the  product, but it is in place and the other non-linux type admins are  familiar with it. Am I best off getting a vmware agent license and  backing up through one of the VM Hosts, do I get a linux agent and  backup the entire Linux San server, or do I get the San agent and backup  with that somehow. I would prefer to be able to run backups and restores on the VM file system as individual guest, backing up the entire Virtual server as a single folder, without having to shut down the vm, if that is possible.

I would appreciate any suggestions and especially experience about your similar setup and what you are doing.

Thanks.

---

### Post by kevinthecomputerguy on 2010-07-29
Whats the most important to you? Data integrity and "time machine" like versions of every file, or uptime?
I would say, with the paid version of VMware, aggressive snapshots would be the best.

If data is your number one concern, and you are the level 3 admin, overseeing level one admins, Then snapshots would rule. You could overcome any mistake they make.

For inside the OS backups, I like "Cobian Backup" for windows. You can install it in each Windows VM, and it supports shadowing (backing up live files)

Your setup is so very enterprise though, aggressive snapshots would be a breeze. Uptime for exchange though... thats tuff one.
-Kev

---

### Post by bcdudley on 2010-07-29
Thank you for the reply. I agree that the snapshots are great. With the  way I have my servers setup, I do not keep any data on the actual  servers. It is all stored on a nas. changes to the servers are made  infrequently, maybe a couple of times  per week in the form of an application upgrade or service pack.  I need a  way to take a snapshot, maybe only once a week, then export either the  snapshot or the entire vm to a tape for disaster recovery.

As far as the data, I currently back up all the data in a disk-disk-tape  configuration. The tapes go off-site every day and are returned 2  months later. We have a directive from the CEO to not store any backups  longer than 2 months. This setup on the data is working well and I have  no need to change it at the present. With over 8Tb of data and growing,  the only viable option I really have to full weekly backups and  incremental daily backups.

I am currently using Symantec Backup Exec. I am more than happy to look at other backup products, but I need something that is easy to use for both myself, as well as the level 1 and 2 admins. I have yet to see another product on the market that offers the completeness and ease of use that Backup Exec offers. 

The tape drive I have is a 48 tape robotic library with 2 lto 4 drives  and I can add 2 more if necessary. It is run over a 1gb iSCSI, so  bandwidth can become a problem. Also, Symantec locks the device out and  prevents other devices from connecting to it.

I really do not want to change the way I am backing up my data, only how  I backup the servers. backing them up inside the os seems inefficient  and will not provide a true disaster recovery. I am looking for a way to  be able to upload the vms from a tape and start going again in the time  it take to perform the actual restore and copy.

Thank you.

---

### Post by walkerk on 2010-07-29
Are you referring to backups of your "SAN" or of the ESXi hosts? 

I have 3 Blade Centers with a total of 18 blades/esxi hosts...

I do not back up ESXi hosts at all. No point. I run all of my VMs from two large NetApps (NFS).

---

### Post by bcdudley on 2010-07-29
I think that is the question I need to be asking. Which should I be backing up. I know there is no need to backup the actual host as it is a small cd download to reinstall. I am talking about the best way to backup the guests. All of the guests reside on a SAN connected via iSCSI to the VMWare hosts, similar to most other setups I would think. 

Do I need to backup the SAN itself as an entire server? If I do so, will I be able to restore individual VM guests, or do I need to restore the entire SAN. My concern is that the VMWare datastore is a proprietary format and I cannot read inside the datastore without going through one of the ESXi hosts.

---

### Post by kevinthecomputerguy on 2010-07-29
I use ESX4, i think you said you are at 3.5, so im not sure if the vSphere software is different. But from my vSphere software I can upload and download entire VM's. So if you have and entire backup of your SAN (which is probably the best idea) You could restore broken VM's, by uploading a backed up one. 
 
If your software is like mine, when your in the datastore, there is an upload and download button, and as long as you can browse to the SAN, or the SANs backup folder from the PC you have vSphere install on, then you can upload and replace a VM.
 
Basically just map a drive to your SAN or the SANs backup, then lauch vSphere. Ive also heard there is better software than vSphere.
 
Your very good at painting a picture of your setup, have you tried emailing vmware support? Im sure they would sell you something awesome to address your needs. Now... how your other techs will like it... well... :- )
 
-Kev

---

### Post by bcdudley on 2010-07-30
I think I found my answer by playing around with the trial version of Backup Exec 2010. If the VMWare agent is purchased, it will let you connect to the VCenter Server. From there, you can select entire VM Guests to backup. When doing the backup, it also performs a granular backup of all Active Directory, Exchange and SQL components. You have the ability to restore not only the entire VM, but individual files within the VM. 

I think that is going to work for what I need. I do appreciate all of the help provided and suggestions. 

Thank you.

---

