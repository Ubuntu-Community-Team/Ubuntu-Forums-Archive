---
title: "Xen crashes entire server when creating a virtual machine"
date: 2016-06-25
forum: Virtualisation
---

### Post by Mikael_Niemel on 2016-06-25
Looks like my Xen problems aren't over. When I try to create a Xen virtual machine, I get a bunch of ATA related errors, and after that the entire server crashes and/or reboots.

Here's the first message, I wasn't even able to save any logs, so I had to manually take a pic of them before the server rebooted.. :(

```
ata9: illegal qc_active transition (0001c000->0000bfff)
```

After that I got a bunch of

```
ata<x>.00: failed command: READ FPDMA QUEUED
```

Amongst the errors there also was a

```
ata<x>.00: PCI err cause 0x9ca634e3
```



Anyways, I'm trying to use a ZFS volume in Dom0 for VM storage, should it be okay for Xen?

---

### Post by MAFoElffen on 2016-06-26
You have said Xen and ZFS... But I see an incomplte picture.

What is the OS and version of, that you have Xen running on? What is your version of Xen. Are you suing the newer kernel module or FUSE for ZFS? Is this error on your host or guest? If on a guest, what is the OS and verson of the guest?

Here is why I ask those-- The times I've seen that error was either on iron, when SATA first cam out, and when the nwer SATA drives came out... and controllers where having issues reading the nwer drives. The other times I've seen this error under a hypervisor, is when there was a PCI passthrough and there was a problem with the passthrough...

So please explain the circumstances surrounding your system and the errors.

EDIT-- 
Depending on how, which implementation of the ZFS interface, etc... I have no issues with ZFS. I've used ZFS for over about 9-10 years. I've run Ubuntu on ZFS on metal with no issues. I've run Ubuntu on  ZFS in KVM with no issues. I can't say I've run Ubuntu on ZFS in any of my Xen Server, but I can say Solaris on ZFS in Xen has no issues on any on my Xen Servers.

---

### Post by Mikael_Niemel on 2016-06-26
[FONT=arial]I'm using Ubuntu 16.04 for host, kernel version is 4.4.0-24-generic. I installed ZFS just by doing ```
[COLOR=#333333]sudo apt install zfs[/COLOR]
```[COLOR=#333333], if I understood correctly, that means the new kernel module. Without Xen DomUs running, ZFS has been working just fine in Ubuntu.

Also, this error is on host, not on guest, which is Ubuntu 14.04 LTS. No errors are seen on guest before the system crashes, and I haven't set up PCI passthrough either. Xen version is 4.6.0.

I'm using a AOC-SAT-MV8 controller to connect my S-ATA drives for ZFS array, but my OS disk (a SSD) is on a MB S-ATA port. I'll check if this happens on a cheapo Sil3124 controller, though I have had other problems with it.[/COLOR][/FONT]

---

### Post by MAFoElffen on 2016-06-26
You know, funny you should mention that (Xen and S-ATA). I've seen a few problems lately from users using Xen with S-ATA as being the culprits. I think the most recent was in this Virtualization Section, started about week ago. So a coincidence that you mention that. 

Look at this thread, page 2. posts 18 & 19: [http://ubuntuforums.org/showthread.php?t=2326179](http://ubuntuforums.org/showthread.php?t=2326179) It is now solved (was related to S-ATA) and I'm now workig out a few details on a side question with him. It was not related to ZFS. It was just Xen and S-ATA.

I tested the ZFS modules during the last 2 dev cycles and it is so much better than the previous fuse implementation. It tested out fine for me. I don't suspect ZFS itself, but I didn't test it with S-ATA and Xen. Admittedly, I used LVM on hardware RAID on my KVM and Xen Servers.

---

### Post by Mikael_Niemel on 2016-06-26
> **MAFoElffen said:**
> You know, funny you should mention that (Xen and S-ATA). I've seen a few problems lately from users using Xen with S-ATA as being the culprits. I think the most recent was in this Virtualization Section, started about week ago. So a coincidence that you mention that. 

Look at this thread, page 2. posts 18 & 19: [http://ubuntuforums.org/showthread.php?t=2326179](http://ubuntuforums.org/showthread.php?t=2326179) It is now solved (was related to S-ATA) and I'm now workig out a few details on a side question with him. It was not related to ZFS. It was just Xen and S-ATA.

I tested the ZFS modules during the last 2 dev cycles and it is so much better than the previous fuse implementation. It tested out fine for me. I don't suspect ZFS itself, but I didn't test it with S-ATA and Xen. Admittedly, I used LVM on hardware RAID on my KVM and Xen Servers.

Umm, that linked thread is my previous thread, which was about Xen not even booting to Dom0 (I started a new thread as this seemed like a new issue). It turned out that it didn't recognize old IDE disks (and the Ubuntu instance was on a IDE HDD), but it booted fine to Dom0 when I re-installed the instance to a S-ATA disk.

---

### Post by MAFoElffen on 2016-06-27
LOL, sorry... So it is *really* still having troubles along the same line then. 

I've been looking at that limiting to 32 bit guests with the newer XenLight Toolset for you. That has me been driving me batty. While a DomU is running or active (but stopped), I can see the xml and json for it. Before that,, well, it has to be stored somewhere, but I haven't found where yet.

In the xml, it's linked to the os type equals i686, where it you did 
```

sudo virsh edit DomainName

```
It would then change that... but had family things this weekend, so not a lot of time. In the json, I can see it affects with version of the kernel it is using to virtualize the Dom. But since I can't figure out where it is storing the config itself, in it's own internal format, I can't see what the change is, to be able to change the default xl.conf. But still chasing that.

But you are saying you are still getting I/O errors. You said journalctl doesn't work for you? With dmesg, can you tell if is it getting the errors on the physical disk, or on the filesystem? Is there sensitive data in it where that would preclude posting a filtered result to ubuntu.pastebin.com? Like pm me the link, so the world does not have to get access to it?

EDIT#1--
I didn't ask in the other thread, what is the spec's of you server. Wondering the cpu, memory, etc. and version of Xen.

Sidenote-- Mine is Xen version 4.6 on 16.04. I am not without any errors. It seems to want to lose the cursor on a Windows 2016 preview 5 DomU in some viewers, if I switch between windows (it loses focus, then gets focus again).

EDT#2--
I told you I was using LVM. Are you using pools for your DomU Domain/Guest or creating images files? One way of creating DomU's is to create and LVM Volume Group, then install the DomU to that Volume Group. For that to happen, the Volume Group has to pre-exist. I was wondoering if you were trying to to the same logical method using ZFS (something I have never tried, but I don't see why it wouldn't work in the same manner).

If to it's own ZFS pools, then may be more of a logic error, were it is trying to write to something it can't fully find? Just thinking out loud.

So have you been able to successfully create any DomU on your new Xen install yet?

EDIT#3--
So 3 years ago, when it was still Fuse ZFSonLinux... Users on the Xen User Mail List said the ZFS pool  had to pre-exist. There was a problem with creation directly one ZFS, so they had this work-around:
> 
The procedure I followed is: 
0) set options in /etc/xen-tools/xen-tools.conf 
```

        dir = /home/xen/ 
        fs     = ext3 
        image  = sparse 

```
1) create DomU eg: 
```

xen-create-image --hostname vitrualM --memory=8gb --dhcp --vcpus 2 --pygrub --dist wheezy 

```
this creates volumes in /home/xen/domains/virtualM/ 
```

disk.img 
swap.img 

```
2) create zvol, eg: 
```

zfs create -V 100G zpool1/vitrualM 

```
3) use dd to copy over image to zvol: 
```

dd if=/home/xen/domains/vitrualM/disk.img of=/dev/zvol/zpool1/vitrualM bs=1M 

```
4) set DomU config to point to new location of image: 
```

'phy:/dev/zvol/zpool1/vitrualM,xvda2,w', 

```

I haven't confirmed this, but ... I'm suspecting that now-a-days, with the ZFS support now in the newer kernel, that if you declared the new zvol, then pointed the create statement to that zvol... that it may write it directly to that zvol. If not, then there is still that old work-around.

Using the above example, with LVM you would use 
```

xen-create-image --hostname vitrualM --memory=8gb --dhcp --vcpus 2 --pygrub --dist wheezy --image full --lvm my--vg--virtualM

```
I know that when using LVM, that you pre-define, and that these options are important:
```

 &#8722;&#8722;image   Specify whether to create "sparse" or "full" disk images. Full images are mandatory when using LVM, so this setting
 &#8722;&#8722;dir   Specify where the output images should go. Subdirectories will be created for each guest. If you do not wish to use loopback images specify &#8722;&#8722;lvm or &#8722;&#8722;evms.  (These three options are mutually exclusive.)
 &#8722;&#8722;lvm   Specify the volume group to save images within. If you do not wish to use LVM specify &#8722;&#8722;dir or &#8722;&#8722;evms. (These three options are mutually exclusive.)
 &#8722;&#8722;evms   Specify the container to save images within, i.e. &#8217;&#8722;&#8722;evms lvm2/mycontainer&#8217;.  If you do not wish to use EVMS specify &#8722;&#8722;dir or &#8722;&#8722;lvm.  (These three options are mutually exclusive.)

```
So, for a pre-defined zvol, I see it as possibly (guess) being something like
```

xen-create-image --hostname vitrualM --memory=8gb --dhcp --vcpus 2 --pygrub --dist wheezy --image full --dir /Path_To/New_ZVol/vitrualM

```
But that might also be via evms. If creating new domains from config files, then are you directly pointing the config to a pre-deined  zvol?

---

### Post by Mikael_Niemel on 2016-07-04
I have been a bit busy for some days, but I'm now back again..

> **MAFoElffen said:**
> LOL, sorry... So it is *really* still having troubles along the same line then. 

I've been looking at that limiting to 32 bit guests with the newer XenLight Toolset for you. That has me been driving me batty. While a DomU is running or active (but stopped), I can see the xml and json for it. Before that,, well, it has to be stored somewhere, but I haven't found where yet.

In the xml, it's linked to the os type equals i686, where it you did 
```

sudo virsh edit DomainName

```
It would then change that... but had family things this weekend, so not a lot of time. In the json, I can see it affects with version of the kernel it is using to virtualize the Dom. But since I can't figure out where it is storing the config itself, in it's own internal format, I can't see what the change is, to be able to change the default xl.conf. But still chasing that.


Hmm, it says that command virsh isn't found when I try that..

> **MAFoElffen said:**
> But you are saying you are still getting I/O errors. You said journalctl doesn't work for you? With dmesg, can you tell if is it getting the errors on the physical disk, or on the filesystem? Is there sensitive data in it where that would preclude posting a filtered result to ubuntu.pastebin.com? Like pm me the link, so the world does not have to get access to it?

EDIT#1--
I didn't ask in the other thread, what is the spec's of you server. Wondering the cpu, memory, etc. and version of Xen.

Sidenote-- Mine is Xen version 4.6 on 16.04. I am not without any errors. It seems to want to lose the cursor on a Windows 2016 preview 5 DomU in some viewers, if I switch between windows (it loses focus, then gets focus again).


Thing is that when the errors appear, the entire server crashes or reboots before I can save the errors anywhere. The only way I was able to get some dmesg logs out was by taking a picture of the errors.

Anyways, my Xen is version 4.6 on ubuntu 16.04 as well. My server motherboard is a Tyan Thunder K8WE with two Opteron 275 CPUs and 24Gb memory.




> **MAFoElffen said:**
> EDT#2--
I told you I was using LVM. Are you using pools for your DomU Domain/Guest or creating images files? One way of creating DomU's is to create and LVM Volume Group, then install the DomU to that Volume Group. For that to happen, the Volume Group has to pre-exist. I was wondoering if you were trying to to the same logical method using ZFS (something I have never tried, but I don't see why it wouldn't work in the same manner).

If to it's own ZFS pools, then may be more of a logic error, were it is trying to write to something it can't fully find? Just thinking out loud.

So have you been able to successfully create any DomU on your new Xen install yet?

I have been trying to use ZFS volumes created to the single ZFS pool I have in the system. I basically created a ZFS volume to my pool by

```
**zfs create -V 20gb data/testserver**
```

Then I set that volume as the disk to the Xen config file, it's path was "/dev/zvol/data/testserver".


Anyways, I'll try to use file based storage for DomU and see if that works.. Now the install of guest system is going on with no errors.. yet.

EDIT: No luck, it still crashes even when using file based storage. Next I'll try disabling ZFS and using a file on my OS disk..

EDIT2: Nope, it still doesn't work, so it shouldn't be about ZFS. So looks like I'm not able to successfully create any DomU..

---

### Post by MAFoElffen on 2016-07-04
> **Mikael_Niemel said:**
> 
Anyways, my Xen is version 4.6 on ubuntu 16.04 as well. My server motherboard is a Tyan Thunder K8WE with two Opteron 275 CPUs and 24Gb memory.

LOL! Very small world! I have an old Test Server that is Tyan K8SE S2892G3NR. I  have a spare board that box, that is a ASUS K8N-DRE. So Both are a few moths older than yours, but not by much. Both my Boards use the same Opteron Series 200 processors as yours. So yes, I am familiar with your hardware. I think the main different between the series I have and yours, was that your did SLI.

Now I understand some of your configuration considerations.On those boards, we have socket 940 and Opteron 200 series. AMD-v didn't come out until later with "Paifica" and Socket F processors, like the Opteron 2000 series.. So no iommu on those.

No no idea? That board has BIOS server logs a irght? No messages there? Then, Xen server does journalctl journaling... but you said yours does not right? Cause if you turned on persistent journaling, then you would have the system log of that crash... 

Just thinking out loud. I guess my old test server is similar to yours to slap together for a Xen test with ZFS... I need to get a few other things done before I could do that. But if need be, at least it's there and available.

---

### Post by Mikael_Niemel on 2016-07-04
I checked again logs with journalctl, and now it actually had logs in it. IIRC it didn't initially work, but I'm not sure if I have just been brainfarting or something.. :redface:[CENTER][COLOR=#000000]
[/COLOR][/CENTER]
Anyways, here's what I got from it this time, I'm really sorry that it took so long for me to get some useful data for solving this..

```
heinä 04 18:52:54 ruoska kernel: BUG: unable to handle kernel paging request at ffffc910436df210heinä 04 18:52:54 ruoska kernel: IP: [<ffffffffc034a441>] xenvif_kthread_guest_rx+0x4e1/0xa20 [xen_netback]
heinä 04 18:52:54 ruoska kernel: PGD 1f6fac067 PUD 0 
heinä 04 18:52:54 ruoska kernel: Oops: 0000 [#1] SMP 
heinä 04 18:52:54 ruoska kernel: Modules linked in: xt_physdev br_netfilter iptable_filter ip_tables x_tables xen_netback xen_blkback xen_gntdev xen_evtchn xenfs xen_privcmd ppdev bridge stp llc input_leds serio_raw k8temp edac_mce_amd edac_core shpchp parport_pc 8250_fintek parport i2c_nforce2 mac_hid ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear pata_acpi e1000 sata_mv sata_nv pata_amd fjes
heinä 04 18:52:54 ruoska kernel: CPU: 3 PID: 1788 Comm: vif1.0-q0-guest Not tainted 4.4.0-28-generic #47-Ubuntu
heinä 04 18:52:54 ruoska kernel: Hardware name: TYAN Computer Corp. S2895/S2895, BIOS 2004Q3 11/18/2008
heinä 04 18:52:54 ruoska kernel: task: ffff88022271cb00 ti: ffff88021d91c000 task.ti: ffff88021d91c000
heinä 04 18:52:54 ruoska kernel: RIP: e030:[<ffffffffc034a441>]  [<ffffffffc034a441>] xenvif_kthread_guest_rx+0x4e1/0xa20 [xen_netback]
heinä 04 18:52:54 ruoska kernel: RSP: e02b:ffff88021d91fdf8  EFLAGS: 00010286
heinä 04 18:52:54 ruoska kernel: RAX: ffffc910436aa000 RBX: ffffc9004372c9d8 RCX: 0000000000000001
heinä 04 18:52:54 ruoska kernel: RDX: 00000000ffff8800 RSI: 0000000000000000 RDI: 0000000000000005
heinä 04 18:52:54 ruoska kernel: RBP: ffff88021d91fec0 R08: 000000000000062a R09: ffff880005a94840
heinä 04 18:52:54 ruoska kernel: R10: ffffc90043722000 R11: ffffc9004372c9d8 R12: 0000000000000000
heinä 04 18:52:54 ruoska kernel: R13: 0000000000000000 R14: ffffc90043722000 R15: ffff88021d91fe3c
heinä 04 18:52:54 ruoska kernel: FS:  00007f3a077ed700(0000) GS:ffff880229f80000(0000) knlGS:0000000000000000
heinä 04 18:52:54 ruoska kernel: CS:  e033 DS: 0000 ES: 0000 CR0: 000000008005003b
heinä 04 18:52:54 ruoska kernel: CR2: ffffc910436df210 CR3: 00000000cce0c000 CR4: 0000000000000660
heinä 04 18:52:54 ruoska kernel: Stack:
heinä 04 18:52:54 ruoska kernel:  ffff88021d91fe3c ffff88022271cb00 ffff880229e96d00 ffffc90043757208
heinä 04 18:52:54 ruoska kernel:  ffff880005a94840 ffffc9004372ca00 ffffc9004372c9d8 ffff880200000003
heinä 04 18:52:54 ruoska kernel:  0000000000000000 ffff88021d91fe40 ffff88021d91fe40 ffff88021ee35e00
heinä 04 18:52:54 ruoska kernel: Call Trace:
heinä 04 18:52:54 ruoska kernel:  [<ffffffff81827a4f>] ? ret_from_fork+0x3f/0x70
heinä 04 18:52:54 ruoska kernel:  [<ffffffff810a0730>] ? kthread_create_on_node+0x1e0/0x1e0
heinä 04 18:52:54 ruoska kernel: Code: 48 c7 03 00 00 00 00 48 c7 43 08 00 00 00 00 48 89 42 08 48 89 10 8b 45 b4 4d 8b 4e 20 48 89 c2 48 c1 e0 04 41 8b 71 28 4c 01 f0 <8b> 88 10 52 03 00 0f a3 ce 73 5a 41 8b 8e c0 a9 00 00 49 8b be 
heinä 04 18:52:54 ruoska kernel: RIP  [<ffffffffc034a441>] xenvif_kthread_guest_rx+0x4e1/0xa20 [xen_netback]
heinä 04 18:52:54 ruoska kernel:  RSP <ffff88021d91fdf8>
heinä 04 18:52:54 ruoska kernel: CR2: ffffc910436df210
heinä 04 18:52:54 ruoska kernel: ---[ end trace c3c7b08cf215a43c ]---
heinä 04 18:52:54 ruoska kernel: BUG: unable to handle kernel NULL pointer dereference at           (null)
heinä 04 18:52:54 ruoska kernel: IP: [<ffffffffc03490ea>] xenvif_rx_queue_tail+0x3a/0xa0 [xen_netback]



```

---

### Post by MAFoElffen on 2016-07-05
You know, I'm really surprised that the Xen Kernel starts. The first thing that the requirements says is to test for IOMMU and that virtualization is turned on, which I know those CPU's where not capable of. So lets see what you have and what it is capable of... You would not be ablle to run an HVM guest, which leaves running a PV host.
> 
PV

Paravirtualization (PV) is an efficient and lightweight virtualization technique originally introduced by Xen Project, later adopted by other virtualization platforms. [COLOR=#ff0000]PV does not require virtualization extensions from the host CPU.[/COLOR] However, paravirtualized guests require a PV-enabled kernel and PV drivers, so the guests are aware of the hypervisor and can run efficiently without emulation or virtual emulated hardware. PV-enabled kernels exist for Linux, NetBSD, FreeBSD and OpenSolaris. Linux kernels have been PV-enabled from 2.6.24 using the Linux pvops framework. In practice this means that PV will work with most Linux distributions (with the exception of very old versions of distros).

I looked at the error and the specific dump had to do with brctl virtualizing networking, which might have to do with vt-d capabilities being not there. Which, was the module load on the Xen backend... on virtulaization modules...Which isn't going to be possible on a non-iommu cpu... but I don't know that bridge itself is HVM. Bridge can still happen with PV. However, more complex virt networking cannot.

I found the error: [https://lists.xenproject.org/archives/html/xen-users/2013-04/msg00453.html](https://lists.xenproject.org/archives/html/xen-users/2013-04/msg00453.html)
 So, being limited to a fully paravirtulized DomU, did you, by mistake, use an HVM templete, instead of an PV template?

[PV fully virtualized configuration options]("http://xenbits.xen.org/docs/unstable/man/xl.cfg.5.html#paravirtualised__pv__guest_specific_options")

---

### Post by Mikael_Niemel on 2016-07-05
I copied the xlexample.pvlinux file and modified it. Here's my modified config file:

```
# =====================================================================
# Example PV Linux guest configuration
# =====================================================================
#
# This is a fairly minimal example of what is required for a
# Paravirtualised Linux guest. For a more complete guide see xl.cfg(5)

# Guest name
name = "Dom4Server"
arch = "i686"

# 128-bit UUID for the domain as a hexadecimal number.
# Use "uuidgen" to generate one if required.
# The default behavior is to generate a new UUID each time the guest is started.
#uuid = "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"

# Kernel image to boot
kernel = "/var/lib/xen/images/ubuntu-netboot/trusty14LTS/vmlinuz"
ramdisk = "/var/lib/xen/images/ubuntu-netboot/trusty14LTS/initrd.gz"

# Ramdisk (optional)
#ramdisk = "/boot/initrd.gz"

# Kernel command line options
extra = "root=/dev/xvda1"

# Initial memory allocation (MB)
memory = 2048

# Maximum memory (MB)
# If this is greater than `memory' then the slack will start ballooned
# (this assumes guest kernel support for ballooning)
#maxmem = 512

# Number of VCPUS
vcpus = 1

# Network devices
# A list of 'vifspec' entries as described in
# docs/misc/xl-network-configuration.markdown
vif = [ '' ]

# Disk Devices
# A list of `diskspec' entries as described in
# docs/misc/xl-disk-configuration.txt
disk = [ '/etc/xen/dom4server.img,raw,xvda,rw' ]


```

Unless I'm mistaken, this should be a PV config..

---

### Post by MAFoElffen on 2016-07-06
I think arch in an XL type of cinfig file detects the arch from whatever the installed OS is. so you have to be careful on what is installed. So not a vailid option as you put there. That is if you had an XML styled config file.

Other pv options: (from [http://xenbits.xen.org/docs/unstable/man/xl.cfg.5.html#Paravirtualised-PV-Guest-Specific-Options](http://xenbits.xen.org/docs/unstable/man/xl.cfg.5.html#Paravirtualised-PV-Guest-Specific-Options) )
> 
Paravirtualised (PV) Guest Specific Options

The following options apply only to Paravirtual guests.

bootloader="PROGRAM"
Run PROGRAM to find the kernel image and ramdisk to use. Normally PROGRAM would be pygrub, which is an emulation of grub/grub2/syslinux. Either kernel or bootloader must be specified for PV guests.

bootloader_args=[ "ARG", "ARG", ...]
Append ARGs to the arguments to the bootloader program. Alternatively if the argument is a simple string then it will be split into words at whitespace (this second option is deprecated).

e820_host=BOOLEAN
Selects whether to expose the host e820 (memory map) to the guest via the virtual e820. When this option is false (0) the guest pseudo-physical address space consists of a single contiguous RAM region. When this option is specified the virtual e820 instead reflects the host e820 and contains the same PCI holes. The total amount of RAM represented by the memory map is always the same, this option configures only how it is laid out.

Exposing the host e820 to the guest gives the guest kernel the opportunity to set aside the required part of its pseudo-physical address space in order to provide address space to map passedthrough PCI devices. It is guest Operating System dependent whether this option is required, specifically it is required when using a mainline Linux ("pvops") kernel. This option defaults to true (1) if any PCI passthrough devices are configured and false (0) otherwise. If you do not configure any passthrough devices at domain creation time but expect to hotplug devices later then you should set this option. Conversely if your particular guest kernel does not require this behaviour then it is safe to allow this to be enabled but you may wish to disable it anyway.

pvh=BOOLEAN
Selects whether to run this PV guest in an HVM container. Default is 0.

But I didn't see anyhting obvious that would be loading HVM drivers.

---

### Post by Mikael_Niemel on 2016-07-18
Hmm, do you still have any suggestions about how to continue with this?

Also, it's weird that sometimes the DomU installation progressed quite far and it downloaded setup files from internet, and sometimes it crashed pretty early in the setup..

---

### Post by MAFoElffen on 2016-07-18
Let me sleep on this. I have 2 servers to upgrade here. Once I do, then I'll take my server that is similar to your server board and install Xen on the hardware. That way maybe i can recreate your problem. 

But like I said, I need to get those 2 back up first... and I'm waiting on one part to get here for the second of the two.

Are you creating the DomU from the commandline? If so, then post that, so I can create the same.

EDIT: 
Status-- One server back online. Next server still waiting on it's part, which should get here the 22nd.

---

### Post by Mikael_Niemel on 2016-07-19
Yes, I created the DomU from command line with this command

```
sudo xl create -c /etc/xen/dom4server.cfg
```

where the file is the config file listed earlier.

---

### Post by Mikael_Niemel on 2016-07-19
Looks there more weird stuff going on. When I was trying to copy stuff to my samba share with just Dom0 running, I got errors like these:


```
heinä 19 21:58:29 ruoska kernel: BUG: unable to handle kernel paging request at ffff88007ff80000heinä 19 21:58:29 ruoska kernel: IP: [<ffffffff813fe01e>] do_csum+0x7e/0x170
heinä 19 21:58:29 ruoska kernel: PGD 1e0b067 PUD 1f9c46067 PMD 1f9a46067 PTE 0
heinä 19 21:58:29 ruoska kernel: Oops: 0000 [#1] SMP 
heinä 19 21:58:29 ruoska kernel: Modules linked in: xen_gntdev xen_evtchn xenfs xen_privcmd zfs(PO) zunicode(PO) zcommon(PO) znvpair(PO) spl(O) zavl(PO) ppdev bridge stp llc serio_raw edac_mce_amd shpchp k8temp edac_core parport_pc parport 8250_fintek i2c_nforce2 mac_hid ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear pata_acpi e1000 sata_mv sata_nv pata_amd fjes
heinä 19 21:58:29 ruoska kernel: CPU: 0 PID: 2893 Comm: smbd Tainted: P           O    4.4.0-31-generic #50-Ubuntu
heinä 19 21:58:29 ruoska kernel: Hardware name: TYAN Computer Corp. S2895/S2895, BIOS 2004Q3 11/18/2008
heinä 19 21:58:29 ruoska kernel: task: ffff88021f581900 ti: ffff8800ab280000 task.ti: ffff8800ab280000
heinä 19 21:58:29 ruoska kernel: RIP: e030:[<ffffffff813fe01e>]  [<ffffffff813fe01e>] do_csum+0x7e/0x170
heinä 19 21:58:29 ruoska kernel: RSP: e02b:ffff8800ab283a90  EFLAGS: 00010286
heinä 19 21:58:29 ruoska kernel: RAX: 8c121bd87fe9fd90 RBX: 0000000000000000 RCX: 0000000000000000
heinä 19 21:58:29 ruoska kernel: RDX: ffff880096d446a8 RSI: 000000002214a7fa RDI: ffff88007ff7ffe8
heinä 19 21:58:29 ruoska kernel: RBP: ffff8800ab283a90 R08: 0000000000000000 R09: 00000000044294ff
heinä 19 21:58:29 ruoska kernel: R10: 0000000000000000 R11: 0000000254289cfa R12: 000000002214a800
heinä 19 21:58:29 ruoska kernel: R13: 000000002214a800 R14: ffff880215b3a608 R15: 0000000000000000
heinä 19 21:58:29 ruoska kernel: FS:  00007f51201258c0(0000) GS:ffff880229e00000(0000) knlGS:0000000000000000
heinä 19 21:58:29 ruoska kernel: CS:  e033 DS: 0000 ES: 0000 CR0: 000000008005003b
heinä 19 21:58:29 ruoska kernel: CR2: ffff88007ff80000 CR3: 00000000aecf1000 CR4: 0000000000000660
heinä 19 21:58:29 ruoska kernel: Stack:
heinä 19 21:58:29 ruoska kernel:  ffff8800ab283aa8 ffffffff813fe151 ffff880215c2d900 ffff8800ab283ab8
heinä 19 21:58:29 ruoska kernel:  ffffffff8170d869 ffff8800ab283b28 ffffffff8170fb75 0000000000000000
heinä 19 21:58:29 ruoska kernel:  0000000000000000 000000018010000c ffff880215c2d900 2214a800d15796ef
heinä 19 21:58:29 ruoska kernel: Call Trace:
heinä 19 21:58:29 ruoska kernel:  [<ffffffff813fe151>] csum_partial+0x11/0x20
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8170d869>] csum_partial_ext+0x9/0x10
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8170fb75>] __skb_checksum+0x65/0x2d0
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8170fe15>] skb_checksum+0x35/0x50
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8170d860>] ? skb_panic+0x70/0x70
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8170d0a0>] ? reqsk_fastopen_remove+0x170/0x170
heinä 19 21:58:29 ruoska kernel:  [<ffffffff81715b42>] __skb_checksum_complete+0x22/0xd0
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8177b30f>] tcp_rcv_established+0x18f/0x780
heinä 19 21:58:29 ruoska kernel:  [<ffffffff81786165>] tcp_v4_do_rcv+0x145/0x200
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8170a5c5>] release_sock+0x95/0x160
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8176f73c>] tcp_recvmsg+0x3fc/0xbe0
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8179d87e>] inet_recvmsg+0x7e/0xb0
heinä 19 21:58:29 ruoska kernel:  [<ffffffff81705eab>] sock_recvmsg+0x3b/0x50
heinä 19 21:58:29 ruoska kernel:  [<ffffffff81705f52>] sock_read_iter+0x92/0xe0
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8120ca3c>] do_iter_readv_writev+0x6c/0xa0
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8120d5bf>] do_readv_writev+0x18f/0x230
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8120d696>] vfs_readv+0x36/0x50
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8120e329>] SyS_readv+0x59/0xf0
heinä 19 21:58:29 ruoska kernel:  [<ffffffff8182db32>] entry_SYSCALL_64_fastpath+0x16/0x71
heinä 19 21:58:29 ruoska kernel: Code: d1 c1 ea 04 41 d1 e9 85 d2 0f 84 06 01 00 00 83 ea 01 45 31 c0 48 83 c2 01 48 c1 e2 06 48 01 fa 48 03 07 48 13 47 08 48 13 47 10 <48> 13 47 18 48 13 47 20 48 13 47 28 48 13 47 30 48 13 47 38 4c 
heinä 19 21:58:29 ruoska kernel: RIP  [<ffffffff813fe01e>] do_csum+0x7e/0x170
heinä 19 21:58:29 ruoska kernel:  RSP <ffff8800ab283a90>
heinä 19 21:58:29 ruoska kernel: CR2: ffff88007ff80000


