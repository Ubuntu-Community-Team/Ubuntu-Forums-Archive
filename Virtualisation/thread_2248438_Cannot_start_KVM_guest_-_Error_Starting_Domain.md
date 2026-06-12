---
title: "Cannot start KVM guest - Error Starting Domain"
date: 2014-10-14
forum: Virtualisation
---

### Post by scojopa on 2014-10-14
Can someone help me get started on solving this. I have a ubuntu 14.04 server as kvm host running ubuntu 14.04 guests. One of the quests will not start. I have been searching and found nothing  - I do not have CDROM or monitor connected to host machine. Please help - this is my mail server. One thing I have noticed is the time in the logs (below) is 10-15 00:23:11  but the time on the server itself is 10-14 21:04? I have tried rebooting the host 

Also my other kvm quest is running fine. 

When I try to start it from virt-manager I get the following:

Error starting domain: cannot read header '/dev/vmstage1/mail': Input/output error


Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 117, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1162, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 866, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: cannot read header '/dev/vmstage1/mail': Input/output error

Under libvirt logs - same error:

2014-10-15 00:23:11.419+0000: 2133: error : qemuAutostartDomain:292 : Failed to autostart VM 'mail': cannot read header '/dev/vmstage1/mail': Input/output error
2014-10-15 00:23:25.945+0000: 2123: error : virStorageFileGetMetadataFromFDInternal:1000 : cannot read header '/dev/vmstage1/mail': Input/output error
2014-10-15 00:26:39.993+0000: 2126: error : virStorageFileGetMetadataFromFDInternal:1000 : cannot read header '/dev/vmstage1/mail': Input/output error
2014-10-15 00:48:19.160+0000: 2124: error : virStorageFileGetMetadataFromFDInternal:1000 : cannot read header '/dev/vmstage1/mail': Input/output error
2014-10-15 00:52:31.394+0000: 2120: error : qemuMonitorIO:656 : internal error: End of file from monitor
2014-10-15 00:54:50.969+0000: 2137: info : libvirt version: 1.2.2
2014-10-15 00:54:50.969+0000: 2137: error : virStorageFileGetMetadataFromFDInternal:1000 : cannot read header '/dev/vmstage1/mail': Input/output error
2014-10-15 00:54:50.987+0000: 2137: error : qemuAutostartDomain:292 : Failed to autostart VM 'mail': cannot read header '/dev/vmstage1/mail': Input/output error
2014-10-15 00:55:17.685+0000: 2128: error : virStorageFileGetMetadataFromFDInternal:1000 : cannot read header '/dev/vmstage1/mail': Input/output error
2014-10-15 01:00:17.563+0000: 2128: error : virStorageFileGetMetadataFromFDInternal:1000 : cannot read header '/dev/vmstage1/mail': Input/output error



Thank you in advance

---

### Post by TheFu on 2014-10-14
Can you export the XML using virsh dumpxml and post that please?
I take it that virt-manager is running remote - after all, no self respecting "server" would have a GUI. ;)
Does virsh create work?

I've been running email servers for almost 20 years - never heard of /dev/vmstage1/mail before.

---

### Post by scojopa on 2014-10-14
Under Storage, LVM Volume Group - the Volume is not listed. 
lvidisplay shows the LV snapshot status INACTIVE  but LV Status available.

---

### Post by scojopa on 2014-10-14
root@hyper:/dev/vmstage1# virsh dumpxml mail
<domain type='kvm'>
  <name>mail</name>
  <uuid>7d2a52fc-e731-f3bf-7b5d-3351f6ddc75b</uuid>
  <memory unit='KiB'>7168000</memory>
  <currentMemory unit='KiB'>7168000</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/vmstage1/mail'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:3a:4e:0b'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

---

### Post by scojopa on 2014-10-14
just a followup to your post - yes running virt-manager over ssh - a newbie - but no gui ;)

mail is the name of the quest 
vmstage1 is the name of the lv group

---

### Post by TheFu on 2014-10-15
Didn't see anything obviously wrong and the error seems to say there is something wrong with the storage.

lvdisplay?

Just to validate. If that LV is there, then I'd connect up a liveCD and boot that then go poking around in the installation from that.

---

### Post by scojopa on 2014-10-15
Under Storage, LVM Volume Group - the Volume is not listed. 
lvidisplay shows the LV snapshot status INACTIVE but LV Status available.

---

### Post by KillerKelvUK on 2014-10-15
so is "vmstage" the volume group and "mail" the logical volume?

I stopped using lvm's as the disk storage a while back but I recall having to use a mount path like "/dev/mapper/vmstage1-mail" which is also how the /etc/fstab syntax operates.  If the /dev/mapper location doesn't contain your lvm storage then the VM guest won't be able to locate it to start.

---

### Post by TheFu on 2014-10-15
Sorry - guess I've been completely obtuse.

Please post the output of the **lvdisplay** for the system. Run the command, post the output. Please use "code" tags.

---

### Post by scojopa on 2014-10-15
vmstage1 = lvg 
mail = guest that will not start

