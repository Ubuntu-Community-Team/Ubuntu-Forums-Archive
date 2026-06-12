---
title: "restoring grub2 record on each drive of a raid 5 or 6 array"
date: 2013-08-26
forum: Server Platforms
---

### Post by PavelMan on 2013-08-26
After expanding a raid 6  mdadm array from 4 to 5 drives, with --add and --grow, and before any updates to grub were made, computer was restarted.
At boot, it now says something about an invalid arch independent ELF magic, and a grub rescue> prompt.

Since the raid hosts /, I wonder if the ability of grub to assemble the md0 to get to /boot is now compromised. I have no idea how does that part work...


What I have done, I booted from the "live usb" and have also found that as a part of my previous attempts to boot  from the raid, one drive fell out (sdc), and --assemble --scan was only using 3 drives, ending up in degraded array. I have probably accidentally unplugged the drive, when checking cables out of desperation ;-), but in any case - I have plugged the drive back in, and it was still not willing to join, complaining about superblock. 

Anyway, I have started the --manage --add, and it is resyncing now. When it  is done, I am not sure what to do... I will attempt the restart, but something tells me it will fail again.
Do I somehow need to fix the grub record first?

---

### Post by PavelMan on 2013-08-27
Well, as I was suspecting, it all has synced fine, but I now get this

error: invalid arch independent ELF magic.
grub rescue>

I am not sure why, but I have a gut feeling now, that the ASRock motherboard (I have 6 SATA connectors on it) may be funny, and the 5th drive is not visible at boot. Once the OS is loaded, some drivers kick in, and see that connector. So, you can add a drive, expand your raid, but at reboot - it will always fail... Is that possible? I have 9700/U3S3 model...

But even then, it must be possible to boot with degraded raid. There is this setting "bootdegraded=yes" somewhere, but I can not boot into the system. Besides, I think I have set it to "yes" on initial installation...
Anyway, any ideas on this will be highly appreciated.

---

