---
title: "Grub Assistance after 3rd OS install"
date: 2016-10-23
forum: Windows
---

### Post by infinitelink on 2016-10-23
This one should be a little fun--and if after fixing this you want, please do explain the problem to me, and point to relevant resources on the Grub2 design so that I can turn around and pay forward to the next guy or gal who comes on the forums with a similar problem. 

Quick Background: 

I had Windows 8.1 (shudder) installed, and then installed Linux Mint 16.04 LTS. 2 drives in this system, MBR to the Linux drive. 

(Much) Later I installed (yesterday) Windows 2012 Server R2 to a third drive (just installed) in order to learn it. **I only installed it after disconnecting the other 2 drives in the vain hope of avoiding issues.** Plan was to install WinServer and then use boot-repair to update Grub2. 

After reconnecting everything, upon restart and without using boot-repair (to see what happened) my system skips Grub2 and goes straight to Windows 8.1 login. 

So I restart with a USB key, and use boot repair. This time I choose to set boot on sda (the 2nd partition of the WinServer hard drive to be more precise) whereas it had been on sdc (with the linux install) and have boot-repair put Grub2 there. 

No dice--restart gives me the Windows 8 login screen. 

I go back in with the USB live system, and re-use boot repair, but this time I set it back to sdc (where the .img file can be found). 

Still getting Windows 8 login. 

So...help? 

Here is a link to a google doc with the repair log/report. Note I plan to leave it as a link this way so that others who have similar problems or want to learn can reference the same doc you and I can see/are using. :) 

**Repair Log: **

[https://docs.google.com/document/d/1Hsq_0UPND4nTbMqR5FX6WPj308ZUV6baGric3TxMexY/edit?usp=sharing](https://docs.google.com/document/d/1Hsq_0UPND4nTbMqR5FX6WPj308ZUV6baGric3TxMexY/edit?usp=sharing)

(Edit: /dev/sde in that doc is the usb-drive which is running live linux!)

---

### Post by oldfred on 2016-10-23
You have mixed BIOS & UEFI boot loaders in several drives. You need to make sure configurations are set for UEFI and always only boot in UEFI mode.

You have grub or Windows installed to gpt protective MBR for BIOS boot. Note Windows on gpt will never boot in BIOS mode.

Ubuntu can boot from gpt with either UEFI if ESP - efi system partition available, or BIOS if bios_grub partition is available. I actually add both partitions to all drives now, but usually only configure for UEFI boot, so gpt's MBR is blank.

How you install system UEFI or BIOS is based on how you boot install media for both Windows & Ubuntu. But that install from flash drive may not be the same boot mode as you have set for hard drive(s) in UEFI/BIOS. You must be consistent in installing and UEFI settings for booting.
There actually are now 3 ways to install and boot, so do not mix them.
UEFI with Secure Boot
UEFI
BIOS/CSM/Legacy

If you install Windows in BIOS mode to a drive previously in gpt, it will incorrectly convert drive to MBR(msdos) leaving backup gpt partition table. Then Linux partition tools see both MBR & gpt and fail.

Boot-Repair only knows ext4. You cannot run fsck which is only for ext2, ext3 or ext4 formats on any other format. 
If file system repair is required then you will have to manually run the correct repair tool for your file system.

---

### Post by howefield on 2016-10-23
Moved to the "*Windows*" forum.

---

### Post by infinitelink on 2016-10-23
> **oldfred said:**
> You have mixed BIOS & UEFI boot loaders in several drives. You need to make sure configurations are set for UEFI and always only boot in UEFI mode.

You have grub or Windows installed to gpt protective MBR for BIOS boot. Note Windows on gpt will never boot in BIOS mode.


I'm not sure of the significance here because right now Windows will boot. Point me to the right resources if you would or explain and I'd really appreciate it--and whoever else I can be of assistance to later on account of leveling-up. ;) (Pay it forward and that jazz.)

> **oldfred said:**
> 
Ubuntu can boot from gpt with either UEFI if ESP - efi system partition available, or BIOS if bios_grub partition is available.


Apologies. "ESP"?

> **oldfred said:**
> I actually add both partitions to all drives now, but usually only configure for UEFI boot, so gpt's MBR is blank.

