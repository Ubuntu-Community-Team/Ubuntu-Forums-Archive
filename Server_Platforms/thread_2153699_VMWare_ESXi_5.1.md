---
title: "VMWare ESXi 5.1"
date: 2013-06-12
forum: Server Platforms
---

### Post by termvrl on 2013-06-12
Hi All,

I want to ask. I have a virtual machine running on ESXi 5.1 and i do a few snapshots. 
After running smoothly for a few weeks, it prompt out an error, [FONT=&amp]&#8220;Cannot open the disk &#8216;XXXXXX.vmdk&#8217; or &#8216;Insufficient disk space on datastore&#8217;.
[/FONT]So, i simply delete old snapshot and left only latest snapshot. I reboot the server and it can run normally. 

But after 10days, it occurs again.
I delete the only left snapshot and try to reboot the virtual server, but unfortunately it linked to another error, Cannot open the disk 'VirtualVM-000006.vmdk' or one of the snapshot disks it depends on. The system cannot find the file specified VMware ESX cannot find the virtual disk "VirtualVM-000006.vmdk". Verify the path is valid and try again."

When I check Virtual Machine Properties, the hard disk still point to "[datastore1] VirtualVM/VirtualVM-000006.vmdk". The VirtualVM 0000006.vmdk i already delete from datastore. Now, only left VirtualVM.vmdk.

So, what can i do to start the VM again?
And is there any best practices to do snapshot/or delete it?
And what lesson can i take from this situation.
Fyi, i am new to VMWare ESXi.

Thanks!

:(:cry:

---

### Post by linuxtechguy on 2013-06-12
So how much space do you actually have on your datastore.

Also it is extremely bad idea to run a vm with snapshots. It degrades performance like crazy. You should never always have snapshots.

---

### Post by LHammonds on 2013-06-12
As already said, you should not keep VMware snapshots on a normal basis.  They are there so you can easily revert after a major change.  Take your snapshot, do you upgrade/install/test/etc. and once you validate that the system is stable, commit the change and remove the snapshots.

The way snapshots work is like this:

1. You make a snapshot.
2. The disk becomes frozen in time and another disk is written to anytime there is a change from the original (or prior snapshot).
3. Any change will be written to the current image and will continue to do so...thus taking up a lot of extra space very fast with no end in sight.

If you commit the change, it will apply the changes to the original (or prior snapshot).

If you rollback, it will simply delete the current image and use the original (or prior snapshot).

Never touch/manage the VMDK files directly.  That is a very bad thing to do.

LHammonds

---

### Post by termvrl on 2013-06-16
Fyi, i have 500GB physical HDD, and i set VM with 350GB HDD, i notice that when i take a snapshot, the maximum limits on VM HDD changed from 350GB to "N/A". 
I guess that this will let the Virtual Disk to grow as far as it can, unlimited.  In my situation, i able to startup the virtual machine using the 1st vmdk, which mean that it a fresh install server, not activate yet, not updated, all my installed software gone. And the Virtual Machine HDD same, still maximum limits "N/A".
What i do is, i remove the VM, and create it back from zero. I fresh install OS, activate, update, install back all soft, i take me a lot of times and effort.

As i notice that about export/import OVF template. What is it about? And how do we backup on VM ? 

Thanks for your response.

---

### Post by CharlesA on 2013-06-16
Keep in mind that each snapshot is basically a copy of the existing data and if you do not have enough room on the drive to store it, bad things happen.

How many space is currently being used on the snapshot you are trying to access?

---

### Post by termvrl on 2013-06-16
Hi All,

at the datastore only left less than 8GB.. 
if i plan to use snapshot what is the ratio for the physical HDD?
for example, i created 350GB Virtual Machine HDD, how many GB in physical HDD i should have?

---

