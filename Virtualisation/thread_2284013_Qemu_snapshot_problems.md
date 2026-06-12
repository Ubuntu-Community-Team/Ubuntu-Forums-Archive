---
title: "Qemu snapshot problems"
date: 2015-06-26
forum: Virtualisation
---

### Post by paul215 on 2015-06-26
Hello all,

First off I am new to posting in this forum. I have browsed a lot threw the years and it has helped me tons. So I apologize for my newbie-ness ahead of time. Also I give thanks ahead of time.

I am setting up a Malware test lab. So far I have Ubuntu 12.04 Running in VirtualBox on a XP machine. Also I have a Guest windows XP OS setup and running using KVM inside my Ubuntu VM. I have a bunch of tools installed including Cuckoo. My problem is I can not get Cuckoo to test anything do to the fact that I can not create a snapshot of any VMs. When using "virsh snapshot-create xpguest /home/pauld/share/snap1.xml" I run into this error message : 

"error: Requested operation is not valid: Disk '/media/jump/windows.raw' does not support snapshotting" 

I have tryed RAW and qcow2 both of which return the same error. Now the strange thing is when attempting to make a snapshot of my qcow2 file I noticed after receiving the error, my XML file lists the qcow2 file as a RAW file type. The machine is listed as RAW format , and shows it using a .qcow2 file. I have edited this using virsh edit and I was successful at updating it so the file type remains qcow2. After fixing the XML and attempting to create a snapshot I get this error: 

"error: internal error Child process (/usr/bin/kvm-img snapshot -c snap1-Cuckoo1 /media/jump/windows.qcow2) status unexpected: exit status 1"

I have done a lot of googling, with out finding a solution. With the exception of a Ubuntu Bug report page, with no solution. Hopefully I am over looking something here and its not just a bug...


virsh --version 0.9.8

 libvirtd --version (libvirt) 0.9.8

QEMU emulator version 1.0 (qemu-kvm-1.0)

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

Thanks again!

---

### Post by TheFu on 2015-06-26
So ... you have 3 levels here and 2 levels of virtualization?
It isn't clear to me exactly what you've setup - any chance you could create a diagram to clarify it?

Is the base OS running on physical HW actually WindowsXP?  Without support - WinXP?

---

### Post by paul215 on 2015-06-27
Ill give a diagram a shot...
 
{Windows XP Physical hard drive[Virtual hard drive ubuntu 10.04(windows XP qcow2 drive)]}

I don't know if that helps or not but what I am trying to set up is a portable malware test lab . Which consist of a Windows OS hard drive running Ubuntu Virtually using VM VirtualBox. Inside the Virtual Ubuntu I am using KVM to run a Windows OS to test with. 

Yes the "out of support" Winxp. At this stage its a test. XP can run with very little hard drive space(which is crucial on my current test machine), and is much faster to test this with. The end result will be on a supported Win7 machine running Win7 virtually to test.

Do not worry,I keep the leash on all my XP machines to keep them far away from the dangerous internet. :p

---

### Post by TheFu on 2015-06-27
Well - Ubuntu 10.04 Server support ended a few month ago too - the desktop version support ended a few years ago. ;(  If you need a smaller Ubuntu - there is a mini install for Ubuntu 14.04. [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)  So - is it 10.04 or 12.04?  The virtualization tools for 12.04 and then 14.04 are vastly improved.

Can you post the snapshot.xml file?
BTW - libvirt doesn't create qcow2 files - those must be created manually from the CLI. How did you create the WinXP virtual-storage, with **qemu-img create**?

I tested this on a VM here running a raw img. Got the same error you got.  Converted that img to qcow2 (qemu-img convert -p -O qcow2 ./vpn.img ./vpn.qcow2 ), edited the vm XML file (virsh edit vpn) and tested again creating a snapshot while the VM was running (qemu-img snapshot -c TEST vpn.qcow2).  This time it worked. See:
```
# qemu-img snapshot -l  vpn.qcow2 
Snapshot list:
ID        TAG                 VM SIZE                DATE       VM CLOCK
1         TEST                      0 2015-06-27 20:28:25   00:00:00.000
2         TEST2                     0 2015-06-27 20:33:01   00:00:00.000
```

Oh - normally I disable disk caching, but read something about writeback being suggested for qcow2 vm-storage.  My minimal testing for performance seems that qcow2 isn't significantly slower than raw ... but I'm not running this inside a virtualbox with that extra layer of storage.  BTW - snapshots work well in vbox - could you use that instead?

---

### Post by paul215 on 2015-06-30
Thanks for your Replay TheFu! Sorry it took some time for me to reply. 

I am running 12.04 not 10.04 sorry for the confusion. I will definitely look into the mini install for my permanent test lab though. Thanks!

Here is the snapshot.xml file:

<domainsnapshot>
    <name>snap1-xpguest2 </name>
    <description>first clean fresh snap </description>
</domainsnapshot>


I was worried its very simple compared to others I see during research.

Also I created my qcow2 files with # qemu-img create -O qcow2 

I am going to try to convert the RAW back to qcow2 to see if I get the same result as you. I chose to use KVM instead of vbox due to conflicts I read about when you use Vbox inside a Vbox session. I may be going that route if I cant get the snapshots to work.

Thanks again!

well.... after converting RAW back to qcow2 I get a disk read error when attempting to boot from hard disk...

also after first run I checked the .xml and it again lists it as a .qcow2 file but the type show up as RAW? I changed this using virsh edit and the only change is it stops at booting from hard drive.Before the change it attempts to boot from network and all other devices, and of course fails

looking into why this happened right now

ok so know knows when but my virtual machines are all messed up. I deleted the bad ones and once I made a new machine with my .qcow2 file I am back up and running.

Viola! After converting the working RAW file back to qcow2 the snapshot works! Awesome. Thanks for your help. Any idea why such a thing would happen so i can prevent in the future?

---

### Post by kwolf-redhat on 2015-12-07
> **TheFu said:**
> tested again creating a snapshot while the VM was running (qemu-img snapshot -c TEST vpn.qcow2). 
I know this thread is already a few months old. But I feel this is important enough to warn against in case someone finds this thread in the archive:[B]

Never ever do this, it will eat your data![/B]

While a VM is running, you must not access it from another read-write process like 'qemu-img snapshot'. Instead you must use libvirt functions or directly the qemu monitor of the running VM to take snapshots.

---

### Post by TheFu on 2015-12-07
Thanks for posting kwolf-redhat, but since this is your very first post here, could you please provide a link to backup the statement?  

I would expect that the snapshot data would be lost unless it was reincorporated back into the base, but there are clear warnings about that in the docs I've read. Don't know that it would corrupt anything. It didn't here when I removed the snapshot ... didn't really need it.

Plus, the OP was running 12.04, so libvirt snapshot support back then ... er ... did it even exist? I know I used LVM snapshots and not libvirt (still do). Ubuntu tends to run over a year behind the libvirt releases.  OTOH, if you're running redhat, that isn't unexpected. RHEL 6.x is still on a 2.6 kernel after all. Stabilität über alles!

To the OP, LVM snapshots are an excellent reason to run Linux as the hostOS for virtualization, BTW.

---

