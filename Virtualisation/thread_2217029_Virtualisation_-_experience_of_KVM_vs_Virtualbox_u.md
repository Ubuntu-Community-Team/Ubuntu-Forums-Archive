---
title: "Virtualisation - experience of KVM vs Virtualbox using Command Line"
date: 2014-04-15
forum: Virtualisation
---

### Post by npinn001 on 2014-04-15
Hi,

So I'm installing Ubuntu server minimal as a base server and then want to run seperate virtual machines on top of it for media server, file server, test box etc.

Does anyone have any experience with using KVM or Virtualbox for this via the command line, and which one offers better:

1) Security
2) Performance
3) Backup/Restore options.

I want to set it up this way as a I run it headless tucked away, so having a stable base means I can remotely connect and use the VMs on top, and if anything goes wrong, just delete the VM or restore a backup!

Thanks

---

### Post by heiko_s on 2014-04-16
I would include Xen as well. Performance wise Xen or KVM should outperform Virtualbox anytime.

For best performance and flexibility under Xen I would use LVM formatted drives, which also makes backup very easy. If you run Linux in the VMs you can back them up using the snapshot feature of LVM while they are running.

Both Xen and KVM can be fully controlled via CLI. With Xen all you need to do is create a guest config file under /etc/xen and use the xl commands to create, pause, etc. the guest. Xen offers different types of guests, best performance is achieved with paravirtualised (PV) guests, but also fully virtualised HVM guests can be tuned to perform to near bare metal performance given the right drivers and setup. KVM should provide similar performance, but I'm less familiar with it.

I use Xen for VGA passthrough of a Windows 7 guest, but KVM would also be suitable.

For remote access I use ssh, it's very easy to setup and probably the safest way. Using keys, you can login remotely without password.

Good luck!

---

### Post by jasonvp on 2014-04-17
> **npinn001 said:**
> So I'm installing Ubuntu server minimal as a base server and then want to run seperate virtual machines on top of it for media server, file server, test box etc.

Were I in your shoes, I'd reconsider this approach *slightly*.  Mainly: I'd get rid of the file server from the mix.  You really want file servers to be their own devices versus a VM from a performance perspective.  That means having a second box, and I can understand if that's a bit of a problem.  But: that's my opinion on the matter.  Take it for what it's worth (probably less than you paid for it. :-))

> Does anyone have any experience with using KVM or Virtualbox for this via the command line

I'm just now making the migration from VMWare's ESXi to KVM on Ubuntu, so I'm learning tons about it as I write this.  I have zero experience with VB, so I can't really help you there.

> and which one offers better

1) Security

Security as in how?  KVM runs on top of any standard Linux distro, which has available to it all of the standard Linux security pieces such as ssh, iptables, and anything else you may or may not want to add to it.  Further, you're going to secure each VM with the aforementioned technologies, right? :-)

> 2) Performance

I don't have enough experience to know this one yet.

> 3) Backup/Restore options.

As the previous poster mentioned, you have a few options with KVM and/or Xen.  They can both use flat files like ESXi does, which you can back up to some other disk if you want.  They can also use the LVM subsystem for the VMs' /dev/[s|h]d* devices if you want, and you can take snapshots of those from the hypervisor.

> I want to set it up this way as a I run it headless tucked away, so having a stable base means I can remotely connect and use the VMs on top, and if anything goes wrong, just delete the VM or restore a backup!

With KVM, you have several remote management options.  Just about every and anything you'd want to do with the hypervisor itself can be done via the CLI after sshing into it.  To manage the running VMs from the same CLI, it becomes *slightly* more challenging, but not difficult at all.  After the VM is running, you'll want to tell it to run an agetty on ttyS0, and (assuming it's a Linux VM) tell its grub config that the ttyS0 is a valid console.  Once you've done that and rebooted the VM, you can connect to it with the **virsh** command on the KVM hypervisor.
```

blackgate$ virsh list
 Id    Name                           State
----------------------------------------------------
 2     deathstroke                    running
 4     kvm-test                       running
blackgate$ virsh console 2
Connected to domain deathstroke
Escape character is ^]

CentOS release 6.5 (Final)
Kernel 2.6.32-431.11.2.el6.x86_64 on an x86_64

deathstroke login:

```

Note: the above quoted text *won't work* until you have an agetty running on ttys0 on the VM.

What kind of device/OS will you primarily be sitting in front of?  A PC running Linux?  Windows?  A Mac?  KVM can easily be configured to allow incoming VNC connections that will dump you right onto the console of the running VMs as well.  Each VM gets its own port, so you can easily connect to your.hypervisor.somedomain.com:5000, or :5001, or :5002, etc to get the consoles of each VM.  For that, I use **Chicken of the VNC** on my Mac.  It works beautifully.

---

### Post by houstonbofh on 2014-04-18
I second looking at Xen for this.  There are more mature tools for managing Xen headless servers than for KVM right now...   (like OpenXenManager)  As for a development workstation with VMs on it that need to start up automatically, KVM wins hands down.

---

### Post by TheFu on 2014-04-21
> **npinn001 said:**
> Hi,

So I'm installing Ubuntu server minimal as a base server and then want to run seperate virtual machines on top of it for media server, file server, test box etc.

Does anyone have any experience with using KVM or Virtualbox for this via the command line, and which one offers better:

1) Security
2) Performance
3) Backup/Restore options.

