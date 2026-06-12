---
title: "physical disk with vmdk problem"
date: 2014-10-10
forum: Virtualisation
---

### Post by info24 on 2014-10-10
Hi,


I have a virtualization server, ubuntu 12.04 LTS,  running virtualbox in headless mode. On it where several VM's such as a Windows Domain Controller / Fileserver, utilizing two physical disks with generated vmdk files. (These files were name dev-sdc.vmdk and dev-sdd.vmdk). 

A few days ago after a planned shutdown of the physical machine, the server broke down and was unable to boot up again. The problem was a broken power supply. Since I was going to upgrade hardware anyway, I also upgraded the motherboard and basically a complete different chipset resulting in having to completely wipe and reinstalling the base operating system which is now running ubuntu server 14.04 LTS. At the time of shutdown from the previous setup, all running VM's where put into a "save" state. However, because I couldn't edit the VM's configuration, I had to discard it, so I could fix some problems.

The vmdk files that were generated from the previous system setup, don't work anymore because the drives changed names to /dev/sdc1 and /dev/sdd1, so I generated new vmdk files and attached them to the virtual machine.

The problem that I'm having now is that Windows recognizes the drives, but the partitions just say "Healthy (Unknown Partition) 857GB" (This should be NTFS).
To be sure that the partitions were still good, I checked with the command fdisk -ls on the host and the are recognized as followed:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.

```

On the virtual machine, those two disks are displayed as illustrated in this screen shot.
[ATTACH=CONFIG]257114[/ATTACH]

To my knowledge, it is suppose the be one big partition for each disk. I know it's the VMDK files where the error is. I still have the old vmdk's is there a way I can fix this or did someone have had the same problem?

I don't really want to loose any data on those disks



Thank you for your input

---

### Post by info24 on 2014-10-10
Solved.

Looks like sdc1 is a partition on sdc. I generated a new vmdk that points to sdc now and it works. Looks like I learned something new today.

---

