---
title: "Seeking document to configure Virtual Machine Manager - KVM"
date: 2022-01-16
forum: Virtualisation
---

### Post by satimis on 2022-01-16
Hi all,

I have installed KVM/QEMU and Virtual Machine Manager on Ubuntu 20.04 as host.  Also I have created Linuxmint and Win 10 guests.

Please advise where can I find documents to properly configure Virt-Manager with Windows and Linux guests, something similar to Guest-Addition on Oracle VirtualBox.

Thanks in advance

Regards

---

### Post by TheFu on 2022-01-16
I know of no "properly configure" answer.  There are certain things that work better, depending on the requirements. libvirt is very flexible, so I'd start by reading those documents.  Settings for Windows aren't the same as settings for Linux because Windows just doesn't come pre-installed with the same drivers.  

I know the settings for WinXP and Win7, but not for any newer versions of Windows.  Since everything except the storage can be changed easily after a VM is created, I'd spend my time learning about the different storage options.  The answer for "best" settings for storage depends on what physical storage is being used.  HDD and SATA-SSD vs NVMe-SSD matters.  Is there RAID?  Are you using ZFS, LVM, XFS, EXT4 or the most dangerous, BTRFS?  Do you want replicated storage between 2 systems, automatic?

See how it gets complex quickly?

I have a few blog articles about my setups.  [https://blog.jdpfu.com/2012/07/30/improving-kvm-performance](https://blog.jdpfu.com/2012/07/30/improving-kvm-performance) is one from 2012.  Some of my settings are now the defaults in libvirt, which is good news.

I use LVM with a separate LV for each VM.  The LV is presented to the VM as a block device.  All disk and networking uses virtio drivers. This is the fastest, lowest overhead possible.  Don't provide too many cores or too much RAM to guests.  In general, 1 vCPU to a guest is sufficient, unless you 100% know more is necessary. MS-Windows used to install different kernels based on single core or 2+ cores, so I'd give 2 vCPUs to Windows guest VMs to ensure a multi-core Widnows kernel was installed.
As for the fake GPU, that becomes a harder thing and depends on needs.  For non-GUI servers, I keep is simple and light. Cirrus or vmvga. It isn't' like I'll ever access the system through the console anyway - all access will be over ssh.  For Windows, I'm using SPICE which requires loading the QXL drivers into the guest. If Win10+ doesn't already have virtio drivers included (it didn't for Win7), then having those for disk and network access can lead to extra problems when Windows refuses to boot.  I've been tempted to go back to SCSI drivers on Windows and an Intel PRO/1000 NIC just to make the failed boot troubleshooting easier. I don't think the overhead for not using virtio is THAT much.  Again, it is a consideration.

Keep as much storage out of the VMs as possible. In my VMs, I want the OS, applications and settings. Most data storage, if it is more than 20G, will be on a NAS somewhere on the LAN.

If the system doesn't need to be a full VM for security reasons (or MS-Windows), then consider using a Linux container like lxd.  Containers have much lower overhead and usually 10 containers will use the resources of 1 VM.  Just something more to consider.

---

### Post by satimis on 2022-01-16
Hi TheFu,

Thanks for your detail explanation.

What I'm trying to do is to setup a shared folder between KVM Host and Guest

Host - Ubuntu 20.04
Guests - Linux and Windows

I found following document online;
Setup A Shared Folder Between KVM Host And Guest
[https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/](https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/)

That is for Linux guest.

I'm now digging around for documenmts to setup; 

1) A shared folder between KVM Host and Windows Guest

2) To share files between Windows and the storage drive, ext 4 format, in the same PC.

Do I need Samba to assist me?

Regards

---

### Post by TheFu on 2022-01-16
I use NFS for that. Treat the guest just like any other physical server. This avoids a bunch of VM-specific security issues which are common in the host-file-sharing implementations of all hypervisors. I've been bitten by vbox stuff that way. Never again.

For Windows to access storage on Linux, use the same "Treat the guest just like any other physical server" method.  Forget that they are running on the same PC.  EXT4 doesn't matter if Linux is the host for the storage.  Whether you use samba or not is your choice. There are other methods, but I typically avoid samba since it breaks the Unix file security model and overlays the CIFS one.  Lots of people use samba happily. I use it for a Windows system to access data for processing that is on a Linux system where most of the heaving lifting happens.  Since I found LosslessCut-linux.AppImage, that use has dropped drastically.  Seems that a number of people have created similar ffmpeg segment cut tools the last year.  Lossless-Cut is far from perfect (electron apps aren't my favorite) and the hidden ffmpeg command used drops streams and metadata contained in the source, but at least it doesn't require Windows. I've been using it to create exact EDL files which feed into my mkvmerge-cut script. I'm working on the new processing steps now and hope to get this down to an efficient method ASAP. The Lossless-cut program hasn't been released since August and has a number of critical fixes that I need. The caption and support for AC3 audio isn't working in that release. Also, I'd love to remap the keys used for different parts of the editing process.  F3/F4 are my known start-cut and end-cut keys. I like left-hand for edits, right hand for moving around the file. It also shows where the key frames are located, so picking where a cut happens isn't guesswork.

