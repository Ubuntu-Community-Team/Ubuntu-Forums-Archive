---
title: "Clean Ubuntu 11.10 server installation failing (10.04.3 works)"
date: 2011-10-26
forum: Server Platforms
---

### Post by jlinoff on 2011-10-26
I apologize in advance if this is something silly or if it has already been answered. I searched the forum and the internet for hours before posting this. I also ran multiple experiments installing other servers.

I am having trouble doing a clean installation of Ubuntu 11.10 server amd64 on a Dell Precision T5400. The problem is that the partition menu gives me these 3 options:

1. Configure iSCSI volumes
2. Undo changes to partitions
3. Finish partitioning and write changes to disk

There are no options for defining partitions or configuring LVM.

If I choose #1 "iSCSI volumes" it asks me for an initiator. I don't have one. This is a standalone machine on its own network.

If I choose #2 "Undo changes to partitions" it hangs.

If I choose #3 "Finish partitioning ..." it tells me that i don't have a root partition. Which is what I want to create in the first place.

I have two 250GB disks configured in the BIOS for AHCI. The disks (Seagate and Hitachi).

It doesn't matter if I choose RAID or no RAID during the configuration process, I still get the same menu options.

The server installation works correctly on this host for "Ubuntu server 10.04.3 amd64" and "CentOS 5.7" so this may be a problem with 11.10 release. It may also be a subtle problem with my BIOS settings but i have checked everything that i could think of.

For the Ubuntu Server 10.04.3 installation the partitioning menu looks like this (which is what I expected):

1. Guided - use entire disk
2. Guided - use entire disk and set up LVM
3. Guided - use entire disk and set up encrypted LVM
4. Manual

Can anyone suggest how to proceed? I am stuck. 

Thanks.

---

### Post by darkod on 2011-10-26
"Finish partitioning" sounds like it "thinks" it is in the middle of it. Have you tried booting it with the desktop version into the live environment and check the disk(s) with Gparted. If it shows any partitions, try deleting them and leave the disks as "unallocated".

See what the 11.10 server install says after.

There might also be some remains of raid metadata which doesn't bother 10.04 but it bothers 11.10.

Are you trying to use raid settings on your board?

---

### Post by jlinoff on 2011-10-26
Thank you for the quick response.

> "Finish partitioning" sounds like it "thinks" it is in the middle of it. Have you tried booting it with the desktop version into the live environment and check the disk(s) with Gparted. If it shows any partitions, try deleting them and leave the disks as "unallocated".

I did boot with the desktop version and partitions were present. I didn't try to delete them because I didn't think that it mattered because it worked with 10.04. It sounds like that might be the source of the problem. I will try it now.

> There might also be some remains of raid metadata which doesn't bother 10.04 but it bothers 11.10.


That makes sense.

> Are you trying to use raid settings on your board? 

No. I might try to madm later but for now I just want to bring up the server and install Openstack for testing.

I really appreciate your insight. I didn't occur to me that 11.10 would care about a previous RAID/LVM setup.

---

### Post by jlinoff on 2011-10-26
> I didn't try to delete them because I didn't think that it mattered because it worked with 10.04. It sounds like that might be the source of the problem. **I will try it now.**

I booted up using the live desktop, ran gparted and deleted all partitions. I then shutdown and rebooted with the 11.10 live disk again and re-ran gparted to verify that the partitions were gone from both sda and sdb. They were. 

I then rebooted using the 11.10 server disk. The same problem occurred. 

I then re-verified that the 10.04.3 server worked. 

I am sure that you are on the right track but it appears that deleting the partitions is not sufficient. There must be some other state data that is confusing the configuration. 

To get more information I rebooted using the 11.10 server disk, went into expert mode, removed the quiet option to get more information about what was going on and rebooted. It said that no partitions were detected but still gave me the same three menu options.

I also tried booting in recovery mode. It ended up in the same place.

In all cases i disabled HW raid.

I am confused. I am sure that this is working for other folks. I wonder why I am having problems. Maybe there is a configuration problem. Here are my machine details. Perhaps that will shed some light on the matter.

MODEL: DELL Precision T5400
CPUs: 2 x Xeon E5430 Quad Core CPUs
RAM:  16GB
DISKS: 
   (1) 250GB - ATA ST3250310AS (scsi)
   (2) 250GB - ATA Hitachi HDT72502 (scsi)

Can you suggest anything else to try?

---

### Post by collisionystm on 2011-10-26
I have worked with that computer before. It has a built in raid controller. I see you did this

> I have two 250GB disks configured in the BIOS for AHCI. The disks (Seagate and Hitachi).

Do you see anywhere to change the drive controller to SATA ?

> Setting Your Computer to RAID-Enabled Mode

	NOTE: This procedure is only possible if you ordered your computer with a RAID configuration.
Enter the system setup program (see System Setup). 

Press the up- and down-arrow keys to highlight Drives, and press <Enter>. 

Press the up- and down-arrow keys to highlight SATA Operation, and press <Enter>. 

Press the left- and right-arrow keys to highlight RAID Autodetect /AHCI or RAID Autodetect/ ATA, according to your preferences; press <Enter>, and then press <Esc>. 

For more information about RAID options, see System Setup Options.

Press the left- and right-arrow keys to highlight Save/Exit, and press <Enter> to exit system setup and resume the boot process. 

