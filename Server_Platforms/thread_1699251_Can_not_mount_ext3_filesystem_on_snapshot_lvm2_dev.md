---
title: "Can not mount ext3 filesystem on snapshot lvm2 device."
date: 2011-03-03
forum: Server Platforms
---

### Post by dodtsair on 2011-03-03
Here is the problem.  When I run 
sudo mount -t ext3 /dev/mapper/vol_group1-name1p5 name1p5

The command takes a ton of time and eventually fails.  I find entries like the following in my syslog:

Mar  3 08:22:00 dodtsair kernel: [39317.220777] ata3.00: exception Emask 0x0 SAct 0x11 SErr 0x0 action 0x0
Mar  3 08:22:00 dodtsair kernel: [39317.220787] ata3.00: irq_stat 0x40000008
Mar  3 08:22:00 dodtsair kernel: [39317.220796] ata3.00: failed command: READ FPDMA QUEUED
Mar  3 08:22:00 dodtsair kernel: [39317.220810] ata3.00: cmd 60/48:20:f0:c2:00/00:00:0a:00:00/40 tag 4 ncq 36864 in
Mar  3 08:22:00 dodtsair kernel: [39317.220813]          res 51/40:48:25:c3:00/00:00:0a:00:00/00 Emask 0x409 (media error) <F>
Mar  3 08:22:00 dodtsair kernel: [39317.220819] ata3.00: status: { DRDY ERR }
Mar  3 08:22:00 dodtsair kernel: [39317.220824] ata3.00: error: { UNC }
Mar  3 08:22:00 dodtsair kernel: [39317.222703] ata3.00: configured for UDMA/133
Mar  3 08:22:00 dodtsair kernel: [39317.222729] ata3: EH complete


Here is some back ground.  I play around with various server software.  Rather then putting a whole bundle of random stuff on my linux desktop I run KVM virtual machines and play with servers there.  In order to facilitate this I created a template vm that I don't run much.  Then I use lvm2 to create a snap shot of that template.  The scripts also mount the new instance and make any modifications needed to that filesystem.  It creates the new entries in kvm.  

The other thing I like to do is put server software in a vm to isolate it from my system.  Conceptually reducing the risk of anyone penetrating the server.  I played around with a bind server and decided to keep it around as a local caching name server.  I recently did an update of my main machine and rebooted.  After the reboot of the three vms I have kept around one did not come up.  Once I got onto the vm I noticed the vm did load the boot loader, but it seemed to fail when attempting to load the kernel.

I have since for triage moved off kvm.  So this is not a kvm issue.  Since I wanted to be able to mount the vm partition on the host.  I setup the template to run on one logical volume.  Then when installing the template I used plain partitions for the virtual disk. I put the swap in front.  Then used the rest of the 10g for the main file system.  

Thus at this point if the vm is not running and I want to mount its partition.  I can run:
sudo partprobe /dev/mapper/vol_group1-name1
That creates a new device for each partition.  Then I can run
sudo mount -t ext3 /dev/mapper/vol_group1-name1p5 /mnt/name1p5/


I wondering if I simply ran out of space?  When you create a snapshot on lvm2 you have to specify how big it is.  You can make it smaller then the actual drive image.  Since it is a snapshot and the appropriate bits are already on disk it does not need to copy them.  Instead the drive image size is a changelog for any changes the happen to the source or target since the snapshot was created.  I assumed that since I created the snapshot with equal size to the original then it had enough space to handle as many modifications as possible.  

Is there a way I can check to see if my lvm2 snapshot is full?

---