Both partitions? (I know what a partition is, I'm just not sure what you mean here.) 

> **oldfred said:**
> 

How you install system UEFI or BIOS is based on how you boot install media for both Windows & Ubuntu. But that install from flash drive may not be the same boot mode as you have set for hard drive(s) in UEFI/BIOS. You must be consistent in installing and UEFI settings for booting.

I don't have an install from a flash drive actually. :)

> **oldfred said:**
> If you install Windows in BIOS mode to a drive previously in gpt, it will incorrectly convert drive to MBR(msdos) leaving backup gpt partition table.

I installed Windows Server to a new drive **while the other drives were disconnected** specifically to prevent Windows Server from altering the other drives, MBR, Grub2, etc. 

> **oldfred said:**
> Then Linux partition tools see both MBR & gpt and fail.

But you're saying that this can somehow still affect the other drives/Grub2/mbr? Like upon repair? Or?

> **oldfred said:**
> Boot-Repair only knows ext4. You cannot run fsck which is only for ext2, ext3 or ext4 formats on any other format.

So you're saying that boot-repair wouldn't even properly get/see the additional windows install, or? It seems like it did see it and work with it though, just didn't get the core.img right (re-point or anything like that). The lack of the core.img deal is why I repeated and went back to sdc and removed the boot flag from sda (doing fdisk -l with sudo on livelinux shows the boot flag is only on sdc1 now, as it should be). 

> **oldfred said:**
> 
If file system repair is required then you will have to manually run the correct repair tool for your file system.

? I'm not sure what would have to be repaired though--pretty sure that Windows Server couldn't modify the other drives due to being disconnected physically at the time precisely to avoid troubles like that.

---

### Post by infinitelink on 2016-10-23
> **howefield said:**
> Moved to the "*Windows*" forum.

Er...is this "Windows"? Dealing with Grub2, and hoping to learn enough here/work with people so this becomes something others can reference, and of course so I could help with Grub2 as well later. :)

---

### Post by howefield on 2016-10-23
> **infinitelink said:**
> Er...is this "Windows"? Dealing with Grub2, and hoping to learn enough here/work with people so this becomes something others can reference, and of course so I could help with Grub2 as well later. :)

Err.. It is not Ubuntu. 

Take your pick, the *Windows* forum or the *Mint* forum.

---

### Post by infinitelink on 2016-10-23
> **howefield said:**
> Err.. It is not Ubuntu. 

Take your pick, the *Windows* forum or the *Mint* forum.

Er...

The installed Linux system is Ubuntu Mate. The live system I am using is the same.

---

### Post by oldfred on 2016-10-23
I think you missed most of my points. You may want to review the very end of the link in my signature that explains things like ESP which is the efi system partition that is required for all UEFI boots. Or the bios_grub partition which is required for Ubuntu to install in BIOS mode on a gpt partitioned drive.

Most of comments were to point out issues with your configuration which make it more complex. 
But bottom line is, you always need to boot in UEFI mode.

When you installed Windows server did you install it in UEFI or BIOS boot mode? It was not specifically shown in Boot-Repair's summary report. 
Does new Server work like desktop in that it always uses fast start up or always on hibernation. If hibernated then Linux cannot mount it or see it to add to grub or read files.

You said third drive, but sdc (third drive) is BIOS/MBR and shows only Linux partitions.
And sdd is also shown as BIOS/MBR with one NTFS partition, no boot flag nor boot data shown.

But also if not installed in same boot mode or if then BIOS, you cannot boot from grub, only from UEFI menu directly.
UEFI & BIOS are not compatible, once you start booting in one mode, you cannot switch to another mode. Or grub can only boot systems installed in same boot mode.
 Windows pretends to do that boot other modes, but actually reboots system back into UEFI and uses UEFI one time boot option to choose another boot.

---

### Post by infinitelink on 2016-10-23
Computer itself is set to UEFI but I'll disconnect the Windows Server disk and see what happens to start. 

I also found out that Windows since 8 has a hybrid-shutdown. It is created a hibernate file across systems to appear to start more quickly than it does. I found a way to force shutdown not to do that though, and then re-tried repair but no dice. x*D 

