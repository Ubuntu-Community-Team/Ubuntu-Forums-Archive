---
title: "Development of the [Boot-Repair] and [Boot-Info] utilities"
date: 2021-12-28
forum: Ubuntu Application Development
---

### Post by YannBuntu on 2021-12-28
hi all,

This is discussion about the dev of the tool, inform about new versions, call for testing, etc.
I especially appreciate the feedback from the forum 'helpers' , i.e. people like oldfred who daily help others with their boot issues, because those tools are mainly here to decrease their workload by providing a useful diagnostic (boot-info) and solving the frequent cases (boot-repair).

This is not a topic for user support. If you have an issue with the boot of your computer, please open a new thread in the Support section of the forums.

---

### Post by YannBuntu on 2021-12-28
To begin, here is a quick summary of the December updates:

ppa131: fixed [https://bugs.launchpad.net/boot-repair/+bug/1905578](https://bugs.launchpad.net/boot-repair/+bug/1905578) + added free spaces and gdisk sections to the Boot-Info report
ppa134: Boot-Repair will install grub-efi on an hidden ESP in one of the 2 following cases knowing that it prefers ESP located on the disc where the Linux we install grub-efi is:
1)  if it detects a WindowsEFI, and there is no normal ESP on the same disc as the hidden ESP
2)  if no Windows detected and there is no normal ESP on the same disc as the hidden ESP
ppa135: added an advice to remove the hidden flag in these cases
ppa138: removes the "Unknown MBRs" section from the boot-info report when grub-efi selected
and "StdErr Messages" et "Devices which don't seem to have a corresponding hard drive" , except if option --no-filter is enabled.
ppa139: improved gdisk filter + added mdadm & dmraid titles 
ppa140: no more select 'win-legacy-basic-fix' if grub-efi
ppa141: select grub-efi-signed by defaut only when SecureBoot is enabled in the firmware. 
ppa142: modifies GRUB_DISABLE_OS_PROBER=true to false by default , at the moment is included in the 'Display the boot menu' option, so enabled by default.
ppa143: solves empty pastebin  [https://paste2.org/](https://paste2.org/)  case
- extended the no more attempt to install grub-pc on GPT discs without bios-boot, blocks if main disc, silent for others (when install on several discs).
- remplace the purge grub*-common+shim-signed by the double command (grub-common* then grub2-common*) for compatibility with OS using grub-common:i386 and grub2-common:i386 packages

---

### Post by MAFoElffen on 2021-12-28
Welcome back.

I'm all-in to help...

---

### Post by oldfred on 2021-12-29
Also my welcome back.
I regularly update & noticed a lot of updates on the Boot-Repair packages.

Grub2 has now turned off os-prober for security reasons. 
One suggest was to just turn it on, run it once to get other boot stanza & then turn it off again.
Not sure how newer users would add Windows to grub menu otherwise.  I have preferred adding boot stanza to 40_custom, but that a bit more advanced.

Noticed next version of Ubuntu 22.04 will use grub 2.06, so we can expect more changes in 2022.

---

### Post by MAFoElffen on 2021-12-29
What do you needed tested and under what test conditions? 

I have various hardware to test on. I can also replicate quite a myriad of test machines in virtual... I can recreate quite a few "problems' for test cases. I just need some parameter direction and boundaries of 'what' you want to test against...

x86, amd64, arm32, arm64, Intel, AMD, ARM, Mac, etc...

---

### Post by YannBuntu on 2021-12-29
@ MAFoElffen : thx for your help. In [https://ubuntuforums.org/showthread.php?t=2465764&p=14054758#post14054758](https://ubuntuforums.org/showthread.php?t=2465764&p=14054758#post14054758) you indicated that boot-repair fails with ZFS. Please could you describe what's wrong ?

**ppa145:** as discussed with oldfred, if Windows detected, Boot-Repair will not install grub in all MBRs (but only in the mbr of the selected Linux drive).

TODO: if several Linux available, B-R should try to select one which is not on same drive as Windows. (in order to avoid installing grub in the mbr of the Windows drive)

---

### Post by YannBuntu on 2021-12-30
hi,
I've been reported a regression ('syntax error near unexpected token' which removes chroot prefix from the commands) since ppa142, that I don't find the origin, so I'm going to revert back to ppa141 and redo all gradually.
ppa150: reverted major changes done since Monday (i.e. purge commands update, non install if no BIOSboot, non install in all MBRs if Windows).
Compared to 141, I left the resolution of empty pastebin and GRUB_DISABLE_OS_PROBER=false.

---

### Post by MAFoElffen on 2021-12-31
> **YannBuntu said:**
> @ MAFoElffen : thx for your help. In [https://ubuntuforums.org/showthread.php?t=2465764&p=14054758#post14054758](https://ubuntuforums.org/showthread.php?t=2465764&p=14054758#post14054758) you indicated that boot-repair fails with ZFS. Please could you describe what's wrong ?

**ppa145:** as discussed with oldfred, if Windows detected, Boot-Repair will not install grub in all MBRs (but only in the mbr of the selected Linux drive).

TODO: if several Linux available, B-R should try to select one which is not on same drive as Windows. (in order to avoid installing grub in the mbr of the Windows drive)
Yes... 

Right before that I had helped two Forum Users to mount and re-install Grub to their Ubuntu on ZFS systems. (There was One additional was a problem with a Kernel update, which affected ZFS related kernel modules.) Both had tried to use the Boot Repair ISO unsuccessfully on them. As soon as they could mount their systems, then they could reinstall Grub.

Honestly, I haven't seen/gone through any of your code of boot repair... So I do not even know if you do ZFS, or what and how you deal with things yet... But I have always had a lot of respect for you and what you have done.

My test environment for Ama-gi has 5 different systems installed on 5 Virtual disks, which one is booting on ZFS... Which I test on. Since it tests for multiple installed systems, (parsing if each is Linux > Debian Branch > Ubuntu, etc,) while parsing and analyzing, I build a data structure of what is found, and store certain things on each (including filesystem types and managers) then use that data structure to give the user a choice on what system they want/need to chroot into... I use the info I store in that data-structure to do the mount and chroot into that filesystem or file manager (mdadm, lvm, zfs). At least, that is how I dealt with it in that...

You mentioned MBR... Then CSM boot on GPT... which then has the 'bios_grub' flagged partition where that Grub boot microcode resides, that would be on CSM MBR disks before.. Then hybrid disks that have both bios_grub and EFI partitions, and both legacy and EFI versions of Grub installed to GPT... Just thinking out loud.

---

### Post by oldfred on 2021-12-31
I really wish MBR would go away. 

The only place you have to have MBR, now is with Windows in BIOS mode. Which users should not be doing with new installs. Perhaps some old Windows 7 systems or updates to those would then still be BIOS/MBR. But those are now often 10 years old systems. A few downgraded Windows 9 to Windows 7, but those could have been UEFI.

Microsoft has required vendors to install in UEFI boot mode to gpt drives since 2012. 
But Ubuntu lets uses use UEFI on MBR and that often prevents grub from dual booting if Windows is BIOS as drive can only have one boot flag, either Windows boot partition or ESP with UEFI. Grub may boot Windows for short time if fast start up is off.

I started conversion to gpt 10 years ago. XP on MBR and new install of Ubuntu using gpt. 
When I knew I was eventually getting a new system with UEFI, I added both bios_grub & ESP to all new drives. But then you could only install one version of grub, grub-pc or grub-efi-amd64. I think sudodus had a work around where he installed one version then the other, but then eventually would get out of sync with updates.
Now I believe you can install both grub packages, but still only have one or the other installed.

---

### Post by YannBuntu on 2022-01-04
Happy new year !

ppa151: improved ZFS detection
**ppa152:** purge commands improvement, non install if no BIOSboot, non install in all MBRs if Windows

@MAFoElffen: please can you show the output of your script and the output of boot-info on your ZFS environment, so that we can compare ?

@oldfred: the Ubuntu installer (ubiquity) installs grub-pc in addition to grub-efi when signed, not sure why:
```
	case $grub_package in
	    *-signed)
		apt-install shim-signed || true
		apt-install grub-pc || true
		;;
	esac
```

---

### Post by oldfred on 2022-01-04
It used to be that Ubuntu only installed one grub, either grub-pc or grub-efi-amd64.
But then I saw somewhere that they were installing both. Not quite sure why?

---

### Post by MAFoElffen on 2022-01-06
@oldfred. On Post #11.

I admit that I "used to" do that. Now I try to stay and recommend GPT partitioning and UEFI booting. But some users are still using old hardware.

For me, with CSM or EFI, trying to stay BIOS dual boot capable between, that was years ago. The "reasoning" I did that on 'some' of my hardware, was on servers, where I had GPT disks that was on some Dell PowerEdge 2900's, where if I had a hardware failure, that I could take the disks and just put them in any of my other hardware, no matter whether they were CSM or UEFI boot, and they would boot and run. At the time, that seemed like a good fallback (LOL), but it turned out to be... not that much...

As time went by, everything new was UEFI, so falling back to a CSM machine would have been a step backward. That and all those drives were on Dell PERC RAID Controllers, which couldn't do JBOD, so all disks, if you wanted to treat then as single disks, had to be setup as single disk RAID0 arrays... So I only could go to one of my other servers that could ID that specific animal of through their hardware RAID controllers. (That was another side issue.).

Now a-days, I don't recommend it. Installing both grub-pc and grub-efi-amd64 is just  extra work for no reward. That it not even addressing the many drawbacks to MBR partitioning... Let alone to CSM only BIOS booting.

EDIT:
I 'have' seen new SSD's come with MBR partition tables still... Those SSD's were all 500GB and less. So  User's not knowing that, or to just start out setting a new disk with a  new, fresh GPT partition table, are still getting caught what that when  they try to add a 5th partition...

---

### Post by sudodus on 2022-01-06
Hi YannBuntu et. al.,

I just discovered this thread. It will be interesting to follow the discrussion.

Maybe I can help testing too, but at the moment I don't know what it would be ...

[hr][/hr]
Please post a link to the test version of Boot-Repair and the Boot-Info script. (I guess there is a test/unstable version somewhere.)

---

### Post by YannBuntu on 2022-01-07
hi Sudodus, good to see you here ! ):P

You can test all the configurations that come to your mind (multi-disc / multi-OS / exotic FS / SecureBoot or not ...) :
1) check that the [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") diagnosis is relevant, especially the 'Suggested repair' section at the very bottom.
2) check (preferably in VM) that the actual execution of this suggested repair (via [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")'s 'Recommended Repair' button) correctly works.

(FYI, there is a dev PPA, but I don't recommend to use it at the moment, wouldn't help)

---

### Post by sudodus on 2022-01-08
I installed the Boot-Info script and Boot-Repair into a current Lubuntu Jammy persistent live system.

Then I tested with a working system with two installed systems (installed in BIOS mode) in an old Toshiba laptop. Things worked as expected, the description was correct and Boot-Repair did not damage the system.

After that I did a lot to corrupt the systems (moved the partitions and booted the persistent live system in UEFI model). I ran Boot-Repair but it could not fix the system, not even after I created a FAT32 partition. Obviously this was way too much (I caused too much corruption).

Then I did something more reasonable: Created a fresh GPT with a FAT32 partition and an bios_grub partition. I installed Lubuntu Jammy in UEFI mode, and after that another Lubuntu Jammy system in BIOS mode. Boot-Repair could make the boot system recognize and use both systems.

[hr][/hr]
I noticed that the desktop environment's graphics of the running system (the persistent live Lubuntu Jammy) was corrupted after running the scripts. Is this typical or is it happening only in Jammy?

[hr][/hr]
I noticed also that **[FONT=Courier New]sudo update-grub[/FONT]** no longer finds and activates other operating systems unless
```

GRUB_DISABLE_OS_PROBER="true"
is changed to
GRUB_DISABLE_OS_PROBER="false"

```
in **[FONT=Courier New]/usr/sbin/grub-mkconfig[/FONT]**

I think this is a new feature (security-related), and we (who help here and may use Boot-Repair) should be aware of it.
[Edit 2: See this bug report.](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1955109)
[hr][/hr]
Edit: Please tell me a couple of typical corruptions (that happen to end users), where Boot-Repair should work, and I can create such corruptions and test if I can make Boot-Repair see them and make Boot-Repair fix them.

---

### Post by MAFoElffen on 2022-01-12
Well Dang...
[https://paste.ubuntu.com/p/wSbCmPqZGV/](https://paste.ubuntu.com/p/wSbCmPqZGV/)

This is a Default Ubuntu 20.04.3 EFI ZFS installation on an AMD64 KVM VM, that is booting fine.... I didn't add any errors to it yet. Any idea what "Error 32" is or should I research that and find out? It's recommending repairs... But aren't needed(?)

Here is the machine report from system-info:
```

Starting the Ubuntu Forums 'system-info' Report: 2022-01-12  01:28:14 PST (-0800)
    Part of the Ama-gi Project
    Version: 01.00-02, Script Date: 2021.12.06

---------------------------------------------------------------
Main Complaint: Test
Problem Description:  Test
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu:0
    Description: CPU
    Product: Intel Xeon E312xx (Sandy Bridge, IBRS update)
    Vendor: Intel Corp.
    Physical id: 400
    Bus info: cpu@0
    Version: pc-q35-4.2
    Slot: CPU 0
    Size: 2GHz
    Capacity: 2GHz
    Width: 64 bits
    Capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall 
        nx rdtscp x86-64 constant_tsc rep_good nopl xtopology cpuid 
        tsc_known_freq pni pclmulqdq vmx ssse3 cx16 pdcm pcid sse4_1 sse4_2 
        x2apic popcnt tsc_deadline_timer aes xsave avx hypervisor lahf_lm 
        cpuid_fault pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept 
        vpid tsc_adjust xsaveopt arat umip md_clear arch_capabilities
    Configuration: cores=1 enabledcores=1 threads=1
*-Cpu:1
    Description: CPU
    Product: Intel Xeon E312xx (Sandy Bridge, IBRS update)
    Vendor: Intel Corp.
    Physical id: 401
    Bus info: cpu@1
    Version: pc-q35-4.2
    Slot: CPU 1
    Size: 2GHz
    Capacity: 2GHz
    Width: 64 bits
    Capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall 
        nx rdtscp x86-64 constant_tsc rep_good nopl xtopology cpuid 
        tsc_known_freq pni pclmulqdq vmx ssse3 cx16 pdcm pcid sse4_1 sse4_2 
        x2apic popcnt tsc_deadline_timer aes xsave avx hypervisor lahf_lm 
        cpuid_fault pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept 
        vpid tsc_adjust xsaveopt arat umip md_clear arch_capabilities
    Configuration: cores=1 enabledcores=1 threads=1

computer
    Description: Computer
    Product: Standard PC (Q35 + ICH9, 2009)
    Vendor: QEMU
    Version: pc-q35-4.2
    Width: 64 bits
    Capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    Configuration:
        boot=normal
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         EFI Development Kit II / OVMF
Bios Version:        0.0.0
Bios Release:        0.0

Current boot mode:   UEFI Firmware mode
SecureBoot disabled
Platform is in Setup Mode


---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       2.9Gi       253Mi        10Mi       662Mi       681Mi
Swap:         922Mi       1.0Mi       921Mi

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: MAF-PC-Q35-ICH9-2009


---------- File system specs from 'df -h':
Filesystem                                       Type      Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_64fs0l                         zfs        15G  3.5G   12G  24% /
rpool/USERDATA/mafoelffen_7vzpaq                 zfs        12G  3.2M   12G   1% /home/mafoelffen
rpool/USERDATA/root_7vzpaq                       zfs        12G  256K   12G   1% /root
rpool/ROOT/ubuntu_64fs0l/var/games               zfs        12G  128K   12G   1% /var/games
rpool/ROOT/ubuntu_64fs0l/var/mail                zfs        12G  128K   12G   1% /var/mail
rpool/ROOT/ubuntu_64fs0l/var/lib                 zfs        13G  863M   12G   7% /var/lib
rpool/ROOT/ubuntu_64fs0l/var/log                 zfs        12G  2.7M   12G   1% /var/log
rpool/ROOT/ubuntu_64fs0l/var/snap                zfs        12G  640K   12G   1% /var/snap
rpool/ROOT/ubuntu_64fs0l/srv                     zfs        12G  128K   12G   1% /srv
rpool/ROOT/ubuntu_64fs0l/var/www                 zfs        12G  128K   12G   1% /var/www
rpool/ROOT/ubuntu_64fs0l/usr/local               zfs        12G  128K   12G   1% /usr/local
rpool/ROOT/ubuntu_64fs0l/var/spool               zfs        12G  128K   12G   1% /var/spool
rpool/ROOT/ubuntu_64fs0l/var/lib/apt             zfs        12G   84M   12G   1% /var/lib/apt
rpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService zfs        12G  128K   12G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager  zfs        12G  256K   12G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_64fs0l/var/lib/dpkg            zfs        12G   36M   12G   1% /var/lib/dpkg
bpool/BOOT/ubuntu_64fs0l                         zfs       655M  206M  450M  32% /boot
/dev/vda1                                        vfat      511M   14M  498M   3% /boot/grub
/dev/sr0                                         iso9660   2.9G  2.9G     0 100% /media/mafoelffen/Ubuntu 20.04.3 LTS amd64

---------- Disk/Partition Information From 'fdisk':

Disk /dev/vda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4BD32A91-14FF-40C9-8092-0277030D90F5

Device       Start      End  Sectors  Size Type
/dev/vda1     2048  1050623  1048576  512M EFI System
/dev/vda2  1050624  2940927  1890304  923M Linux swap
/dev/vda3  2940928  4984831  2043904  998M Solaris boot
/dev/vda4  4984832 41943006 36958175 17.6G Solaris root

---------- Disk/Partition Information From 'lsblk':
NAME    SIZE FSTYPE     LABEL                    MOUNTPOINT                                 MODEL
sr0     2.9G iso9660    Ubuntu 20.04.3 LTS amd64 /media/mafoelffen/Ubuntu 20.04.3 LTS amd64 QEMU_DVD-ROM
vda      20G zfs_member rpool                                                               
|-vda1  512M vfat                                /boot/grub                                 
|-vda2  923M swap                                [SWAP]                                     
|-vda3  998M zfs_member bpool                                                               
`-vda4 17.6G zfs_member rpool                                                               
   ------- 'lsblk' information continued ...
NAME   HOTPLUG PARTUUID                             UUID
sr0          1                                      2021-08-19-11-03-38-00
vda          0                                      11989003535406521883
|-vda1       0 8a44c030-0723-40df-b1ab-51280a5fcf1e FF71-A6FE
|-vda2       0 f47b0331-0704-6e49-9e21-0515611c582a 1d4f42f7-d8fe-4536-92f0-1dcf1422d394
|-vda3       0 e4f84806-109c-fc4e-b5e8-913884780152 6409571740606934475
`-vda4       0 d7df17c7-df9f-d343-81f6-5949b2c22f59 11989003535406521883

---------- Mount Details of '/etc/fstab':
UUID=FF71-A6FE  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub    /boot/grub    none    defaults,bind    0    0
UUID=1d4f42f7-d8fe-4536-92f0-1dcf1422d394    none    swap    discard    0    0

---------- Current Mount Details of 'mount':
/dev/fuse on /root/.cache/doc type fuse (rw,nosuid,nodev,relatime,user_id=0,group_id=0)
/dev/sr0 on /media/mafoelffen/Ubuntu 20.04.3 LTS amd64 type iso9660 (ro,nosuid,nodev,relatime,nojoliet,check=s,map=n,blocksize=2048,uid=1000,gid=1000,dmode=500,fmode=400,iocharset=utf8,uhelper=udisks2)
/dev/vda1 on /boot/grub type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

---------- USB Information from 'lsusb -t -v':
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 480M
        ID 0627:0001 Adomax Technology Co., Ltd 

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: QXL paravirtual graphic card
       vendor: Red Hat, Inc.
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master rom
       configuration: driver=qxl latency=0
       resources: 
           irq:21 
           memory:c4000000-c7ffffff 
           memory:c0000000-c3ffffff 
           memory:c8c84000-c8c85fff 
           ioport:1040(size=32) 
           memory:c0000-dffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
Virtual-1 connected primary 1024x768+0+0 0mm x 0mm
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru'
The Current Virtual TTYs being used are:
    TTY#    Used By
    tty2    gdm-x-session
    tty2    Xorg
    tty2    gnome-session-b

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-focal.list:
deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal main

---------- Other Details from 'Various':
The current kernel version is:       5.11.0-46-generic 
The current release description is:  Ubuntu 20.04.3 LTS 
Original Installation Date:          2022-01-12+00:21:00 
Original Installation Media: Ubuntu 20.04.3 LTS "Focal Fossa" - Release amd64 (20210819)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.11.0.46.51
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
Package linux-generic-hwe-20.04 is installed.

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
mafoelffen :0           Jan 12 00:47 (:0)

The User running this script was: mafoelffen
uid=1000(mafoelffen)
gid=1000(mafoelffen)
groups=1000(mafoelffen),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
120(lpadmin),132(lxd),133(sambashare)

---- Required Programs For Report.
    All required programs installed for report. 

*** End Of Report ***

```

That is from the script from the PPA... I could run that to one of my ZFS-on-root Server images, because I don't have X installed to them, but I can run a Boot-Repair ISO on them... Would you like me too? Or I can install a minimal X to them to test on.(?)

---

### Post by MAFoElffen on 2022-01-13
This is just a test, that I don't think will appear, but does open other possibilities:
[https://pastebin.ubuntu.com/p/7GynDCfG2b/](https://pastebin.ubuntu.com/p/7GynDCfG2b/)

It  does identify that it was booted as EFI, but is misidentifying if it  has an ESP or not. Because of that, it misdiagnoses the repair, missing  that is has grub-efi-arm64-signed installed. (so is recommending purging  and (re)installing grub-pc?)

Here is a machine report::
[https://pastebin.ubuntu.com/p/rh53Q7BSPn/](https://pastebin.ubuntu.com/p/rh53Q7BSPn/)

---

### Post by oldfred on 2022-01-13
Is that an Arm system?
And ESP is FAT16.
FAT16 is allowed but was more for tiny devices. Ubuntu was in the very beginning using FAT16 for everything but then changed to FAT32.

---

### Post by MAFoElffen on 2022-01-13
Yes it is... LOL

It was installed from 18.04 LTS Server ARM64 ISO. It was release upgraded to 20.04 LTS. It is an Ubuntu ARM64 Server with a minimal X and LXQT installed so I could run the boot-info script on it.

I created it originally to test the system-info script on...

---

### Post by YannBuntu on 2022-01-13
Thx MAF for your feedback. wow, that's challenging configs! 

1st case: l.11 bootinfoscript doesn't list the partitions
l.15 partition missing
l.26  output of df -Th / is empty !! how can this be?
l.400: errors code 32 , shouldn't try to mount these.

2nd case:
l20: bootinfoscript doesn't list the LVM volumes
l66: the ESP is not recognized correctly, with the consequence you mention on the suggested repair.

You gave me work for several weeks ;-)

---

### Post by MAFoElffen on 2022-01-14
> **YannBuntu said:**
> Thx MAF for your feedback. wow, that's challenging configs! 

1st case: l.11 bootinfoscript doesn't list the partitions
l.15 partition missing
l.26  output of df -Th / is empty !! how can this be?
l.400: errors code 32 , shouldn't try to mount these.

2nd case:
l20: bootinfoscript doesn't list the LVM volumes
l66: the ESP is not recognized correctly, with the consequence you mention on the suggested repair.

You gave me work for several weeks ;-)

On 1st Case, Line 26, compare that with it's system-info report, under the heading "---------- File system specs from 'df -h':" 

Would it help if I share an early-version  mount/chroot script I have in the Ama-Gi Project for ZFS file manager systems? I identify ZFS from the results from fdisk where both "Solaris_root" and  "Solaris_boot" types exist... As you can see in it's system-info report under the heading "---------- Disk/Partition Information From 'fdisk':". 

This was early work, that I haven't gotten back to yet, but should give you some ideas:
```

#!/bin/bash
# MAFoElffen <mafoelffen@ubuntu.com> 2021.08.18
# This should work for a LiveCD that has a read-only filesystem
# This will only work if we have already confirmed that Solaris_root and Solaris_boot exists.
#
#########################################################################
#  Copyright (c) 2012, 2021
#
#  GNU General Public Llicense (GPL-3.0-or-later)
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

echo "This LiveCD already has OpenSSH Server installed, With a default user and password. 
    Reminder: Use the \"ubuntu\" user and the \"ubuntu\" as password."

# View and display IP Adresss
ip addr show scope global  | grep -E 'inet ' | grep -v br0
echo "You can use the address shown above to ssh remotely into this machine"
pause = input -p "Press any key to continue..."

echo "Configuring Temporary ZFS Environment"
echo "Becoming root"
sudo -i

echo "Installing ZFS in the Live CD environment"
apt-add-repository universe
echo "Ignore any errors on the following, about moving an old database out of the way..."
apt update
apt install --yes debootstrap gdisk zfs-initramfs

# Check if it has existing datasets or "no datasets available" 
test1 = zpool lists | grep -q 'no datasets'    # If output, then export
test2 = zfs list | grep -q 'no datasets'       # If output, then export
if [ $test1 ]; then
    echo "Existing Datasets found. Exporting rpool."
    zpool export rpool
    elfi [ $test2 ]; then
        echo "Existing Datasets found. Exporting rpool."
        zpool export rpool
    else
        echo "No existing Datasets found."
fi
    
# Chroot into ZFS pool. Import pool to non-default location. The -N flag means 'don&#8217;t automatically mount' and is necessary,
#     otherwise the rpool root, and the rpool/root/UBUNTU pool, will both try to mount on /mnt.
echo "Importing the Pools"
zpool import -N -R /mnt rpool

echo "Mounting the root system"
zfs mount rpool/ROOT/ubuntu

echo "Mounting the remaining file systems"
zfs mount -a

# Bind the virtual filesystems from the LiveCD environment to the new system and chroot into it:
echo "Mounting the virtual filesystems"
mount --rbind /dev  /mnt/dev
mount --rbind /proc /mnt/proc
mount --rbind /sys  /mnt/sys
echo "chrooting into the mounted system"
chroot /mnt /bin/bash --login

# After exiting chroot, shutdown ZFS filesystems cleanly, unmount all ZFS pools, unmount all mounts and reboot
zfs umount rpool/ROOT/ubuntu
zpool export rpool
umount /mnt
reboot

```

---

### Post by sudodus on 2022-01-14
@ everybody,

*Please describe a couple of **typical corruptions** (that happen to end users)*, where Boot-Repair should work, and I can create such corruptions (and variations around them) and test if I can make Boot-Repair see them and make Boot-Repair fix them.

---

### Post by MAFoElffen on 2022-01-14
I think where I see most of the problem with boot-info and boot-repair is when the system has multiple operating systems and multiple disks.

I think some of the common issues "lately", don't specifically have to do with Ubuntu or Linux... But that in conjunction "with" the  installation of Ubuntu or other Linux, that Windows 10 or Windows 11 is installed... of those, that splits off to where Windows does not want to boot, or where Windows wants to be the only booted... Some of these occur when there is a Windows Update...

Next is where there are multiple versions of a Linux Distribution, where those distributions both/all use Grub... So there are multiple versions of Grub installed. Most of the time for those, the challenge is trying to figure out which of the OS'es installations was installed last, and has taken over being the primary boot of Grub. Because that one it the one that will update the Grub Boot Menu, in that case, if there are special boot parameters needed for the Other OS, then we usually recommend (as oldfred mentioned) that it be split off in the menu as a 40_ Custom menu item so those boot parameters are honored. A lot of those sometimes get hosed when there is an update of one or the other.

I think next is where, there was in the past, one of the disks was MBR/CSM, then later moved to another computer as GPT/UEFI.... Then it shows a leftover MBR record that is still there, but booting off of EFI, and sometimes gets confused on what to recommend to solve...

There are more... But those are the ones that stand out in my memory, off the top of my head... oldfred probably can relate many more to add to that list...

And Yann probably has a lot e has in mind, from users emaillng the boot-info support email address, right?

---

### Post by sudodus on 2022-01-14
Thanks MAFoElffen :-)

---

### Post by oldfred on 2022-01-14
I see this a lot:
> Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
In beginning I was not sure what it was. I believe it is how many USB flash drives are written, so not really an issue.
Recent example From this pastebin before it expires.
[https://ubuntuforums.org/showthread.php?t=2470854](https://ubuntuforums.org/showthread.php?t=2470854)
[https://paste.ubuntu.com/p/7MhrSH2xtB/](https://paste.ubuntu.com/p/7MhrSH2xtB/)

Above also has this, but user has 20.04 :
> Warning: this will install necessary packages from Ubuntu-22.04 repositories. Please backup your data before this operation.


---

### Post by MAFoElffen on 2022-01-15
> **oldfred said:**
> 

Above also has this, but user has 20.04 :
> 
Warning: this will install necessary packages from Ubuntu-22.04 repositories. Please backup your data before this operation.                           
 


???
```

User settings: _________________________________________________________________

Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Warning: this will install necessary packages from Ubuntu-22.04 repositories. Please backup your data before this operation.
The settings chosen by the user will reinstall the grub-efi-amd64-signed of
sda2,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file


/boot/efi added in sda2/fstab
Mount sda1 on /mnt/boot-sav/sda2/boot/efi

Unhide GRUB boot menu in sda2/etc/default/grub

```
I have a bunch of test machines on 22.04... And I am trying to get the Ama-Gi Project LiveCD ready for it... But why would it say that on a 20.04 machine? That "is" just... "odd".

I did find this on the first "Warning" message, which like oldfred said, is about the USB thumb drive used to boot the machine:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1708881](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1708881)
To fix that (is located in #2) wipes out whatever is there, but fixes the erroneous descriptor on the thumb drive...

The fix for the thumb drive is:
```

sudo wipefs --all /dev/sdX

```
Which would wipe out all data on that thumb drive... Is the second "warning" message also related to a fix of that thumb drive? (Which is not related to a fix of the installed system it is trying to diagnose...) I can see where that would confuse, worry and scare the User...

EDIT:
I think and feel, that maybe what the system is booted "from" should be ID'ed and isolated in the report of problems... It can still be reported, but I think that if it is ID'ed as being "from where," that it reflects higher on the script to ID that that as a sideline issue. I think that would reflect higher confidence in the script, to point that out as such. So that if there is a problem with the boot media, that it doesn't confuse the User and any Helpers, that it is related to the installed system's problems. That would be *more clear* and give the User more confidence in what is going on, and in the recommendations being made... Instead of something that might be confused is a sideline issue with the diagnostic tool itself. This has nothing to do with the boot-info script or the Boot-Repair ISO, but rather in some media creation tools that the User used to create the bootable media.

Note: Even if the ID of the booted media was a one-liner saying something like: "The system was temporarily booted from USB Media identified as /dev/sdX." and using that to isolate that in later recommendations(?)

Just an idea...

---

### Post by MAFoElffen on 2022-01-16
Okay... I have a live test, with a User... boot-info results are on this post:
[https://ubuntuforums.org/showthread.php?t=2470789&p=14075663#post14075663](https://ubuntuforums.org/showthread.php?t=2470789&p=14075663#post14075663)

Is UEFI. It keeps booting an old kernel. update-grub does not change the booted Grub Menu... Has both the files menu.lst and grub.cfg within /boot/grub/. I was thinking that maybe it had both Grub and Grub2 installed and that is was confused... The repsence of one or the other file used to be how to identify Grub or Grub2, right? It prints out the menu.lst file in the boot-info report... It was installed as Server 18.04 and release-upgraded to 20.04.

I thought this was odd and definitive, but... When I was looking at that Arm64 Server that I posted a few posts back. It was also installed as Server 18.04, and was release-upgraded to 20.04. It also has both files menu.lst and grub.cfg in /boot/grub/... But it is working fine. And in the boot-info report I posted for it, it did not include the menu.lst file in that report(?) Hmmm.

EDIT:
This User's problem was Solved. Problem was actually that his /boot somehow along the way got commented out in the fstab, so was not getting mounted... But it still 'booted' the system.

---

### Post by TheFu on 2022-01-16
Can I ask a dumb question?  Where do we find the alpha versions of the updated tools?  Is there a link that I missed?

> **oldfred said:**
> I really wish MBR would go away. 
 

Me too. The last time I installed 20.04 with LVM, it still was using MBR by default, not GPT, so we need to get the Ubuntu installers to stop pushing MBR partition tables.  The parted -lm from that system.
```
BYT;
/dev/vda:32.2GB:virtblk:512:512:msdos:Virtio Block Device:;
1:1049kB:538MB:537MB:fat32::boot;
2:539MB:32.2GB:31.7GB:::;
5:539MB:32.2GB:31.7GB:::lvm;

```

I do recall an install after that time, 21.04 perhaps, that used GPT. I *cried tears of joy* when I saw it. I was soooooo happy.
I have a number of older systems - *new* is an enemy to me and my data.  Happy to run boot-info on them all.

---

### Post by MAFoElffen on 2022-01-16
> **TheFu said:**
> Can I ask a dumb question?  Where do we find the alpha versions of the updated tools?  Is there a link that I missed?
Through the instructions pointing to the PPA here:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Which points to Yann's PPA:
[https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)

Which is what we are testing, and where Yann is making the changes to...

-------------------------------------------------------------------------------------------------
I am still finding that a lot on CSM systems. It's almost like install scripts (Both Linux and Windows) assume that if not booted EFI, then people should use MBR. I have a disk here now, that I have to get around to converting for someone... I've tried to use GPT exclusively for my own for almost 12 years now... I still get caught sometimes, forgetting or assuming.

---

### Post by YannBuntu on 2022-01-19
hi all

New version to be tested: **ppa166** in the dev ppa  ( ppa:yannubuntu/boot-repair**-dev**  ).

changelog:
  * remove useless Warning grub upgrade from log (keep it as popup when users selects the option)
  * when zfs, add partitions from mount
  * filter 'Warning: The driver descriptor says' lines from log (unless --no-filter)
  * improved EFi section of boot-info
  * removed options to install grub on all MBRs and to force in PBR
  * improved grub*.efi detection
  * improve ESP detection on vda
  * made df / compatible with zfs
  * display blkid when lvm/raid/zfs
  * in boot-info hide identic consecutive lines of grub.cfg
  * hide 'Warning: Unable to open '
  * no more purge when both grub-pc and grub-efi, nor to unsign
  * improved filters when zfs
  * replaced gdisk -l by sgdisk -p
  * cleaned pastebinaction
  * --no-nvram instead of -recheck when grub-efi

---

### Post by YannBuntu on 2022-01-21
ppa169  (in the standard ppa)
 * improved partition detection for >10 partitions systems

4ppa168
  * added a translatable string
  * remove useless 'Grub-efi WIOULD not be selected by default because' when user forced grub-pc
  * refined "Warning: NVram was not modified." condition for Mint
  * solved GUI delay when clicking Advanced options
  * added fat option to os-uninstaller
  * removed advanced option to skip report creation

---

### Post by MAFoElffen on 2022-01-22
Here is the pastebin for the ZFS machine:
[https://paste.ubuntu.com/p/4DSCchsdSs/](https://paste.ubuntu.com/p/4DSCchsdSs/)

I didn't try a repair yet... But this time it didn't throw any errors so far... 

On my way into work.

---

### Post by TheFu on 2022-01-22
> **MAFoElffen said:**
> Here is the pastebin for the ZFS machine:
[https://paste.ubuntu.com/p/4DSCchsdSs/](https://paste.ubuntu.com/p/4DSCchsdSs/)

I didn't try a repair yet... But this time it didn't throw any errors so far... 

On my way into work.

```
You need to be logged in to view this paste.
```
Any idea when that changed?

---

### Post by YannBuntu on 2022-01-22
@MAF: thx! i just released ppa171 in the standard ppa, please can you create 3 new boot-info with it on your zfs system: one normal in installed session + 1normal from a fresh live-session, and 1 in debug mode (sudo boot-info -d)  from a different fresh live-session (reboot between each so that zfs activation isn't polluted by previous one).
Also, do you manage to manually reinstall grub in your zfs from a live session ? how?

---

### Post by MAFoElffen on 2022-01-23
@YannBuntu

Yes I will. On my way into work right now (closing shift). I have tomorrow off.

@TheFu

I think it's been within the last year or so. I'm still used to how it used to be- going right there to a pastebin. It's new enough that it still confuses me when I go there.

---

### Post by MAFoElffen on 2022-01-24
Of the three 4ppa171 Reports (fresh boot in between each...

From the installed system:
[https://paste.ubuntu.com/p/S7pjmp7SbN/](https://paste.ubuntu.com/p/S7pjmp7SbN/)

From an Ubuntu 20.04.3 LiveCD:
[https://paste.ubuntu.com/p/nmMHRxqGmh/](https://paste.ubuntu.com/p/nmMHRxqGmh/)

From a different Live Session In debug mode:
[https://paste.ubuntu.com/p/JvPM4qqPRb/](https://paste.ubuntu.com/p/JvPM4qqPRb/)

And here were the debug messages in the terminal:
```

ubuntu@ubuntu:~$ boot-info -d
Root privileges are required to run boot-info -d
ubuntu@ubuntu:~$ sudo boot-info -d
[debug]Delete the content of TMP_FOLDER_TO_BE_CLEARED
[debug]Mount all blkid partitions except the ones already mounted and BIOS_Boot
[debug]BLKIDMNT_POINT of vda1 is: /mnt/boot-sav/vda1
[debug]BLKIDMNT_POINT of vda3 is: /mnt/boot-sav/zfs
[debug]BLKIDMNT_POINT of vda4 is: /mnt/boot-sav/zfs
[debug]PART_UUID of vda1 is FF71-A6FE
[debug]PART_UUID of vda3 is 6409571740606934475
[debug]PART_UUID of vda4 is 11989003535406521883
[debug] BYTES_BEFORE_PART[1] (vda) = 2048 sectors * 512 bytes = 1048576 bytes.
[debug]Mount all blkid partitions except the ones already mounted and BIOS_Boot
[debug]BLKIDMNT_POINT of vda1 is: /mnt/boot-sav/vda1
[debug]BLKIDMNT_POINT of vda3 is: /mnt/boot-sav/zfs
[debug]BLKIDMNT_POINT of vda4 is: /mnt/boot-sav/zfs
[debug]PART_WITH_OS of vda1 : no-os
[debug]PART_WITH_OS of vda3 : no-os
[debug]PART_WITH_OS of vda4 : no-os
[debug]/var/log/boot-info/20220124_063649/vda/partition_table.dmp created
[debug] vda1 ends at 537918976GB. not-far
[debug] vda3 ends at 2552233472GB. not-far
[debug] vda4 ends at 21474819072GB. not-far
[debug] vda4 ends at 21474819072GB. not-far
[debug] ECHO_SUMEFI_SECTION
[debug]TARGET_PARTITION_IS_AVAILABLE[vda] is : yes
[debug]combobox_ostoboot_bydefault_fillin
[debug]MAIN_MENU becomes : Boot-Info
[debug]CHOSEN_KERNEL_OPTION becomes : nomodeset
[debug] debug_echo_important_variables
[debug]MAIN_MENU becomes : Boot-Info
[debug]DISABLEWEBCHECK1 becomes :  disable-internet-check
[debug]MAIN_MENU becomes : Boot-Info
[debug] debug_echo_important_variables
[debug] first_actions=action before removal (if os-un)
[debug] actions_final=action after removal (if os-un)
[debug] unmount_all_and_success_br_and_bi
[debug] bis
[debug] Check_prg
[debug] Add raid if any
[debug] List mount
[debug] for /dev/vda
[debug] Identifying MBRs...
[debug] Store and display partition tables
[debug] deactivate dmraid if activated by the script
[debug] Search lvm
[debug] Search mdraid
[debug] Search fs hd
[debug] os detected
[debug] systinfo
[debug] check efidmsg
[debug] ECHO_SUMEFI_SECTION
[debug] print fdisk
[debug] print parted
[debug] print free space
[debug] print sgdisk -p
[debug] print blkid
[debug] print df / findmnt
[debug] print mount options
[debug] by-id
[debug] ls mapper
[debug] unknown mbrs
[debug]internet: connected
[debug]Unmount all blkid partitions except df ones
[debug]unmount /mnt/boot-sav/vda1
[debug]internet: connected

```

On how do I reinstall grub to an installed system, from I LiveCD... Why don't I show you. That might be easier to explain that way. 

I'll do that in another post. Let put that together.

---

### Post by MAFoElffen on 2022-01-24
I just re-installed Grub to that that ZFS system from a LiveCD...

Here was my terminal Log for that, showing all commands and the output:
```

ubuntu@ubuntu:~$ sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

Disk /dev/vda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4BD32A91-14FF-40C9-8092-0277030D90F5

Device       Start      End  Sectors  Size Type
/dev/vda1     2048  1050623  1048576  512M EFI System
/dev/vda2  1050624  2940927  1890304  923M Linux swap
/dev/vda3  2940928  4984831  2043904  998M Solaris boot
/dev/vda4  4984832 41943006 36958175 17.6G Solaris root
ubuntu@ubuntu:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
NAME    SIZE FSTYPE     LABEL                    MOUNTPOINT                   MODEL
loop0     2G squashfs                            /rofs                        
sr0     2.9G iso9660    Ubuntu 20.04.3 LTS amd64 /cdrom                       QEMU_DVD-ROM
vda      20G zfs_member tmprpool                                              
&#9500;&#9472;vda1  512M vfat                                                             
&#9500;&#9472;vda2  923M swap                                [SWAP]                       
&#9500;&#9472;vda3  998M zfs_member tmpbpool                                              
&#9492;&#9472;vda4 17.6G zfs_member tmprpool                                              
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# apt-add-repository universe
'universe' distribution component enabled for all sources.
Ign:1 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal InRelease
Hit:2 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal Release
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease         
Hit:5 http://archive.ubuntu.com/ubuntu focal InRelease                   
Get:6 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [677 kB]
Hit:7 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Get:8 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8,628 kB]
Get:9 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [115 kB]
Get:10 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66.3 kB] 
Get:11 http://security.ubuntu.com/ubuntu focal-security/universe DEP-11 48x48 Icons [33.1 kB]   Get:14 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [13.0 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal/universe Translation-en [5,124 kB]              
Get:16 http://archive.ubuntu.com/ubuntu focal/universe amd64 DEP-11 Metadata [3,603 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal/universe DEP-11 48x48 Icons [3,016 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal/universe DEP-11 64x64 Icons [7,794 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal/universe DEP-11 64x64@2 Icons [44.3 kB]
Get:20 http://archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
Get:21 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [894 kB]
Get:22 http://archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [196 kB]
Get:23 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [364 kB]
Get:24 http://archive.ubuntu.com/ubuntu focal-updates/universe DEP-11 48x48 Icons [221 kB]
Get:25 http://archive.ubuntu.com/ubuntu focal-updates/universe DEP-11 64x64 Icons [396 kB]
Get:26 http://archive.ubuntu.com/ubuntu focal-updates/universe DEP-11 64x64@2 Icons [29 B]
Get:27 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [20.0 kB]
Fetched 31.5 MB in 6s (5,024 kB/s)                                                                     
Reading package lists... Done
root@ubuntu:~# apt update
Ign:1 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal InRelease
Hit:2 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal Release
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease         
Hit:5 http://archive.ubuntu.com/ubuntu focal InRelease                   
Hit:6 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
265 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@ubuntu:~# apt install --yes debootstrap gdisk zfs-initramfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdisk is already the newest version (1.0.5-1).
gdisk set to manually installed.
The following additional packages will be installed:
  libnvpair1linux libuutil1linux libzfs2linux libzpool2linux zfsutils-linux
Suggested packages:
  arch-test squid-deb-proxy-client nfs-kernel-server samba-common-bin
The following NEW packages will be installed:
  debootstrap
The following packages will be upgraded:
  libnvpair1linux libuutil1linux libzfs2linux libzpool2linux zfs-initramfs zfsutils-linux
6 upgraded, 1 newly installed, 0 to remove and 259 not upgraded.
Need to get 1,526 kB of archives.
After this operation, 302 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 debootstrap all 1.0.118ubuntu1.6 [39.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 zfs-initramfs amd64 0.8.3-1ubuntu12.13 [23.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 zfsutils-linux amd64 0.8.3-1ubuntu12.13 [354 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libuutil1linux amd64 0.8.3-1ubuntu12.13 [41.7 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libzfs2linux amd64 0.8.3-1ubuntu12.13 [207 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libzpool2linux amd64 0.8.3-1ubuntu12.13 [812 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libnvpair1linux amd64 0.8.3-1ubuntu12.13 [48.3 kB]
Fetched 1,526 kB in 2s (905 kB/s)       
Selecting previously unselected package debootstrap.
(Reading database ... 190714 files and directories currently installed.)
Preparing to unpack .../0-debootstrap_1.0.118ubuntu1.6_all.deb ...
Unpacking debootstrap (1.0.118ubuntu1.6) ...
Preparing to unpack .../1-zfs-initramfs_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking zfs-initramfs (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../2-zfsutils-linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking zfsutils-linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../3-libuutil1linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking libuutil1linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../4-libzfs2linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking libzfs2linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../5-libzpool2linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking libzpool2linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Unpacking libnvpair1linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Setting up debootstrap (1.0.118ubuntu1.6) ...
Setting up libuutil1linux (0.8.3-1ubuntu12.13) ...
Setting up libnvpair1linux (0.8.3-1ubuntu12.13) ...
Setting up libzfs2linux (0.8.3-1ubuntu12.13) ...
Setting up libzpool2linux (0.8.3-1ubuntu12.13) ...
Setting up zfsutils-linux (0.8.3-1ubuntu12.13) ...
zfs-import-scan.service is a disabled or a static unit, not starting it.
zfs-import-scan.service is a disabled or a static unit, not starting it.
Setting up zfs-initramfs (0.8.3-1ubuntu12.13) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for systemd (245.4-4ubuntu3.11) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs is disabled since running on read-only media
root@ubuntu:~# zpool list
no pools available
root@ubuntu:~# zfs list
no datasets available
root@ubuntu:~# zpool import -N -R /mnt tmprpool
root@ubuntu:~# zfs list
NAME                                                  USED  AVAIL     REFER  MOUNTPOINT
tmprpool                                             7.81G  9.15G       96K  /mnt/mnt/boot-sav/zfs
tmprpool/ROOT                                        7.78G  9.15G       96K  none
tmprpool/ROOT/ubuntu_64fs0l                          7.78G  9.15G     3.52G  /mnt
tmprpool/ROOT/ubuntu_64fs0l/srv                       152K  9.15G       96K  /mnt/srv
tmprpool/ROOT/ubuntu_64fs0l/usr                       408K  9.15G       96K  /mnt/usr
tmprpool/ROOT/ubuntu_64fs0l/usr/local                 312K  9.15G      128K  /mnt/usr/local
tmprpool/ROOT/ubuntu_64fs0l/var                      1.81G  9.15G       96K  /mnt/var
tmprpool/ROOT/ubuntu_64fs0l/var/games                 152K  9.15G       96K  /mnt/var/games
tmprpool/ROOT/ubuntu_64fs0l/var/lib                  1.78G  9.15G     1.57G  /mnt/var/lib
tmprpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService   352K  9.15G      104K  /mnt/var/lib/AccountsService
tmprpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager    588K  9.15G      132K  /mnt/var/lib/NetworkManager
tmprpool/ROOT/ubuntu_64fs0l/var/lib/apt               106M  9.15G     83.8M  /mnt/var/lib/apt
tmprpool/ROOT/ubuntu_64fs0l/var/lib/dpkg             61.2M  9.15G     36.4M  /mnt/var/lib/dpkg
tmprpool/ROOT/ubuntu_64fs0l/var/log                  21.0M  9.15G     7.55M  /mnt/var/log
tmprpool/ROOT/ubuntu_64fs0l/var/mail                  152K  9.15G       96K  /mnt/var/mail
tmprpool/ROOT/ubuntu_64fs0l/var/snap                 1.12M  9.15G      904K  /mnt/var/snap
tmprpool/ROOT/ubuntu_64fs0l/var/spool                 360K  9.15G      112K  /mnt/var/spool
tmprpool/ROOT/ubuntu_64fs0l/var/www                   152K  9.15G       96K  /mnt/var/www
tmprpool/USERDATA                                    12.0M  9.15G       96K  /mnt
tmprpool/USERDATA/mafoelffen_7vzpaq                  11.4M  9.15G     3.82M  /mnt/home/mafoelffen
tmprpool/USERDATA/root_7vzpaq                         492K  9.15G      160K  /mnt/root
root@ubuntu:~# zfs mount tmprpool/ROOT/ubuntu_64fs0l
root@ubuntu:~# zfs mount tmprpool/ROOT/ubuntu_64fs0l
root@ubuntu:~# zfs mount -a
root@ubuntu:~# mount --rbind /dev  /mnt/dev
root@ubuntu:~# mount --rbind /proc /mnt/proc
root@ubuntu:~# mount --rbind /sys  /mnt/sys
root@ubuntu:~# chroot /mnt /bin/bash --login
root@ubuntu:/# ls
bin   cdrom  etc   lib    lib64   media  opt   root  sbin  srv  tmp  var
boot  dev    home  lib32  libx32  mnt    proc  run   snap  sys  usr
root@ubuntu:/# ls /boot/efi
ls: cannot access '/boot/efi': No such file or directory
root@ubuntu:/# ls /boot
root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot/efi was on /dev/vda1 during installation
UUID=FF71-A6FE  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub    /boot/grub    none    defaults,bind    0    0
UUID=1d4f42f7-d8fe-4536-92f0-1dcf1422d394    none    swap    discard    0    0
root@ubuntu:/# mkdir /boot/efi
root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# mount -a
root@ubuntu:/# mount
tmprpool/ROOT/ubuntu_64fs0l on / type zfs (rw,relatime,xattr,posixacl)
tmprpool/USERDATA/mafoelffen_7vzpaq on /home/mafoelffen type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/srv on /srv type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/log on /var/log type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/games on /var/games type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/mail on /var/mail type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/snap on /var/snap type zfs (rw,relatime,xattr,posixacl)
tmprpool/USERDATA/root_7vzpaq on /root type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib on /var/lib type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/www on /var/www type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/spool on /var/spool type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/apt on /var/lib/apt type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService on /var/lib/AccountsService type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/usr/local on /usr/local type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/dpkg on /var/lib/dpkg type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager on /var/lib/NetworkManager type zfs (rw,relatime,xattr,posixacl)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=1953388k,nr_inodes=488347,mode=755,inode64)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14759)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755,inode64)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/dev/vda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/vda1 on /boot/grub type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
root@ubuntu:/# mount | grep /boot/grub
/dev/vda1 on /boot/grub type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi \
>     --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
Installation finished. No error reported.
root@ubuntu:/# exit
logout
root@ubuntu:~# exit
logout
ubuntu@ubuntu:~$ sudo shutdown -P now

```
It rebooted, and came up fine...

---

### Post by MAFoElffen on 2022-01-24
I thought I forgot a step...  (And it will not let me edit Post #37.)  I did it again. I hadn't forgot anything. It worked fine again.

I did it again... And was the same, except instead of 'tmprpool', the next time it came up as rpool...

To explain... 
 - Do the fdisk to check for and identify 'Solaris boot' and 'Solaris root'. 
 - Do lsblk to identify the rpool name under 'Label'. Keep that rpool name for later. 
 - Become root.
 - Add the Universe repo
 - Update the apt cache
 - Install what is required for ZFS Utils to the LiveCD ENV.
 - do a zpool list to show any dataset pools. If none fine. Else export the rpool.
 - Do a ZFS List to show if any datasets. If none fine. Else export rpool.
 - Import the rpool to the /mnt dierectory
 - Do a zfs list to see if it was successful
 - Do a ZFS mount of the root to mount the filesystem
 - Do a ZFS mount all
 - Mount dev, proc, and sys
 - Chroot nto the installed system
 - remount all
 - check the mounts for /boot/efi and /boot/grub
 - reinstall grub

---

### Post by YannBuntu on 2022-01-24
thx MAF that really helps
I just loaded **ppa172** in ppa **dev**, please can you create :
1) one boot-info normal and another in --debug mode, from fresh live sessions ?
2) try to run boot-info from a live session where you have already activated a pool  -> it should block and display a message.  (maybe it should 'export -a' instead, but i'll see that later)
3) one boot-info from your installed zfs session
 
Questions: is the install of debootstrap really necessary ?  (FYI the 3 packages are in main so you don't need to add Universe)
I understand you mount the esp (vda1) on /boot/efi, but why also on /boot/grub ? 
Did you find good documentation about chroot in zfs ?  FYI  the best I found so far is [https://openzfs.github.io/openzfs-docs/Getting%20Started/Debian/Debian%20Bullseye%20Root%20on%20ZFS.html#step-5-grub-installation](https://openzfs.github.io/openzfs-docs/Getting%20Started/Debian/Debian%20Bullseye%20Root%20on%20ZFS.html#step-5-grub-installation)
What happens if you don't mount the root before doing 'zfs mount -a' ?

---

### Post by MAFoElffen on 2022-01-24
LOL. Okay. let's see how this goes.

Answers:
No. debootstrap and gdisk do not have to be installed. That was from old thoughts when I was doing that on Ubuntu 12.04. debootstrap was the Ubuntu installer to a chroot. Since then I have gotten creative with custom mounts between a LiveCD Image, and a chroot to make scripts accessible from within the chroot.

On the mounts... becuase sometimes it just gets different random behaviors. I don't know why... But sometimes after the initial rpool activate... If you activate the bpool, it mounts it in /boot, but is sometime empty(???) and even so, if you try to do zfs mount -a, it fails saying that /boot populated... If you don't activate the bpool, skip it... then do zfs mount -a, it succeeds, but is inscosistent. Sometimes /boot has directories (efi and grub) and sometimes is empty(???). So I add making those directories for the just in case. Then I do a mount -a for the fstab to remount... somehow it comes together.

What happens if you don't activate the root pool, before you do a pool remount? Then the pool isn't open with it's pool def's to know how to do that and just fails.On doc's? I frequent that website for reference on what is "new and working" from time to time. I had not seen that page though. Some of the things are wrong or confused though. You can create an Ubuntu Server Edition (console) from the Ubuntu Desktop LiveCD... You just install as Minimum and and select ZFS install as an option, Once is boots, change the network manager to networkd, install ubuntu-server, and reboot. You can also install to an encrytped zfs-on-root from the Ubuntu Desktop LiveCD... I think the last instructions I came up for someone for that is [HERE]("https://ubuntuforums.org/showthread.php?t=2470861&p=14075373#post14075373").

I'll try to do things that way to just confirm those things, but that is how I remember what happens when I did those. Like I said, I used to use it and support it a lot about 14-20 years ago (about a 6 year span)... I had Ubuntu running on zfs-fuse on Ubuntu 12.04 through 14,04. I picked it back up when it showed up as an option for 20.04 as an install option.

I also spun up a SecureBoot Machine today, would you like it tested on that also?

Oh, yes... Why do I enable the Universe Repo? On my Ubuntu SupportCD, I limit the support in my scripts to support installed systems 18.04 and newer... Updated to what is still supported versions. Package 'zfs-initramfs' is now since 20.04 in MAIN... but was in the Universe Repo for Bionic. For a 20.04 through 22.04 based LiveCD, can now skip that add-repo. If you are giving instructions to someone who is running *from* 18.04 though, or put it into a script that might run on 18.04, then they need to add that repo.

---

### Post by MAFoElffen on 2022-01-25
I was helping a user on "named" md devices in RAID... I created a test case for it straight from the 20.04.3 Server Install LiveCD... I decided to test your boot-info script on it...

The Machine has 3 disks, each containing 3 partitions. An /efi, vdx1 and vdx2. The primary /efi is on /dev/vd1/efi. On the other two, they are backup/failback copies of that. the other teo partitions are members of the two arrays, which those are assembled and mounted intothe filesystem as root and home, named md arrays as same... 

Here is the boot-info pastebin:
[https://paste.ubuntu.com/p/gGhdkGQqwW/](https://paste.ubuntu.com/p/gGhdkGQqwW/)

Look at Line #152
```

md127p1    : is---ESP,    fstab-has-bad-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

```
I am confused, or am I? The mount to the primary /dev/vda1 is correct via UUID right? Well, you used to show the fstab on some versions of the reports(?) Here is the machine in 'system-info'... The fstab is shown there:
[https://paste.ubuntu.com/p/7jtdZk2mVb/](https://paste.ubuntu.com/p/7jtdZk2mVb/)

It works. It boots,... but I'm confused by the results of that line there. What are the determination factors that evaluate there? Just curious what it means.

Because it also says "is---ESP" in that Array(???), which the esp is separate from any Array. What is the eval and what does it mean? Does that mean that is where the boot file /efi/ubuntu/config.cfg file points to?

I guess I would understand better if I just took the time to dump the code and read through it... Then maybe I would answers those myself. Just not a lot of hours to the day. LOL.

---

### Post by MAFoElffen on 2022-01-25
Here is what you asked for using ppa172...

1a) one boot-info normal from fresh live sessions ?
[https://paste.ubuntu.com/p/h5VZWBm3Pf/](https://paste.ubuntu.com/p/h5VZWBm3Pf/)

1b) one boot-info in --debug mode, from fresh live sessions ?
[https://paste.ubuntu.com/p/9z94vJpZCv/](https://paste.ubuntu.com/p/9z94vJpZCv/)

2) try to run boot-info from a live session where you have already activated a pool -> it should block and display a message. (maybe it should 'export -a' instead, but i'll see that later)
-- I did and it ran. It was not blocked. There was no message that popped up. Here is the terminal ogg that led up to it:
```

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
 Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal InRelease
Hit:2 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal Release
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease               
Hit:5 http://archive.ubuntu.com/ubuntu focal InRelease                         
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal InRelease [17.5 kB]
Hit:7 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 Packages [1,808 B]
Get:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main Translation-en [1,596 B]
Fetched 20.9 kB in 2s (12.5 kB/s)                   
Reading package lists... Done
Ign:1 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal InRelease
Hit:2 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal Release
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease               
Hit:5 http://archive.ubuntu.com/ubuntu focal InRelease                         
Hit:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal InRelease
Hit:7 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
268 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu@ubuntu:~$ sudo apt install boot-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  boot-sav boot-sav-extra efibootmgr glade2script glade2script-python3
  pastebinit
Suggested packages:
  boot-repair mdadm os-uninstaller gir1.2-appindicator3-0.1
The following NEW packages will be installed:
  boot-info boot-sav boot-sav-extra efibootmgr glade2script
  glade2script-python3 pastebinit
0 upgraded, 7 newly installed, 0 to remove and 268 not upgraded.
Need to get 661 kB/689 kB of archives.
After this operation, 3,284 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal/main amd64 efibootmgr amd64 17-1 [28.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal/main amd64 pastebinit all 1.5.1-1 [14.2 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 glade2script-python3 all 3.2.4~ppa23 [35.9 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 glade2script all 3.2.4~ppa23 [2,204 B]
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 boot-sav all 4ppa171 [456 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 boot-info all 4ppa171 [8,452 B]
Get:7 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 boot-sav-extra all 4ppa171 [145 kB]
Fetched 661 kB in 3s (195 kB/s)         
Selecting previously unselected package glade2script-python3.
(Reading database ... 190714 files and directories currently installed.)
Preparing to unpack .../0-glade2script-python3_3.2.4~ppa23_all.deb ...
Unpacking glade2script-python3 (3.2.4~ppa23) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../1-glade2script_3.2.4~ppa23_all.deb ...
Unpacking glade2script (3.2.4~ppa23) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../2-boot-sav_4ppa171_all.deb ...
Unpacking boot-sav (4ppa171) ...
Selecting previously unselected package boot-info.
Preparing to unpack .../3-boot-info_4ppa171_all.deb ...
Unpacking boot-info (4ppa171) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../4-boot-sav-extra_4ppa171_all.deb ...
Unpacking boot-sav-extra (4ppa171) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../5-efibootmgr_17-1_amd64.deb ...
Unpacking efibootmgr (17-1) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../6-pastebinit_1.5.1-1_all.deb ...
Unpacking pastebinit (1.5.1-1) ...
Setting up efibootmgr (17-1) ...
Setting up glade2script-python3 (3.2.4~ppa23) ...
Setting up glade2script (3.2.4~ppa23) ...
Setting up pastebinit (1.5.1-1) ...
Setting up boot-sav (4ppa171) ...
Setting up boot-sav-extra (4ppa171) ...
Setting up boot-info (4ppa171) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
ubuntu@ubuntu:~$ sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

Disk /dev/vda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4BD32A91-14FF-40C9-8092-0277030D90F5

Device       Start      End  Sectors  Size Type
/dev/vda1     2048  1050623  1048576  512M EFI System
/dev/vda2  1050624  2940927  1890304  923M Linux swap
/dev/vda3  2940928  4984831  2043904  998M Solaris boot
/dev/vda4  4984832 41943006 36958175 17.6G Solaris root
ubuntu@ubuntu:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
NAME    SIZE FSTYPE     LABEL                    MOUNTPOINT                   MODEL
loop0     2G squashfs                            /rofs                        
sr0     2.9G iso9660    Ubuntu 20.04.3 LTS amd64 /cdrom                       QEMU_DVD-ROM
vda      20G zfs_member tmprpool                                              
&#9500;&#9472;vda1  512M vfat                                                             
&#9500;&#9472;vda2  923M swap                                [SWAP]                       
&#9500;&#9472;vda3  998M zfs_member tmpbpool                                              
&#9492;&#9472;vda4 17.6G zfs_member tmprpool                                              
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# apt install -y zfs-initramfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libnvpair1linux libuutil1linux libzfs2linux libzpool2linux zfsutils-linux
Suggested packages:
  nfs-kernel-server samba-common-bin
The following packages will be upgraded:
  libnvpair1linux libuutil1linux libzfs2linux libzpool2linux zfs-initramfs
  zfsutils-linux
6 upgraded, 0 newly installed, 0 to remove and 262 not upgraded.
Need to get 1,487 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 zfs-initramfs amd64 0.8.3-1ubuntu12.13 [23.6 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 zfsutils-linux amd64 0.8.3-1ubuntu12.13 [354 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libuutil1linux amd64 0.8.3-1ubuntu12.13 [41.7 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libzfs2linux amd64 0.8.3-1ubuntu12.13 [207 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libzpool2linux amd64 0.8.3-1ubuntu12.13 [812 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libnvpair1linux amd64 0.8.3-1ubuntu12.13 [48.3 kB]
Fetched 1,487 kB in 2s (906 kB/s)         
(Reading database ... 190896 files and directories currently installed.)
Preparing to unpack .../0-zfs-initramfs_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking zfs-initramfs (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../1-zfsutils-linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking zfsutils-linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../2-libuutil1linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking libuutil1linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../3-libzfs2linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking libzfs2linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../4-libzpool2linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking libzpool2linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Preparing to unpack .../5-libnvpair1linux_0.8.3-1ubuntu12.13_amd64.deb ...
Unpacking libnvpair1linux (0.8.3-1ubuntu12.13) over (0.8.3-1ubuntu12.12) ...
Setting up libuutil1linux (0.8.3-1ubuntu12.13) ...
Setting up libnvpair1linux (0.8.3-1ubuntu12.13) ...
Setting up libzfs2linux (0.8.3-1ubuntu12.13) ...
Setting up libzpool2linux (0.8.3-1ubuntu12.13) ...
Setting up zfsutils-linux (0.8.3-1ubuntu12.13) ...
zfs-import-scan.service is a disabled or a static unit, not starting it.
zfs-import-scan.service is a disabled or a static unit, not starting it.
Setting up zfs-initramfs (0.8.3-1ubuntu12.13) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for systemd (245.4-4ubuntu3.11) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs is disabled since running on read-only media
root@ubuntu:~# zpool list
no pools available
root@ubuntu:~# zfs list
no datasets available
root@ubuntu:~# zpool import -N -R /mnt tmprpool
root@ubuntu:~# zfs list
NAME                                                  USED  AVAIL     REFER  MOUNTPOINT
tmprpool                                             7.84G  9.12G       96K  /mnt/mnt/boot-sav/zfs
tmprpool/ROOT                                        7.81G  9.12G       96K  none
tmprpool/ROOT/ubuntu_64fs0l                          7.81G  9.12G     3.52G  /mnt
tmprpool/ROOT/ubuntu_64fs0l/srv                       152K  9.12G       96K  /mnt/srv
tmprpool/ROOT/ubuntu_64fs0l/usr                       408K  9.12G       96K  /mnt/usr
tmprpool/ROOT/ubuntu_64fs0l/usr/local                 312K  9.12G      128K  /mnt/usr/local
tmprpool/ROOT/ubuntu_64fs0l/var                      1.81G  9.12G       96K  /mnt/var
tmprpool/ROOT/ubuntu_64fs0l/var/games                 152K  9.12G       96K  /mnt/var/games
tmprpool/ROOT/ubuntu_64fs0l/var/lib                  1.78G  9.12G     1.57G  /mnt/var/lib
tmprpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService   344K  9.12G       96K  /mnt/var/lib/AccountsService
tmprpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager    592K  9.12G      136K  /mnt/var/lib/NetworkManager
tmprpool/ROOT/ubuntu_64fs0l/var/lib/apt               106M  9.12G     83.8M  /mnt/var/lib/apt
tmprpool/ROOT/ubuntu_64fs0l/var/lib/dpkg             61.2M  9.12G     36.4M  /mnt/var/lib/dpkg
tmprpool/ROOT/ubuntu_64fs0l/var/log                  22.6M  9.12G     8.82M  /mnt/var/log
tmprpool/ROOT/ubuntu_64fs0l/var/mail                  152K  9.12G       96K  /mnt/var/mail
tmprpool/ROOT/ubuntu_64fs0l/var/snap                 1.12M  9.12G      904K  /mnt/var/snap
tmprpool/ROOT/ubuntu_64fs0l/var/spool                 360K  9.12G      112K  /mnt/var/spool
tmprpool/ROOT/ubuntu_64fs0l/var/www                   152K  9.12G       96K  /mnt/var/www
tmprpool/USERDATA                                    12.3M  9.12G       96K  /mnt
tmprpool/USERDATA/mafoelffen_7vzpaq                  11.7M  9.12G     3.88M  /mnt/home/mafoelffen
tmprpool/USERDATA/root_7vzpaq                         504K  9.12G      164K  /mnt/root
root@ubuntu:~# zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
tmprpool  17.5G  7.84G  9.66G        -         -     8%    44%  1.00x    ONLINE  /mnt
root@ubuntu:~# boot-info
### Here is where boot-info ran ### 
### When exited, it returned to the command prompt fine, but:
root@ubuntu:~# zfs list
NAME                                                  USED  AVAIL     REFER  MOUNTPOINT
tmpbpool                                              669M   162M       96K  /mnt/boot-sav/zfs/mnt/boot-sav/zfs
tmpbpool/BOOT                                         668M   162M       96K  none
tmpbpool/BOOT/ubuntu_64fs0l                           668M   162M      312M  /mnt/boot-sav/zfs/boot
tmprpool                                             7.84G  9.12G       96K  /mnt/mnt/boot-sav/zfs
tmprpool/ROOT                                        7.81G  9.12G       96K  none
tmprpool/ROOT/ubuntu_64fs0l                          7.81G  9.12G     3.52G  /mnt
tmprpool/ROOT/ubuntu_64fs0l/srv                       152K  9.12G       96K  /mnt/srv
tmprpool/ROOT/ubuntu_64fs0l/usr                       408K  9.12G       96K  /mnt/usr
tmprpool/ROOT/ubuntu_64fs0l/usr/local                 312K  9.12G      128K  /mnt/usr/local
tmprpool/ROOT/ubuntu_64fs0l/var                      1.81G  9.12G       96K  /mnt/var
tmprpool/ROOT/ubuntu_64fs0l/var/games                 152K  9.12G       96K  /mnt/var/games
tmprpool/ROOT/ubuntu_64fs0l/var/lib                  1.78G  9.12G     1.57G  /mnt/var/lib
tmprpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService   344K  9.12G       96K  /mnt/var/lib/AccountsService
tmprpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager    592K  9.12G      136K  /mnt/var/lib/NetworkManager
tmprpool/ROOT/ubuntu_64fs0l/var/lib/apt               106M  9.12G     83.8M  /mnt/var/lib/apt
tmprpool/ROOT/ubuntu_64fs0l/var/lib/dpkg             61.2M  9.12G     36.4M  /mnt/var/lib/dpkg
tmprpool/ROOT/ubuntu_64fs0l/var/log                  22.6M  9.12G     8.82M  /mnt/var/log
tmprpool/ROOT/ubuntu_64fs0l/var/mail                  152K  9.12G       96K  /mnt/var/mail
tmprpool/ROOT/ubuntu_64fs0l/var/snap                 1.12M  9.12G      904K  /mnt/var/snap
tmprpool/ROOT/ubuntu_64fs0l/var/spool                 360K  9.12G      112K  /mnt/var/spool
tmprpool/ROOT/ubuntu_64fs0l/var/www                   152K  9.12G       96K  /mnt/var/www
tmprpool/USERDATA                                    12.3M  9.12G       96K  /mnt
tmprpool/USERDATA/mafoelffen_7vzpaq                  11.7M  9.12G     3.88M  /mnt/home/mafoelffen
tmprpool/USERDATA/root_7vzpaq                         504K  9.12G      164K  /mnt/root
root@ubuntu:~# zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
tmpbpool   960M   670M   290M        -         -    16%    69%  1.00x    ONLINE  /mnt/boot-sav/zfs
tmprpool  17.5G  7.84G  9.66G        -         -     8%    44%  1.00x    ONLINE  /mnt
root@ubuntu:~# zpool export tmprpool
root@ubuntu:~# zfs list
NAME                          USED  AVAIL     REFER  MOUNTPOINT
tmpbpool                      669M   162M       96K  /mnt/boot-sav/zfs/mnt/boot-sav/zfs
tmpbpool/BOOT                 668M   162M       96K  none
tmpbpool/BOOT/ubuntu_64fs0l   668M   162M      312M  /mnt/boot-sav/zfs/boot
root@ubuntu:~# zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
tmpbpool   960M   670M   290M        -         -    16%    69%  1.00x    ONLINE  /mnt/boot-sav/zfs
root@ubuntu:~# zpool export tmpbpool
root@ubuntu:~# zfs list
no datasets available
root@ubuntu:~# zpool list
no pools available
root@ubuntu:~# umount /mnt
root@ubuntu:~# exit
logout
ubuntu@ubuntu:~$ 

```
Here is the pastebin from that session: [https://paste.ubuntu.com/p/PHtZpg4tJr/](https://paste.ubuntu.com/p/PHtZpg4tJr/)

*** If you look above, after the script ran, that is my fault. I should have said something earlier. You (anyone doing this) should export the zpools to ensure that the filesystem is closed down cleanly.

3) one boot-info from your installed zfs session
??? When I booted the machine straight to te system, it said it was up to date... no updated ppa172,. It was ppa171. Just to make sure, I purged boot-info and re-installed it. Same version. I hadn't checked the previous pastebins. Will go back and check what they say...
[https://paste.ubuntu.com/p/qkRRjSrmyf/](https://paste.ubuntu.com/p/qkRRjSrmyf/)

---

### Post by MAFoElffen on 2022-01-25
Dang. 

All those are 4ppa171. That was the last update uploaded to your launchpad ppa. 4ppa172 is not there yet.

---

### Post by YannBuntu on 2022-01-25
hi, ppa172 is in the **dev** ppa ( [ppa:yannubuntu/boot-repair-dev]("https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair-dev/+packages") ), not the standard ppa ( [ppa:yannubuntu/boot-repair]("https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair/+packages") ). I'll try to mention 'dev' or 'standard' at every ppa release, but you can check those links to verify which version is in which ppa. Remark: it takes sometimes hours between my upload and the package to be downloadable. It is available when status is 'Published'.

> **MAFoElffen said:**
> On the mounts... becuase sometimes it just gets different random behaviors. I don't know why... But sometimes after the initial rpool activate... If you activate the bpool, it mounts it in /boot, but is sometime empty(???) and even so, if you try to do zfs mount -a, it fails saying that /boot populated... If you don't activate the bpool, skip it... then do zfs mount -a, it succeeds, but is inscosistent. Sometimes /boot has directories (efi and grub) and sometimes is empty(???). So I add making those directories for the just in case. Then I do a mount -a for the fstab to remount... somehow it comes together.

Wow, random fs behavior :P  For the moment I'll consider the esp must be mounted on /boot/efi as usual. I'll see later the detection of unusual cases.

> **MAFoElffen said:**
> I also spun up a SecureBoot Machine today, would you like it tested on that also?
Yes, simple test: create a boot-info and just check that SecureBoot is corretly detected (the UEFI section should indicate 'SecureBoot enabled').

---

### Post by YannBuntu on 2022-01-25
> **MAFoElffen said:**
> [https://paste.ubuntu.com/p/gGhdkGQqwW/](https://paste.ubuntu.com/p/gGhdkGQqwW/)
(...)
What is the eval and what does it mean? 

Thx, you found a nice one, I'll have a look. 
To understand fully how ESP is detected by boot-info&boot-repair, look at the function esp_check()  in /usr/share/boot-sav/bs-cmd_terminal.sh
Hint:  PARTDLM and FDISKL are defined at the top of  /usr/share/boot-sav/bs-common.sh

---

### Post by YannBuntu on 2022-01-25
ppa172 is buggy, please wait for ppa173  (in the ppa dev).

---

### Post by MAFoElffen on 2022-01-25
> **YannBuntu said:**
> Wow, random fs behavior :P  
For the moment I'll consider the esp must be mounted on /boot/efi as usual. I'll see later the detection of unusual cases.


The one, most important random case where you need to check and store as a variable, is whether the ouput of of lsblk says "rpool" or "tmprpool"... Because you need that name to activate/mount the root zpool. In all I have done, it is either one or the other of those two cases. I have not seen any variation from those two names for that. (And that does that randomly on this same test case VM, with no system or file changes done to it.) But that only seems to happen from mounting it from a LiveCD. On an installed system, it is always 'rpool'.

---

### Post by YannBuntu on 2022-01-25
ppa174 in the dev ppa to be tested in live (normal and debug) and installed zfs session
Also fixed the 'is---ESP' bug (which was due to md127 not being in blkid).

> **MAFoElffen said:**
> The one, most important random case where you need to check and store as a variable, is whether the ouput of of lsblk says "rpool" or "tmprpool"... Because you need that name to activate/mount the root zpool. In all I have done, it is either one or the other of those two cases. I have not seen any variation from those two names for that. (And that does that randomly on this same test case VM, with no system or file changes done to it.) But that only seems to happen from mounting it from a LiveCD. On an installed system, it is always 'rpool'.

yep, I think I found a way to grab the name whatever it is. We'll see if it works in your --debug boot-info.

---

### Post by oldfred on 2022-01-25
If the drive is gpt, the ESP GUID type is always: C12A7328-F81F-11D2-BA4B-00A0C93EC93B
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

Not sure then what it is if Ubuntu installs UEFI to MBR(msdos) partitioned drive.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -o +parttype [/COLOR]
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT [COLOR=#ff0000]PARTTYPE[/COLOR] 
sda           8:0    0 232.9G  0 disk             
&#9500;&#9472;sda1        8:1    0   510M  0 part            [COLOR=#ff0000]c12a7328-f81f-11d2-ba4b-00a0c93ec93b [/COLOR]
&#9500;&#9472;sda2        8:2    0  31.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sda4        8:4    0  25.4G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9492;&#9472;sda5        8:5    0 127.4G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
sdb           8:16   0 931.5G  0 disk             
&#9500;&#9472;sdb1        8:17   0 510.2M  0 part            [COLOR=#ff0000]c12a7328-f81f-11d2-ba4b-00a0c93ec93b[/COLOR] 
&#9500;&#9472;sdb2        8:18   0  30.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb3        8:19   0  49.8G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb4        8:20   0 147.6G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb5        8:21   0  30.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb6        8:22   0 302.8G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb7        8:23   0   2.1G  0 part            0657fd6d-a4ab-43c4-84e5-0933c84b4f4f 
&#9500;&#9472;sdb8        8:24   0  24.4G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb9        8:25   0    24G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9492;&#9472;sdb10       8:26   0  33.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
nvme0n1     259:0    0 465.8G  0 disk             
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part /boot/efi  [COLOR=#ff0000]c12a7328-f81f-11d2-ba4b-00a0c93ec93b[/COLOR] 
&#9500;&#9472;nvme0n1p2 259:2    0  29.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;nvme0n1p3 259:3    0  29.3G  0 part /          0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;nvme0n1p4 259:4    0  29.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9492;&#9472;nvme0n1p5 259:5    0 195.3G  0 part /mnt/data  0fc63daf-8483-4772-8e79-3d69d8477de4


[/FONT]
```

---

### Post by MAFoElffen on 2022-01-27
> **oldfred said:**
> If the drive is gpt, the ESP GUID type is always: C12A7328-F81F-11D2-BA4B-00A0C93EC93B

Not sure then what it is if Ubuntu installs UEFI to MBR(msdos) partitioned drive.


I'm confused. I must be... Because I was taught that if a system  needs to boot UEFI from a mass storage device, (CD's and USB 's are not mass storage devices).. That mass storage device "is required" to be GPT. I've gone by  that since 2007. 
> 
Partition Requirements.  When you deploy Windows to a UEFI-based device, you must format the hard  drive that includes the Windows partition by using **a GUID partition table (GPT) file system**.  Additional drives may use either the GPT or the master boot record  (MBR) file format. A GPT drive may have up to 128 partitions.

UEFI/GPT-based hard drive partitions
Microsoft Documentation, 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11)

Linux,Windows, and MS Windows requires if UEFI boot, then the mass storage it is installing to be GPT, In fact, for MAC's, even a USB thumbdrive for them to be bootable, has  to be GPT.

GPT can be booted from either UEFI or CSM/Legacy. If  UEFI boot, then /efi directory. For CSM/Legacy boot, then Grub installs  boot.img in the first 446 bytes of Sector 0, then core.img "in the  /bios_grub partition."

For MBR disks, the boot code is written directly to Sector 0, before the MBR (ms_dos) partition tables, before the first partition.

So... Do you want me to spin up a test machine to find the partition type to the installed /bios_boot partition on a GPT disk installed for CSM/Legacy?

Or is there some new math that changed what was, that I don't know about yet? I'm curious if there is...

---

### Post by sudodus on 2022-01-27
> **MAFoElffen said:**
> I'm confused. I must be... Because I was taught that if a system  needs to boot UEFI from a mass storage device, (CD's and USB 's are not mass storage devices).. That mass storage device "is required" to be GPT. I've gone by  that since 2007. 

Linux,Windows, and MS Windows requires if UEFI boot, then the mass storage it is installing to be GPT, In fact, for MAC's, even a USB thumbdrive for them to be bootable, has  to be GPT.

...

Or is there some new math that changed what was, that I don't know about yet? I'm curious if there is...

My experience is that *'what you were taught'* applies to Windows, but Linux is not fuzzy about the partition table. I can boot SSDs (that can be classified as mass storage devices) with an MSDOS partition table in UEFI mode in real computers.

It is possible that the reason is that the particular UEFI systems are not strictly applying the general specifications, but anyway, it works. If this is the case, there might also be computers where *'what you were taught'* applies strictly to all attempts to boot an operating system.

---

### Post by oldfred on 2022-01-27
I started to convert to gpt back in 2010. And now all  drives & even larger flash drives are all gpt.
But Ubuntu installer & gparted still default to MBR unless drive is gpt or over 2TB.

I can understand not changing a MBR drive to gpt if UEFI install as that would erase drive. And if user is installing Ubuntu in UEFI mode to a Windows BIOS/MBR configuration, it would erase Windows. Or converting MBR to gpt with Windows breaks Windows as it is not easy to convert in place.

---

### Post by MAFoElffen on 2022-01-27
Well dang. LOL. I learned something new. Thank you very much. 

Yes, I guess I went off of both Microsoft and Apple, for MAC OS.Then off of what I was taught in College. Was drilled into to me hard to stop using MBR partition tables. Working as a Systems Admin, and as a Tech, I didn't see MBR partition tables anymore. Installing new drives, first step, add new GPT Partition table...

I guess that can be filed more as "***Best Practices***" now, instead of absolute. 

I need to build some new test cases to test for now. I'll spin some up... And get that UUID information posted.

EDIT:
I should know better. I just got through having to explain to a User how Linux "Handles Graphics Differently" than Windows... And why a very cheap "VGA to HDMA adapter" in between his computer and display is the problem why Ubuntu and Grub can not see the native resolutions from his TV. (It took 2 pages of posts until I had him post pictures of his setup... And there it was in the corner, half out of of one of his pictures...) The system was Intel iCore CPU, but Grub can only set KMS to what Grub see's as valid in BIOS and what it see's from Grub videoinfo (previously vbeinfo). It could only see modes from the from the adapter itself... which was much less. (1024x768 instead of 4k.)

---

### Post by oldfred on 2022-01-27
Almost absolute.
The only place for MBR anymore is BIOS boot of Windows. And that is usually obsolete versions of Windows, unless user installed (and really installed incorrectly). 
But almost all PC hardware since 2012 is UEFI as Microsoft has required vendors to install in UEFI/gpt mode since 2012 and Windows 8.

I think the only reason BIOS installs of Windows were allowed was major PC users (1000s) had somewhat older systems that were BIOS, and Microsoft wanted to allow them to use newer Windows on the older hardware.

Now vendors are releasing PCs that are UEFI class 3 or no  CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode.

Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

---

### Post by MAFoElffen on 2022-01-28
> **oldfred said:**
> If the drive is gpt, the ESP GUID type is always: C12A7328-F81F-11D2-BA4B-00A0C93EC93B
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

Not sure then what it is if Ubuntu installs UEFI to MBR(msdos) partitioned drive.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -o +parttype [/COLOR]
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT [COLOR=#ff0000]PARTTYPE[/COLOR] 
sda           8:0    0 232.9G  0 disk             
&#9500;&#9472;sda1        8:1    0   510M  0 part            [COLOR=#ff0000]c12a7328-f81f-11d2-ba4b-00a0c93ec93b [/COLOR]
&#9500;&#9472;sda2        8:2    0  31.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sda4        8:4    0  25.4G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9492;&#9472;sda5        8:5    0 127.4G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
sdb           8:16   0 931.5G  0 disk             
&#9500;&#9472;sdb1        8:17   0 510.2M  0 part            [COLOR=#ff0000]c12a7328-f81f-11d2-ba4b-00a0c93ec93b[/COLOR] 
&#9500;&#9472;sdb2        8:18   0  30.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb3        8:19   0  49.8G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb4        8:20   0 147.6G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb5        8:21   0  30.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb6        8:22   0 302.8G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb7        8:23   0   2.1G  0 part            0657fd6d-a4ab-43c4-84e5-0933c84b4f4f 
&#9500;&#9472;sdb8        8:24   0  24.4G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;sdb9        8:25   0    24G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9492;&#9472;sdb10       8:26   0  33.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
nvme0n1     259:0    0 465.8G  0 disk             
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part /boot/efi  [COLOR=#ff0000]c12a7328-f81f-11d2-ba4b-00a0c93ec93b[/COLOR] 
&#9500;&#9472;nvme0n1p2 259:2    0  29.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;nvme0n1p3 259:3    0  29.3G  0 part /          0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9500;&#9472;nvme0n1p4 259:4    0  29.3G  0 part            0fc63daf-8483-4772-8e79-3d69d8477de4 
&#9492;&#9472;nvme0n1p5 259:5    0 195.3G  0 part /mnt/data  0fc63daf-8483-4772-8e79-3d69d8477de4
[/FONT]
```

For MBR with UEFI:
```

mafoelffen@ubuntu-mbr-efi:~$ lsblk -o +parttype
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT  PARTTYPE
loop0    7:0    0  219M  1 loop /snap/gnome 
loop1    7:1    0 55.4M  1 loop /snap/core1 
loop2    7:2    0 65.1M  1 loop /snap/gtk-c 
loop3    7:3    0   51M  1 loop /snap/snap- 
loop4    7:4    0 32.3M  1 loop /snap/snapd 
sr0     11:0    1  2.9G  0 rom  /media/mafo 
vda    252:0    0   15G  0 disk             
&#9500;&#9472;vda1 252:1    0  512M  0 part /boot/efi   [COLOR=#ff0000]c12a7328-f81f-11d2-ba4b-00a0c93ec93b[/COLOR]
&#9492;&#9472;vda2 252:2    0 14.5G  0 part /           0fc63daf-8483-4772-8e79-3d69d8477de4

```
...same partition type.

For GPT booted with CSM/Legacy:
```

mafoelffen@ubuntu-gpt-csm:~$ lsblk -o +parttype
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT                   PARTTYPE
loop0    7:0    0 55.4M  1 loop /snap/core18/2128            
loop1    7:1    0 65.1M  1 loop /snap/gtk-common-themes/1515 
loop2    7:2    0   51M  1 loop /snap/snap-store/547         
loop3    7:3    0  219M  1 loop /snap/gnome-3-34-1804/72     
loop4    7:4    0 32.3M  1 loop /snap/snapd/12704            
sr0     11:0    1 1024M  0 rom                               
vda    252:0    0   15G  0 disk                              
&#9500;&#9472;vda1 252:1    0  512M  0 part /boot/efi                    0xb
&#9500;&#9472;vda2 252:2    0    1K  0 part                              0x5
&#9492;&#9472;vda5 252:5    0 14.5G  0 part /                            0x83

```

---

### Post by MAFoElffen on 2022-01-28
Here is what you asked for using ppa174...

1a) one boot-info normal from fresh live sessions ?
[https://paste.ubuntu.com/p/cYGZS83sX5/](https://paste.ubuntu.com/p/cYGZS83sX5/)

1b) one boot-info in --debug mode, from fresh live sessions ?
[https://paste.ubuntu.com/p/k54d4rydWP/](https://paste.ubuntu.com/p/k54d4rydWP/)

2) try to run boot-info from a live session where you have already activated a pool
```

sudo add-apt-repository ppa:yannubuntu/boot-repair-dev
sudo apt update
sudo apt install boot-info
sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq
lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
sudo -i
apt install -y zfs-initramfs
zpool list
zfs list
zpool import -N -R /mnt tmprpool
zfs list
zpool list

```
MessaegBox said: " ZFS pools aalready activated. Please retry from a fresh live-session, without activating the pools." Said it did nothing, then exited.

Where I went 'ahead' to what you mentioned, and I thought it should branch from there to remedy on it's own and continue...
```

zpool export -a
zfs list
zpool list
boot-info

```
Here is the pastebin from that session, after issuing 'zpool export -a', and restarting boot-info: [https://paste.ubuntu.com/p/6R7Qt6996N/](https://paste.ubuntu.com/p/6R7Qt6996N/)

3) one boot-info from your installed zfs session
"We have a problem Houston..." It ran previous from an actual ZDS-on-root system... When I booted the machine straight to the system, it came up with the previous message saying to deactivate the pools first before starting the script... So it does not want to run the script when it is running in the system as ZFS-as-root... Because 'logically', of course, if it is booted into that and running, those pools "are" activated". When running as normal, it cannot deactivate the pool it is running on as Root. Can you check if running from a LiveCD or Actual real system? then branch from those two conditions?

---

### Post by YannBuntu on 2022-01-28
thx MAF. New package (**4ppa176**) in ppa DEV :
 * remove '--no-uefi-secure-boot' to avoid unrecognized option error
  * check efi files on liveUSB/MMC containing windows
  * purge to remove grub-efi when install grub-pc from EFI session
  * Workaround GRUB&#8217;s missing zpool-features support 
 *  STILL NOT SOLVED: does not display /etc/fstab

please can you test (without --debug for the moment) :
1) boot-info in live-session
2) boot-info in installed zfs session
3) grub reinstall in live session

---

### Post by YannBuntu on 2022-01-29
ppa177 (in ppa dev):  fix the chroot for zfs

---

### Post by MAFoElffen on 2022-01-29
Here is what you asked for using ppa177 (without --debug for the moment) :

1) boot-info in live-session
[https://paste.ubuntu.com/p/BgMbWsZx9q/](https://paste.ubuntu.com/p/BgMbWsZx9q/)

2) boot-info in installed zfs session
- Failure to generate report: "ZFS pools already activated. Please retry from a fresh live-session, without activating the pools.
- In bs-cmd_terminal.sh: In check_if_live_sesssion()... 
  -- CURRENTSESSIONPARTITION populates. 
  -- On the EVAL, both Eval's result in "" (empty string). That is what they should do on those evals, to check if Live session or installed... Great way to ID that... (My compliments)
    --- Though empty strings, Eval results to true, because the expressions complete successfully, they just result in empty strings.

I know this, because I checked the results of the expressions, and added a debug statement there at the end of the function to check, and  it wrongfully sets LIVESESSION=live... Instead of LIVESESSION=installed. 

Here is where that problem is, on the EVAL resulting in true all the time, 

If you check for non-empty string as result of your expressions there, then that would eval as true/false.

Just trying to help, if that is okay...

---

### Post by MAFoElffen on 2022-01-31
I hadn't heard from you Yann...

So I changed the expression in script file bs-cmd_terminal.sh, in function check_if_live_sesssion()... So it could evaluate to true or false, based on the spirit of what you where looking for, so that LIVESESSION could be set to "installed" if that were such... Here is the pastebin for that running successfully, with the scripts running on an installed ZFS system after that change:
[https://paste.ubuntu.com/p/PP6HP32JXG/](https://paste.ubuntu.com/p/PP6HP32JXG/)

## FYI: Ignore Line 198. The iso file was there mounted to the CDROM device as such, but was not booted from it.

Suggested edit, (without the debug test lines):
```

########################## CHECK IF LIVE-SESSION #######################
check_if_live_session() {
CURRENTSESSIONPARTITION="$(findmnt -n -o SOURCE /)" #eg rpool/ROOT/ubuntu_64fs0l or /dev/sda3
[[ ! "$CURRENTSESSIONPARTITION" ]] && echo "Error: empty findmnt -n -o SOURCE / , $PLEASECONTACT"
hash lsb_release && DISTRIB_DESCRIPTION="$(lsb_release -ds)" || DISTRIB_DESCRIPTION=Unknown-name
if [ -z $(grep -E '(boot=casper)|(boot=live)' /proc/cmdline) ] || [ -z $(findmnt -n -o FSTYPE / | grep -E 'squashfs|aufs|overlay') ];
then #aufs bug#1281815, overlay since 19.10
    LIVESESSION=installed
    CURRENTSESSIONNAME="$The_system_now_in_use - $DISTRIB_DESCRIPTION"
    echo "true" > ~/debug.txt   ## DEBUG TEST
else
    LIVESESSION=live
    echo "false" > ~/debug.txt   ## DEBUG TEST
fi 
echo $LIVESESSION >> ~/debug.txt  ## DEBUG TEST
}

```

---

### Post by YannBuntu on 2022-02-01
Thx a lot MAF, and congratulations you're 2022's first patch contributor \\:D/ 
Sorry I'm pretty busy at work this week, but I'll review asap.

---

### Post by MAFoElffen on 2022-02-02
You are very welcome. Anytime.

---

### Post by MAFoElffen on 2022-02-10
@yannubuntu

Is it time to bring up boot-info's quarks on current Luks encryption yet? And get ready for the changes brought on in April?

Background  with 20.04.3, default install with encryption is partial,there is a way  that Canonical approved for "Mostly" encrypted. Grub2, up to version  2.04 could not read or boot luks2, so if the boot partiton was encrpted,  it was luks1 withe the root being luks2. On just released Grub2 version  2.06, now Grub can rad and boot luks2. Grub2 version 2.06 gets  officially released with Ubuntu 22.04 LTS in two months. It's in the dev  repo's now for 22.04...

Here is a partial, installed by default on the 20.04.3 ISO test machine. It was run using using nppa190, from your changes from 2 hours ago:
[https://paste.ubuntu.com/p/4H2dVS6fq8/](https://paste.ubuntu.com/p/4H2dVS6fq8/)

I also have 2 mostly encrypted, and working on the same for 22.04...

---

### Post by MAFoElffen on 2022-02-11
Well... On the previous result above and in this one, which is the Mostly encrypted for 20.04.3:
[https://paste.ubuntu.com/p/hxWSYb9rhJ/](https://paste.ubuntu.com/p/hxWSYb9rhJ/)

Notice on both of those, it doesn't recognize the bootloader(?) and does a hex dump on it. You can see the LUKS header in those.

On those, the 'boot-info' script correctly recognizes that partition(s) are encrypted and pops up a windows saying that, and that it needs to install package encryptfs-utils... Then sort of gets caught in a loop 3 times installing it and saying it needs to be installed, until it finally works.

On 22.04, the script never pops up that dialog, but on the report it is incomplete. At the end it says there are encrypted drives, to install encryptfs-utils and mount the partitions and try again...

I tried to manually install encrytfs-utils, but then found that with 22.04, that encryptfs-utils is in the jammy universe repo, so you will need to add-apt repo universe for that to be installed...

I haven't looked at the code yet...

And Grub version 2.06...I really need to go through the docs on the release. To look more into the changes of...

---

### Post by YannBuntu on 2022-02-11
hello,
The 3x loop was introduced 16h ago, and fixed 2hours ago (ppa191).

---

### Post by YannBuntu on 2022-02-11
**ppa192** to be tested, in ppa:yannubuntu/boot-repair**-dev**

  * chroot install efibootmgr wen absent during grub-efi purge
  * don't propose to enable raid on pure lmv (when mapper/vg.. )
  * propose to decrypt when crypto_LUKS and no Linux detected
  * force grub purge when grub.d missing
  * add sid to the list of EFIGRUBFILE detection
  * propose to remove hidden flag from default esp
  * block when efibootmgr not installed and grub-efi repair
  * add -lf to unchroot umount (for all: zfs and others)
  * ask install pastebinit only when upload
  * zfs improvements

---

### Post by oldfred on 2022-02-15
BIOS install on sda
Just saw this report which dumped into report every available kernel and lots of issues
Seems to have reinstalled kernel from 20.04.1 5.4.0-99 but had 5.11.0.27.29~20.04.11 
[https://paste.ubuntu.com/p/nRf4Q29pfv/](https://paste.ubuntu.com/p/nRf4Q29pfv/)
From this thread, still working on issues.
[https://ubuntuforums.org/showthread.php?t=2472016](https://ubuntuforums.org/showthread.php?t=2472016)

Also getting on line 2024
> grub-install: error: failed to get canonical path of `/cow'.

But sda where install is occurring is a standard install, not a live installer that is the /cow.

---

### Post by YannBuntu on 2022-02-16
hi oldfred,
the numerous warnings about kernels are just information, no negative impact. I'll try to hide them in the next bootinfo versions.
Boot-Repair kernel purge does the following: purge all kernels (see line 66) , then reinstalls linux-generic. Kernel 5.4.0-99 is the default kernel that comes with linux-generic  (see line 1934).
Concerning the/cow issue, I've answered in the thread.

---

### Post by oldfred on 2022-02-16
Yann,
Thanks for posting in the thread.

---

### Post by MAFoElffen on 2022-02-16
> **YannBuntu said:**
> **ppa192** to be tested, in ppa:yannubuntu/boot-repair**-dev**
ZFS-on-root, ran form installed system: [https://paste.ubuntu.com/p/VbDddqsHJZ/](https://paste.ubuntu.com/p/VbDddqsHJZ/)
Not understanding lines 210-215
```

Error code 32
mount -r /dev/vda4 /mnt/boot-sav/vda4 
mount -r /dev/vda4 : Error code 32
Error code 32
mount -r /dev/vda4 /mnt/boot-sav/vda4 
mount -r /dev/vda4 : Error code 32

```

ZFS-on-root, ran from LiveCD: 
Stopped/Paused on a dialog saying: "If needed, type 'zfs load-key -a' in another terminal." I just pressed "Okay". (zfs ad zpool commands should run as sudo right?) 'zfs load-key' would only be used if it had zfs encrypted pools... I did this later on a fresh run, and it took the command without error, even though there was no keys, and no encrypted pools. But logically, if someone didn't know if there was any encrypted pools, you should first run 'zfs ketstaus' which shoudl return either 'none', 'available' or 'unavailable'... But for some reason 'zfs ketstatus resulted in the help screen(???) So for some reason, that option is not working right.
```

================================ ZFS activation ================================

dpkg-query -W -f=${Version} zfsutils-linux : 0.8.3-1ubuntu12.12
zpool export -f -a 

zpool import -N -f -R /mnt/boot-sav/zfs bpool 
zpool import -N -f -R /mnt/boot-sav/zfs rpool 
If needed, type 'zfs load-key -a' in another terminal.
zfs mount rpool/ROOT/ubuntu_64fs0l 
zfs mount -a 
Error: could not activate ZFS. Please report this message to boot.repair@gmail.com
zpool list after activation
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool   960M   777M   183M        -         -    47%    80%  1.00x    ONLINE  /mnt/boot-sav/zfs
rpool  17.5G  10.1G  7.41G        -         -    14%    57%  1.00x    ONLINE  /mnt/boot-sav/zfs

zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              777M  54.6M       96K  /mnt/boot-sav/zfs/mnt/boot-sav/zfs
bpool/BOOT                                         775M  54.6M       96K  none
bpool/BOOT/ubuntu_64fs0l                           775M  54.6M      225M  /mnt/boot-sav/zfs/boot
rpool                                             10.1G  6.86G       96K  /mnt/boot-sav/zfs/mnt/boot-sav/zfs
rpool/ROOT                                        10.1G  6.86G       96K  none
rpool/ROOT/ubuntu_64fs0l                          10.1G  6.86G     3.92G  /mnt/boot-sav/zfs
rpool/ROOT/ubuntu_64fs0l/srv                       208K  6.86G       96K  /mnt/boot-sav/zfs/srv
rpool/ROOT/ubuntu_64fs0l/usr                       768K  6.86G       96K  /mnt/boot-sav/zfs/usr
rpool/ROOT/ubuntu_64fs0l/usr/local                 672K  6.86G      128K  /mnt/boot-sav/zfs/usr/local
rpool/ROOT/ubuntu_64fs0l/var                      2.39G  6.86G       96K  /mnt/boot-sav/zfs/var
rpool/ROOT/ubuntu_64fs0l/var/games                 152K  6.86G       96K  /mnt/boot-sav/zfs/var/games
rpool/ROOT/ubuntu_64fs0l/var/lib                  2.31G  6.86G     1.88G  /mnt/boot-sav/zfs/var/lib
rpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService   608K  6.86G       96K  /mnt/boot-sav/zfs/var/lib/AccountsService
rpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager   1.16M  6.86G      144K  /mnt/boot-sav/zfs/var/lib/NetworkManager
rpool/ROOT/ubuntu_64fs0l/var/lib/apt               160M  6.86G     84.6M  /mnt/boot-sav/zfs/var/lib/apt
rpool/ROOT/ubuntu_64fs0l/var/lib/dpkg             90.3M  6.86G     36.6M  /mnt/boot-sav/zfs/var/lib/dpkg
rpool/ROOT/ubuntu_64fs0l/var/log                  80.0M  6.86G     18.4M  /mnt/boot-sav/zfs/var/log
rpool/ROOT/ubuntu_64fs0l/var/mail                  152K  6.86G       96K  /mnt/boot-sav/zfs/var/mail
rpool/ROOT/ubuntu_64fs0l/var/snap                 1.33M  6.86G      896K  /mnt/boot-sav/zfs/var/snap
rpool/ROOT/ubuntu_64fs0l/var/spool                 720K  6.86G      112K  /mnt/boot-sav/zfs/var/spool
rpool/ROOT/ubuntu_64fs0l/var/www                   152K  6.86G       96K  /mnt/boot-sav/zfs/var/www
rpool/USERDATA                                    17.4M  6.86G       96K  /mnt/boot-sav/zfs
rpool/USERDATA/mafoelffen_7vzpaq                  16.3M  6.86G     4.26M  /mnt/boot-sav/zfs/home/mafoelffen
rpool/USERDATA/root_7vzpaq                        1.04M  6.86G      192K  /mnt/boot-sav/zfs/root
```
Line 182 said: "Error: could not activate ZFS. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]"... But from the results, it did activate ZFS...

Will post later after I have some time to test on the LUKS machines...

---

### Post by MAFoElffen on 2022-02-16
On LUKS from a LiveCD...
20.04.3 with LUKS Mostly: [https://paste.ubuntu.com/p/W6kKjSFhSC/](https://paste.ubuntu.com/p/W6kKjSFhSC/)

But... I think I need to share how I open and mount LUKS. Your commands in your dialog, do not work, which where:
```

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/vda3: UUID="094ce3d4-6e4d-4764-960d-1467aef19984" TYPE="crypto_LUKS" PARTLABEL="/boot" PARTUUID="831559d2-7047-4e69-80bc-127f87ac5d83"
Device /dev/vda3: doesn't exist or access denied.

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/vda3: UUID="094ce3d4-6e4d-4764-960d-1467aef19984" TYPE="crypto_LUKS" PARTLABEL="/boot" PARTUUID="831559d2-7047-4e69-80bc-127f87ac5d83" MyVolume
Device /dev/vda3: doesn't exist or access denied.

```
That returned that it didn't exist

boot is luks1, root is luks2. Here is how I open luks encrypted filesystems
```

ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0    7:0    0    2G  1 loop /rofs
loop1    7:1    0 55.4M  1 loop /snap/core18/2128
loop2    7:2    0  219M  1 loop /snap/gnome-3-34-1804/72
loop3    7:3    0 32.3M  1 loop /snap/snapd/12704
loop4    7:4    0 65.1M  1 loop /snap/gtk-common-themes/1515
loop5    7:5    0   51M  1 loop /snap/snap-store/547
sr0     11:0    1  2.9G  0 rom  /cdrom
vda    252:0    0   25G  0 disk 
&#9500;&#9472;vda1 252:1    0    2M  0 part 
&#9500;&#9472;vda2 252:2    0  128M  0 part 
&#9500;&#9472;vda3 252:3    0  768M  0 part 
&#9492;&#9472;vda5 252:5    0 24.1G  0 part 

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# export DEV="/dev/vda"

root@ubuntu:~# export DM="${DEV##*/}"

root@ubuntu:~# export DEVP="${DEV}$( if [[ "$DEV" =~ "nvme" ]]; then echo "p"; fi )"

root@ubuntu:~# export DM="${DM}$( if [[ "$DM" =~ "nvme" ]]; then echo "p"; fi )"

root@ubuntu:~# sgdisk --print $DEV
Disk /dev/vda: 52428800 sectors, 25.0 GiB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): F55FCB42-F356-4C7B-A747-5D046D7B8907
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 52428766
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     EF02  GRUB
   2            6144          268287   128.0 MiB   EF00  EFI-SP
   3          268288         1841151   768.0 MiB   8301  /boot
   5         1841152        52428766   24.1 GiB    8301  rootfs

root@ubuntu:~# ls /dev/mapper/
control  LUKS_BOOT  ubuntu--vg-root  ubuntu--vg-swap_1  vda5_crypt

root@ubuntu:~# cryptsetup open ${DEVP}3 LUKS_BOOT
Enter passphrase for /dev/vda3: 

root@ubuntu:~# cryptsetup open ${DEVP}5 ${DM}5_crypt
Enter passphrase for /dev/vda5: 

```
Then I ran boot-info...

---

### Post by MAFoElffen on 2022-02-20
I see there is a new dev version... Should we test it? Or wait?

---

### Post by MAFoElffen on 2022-02-24
This thread (especially this post ad post #22) is relevant to something I think I should bring up about ZFS peculiarities and ZSys integration into Grub2...
[https://ubuntuforums.org/showthread.php?t=2472059&p=14082246#post14082246](https://ubuntuforums.org/showthread.php?t=2472059&p=14082246#post14082246)

Read the link for my description of the Grub2 ZFS/ZSys History and Restore menus. (Just so I don't have to retype and that)... This User just happens to be diagnosed as having a primary 'Chief Complaint" of having a Graphics Issue. Uncovered in the diagnosis, he has a secondary issue of not having those ZFS/ZSYS Menu's integrated into his Grub2 Boot Menu (which they should have).

Here is the differing Grub2 code:
```

### BEGIN /etc/grub.d/10_linux_zfs ###
 function gfxmode {
     set gfxpayload="${1}"
     if [ "${1}" = "keep" ]; then
         set vt_handoff=vt.handoff=1
     else
         set vt_handoff=
     fi
 }
 if [ "${recordfail}" != 1 ]; then
   if [ -e ${prefix}/gfxblacklist.txt ]; then
     if hwmatch ${prefix}/gfxblacklist.txt 3; then
       if [ ${match} = 0 ]; then
         set linux_gfx_mode=keep
       else
         set linux_gfx_mode=text
       fi
     else
       set linux_gfx_mode=text
     fi
   else
     set linux_gfx_mode=keep
   fi
 else
   set linux_gfx_mode=text
 fi
 export linux_gfx_mode
 function zsyshistorymenu {
     # $1: root dataset (eg rpool/ROOT/ubuntu_2zhm07@autozsys_k56fr6)
     # $2: boot device id (eg 411f29ce1557bfed)
     # $3: initrd (eg /BOOT/ubuntu_2zhm07@autozsys_k56fr6/initrd.img-5.4.0-21-generic)
     # $4: kernel (eg /BOOT/ubuntu_2zhm07@autozsys_k56fr6/vmlinuz-5.4.0-21-generic)
     # $5: kernel_version (eg 5.4.0-21-generic)
 
     set root_dataset="${1}"
     set boot_device="${2}"
     set initrd="${3}"
     set kernel="${4}"
     set kversion="${5}"
 
     menuentry 'Revert system only' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
         recordfail
         load_video
         gfxmode ${linux_gfx_mode}
         insmod gzio
         if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
         if [ ${boot_device} = /dev/nvme1n1p3 ]; then
             insmod part_gpt
             insmod zfs
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  c25c5e527df3275b
             else
               search --no-floppy --fs-uuid --set=root c25c5e527df3275b
             fi
         fi
         linux    ${kernel} root=ZFS=${root_dataset} ro   
         initrd    ${initrd}
     }
     menuentry 'Revert system and user data' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
         recordfail
         load_video
         gfxmode ${linux_gfx_mode}
         insmod gzio
         if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
         if [ ${boot_device} = /dev/nvme1n1p3 ]; then
             insmod part_gpt
             insmod zfs
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  c25c5e527df3275b
             else
               search --no-floppy --fs-uuid --set=root c25c5e527df3275b
             fi
         fi
         linux    ${kernel} root=ZFS=${root_dataset} ro   zsys-revert=userdata
         initrd    ${initrd}
     }
     menuentry 'Revert system only (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
         recordfail
         load_video
         insmod gzio
         if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
         if [ ${boot_device} = /dev/nvme1n1p3 ]; then
             insmod part_gpt
             insmod zfs
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  c25c5e527df3275b
             else
               search --no-floppy --fs-uuid --set=root c25c5e527df3275b
             fi
         fi
         echo Loading Linux ${kversion} ...
         linux    ${kernel} root=ZFS=${root_dataset} ro recovery nomodeset dis_ucode_ldr  
         echo 'Loading initial ramdisk ...'
         initrd    ${initrd}
     }
     menuentry 'Revert system and user data (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
         recordfail
         load_video
         insmod gzio
         if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
         if [ ${boot_device} = /dev/nvme1n1p3 ]; then
             insmod part_gpt
             insmod zfs
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  c25c5e527df3275b
             else
               search --no-floppy --fs-uuid --set=root c25c5e527df3275b
             fi
         fi
         echo Loading Linux ${kversion} ...
         linux    ${kernel} root=ZFS=${root_dataset} ro recovery nomodeset dis_ucode_ldr  zsys-revert=userdata
         echo 'Loading initial ramdisk ...'
         initrd    ${initrd}
     }
 }

```
Which what that does is show that History menu item, drills through the menu, sub-menus to select a Restore of a specific snapshot, then which version type of a restoration to do for that specific snapshot, then substitutes that snapshot name for what was there in the boot code lines. Also does some transient renaming magic of that snapshot so it remains as the current default boot item... (Simplistic explanation of...)

This User, for some reason has a secondary issue that the ZFS/ZSys Menu Integration is not there for him so he cannot restore to a previous point via his Grub2 Menu current Options. I do know the cli commands to do that, in place of doing it through the Grub2 Menu... So there is a fail back for that. But his Grub2 Menu will be needed to be regen'ed correctly eventually. I'm checking into a current bug that maybe related to this at GitHiub...

But there is also another current BPool Issue... which I mentioned to that User in that thread, just like previously when Ubuntu used /boot as a mounted partition. I think I described it in detail in Post #22... Where the BPool runs low on space on kernel updates, because of BPool Snapshots... I wrote a script to help with that, if you want to see how that works, and need to include anything from that.

The only reason I say this, is that Grub2 can be rolled back to "previous" a working condition, via ZFS snapshot rollbacks... This might be a plus to your repair of in boot-repair, and in your recommendations in boot-info.

Just thinking out loud. I think I may have figured out his Grub2 Boot Menu problem, which may be something he hasn't shared yet... But it wouldn't make sense from some of what he has done so far.

---

### Post by MAFoElffen on 2022-03-17
I see this from last week in the DEV PPA:
```
[TABLE="class: listing sortable"]
[TR]
[TD]boot-repair               [/TD]
[TD]                 4ppa200                                [/TD]
[TD]                   [YannUbuntu]("https://launchpad.net/~yannubuntu")                                      (2022-03-06)[/TD]
[/TR]
[/TABLE]

```
I haven't seen any activity in this thread (here) in over 3 weeks, but will continue to test this new version...

---

### Post by #&amp;thj^% on 2022-03-17
+1 on the activity.

---

### Post by YannBuntu on 2022-03-23
hi all, no activity since last update 4ppa200.
changelog between version 192 and 200:

* hide redundant Advices in log
* add ${CHROOTCMD}modprobe efivars
* show only once the errors on mount -r
* display free space only when > 10MiB
* improve secure boot detection
* added BIOS version
* display CHROOTCMD before grub-install in logs
* rm /boot/efi/EFI/ubuntu when error: cannot open /boot/efi/EFI/ubuntu/grubx64.efi: Not a directory.
* display message 'purge grub* packages from ${BLKIDMNT_POINT[$USRPART]}' when auto purge fails

@MAF: thx for the feeback. #70: please retry with ppa200, most issues should be fixed. 
#71: I will try to improve the luksOpen dialog 
#73 I don't know what/how to improve, feel free to submit a patch.

---

### Post by MAFoElffen on 2022-05-28
@yann... will get to that later this morning. Have a bit of catching up to do...

---

### Post by MAFoElffen on 2022-06-03
Okay... This weekend I will test the script on 20.04 and 22.04  ZFS-On-Root systems. There were some changes in ZFS and ZSys from 20.04  to 22.04...

Major change is that ZSys is not installed by  default... So auto ZFS snapshots are not provided by default, nor is the  "History" Menu Item turned on in the Grub Menu to restore to ZSys  System Snaphots... So if someone wanted to restore to a previous state,  they would have had to either Installed and turned on ZSys, where they  can then restore from the Grub Menu... Or manually created ZFS System  Snapshots, then mount and chroot into the system and ZFS filesystem,  then use ZFS Rollback manually to rollback a specific snapshot.

They  had plans to enhance development on ZSys, to setup an external config  file, so the user could set the number of snapshots to a count, keeping  the last "x" number of snapshots, then roll off the older snapshots...  Somehow, at least in the initial release of 22.04, it's not even a  default installed daemon anymore.

Hmmm... Maybe I'll look into  "that" more when I get more time. For the new test machine, I just  installed and setup ZSys, which they had said "was" their plan. (LOL)

---

### Post by MAFoElffen on 2022-10-21
Yann - 

I was busy updating the UbuntuForums 'system-info' script to Version 2.00-00...

I recently added a link to your boot-info ppa <STABLE> in my UbuntuForums 'system-info' script:
> 
For more detailed disk Information, please run the 'boot-info' script 
from: (STABLE) [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)


---

### Post by MAFoElffen on 2022-10-30
While assisting a user recently on the Forum, I revised my ZFS mount information and instructions for re-installing grub to Ubuntu ZFS-On-Root machines from a LiveCD...
```

#!/bin/bash

## MAFoElffen, <mafoelffen@ubuntu.com>, last modified 2022.10.31
#

sudo -i
apt zfs-initramfs
zpool export -a
DISK=$(fdisk -l | \
    grep '^/dev/' | \
    grep -i 'Solaris\|FreeBSD' | \
    head -n 1 | \
    awk '{print $1}' | \
    sed 's/\/dev\///g' | \
    cut -b -3 )
    
rpool_name=$(lsblk -o NAME,FSTYPE,LABEL | \
    grep -v '/snap/\|loop\|sr0' | \
    grep 'zfs_member' | \
    grep 'rpool' | \
    awk '{print $3}' )
    
bpool_name=$(lsblk -o NAME,FSTYPE,LABEL | \
    grep -v '/snap/\|loop\|sr0' | \
    grep 'zfs_member' | \
    grep 'bpool' | \
    awk '{print $3}' )
 
zpool import -N -R /mnt $rpool_name
zpool import -N -R /mnt $bpool_name
zfs load-key -a

pool_uuid=$(zfs list | \
    grep 'rpool/ROOT/ubuntu_' | \
    head -n 1 | \
    sed 's/rpool\/ROOT\/ubuntu_//g' | \
    awk '{print $1}' )
   
zfs mount $rpool_name/ROOT/ubuntu_$pool_uuid
zfs mount $bpool_name/BOOT/ubuntu_$pool_uuid
zfs mount -a

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount -t tmpfs tmpfs /mnt/run
mkdir /mnt/run/lock
chroot /mnt /bin/bash --login
mount -a

grub-install $DISK

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy

exit

mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}

zpool export -af
reboot

```
The user was a Legacy Boot, BUT... CSM ZFS installs create an ESP EFI directory that gets mounted under /boot, so it ends up being a dual arch BIOS/UEFI boot...
```

mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ sudo debconf-show grub-pc
  grub-efi/install_devices_disks_changed:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/install_devices_disks_changed:
  grub-pc/postrm_purge_boot_grub: false
* grub-pc/install_devices: /dev/vda
  grub-pc/install_devices_failed: false
  grub2/no_efi_extra_removable: false
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/linux_cmdline_default: quiet splash
  grub-efi/install_devices_failed: false
  grub2/kfreebsd_cmdline:
  grub2/unsigned_kernels_title:
  grub-pc/timeout: 0
  grub2/unsigned_kernels:
  grub-efi/install_devices:
  grub-pc/install_devices_empty: false
  grub2/linux_cmdline:
  grub-efi/install_devices_empty: false
  grub-efi/partition_description:
  grub2/update_nvram: true
  grub-pc/kopt_extracted: false
  grub-pc/disk_description:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/partition_description:
  grub-pc/hidden_timeout: true

```

---

### Post by MAFoElffen on 2022-11-01
@YannBuntu -

I have a question about this:
```

DISK=$(fdisk -l | \
    grep '^/dev/' | \
    grep -i 'Solaris\|FreeBSD' | \
    head -n 1 | \
    awk '{print $1}' | \
    sed 's/\/dev\///g' | \
    cut -b -3 )

# EDITTED

grub-install $DISK

```
...which assumes that Grub is going to be installed on the same disk that the bpool and rpool is on.

Which more correctly:
```

grep -E --color=never 'Value: \/dev\/disk\/' /var/cache/debconf/config.dat

```
"IS" the saved disk information of where Grub was installed to... Which for CSM would be the disk, or UEFI would be the ESP / EFI partition. Right?

---

### Post by MAFoElffen on 2022-11-03
Still helping that user. Changes were as follows:
```

#!/bin/bash

## MAFoElffen, <mafoelffen@ubuntu.com>, last modified 2022.11.03
#

sudo -i
apt zfs-initramfs
zpool export -a
DISK=$(fdisk -l | \
    grep '^/dev/' | \
    grep -i 'Solaris\|FreeBSD' | \
    head -n 1 | \
    awk '{print $1}' | \
    sed 's/\/dev\///g' | \
    cut -b -3 )
    
rpool_name=$(lsblk -o NAME,FSTYPE,LABEL | \
    grep -v '/snap/\|loop\|sr0' | \
    grep 'zfs_member' | \
    grep 'rpool' | \
    awk '{print $3}' )
    
bpool_name=$(lsblk -o NAME,FSTYPE,LABEL | \
    grep -v '/snap/\|loop\|sr0' | \
    grep 'zfs_member' | \
    grep 'bpool' | \
    awk '{print $3}' )
 
zpool import -N -R /mnt $rpool_name
zpool import -N -R /mnt $bpool_name
zfs load-key -a

pool_uuid=$(zfs list | \
    grep 'rpool/ROOT/ubuntu_' | \
    head -n 1 | \
    sed 's/rpool\/ROOT\/ubuntu_//g' | \
    awk '{print $1}' )
   
zfs mount $rpool_name/ROOT/ubuntu_$pool_uuid
zfs mount $bpool_name/BOOT/ubuntu_$pool_uuid
zfs mount -a

mount -o bind /dev /mnt/dev
mount -o bind /sys /mnt/sys
mount -t proc /proc /mnt/proc
echo "nameserver 127.0.0.53 8.8.8.8 1.1.1.1" > /mnt/etc/resolv.conf

mkdir /mnt/run/lock
chroot /mnt /bin/bash --login
mount -a

grub-install /dev/$DISK

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy

exit

mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}

zpool export -af
reboot

```

---

### Post by YannBuntu on 2022-12-03
hi all,

Winter is back, the bear is back home... in front of his PC :)

**boot-repair (4ppa203)**
  * hide snap from mount info 
  * hide 35_fwupd
  * improve default grub entry  --> OS by default should propose all OS except Linux  (before it proposed only Windows)
  * manage mokutil new sentence: SecureBoot enabled   --> solves 'SecureBoot enabled but mokutil says: SecureBoot enabled' -like messages
  * hide /sda2[/usr/share/hunspell] -like from mount points
  * fix CURRENTSESSIONPARTITION   --> allows Boot-Repair fto work in installed session
  * fix lib64 condition
  * bis stop displaying hexdump of MBRs 
  * improved detection of Legacy/efi Windows -> any Windows on GPT is considered efi


Notes for me:
#71: try to improve the luksOpen dialog 
#80 & 82: i need to test latest ZFS packages
check MAF post #81

---

### Post by MAFoElffen on 2023-05-18
> **YannBuntu said:**
> hi all,

Winter is back, the bear is back home... in front of his PC :)

**boot-repair (4ppa203)**
  * hide snap from mount info 
  * hide 35_fwupd
  * improve default grub entry  --> OS by default should propose all OS except Linux  (before it proposed only Windows)
  * manage mokutil new sentence: SecureBoot enabled   --> solves 'SecureBoot enabled but mokutil says: SecureBoot enabled' -like messages
  * hide /sda2[/usr/share/hunspell] -like from mount points
  * fix CURRENTSESSIONPARTITION   --> allows Boot-Repair fto work in installed session
  * fix lib64 condition
  * bis stop displaying hexdump of MBRs 
  * improved detection of Legacy/efi Windows -> any Windows on GPT is considered efi


Notes for me:
#71: try to improve the luksOpen dialog 
#80 & 82: i need to test latest ZFS packages
check MAF post #81
Oh Dang. I hadn't checked this thread in a while. Sorry Yann.

Doing some improvements and updates to the 'system-info' script the next few days, then will test all this again. And yes, openning LUKS encrypted is still a challenge. I've had some ideas on that.

---

### Post by MAFoElffen on 2023-07-21
Yann... I amended in instructions for chroot'ing into ZFS encrytped volumes. I hope you can incorporate this into your code... I think this will fix that when 'boot-repair' runs into that.

RE: [https://ubuntuforums.org/showthread.php?t=2488546&p=14151714#post14151714](https://ubuntuforums.org/showthread.php?t=2488546&p=14151714#post14151714)

---

### Post by YannBuntu on 2023-12-06
hi all,
sorry for my bad reactivity, I now spend most my free time to help OSM/Panoramax and Fdroid apps.
On Sunday I added the PPA packages for Mantic and Noble.
I need to update code to fix [this]("https://bugs.launchpad.net/boot-repair/+bug/2024986"). Anything else needs urgent fix ?

Notes for me:
[#71]("https://ubuntuforums.org/showthread.php?t=2470405&p=14081645#post14081645"): try to improve the luksOpen dialog
check MAF posts [#81]("https://ubuntuforums.org/showthread.php?t=2470405&p=14117740#post14117740") and [#85]("https://ubuntuforums.org/showthread.php?t=2470405&p=14151715#post14151715")

---

### Post by oldfred on 2023-12-06
Yann, glad to see you are still around.

Recently saw a Boot-Repair report that said Windows legacy installed. Windows boot loaders were (somehow) installed to gpt's protective MBR.
But since drive was gpt, and there was an ESP with Windows boot files, Windows was UEFI.

We are getting a lot of "Locked NVRAM" issues.
Many seem to be where they had working system, and the reinstall of grub gives that message.
But sometimes they do not have an Ubuntu entry in UEFI.

Some are related to UEFI that has extra settings beyond secure boot to prevent updates to UEFI.
Locked UEFI/BIOS setting: Lenovo UEFI screen with setting to lock UEFI:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

A lot seem to be fixed with random settings changes, so we cannot really tell what fixed it.
We have various posts where users have turned on or turn off Secure Boot, TPM or other systems & then grub install works.

HP PROBOOK with preinstalled WINDOWS 11. Locked NVRAM Larger ESP
[https://askubuntu.com/questions/1490046/grub-install-fails-at-the-end-of-ubuntu-22-04-installation-on-a-uefi-based-hp-pr](https://askubuntu.com/questions/1490046/grub-install-fails-at-the-end-of-ubuntu-22-04-installation-on-a-uefi-based-hp-pr)
HP Zbook 15 NVRAM locked, install issues multiple settings
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
Dell Locked BIOS
[https://ubuntuforums.org/showthread.php?t=2489447](https://ubuntuforums.org/showthread.php?t=2489447)

Do not know if there is an answer beyond the UEFI with specific settings like the Lenovos.

I have seen this for those with ubuntu entry in UEFI to avoid the grub error.
add "--no-nvram" to the "grub-install" command 
[https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0](https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0)

I have seen MAFoElffen ask about if efivars folder exists and use chroot.
[FONT=monospace][COLOR=#000000]ls /sys/firmware/efi/efivars/ [/COLOR]
[/FONT]https://ubuntuforums.org/showthread.php?t=2491460&page=2

---

### Post by YannBuntu on 2023-12-08
> **oldfred said:**
> Recently saw a Boot-Repair report that said Windows legacy installed. Windows boot loaders were (somehow) installed to gpt's protective MBR.
But since drive was gpt, and there was an ESP with Windows boot files, Windows was UEFI.

That should not happen with ppa209 or higher. If it does, please let me know.

> **oldfred said:**
> We are getting a lot of "Locked NVRAM" issues.
User needs to set up his firmware, can't do it from Boot-Repair.

> **oldfred said:**
> I have seen this for those with ubuntu entry in UEFI to avoid the grub error.
add "--no-nvram" to the "grub-install" command 
It just hides the error. 

> **oldfred said:**
> I have seen MAFoElffen ask about if efivars folder exists and use chroot. [https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0](https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0)
thx, I'll have a look.

---

### Post by YannBuntu on 2023-12-08
ppa2057

  * improved ZFS management (to be tested)

ppa209

  * detects copies of grub in windows efi via md5
  * WindowsGPTwithoutESP detected You may want to retry after repairing ESP via command in Windows: bcdboot Letter:\Windows /l fr-fr /s x: /f ALL

---

### Post by #&amp;thj^% on 2023-12-08
As I live and breath Look who's here YannBuntu
> * improved ZFS management (to be tested)
is it ready to test then from the PPA?
```
zpool status
  pool: bpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	bpool                                   ONLINE       0     0     0
	  fec209ba-5d9b-41df-b7fd-bbd77bbba535  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	rpool                                   ONLINE       0     0     0
	  eb96bca0-1c4e-424c-b8e9-ed3a0151e024  ONLINE       0     0     0

errors: No known data errors

  pool: tank
 state: ONLINE
config:

	NAME        STATE     READ WRITE CKSUM
	tank        ONLINE       0     0     0
	  sdc2      ONLINE       0     0     0

errors: No known data errors

```

---

### Post by YannBuntu on 2023-12-08
you're super fast :) please wait for the ppa2057 to be available for your Ubuntu version, probably tomorrow.  You can check PPA status here: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair/+packages)

---

### Post by #&amp;thj^% on 2023-12-08
Thanks Yann and will do ;)

---

### Post by YannBuntu on 2023-12-09
2057 is buggy, please wait **ppa2058**.  EDIT: it's available now.

---

### Post by YannBuntu on 2023-12-09
**ppa2059**
  * final advice when partition containing /boot (MBR boot only) or ESP ends after 100GB

---

### Post by #&amp;thj^% on 2023-12-09
Results are in: [https://paste.ubuntu.com/p/DDJmVNDSk5/](https://paste.ubuntu.com/p/DDJmVNDSk5/)

---

### Post by YannBuntu on 2023-12-10
@1fallen: thx. Please can you also create a Boot-Info report ( https://help.ubuntu.com/community/Boot-Info ) from live session ?

---

### Post by #&amp;thj^% on 2023-12-10
> **YannBuntu said:**
> @1fallen: thx. Please can you also create a Boot-Info report ( [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) ) from live session ?

Will do, give me a little time to finish some other obligations, but it will be today.
I threw in encryption this go round, with secure boot.

---

### Post by #&amp;thj^% on 2023-12-10
Don't pay the ransom, I escaped.
New report: [http://paste.ubuntu.com/p/PWCNX2kNHb/](http://paste.ubuntu.com/p/PWCNX2kNHb/)
Sorry for the delay, but you know how you developers are :)

---

### Post by YannBuntu on 2023-12-11
thx but your last log shows 'ppa125', which is an old version. Please can you boot on your Boot-Repair-Disk in live session, connect internet, update the 'boot-sav' package then run boot-info ?

---

### Post by #&amp;thj^% on 2023-12-11
> **YannBuntu said:**
> thx but your last log shows 'ppa125', which is an old version. Please can you boot on your Boot-Repair-Disk in live session, connect internet, update the 'boot-sav' package then run boot-info ?

Did that 4 times and no change...I was hoping you would see that is was from the older PPA

---

### Post by #&amp;thj^% on 2023-12-11
> **1fallen said:**
> Did that 4 times and no change...I was hoping you would see that is was from the older PPA

I may have found yet another bug on 24.04 xubuntu installer, anyway from Live 22.04 Jammy
```
apt policy boot-repair
boot-repair:
  Installed: 4ppa2060
  Candidate: 4ppa2060

```
Report found here: [https://paste.ubuntu.com/p/yGHtwxxsGt/](https://paste.ubuntu.com/p/yGHtwxxsGt/)

---

### Post by #&amp;thj^% on 2023-12-11
bad post
 Last Update: 2021-12-16 for the boot-rerpair disk??

---

### Post by YannBuntu on 2023-12-12
Yes, i need to find some time to update Boot-Repair-Disk.
Thx for the new log, it shows failure when trying to activate zfs.
Which commands would you use to enable ZFS from live session? Please can you try and show the output?

---

### Post by #&amp;thj^% on 2023-12-12
It wouldn't accept my encrypted LUKs passphrase.
Which is how I logged in to this current session
Maybe the .iso, is not really needed, as we tell folks here in UF to use their Live Installer and add the PPA then run the boot-info.
Up to you. :)
Oopps I forgot to reply on the commands used to mount my encrypted ZFS
```
udisksctl unlock -b /dev/xxx
udisksctl mount -b /dev/mapper/xxx
```

---

### Post by breakdaze on 2024-01-28
Does the running from command line in README.md need to suggest chmod +x or would having only the user run it be acceptable, as in chmod u+x ?

---