I want to set it up this way as a I run it headless tucked away, so having a stable base means I can remotely connect and use the VMs on top, and if anything goes wrong, just delete the VM or restore a backup!

I've used ESXi, ESX, Xen, VirtualBox, VMware Workstation and KVM for years.  About 2 yrs ago, I switched away from Xen to KVM. Xen would refuse to boot after kernel updates from time to time. That was the hostOS refusing to boot!  Can't have that on a system that runs 8-10 client VMs that people expect to use (except during approved maintenance periods).  Unacceptable. Xen is removed from my consideration due to multiple times with that issue.

3-4 yrs ago, VMware was screwing around with license costs, so my company made a concerted effort to remove anything with VMware 100% rather then pay 2-3x more. Eventually the company realized how stupid they were and lessened the price increase, but not before we'd already purged their software from our systems. NEVER AGAIN. That goes for the free tools too.  BTW, VMware Workstation is by far the best for desktop-on-desktop needs in a professional environment (think about QA/Testers).

Security - That depends on YOUR skill more than anything else.

Backup/Restore - that depends on YOUR skill more than anything else. Nothing is "built-in", but there are many powerful techniques with and without leveraging VM technology. I don't bother. Snapshots sound great, but how do you restore that to another physical machine?  Old school backups will probably take much too long and extra steps are needed to quiesce the DBs to avoid corruption.

Performance - this depends on too many things that only YOU control.  There are times when Xen is faster, times when KVM is faster .... virtualbox is NEVER faster, but it isn't THAT much slower that it becomes a consideration for most people.  KVM is almost always faster than ESXi too. Check the Virt-SPEC tests.  The manner that you setup the infrastructure matters most to get the best performance. There are smart choices and not-so-smart choices which are completely dependent on the available hardware, networking, and existing security situation for your specific location(s).

There is NO need to manage KVM from the command line. Use libvirt and any CLI/GUI you like from a remote machine.  For fewer than 50 VMs, virt-manager is easy. It works over ssh, so it is as secure as any other ssh tool (fairly secure with keys, not passwords).  For more than 50 machines, use something like cobbler to bring them up and use ansible, puppet, chef, to manage the settings if you have more than 10 machines.  This stuff has been solved, though sometimes the solutions add more work in the start.  I like ansible.

The workload on the guestOSes matters most when selecting the virtualization infrastructure more than anything else, but more and more KVM does all that I need, fast, with extreme stability. In 3 yrs running KVM, it has NEVER crashed on any systems here.  Performance tuning for all the VM options is basically the same, so once you get that down, it transfers to other hypervisors.

So ... the short answer is KVM with manual Linux bridges, with libvirt and virt-manager, IMHO.

Hope this helps someone.

---

### Post by heiko_s on 2014-04-21
@TheFu: I remember that, under Xen, a dom0 kernel update caused issues with starting VMs, but I haven't experienced issues with booting the dom0, yet. I wonder which distribution you were running with Xen?

I agree with manual bridges, and in my opinion it's best to remove network-manager after setting up and testing networking.

I didn't have good experiences with virt-manager, though. Under Xen, using the CLI and the guest config files seem to be an easier approach.

---

### Post by TheFu on 2014-04-22
It was Xen on Ubuntu 10.04.  I understand from others that Xen on CentOS/Redhat works very well.  When 12.04 was released, I'd had enough of Xen and KVM was reported to be stable. It was and it still is.  Performance is excellent, so I elected to use it on all new deployments to leave the Xen issues behind. It has worked extremely well.

---

### Post by npinn001 on 2014-04-22
Thanks everyone. 

TheFu - thanks for that. Your two posts in threads have really helped me a great deal. I know now that KVM is the way to go and I'll go from there, using virt-manager.

Thanks again to all!

---

### Post by TheFu on 2014-04-22
KVM has worked for us, but that doesn't take anything away from Xen.  If you need high performance, remote, desktops, I believe (don't know) that the XEN VDI solution ($$) is one of, if not THE best choice.  I know people who stream 720p video from 1000 miles away using Xen-VDI.  Don't know any way to get that video performance from KVM.

