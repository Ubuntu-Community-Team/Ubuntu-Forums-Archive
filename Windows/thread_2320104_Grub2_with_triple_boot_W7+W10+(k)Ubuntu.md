---
title: "Grub2 with triple boot W7+W10+(k)Ubuntu"
date: 2016-04-10
forum: Windows
---

### Post by bartgrefte on 2016-04-10
A while ago I installed Kubuntu next to W7 on my laptop and Grub2 detected W7 without any issues.
Recently I added W10 to the dual boot and that's where it gets a little weird.

First of, the not weird part: the W10 installer got rid of Grub2, I was expecting that. I solved this by booting into a Kubuntu live environment, mounting the Kubuntu partition and then reinstall Grub2, followed by running update-grub.

After running update-grub I was expecting both W7 and W10 to appear in Grub2, but that wasn't the case. Instead of Kubuntu and an entry for W7 (like it was before), it now contains an entry for Kubuntu and one for W10, not W7.

After selecting W10 in Grub2 and waiting for a short time (the W10 OS-selection menu takes some time to load apparently), I get the W10 OS-selection menu that displays W10 and W7. Selecting W10 boots directly to W10, but selecting W7 causes a reset of my laptop after which I have to select W10 in Grub2 again and then it immediately starts W7, skipping the W10 OS-selection menu.
After I shutdown or reboot W7 and select W10 again in Grub, the W10 OS-selection menu appears again.

My questions are:
- Is there any way to start W10 and 7 directly from Grub2 or is the W10 OS-selection menu in the way?
- Can someone explain why a reset is required and a second selection of W10 in Grub2 before W7 starts? Not sure if this is a Linux-related issue or Windows though...

---

### Post by oldfred on 2016-04-10
If BIOS Windows only boots from one primary NTFS partition with boot flag. Not sure with UEFI.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

If both Windows are BIOS and on primary partitions you can move boot flag & run repairs, so both installs have bootmgr & BCD. Then grub can find both. If UEFI not sure if there is a way to separate them or not.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by yancek on 2016-04-10
If you are using MBR to boot and windows 7 is on a primary partition and windows 10 on a logical, then the windows 10 installer would have put  it's boot files on the windows 7 partition and overwritten the 7 files.   If that's the case, there isn't  anything you can do about it.  Maybe contact microsoft for a solution if there is one. I doubt it would matter much if they are both on primary partitions as only one can be marked active/bootable.  There is probably something wrong on one of the windows systems as you should be able to select windows 7 from the 10 boot menu and boot it.

Since Ubuntu and Grub are not involved in this problem and it is simply the windows dual-boot problem, you might have better luck at a windows forum.  Posting the output of boot repair would be the first step here, maybe someone will have a solution.

---

### Post by bartgrefte on 2016-04-11
> **oldfred said:**
> If BIOS Windows only boots from one primary NTFS partition with boot flag. Not sure with UEFI.
My laptop has a BIOS, not UEFI....As far as I know. Now that I think of it, I'm not entirely sure, would have to check. It's a Lenovo G780 series laptop. To make things a little complicated, it is running a modified BIOS. The damn thing had a whitelist for wifi-cards build into it, it no longer does now:)

After checking the BIOS, I do see "UEFI Boot" enabled, but that's the only UEFI reference I see. It looks like plain old BIOS and I never did a UEFI-install, I don't even think I ever saw an option for that.
At the main screen, it says BIOS version, not UEFI version, how confusing since there is a reference to UEFI...

