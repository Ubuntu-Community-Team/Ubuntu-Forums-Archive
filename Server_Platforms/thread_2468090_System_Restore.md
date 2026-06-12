---
title: "System Restore"
date: 2021-10-18
forum: Server Platforms
---

### Post by sidneyki757 on 2021-10-18
Hello,

I am looking for a package that will work with the Ubuntu Server 20.04.3 LTS that will let me roll back changes done to the server.

I have broke my server several times and had to start over by wiping and installing the OS.

If there was a software that I could set the server back to when it was first setup or last known good configuration.


Also where is the best place to look for software for application for this server that are approved and tested?

Thank You

---

### Post by TheFu on 2021-10-18
Well, there are many solutions.  If you use a volume manager like ZFS or LVM, then snapshots allow this rollback.  But the snapshots use storage and prevent those blocks from being modified. Snapshot management becomes a problem.  How many snapshots you should keep is a dynamic thing, since it depends on how many changes are made.  Also, you'll want different file system areas to be part of different snapshots, since the entire snapshot point will be put back, not selectively.

For finer control over what gets put back, you'd want a versioned backup tool.  There are many of those that work fine. I use rdiff-backup daily for my automatic, versioned, backups. I keep between 90 and 180 days of versioned backup sets depending on the system and risk level. A desktop doesn't need nearly as many versions as an email gateway on the internet 24/7/366.  But an email gateway doesn't really have any data, so the backup versions are relatively tiny. 180 days for that gateway system uses 64MB of storage. That's all that is needed to restore any version during that period of time in about 20 minutes.

BTW, there is nothing like a "restore point" you may be familiar with from some other OS.  Every other OS calls that "a backup."  A few months ago, I posted a little script here that would make nearly the same thing as a system restore point for Linux.  Search for my username and "restore point" in these forums.  [https://ubuntuforums.org/showthread.php?t=2465374&p=14052519#post14052519](https://ubuntuforums.org/showthread.php?t=2465374&p=14052519#post14052519) is the post. Hope you find it helpful.

Many people use a config file tool called etc-keeper or they just use a git repo.  That is up to you.  I use git for development, but find that automatic daily backups is my preferred tool.  I also use LVM snapshots to feed into my backups.

Of course some other tools like Timeshift and back-in-time can be easier to understand.  But all of these tools, including rdiff-backup have important caveats. It is likely that you'll miss something important until you take the time and effort to actually test a restore.  Whenever I'm forced to change to a new backup solution, I plan on at least 5 test runs to ensure I didn't miss anything that would prevent a system restore.  To really test it, take your backup disk to a friend's place and try to restore it there.  Hopefully, you won't run into a chicken-egg issue, which is why I needed 5 restore tests. I'd always forgotten some critical thing.  For example, my backups were going to encrypted storage and I backed up the encryption key too. Great, right?  Well, without the key, I couldn't access the backups.  The encryption key needed to be outside the encrypted backups. ;)  Seems obvious, right?

---

### Post by sidneyki757 on 2021-10-18
TheFu,

Thank you for taking time to answering my post.  okay you caught me :) i'm a windows guy "restore point",.. ha ha ha
You provide some great advice!

I will take a look at that article. Its been a big learning curve for me using linux. I have gotten good at breaking things.
 
Thank you very much.

---

### Post by LHammonds on 2021-10-19
And if you run inside a virtual environment, you can create VM-level snapshots...which are oh-so-handy at quickly making a snapshot (or more) and the rollback to a particular snapshot.  Extremely valuable when learning Linux or testing software packages, etc.

If you want the most simple virtual environment without knowing a ton about it, you can install Oracle VirtualBox on your Windows PC and create VMs that you can play with when you want to work on them.  This is handy for a Windows guy and for a system that does not need to be online all the time.  Be sure to setup the NIC in bridged mode if you want it acting like a server with its own IP on the LAN.

If you want a more permanent always-on server, you could completely wipe a machine and install a hypervisor at the base level such as Proxmox or Vmware ESXi.   Once your hypervisor is running, you then use its controls to make one or more VMs which will share the machines resources.

LHammonds

