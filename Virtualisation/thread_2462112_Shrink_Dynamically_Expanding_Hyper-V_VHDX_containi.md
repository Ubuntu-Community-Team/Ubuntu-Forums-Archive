---
title: "Shrink Dynamically Expanding Hyper-V VHDX containing LVM Ubuntu Server"
date: 2021-05-13
forum: Virtualisation
---

### Post by Marc-NJ on 2021-05-13
Initially I set up a dynamically expanding VHDX under Hyper-V that was about 6 TB and then installed Ubuntu Server 20.04 using LVM on it.  I've since managed to shrink the installed Ubuntu Server down to 155 GB, but the dynamically expanding VHDX still has a capacity of 6 TB.  I want to move this to a drive that has nowhere near 6 TB.  I think it might work anyway since the Ubuntu Server can't go bigger than 155 GB, but I'd like to VHDX to reflect maybe 200 or 250 GB max.  I can't figure out how to shrink it though without killing the installed Ubuntu Server.  If I remove all checkpoints and just go into editing the VHDX via Hyper-V and shrink it that way, it somehow causes an issue and the Ubuntu Server won't load up afterwards.  I must be missing a step here...any help is greatly appreciated!!

---

### Post by Marc-NJ on 2021-05-14
[COLOR=#242729][FONT=system-ui]OK, so I actually think I figured it out (with help from some of the websites below) - it was not easy.[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui]
First, as mentioned, I had to previously (prior to asking the above question) reduce the size of everything in Ubuntu Server (posting below just to be complete) - I did that following the below websites:[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui][https://maideveloper.com/blog/how-to-move-lvm-partition-to-another-disk-drive](https://maideveloper.com/blog/how-to-move-lvm-partition-to-another-disk-drive)[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui][How can I resize an LVM partition? (i.e: physical volume)]("https://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume")[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui]
Here's what I did:[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui]
I booted into a LiveCD (Ubuntu Desktop 20.04) and in terminal ran these commands (I think - my memory is a bit hazy at this point):[/FONT][/COLOR]
sudo e2fsck -f /dev/<VOLUME_GROUP/<LOGICAL_VOLUME>
sudo resize2fs /dev/<VOLUME_GROUP>/<LOGICAL_VOLUME> 150G
sudo lvreduce -L 155G /dev/<VOLUME_GROUP>/<LOGICAL_VOLUME>
sudo resize2fs /dev/<VOLUME_GROUP>/<LOGICAL_VOLUME>
[COLOR=#242729][FONT=system-ui]You should replace <VOLUME_GROUP> and <LOGICAL_VOLUME> with appropriate entries for your system. I believe the above commands: checks for errors, then shrinks the file system, then shrinks the logical volume (don't shrink to something smaller than new file system size you just shrunk), then extends the file system to use all available space on the logical volume. I also think something along these lines might have worked but I didn't try: sudo lvreduce --resizefs -L 155G /dev/<VOLUME_GROUP>/<LOGICAL_VOLUME>

[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui]Then I went into GParted GUI on the LiveCD and used that to shrink the partition to it's new 155 GB size and was left with a ton of unallocated space. This is where my question above picks up.[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui]
So next I found this answer: [How do I move my LVM 250 GB root partition to a new 120GB hard disk?]("https://askubuntu.com/questions/161279/how-do-i-move-my-lvm-250-gb-root-partition-to-a-new-120gb-hard-disk")[/FONT][/COLOR]
[COLOR=#242729][FONT=system-ui]
Here's what I did:[/FONT][/COLOR]

[LIST=1]
[*]Used Hyper-V to create a new dynamically expanding VHDX hard drive (this time only 250 GB) and attached it to my existing Ubuntu Server Hyper-V
[*]Booted into LiveCD again and used GParted to create exactly the same partitions on this new VHDX hard drive (sdb) that I had on my existing 6 TB dynamically expanding VHDX hard drive (sda) - even setting the flags, etc.
[*]Booted back into my Ubuntu Server and ran these commands:
[LIST]
[*]sudo pvcreate /dev/sdb3 *(sda3 is where my logical volume resides)*
[*]sudo vgextend <VOLUME_GROUP> /dev/sdb3
[*]sudo pvmove /dev/sda3 /dev/sdb3
[*]sudo vgreduce <VOLUME_GROUP> /dev/sda3
[/LIST]

[*]Booted into Clonezilla and cloned sda1 to sdb1 and then cloned sda2 to sdb2
[*]Modified the settings of the Hyper-V:
[LIST]
[*]removed the new second 250 GB VHDX hard drive
[*]adjusted the primary drive to point to the new 250 GB VHDX hard drive
[/LIST]

[*]Booted up the Ubuntu Server Hyper-V and got a weird error initially (briefly) and then it booted fine and voila - I was using the 250 GB hard drive! The error I got was: System BootOrder not found.  Initializing defaults.  Creating boot entry "Boot0004 with label "ubuntu" for file "\EFI\ubuntu\shimx64.efi"
[*]Realized that if you went to look at the Hyper-V settings under Firmware -> Boot order, there were now 2 shimx64.efi files - one at the very top (the new one that apparently was created by Hyper-V in step 6 above) and one below DVD Drive (the old one). No easy way to remove the old one - so I found this site: [https://vmlabblog.com/2018/08/how-to-change-vm-bootorder-with-powershell/](https://vmlabblog.com/2018/08/how-to-change-vm-bootorder-with-powershell/) which provided some guidance
[*]In an administrator PowerShell, ran these commands:
[LIST]
[*]$ubuntuserver = Get-VMFirmware "<NAME OF VIRTUAL MACHINE IN HYPER-V>"
[*]$goodfile = $ubuntuserver.BootOrder[0]
[*]$dvddrive = $ubuntuserver.BootOrder[1]
[*]$badfile = $ubuntuserver.BootOrder[2]
[*]$hddrive = $ubuntuserver.BootOrder[3]
[*]$network = $ubuntuserver.BootOrder[4]
[*]Set-VMFirmware -VMName "<NAME OF VIRTUAL MACHINE IN HYPER-V>" -BootOrder $dvddrive,$goodfile,$hddrive,$network
[*]$ubuntuserver.BootOrder *(just to confirm everything)*
[/LIST]

[*]And I think that did the trick. I believe I'm now all set.
[/LIST]
[COLOR=#242729][FONT=system-ui]
I would welcome any comments or checks on the above since I'm not entirely sure what I did is OK, but it seems to be. Hope this helps others in the future too![/FONT][/COLOR]

---