> **oldfred said:**
>  But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 
While figuring out the best way to restore Grub2 (before I did that manually), I ran into Boot-Repair. Kept getting "Unable to locate package boot-repair" in Kubuntu 15.10, and yes, I added the repository and did an apt-get update. Got the Boot-Repair disk now: [https://paste.ubuntu.com/15756043/](https://paste.ubuntu.com/15756043/)

> **oldfred said:**
> If both Windows are BIOS and on primary partitions you can move boot flag & run repairs, so both installs have bootmgr & BCD. Then grub can find both. If UEFI not sure if there is a way to separate them or not.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

> **yancek said:**
> If you are using MBR to boot and windows 7 is on a primary partition and windows 10 on a logical, then the windows 10 installer would have put  it's boot files on the windows 7 partition and overwritten the 7 files.   If that's the case, there isn't  anything you can do about it.  Maybe contact microsoft for a solution if there is one. I doubt it would matter much if they are both on primary partitions as only one can be marked active/bootable.  There is probably something wrong on one of the windows systems as you should be able to select windows 7 from the 10 boot menu and boot it.

Since Ubuntu and Grub are not involved in this problem and it is simply the windows dual-boot problem, you might have better luck at a windows forum.  Posting the output of boot repair would be the first step here, maybe someone will have a solution.
Both W7 and W10 are installed on primary partitions, see the link above.

So this is not a Linux but a Windows problem?

---

### Post by oldfred on 2016-04-11
Moved to Windows sub-forum.

You do have BIOS install. And both Windows are in primary partitions.
And as most newer Windows you do have a separate Boot partition sda1 that has bootmgr & BCD.
But Windows does not have to have a separate Boot partition.
Grub looks for bootmgr & BCD where Windows looks for boot flag.

So you may be able to copy both bootmgr & /boot/BCD to both installs. Probably have to or want to edit BCD to just boot that one install.
You may need each installs Windows repair disk. But must move boot flag to that install before you repair or try to directly boot from MBR.
You can use Windows repair disk or Boot-Repair to restore Windows boot to MBR to test  install, and move boot flag to test other.

Grub only boots working Windows. So once both Windows boot, use boot Repair to restore  grub to MBR. and run this to find both:
sudo update-grub

---

### Post by bartgrefte on 2016-04-11
> **oldfred said:**
> Moved to Windows sub-forum.Thanks :)

Well, after Googling some more, it looks like I have found the solution. I just executed **bcdboot c:\windows /s c:** in an elevated command prompt on W10, then rebooted to Kubuntu and executed **sudo update-grub**. Now I've got two W10 options in Grub, one on the 1st (small system) partition and one on the W10 partition. Then I executed **bcdboot c:\windows /s c:** in W7 and ran **sudo update-grub** again. 

Now I've got (as far as Windows is concerned) 3 options in Grub:
Windows 10 loader (/dev/sda1) -> W7/W10 dualboot menu
Windows 7 loader (/dev/sda2) -> boots W7 directly
Windows 10 loader (/dev/sda3) -> boots W10 directly

The 1st one is stored on the system partition, not sure how to get rid of that one. So I thought I'd just remove that one from menu.lst, but that's no longer possible since I'm using Grub2....

edit: Any comments about this workaround? [https://www.linuxquestions.org/questions/linux-software-2/grub2-skipping-one-partition-from-os-detection-741100/#post3792729](https://www.linuxquestions.org/questions/linux-software-2/grub2-skipping-one-partition-from-os-detection-741100/#post3792729) ?

---

### Post by oldfred on 2016-04-11
I do not like editing grub's scripts which often change with grub version.

I just copy boot stanza to 40_custom for whatever you want.
Once you know that works, turn off os-prober so it does not search for any other installs. It will still update for new kernels.
And you can turn on os-prober again, if needed.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[URL="http://ubuntuforums.org/showthread.php?t=2076205"]http://ubuntuforums.org/showthread.php?t=2076205
[/URL] 
My saved instructions usually use gksudo gedit, but now they do not like gksudo. So am updating to use sudo nano as editor. Use whatever editor you prefer.


 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
or:
sudo nano /etc/grub.d/40_custom
Then do:
sudo update-grub 

   sudo nano /etc/default/grub
#Add this line:
GRUB_DISABLE_OS_PROBER=true
sudo update-grub

---

### Post by bartgrefte on 2016-04-17
I managed to get rid of the 2nd W10 entry without messing around with Grub. Since I already ran commands to create bootfiles on both of the Windows partitions, the 100MB system partition (which contained the W7/W10 dual boot menu) wasn't necessary anymore.

So I deleted that partition, ran sudo update-grub, problem solved :)

If I ever need the recovery stuff that was on there, I just get my Zalman VE-300 which contains a bunch of iso's that can help with that.

---