---

### Post by sidneyki757 on 2021-10-19
LHammonds,

Do you know of any good instructions on setting up Proxmox?

Thanks

---

### Post by LHammonds on 2021-10-19
> **sidneyki757 said:**
> Do you know of any good instructions on setting up Proxmox?There is a lot of documentation out there to be found but I never found a "single source of truth" because there isn't one.  The hardware used by each person will be different and will change how the system is designed.

I [started to create a tutorial](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=276) for it but that project got put on hold due to hardware limitations I could not overcome (needed much more space than I had available using puny / unwanted desktop machines)

It wasn't hard to get a basic system running with Proxmox.  But like any complex system, it can get involved when you want to fine-tune in specific ways (pass-thru access to hardware for example)

LHammonds

---

### Post by TheFu on 2021-10-19
> **sidneyki757 said:**
> LHammonds,

Do you know of any good instructions on setting up Proxmox?

Thanks

Proxmox takes over the system completely and makes it into a VM host system.  Proxmox uses LVM for storage management and has a pretty web interface.  I've never used it, but have seen it used a few places and it does a reasonable job.  I'd pick Proxmox over ESXi.  

ESXi is very picky about hardware.  It wants real servers.  Of my 6 desktops here, only 1 had the hardware that ESXi liked enough to install.  For about half, it didn't like the SATA controller on the motherboards.  For others, it didn't like the NICs.  ESXi is from a company called VMware which has a history of charging premium prices for enterprise stuff.  They also make VMware Player (free) and VMware Workstation ($150-ish). Just as I was finishing up an ESXi deployment at a client about 10 yrs ago, VMware announced license cost changes which would cost that client 3x more.  Plus, the "cheap" backup software for ESXi was $1000. Back then, there wasn't any F/LOSS that worked at the hypervisor level. That cheap backup software only did full backups, no differential (what has changed since the last backup) backups. Anyway, we showed the price change announcement to our client and suggested moving to libvirt and KVM.  They agreed and decided that flushing the $5K in software licenses was worth it to never have to pay again.  There are good things about using VMware stuff.  Those license costs immediately remove super cheap people from consideration and if you are being paid by those same people, that is a good thing.  Also, it is fairly fast and works.  There is a huge community and because it has been around and in enterprise use for 20 yrs, nearly everything you can imagine has already been thought thru and solved.  For home lab use, ESXi is free for some small CPUs.  I think the license is based on number of cores and RAM in the system, but I've not looked since 2011-ish. I do remember that almost anything that needed software to accomplish was $1000 added to the other costs.  Want vSphere?  <---- that's their version of virt-manager, open your wallet.

Ubuntu can do the same, just with a little more manual control and setup required.  I use KVM+libvirt for the hypervisor and **virt-manager** to control my VMs.  There are other choices.  This setup also supports using LVM and snapshots, but provides more flexibility.  Of course, flexibility == choices which can be confusing for someone new.

LVM can be part of a normal Ubuntu Desktop or Server installation. It sits between the partitions and the file systems, but provides all the snapshot and other volume management things we expect from enterprise tools.  In Linux, LVM is LVM regardless of the distro. There is no GUI after the initial choice is made during the install, so be prepared to work with it from a shell only.
You can add LVM to new disks regardless of what the OS storage uses.  It wouldn't be unreasonable to have LVM on storage used for virtual machines, but not for the hostOS/hypervisor.  So, depending on your desires and the equipment you have, wiping a 2nd drive (or adding a $50 new 2nd drive) in the system, creating a GPT partition table, 1 huge partition, then putting LVM into that partition could provide a place for multiple VMs to have a shared PV, shared VG, but separate LVs.  Snapshots happen at the LV level. Just be certain to leave plenty of storage unused in the VG so the transient LVs needed for snapshots have a place to be.

