---
title: "Lost Win7 boot after installing UBUNTU Vivid"
date: 2015-01-30
forum: Ubuntu Development Version
---

### Post by akkosh-heckal on 2015-01-30
I have a dual boot system (Win7 for my company) and (UBUNTU 14.10) .. My company is using Encryption for the image of Win7.
After Win7 installation i installed UBUNTU 14.10 and i was able to boot both.
My HDD is partitioned as follows:
3 Primary partitions (c: for windows , D: , E: for data ) and 5 Logical partitions (3 data and 1 for Ubuntu and 1 for swap).

Firstly, (N.B. Problem_1) I noticed that from Ubuntu i'm unable to mount any of the primary partitions, but i can normally mount the other logical ones.

Secondly, (N.B. Problem_2) I decided to test Ubuntu Vivid 15.04 so i installed it on one of the logical partitions.
After the installation i lost the Windows totally and i'm unable to boot to it, and from both Ubuntu versions, i'm unable to mount the primary partitions.
I used Boot Repair software on both Ubuntu versions, but none of them detected the Windows.

During boot of Ubuntu Vivid, it shows error (TPM error) and I understood that it is related to TPM Chip that is implemented for the security on Bios, i logged in to BIOS and disabled TPM option then the error disappeared.

I'm currently unable to boot from windows as it is not seen by Grub. And unable to mount the NTFS partition for windows.

If i understand well, this could be related to the security option done by the company that is preventing accessing the primary partition if the HDD is used outside the laptop, but at least i should be able to mount it even as Read-only or to boot from it in parallel with other OSs especially that it was working before and that i also disabled TPM.

Can anyone explain to me how to mount windows7 partition or to get its boot option back ?

---

### Post by Frogs Hair on 2015-01-30
Moved to ***Ubuntu Development Version***

---

### Post by kansasnoob on 2015-01-30
Use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") again but this time only click on the Create Boot Summary and then post the URL to the boot info.

---

