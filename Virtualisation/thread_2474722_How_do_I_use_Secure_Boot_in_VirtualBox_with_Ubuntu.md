---
title: "How do I use Secure Boot in VirtualBox with Ubuntu?"
date: 2022-05-06
forum: Virtualisation
---

### Post by Paddy Landau on 2022-05-06
I have Ubuntu 20.04 (host), and I've installed Ubuntu 22.04 (guest) in VirtualBox 6.1.34.

Before running the guest installation, in the VirtualBox settings, I turned on Settings > System > Motherboard > Enable UEFI.

But, after having installed Ubuntu 22.04 as the guest, I find that Secure Boot isn't actually turned on. At first, it looks like it, but [FONT=courier new]mokutil[/FONT] says that it isn't.
```
[COLOR=#0000cd]$ [[ -e /sys/firmware/efi ]] && echo yes[/COLOR]
yes
```
```
[COLOR=#0000cd]$ sudo efibootmgr[/COLOR]
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0000,0001,0002,0003
Boot0000* UiApp
Boot0001* UEFI VBOX CD-ROM VB2-01700376 
Boot0002* UEFI VBOX HARDDISK VB8573e6c9-0375295f 
Boot0003* EFI Internal Shell
Boot0004* ubuntu
```
```
[COLOR=#0000cd]$ mokutil --sb-state[/COLOR]
This system doesn't support Secure Boot
```
What do I need to do to enable Secure Boot on VirtualBox?

---

### Post by TheFu on 2022-05-07
_2.3.2.1. Kernel Modules and UEFI Secure Boot_ in the virtualbox manual has a small section on this.

>  If you are running on a system using UEFI (Unified Extensible Firmware Interface) Secure Boot, you may need to sign the following kernel modules before you can load them:

[LIST]
[*]    vboxdrv
[*]    vboxnetadp
[*]    vboxnetflt
[*]    vboxpci 
[*]
[/LIST]

See your system documentation for details of the kernel module signing process.

---