---

### Post by npinn001 on 2014-04-22
> **TheFu said:**
> KVM has worked for us, but that doesn't take anything away from Xen.  If you need high performance, remote, desktops, I believe (don't know) that the XEN VDI solution ($$) is one of, if not THE best choice.  I know people who stream 720p video from 1000 miles away using Xen-VDI.  Don't know any way to get that video performance from KVM.

Thats interesting to know!

Quick Q - I'm guessing KVM stores the VMs in /home. I have a 250GB hard drive and I wasnt sure the best way to partition it for my needs. Was going to go with a /boot /root /home swap setup, but not sure if I limit /root in size if that impacted KVM in some way. No GUI on server, very few applications apart from KVM and SSH. What do you reccomend as a partition setup?

Thanks

---

### Post by Doug S on 2014-04-22
> **npinn001 said:**
> I'm guessing KVM stores the VMs in /home.You can put your VM anywhere. Some of mine are in /home/doug/img, some in /var/lib/libvirt/images and some are on another HD that I mount ending up at /media/newhd.

I do not have a suggestion for how you should partition things.

---

### Post by heiko_s on 2014-04-23
Not sure this holds for KVM, but I have been very satisfied with LVM formatted drives (Xen VMs perform very well on these). LVM gives you more flexibility if you ever need to resize partitions or add a drive. I have adopted LVM for all my PCs - desktop (with Xen), media server, and other PCs.

Here my partitioning / LVM assignment:

sda1 - /boot - 1GB as ext2 (SSD)
sda2 - LVM volume group "main" - rest of disk
LVM "main" group logical volumes (LV):
root - / - 16GB as ext4 (you need much less for a server without GUI)
home - /home - whatever you need for a /home partition as ext4
vm1 - no mount point specified - whatever size you give to the 1st VM - unformatted (under Xen it will be formatted by the guest OS)
vm2 - no mount point specified - ...
...

The VMs are accessible from the host via the kpartx command. Under Xen, the guest OS sees the LVM volumes vm1, vm2, etc. just like regular raw partitions and formats them the way you specify. This works very well under Xen and HVM Windows guests, and performance is near or equal to bare metal performance. However, if you run Linux guests on KVM, there may be better ways.

I find LVM very convenient for backups of VMs, where you can use the "snapshot" feature. I usually backup and compress the entire VM volume (keeping multiple copies and a "golden" copy) and never had any issue restoring from a backup.

Another feature I use regularly with LVM is growing a volume over several HDDs. Sooner or later a PC runs out of disk space, so I just pop in a drive and add that drive to the volume group (VG) in need to grow.

LVM naming:
In LVM you use VG (volume group) and LV (logical volume) names. After making the mistake to create multiple VGs for host OS, VMs, media drives, etc. I learned that it's best to have only a minimal number of VGs. I now use only "main" and "backup" VGs. Why? Because I need them on different physical drives.

The "main" VG holds both the host OS and the VMs, as well as all data drives. This gives me maximum flexibility to adjust the LVs (the logical volumes or "partitions") the way I want. If I oversized my "root" LV (/) I just resize the file system and shrink the LV. The space I gained I can assign to any LV in that "main" VG, for example "vm1". The "backup" VG is only for backup purposes and holds (compressed) images or backup copies (rsync) of my data on the "main" VG.

Hope I haven't overshot here and stated the obvious. Perhaps TheFu can shed more light on KVM specific solutions?

---

### Post by npinn001 on 2014-04-23
> **heiko_s said:**
> Not sure this holds for KVM, but I have been very satisfied with LVM formatted drives (Xen VMs perform very well on these). LVM gives you more flexibility if you ever need to resize partitions or add a drive. I have adopted LVM for all my PCs - desktop (with Xen), media server, and other PCs.

Here my partitioning / LVM assignment:

sda1 - /boot - 1GB as ext2 (SSD)
sda2 - LVM volume group "main" - rest of disk
LVM "main" group logical volumes (LV):
root - / - 16GB as ext4 (you need much less for a server without GUI)
home - /home - whatever you need for a /home partition as ext4
vm1 - no mount point specified - whatever size you give to the 1st VM - unformatted (under Xen it will be formatted by the guest OS)
vm2 - no mount point specified - ...
...

The VMs are accessible from the host via the kpartx command. Under Xen, the guest OS sees the LVM volumes vm1, vm2, etc. just like regular raw partitions and formats them the way you specify. This works very well under Xen and HVM Windows guests, and performance is near or equal to bare metal performance. However, if you run Linux guests on KVM, there may be better ways.

I find LVM very convenient for backups of VMs, where you can use the "snapshot" feature. I usually backup and compress the entire VM volume (keeping multiple copies and a "golden" copy) and never had any issue restoring from a backup.