heinä 19 21:58:29 ruoska kernel: ---[ end trace 0fb3718651e29e0f ]---
```




```
heinä 19 22:06:24 ruoska kernel: NMI watchdog: BUG: soft lockup - CPU#1 stuck for 23s! [smbd:2957]heinä 19 22:06:24 ruoska kernel: Modules linked in: xen_gntdev xen_evtchn xenfs xen_privcmd zfs(PO) zunicode(PO) zcommon(PO) znvpair(PO) spl(O) zavl(PO) ppdev bridge stp llc serio_raw edac_mce_amd shpchp k8temp edac_core parport_pc parport 8250_fintek i2c_nforce2 mac_hid ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear pata_acpi e1000 sata_mv sata_nv pata_amd fjes
heinä 19 22:06:24 ruoska kernel: CPU: 1 PID: 2957 Comm: smbd Tainted: P      D    O    4.4.0-31-generic #50-Ubuntu
heinä 19 22:06:24 ruoska kernel: Hardware name: TYAN Computer Corp. S2895/S2895, BIOS 2004Q3 11/18/2008
heinä 19 22:06:24 ruoska kernel: task: ffff8800cd21cb00 ti: ffff880185e5c000 task.ti: ffff880185e5c000
heinä 19 22:06:24 ruoska kernel: RIP: e030:[<ffffffff81723091>]  [<ffffffff81723091>] napi_gro_flush+0x21/0x80
heinä 19 22:06:24 ruoska kernel: RSP: e02b:ffff880229e83db8  EFLAGS: 00000286
heinä 19 22:06:24 ruoska kernel: RAX: ffff8801fc6a6000 RBX: ffff88021dcc8af0 RCX: ffff88022223f000
heinä 19 22:06:24 ruoska kernel: RDX: ffff8801fc6a6000 RSI: 0000000000000000 RDI: ffff8801fc6a6000
heinä 19 22:06:24 ruoska kernel: RBP: ffff880229e83dd0 R08: 0000000000000002 R09: 0000000000000000
heinä 19 22:06:24 ruoska kernel: R10: ffff8801fa5d1ec0 R11: 000000001917ff00 R12: ffff88021dcc8af0
heinä 19 22:06:24 ruoska kernel: R13: 0000000000000000 R14: 0000000000000002 R15: ffff88021dcc8af0
heinä 19 22:06:24 ruoska kernel: FS:  00007f51201258c0(0000) GS:ffff880229e80000(0000) knlGS:0000000000000000
heinä 19 22:06:24 ruoska kernel: CS:  e033 DS: 0000 ES: 0000 CR0: 000000008005003b
heinä 19 22:06:24 ruoska kernel: CR2: 00007f76983cff90 CR3: 0000000196518000 CR4: 0000000000000660
heinä 19 22:06:24 ruoska kernel: Stack:
heinä 19 22:06:24 ruoska kernel:  ffff88021dcc8af0 0000000000004e20 0000000000000003 ffff880229e83df0
heinä 19 22:06:24 ruoska kernel:  ffffffff81723158 ffff88021dcc8af0 0000000000004e20 ffff880229e83ea0
heinä 19 22:06:24 ruoska kernel:  ffffffffc004e831 000000000000001c ffff880229e83e20 0000000000000000
heinä 19 22:06:24 ruoska kernel: Call Trace:
heinä 19 22:06:24 ruoska kernel:  <IRQ> 
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81723158>] napi_complete_done+0x68/0xb0
heinä 19 22:06:24 ruoska kernel:  [<ffffffffc004e831>] e1000_clean+0x371/0x8c0 [e1000]
heinä 19 22:06:24 ruoska kernel:  [<ffffffff817233be>] net_rx_action+0x21e/0x360
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81085b51>] __do_softirq+0x101/0x290
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81085e53>] irq_exit+0xa3/0xb0
heinä 19 22:06:24 ruoska kernel:  [<ffffffff814d1725>] xen_evtchn_do_upcall+0x35/0x40
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8182f8ae>] xen_do_hypervisor_callback+0x1e/0x40
heinä 19 22:06:24 ruoska kernel:  <EOI> 
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8100122a>] ? xen_hypercall_xen_version+0xa/0x20
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8100122a>] ? xen_hypercall_xen_version+0xa/0x20
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8102345d>] ? xen_force_evtchn_callback+0xd/0x10
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81023c82>] ? check_events+0x12/0x20
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81023c6f>] ? xen_restore_fl_direct_reloc+0x4/0x4
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81085590>] ? do_softirq.part.19+0x30/0x40
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8108561d>] ? __local_bh_enable_ip+0x7d/0x80
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8182d65e>] ? _raw_spin_unlock_bh+0x1e/0x20
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8170a641>] ? release_sock+0x111/0x160
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8176f73c>] ? tcp_recvmsg+0x3fc/0xbe0
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8179d87e>] ? inet_recvmsg+0x7e/0xb0
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81705eab>] ? sock_recvmsg+0x3b/0x50
heinä 19 22:06:24 ruoska kernel:  [<ffffffff81705f52>] ? sock_read_iter+0x92/0xe0
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8120ca3c>] ? do_iter_readv_writev+0x6c/0xa0
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8120d5bf>] ? do_readv_writev+0x18f/0x230
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8182fed9>] ? error_exit+0x9/0x20
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8120d696>] ? vfs_readv+0x36/0x50
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8120e329>] ? SyS_readv+0x59/0xf0
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8100122a>] ? xen_hypercall_xen_version+0xa/0x20
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8182db32>] ? entry_SYSCALL_64_fastpath+0x16/0x71
heinä 19 22:06:24 ruoska kernel:  [<ffffffff8102345d>] ? xen_force_evtchn_callback+0xd/0x10


