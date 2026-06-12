---
title: "virt-sparsify or other method to shrink virtual machines for backup?"
date: 2021-12-13
forum: Virtualisation
---

### Post by glued-2-keyboard on 2021-12-13
Hi

I am trying to reduce the size of my qemu/kvm virtual machine backups.

Was wonder if I should use virt-sparsify to reduce the size of my vm backups?

For example I have VM_One.qcow2

qemu-img info VM_One.qcow2

image: VM_One.qcow2
file format: qcow2
virtual size: 100G (107374182400 bytes)
disk size: 77G
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false


from within VM_One df -h 

Filesystem                                Size  Used Avail Use% Mounted on
udev                                        2.9G     0  2.9G   0% /dev
tmpfs                                       597M  732K  596M   1% /run
/dev/mapper/vm_one--vg-root   95G   12G   79G  13% /
tmpfs                                       3.0G     0  3.0G   0% /dev/shm
tmpfs                                       5.0M     0  5.0M   0% /run/lock
tmpfs                                       3.0G     0  3.0G   0% /sys/fs/cgroup
tmpfs                                       3.0G     0  3.0G   0% /run/shm


Would virt-sparsify shrink VM_One.qcow2 from ~77G to around ~12G?

If so would the new image VM_One_sparsified.qcow2 if put back into production live would it then continue to grow as normal or is it now stuck to the shrunk size?

Can virt-sparsify be used on a backup image for example ( virt-sparsify VM_One_Backup.qcow2 VM_One_sparsified.qcow2 ) rather than the live / in service virtual machine VM_One.qcow2 ?

Thanks.

---

### Post by TheFu on 2021-12-13
Don't backup the entire OS. Use normal, efficient, backups, just like we use for physical systems.  Backups doing that are much faster and much more efficient.
You can take advantage of the qcow2 snapshot feature, to make things a little easier, but really it would be best to use LVM as the backend storage for all VMs instead. LVM integrates with libvirt nicely. An LV for each VM happens and then we can use LVM snapshots, mount the 100% quiesced snapshot-lv read-only and perform efficient backups using any number of standard backup tool methods.

BTW, it appears you are using LVM inside that VM_One - so you can use LVM snapshots from inside the VM, if that's how you want to go.

Also, would be very helpful if you edited the post above to wrap the df output in code tags so everything lines up.

It appears you broke a cardinal rule with LVM. Only allocate what you need to an LV for the next few months, leaving extra space unused in the VG.  Had you done that, you would likely only have 15G allocated to the LV (/dev/mapper/vm_one--vg-root).
All the other storage in the df output is pseudo-storage - not real.  Use this alias to only show real storage:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

How to fix this?  There are infinite methods.  
What I'd do ... 
[LIST]
[*]I'd create some new storage, 20G or so using virt-manager (libvirt) and connect it to the VM. You'll have both this new 20G and the old 70G+ connected.
[*]Boot an ubuntu "Try Ubuntu" desktop ISO inside this VM ... so I could see the storage. 
[*]Create a new PV, VG, and LV on the new storage. Make the VG name different from whatever is already used. We'll copy over the old files from the old LV there using a smart rsync command. The LV name can still be "root", if you like.  Might be a good time to create "var" and "home" LVs too, if you are so inclined. Different servers may or may not need those other LVs. Up to you.
[*]Format the new LV as ext4. This will be 20G.
[*]Activate the LVM using **vgchange -ay**. This will get all the LVM PV, VG, and LV storage "seen" by the OS so we can do stuff.
[*]Mount the old and new LV for root temporarily under /mnt/old and mnt/new in the live-boot environment.
[*]```
sudo rsync --progress --stats -avz  /mnt/old   /mnt/new
```
[*]This will copy everything as it is, with the owner, group, permissions, acls, over.
[*]Now you have to fix the /mnt/new/etc/fstab to use the new names of the /dev/mapper/... or /dev/{vgname}/{lvname} for the new setup.  The boot partition will need to be moved over too, methinks. I prefer the /dev/{vgname}/{lvname} method over LABEL or UUID or /dev/mapper methods. It provides clear information.
[*]Some other steps are needed based on whether UEFI, encryption, and if you use a swap partition, swap LV, or swapfile ... Basically, If it were me, I'd create a swap LV, use the mkswap command (that's how to format swap), then modify the  /mnt/new/etc/fstab to add the new swap LV location.  All sizing should address the use of swap.  On a server, there is some good reason to have 250MB of swap even if we always allocate plenty of RAM to the VM.  For desktops, I always create 4.1G of swap, period.  Nothing smaller and nothing larger, regardless of RAM. I don't hibernate, but I do suspend.
[/LIST]

