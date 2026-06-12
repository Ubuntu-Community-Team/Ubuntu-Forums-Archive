---
title: "ESXi / iSCSI / Openfiler"
date: 2008-08-27
forum: Virtualisation
---

### Post by TheGameAh on 2008-08-27
The biggest hurdle preventing me from experimenting with ESXi as opposed to my Debian VMWare servers has been the features that Debian provides, mainly SSH and MDADM software raid.  From what I understand ESXi is a bare metal OS that wouldn't provide such features.

However, I'm now learning about iSCSI targets (I know this is old technology, please forgive my slowness).  So let's see if I can wrap my head around this.

You build an iSCSI target (looking at openfiler).  This then acts as public storage that a server running ESXi would point to, seeing the storage as local.  Is that about the summary of it?

Hmm, this is tempting me to play with it.  However, how does one go about backing up the Openfiler server?  Or if a drive fails in the Openfiler box, would you go about rebuilding the raid as in Debian, with MDADM?

---

### Post by tregora on 2008-09-18
Have you made any progress on this.  I was looking at doing the exact same thing.  I downloaded the vm of openfiler and it has a command line interface with ssh so I would assume you should be able to rebuild a raid setup from there.  Also if the raid card supports it you can have an online spare that can automatically rebuild if a drive fails.  I'm not sure if there is a way to boot to iscsi through.

---

### Post by JinxAu on 2008-09-19
I have had the chance recently to play around with Xen Server Enterprise, utilising Openfiler as the SAN/NAS backend. Have to say, once it is setup, it works pretty well.

iSCSI is exported how you mentioned... because you create LVM volumes on the Openfiler, you can setup Scheduled Snapshots and then rsync these snapshot backups to another server in case of disk failure.

We ended up configuring Openfiler to work in High Availability utilising DRBD (RAID-1 over network). It took a bit to setup, but ended up working quite well.

So, the end result is if filer1 goes down, filer2 detects this and comes up as filer1... got this down to around 10 seconds (can go lower) to fail over, which seemed to satisfy Xen as far as running the host VMs (only a bit of a pause in OS activity).

We ran through [http://wiki.hyber.dk/doku.php/openfiler_2.2_ha-cluster_guide](http://wiki.hyber.dk/doku.php/openfiler_2.2_ha-cluster_guide) for the initial setup, but there were a couple of idiosyncrasies with the setup - assumably because we were using 2.3, not 2.2.

Cya round
Jinx

---

### Post by trmentry on 2008-09-19
> **TheGameAh said:**
> The biggest hurdle preventing me from experimenting with ESXi as opposed to my Debian VMWare servers has been the features that Debian provides, mainly SSH and MDADM software raid.  From what I understand ESXi is a bare metal OS that wouldn't provide such features.

However, I'm now learning about iSCSI targets (I know this is old technology, please forgive my slowness).  So let's see if I can wrap my head around this.

You build an iSCSI target (looking at openfiler).  This then acts as public storage that a server running ESXi would point to, seeing the storage as local.  Is that about the summary of it?

Hmm, this is tempting me to play with it.  However, how does one go about backing up the Openfiler server?  Or if a drive fails in the Openfiler box, would you go about rebuilding the raid as in Debian, with MDADM?


I wrote up a quick and dirty how-to on getting esxi to attach to an iscsi target running on ubuntu 8.04.1 server using part of a raid5 array that was lvm2 section to be the target.

[http://ubuntuforums.org/showthread.php?t=917155](http://ubuntuforums.org/showthread.php?t=917155)

Hope that helps.

---

### Post by Ocelaris on 2008-11-18
Has anyone set up a regular ubuntu box with raid-1 for the OS and then some extra hard drives for storage? running a VM appliance of Openfiler, and using it just as a front end? 

I'm not sure as to openfiler's ability to notify of raid degradation etc... but for a small office system, I would think that would be ideal.

---

### Post by PilotJLR on 2008-11-20
I'm not sure WHY you would want your iscsi target to be in a VM itself...

As trmentry points out, an iscsi target is included in the repos of Ubuntu. I would recommend using that target to present a volume to ESXi... ESXi can then format the volume to vmfs3 and use it as a datastore.

Also consider NFS as well... that works perfectly well as an ESX datastore too. Unless you want to use non-free functionality like VCB, you won't lose anything by going to NFS.

---

### Post by Ocelaris on 2008-11-20
> **PilotJLR said:**
> I'm not sure WHY you would want your iscsi target to be in a VM itself...


Well, I don't want the iScsi target to be in a VM, I want that on the base server... I would set up the LVM2 + MDADM raid outside, and just manage it through openfiler. But I don't know if Openfiler can control through a VM the hardware... maybe just adding too much complexity to the system. I just like the front end of Openfiler. I can probably get open iscsi working CLI, but my friends and coworkers aren't going to sift through documentation to figure out linux if there's a gui. 

But if there's a nice VM based gui which can control the backend, that's the hook which will sell Linux to a lot of people without the pain threshold for linux...

Like I want the functionality of Openfiler, but I don't want to waste an entire server for just that purpose if I can throw other functionality into the box as well. For example a VMware server win2k3 domain controller, print server etc... all in that ubuntu server box, would be neat. In fact I'll be setting up something like that for a small office this weekend. 

I don't need iSCSI on that project, but later I am going to have the opportunity to put together a U320 SCSI iSCSI target based on 12 disks which will be supplementary to a small EMC system, and if all goes well, who knows we might use it more often if it works out. BUT the people I work with are gui-holics, they're not going to sit through CLI setting up iSCSI... But they would use openfiler to manage it if I set it up ahead of time for them. Hence my question if Openfiler running as a VM, would work ok as a front end on a ubuntu server... I just want Openfiler for the bling pretty much.

---

### Post by Underpants on 2008-11-30
You're correct about the iSCSI bit. Go to youtube and look up openfiler. There is a very nice video that you will easily find that gives a howto.


In regard to backups, you're really looking at two different problems that need to be solved.

Backing up VMs: 
* Use VCB (vmware consolidated backup) if you want image level. Or use standard backup software running on the guest machines like you normally would.

Protecting openfiler:
* openfiler uses mdadm. So if you lose a disk you can repair the array like you normally would. I know there are some other resiliency options with openfiler such as clustering that I have not yet used or needed.

Let me know if you have any other questions. :KS

---