Dell Manual for your machine.
[http://support.dell.com/support/systemsinfo/document.aspx?c=us&l=en&s=hied&~file=/systems/wst5400/en/ug/html/advfeat.htm]("http://support.dell.com/support/systemsinfo/document.aspx?c=us&l=en&s=hied&~file=/systems/wst5400/en/ug/html/advfeat.htm")




P.S. While looking up your problem I see that someone succesfully had Snow Leopard running on your machine!
[http://www.insanelymac.com/forum/index.php?showtopic=188929](http://www.insanelymac.com/forum/index.php?showtopic=188929)

---

### Post by jlinoff on 2011-10-26
Thank you. It sounds like the problem might be related to AHCI...

Interesting, I thought that was the newer instruction specification for SATA drives in RAID configurations. I have been using that setup for a number of years. It never would have occurred to me that was the source of the problem.

I will play with the SATA setup: ATA and RAID tonight to see if that helps.

> P.S. While looking up your problem I see that someone succesfully had Snow Leopard running on your machine!

That's impressive and encouraging.

I was able to setup the server as a KVM guest on another Ubuntu 11.10 desktop so I am not completely stuck at this point.

---

### Post by collisionystm on 2011-10-26
> **jlinoff said:**
> Thank you. It sounds like the problem might be related to AHCI...

Interesting, I thought that was the newer instruction specification for SATA drives in RAID configurations. I have been using that setup for a number of years. It never would have occurred to me that was the source of the problem.

I will play with the SATA setup: ATA and RAID tonight to see if that helps.



That's impressive and encouraging.

I was able to setup the server as a KVM guest on another Ubuntu 11.10 desktop so I am not completely stuck at this point.


Well atleast you have some kind of a fix for now.

What role will the server be playing? 

And for your drives... check the physical connections on the motherboard also. I think they are color coordinated and labeled SATA0 - SATA 5 or something like that. Check the manual to see if certain SATA ports are meant for RAID only.

---

### Post by jlinoff on 2011-10-27
> What role will the server be playing?
This server is acting an OpenStack master with nova, swift and glance installed to test that SW stack. I am comparing it to my current solution based on cobbler, Xen 3.4.3 and custom tools. If it works, there will be two of these acting in tandem (HA) for a small private cloud.

> And for your drives... check the physical connections on the motherboard also. I think they are color coordinated and labeled SATA0 - SATA 5 or something like that. Check the manual to see if certain SATA ports are meant for RAID only. 
Excellent suggestions. Thank you. I did a physical check yesterday. Also when I booted with CentOS (see below) I ran smartctl and the drives were in good shape. 

Since yesterday I have run 9 experimental setups to try understand what was going on.

_Experiments 1-6_
I discovered that Ubuntu 11.10 is just not going to work regardless of the SATA operations configuration. I tried the following:
[LIST=1]
[*]RAID Autodetect / AHCI with RAID enabled at boot time
[*]RAID Autodetect / AHCI with RAID disabled at boot time
[*]RAID Autodetect / ATA with RAID enabled at boot time
[*]RAID Autodetect / ATA with RAID disabled at boot time
[*]RAID on with RAID enabled at boot time
[*]RAID on with RAID disabled at boot time
[/LIST]

None of them worked. In cases 1,2,5,6 the partition options were not usable. For cases 3, 4 it wouldn't even boot because of grub errors.

In all cases I verified that the disks were completely unassigned (no partitions).

_Experiment 7_
I then tried Ubuntu 10.04.3 server. It worked the first time with the default configuration.

_Experiment 8_
I also tried Ubuntu 11.10 desktop. It worked the first time with the default configuration.

_Experiment 9_
Then I tried CentOS 6.0 and it worked the first time.

I have also run these hosts in production as Xen 3.x hypervisors with various flavors of CentOS and Fedora.

At this point I am beginning to think that there is a problem with the Ubuntu 11.10 server distribution. 

Unfortunately, having spent several days on this I am out of time and need to pick another platform. I simply can't justify spending time on this when I can't boot a single production server. My current inclination is to give 10.04 a go and see how it works out.

I want to say, for the record, that I really, really like Ubuntu 11.10 and am using the desktop version for my development. I am really disappointed that I can't use the server version at this time. 

If there is a patch release in the near future, I would be happy to try it.

Also, I really appreciate the help that you and others have provided.

---

### Post by darkod on 2011-10-27
Your problem is really strange. Just to add, that being a LTS, the 10.04 was probably the recommended way to go from the start.

From your last post, you can't wait more, otherwise the next LTS version, the 12.04, is coming in April 2012.

---

### Post by jlinoff on 2011-10-27
> Your problem is really strange. 
Yup. It is driving me nuts.

> Just to add, that being a LTS, the 10.04 was probably the recommended way to go from the start.
Thanks. That is what I will do.

> From your last post, you can't wait more, otherwise the next LTS version, the 12.04, is coming in April 2012. 
Great. Thanks for the heads up.

I am also happy to try any patches or other ideas as time allows.

---

### Post by Vegan on 2011-10-27
This is rather interesting. Not many machine choke using Linux.

I wonder if the disk controller is not recognized

---

### Post by jlinoff on 2011-10-27
Installed Ubuntu 11.10 server amd64 on a Dell XPS 9100 with no problems. I am now using this host as my test bed.

I also confirmed that the installation failed on another T5400 host that was running CentOS 6 before the test. There is definitely something about my T5400 HW configuration that is causing problems.

---

### Post by jlinoff on 2011-10-27
> This is rather interesting. Not many machine choke using Linux.
Yup. It has been a long time since I have seen a problem like this.

> I wonder if the disk controller is not recognized 
You might be right but if that were the case wouldn't it also fail for the Ubuntu 11.10 desktop installation? Also, I was able to install CentOS 5.5 and CentOS 6 servers on the same machines with no problems using manual and PXE installations.

---