### Post by akkosh-heckal on 2015-01-30
this is the link 
[http://paste.ubuntu.com/9966962/](http://paste.ubuntu.com/9966962/)

I performed the test from UBUNTU 14.10
Note: sda1 should be Win7 Boot

Thanks

---

### Post by grahammechanical on 2015-01-30
As a simple test load into Ubuntu 14.10 and run this command

```
sudo update-grub
```

In the printout does it list the Windows 7 bootloader? If it does then run

```
sudo grub-install /dev/sda
```

But my feeling is that Grub os-prober will not detect the Windows 7 bootloader. The Grub boot menu configuration files in 14.10 and 15.04 do not have a record for Windows 7 bootloader. And the Boot Repair report says this:

> 1 disks with OS, 2 OS : 2 Linux, 0 MacOS, 0 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.

This is the problem that Boot Repair is meeting

> NTFS signature is missing.
Failed to mount [COLOR=#BB4444]'/dev/sda1'[/COLOR]: Invalid argument
The device [COLOR=#BB4444]'/dev/sda1'[/COLOR] doesn[COLOR=#BB4444]'t seem to have a valid NTFS.[/COLOR]
[COLOR=#BB4444]Maybe the wrong device is used? Or the whole disk instead of a[/COLOR]
[COLOR=#BB4444]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]
[COLOR=#BB4444]mount /dev/sda1 : Error code 12[/COLOR]
[COLOR=#BB4444]mount -r /dev/sda1 /mnt/boot-sav/sda1[/COLOR]
[COLOR=#BB4444]NTFS signature is missing.[/COLOR]
[COLOR=#BB4444]Failed to mount '[/COLOR]/dev/sda1[COLOR=#BB4444]': Invalid argument[/COLOR]
[COLOR=#BB4444]The device '[/COLOR]/dev/sda1[COLOR=#BB4444]' doesn'[/COLOR]t seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition [COLOR=#666666]([/COLOR]e.g. /dev/sda, not /dev/sda1[COLOR=#666666])[/COLOR]? Or the other way around?
mount -r /dev/sda1 : Error code 12

Boot Repair cannot mount those NTFS partitions. It cannot read them to identify a Windows 7 bootloader.

What to do about it? I have no idea. It seems illogical that this problem should happen when installing Vivid Vervet but not when you installed 14.10. What is being done differently? Has the Windows boot partition been encrypted since you installed 14.10?

Regards.

---

### Post by kansasnoob on 2015-01-30
I don't know enough about UEFI to know for sure but I see that you actually have 5 windows partitions; sda1and sda2 both show unknown, then sda3, sda5, and sda7 all show some relation to NTFS.

And both sda5 and sda7 say "According to the info in the boot sector they start at sector 2048". Clearly two partitions can't both start in the same place.

I sort of wonder if Windows didn't install in GPT mode and maybe the last Ubuntu install converted the drive to MSDOS. I'm just not sure but it appears to be a real mess.

---

### Post by zika on 2015-01-31
Tough job for SW:```
[COLOR=#000000]Partition  Boot  Start Sector    End Sector  [/COLOR][COLOR=#008800]*# of Sectors  Id System*[/COLOR]
/dev/sda1    *          2,048   123,654,143   123,652,096   7 NTFS / exFAT / HPFS
/dev/sda2         123,654,144   328,454,143   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda3         328,454,144   533,254,143   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda4         [COLOR=#ff0000]533,256,190   976,771,071[/COLOR]   443,514,882   f W95 Extended [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]
/dev/sda5         [COLOR=#0000cd]533,256,192   738,056,191[/COLOR]   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda6         [COLOR=#ee82ee]738,058,240   805,642,224[/COLOR]    67,583,985  83 Linux
/dev/sda7         [COLOR=#ee82ee]805,644,288   881,420,287 [/COLOR]   75,776,000   7 NTFS / exFAT / HPFS
/dev/sda8         [COLOR=#ee82ee]881,422,336   961,294,335[/COLOR]    79,872,000  83 Linux
/dev/sda9         [COLOR=#ee82ee]961,296,384   976,771,071[/COLOR]    15,474,688  82 Linux swap / Solaris


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1                                                          
/dev/sda2                                                          
/dev/sda3                                                          
/dev/sda5        027A19BC7A19AE03                       ntfs       New Volume
/dev/sda6        2e5e286d-dc16-4d9b-9af8-a6bb19490ee4   ext4       
/dev/sda7        D446632246630498                       ntfs       New Volume
/dev/sda8        97aaa560-e3b3-42ff-a6ca-cdc4ee239bca   ext4       
/dev/sda9        02b2af0d-b7b8-4078-acaf-3db8a8d9f3c7   [COLOR=#B8860B]swap[/COLOR] 
```This install shoud be preserved and studied gaining a new and better Grub for us... ;)

---

### Post by ventrical on 2015-01-31
> **akkosh-heckal said:**
> I have a dual boot system (Win7 for my company) and (UBUNTU 14.10) .. My company is using Encryption for the image of Win7.
After Win7 installation i installed UBUNTU 14.10 and i was able to boot both.
My HDD is partitioned as follows:
3 Primary partitions (c: for windows , D: , E: for data ) and 5 Logical partitions (3 data and 1 for Ubuntu and 1 for swap).

Firstly, (N.B. Problem_1) I noticed that from Ubuntu i'm unable to mount any of the primary partitions, but i can normally mount the other logical ones.

Secondly, (N.B. Problem_2) I decided to test Ubuntu Vivid 15.04 so i installed it on one of the logical partitions.
After the installation i lost the Windows totally and i'm unable to boot to it, and from both Ubuntu versions, i'm unable to mount the primary partitions.
I used Boot Repair software on both Ubuntu versions, but none of them detected the Windows.

During boot of Ubuntu Vivid, it shows error (TPM error) and I understood that it is related to TPM Chip that is implemented for the security on Bios, i logged in to BIOS and disabled TPM option then the error disappeared.



From what I understand , once the TPM is cleared (disabled) you will not be able to access any info in that partition (Windows 7 Bootloader) because all the keys are wiped.

But it appears that there is still hope.  Often times  (with dual boot / ubuntu/Win7) I will have to use GRuB rescue (not super grub rescue). GRuB rescue is an .iso file that can be burned to  CD using unetbootin.

  Unfortunately I cannot find the original Grub Rescue so you may have to use this:


[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/)

Regards..

---

### Post by akkosh-heckal on 2015-01-31
> **grahammechanical said:**
> 

Boot Repair cannot mount those NTFS partitions. It cannot read them to identify a Windows 7 bootloader.

What to do about it? I have no idea. It seems illogical that this problem should happen when installing Vivid Vervet but not when you installed 14.10. What is being done differently? Has the Windows boot partition been encrypted since you installed 14.10?

Regards.


Thanks for your reply.
The TPM error appeared only when i login to UBUNTU vivid and when i was trying to login using UBUNTU 14.10 there was no error but also i was unable to mount the first 3 sda.
The only thing that could make sense, is that when the new kernel installed it tried to check something on the security chip which triggered the encryption and as a result it detected that the someone trying to access HDD data outside Corporate windows, so that it disabled it :p maybe i watch so much spying movies .. but i'm totally lost here :p

---

### Post by akkosh-heckal on 2015-01-31
Thanks so much    [[COLOR=#000000]kansasnoob[/COLOR]]("http://ubuntuforums.org/member.php?u=554595")[COLOR=#000000]    [/COLOR]for your reply. but i don't know which part mentioned that both start at the same sector ?

---

### Post by akkosh-heckal on 2015-01-31
> **zika said:**
> 

Tough job for SW
This install shoud be preserved and studied gaining a new and better Grub for us... ;)

Thanks so much for your reply .. 

I don't know why this fails .. i had a similar configuration on my old PC but as i remember the image used by the company was different, i think the usage of the Encryption mechanism is brand new, that's is why i'm trying to find the relation between both.

Earlier, i had Win7, then divided the HDD to 9 partitons, i do all partitioning from Windows that's is why they are all NTFS to keep all Data partitions accessible from all OSs
Then i installed UBUNTU 13.04 on one partition , and UBUNTU 14.10 on another .. 
At this point there were no problem at all and all partitions were working and accessible .. 

The only change this time is
Win7 new image with encryption
Ubuntu Vivid 

Which one is the root cause :p i dont know

---

### Post by akkosh-heckal on 2015-01-31
> **ventrical said:**
> From what I understand , once the TPM is cleared (disabled) you will not be able to access any info in that partition (Windows 7 Bootloader) because all the keys are wiped.

But it appears that there is still hope.  Often times  (with dual boot / ubuntu/Win7) I will have to use GRuB rescue (not super grub rescue). GRuB rescue is an .iso file that can be burned to  CD using unetbootin.

  Unfortunately I cannot find the original Grub Rescue so you may have to use this:


[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/)

Regards..



Thanks so much for your reply .. i will check your suggestion and post the updates ..

But do you think i should return the TPM option back before Grub initiallization ?

---

### Post by ventrical on 2015-01-31
> **akkosh-heckal said:**
> Thanks so much for your reply .. i will check your suggestion and post the updates ..

But do you think i should return the TPM option back before Grub initiallization ?

Required reading:

[http://www.trustedcomputinggroup.org/media_room/news/340](http://www.trustedcomputinggroup.org/media_room/news/340)


  I can only state my opinion.  Restore  or <enable> your TPM as it was previously. I have not had any problem boot from UEFI shell <secure-mode> with Win 8 selected first but  if GRuB is slected as the first option then the efi-shim will be needed , unless they have fixed that.  Windows 7 has not required any special maintanance. The Grub-Rescue disk should restore it. You do NOT want to install GRuB. You want to restore it.. so you would choose that option when presented. Just wait and be patient with the process. It takes a little time to finish - I am just warning that if you choose to install GRuB from GRuB rescue you could loose your Windows 7.

---

### Post by ventrical on 2015-01-31
Grub Rescue should be able to restore this:

```

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu Vivid Vervet (development branch) 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        


```

---

### Post by akkosh-heckal on 2015-01-31
> **ventrical said:**
> 

Required reading:

[http://www.trustedcomputinggroup.org/media_room/news/340](http://www.trustedcomputinggroup.org/media_room/news/340)


  I can only state my opinion.  Restore  or <enable> your TPM as it was previously. I have not had any problem boot from UEFI shell <secure-mode> with Win 8 selected first but  if GRuB is slected as the first option then the efi-shim will be needed , unless they have fixed that.  Windows 7 has not required any special maintanance. The Grub-Rescue disk should restore it. You do NOT want to install GRuB. You want to restore it.. so you would choose that option when presented. Just wait and be patient with the process. It takes a little time to finish - I am just warning that if you choose to install GRuB from GRuB rescue you could loose your Windows 7.


I've read the article, it is very useful. Thanks.

But i still unable to understand which action i made initiated the problem .. 

Actually, (luckily) i have no fears of losing windows as i have a restore image .. but my concern is that i don't understand where the problem is, as this is the second time in one week to lose windows after ubuntu installation with this image of win7.

I tried the rescue disk (i didnt understand all the options but i used them all) and it was not able to retrieve the windows boot even after the selection of mounting encrypted partitions.

I think if i couldnt find a solution, in few hours, i will restore the old image again and try to partition and install UBUNTU vivid directly to see what is gonna happen.

---

### Post by ventrical on 2015-01-31
This is a currently hot topic with UEFI systems.  I just check one of my PCs and it has TPM capable but dos not have the insertable chip module-chip to go with it. I had sent my other UEFI system with TPM out to another tester. I think I have 2 left.

```

But i still unable to understand which action i made initiated the problem .. 


```

  I do not think it is anything you did. There are dozens of threads  here on this topic. If I find anything I'll drop in. 

Are you saying you tried the Grub Rescue CD?

Regards..

---

### Post by ventrical on 2015-01-31
> **akkosh-heckal said:**
> I've read the article, it is very useful. Thanks.

But i still unable to understand which action i made initiated the problem .. 

Actually, (luckily) i have no fears of losing windows as i have a restore image .. but my concern is that i don't understand where the problem is, as this is the second time in one week to lose windows after ubuntu installation with this image of win7.

I tried the rescue disk (i didnt understand all the options but i used them all) and it was not able to retrieve the windows boot even after the selection of mounting encrypted partitions.

I think if i couldnt find a solution, in few hours, i will restore the old image again and try to partition and install UBUNTU vivid directly to see what is gonna happen.


see zika's post again
[http://ubuntuforums.org/showthread.php?t=2263283&p=13219132#post13219132](http://ubuntuforums.org/showthread.php?t=2263283&p=13219132#post13219132)

 and perhaps wait and see if we can come up with somthing..

---

### Post by ventrical on 2015-01-31
Do you have your UEFI enabled or disabled in BIOS?

---

### Post by ventrical on 2015-01-31
> **akkosh-heckal said:**
> I have a dual boot system (Win7 for my company) and (UBUNTU 14.10) .. My company is using Encryption for the image of Win7.


So in what manner are they encrypting it! Is it the image on the DVD iself that is encrypted or do you have to have the TPM enabled during setup?

---

### Post by akkosh-heckal on 2015-01-31
> **ventrical said:**
> 

  I do not think it is anything you did. There are dozens of threads  here on this topic. If I find anything I'll drop in. 

Are you saying you tried the Grub Rescue CD?

Regards..


I tried the Grub Rescue ISO on USB and it didn't help much .. it was not able to detect the C: partition at all .. only detected both UBUNTU versions

---

### Post by akkosh-heckal on 2015-01-31
> **ventrical said:**
> So in what manner are they encrypting it! Is it the image on the DVD iself that is encrypted or do you have to have the TPM enabled during setup?

Actually i don't know what is the encryption mechanism they are using, i just discovered all that when the problem occurred.

Unfortunately, Tomorrow is a working day and i had to restore the image of windows to be able to work tomorrow :p
So that now i formatted all the HDD partitions into only one to be able to restore the image .. and now windows is working normally.

I will install tomorrow UBUNTU vivid and then UBUNTU 14.10 to check what will happen.

I didn't check the UEFI earlier, but i found on BIOS before the restore  that the Boot mode is set to "Legacy"

Only one thing i'm afraid to apply, is to clear TPM value.
I tried to restore BIOS to factory, but at the end it asked to clear TPM value and i selected "NO" as i'm afraid that this could prevent me accessing windows anymore.

I'm quit sure that the problem will reoccur, so that i will keep you updated, and if you need to try anything before i install UBUNTU, please let me know.

Thanks so much for your concern

---

### Post by akkosh-heckal on 2015-01-31
I think also it is important to mention that, i just remembered, before the installation of Vivid i performed disk Check on the surface of the C: partition as i had doubts of Bad Sectors (result was clear OK), but i performed the same check on another partition which appeared and mountd normally in Linux.

I say that because i noticed that when i performed the check on one partition, then i interrupted it, when i logged in to Linux i was not able to mount that partition unless i reformatted the partition from Linux.

---

### Post by oldfred on 2015-02-01
You are not showing any of the normal efi partitions, so I do not think any of the issues are UEFI related. But if system also boots in UEFI mode, be sure to have it set for Legacy/BIOS/CSM and do not boot anything in UEFI mode.

I do think issues are related to Windows encryption. The few systems we have seen also have to have absolute control over MBR and installing grub breaks encryption or rebooting into Windows auto restores the encrypted MBR. Boot-Repair restores a Windows 'like' standard boot, syslinux but most encrypted systems take over both MBR and partition's boot sector or PBR with proprietary code.

Most companies that want encryption and really good security also lock out BIOS/UEFI, so users cannot modify system and potentially compromise the secure system.
And if Windows is encrypted, you cannot access that from Linux. There are not compatible systems. And as such you should not be able to access the encrypted partition.

One user was able to access BIOS and just installed grub boot loader to a flash drive. He did have access to BIOS and then could boot Ubuntu if booting flash drive, but default system boot was still Windows from MBR.

---

### Post by akkosh-heckal on 2015-02-01
Latest update:

I restored Win7 Image, Kept TPM value as it is in BIOS, Partitioned HDD to 3 primary + 5 Logical partitions, installed UBUNTU 14.10 
after that, i found that i'm able to mount all the partitions from Ubuntu even Win7 partition !!!

What i don't understand here is that: if the partition is encrypted, why i was able to mount Win7 partition and also what is the usage of encryption if i'm able to mount it using UBUNTU ISO over USB ??


Next will be:
- install Ubuntu Vivid 
- Scan/check Disk for three partitions (Win7 + any primary + any logical) and check if all will be mounted normally

---

### Post by akkosh-heckal on 2015-02-06
I disabled TPM from BIOS and then i installed both UBUNTU versions (14.10 and Vivid) and i was able to mount Win7 partition on both UBUNTU versions.

It seems that the security module (TPM) has encrypted the partition during the boot of UBUNTU and that's why i was unable to mount it after installation of both versions.

I still don't fully understand the case, i don't understand how the problem was initiated .. but this is my suspection about the present scenario.

Thanks for all who were interested, and who helped me ..  i will try to reproduce the problem again and if i understood anything i will try to keep you posted.

---