LVM supports real snapshots.
ZFS and BTRFS both support real snapshots too.
and QCOW2 supports snapshots for VMs (only), but if the VM storage is backed with LVM or ZFS  (don't use BTRFS for VM storage!!!!), then we can use that for snapshots as well.

These are all huge jumps in required skills and knowledge for someone new to Linux. Beware of the steep learning curve each will require for an area of computing you've likely never worried about before.

And if it isn't clear, changing a file system requires a clean wipe, total data loss on that storage.  There are no migration tools that magically convert ext4 into LVM + ext4.  Heck, the only easy migrations are from ext2 ---> ext3 ---> ext4 - that's it.  Any other changes all begin with a "Nuke it from orbit" just after the "backup anything you don't want to lose" step.

BTW, no proper snapshot is a backup.  Snapshots just freeze storage blocks and don't allow them to change. That's it. That's why they are nearly instant.  That space is held frozen until the snapshot is removed.  Only changed data from the time the snapshot was created uses added storage, so when I'm doing backups, I'll typically create a snapshot and allow 1-10GB of new data to be changed while the backup processes pull the frozen blocks from the snapshot storage (read-only mount) to a backup server.  When that process finishes, I umount the snapshot and remove/delete the snapshot so that normal block use can occur.

There are lots of LVM tutorials on the internet.  Any from the last 15 yrs should be fine. LVM hasn't changed. Sometimes people call LVM "LVM2" ... I'm just lazy, since LVM2 was released about 20 yrs ago, it hardly seems worth mentioning. It is the same.  The main thing I would strongly suggest when using LVM is to allocate only the amount of storage to an LV for what you **Know** will be needed the next 3 months.  Smaller LVs are better than larger.  This is because extending (growing) an LV is 5 seconds of effort while the system keeps running, but reducing an LV often requires booting from an install disk into a *Try Ubuntu* environment and there are risks reducing just like there are risks in reducing a partition size.  Having lots of unused storage in the VG means we can add some where needed, as needed, relatively easy, as the system keeps running. Zero downtime.  Don't go too crazy with having too many LVs, but don't be afraid to use them were it makes good sense either.  You don't need 20 LVs for a single system, but you probably want 4 and 1 (at the hostOS layer) for each virtual machine.  Being able to make a snapshot at the virtual machine level is handy, which is why 1 LV per VM is the goal.  At least for me.  Inside the VM, you probably want 3-4 LVs, but for really simple VMs that don't have data, 1 could be enough.

Hopefully, I didn't miss the point or throw so much knowledge/experience into here to be too confusing.

---

### Post by sidneyki757 on 2021-10-19
Have you guys tried XCP-ng before?
When I was looking for a open source host server both xcp-ng and proxmox came up

I first need to get another test computer that the hardware supports hypervisor before I can test either one.

---

### Post by LHammonds on 2021-10-19
> **sidneyki757 said:**
> Have you guys tried XCP-ng before?I have not.

My first deployment of a virtual system was using ESXi many years ago and it is still running to this day...although on its last legs since our company has been moving away from internally-hosted solution to all 3rd-party.

I have used VirtualBox as a testing lab on my Windows PC for ages and anything that worked out would get setup on the ESXi system that runs 24/7.

I also use a pre-packaged (hardware+software) system called Nutanix which is built on top of opensource (KVM) software + its own proprietary controls.  Even though it is a solid system, it was just too expensive for my company to continue the maintenance on it...so now it is running with just me to keep it online until all systems are migrated.

My most recent research was looking into a 100% license-free system that I could deploy anywhere and allow for scaling from a single little desktop machine to multiple large servers with NAS support and I choose Proxmox.  Although, just like with Ubuntu, I could tack on an enterprise license for support if I wanted...but is not required.

There were not a lot of viable options when I first selected VMware.  Back then, it was considered the defacto virtualization system and reached a stable point where servers could be run with uptime as good as the physical server or better...which was a must when converting from physical to VM.  When I did my most recent selections, I used [urlhttps://en.wikipedia.org/wiki/Comparison_of_platform_virtualization_software]this wiki page[/url] as a starting point and then picked a handful of hopeful candidates and then tried them out.  I first [tried KVM]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=270") directly on a [minimal install of Ubuntu]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=272") (which is no longer available on 20.04+) but that proved to be a headache and it did not seem like a good fit with other non-Linux admins in the group that would support it.  

Proxmox was the 2nd solution I tried and I ended up going with that until I stalled out due to lack of hardware that was needed. (Never finished researching that project but it looked like a winner from what I saw of it)

LHammonds

---

### Post by TheFu on 2021-10-19
I used the Xen xm tools before switching to KVM/libvirt+virt-manager.
XCP-ng makes for a pretty screen, but from a stability standpoint, I think KVM has been much more stable. There are historical reasons by KVM is faster and more stable.

I'm not suggesting anyone use KVM directly, though many people do.  For people trying to be productive, use virt-manager to manage your VMs. I've not been impressed by any tools to manage containers, but my hands-on container knowledge has only been growing the last year. For around the last 7 yrs, I've watched and toyed with different container tools. Learned the best practices - in theory - and made a few decisions based on "marketing lies" that some of the most popular container marketing teams spewed for many years. Even when they were making clearly false claims, I knew I'd never use that type of container.  If a company needs to lie about their stuff, how can we trust them?

BTW, I was a stockholder in Citrix - the company behind Xen because their stuff was fairly good and Amazon was using it.  But when Amazon migrated off Xen to KVM-based solutions, that make it clear to me that Xen would always be a 2nd tier offer.  The integration into Linux was much more complex than they way that KVM does it. KVM is part of the core kernel maintainers responsibility now, but Xen is still an external addon.

A little history about each hypervisor is helpful in deciding on a solution.

But ... how did this thread devolve into virtualization from "system restore?"

---

### Post by LHammonds on 2021-10-19
> **TheFu said:**
> how did this thread devolve into virtualization from "system restore?"Well, you mentioned snapshots at the OS level.  I talked about snapshots at a hypervisor level above the OS and then the Op started asking direct questions about virtualization.  :)

---

### Post by MAFoElffen on 2021-10-21
From the devolution... TheFu has probably, hands-down the best responses on backing up and taking snapshots of systems. He has lot of good threads and posts on those. I agree with both LHammonds and TheFu on all their posts so far, on that they align with what I have done professionally, working for other people, as an IT Consultant, and personally. 

You can do snapshots and backups in many different ways, and at various different levels. As server clusters/mirrors/replications, full system backups and/or imaging, incremental's, dB replications/mirrors/failovers., transaction logs... file system manager snaphshots (lvm, zfs), and virtual host VM snapshots/checkpoints... There is sooooo many ways you can do that.

If "someone" has me come up with their disaster/recovery plan for them (paid), I usually used a combination of "many", to cover them, to get them to a "specific point of time", depending on what they decide is their own acceptable "risk factor" for their business. You can really get down to minute details in that, but the resources and cost of that gets higher with implementing those to the finer details.

On the "devolution"... I also moved away from Centrix and Xen based solutons around 2014-2016. I try not to mention them now. I still support KVM (and KVM derivatives), Hyper-V, vSphere/ESXi... But the only one that is really open on hardware right now is KVM. Both VMware... and "now" the current and future releases of Hyper-V (2019 on) are hardware specific and getting very picky about the hardware they support as being certified. VMware even more so, as it will refuse to install to what they consider what it will run on. Microsoft is moving to that also... On what it will install to.

And hardware that is being certified for "cloud flavors" is getting very picky now also. Especially if for Azure and/or VMware Cloud solutions. (Except for KVM). Amazon AWS moved from being XEN to KVM based...  I beta test and verify system/features for Insider Win Server, VMware vSphere/vCenter(includes ESXi), and KVM. Currently testing Win Server 2022, vSphere 7.2 and KVM 6.1.

Just a note of agreement and compliance with those above. Commercially, it boils down to what your company needs to get back to, and what they can pay licenses/support for that. For KVM, Canonical has great commercial support, and is less than RedHat, SUSE, Oracle, etc. Commercial is just another animal... concerning licensing and support. It just is.

Personally, I have a preference for Ubuntu and Canonical. I have been on their Server team since 2012. There is a lot of things that get resolved, right here, in Ubuntu. (Or get pointed out as upstream bugs, that this is wrong and not how it should be.) That is not bragging. It is just how it is. I am very proud of being a small part of that, in some way.

---