heinä 19 22:06:24 ruoska kernel: Code: eb df 0f 1f 84 00 00 00 00 00 66 66 66 66 90 55 31 d2 48 89 e5 41 55 41 54 49 89 fc 53 48 8b 7f 38 41 89 f5 48 85 ff 75 05 eb 44 <48> 89 c7 48 8b 07 48 89 57 08 48 89 fa 48 85 c0 75 ee eb 03 48
```

---

### Post by Mikael_Niemel on 2016-07-19
Looks like transfer went just fine with plain Ubuntu kernel.. nothing out of ordinary on dmesg.

I have no idea why this had not happened earlier, maybe it's because it was the first time I had transferred very large amounts of data with this installation?

---

### Post by MAFoElffen on 2016-07-20
Mikael-

I've seen the error in your your last post before on the Xen Development Mailing List, There, it was corrected and went away by his next distro kernel update. When I chased another Debian Bug report down with the same eror under Xen... it was traced to an XSave option in the code of the kernel (in the kernel config file used when compiling), that affects some kernel/cpu combinations.. What that  translates to, is that Dom0, leaves a saved page in memory, when is was actually through with it. When something tries to reuse that page (generates a page request), it gets confused whether it can or not (results in bad page request).

Try to add these options into /etc/default/grub, in line GRUB_CMDLINE_XEN:
```