Another feature I use regularly with LVM is growing a volume over several HDDs. Sooner or later a PC runs out of disk space, so I just pop in a drive and add that drive to the volume group (VG) in need to grow.

LVM naming:
In LVM you use VG (volume group) and LV (logical volume) names. After making the mistake to create multiple VGs for host OS, VMs, media drives, etc. I learned that it's best to have only a minimal number of VGs. I now use only "main" and "backup" VGs. Why? Because I need them on different physical drives.

The "main" VG holds both the host OS and the VMs, as well as all data drives. This gives me maximum flexibility to adjust the LVs (the logical volumes or "partitions") the way I want. If I oversized my "root" LV (/) I just resize the file system and shrink the LV. The space I gained I can assign to any LV in that "main" VG, for example "vm1". The "backup" VG is only for backup purposes and holds (compressed) images or backup copies (rsync) of my data on the "main" VG.

Hope I haven't overshot here and stated the obvious. Perhaps TheFu can shed more light on KVM specific solutions?

Thanks very much for that, its a really useful post. I'll go with a setup similar to that then as that seems like a sensible partition scheme!

---

### Post by heiko_s on 2014-04-23
I forgot to mention: I use MBR for the boot disk. I'm not a friend of EFI. If you use (U)EFI boot, you need a /boot/efi partition as well that needs to be in FAT16 format. But if possible, try to avoid EFI.

---

### Post by TheFu on 2014-04-23
MBR has NOTHING to do with EFI.  MBR vs GPT is an easy answer - use GPT if your BIOS supports it and you aren't running MS-Windows.  There are tooo many reasons to list for why GPT partitioning is better than MBR.

I don't have any partitioning advice.  KVM let's you put VM storage anywhere, but defaults to /var. I'd NEVER put anything in /home on a VM server. This is NOT a desktop, so HOME can be 10MB. If you want slightly more performance, greater flexibility (at the cost of greater complexity), use LVM.

---

### Post by jasonvp on 2014-04-23
It depends on how many disks you want to install in your server; I'm a fan of having as many as I can because, let's face it: spinning disks are basically free again.  But, that's just my opinion.  My suggestion would be to have *at least* 2 physical drives in your server, but preferably 3 or 4.

**_Disk 1_**
Reasonably small.  It's going to hold the hypervisor's OS on it along with some swap space.  For this reason, I'd avoid an SSD even though quick boots are really tempting.  The question you have to ask yourself is: how many times am I *really* going to reboot this machine?  If it's a hypervisor, the answer to that should be somewhere between "rarely" and "never".
/dev/sda1: /boot - 256M.  Any more is a waste.
/dev/sda2: swap space - Size this accordingly. 
/dev/sda3: / - Rest of space

Each of these 3 should be boring ol' primary partitions.  The idea behind the layout is: easy to destroy and recreate without affecting other things on the server.  Since it's a hypervisor, you shouldn't be doing much as a non-root user.  In other words: you don't need a separate /home.  Right?

**_Disk 2_**
Tag the entire thing with a VG.  I call mine "LVM-Root" because it's where I install most of my VMs' /dev/sda drives on.  But you can call it anything you want.

Create a small LV called "LVM-Conf" and format it with ext4.  It doesn't need to be more than 200-300M.  Everything that's in **/etc/libvirt** will be moved to this filesystem.  This is where we'll store all of the KVM configuration files so that when we decide to nuke /dev/sda to re-install a new version of Ubuntu, KVM will be unaffected.

```

blackgate# cd /etc
blackgate# ls -latd libvirt
lrwxrwxrwx 1 root root 17 Apr 18 22:49 libvirt -> /KVM-Conf/libvirt/

```

The rest of the VG will be used to create LVs for new VMs.

**_Disks 3..._**
Add a VG to each of these, and create new LVs for new VMs as needed.  Or as **heiko_s** mentioned, use one for snapshots of your VMs.  It's really entirely up to you.

[quote=heiko_s]I forgot to mention: I use MBR for the boot disk. I'm not a friend of  EFI. If you use (U)EFI boot, you need a /boot/efi partition as well that  needs to be in FAT16 format. But if possible, try to avoid EFI.[/quote]

There's no reason to avoid EFI; get used to it because it **is** the future.  "Old fashioned" BIOS are doomed to the dustbin of history.  Ubuntu's grub2 installation handles and groks EFI just fine.  For what it's worth: my Ubuntu installation is on a monster Mac Pro 5,1, which means EFI is my only choice.  Ubuntu installed without a hitch.

---

### Post by Doug S on 2014-04-23
> **TheFu said:**
> I'd NEVER put anything in /home on a VM server. This is NOT a desktop, so HOME can be 10MB.If home is plenty big enough, why not?

---