```
  /dev/vmstage1/mail: read failed after 0 of 4096 at 20971454464: Input/output error  /dev/vmstage1/mail: read failed after 0 of 4096 at 20971511808: Input/output error
  /dev/vmstage1/mail: read failed after 0 of 4096 at 0: Input/output error
  /dev/vmstage1/mail: read failed after 0 of 4096 at 4096: Input/output error
  --- Logical volume ---
  LV Path                /dev/vmclones1/mailclone
  LV Name                mailclone
  VG Name                vmclones1
  LV UUID                XVApT1-tE0j-7jOL-QscO-ZuvH-EL43-0Qwxci
  LV Write Access        read/write
  LV Creation host, time hyper, 2014-09-26 20:46:14 -0400
  LV snapshot status     active destination for mailclone_vorigin
  LV Status              available
  # open                 0
  LV Size                19.53 GiB
  Current LE             5000
  COW-table size         8.00 GiB
  COW-table LE           2048
  Allocated to snapshot  0.00%
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:5
   
  --- Logical volume ---
  LV Path                /dev/vmstage1/web
  LV Name                web
  VG Name                vmstage1
  LV UUID                dUrHgT-hEqM-O10W-k15c-fIOk-yWdE-r793ul
  LV Write Access        read/write
  LV Creation host, time hyper, 2014-09-22 22:37:29 -0400
  LV snapshot status     active destination for web_vorigin
  LV Status              available
  # open                 1
  LV Size                19.53 GiB
  Current LE             5000
  COW-table size         8.00 GiB
  COW-table LE           2048
  Allocated to snapshot  40.80%
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:9
   
  --- Logical volume ---
  LV Path                /dev/vmstage1/mail
  LV Name                mail
  VG Name                vmstage1
  LV UUID                0ZxG9v-5jnx-KKdN-QJ3O-wLat-iCRr-voJUzq
  LV Write Access        read/write
  LV Creation host, time hyper, 2014-09-25 18:10:48 -0400
  LV snapshot status     INACTIVE destination for mail_vorigin
  LV Status              available
  # open                 0
  LV Size                19.53 GiB
  Current LE             5000
  COW-table size         8.00 GiB
  COW-table LE           2048
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:13
   
  --- Logical volume ---
  LV Path                /dev/vmstage1/mail-clone
  LV Name                mail-clone
  VG Name                vmstage1
  LV UUID                gFToS7-kYwe-Zjoq-cIac-aHLK-CiOw-rm0m5x
  LV Write Access        read/write
  LV Creation host, time hyper, 2014-09-26 20:48:48 -0400
  LV Status              available
  # open                 0
  LV Size                19.53 GiB
  Current LE             5000
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:14
   
  --- Logical volume ---
  LV Path                /dev/hyper-vg/root
  LV Name                root
  VG Name                hyper-vg
  LV UUID                i4BWt4-9Tfp-UCki-eXJU-4SMS-BdZi-Izj7rz
  LV Write Access        read/write
  LV Creation host, time hyper, 2014-09-01 13:22:15 -0400
  LV Status              available
  # open                 1
  LV Size                169.18 GiB
  Current LE             43309
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/hyper-vg/swap_1
  LV Name                swap_1
  VG Name                hyper-vg
  LV UUID                eZ1ias-Jd4s-q9AT-C0mA-7Q33-OLcu-NLJfTz
  LV Write Access        read/write
  LV Creation host, time hyper, 2014-09-01 13:22:15 -0400
  LV Status              available
  # open                 2
  LV Size                63.89 GiB
  Current LE             16357
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1



```

---

### Post by scojopa on 2014-10-15
what do you use for disk storage now?

---

### Post by scojopa on 2014-10-15
```
pvs  /dev/vmstage1/mail: read failed after 0 of 4096 at 20971454464: Input/output error
  /dev/vmstage1/mail: read failed after 0 of 4096 at 20971511808: Input/output error
  /dev/vmstage1/mail: read failed after 0 of 4096 at 0: Input/output error
  /dev/vmstage1/mail: read failed after 0 of 4096 at 4096: Input/output error
  PV         VG        Fmt  Attr PSize   PFree 
  /dev/sda5  hyper-vg  lvm2 a--  233.07g     0 
  /dev/sdb   vmstage1  lvm2 a--  100.00g 64.46g
  /dev/sdc   vmclones1 lvm2 a--  100.00g 92.00g



```

---

### Post by TheFu on 2014-10-15
Thanks.
[http://www.linuxtechi.com/fixing-lvm-io-errors/](http://www.linuxtechi.com/fixing-lvm-io-errors/) provides some steps to correct this. Don't know if it will help, but I don't think it can hurt. 
If this doesn't solve it, I'd wipe the LV and start over from the last backup.

---

### Post by scojopa on 2014-10-15
thanks I tried that - but same error -

Will wipe it and rebuild - good for learning anyway.

---

### Post by TheFu on 2014-10-15
> **scojopa said:**
> what do you use for disk storage now?

I use raw files, fully allocated, on LVM hostOS storage.  Can't take snapshots, but backups using rdiff-backup take just 1-3 min daily and the front-end email server doesn't need to be taken down at all.  I've had to restore the email system to new storage/VM host a few times (practicing Zimbra migrations) and it takes 30-45 min.  That's reasonable for our needs.

Tried using NFS, but it wasn't fast enough.

---