---

### Post by TheFu on 2021-12-13
Sparse files cause all sorts of problems for many backup tools.  I've seen a 5MB sparse file explode to 80G in a backup because the tool didn't know what to do with sparse.  rsync and tar have extra options to handle sparse files correctly, but they are not the default. Beware.  I think cp tries to handle sparse files as expected, but it can be confused and explode them too.

In short, using sparse files isn't the solution you probably want.

---

### Post by glued-2-keyboard on 2021-12-14
> **TheFu said:**
> In short, using sparse files isn't the solution you probably want.

Thank you so much for your knowledgeable reply.

If sparse is not the answer then what about **discard='unmap' **?

I verified that **TRIM** is enabled on both the **HOST** and the **GUEST** **VM**.

If I use **virsh edit **to add the **discard='unmap' **option will the size of the **GUEST VM** be reduced when **TRIM** is executed?

And if so does the desired results come from executing **TRIM** on the **HOST** or the **GUEST**?

Thank you again.

---

### Post by TheFu on 2021-12-14
I stopped using sparse files for VMs around 2010. Too many issues.  I vaguely remember some issues related to using trim on any VM storage. Sorry, I don't remember the details.

I've posted in 50+ threads here how to do backups. I use the same methods for VMs as I do for physical servers. Started doing that after my backups of each VM were taking over an hour. It took a little bit, but since the switch, the backups for most VMs take 1-3 minutes and are very storage AND network efficient. I spent months looking for and perfecting the best backup option for my needs in production with client data.  I tried about 10 different solutions before finally getting to the right solution that did the backups, made the restore process crazy flexible - even to 100% new hardware - and efficient. As always, there are trade offs.

Everyone has to come to their own answers. Good luck, if you choose to do something different.

---

### Post by MAFoElffen on 2021-12-14
> **glued-2-keyboard said:**
> 
For example I have VM_One.qcow2

qemu-img info VM_One.qcow2

image: VM_One.qcow2
file format: qcow2
virtual size: 100G (107374182400 bytes)file?
disk size: 77G
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false

Did I hear "sparse files" and 'trim'? RAW is 'sparse'. QCOW2 is, well, sort of a different animal.

On TRIM, if you are going to have a VM around for a while, do a few steps extra to it to save yourself a lot time and effort in the long run. Configure your VM's to automatically trim the deleted files... KVM/QEMU machine types after 2.1 support auto-trim via a discard option. I'll gear this explanation to Virt-Manager... which is also true if your are editing all the domain XML manually. 

Meaning QCOW2 is provisioned as a smaller size than allocated, then grows as the VM disk files are added. Deleted files do not go away (automatically), and are still there until trim'ed. You can use trim to discard the deleted files presence and shrink the size of the actual QCOW2 VM disk file size. Implementing auto-trim in the VM will automatically trim out deleted files, without having to do it manually. 

KVM/QEMU in the Focal Repo's the machine type ais 4.x (so supports it)... So just ensure that in the Domain's XML file, under the <type /> tag where it says "machine=" that the number trailing the BIOS firmware ends in a number greater than 2.1. (But you cannot just pick a random number/ It has to be a valid firmware version that is present.)

