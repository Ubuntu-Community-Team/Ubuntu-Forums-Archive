---
title: "moved kvm vm's to new machine, one vm refuses to boot"
date: 2024-02-11
forum: Server Platforms
---

### Post by Heeter on 2024-02-11
Hi all,

I have copied 4 vm's from and old server to a new server. I copied all the xml and the vm files to the exact same folder structure on the new machine. Updated old kvm server machine to Ubuntu22LTS no-uefi and the new kvm server machine is same Ubuntu22LTS no-uefi.

3 of the VMs boot up and are running correctly

1 of them refuses to boot up. keep getting "Boot failed: not a bootable disk" error.

I have tried copying the main file (509GB) over to new machine several times, always same error.

The other 3 vm's moved without issue.

In virt-manager, I have compared the xml files between all, no difference between the functioning vm's and the non-booting vm.

Any help would be greatly appreciated

---

### Post by TheFu on 2024-02-11
Check that all the virtual hardware in the XML actually exists in the new machine.  If the VM is Linux, you may want to upgrade the motherboard type, for example.   For MS-Windows, things become more complicated.  Moving a VM with MSFT licensing requires NOT changing the virtual hardware unless you want to have to call MSFT to ask to run the OS.

Check the networking (bridge name), disks, peripherals, USB connections, video types, etc.  For all storage locations, actually copy/paste from the XML and validate they exist in a terminal.

None of my VMs are that large.  I do have a Win7 VM that is 130GB, but most of my Linux VMs are 10G or less. A few are 30G.

BTW, what sort of virtual storage is being used?  A few years ago, I moved from pre-allocated img files to LVM LVs. The performance increase was real.  LVM is integrated with virt-manager, so setting up new VMs is really fast and perform great.  I only played with a few qcow2 files over the last decade. Meh.  It is just another layer added between the logical file system used by the running VM and the actual storage hardware. Fewer layers are better, with a few exceptions.

---

### Post by Heeter on 2024-02-11
Hi TheFU!

All the 4 VMs images are Ubuntu20LTS each. There is no Windows VMs.

I opened and compared the xmls of the 3 functioning vms with the non functioning vm, everything matches.

The main KVM and all VMs use a single LVM partition that uses the whole allotted disk space.

The 519GIG VM is an Ubuntu20LTS/Nextcloud/NGinx/PHP/Mysql that is used by my whole family and extended family as a replacement to google drive.

The other 3 functioning vms are approx 15~20 Gigs each.

One thing that I failed to mention was that I used scp to transfer the vm qcow/xml files to the new server. I transferred the non functioning vm three different times with the same result. Maybe it's scp? I am have mounted an external USB and going to try this method now? Maybe the migration tool in virt-manager should be the way to go with this 519G vm image?

Regards

---

### Post by TheFu on 2024-02-11
How is the storage referenced inside the XML file?  For example, my logical volume for my VPN server VM is 
```
      <source dev='/dev/vg00/lv-vpn09-2004'/>
```

On disk (the VM host), it looks like this:
```
$ ll       /dev/vg00/lv-vpn09-2004
lrwxrwxrwx 1 root root 7 Feb 11 04:35 /dev/vg00/lv-vpn09-2004 -> ../dm-8

```
I prefer the /dev/{vgname}/{lvname} way to reference LVM LV storage.

In side the VPN VM, the storage looks like this:
```
$ dft
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4  5.8G  4.3G  1.2G  79% /

```

BTW, I'd have your family VM storage as an NFS mount to the VM, but the storage would be NFS from the VM host, not held inside the VM at all.  I do this with nextcloud ... though I actually run nextcloud in a container, not a full VM.  With containers, I have to use the container system to pass the storage inside, since using NFS directly requires some nasty container security compromises (running the container as root - yuck!):
```
$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
lxd/containers/nextcloud-lxd                     zfs    40G   11G   29G  28% /
/dev/mapper/WDBLK_8T-lv_d7                       ext4  3.6T  1.1T  2.4T  32% /media/Music
hadar:/d/rom/export/www/vhosts/xyzxy.com/gallery nfs   196G  120G   67G  65% /media/Photos
/dev/mapper/istar--vg-lv_media                   ext4  3.5T  3.5T   29G 100% /media/ebooks

```
So, as you can see, nextcloud is in a lxc container - lxc really demands using ZFS.  I oversized it, but fortunately the ZFS storage is shared with about 10 other lxc containers, so only 11G is actually used for nextcloud.  There are 3 external storage locations passed into the nextcloud container for use by that system.  1 of those storage areas is an NFS mount from a different system on the LAN, but passed in a local storage. The container doesn't care.

Clear as mud?

When a VM refuses to boot, it is usually that expected hardware doesn't exist.  Once I left a USB storage device connected to a VM, but I'd long unplugged it from the computer. That VM wasn't rebooted too often, so I'd forgotten.  3 weeks later, a reboot was needed and failed.  Took me far too long to realize it.  And again, check that the motherboard model in the XML is still available.  I've been burned by that.  QEMU does drop support for old virtual motherboards from time to time.

---

### Post by darkod on 2024-02-11
I do not use kvm but I would focus much more on the "not bootable disk" message.

Maybe it somehow lost the boot flag inside the VM or the MBR/UEFI sectors? Or a /boot parttion if separate?

PS: What if you try to boot the VM with the server ISO and go into rescue mode??

---

### Post by Heeter on 2024-02-11
> **TheFu said:**
> 
Clear as mud?


Yup

TheFU, you are the one. I would love to learn how you do this container. 

I am going to tell everyone to do their data backup, Then just going to do a fresh install inside a new VM on the new KVM host server.

You are correct, my current vms are old enough that qemu probably dropped support for them some time ago. Some of these vm's are major system updates from Ubuntu16 and 14.

---

### Post by Heeter on 2024-02-11
Ugh, Just realized what is the problem.

When I did fresh install of Ubuntu22LTS on new server, I completely missed that the default lvm size was 100GIG. I did lvextend up to 4TB, now all vm's migrated are up and running.

That took forever to realize what was going on. 

Thanks for helping me out guys.

---

### Post by TheFu on 2024-02-11
Solved?  Please use the **Thread Tools** button.

The way to use LVM with KVM and libvirt is to have 1 LV per virtual machine, not a huge shared LV that has a file system that gets mounted on the host, then creating qcow2 "file-based" VM storage.  Use LVM the smart way.

```
$ sudo lvs
  LV                VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
.... 
  Mint21.1          vg00           -wi-ao----   40.00g                                                    
  lv-blog44         vg00           -wi-ao----   30.20g                                                    
  lv-vpn09-2004     vg00           -wi-ao----    7.50g                                                    
  lv-xen41-2004     vg00           -wi-ao----   12.50g                                                    
  lv-zcs45-2004     vg00           -wi-ao----   35.00g                                                    
  ubuntu22.04-srv-2 vg00           -wi-a-----   15.00g                                                    
  ubuntu2204-srv    vg00           -wi-a-----   15.00g                                                    
....
```
That's the view from the host OS. Each of those LVs is for a different VM, well, except the 22.04 srv LVs.  I decided to play with LVM RAID1 inside the VM.  Hopefully, you can see the failure with the LVs used for RAID from the **lvs** output above   It is pretty ugly. I've decided that if I need RAID, I'd use mdadm for the RAID, then use LVM as the next layer, but I stopped using RAID since switching to quality SSDs.

---