You can always use other methods based on ssh/sftp for this too, if you just want to copy files around.  WinSCP is a fine Windows client for sftp stuff.

---

### Post by tea for one on 2022-01-16
> **satimis said:**
> 

I'm now digging around for documenmts to setup; 

1) A shared folder between KVM Host and Windows Guest

2) To share files between Windows and the storage drive, ext 4 format, in the same PC.

Have you considered the Windows Guest Tools from [https://www.spice-space.org/download.html](https://www.spice-space.org/download.html)

Folder sharing is also on the page.

I use virt-viewer as a graphical display because it allows you to nominate a shared folder and usb devices.

---

### Post by satimis on 2022-01-17
> **TheFu said:**
> I use NFS for that. Treat the guest just like any other physical server. This avoids a bunch of VM-specific security issues which are common in the host-file-sharing implementations of all hypervisors. I've been bitten by vbox stuff that way. Never again.

Whether run NFS for files sharing btw host and Linux guest as following document ?;

4.3. SHARED STORAGE EXAMPLE: NFS FOR A SIMPLE MIGRATION
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-shared-storage-nfs-migration](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-shared-storage-nfs-migration)

It wouldn't auto-connect the HDD.  Each time it needs to run NFS similar to SMB

For files sharing VirtualBox is more simple and straightforward.

Regards

---

### Post by satimis on 2022-01-17
> **tea for one said:**
> Have you considered the Windows Guest Tools from [https://www.spice-space.org/download.html](https://www.spice-space.org/download.html)

Folder sharing is also on the page.

I use virt-viewer as a graphical display because it allows you to nominate a shared folder and usb devices.
Hi,

Thanks for your advice.  I haven't run SPICE before.

I have following questions;
1) Do I need installing a virt-manager specific for SPICE to replace KVM virt-manager ?
2) Does this virt-manager work for both Windows and Linux Clients ?

Please advice.  Thanks

---

### Post by tea for one on 2022-01-17
I use the virtual machine manager version 2.2.1 (from Ubuntu 20.04 repository)
Both Windows and Linux guests are supported (the info is on the page I linked)

The spice-space.org website has vast quantities of information and it should be your first point of reference if you decide to explore this avenue.

---

### Post by Dennis N on 2022-01-17
> Whether run NFS for files sharing btw host and Linux guest as following document ?

The linked article in post #3 seems overly complicated. If it's Linux host and Linux guest, I just use SSH connection from guest to host to get access to whatever location I want. Initiate the connection from the guest's file manager (Files) using the "connect to server" option. I've never used "shared folders". Files has lots of capabilities - after initial connect, you can opt to store the connection information. You can bookmark host locations in Files as well, and they will connect and open automatically from the guest. 



I don't have Windows on any of my computers so I can't comment on a Windows guest -Linux host interconnection.

---

### Post by TheFu on 2022-01-17
NFS isn't hard to get working.  Ubuntu has a how-to.  Google "ubuntu nfs". [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)
[LIST=1]
[*]Install the nfs-server+nfs-common on the server, 
[*]Install nfs-common on the client, 
[*]Edit the /etc/exports file on the server - 1 line per exported directory. Be certain to limit access - i.e. use specific, static, IPs for which clients are allowed.
[*]Edit the /etc/fstab on the client - 1 line per mount
[*]Set the owner for the NFS storage to whatever userid you want, then that userid can manage the permissions.
[/LIST]
Bob's your uncle.
Troubleshooting is **showmount -e**.  If you like, you can setup tcp-wrapper limitations for NFS. This is from the 1990s-style of security.

There are some basic things that are likely already setup correctly which can cause problems.  The uid/gid (numbers, not usernames) are what match to provide owner, group permissions.  Root/sudo on the client typically has ZERO permissions to control NFS files. Only the server root/sudo can chown.  99.9999% of the time, standard Unix permissions are used.  owner, group, permissions, ACLs, and xattrs all work just like for local storage.  You can override settings to allow the client-side root full control, but this is a security issue for obvious reasons.
MacOS clients typically have issues due to uids starting from 500, not 1000 on that platform.  The solution is to change the uid/gid on either the client or the server, but all clients need to have matching uid/gids for users with access to the NFS storage.  Centralized (LDAP) user management makes this issue go away.