It doesn't do 'discard' just through a single option, or switch and work. Some things have to be 'in place' a certain way for to do it from the VM Configuration side... The 'hypervisor default' disk controller will not pass thorugh 'discard'. In the VM config... You need to look at the VM's HDD Controller. If there is one and it is Virtio SCSI, change it from model "hypervisor default" to "VirtIO SCSI". If there is none shown, then add hardware, Storage, Storage Controller, Virtio SCSI, and configure it to model "VirtIO"...

On Disks, Under Advanced, change the Disk Bus type from "VirtIO" to either "SCSI" or "SATA"... Then it can use "discard" to use Trim... Which is turned on by going into the Domain XML and adding this option in red to the disk device line:
```

<devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <source file="/home/mafoelffen/Downloads/ISO/jammy-desktop-amd64.iso"/>
      <target dev="sda" bus="sata"/>
      <readonly/>
      <boot order="2"/>
      <address type="drive" controller="0" bus="0" target="0" unit="0"/>
    </disk>
    <disk type="file" device="disk">
      <driver name="qemu" type="qcow2" cache="writeback" [COLOR=#ff0000]discard="unmap"[/COLOR]/>
      <source file="/var/lib/libvirt/images/Ubuntu22.04Daily.qcow2"/>
      <target dev="sdb" bus="sata"/>
      <boot order="1"/>
      <address type="drive" controller="0" bus="0" target="0" unit="1"/>
    </disk>

```
The above Virtual Hardware config with the VirtIO SCSI controller, and Disk Models will let the discard option pass through the controller and trim the qcow2 VM Disk...

From there you can manually issue an 'fstrim' command, and later, set it up to do it automatically. You can use the 'discard' option in the VM's fstab file, which would trim it each time the VM is booted (when the volume is mounted) or use systemd to do it on a schedule, using service 'fstrim.service' via 'fstrim.timer'... In a datacenter type setting, I prefer it being scheduled, because the VM is going to be up, with not many reboots. For personal VM's, each reboot may be too much, or just enough...
```

mafoelffen@mike-2204:~$ sudo fstrim -a
mafoelffen@mike-2204:~$ sudo systemctl enable fstrim.timer
mafoelffen@mike-2204:~$ sudo systemctl start fstrim.timer
mafoelffen@mike-2204:~$ sudo systemctl status fstrim.timer
\u25cf fstrim.timer - Discard unused blocks once a week
     Loaded: loaded (/lib/systemd/system/fstrim.timer; enabled; vendor preset: >
     Active: active (waiting) since Tue 2021-12-14 14:16:03 PST; 5min ago
    Trigger: Mon 2021-12-20 00:39:08 PST; 5 days left
   Triggers: \u25cf fstrim.service
       Docs: man:fstrim

Dec 14 14:16:03 mike-2204 systemd[1]: Started Discard unused blocks once a week.
lines 1-8/8 (END)

```
Default on fstrim.timer is one week. That can be adjusted in the fstrim.timer service file... Under [noparse]"[Timer] OnCalendar=<interval>"[/noparse]

Just a note on backups... If using rsync, use the --nosparse option or your backups will inflate.

EDIT:
As an example, 22.04 VM Guest after a clean install of 22.04 daily:
```

mafoelffen@Mikes-ThinkPad-T520:/var/lib/libvirt/images$ sudo qemu-img info /var/lib/libvirt/images/Ubuntu22.04Daily.qcow2
image: /var/lib/libvirt/images/Ubuntu22.04Daily.qcow2
file format: qcow2
virtual size: 70 GiB (75161927680 bytes)
[COLOR=#ff0000]disk size: 8.03 GiB[/COLOR]
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false

```
After an applying updates, apt autoremove and apt clean
```

mafoelffen@Mikes-ThinkPad-T520:/var/lib/libvirt/images$ sudo qemu-img info /var/lib/libvirt/images/Ubuntu22.04Daily.qcow2
image: /var/lib/libvirt/images/Ubuntu22.04Daily.qcow2
file format: qcow2
virtual size: 70 GiB (75161927680 bytes)
[COLOR=#ff0000]disk size: 8.31 GiB[/COLOR]
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false

```
After just doing a manual fstrim
```

mafoelffen@Mikes-ThinkPad-T520:/var/lib/libvirt/images$ sudo qemu-img info /var/lib/libvirt/images/Ubuntu22.04Daily.qcow2
image: /var/lib/libvirt/images/Ubuntu22.04Daily.qcow2
file format: qcow2
virtual size: 70 GiB (75161927680 bytes)
[COLOR=#ff0000]disk size: 7.86 GiB[/COLOR]
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false

```
The advantage of doing a Linux guest using fstrim, is that the VM doesn't have to be offline while you are reclaiming host space. virt-sparsify. qemu-img convert, qemu-img shrink, and other methods, the VM has to be offline/shutdown.

