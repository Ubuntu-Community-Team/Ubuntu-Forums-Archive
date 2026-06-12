---
title: "Can I reinstall qemu KVM?"
date: 2021-09-28
forum: Server Platforms
---

### Post by Heeter on 2021-09-28
Hi all

Have a mature KVM qemu server that has quit working with an Ubuntu server update

[https://ubuntuforums.org/showthread.php?t=2467476](https://ubuntuforums.org/showthread.php?t=2467476)

Haven't been able to fix this

Can I uninstall reinstall KVM without affecting the 2 vms that usually guest on it?

Out of ideas on how to fix , internet searches have not helped

Email srrver vm has been down since Friday, people are getting ornery around me, :(

---

### Post by TheFu on 2021-09-28
There are 2 parts to a valid libvirt/KVM/QEMU setup.  If you don't use libvirt, things are easier.

[LIST=1]
[*]Storage for each VM
[*]XML definition file for each VM
[/LIST]
You can completely change the storage for each VM, provided the XML VM definition matches the new storage.  I've converted file/img-based VMs to LVM-LVs during a move to a different physical VM host, for example.

virsh dump-something will get the XML definition file for a VM.  Use **virsh define /path/to/VM-name.xml**  to put the definition back into a new libvirt system.  Then you can use virsh or virt-manager stuff to deal with it. No root/sudo needed.  libvirt holds those XML files in /etc/libvirt/.... you can find them.  I think you can copy them to skip the "dump" command.  If you want VMs to start automatically at boot, note the autostart/ directory in there too.  Storage and network stuff are there as well, all in /etc/libvirt.

Because of some other things you've mentioned in other threads, I'd propose that you change to LVM-based virtual machine storage. Then you won't need to know in advance how much storage is needed for each VM and you'll have lots of free storage available.  Of course, there are reasons to use file-based VM storage - mainly if you use NFS shared storage for failover between physical VM hosts and don't have block replication under that storage - something like sheepdog provides or any of the more typical block-level redundancy tools (CEPH, etc.).  KVM and libvirt provide options.  
For example, I have a few VMs:
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv     hadar-vg -wi-ao---- 175.00g                                                    
  lv-blog44-1804 hadar-vg -wi-ao----  16.20g                                                    
  lv-regulus     hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2   hadar-vg -wi-ao----  10.00g                                                    
  lv-spam3       hadar-vg -wi-a-----  10.00g                                                    
  lv-tp-lxd      hadar-vg twi-a-tz--  32.23g             0.00   10.06                           
  lv-vpn09-2004  hadar-vg -wi-ao----   7.50g                                                    
  lv-xen41-1804  hadar-vg -wi-ao----  12.50g                                                    
  lv-zcs45-1804  hadar-vg -wi-ao----  25.00g                                                    
  lxd-lv         hadar-vg -wi-ao----  60.00g                                                    
  root           hadar-vg -wi-ao----  32.33g                                                    
  swap_1         hadar-vg -wi-ao----   4.25g                                                    
  lv-backups     vg-hadar -wi-ao---- 465.72g              

```
The LVs are provided directly to each guest VM as block storage. Inside the guest, they appear a virtio devices.  libvirt-lv is a location for play VMs that use files.  root, swap and backups ... you can guess what those are.  Note that backups are on a different physical device and in a different VG. I don't allow VGs to cross physical devices. Been burned doing that before.  Here's the mounted storage, BTW:
```
$ dft
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   16G   15G  52% /
/dev/sdb1                         ext2  720M  165M  519M  25% /boot
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  139G   26G  85% /var/lib/libvirt
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd
/dev/mapper/vg--hadar-lv--backups ext4  459G  356G  103G  78% /Backups
```
Nice and clean, though I'd probably create a separate /var LV going forward.  / is only using 16G, so it isn't THAT important to split out /var or /home on this server.

How does the XML see the storage?  Well, virt-manager will setup the XML for us when we use LVM-backed storage for our VMs. The LV name is created from the VM name, I think. In the XML file, it becomes:
```
$ sudo egrep  lv-zcs45-1804 /etc/libvirt/qemu/z*
/etc/libvirt/qemu/zcs45-18.04.xml:      <source dev='/dev/hadar-vg/lv-zcs45-1804'/>

```
The libvirt XML files are very human readable.
If we need to expand the available storage inside a VM, we have flexibility. I've added another LV (see regulus-2), which showed up inside the VM as vdb storage. Inside regulus, I added the vdb1 to the same VG (same physical device) and then simply expanded the LVs and file systems inside the VM using lvextend -r -L +XYG.  [Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156) has the exact steps I used. Adding another vdb to the VM didn't require any downtime for the VM, though it is a little messier now.

It is also possible to just expand the current LV. Then I'd add a new partition in to the expanded area and add it to the VG, then lvextend ... I don't know if this requires a VM reboot to see the change in the disk or not.

Ideally, you'd have a new computer to migrate onto, so there wouldn't be much risk. 

Of course, doing a **sudo apt-get install --reinstall qemu-kvm **might work, but I doubt it.  I think you'll want to wipe the entire system and start over.

---

### Post by Heeter on 2021-09-28
Thank you FU!!!! Always nice to hear from you, very descriptive

I will report back in a jiffy

---

### Post by Heeter on 2021-09-28
I do have libvirt installed

```

root@serv:/home/adminpc# libvirtd
2021-09-28 20:33:39.214+0000: 6076: info : libvirt version: 4.0.0, package: 1ubuntu8.19 (Victor Manuel Tapia King <victor.tapia@canonical.com> Thu, 18 Feb 2021 17:40:38 +0100)
2021-09-28 20:33:39.214+0000: 6076: info : hostname: serv
2021-09-28 20:33:39.214+0000: 6076: error : virPidFileAcquirePath:422 : Failed to acquire pid file '/var/run/libvirtd.pid': Resource temporarily unavailable
root@serv:/home/adminpc# libvirtd -v
2021-09-28 20:34:28.675+0000: 6078: info : libvirt version: 4.0.0, package: 1ubuntu8.19 (Victor Manuel Tapia King <victor.tapia@canonical.com> Thu, 18 Feb 2021 17:40:38 +0100)
2021-09-28 20:34:28.675+0000: 6078: info : hostname: serv
2021-09-28 20:34:28.675+0000: 6078: info : virObjectNew:254 : OBJECT_NEW: obj=0x55cff5c78f20 classname=virAccessManagerClass
2021-09-28 20:34:28.675+0000: 6078: info : virObjectNew:254 : OBJECT_NEW: obj=0x55cff5c67cd0 classname=virAccessManagerClass
2021-09-28 20:34:28.675+0000: 6078: info : virObjectRef:388 : OBJECT_REF: obj=0x55cff5c78f20
2021-09-28 20:34:28.675+0000: 6078: info : virObjectUnref:350 : OBJECT_UNREF: obj=0x55cff5c78f20
2021-09-28 20:34:28.675+0000: 6078: error : virPidFileAcquirePath:422 : Failed to acquire pid file '/var/run/libvirtd.pid': Resource temporarily unavailable
2021-09-28 20:34:28.675+0000: 6078: info : virNetlinkEventServiceStopAll:781 : stopping all netlink event services
2021-09-28 20:34:28.675+0000: 6078: info : virNetlinkEventServiceStop:744 : stopping netlink event service

root@serv:/home/adminpc# libvirtd -V
libvirtd (libvirt) 4.0.0
root@serv:/home/adminpc# 

```

Regards

---

### Post by TheFu on 2021-09-28
> **Heeter said:**
> I do have libvirt installed 

I knew that - virsh and virt-manager only work with libvirt.

---