>  For files sharing VirtualBox is more simple and straightforward.
Until you have corrupted data because locking doesn't work.  NFS has known and understood locking.  People run VMs over NFS storage and have for 15+ yrs.

---

### Post by MAFoElffen on 2022-01-17
NFS is great for UNIX and Linux... There are some caveats for using NFS with Windows...

Windows Services For NFS Server, you need Win Server 2008 and beyond. For  Win Desktop, I have done it with Windows 10 Pro, with a registry hack.  Before WIN7, you could do it with MS Windows Services For UNIX(SFU)...

Win7 and beyond, in Programs and Features, you turn on "Services For NFS > Client Services For NFS. 

Note:  At MS, it now says only Windows 10. Everywhere you look, it says that  you just turn on the feature, but that feature is not present for all  Editions of Win10.. On TechNet, it says it is only supported under  Editions of Pro and Enterprise. If you look for the feature on Home  Edition, it is not there...

---

### Post by TheFu on 2022-01-17
Last time I used NFS under Windows was in the 1990s. We needed a full-time admin to manually sync the user and group DBs from the Unix side with what Windows needed.
My attempts to use NFS since 2000 with SFU has always failed.  I had every version of Windows available (legally) and wasn't able to get it working.  I did have Hummingbird-NFS working on my WinNT4 workstations in the late 1990s. It worked fine then.

I'm embarrassed by the lack of something to trivially replace NIS natively on all the popular Linux OSes.  By default, Canonical should be setting up an LDAP DB for every system and have a local LDAP DB.  Then it should be trivial to make it into a network service.

---

### Post by MAFoElffen on 2022-01-17
If you just want to share data from the host to the VM, then why not this way?
[https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/](https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/)

Just an idea...

---