---

### Post by TheFu on 2021-12-14
Raw files/images don't have to be sparse.  They can be fully preallocated. 

On non-SSD storage, this makes a major performance difference.  I ran some tests and found it to be over 20% slower using sparse files for VM storage. IT did many different tests on all my different storage devices at the time.  Sometimes it was worse.  With SSD storage, those differences evaporate and it doesn't make sense NOT to use sparse, if using qcow2 for the VM storage container.  I still prefer using LVM for the better management capabilities.

---

### Post by MAFoElffen on 2021-12-14
I do qcow2 as flat virtual sized provisioned disk files, to save space. Let them grow with ticklers to monitor virtual size and percent used. My ticklers are a scheduled script... But I have package " libguestfs-tools" installed, and also use the command virt-df to check the actual space used of my Domain VM disk images from externally. The VM Guest does not even have to be running...

Example
```

sudo virt-df -d Ubuntu22.04Daily -h
#returns
Filesystem                                Size       Used  Available  Use%
Ubuntu22.04Daily:/dev/sda1                3.0G       3.0G          0  100%
Ubuntu22.04Daily:/dev/sda2                4.1M       3.1M       992K   77%
Ubuntu22.04Daily:/dev/sdb1                511M       5.2M       506M    2%
Ubuntu22.04Daily:/dev/vgubuntu/root        67G       6.2G        57G   10%

```
WhereAs:
```

sudo virt-df -h

```
Returns the use stats of every Domain...

My host SSD's, even with SATA SSD, that is not really noticed much. This laptop has 2 x SSD & 1 mSATA. I don't notice it.

Most of the warnings on using 'trim' itself were for Gen1 SSD's when they first came out. What you had to do back then, was to use
```

sudo hdparm -I | grep "TRIM supported"

```
...to ensure the SSD you were using supported 'trim' natively in the firmware.

Things have improved vastly since then on rewrite life on SSD and firmware support. I don't rust the Marketing stat's. I got true and real-work stats from my brother who's company is doing video streaming and video codec compression development for Television Networks> He told me that their datacenter racks are filled with storage modules of over 70 SSD's each, continually doing write/rewrites 24x7, for years. That seemed to ease my early concerns on SSD life. 

But the is physical metal... I am talking about on VM's where the actual VM Disk that your are using trim on are "virtual disk devices". In production, when you started having 100's of VM's provisioned, on good hardware, it doesn't any make sense not to. And for a normal private user, the changes are not that much at all.

The example I post in my last post, that 22.04 Daily VM, is configured with LVM2. You know that I love the heck out of LVM and for myself, feel that is invaluable! LOL. The example showned as manual or scheduled for once a week. True, my laptop is all SSD. But my main VM Host, the VM Host image storage pools are all HHD. For what I do on them, I value the space over the performance gains... which I do not notice much. I could benchmark them... But for what I do, that doesn't matter much. Storage is still fairly cheap, especially compared to what it used to be. 

But my new self-education venture is learning more about provisioning "LVM Thin."

---

### Post by glued-2-keyboard on 2022-02-03
@MAFoElffen & @TheFu Thank you both for your detailed replies.  

Forgive the delay in responding to everyone's posts.  Life has been a little complicated and finding time to even breath has become a task.  

Thought I would provide a little more output and try to simplify my question.

> **MAFoElffen]Just a note on backups... If using rsync, use the --nosparse option or your backups will inflate.[/QUOTE]