Will return and edit this after I've checked what happens when the server HD is disconnected. If things begin to work normally I'll have to figure-out more to find how to "install as UEFI" (I didn't really see any configuration during installation to choose either UEFI or BIOS).

[Edit 1: Okay, disconnected HD3 (which has Windows Server) and no change--still booted directly into Windows 8 rather than showing Grub2 menu.]

[Edit 2: 

Apologies, but here, 
> **oldfred said:**
> Most of comments were to point out issues with your configuration which make it more complex. 


is where I'm confused. e.g. I didn't change anything--I had a working Grub2 with both Windows 8.1 and Ubuntu Mate 16.04 before. I didn't install anything from a linux USB. I later did boot repair but when you boot from USB there are not options presented for choosing either UEFI or BIOS, and the computers "BIOS" settings are to boot only from UEFI. 

So I'm looking at this and going "why is this no longer working, even with HD3 + Windows Server disconnected?" 

Re-ran the repair tool again just to see. But no dice. I'm not sure what you mean by the set-up being complex though. ;( ]

[AH!...I should probably include this--current repair tool log: 

[https://docs.google.com/document/d/11pta8rDE3F7vlxTDENTMiIChtRxdauSkp1DXlN7i4T0/edit?usp=sharing](https://docs.google.com/document/d/11pta8rDE3F7vlxTDENTMiIChtRxdauSkp1DXlN7i4T0/edit?usp=sharing)

]

[Edit 4: 


> **oldfred said:**
> 
But also if not installed in same boot mode or if then BIOS, you cannot boot from grub, only from UEFI menu directly.

I was booting from Grub2 directly prior to this. And my installing Windows Server 2012 could not have touched Grub since the drives Grub was on were disconnected during the install.

[Edit 5: 

So I'm betting I confused something here. The HD with Server is disconnected but fdisk -l still shows sda, so now that means I have Grub2 on sda and on sdb. (I'm not sure, but I think prior to this with the other drive connected the sdb was showing as sdc on the live disk.) 

So basically, looks like two grubs, one with 1.98 (sdb) and one with 1.99 (sda). 
]

---

### Post by oldfred on 2016-10-23
With UEFI Windows will always reset UEFI so Windows is first in boot order even on updates. (new install of grub does also.)
So you have to reset grub/Ubuntu as first UEFI entry.

With BIOS Windows always installs a 100MB boot partition to drive set as default in BIOS, not sure now with UEFI and a BIOS install where it goes.
But some users installing Windows in BIOS to sdb, and grub was BIOS default in sda, had the first 100MB on sda totally reformatted to be the Windows boot partition. Typically destroying the Ubuntu install. Why we always suggest backups or disconnecting drives.

How you boot install media for both Windows & Ubuntu either UEFI or BIOS is then how it installs.
Windows in BIOS mode only makes drive MBR(msdos). Windows in UEFI mode only makes drive gpt partitioned.

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

UEFI is complex enough, but mixed UEFI and BIOS adds to complexity which I was trying to point out.

---

### Post by infinitelink on 2016-10-23
> **oldfred said:**
> 
UEFI is complex enough, but mixed UEFI and BIOS adds to complexity which I was trying to point out. 


Er...sorry. I'm just wondering how they're mixed/how you can tell/where you look in that report and figure that kind of thing out? 

> **oldfred said:**
> With UEFI Windows will always reset UEFI so Windows is first in boot order even on updates. (new install of grub does also.)
So you have to reset grub/Ubuntu as first UEFI entry.


Any ideas or resources on how one does this?

---

### Post by oldfred on 2016-10-23
First is gpt is standard with UEFI.
And MBR(msdos) is standard with BIOS.
But of course there are exceptions.
Windows only boots in UEFI mode from gpt.
Windows only boots in BIOS mode fro MBR.
And report shows sda2 as ESP with both Windows & Ubuntu UEFI boot files.
Your sdb & sdc show as dos or MBR.
And you show a BIOS install of grub in sda, but it says it cannot find core.img which is also required for BIOS boot to work. With MBR, it is right afer the MBR or first sector of drive, but with gpt you have to have a bios_grub partition for it to work.
Or sda is UEFI/gpt drive.

With Ubuntu all installs will put boot loaders into the ESP on sda. And even if second drive is MBR, and you repair in UEFI mode it will add Ubuntu/grub files to ESP on sda. That is not optimal, but some have posted that configuration.

You also show a BIOS grub in sdb, looking for an install in partition 3, but have no Linux partitions as partition 3 in any drive.
Your sdc is MBR, but has no boot loader.
But script is not showing any fstab, which would confirm your configuration. If efi partition mounted in definitely configured for UEFI. If commented out then originally UEFI and converted to BIOS. But with ubuntu entries in ESP, you have UEFI or had UEFI.

Script shows efibootmgr output:
       sudo efibootmgr -v  
See 
man efibootmgr
      
 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 2,1

---