noxsave=0 noxsaveopt=0

```
...which will tell the kernel not to save those unused pages in memory.

Another "fix" might be to update your system, which would pick up a newer kernel. There has been another released kernel update since you first got this error... and see how it does with a newer kernel.

---

### Post by Mikael_Niemel on 2016-07-20
I tried adding those options and getting updates with apt-get, but apparently kernel version was already [COLOR=#000000][FONT=&amp]4.4.0-31-generic[/FONT][/COLOR], which is the newest I think.

Anyways, it didn't work. It still crashed, and dumped errors to console before rebooting automatically within a second or so. This time there indeed were no logs saved (journalctl didn't show anything for several minutes before the crash), so I don't know what caused it. I think there was something about "fatal exception in an interrupt - not syncing" in the last line of the error dump that I saw by glimpse. :confused:

Apparently my board's BIOS has console redirection to serial port, so I suppose I could use that to save the error messages somewhere.. didn't find any BIOS logs, though.

EDIT: I tried again, and got the same error to journalctl as in previous page.

---

### Post by MAFoElffen on 2016-07-21
Okay, well... Just got an email that my heat sink for the second cpu in my second server got held up in customs and shouldn't be here until the 28th. Since that got held up, I'll push the first server online, to pull that older server with the Tyan board down to config like you have yours.

As a test, I'm thinking I should install and test on kernel 4.4.0-28, before upgrading to 4.4.0-31... Reason? I was thinking about you today = I tried installing Xen directly onto that new server, while it was at 4.4.0-31 ... and it crashed so bad it would not boot. I ended up reinstalling a fresh install onto it!!!

---

### Post by Mikael_Niemel on 2016-07-25
> **MAFoElffen said:**
> Okay, well... Just got an email that my heat sink for the second cpu in my second server got held up in customs and shouldn't be here until the 28th. Since that got held up, I'll push the first server online, to pull that older server with the Tyan board down to config like you have yours.

As a test, I'm thinking I should install and test on kernel 4.4.0-28, before upgrading to 4.4.0-31... Reason? I was thinking about you today = I tried installing Xen directly onto that new server, while it was at 4.4.0-31 ... and it crashed so bad it would not boot. I ended up reinstalling a fresh install onto it!!!

Btw, have you yet had time to try it on the Tyan board? Though Xen crashing that bad on 4.4.0-31 doesn't sound particularly good..

---

### Post by Mikael_Niemel on 2016-08-21
So, any news about this?

---

### Post by MAFoElffen on 2016-08-23
Not yet. My non-Vt-x Xen Experiments have been podtponed for about another week or so.. sorry about not keeping you posted on that... My board like yours is still plugging a hole in my fabric until then. I should be back home to take care of that soon.

---

### Post by Mikael_Niemel on 2016-08-31
And just to let you know, I had yesterday an uncorrectable ECC error. When I turned ECC off and started memtest, I got a bunch of errors.. then I looked at the board and I saw some swollen capacitors.. ](*,)

I don't get why it has been working fine without Xen until this point, all I have got has been occasionally some corrected ECC errors, but with Xen it imploded totally and almost instantly. Anyways, I'll change the caps, and see if that fixes the memory errors. If it doesn't, I'll have to move to a new board.

---

### Post by Mikael_Niemel on 2016-09-03
After changing the caps and switching memory modules the ECC errors vanished, but Xen still crashes. So, it apparently wasn't about that.

---

### Post by Mikael_Niemel on 2016-09-14
> **Mikael_Niemel said:**
> Btw, have you yet had time to try it on the Tyan board? Though Xen crashing that bad on 4.4.0-31 doesn't sound particularly good..

Sorry to poke you again, but what's the status? I understand that it's probably a legacy feature, and I can use Virtualbox if Xen doesn't work, even if I'd prefer to use Xen. :)

---

### Post by MAFoElffen on 2016-09-20
Sent you a PM early this AM. Got back from holiday late last night. In the process of pulling my Tyan offline right now and another server back online in it's place.

Once that is done, will get details from you to mirror what you have as a configuration.

---

### Post by Mikael_Niemel on 2016-10-12
Any news yet? :)

---