### Post by PavelMan on 2013-08-27
I have found this one - no resolution there.  [http://ubuntuforums.org/showthread.php?t=1678352](http://ubuntuforums.org/showthread.php?t=1678352)
And in another place, I have seen that grub (starting version 1.99 or something) is capable of booting from raid. But then there must be some part of the record, that indicates which drives to use. Mine all have the "fd" tag, a Linux raid autodetect flag.

---

### Post by oldfred on 2013-08-27
I think the arch error is most often an incompatible version of grub2 trying to boot a different version of grub2. 

With RAID you install grub2's boot loader to the root of the RAID which is where it is booted from.

Someone posted this before.
> 
 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!



---

### Post by PavelMan on 2013-08-27
> **oldfred said:**
> I think the arch error is most often an incompatible version of grub2 trying to boot a different version of grub2. 

With RAID you install grub2's boot loader to the root of the RAID which is where it is booted from.

Someone posted this before.

This may be true in my case as well, as I suspect the bootloader needs to be updated with the new raid information. I do have /boot on the raid array, so grub needs to know how to assemble it. And, I suspect, that part should have been done separately... somehow... So, in a sense, I may have some "incompatibility". As for the port - I will look into that, but I am not sure what Asmedia ports are...

---

### Post by oldfred on 2013-08-27
Boot-Repair also works with RAID. It seems to know more about RAID than I do, but then anything does. :)

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by PavelMan on 2013-09-03
> **oldfred said:**
> Boot-Repair also works with RAID. It seems to know more about RAID than I do, but then anything does. :)

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks, I have done that, and here is the URL: [http://paste.ubuntu.com/6060799](http://paste.ubuntu.com/6060799)
I have booted from the USB drive, I have also had one 2TB (1.8) drive removed (it is suspicious, I think it has failed), but since I have raid6, the other 4 drives are supposed to do the trick. Plus, I have a 3TB external USB drive plugged in.

Any advice would be highly appreciated!

---

### Post by PavelMan on 2013-09-03
I have reviewed the result, and decided to remove the external drive to make it more readable. Plus, I want to mention, that sde is the flash drive I have booted from.
Also, I have noticed, that md0 did not mount. So I have mounted it manually by 

sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 , and since it complained about starting the array, I then have forced it with 
sudo mdadm --run 

Then I ran another boot-repair, and got this: [http://paste.ubuntu.com/6061265/](http://paste.ubuntu.com/6061265/)
Please, help.

---

### Post by oldfred on 2013-09-04
I see grub installed to the drives, but it needs to be install to md0 as I understand RAID. But there are so many different types of RAID and I do not understand differences.

Also Boot-Repair posted this:
> dmraid packages needed
User refused to install dmraid

I think in your RAID is is not the fakeRAID but just md0?

 For RAID reinstall from live-CD/DVD/USB
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

### Post by PavelMan on 2013-09-04
Then, I went to the /etc/initramfs-tools/conf.d/mdadm and have changed BOOT_DEGRADED from false to true. Then with the help of the "repair" part of boot-repair, I have reinstalled grub2, into sda,b,c,d.

---

### Post by PavelMan on 2013-09-04
> **oldfred said:**
> I see grub installed to the drives, but it needs to be install to md0 as I understand RAID. But there are so many different types of RAID and I do not understand differences.

I guess, I can do both, but it was installed into the MBR of those 4 disks, if I remember correctly. As if you install it inside the rais, then some oher boot loader will need to kick in first from sda or whatever your bios thinks is the boot device, and then assemble that raid and chainload the rest.

Boot-repair posted something aboutdmraid, because I have refused it's installation (agreed to uninstall it) after receiving a message, that it may conflict with mdraid. Since I've used mdadm to create this raid, I assumed I am using MDraid, and dmraid is not necerssary.

> I think in your RAID is is not the fakeRAID but just md0? 

I am not sure what you mean by this, but it feels like he answer is "yes". I just have a few drives, plugged into the motherboard, and mdadm does the rest.

I ran the test again keeping the dmraid, and this is what I've got: [http://paste.ubuntu.com/6061462/](http://paste.ubuntu.com/6061462/)
This time it all mounted fine by the test, and I can see the drive. I have restarted, but still get the grub rescue> prompt. I need to somehow make a degraded array to boot. Meanwhile, I have ordered another drive to replace the "suspected" failure. But I have this feeling, that something else is missing... as I should be able to boot with even one failed drive. The question is how to properly do it. It feels like some "chroot" is needed, and then some modifications to mdadm-cfg or grub, and then some grub-update or mdadm-reconfigure etc... But I do not know either procedure well enough, I gues...;-(.

---

### Post by oldfred on 2013-09-04
What little I know is mdadm is Linux software RAID, where the FakeRAID is a BIOS RAID. An advantage of mdadm is that you do not have to have the exact same hardware as replacement if you have a hardware (not drive) failure.

---

### Post by PavelMan on 2013-09-11
I suspect it was a combination of two problems - failed drive (do not know how that was supposed to matter for raid6) and, potentially, the filesystem, that was not expanded to the whole "volume" after the expansion of the array.

What I have done - I have installed a new drive, booted from live usb, partitioned the drive appropriatly, assembled the raid, added the drive and this has triggered the sync (this I have done before, no love). Then, I have done

sudo fsck.ext3 -f /dev/md0
sudo resize2fs /dev/md0

I believ no errors were found, although I was not really watching the output too closely...

Then, once again, I ran the boot-repair to install grub onto every drive. And it worked. So, it throws a funny message "no OS found" or so at the very beginning (could be an artifact of a "smart" bios, capable to launch a browser for your entertainment while the rest of the machine is booting, something like that, that I am not using anyway) but then quickly shows the grub menu, and proceeds to boot normally.

So, in a sense, I am back to "normal". But, I have tried to unplug one of those drives again, and reboot ;-). And it does not boot again ;-). And I had to go though the familiar procedure again, minus the growth of the fs. And it works again. I think even without the boot-rescue.

This makes me semi-happy, but only semi. I have a "working procedure" in hand to undig myself in case of a failure, but it is very frustrating to have a raid6, and not being able to boot with one failed drive...

---

### Post by Entilza on 2013-09-19
This sounds like a horror story :)  Have you considered reinstalling from scratch and just restoring everything?

---

### Post by PavelMan on 2013-09-20
Once I have booted from a live CD and mounted a degraded array, the uncomfortable part was over. The rest - just exploration and satisfying the curiosity. But I do not see how reinstalling will change anything. It all works now too. The trick is to make sure it survives the reboot with a failed drive... This is what I can not understand why isn't it working. Given that I did set bootdegraded=yes...

---

### Post by Entilza on 2013-09-23
No exactly, I wouldn't let it rest if it doesn't boot with a degraded drive.. That's the whole point!  Something if obviously wrong with /boot among all 3.

---

