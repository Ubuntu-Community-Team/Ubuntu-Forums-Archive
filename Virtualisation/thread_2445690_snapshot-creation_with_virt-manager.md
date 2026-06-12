---
title: "snapshot-creation with virt-manager"
date: 2020-06-18
forum: Virtualisation
---

### Post by rosika on 2020-06-18
Hi altogether,


Can anybody help me? I´ve got a question regarding **snapshot**-creation with **virt-manager**.


Info: 
my system (host): Linux/Lubuntu 18.04.4 LTS, 64 bit


I want to achieve the following: installation of WIN (either 8.1 or 10) in a virtual machine with** qemu/kvm**. 
I also have virt-manager installed.


There are instructions for a case like this on  [https://www.pcwelt.de/ratgeber/Windows-als-virtuellen-PC-in-Linux-weiternutzen-9790033.html](https://www.pcwelt.de/ratgeber/Windows-als-virtuellen-PC-in-Linux-weiternutzen-9790033.html) (yet in German).
The procedure described there refers to VirtualBox. I don´t want to use that but rather **qemu/kvm/virt-manager**.


Yet there´s one point worth considering: A bit further on in the WINDOWS-installation process (but more or less at the beginning) there should be
a dialog like this: 


"Welcome" ------> "Region. Is it O.K?".


At this point in time WIN hasn´t been been activated yet. There are no personalized settings and no user account.


This should be the point in time when to create a "save point" or "backup point" so that when the WIN trial period is over (after 90 days)
the "save point" can be restored and thus there should be another 90 days test period etc.


So basically my question is:


Am I right in assuming that such a "save point" can also be created within **virt-manager** by creating a **snapshot** in the same way as described above?
Theoretically this should work because it´s possible to create such a snapshot from a running machine.


Thanks a lot for your help in advance.


Greetings.
Rosika   :-k

---

### Post by TheFu on 2020-06-18
Don't know about the virt-manager, but many of the back-end storage options for KVM+libvirt do support snapshots.  I use LVM's snapshot capability on all my systems nightly just before making backups. This is scripted and has nothing to do with virt-manager.  qcow2 also supports snapshots. Access that through the **qemu-img** tool.

For for any file-based VM storage technique, if the VM isn't running, you can just copy the file to a new name.  When you want to start over, copy that file back and everything will be as it was.  Typically, libvirt places file-based VM storage into ... 
 /var/lib/libvirt/images/
[https://www.cyberciti.biz/faq/how-to-create-create-snapshot-in-linux-kvm-vmdomain/](https://www.cyberciti.biz/faq/how-to-create-create-snapshot-in-linux-kvm-vmdomain/) says that libvirt does snapshots for qcow2 VM storage. 
```
virsh snapshot-create-as --domain {VM-NAME} --name "{SNAPSHOT-NAME}"
```
**virsh** is the TUI version of virt-manager.  The virsh manpage is full of snapshot infohttps://virt-manager.org/documentation/rmation.
The virt-manager documentation [https://virt-manager.org/documentation/](https://virt-manager.org/documentation/) is pretty weak. The virt-manager version on my systems doesn't have any "snapshot" options. None. There is a "Clone..." option, but that is different. The "clone" window has specific caveats about using it.  When I choose to clone a VM using LVM as the back-end storage, it says "storage cannot be shared or cloned" ... which isn't really the truth. The truth is that virt-manager doesn't know how to share or clone it.

BTW, I did look at a file-based Windows VM too. It says it couldn't be cloned either. Those are using raw images, so 100% pre-allocated storage. The system needed to have the best performance possible. Today, that isn't the situation, so I could convert them from raw to qcow2 or (better), LVM storage.
```
-rw-rw---- 1 libvirt-qemu kvm 36507222016 Jun 14 10:24 WinUlt-Data.img
-rw-rw---- 1 libvirt-qemu kvm 63166218240 Jun 18 10:43 WinUlt-os.img
```

**I think we are better off using either virsh or qemu-img directly. Those commands both have good manpages.**

Just to be very clear, virtualbox uses a .vdi file for VM storage. That is like a .qcow2 file, but slightly different.  KVM/libvirt can use vdi files for VM storage, if that's what you have, but expect it to work best with qcow2.  If you need enterprise snapshotting capabilities, look to LVM or ZFS for storage management of VMs.

---

### Post by slickymaster on 2020-06-18
*Thread moved to **Virtualisation**.*

---

### Post by Dennis N on 2020-06-18
If the the VM was installed with UEFI option, snapshots aren't supported.
Otherwise, in the VM console:
View > Snapshots 
'+' key will open dialog to create new snapshot.

---

### Post by rosika on 2020-06-19
@TheFu:

Hi and thank you so much for your response and the detailed information and also for the links. Much appreciated. :)

So I tried it out with my VM:
 
```
virsh snapshot-list --domain ubuntu18.04-2
 Name                 Creation Time             State
------------------------------------------------------------
 snapshot1            2020-06-12 15:31:40 +0200 shutoff
 snapshot2            2020-06-12 15:44:43 +0200 running
```

I had already taken those snaphots from within the virt-manager GUI.
Then:

```
virsh dumpxml ubuntu18.04-2 | grep -i qemu
      <driver name='qemu' type='qcow2'/>
      <source file='/media/rosika/f14a27c2-0b49-4607-94ea-2e56bbf76fe1/für_qemu2/testing-image.img'/>
      <source dir='/media/rosika/f14a27c2-0b49-4607-94ea-2e56bbf76fe1/für_qemu2/Austauschverzeichnis'/>

```

So **qcow2** as a result. Looks good.
Now:```
virsh snapshot-create-as --domain ubuntu18.04-2 --name "snapshot_19_06_2020"
```
And indeed, the new snapshot was created. Fine.

```
virsh snapshot-list --domain ubuntu18.04-2
 Name                 Creation Time             State
------------------------------------------------------------
 snapshot1            2020-06-12 15:31:40 +0200 shutoff
 snapshot2            2020-06-12 15:44:43 +0200 running
 snapshot_19_06_2020  2020-06-19 13:42:16 +0200 running  # new snapshot, created with terminal-command

```


Plus: when firing up virt-manager GUI this new snapshot is also displayed.
So basically it doesn´t seem to matter whether the snapshot is created by command or within the GUI.
And both ways it´s possible to create the snapshot from a running machine which really suits me well.

> Just to be very clear, virtualbox uses a .vdi file for VM storage. That is like a .qcow2 file, but slightly different

Yes, I understand. Thanks for the info. I´d really want to stick to kvm/qemu and qcow2. So there shouldn´t be any problems.

Thank you again for your kind help.

Greetings.
Rosika  ):P

---

### Post by rosika on 2020-06-19
@Dennis N:

Hi and thanks for the info.

> If the the VM was installed with UEFI option, snapshots aren't supported.



Really didn´t know that. But good to know.

Greetings.
Rosika :p

---

