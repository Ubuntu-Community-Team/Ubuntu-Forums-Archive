---
title: "Ubuntu filesystem goes read-only"
date: 2019-09-24
forum: Server Platforms
---

### Post by kathrin-huber on 2019-09-24
[FONT=arial]Hello,

I use Hyper-V (Windows Server 2012 R2) and Ubuntu 18.04.

I use this configuration (in former times 16.04) for some years now without problems.
Suddenly, my VM occationally goes in "read only" mode.
When this happens, I can log in, but not do sudo anymore.

I have to do a fsck, then ubuntu works again, but not apt.
It says that some list-file is damaged. 
I moved all linux* files from [/FONT]
/var/lib/dpkg/info/

[FONT=arial]Then I was able to reinstall the packages [FONT=courier new]([/FONT][/FONT][FONT=arial][FONT=courier new]sudo apt-get install --reinstall *packagename*[/FONT][I])
[/I]
But I have no idea what the reason for this behaviour is and I am afraid, that my vm/file system gets seriously damaged.
The hardware of the Server seems to be ok and the windows vms work perfecly.

Can you help me finding the mistake?

Thank you

[/FONT]

---

### Post by TheFu on 2019-09-24
Probably a disk that is dying.  Backup anything you don't want to lose. If the storage is an SSD, this is a common thing as the SSD fails. IME.

---

### Post by kathrin-huber on 2019-09-25
Thank you but this is a raid 5 with hotspare and I checked all the hardware - but even IF a hd should fail the vm should not even realise it because of the raid.
At the moment everything is running but when I do a dmesg it says:
"EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro"

But then at the end it says:
"new mount options do not match the existing superblock, will be ignored"

What does this mean? 
Is it now read-only? Why?/Why not? I can write to the filesystem...


Thank you

---

### Post by TheFu on 2019-09-25
That is just a mount option to go read-only if there are errors. If there aren't any errors, then it will mount read-write.
I don't know anyone using hyper-v and I've only have seen superblock issues on failing disks.

Where is the RAID5?  On the hostOS or from inside the guest?

I don't recall manually touching any files in  /var/lib/dpkg/info/ in at least a decade.  That area needs to be managed by the APT tools, not manually, unless there is a very good reason.

How do I say this last thing nicely.  Just because HW appears fine in Windows, doesn't mean the HW is ok.  Windows has ignored issues for decades.

---

### Post by kathrin-huber on 2019-09-25
Thank you!
The RAID 5 ist on the host- it's a hardware RAID. If there was an error on a disk, the raid would rebuild the data on the hotspare. Windows is not involved in this. 

It's a GIT, I did a backup of the important repositorys - one repository was damaged - I guess because of this error.

When I google this issue I get links like this: [http://invalidlogic.com/2012/04/28/ubuntu-precise-on-xenserver-disk-errors/](http://invalidlogic.com/2012/04/28/ubuntu-precise-on-xenserver-disk-errors/)

[https://wiki.dawico.de/display/WIKI/Hyper-V+turns+Debian+into+Read+Only+Mode](https://wiki.dawico.de/display/WIKI/Hyper-V+turns+Debian+into+Read+Only+Mode)

ect.
which advice to add a barrier=0 to the /etc/fstab (but I'm not sure if this might be negative for the consistence of my file system)

or add some "timeout rules" .... what do you think about this?

---

### Post by LHammonds on 2019-09-27
Assuming everything is fine at the hardware level, this does not sound like a typical issue.  And doing a full VM restore from a backup will not likely correct the problem.

If the problem cannot be directly found from error logs, I would create a new VM, setup the applications the same way and migrate the data over.  Then abandon the problematic VM once the new VM is verified as a working replacement with all the data.

LHammonds

---

### Post by kathrin-huber on 2019-09-30
Okay we decided to use an older snapshot and push the code again. 
And we will try to change the timeout and hope that this will solve the problem. 

Unfortunately, we are still not sure what the reason for the damaged filesystem is. 

If someone else has any idea or experienced the same we would be happy to hear of this.

---

### Post by kathrin-huber on 2019-09-30
I checked all my ubuntu vms and on every single of them I get the superblock message ... 
"EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro"
Then later:
"cgroup: new mount options do not match the existing superblock, will be ignored"

I'm not sure if this is a problem or usual behaviour?
Do I have to change something in the VM configuration?

As the VMs even are on different hosts I am sure it's no hardware issue.

---

### Post by kathrin-huber on 2019-10-08
I wanted to inform you that we got the reason for the behaviour. 
As It's usually not me doing the windows updates on the host, it was a bit hard to find.
The reason seems to be that when we reboot the host after an update, the staging of the vms doesn't work properly. So the solution seems to be to shutdown the vm befor rebooting the host. 
If anyone has any idea why this might occur I would be happy to hear ;-)

---

### Post by LHammonds on 2019-10-08
Oh!  So Windows wants to do a reboot to apply patches but does not shutdown the VMs before doing so...thus pulling the carpet out from under their feet and not letting them shutdown properly.

I do not use HyperV so I cannot give any pointers.  I use ESXi but RARELY ever reboot them.  But when I do, I have them in an HA (Highly Available) configuration so that when one ESXi wants to reboot, it migrates the VMs it hosts over to another host so that the VMs stay online all the time while the ESXi hosts under them reboot...but only ONE AT A TIME.  On ESXi, upgrades are scheduled out according to a plan.  There might be something similar for HyperV but again, I don't use that system.

LHammonds

---

### Post by guiverc on 2019-10-08
If the VMs aren't being shutdown, there is likely data in the VMs 'ram' that was not written to disk, ie. logical errors on the disk due to the equivalent of power-failure or just pulling the plug on the power because the host went down.

You (or your group/firm..) weren't allowing the VMs to shutdown & write/sync the unwritten data to 'disk' thus data was lost & logical disk errors were the result.

---

### Post by kathrin-huber on 2019-10-21
Thank you, I see why this occurs, but what confuses me is that this method of updating worked fine for years - we never had to shutdown the ubuntu vms... I don't see that we did any changes why staging the vm before reboot doesn't work any more.

---

