---
title: "vmware virtual disk out of space error"
date: 2013-08-15
forum: Virtualisation
---

### Post by nick20 on 2013-08-15
I am running Ubuntu Server 12.04 under vmware. (ESXi 5 with vSphere client)
It's running on a datastore with capacity of 265gb
The VM is on a Thick Provisioned Eager Zeroed disk of 250gb
Leaving 15gb for snapshots etc.
I used default LVM partition setup on installation using all available space.

i am creating an iSCSI target server LUN
and when attempting to create 200gb file with the following command

[FONT=Calibri]dd if=/dev/zero of=/storage/lun1.img bs=1024k count=200000

a new vmdk file (fileserver-000002.vmdk) is produced until the datastore is filled, I get an out of space error in vSphere client and the vm hangs.
I then need to restore from snapshot.

Forgive my noobiness  but I assumed the resulting file would be created within the original fileserver.vmdk file.

Where am I going wrong?? 


[/FONT]

---

### Post by nick20 on 2013-08-15
Problem SOLVED

It was my lack of understanding of how snapshots worked.

If you have active snapshots a new 'working' virtual disk is created until the snapshots are deleted or you consolidate.
I had an active snapshot and was trying to create a 200GB file. My base virtual disk was thick provisioned at 250GB in a Datastore size 265GB.

I needed to delete all snapshots then create the file.

---

### Post by TheFu on 2013-08-15
Please mark the thread as solved in the THREAD TOOLS.
Also, it would be helpful to specify which VMware product you are using. There are 6 different programs, so "vmware" is confusing to many people.

---