Are you saying rsync will copy VM_One.qcow2 so that the backup is the USED size and not the AVAILABLE or SIZED sized?

[QUOTE=MAFoElffen said:**
> use the command virt-df to check the actual space used

From the HOST running virt-df -h

```
Filesystem                             Size       Used  Available  Use%
VM_One:/dev/vm_one-vg/root              95G        11G        79G   12%
VM_Two:/dev/vm_two-vg/root              90G       9.3G        76G   11%
```

running sudo systemctl status fstrim.timer produces

```
&#9679; fstrim.timer - Discard unused blocks once a week
   Loaded: loaded (/lib/systemd/system/fstrim.timer; enabled; vendor preset: enabled)
   Active: active (waiting) since Thu 2022-02-03 13:08:17 EST; 2h 20min ago
  Trigger: Mon 2022-02-07 00:00:00 EST; 3 days left
     Docs: man:fstrim

Feb 03 13:08:17 vm_one systemd[1]: Started Discard unused blocks once a week.
```

From the HOST running df -h

```

Filesystem                     Size  Used Avail Use% Mounted on
udev                            16G     0   16G   0% /dev
tmpfs                          3.2G  1.4M  3.2G   1% /run
/dev/mapper/host--vg-root  411G  121G  270G  31% /
tmpfs                           16G     0   16G   0% /dev/shm
tmpfs                          5.0M  4.0K  5.0M   1% /run/lock
tmpfs                           16G     0   16G   0% /sys/fs/cgroup
tmpfs                           16G     0   16G   0% /run/shm
/dev/sda1                   880G   78G  758G  10% /vm_pool_1
/dev/sdb1                   880G   33G  803G   4% /vm_pool_2
tmpfs                          3.2G     0  3.2G   0% /run/user/0
```


From the VM_One running df -h

```

Filesystem                    Size  Used Avail Use% Mounted on
udev                          2.9G     0  2.9G   0% /dev
tmpfs                         597M  736K  596M   1% /run
/dev/mapper/vm_one-vg-root        95G   11G   80G  13% /
tmpfs                         3.0G     0  3.0G   0% /dev/shm
tmpfs                         5.0M     0  5.0M   0% /run/lock
tmpfs                         3.0G     0  3.0G   0% /sys/fs/cgroup
tmpfs                         3.0G     0  3.0G   0% /run/shm

```


The actual qcow2 file sizes seem to be growing but not decreasing in size.  I feel like I am going in circles at this point so please forgive me.

ls - lth

```

101G Feb  3 16:33 /vm_pool_2/kvm_guests/vm_two.qcow2
  79G Feb  3 16:32 /vm_pool_1/kvm_guests/vm_one.qcow2

```

---

### Post by TheFu on 2022-02-03
There is a tool called qemu-img that you'll find helpful. It has a full manpage which explains what it can do. Be certain to check the stuff about sparse, if you use sparse options.

I found the performance of storage with sparse on HDDs (spinning rust) to be noticeably slower than passing in a block device or using a fully pre-allocated device. If the backing storage is SSD (either SATA or NVMe), then sparse files are fast enough not to impact typical performance, but I still prefer passing in block devices (LVM2 LVs) for each VM for better management and cleaner backups.

---

### Post by MAFoElffen on 2022-02-04
I still agree and go with TheFu on the the original methodology, how and procedure of... Full images are okay, but take forever to do, and to restore.

I cannot speak for TheFu, but I do not understand why some want to treat VM's a files, rather than as just another computer, when it comes to backups. This is finally taking hold on VM Host Management Systems. Whereas, both of us have been saying this for years. If treated as a live machine in that respect, then backup what is important, and what changes. 

I don't understand always taking full disk images as your only backups, again and again. When you can take scheduled images, then in between those, Intermittent changes... to quickly get that image to a point in time where you want to be.Using the same methodology. you could then get a fresh install, to a point in time finished picture.

This is the same basic methodology of how to do migrations. And how TheFu has mentioned he has gotten his own migrations down to about 20 minutes... We both agree on that methodology. It just make sense.

---