### Post by &amp;KyT$0P# on 2022-05-07
If you mean enable Secure Boot of the guest, last I saw [it won't be available until VirtualBox 7]("https://forums.virtualbox.org/viewtopic.php?p=507521#p507521").

---

### Post by TheFu on 2022-05-08
There is always KVM/QEMU which support secure boot in guest VMs the last few years. [https://wiki.debian.org/SecureBoot/VirtualMachine](https://wiki.debian.org/SecureBoot/VirtualMachine) Maybe time to use a better hypervisor?

I've never used secure boot with KVM, to my knowledge.  Heck, I've only forced UEFI for a guest VM once. It worked fine, but I didn't see the point for my needs.

---

### Post by Paddy Landau on 2022-05-08
> **TheFu said:**
> _2.3.2.1. Kernel Modules and UEFI Secure Boot_ in the virtualbox manual has a small section on this…
I wouldn't know even where to start signing the kernel modules!
> **halogen2 said:**
> If you mean enable Secure Boot of the guest, last I saw [it won't be available until VirtualBox 7]("https://forums.virtualbox.org/viewtopic.php?p=507521#p507521").
Ah, that could explain the problem, then.
> **TheFu said:**
> There is always KVM/QEMU… Maybe time to use a better hypervisor?
You need to define "better".

I had a thorough look at QEMU/KVM with virt-manager over the past week. It's harder to use than VirtualBox, not only less intuitive but also poorly documented. But, QEMU is definitely faster. QEMU has a deal-breaker, though: It doesn't allow snapshots with UEFI. That means that I can't use it for Windows.

So, for now, I have to stick with VirtualBox — it's "better" that way &#128578; I'll try QEMU again when they've solved the snapshot problem, but given that this has been an open bug for two years already, I'm not going to hold my breath.

I'll mark this thread as Solved, because Oracle is addressing this problem in VirtualBox version 7. It seems that they have the problem partially solved already (in the development channel).

---

### Post by TheFu on 2022-05-08
> **Paddy Landau said:**
> I wouldn't know even where to start signing the kernel modules!

Ah, that could explain the problem, then.

You need to define "better".

You already did.  It supports secureboot for VM guests.

> **Paddy Landau said:**
> I had a thorough look at QEMU/KVM with virt-manager over the past week. It's harder to use than VirtualBox, not only less intuitive but also poorly documented. But, QEMU is definitely faster. QEMU has a deal-breaker, though: It doesn't allow snapshots with UEFI. That means that I can't use it for Windows.
QEMU alone is slow.  KVM-QEMU uses hardware VT-x and AMD-v extensions to make context switching crazy fast.  This is partially why it is the fastest x64 hypervisor in the world.  And because it is integrated with the Linux kernel, the hardware supported is nearly unlimited, unlike the competition.
I never thought of virt-manager as being any different from the Virtualbox GUI, except that it allows many more enterprise choices, while supporting the typical end-user needs.

You've completely lost me on snapshots with UEFI.  Snapshots don't have to be part of the damn GUI for a hypervisor.  It is part of the back end storage and if you choose either qcow2 or LVM or ZFS for the back-end storage, you'll have full snapshots - better than the way the fake snapshots are done by others.  Snapshots have been around for over a decade in KVM-qemu.  Proxmox makes use of LVM for this and has a 1-click snapshot + backup webapp.  Proxmox has some downsides too, mainly because it takes over the entire hardware, which I suspect you don't like. KVM-Qemu doesn't require that, but it does work nicely on non-GUI servers too.  Crazy flexible.

> **Paddy Landau said:**
> So, for now, I have to stick with VirtualBox — it's "better" that way &#128578; I'll try QEMU again when they've solved the snapshot problem, but given that this has been an open bug for two years already, I'm not going to hold my breath.
What snapshot problem?  Is there a link?  I use snapshots with my KVM VMs nightly.  I suspect the issue found is extremely narrow.

> **Paddy Landau said:**
> I'll mark this thread as Solved, because Oracle is addressing this problem in VirtualBox version 7. It seems that they have the problem partially solved already (in the development channel).

---

### Post by Paddy Landau on 2022-05-08
> **TheFu said:**
> QEMU alone is slow.  KVM-QEMU uses hardware VT-x and AMD-v extensions to make context switching crazy fast.
VirtualBox also enables VT-x/AMD-v.
> **TheFu said:**
> I never thought of virt-manager as being any different from the Virtualbox GUI…
In this context, virt-manager is just a GUI front-end to QEMU/KVM. It makes it easier for people like me, who aren't that technically-minded.
> **TheFu said:**
> … if you choose either qcow2…
I do use qcow2.
> **TheFu said:**
> … you'll have full snapshots…
How do you create a snapshot? I only know how to do it via virt-manager, but I believe that it's possible on the CLI. Maybe that will solve the problem?
> **TheFu said:**
> What snapshot problem?  Is there a link?
I foolishly didn't take the link, but [here is a discussion]("https://www.reddit.com/r/VFIO/comments/dz1cwl/status_on_snapshot_of_uefi_vm_as_of_2019/?utm_source=share&utm_medium=web2x&context=3") of it back in 2019. If my understanding is wrong, I'd be grateful if you could show me how to do the snapshots with UEFI!

---

### Post by #&amp;thj^% on 2022-05-08
> **Paddy Landau said:**
> , I'd be grateful if you could show me how to do the snapshots with UEFI!

here's a good guide: [https://blog.wikichoon.com/2014/03/snapshot-support-in-virt-manager.html](https://blog.wikichoon.com/2014/03/snapshot-support-in-virt-manager.html)
And without virt-manger: [https://www.cyberciti.biz/faq/how-to-create-create-snapshot-in-linux-kvm-vmdomain/](https://www.cyberciti.biz/faq/how-to-create-create-snapshot-in-linux-kvm-vmdomain/)
TheFu's suggestions are all solid.

---

### Post by TheFu on 2022-05-08
If the entire disk inside the VM is provided has a block device from the hostOS, and that block device is from storage that supports snapshots, then the snapshot can be created and used at the hostOS as a read-only mount.

First, you need to use either LVM or ZFS for the block storage. I suppose qcow2 can be used too, but I only use that for play VMs.  LVM integrates into libvirt, at least at VM creation time.  

How well do you know LVM, since nothing for backups or snapshots is specific to the hypervisor. It is all 100% LVM stuff.
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv     hadar-vg -wi-ao---- 175.00g                                                    
[B]  lv-blog44-1804 hadar-vg -wi-ao----  16.20g                                                    
  lv-regulus     hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2   hadar-vg -wi-ao----  10.00g                                                    
  lv-tp-lxd      hadar-vg twi-a-tz--  32.23g             0.00   10.06                           
  lv-vpn09-2004  hadar-vg -wi-ao----   7.50g                                                    
  lv-xen41-1804  hadar-vg -wi-ao----  12.50g                                                    
  lv-zcs45-1804  hadar-vg -wi-ao----  25.00g                                                    
  lv-zcs46       hadar-vg -wi-a-----  25.00g                                                    
  lxd-lv         hadar-vg -wi-ao----  60.00g        [/B]                                            
  root           hadar-vg -wi-ao----  32.33g                                                    
  swap_1         hadar-vg -wi-ao----   4.25g
```
Here's a list of LVM-Logical volumes. The ones in bold aren't mounted. Each is provided to a VM/Linux Container as a block device.
So, my VPN server gets 7.5G of total block storage.  This is all from the KVM host system.

If I log into the VPN VM, here's what it sees:
```
$ dft
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4  5.8G  4.7G  791M  86% /

$ lsblk
NAME    SIZE TYPE FSTYPE MOUNTPOINT
vda     7.5G disk        
&#9500;&#9472;vda1    6G part ext4   /
&#9500;&#9472;vda2    1K part        
&#9492;&#9472;vda5 1021M part swap   [SWAP]

```
It doesn't know that the VM storage is an LVM-LV.  If I wanted, I could create a snapshot on the hostOS using standard LVM commands (you can look those up).  The snapshot gets a name and freezes all the blocks of storage. Then I'd use **kpartx** to find the different partitions inside "lv-vpn09-2004", since we know there are 3, but really only 1 is the OS. That frozen "snapshot" partition can then be mounted read-only and backed up.  

For the VPN server, there isn't any data and the open files are either short term logs or programs+configs, so using a snapshot really isn't needed. I want the simplest backups I can have that get what is necessary.  Because my VPN server is high risk, I use 'pulled' backups and a backup userid into the vpn system from the backup server to get all the data. The actual backup command is 
```
/usr/bin/sudo /usr/bin/rdiff-backup  \
       --exclude-special-files \
       --include "/usr/local" \
       --include /etc \
       --include /home \
       --include /root \
       --exclude '**' \
       $RUSER@$REMOTE::/  "$TGT"

```
With a tiny bit stuff before this line and 2 commands after it (a backup-set trimming command and some cleanup).  The hardest part in this is really setting up the root-like userid on the VPN server that allows root from the backup server access in a secure way.  That's all intermediate ssh stuff - similar to how github/gitlab allow git commands over ssh, but nothing else.

And last night
```
=== Time for Backups to vpn === 
StartTime 1651986104.00 (Sun May  8 01:01:44 2022)
EndTime 1651986105.37 (Sun May  8 01:01:45 2022)
ElapsedTime 1.37 (1.37 seconds)
TotalDestinationSizeChange 1812 (1.77 KB)
```
So, about 1 second to perform the backup.
```
thefu@istar:/Backups$ sudo rdiff-backup --list-increment-sizes vpn
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May  8 01:01:44 2022         10.3 MB           10.3 MB   (current mirror)
Sat May  7 01:01:42 2022         1.77 KB           10.3 MB
Fri May  6 01:01:54 2022       984 bytes           10.3 MB
Thu May  5 01:02:06 2022       953 bytes           10.3 MB
...
Wed Feb  9 01:01:52 2022       953 bytes           10.4 MB
Tue Feb  8 01:02:24 2022       953 bytes           10.4 MB
Mon Feb  7 01:01:36 2022       953 bytes           10.4 MB
```

Did I mention that the VPN server doesn't have any data?
Only ~3200 files are in the backups.  That's everything needed to recreate the system. Because it is a server, no GUI, and has basically 2 VPNs on it, nothing else, I'd be surprised if the reinstall and restore of settings to a working system took more than 15-20 minutes - even on completely different hardware.  
[Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927) has my restore process.

Of course, for systems with more data, more programs, a GUI, ... backups take longer and more storage.
Last night:

```
=== Time for Backups to hadar === 
StartTime 1651986111.00 (Sun May  8 01:01:51 2022)
EndTime 1651986135.62 (Sun May  8 01:02:15 2022)
ElapsedTime 24.62 (24.62 seconds)
TotalDestinationSizeChange 5052272 (4.82 MB)

$ sudo rdiff-backup --list-increment-sizes hadar
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May  8 01:01:51 2022         8.85 GB           8.85 GB   (current mirror)
Sat May  7 01:01:48 2022         21.3 MB           8.87 GB
Fri May  6 01:02:00 2022         6.45 MB           8.88 GB
...
Wed Feb  9 01:02:00 2022         12.3 MB           10.3 GB
Tue Feb  8 01:02:45 2022         3.53 MB           10.3 GB
Mon Feb  7 01:01:43 2022         5.39 MB           10.3 GB

```
25 seconds for the backup. Hadar also gets 90D of versioned backups.

Anyways, the key to all of this is providing block storage to the VM, creating snapshots in the hostOS, and performing backups from outside the VM.  I don't do that, since I don't backup anything except what is needed to perform a reinstall of the OS and restore settings/files.  I don't need/want UEFI or BIOS or /boot/ stuff in my backups. It isn't needed.

---

### Post by Paddy Landau on 2022-05-08
> **1fallen said:**
> here's a good guide: [https://blog.wikichoon.com/2014/03/snapshot-support-in-virt-manager.html](https://blog.wikichoon.com/2014/03/snapshot-support-in-virt-manager.html)
That's what I was using. But it couldn't take a snapshot of a machine using UEFI; only a machine that used BIOS. 
> **1fallen said:**
> And without virt-manger: [https://www.cyberciti.biz/faq/how-to-create-create-snapshot-in-linux-kvm-vmdomain/](https://www.cyberciti.biz/faq/how-to-create-create-snapshot-in-linux-kvm-vmdomain/)
TheFu's suggestions are all solid.
When I get time, I'll redo a VM in QEMU/KVM and see if I can get that to work.

---

### Post by Paddy Landau on 2022-05-08
> **TheFu said:**
> If the entire disk inside the VM is provided has a block device from the hostOS…
Thank you for the extensive instructions. It seems to be unnecessarily complicated!

When I get time to make another VM in QEMU/KVM, I'll give this a try. The problem is that I don't understand the very first step: "If the entire disk inside the VM is provided has a block device from the hostOS…" I wouldn't have a clue if this is the case! How would I find out?

I fully understand the concept behind LVM, and once upon a time I knew how to use it, but I've forgotten virtually all of it.

---

### Post by TheFu on 2022-05-08
I never used qcow/qcow2 for VM storage, except for toy VMs.

The problem with my solutions for snapshots and VMs and backups is they all use ~10 step process, each, so around 30 steps total.  That can be overwhelming to someone used to running a program, setting the source and target directories, then pushing the "backup" button.  

OTOH, LVM has been enterprise grade over 20 yrs, including snapshots.  The integration into libvirt for backups isn't something I've used. I know that LVM storage is integrated with libvirt storage pools for creating new VMs. That works well.  The LVM snapshot is completely separate from the backup tool, so any backup tool can be used, based on the needs of the user.

[https://pve.proxmox.com/wiki/Live_Snapshots](https://pve.proxmox.com/wiki/Live_Snapshots) explains Proxmox with snapshots and backups. Seems they don't support LVM-LV snapshots, but only LVM-lvmthin snapshots.  Thin provisioning is a bit more complex than normal LVM LVs. Proxmox hides those details. I do like this warning: 
>  	If a storage runs full, all guests using volumes on that storage receive IO errors. This can cause file system inconsistencies and may corrupt your data. So it is advisable to avoid over-provisioning of your storage resources, or carefully observe free space to avoid such conditions.

---

### Post by TheFu on 2022-05-08
> **Paddy Landau said:**
>  The problem is that I don't understand the very first step: "If the entire disk inside the VM is provided has a block device from the hostOS…" I wouldn't have a clue if this is the case! How would I find out?

If the storage provided to a VM isn't from a file, then it is probably block storage, like an LVM-LV.  If you didn't specifically set this up, it isn't magically happening.  I showed what my VM block storage looks like in prior posts using the **lvs** command.

BTW, **virsh** has lots of storage commands.  They are described in the virsh manpage. Same for virsh snapshot options, if you want to go that direction.  I don't do that, but I don't want to freeze the blocks for the whole domain, just for the specific file systems I'm going to backup.
```
       snapshot-create domain [xmlfile] {[--redefine [--current]] | [--no-metadata]
       [--halt] [--disk-only] [--reuse-external] [--quiesce] [--atomic] [--live]}
           Create a snapshot for domain domain with the properties specified in xmlfile.
           Normally, the only properties settable for a domain snapshot are the <name> and
           <description> elements, as well as <disks> if --disk-only is given; the rest of
           the fields are ignored, and automatically filled in by libvirt.  If xmlfile is
           completely omitted, then libvirt will choose a value for all fields.  The new
           snapshot will become current, as listed by snapshot-current.
...
           If --disk-only is specified, the snapshot will only include disk state rather
           than the usual system checkpoint with vm state.  Disk snapshots are faster than
           full system checkpoints, but reverting to a disk snapshot may require fsck or
           journal replays, since it is like the disk state at the point when the power
           cord is abruptly pulled; and mixing --halt and --disk-only loses any data that
           was not flushed to disk at the time.
...
           If --quiesce is specified, libvirt will try to use guest agent to freeze and
           unfreeze domain's mounted file systems. However, if domain has no guest agent,
           snapshot creation will fail.  Currently, this requires --disk-only to be passed
           as well.
...
           If --live is specified, libvirt takes the snapshot (checkpoint) while the guest
           is running. Both disk snapshot and domain memory snapshot are taken. This
           increases the size of the memory image of the external checkpoint. This is
           currently supported only for external checkpoints.

```
Clearly, after you get the exact snapshot command desired, you'll want to keep that in a script to get it correct every time. Consistency matters.  Probably want a similar snapshot-delete script to cleanup any old snapshots, so blocks of storage are frozen indefinitely.
```
       snapshot-delete domain {snapshot | --current} [--metadata] [{--children |
       --children-only}]
           Delete the snapshot for the domain named snapshot, or the current snapshot with
           --current.  If this snapshot has child snapshots, changes from this snapshot
           will be merged into the children.  If --children is passed, then delete this
           snapshot and any children of this snapshot.  If --children-only is passed, then
           delete any children of this snapshot, but leave this snapshot intact.  These
           two flags are mutually exclusive.
```

Because libvirt and KVM support live migrations of VMs between different VM hosts, some of the options are useful for both backs and live migrations.

Enterprise features can be confusing sometimes.

---

### Post by Paddy Landau on 2022-05-09
> **TheFu said:**
> If you didn't specifically set this up, it isn't magically happening.
I didn't specifically set it up :)
> **TheFu said:**
> Enterprise features can be confusing sometimes.
I'll say! This isn't for professional use, so I think that I'm going to take the path of least resistance. When it comes built into QEMU/KVM and virt-manager, I'll look at it again, and until then, I'll use the much simpler option, VirtualBox.

If this were for professional use, I would definitely look into it.

Thank you for all your time. You clearly have enough know-how to be able to write a proper "QEMU/KVM for Dummies" book!

---

### Post by TheFu on 2022-05-09
If the system was setup using LVM (which is 1 checkbox during the install) and not all of the VG storage was already allocated to LVs, then this would all be pretty trivial.  There are many reasons to use LVM that have nothing to do with virtual machines.

Also, for the BTRFS people - there are some warnings against using BTRFS for virtual machine storage on the host. Something related to CoW file systems not working well with VMs. Corruption and terrible performance can happen. I think that's regardless of the hypervisor. In the early years, they tried to fix it, but later they added some options to BTRFS as a workaround. Those are beyond me.

But if you can wait for vbox, that's fine too.

I'm still confused why using secure boot with UEFI for Linux systems even matters. I haven't done any research, but almost all security has 1 basic rule - if they can gain physical access to the system, then all security fails.  For virtual machines, "physical access" means any connection to the hostOS.

---

### Post by tea for one on 2022-05-11
> **Paddy Landau said:**
> I had a thorough look at QEMU/KVM with virt-manager over the past week. It's harder to use than VirtualBox, not only less intuitive but also poorly documented. But, QEMU is definitely faster. QEMU has a deal-breaker, though: It doesn't allow snapshots with UEFI. That means that I can't use it for Windows.

Yes, using QEMU-KVM, a Windows 11 Guest in UEFI mode will not allow a snapshot.
```
Error creating snapshot: Operation not supported: internal snapshots of a VM with pflash based firmware are not supported

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 72, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/details/snapshots.py", line 237, in _do_create_snapshot
    self.vm.create_snapshot(xml)
  File "/usr/share/virt-manager/virtManager/object/domain.py", line 1179, in create_snapshot
    self._backend.snapshotCreateXML(xml, flags)
  File "/usr/lib/python3/dist-packages/libvirt.py", line 3070, in snapshotCreateXML
    raise libvirtError('virDomainSnapshotCreateXML() failed')
libvirt.libvirtError: Operation not supported: internal snapshots of a VM with pflash based firmware are not supported
```
Although the snapshot function fails, you can use [COLOR="#0000FF"]Clone Virtual Machine[/COLOR].
Temporarily, would that be an acceptable alternative?

---

### Post by Paddy Landau on 2022-05-11
> **tea for one said:**
> Yes, using QEMU-KVM, a Windows 11 Guest in UEFI mode will not allow a snapshot.
That's the same error that I have. It's a known bug, apparently known for two years already.
> **tea for one said:**
> … Clone Virtual Machine. Temporarily, would that be an acceptable alternative?
Thanks for the idea, but no.

First, it doesn't seem to be temporary (the bug isn't being addressed).

Second, cloning an entire machine for a snapshot is excessive. It potentially takes a lot of space and time.

Third, it's getting too complicated. If I had a public-facing server where response times were critical, yes, I'd consider it, but that's not the case for me.

I'll rather just wait for VirtualBox to fix their bug, which has already been tested but not yet released.

---

### Post by TheFu on 2022-05-11
If you use LVM and create a snapshot outside any virtualization tool, it works, regardless of the data storage involved.

```
# lvcreate -L 1GB -s -n libvirt_snap /dev/hadar-vg/libvirt-lv
  Using default stripesize 64.00 KiB.
  Logical volume "libvirt_snap" created.
```

That was less than 1 second.
```
# lvs
  LV             VG       Attr       LSize   Pool Origin     Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv     hadar-vg owi-aos--- 175.00g                                                        
  libvirt_snap   hadar-vg swi-a-s---   1.00g      libvirt-lv 0.01    
```           

And there's the snapshot which can be used for anything needed, until updates use the 1G allocated.
```

# mount /dev/hadar-vg/libvirt_snap /mnt/src
# cd /mnt/src

# ls
boot/  dnsmasq/  images/  lost+found/  qemu/  sanlock/

# ll
total 44
drwxr-xr-x  8 root root  4096 Apr 23 13:32 ./
drwxr-xr-x  9 root root  4096 Jul  7  2021 ../
drwx--x--x  2 root root  4096 May  6  2020 boot/
drwxr-xr-x  2 root root  4096 May  7 09:55 dnsmasq/
drwx--s--x  3 root root  4096 Dec 20 10:45 images/
drwx------  2 root root 16384 Apr 13  2019 lost+found/
drwxr-x--- 26 tf   kvm   4096 May  7 09:55 qemu/
drwx------  2 root root  4096 May  6  2020 sanlock/

# df .
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-libvirt_snap  173G  132G   33G  81% /mnt/src
```

And to clean up stuff, we may want to merge any changes back into the main LV. First umount, then merge.
```
# umount /mnt/src
# lvconvert --merge /dev/mapper/hadar--vg-libvirt_snap

```
The merge automatically removes the snapshot. The snapshot doesn't show up in the **lvs** output anymore.

The entire time this was going on, a number of KVM VMs were actively running.
[https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/](https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/) has steps.

I cannot imaging any UEFI storage getting in the way, but none of my VMs use UEFI so I don't really know.  This is a 100% storage snapshot, no RAM state gets saved.

---