### Post by TheFu on 2022-01-17
> **MAFoElffen said:**
> If you just want to share data from the host to the VM, then why not this way?
[https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/](https://ostechnix.com/setup-a-shared-folder-between-kvm-host-and-guest/)

Just an idea...

SELinux? Also, this breaks the clear delineation between GuestOS and HostOS.  In that breakage, security failures are often found.  But not everyone used VMs as a security tool.  OTOH, I'm much more comfortable using NFS which has 30+ yrs of known security techniques and the security failures of the protocol are much more likely understood and mitigated.  For example, use read-only NFS exports and mounts.

From the NIST Recommendations [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-125A.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-125A.pdf) for hypervisor security:
> More importantly, many hosted virtualization systems allow guest OSs to share information with the host OS through shared disks or folders, which are normally created by emulating networked disks. In either case, if one guest OS has been compromised by malware, it might spread the malware through the shared disk or folder. This is a security vulnerability that does not exist on regular OSs unless they have shared network storage. Organizations that have security policies that cover network shared storage should apply those policies to shared disks in virtualization systems.

When it becomes time to setup VM failover to a different system, being loosely coupled to the host system is better too. If that is always the situation, there's no more work to be completed.  But this may not matter to everyone.

---

### Post by MAFoElffen on 2022-01-17
For Ubuntu, you skip that step... But it only works for Linux Guests.

For KVM Windows Guests, there is a version of spice-guest-tools that works to cut and paste between and sets up the initial port to share folders from the host, through adding a Spice Channel, set to org.spice-space.webdav.0... Then installing an MSI to run the matching service in the Windows guest. It comes out clean as showing up as another drive in Windows "My Machine"... Works in virt-viewer > preferences > share folder...

Too much to post... Let me see if I can find a link someone's tutorial...

EDIT:
I found one...
[https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/](https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/)

It's not permanent nor persistent... You have to set the folder sharing preference every time virt-viewer starts up.

---

### Post by satimis on 2022-01-19
Hi all,

My problem is half solved, connecting the ext4 storage drive in this PC on Windows 10.  The solution is simple and straightforwards,

Download and install "ext2 volume manager" for Windows
Ext2Fsd-0.69.1044-11.02.exe (Windows App.  It can be download on Internet, FREE to use)

Start "ext2 volume manager"

Select```

Disk 1
Basis EXT4 3726 GB ......

```
(screenshot - Capture-1)

Right-click on it -> Assign Drive Letter
Letter 'F' is assigned to this drive

Start -> File Manager (Window Explorer) -> select Local Disk (F)

All data folders and files of the ext4 Storage Drive are displayed.
(screenshot - Capture-2)

.txt file can be read on Wordpad.

That is all I need, retrieving data from the Linux Storage Drive on Windows 10.  I don't need to copy Windows data on the Storage Drive, avoiding making confusion.

I suppose connecting other Linux drives would be similar.  But I don't need it.

My problem on this posting is half solved.  The remaining problem is data sharing btw Linux/Windows guests and Linux host on KVM/QEMU.  I'll come back after finding a solution.

Regards

---

### Post by TheFu on 2022-01-19
> Download and install "ext2 volume manager" for Windows
Ext2Fsd-0.69.1044-11.02.exe (Windows App. It can be download on Internet, FREE to use)
That is just scary to me, but I find dual booting scary too.

To share storage between the host and all guests, just use NFS and Samba.
But I see in another thread that you appear to be going with virtualbox, so do we need to even continue in this thread?

---

### Post by MAFoElffen on 2022-01-19
The way I do data sharing on a dual boot, where verything is one the same computer (and do not need share things outside that),  is to put the data I want to share between systems on an NTFS partition. Linux reads and writes to NTFS filesystems. Most everything does.

In fact, my storage pool on my Desktop, for my ISO collection is on NTFS. That way, I don't have to have multiple copies anywhere. It I want to have access to anything between systems, I store it there.

---

### Post by satimis on 2022-01-19
> **MAFoElffen said:**
> The way I do data sharing on a dual boot, where verything is one the same computer (and do not need share things outside that),  is to put the data I want to share between systems on an NTFS partition. Linux reads and writes to NTFS filesystems. Most everything does.
Yes, ext2 Volume Manager is a great Windows APP.  Sharing data amongst all drives of different format is possible, "verything is one the same computer" as you said.  I keep all data on the storage drive on operating all drives, convenient for sharing.  Besides I have an external storage drive and periodically, I will duplicate the data from the internal storage drive on it.  It safe-guards the data if one of the storage drive failure.

> 
In fact, my storage pool on my Desktop, for my ISO collection is on NTFS. That way, I don't have to have multiple copies anywhere. It I want to have access to anything between systems, I store it there.
I built the Windows drive solely for graphic editing.  I won't do daily working on it.

Regards

---

### Post by satimis on 2022-01-20
[B][COLOR="#FF0000"]KVM - files sharing between Linux guests and Linux host
[/COLOR][/B]
Following document help me out partially
**Setup A Shared Folder Between KVM Host And Guest**
[https://www.linuxhowto.net/setup-a-shared-folder-between-kvm-host-and-guest/](https://www.linuxhowto.net/setup-a-shared-folder-between-kvm-host-and-guest/)

**KVM/QEMU**
Host - Ubuntu 20.04

Guests:
Debian 11
Linuxmint Edge 20
Ubuntu 20.04
Win10

(pls refer to screenshot-virt-manager.png)

**[COLOR="#FF0000"]Section - Create shared folders in KVM host[/COLOR]**
All steps on the document work without problem.
[B]
File sharing;[/B]
Ubuntu 20.04 - can be connected automatically at boot

Debian 11 and Linuxmint Edge 20
If adding following line on /etc/fstab```

/hostshare /hostfiles 9p trans=virtio,version=9p2000.L,rw 0 0

```

Both Debian 11 and Linuxmint Edge 20 unable to boot

I have to boot them up and on Terminal run:```

sudo mount -t 9p -o trans=virtio /hostshare hostfiles/

```

then both of them can connect the host for files sharing

Any suggestion?

Regards

---

### Post by SeijiSensei on 2022-01-21
Don't you have servers that the physical and virtual machines can see? I often find this the easiest method of moving files between machines. I copy the file to my server in one machine and open it in the other. I use NFS for Linux and Samba on Windows VMs with the server configured to share its files using both protocols.

---

### Post by satimis on 2022-01-21
> **SeijiSensei said:**
> Don't you have servers that the physical and virtual machines can see? I often find this the easiest method of moving files between machines. I copy the file to my server in one machine and open it in the other. I use NFS for Linux and Samba on Windows VMs with the server configured to share its files using both protocols.
Thanks for your advice.

I don't run server here.

Now I have no problem sharing folders between Linux guest and Ubuntu host.  Leaving behind unsolved is sharing folders btw Windows guest and Ubuntu host. "ext2 Volume Manager (Windows App) can't work.  It works on Windows drive and Linux drive in the same PC.  I'm now testing WinSCP.

SMB works which I tried long time before.  I'm now looking for a way sharing folders between Windows guest and Linux host

Regards

---

