---
title: "Boot directly into diffrent Windows versions using GRUB"
date: 2022-09-06
forum: Windows
---

### Post by robin-m-brack on 2022-09-06
Hi

To start off, sorry if I'm posting in the wrong thread/forum. If so, please guide me to where I should post.

I have a system consisting of:
Windows 11
Windows 10 (for testing)
Ubuntu 22.04 (for testing)
Ubuntu 22.04 (daily use)

What I would like is for GRUB to find my different Windows OS, instead I only see Windows Boot Manager.

How can I boot directly into a specific Windows installation?

Regards

---

### Post by oldfred on 2022-09-06
Are these UEFI?or Old BIOS? You cannot mix boot modes.
Are they all one one drive? Lot easier if multiple drives.

Windows dual boots from BCD.
Grub dual boots from grub menu. Os-prober finds other installs, but grub 2.06 now wants to turn os-prober off. Which in your case will be better anyway. You want to copy boot stanza into 40_custom.
Grub will boot working Windows, but fast start up also must be off.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

Post this for specific suggestions, if desired.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Grub/os-prober so not know ESP - efi system partition. UEFI systems install boot loaders into ESP for UEFI booting.
With two Windows, you have to create another FAT32 and move esp,boot flags to it, so Windows boot files for second install are in that ESP. Then move boot flag back to main ESP. You then have one real ESP, and another FAT32 with Windows boot files that grub can use to boot second Windows.
You may have to modify UEFI descriptions with new/changed entries using efibootmgr. See
man efibootmgr

---

### Post by robin-m-brack on 2022-09-09
Hi
Thanks for the reply


All os are on the same drive. All os are UEFI


The problem is not the bootscreen, but grub itself, as it will not find my two diffrent windows installations, only Windows Boot manager
If I try to point it to the right partition, it can't load at all

Pastebin link:
[https://paste.ubuntu.com/p/grTGjfCvqj/](https://paste.ubuntu.com/p/grTGjfCvqj/)

Regards

---

### Post by oldfred on 2022-09-09
Grub cannot see into BCD, to find a second install of Windows.
The work around is to create a new FAT32 partition, move esp,boot flags to it, and install or do Windows boot repair (not Boot-Repair which is for Linux only) of Windows so second FAT32 partition has Windows boot files. Move esp,boot flags back to first FAT32 to boot default Windows & Ubuntu from UEFI.
But now grub can find second install's boot files in second FAT32. Your os-prober may find that or you just create new entry in 40_custom to boot using the efi files in that second partition. You may want to edit descriptions as shown in links above.

you have installed grub customizer which complicates tings. It seems to be ok for minor changes, but for anyone wanting customized grub, better to learn a bit about grub and edit grub files configurate files & 40_custom directly.
From some other posts it looks like it is very difficult to uninstall grub-customizer as it replaces the standard grub file with its own proxy files. It becomes both uninstall & then erase files. And when grub files are erased, system is not bootable. And then a total new install of grub to restore defaults.

---

### Post by coffeecat on 2022-09-10
> **robin-m-brack said:**
> 
To start off, sorry if I'm posting in the wrong thread/forum.

No problem. Yours in an unusual request that doesn't really fit neatly into any of our categories. The [Documentation and Community Wiki Discussions](https://ubuntuforums.org/forumdisplay.php?f=428) sub-forum where you initially posted is for discussion about wiki pages, not for technical support. Yours is not an Ubuntu question, so I've moved this thread into the Windows sub-forum, this probably being the best fit.

Good luck in finding a solution, and welcome to the forum.

---

### Post by yancek on 2022-09-10
>  The problem is not the bootscreen, but grub itself, as it will not find  my two diffrent windows installations, only Windows Boot manager 

That's the way the windows bootloader works.  If you install a second windows (Legacy or EFI) it will overwrite the boot files of the first install and create an entry for the first windows install in the BCD bootloader of the second install.  Grub doesn't directly boot windows but chainloads it as you can see if you look at the grub.cfg entry for windows.  This entry points to the bootmgfw.efi file and you will only have one if the EFI partition so you would need to go through a rather convoluted process described by oldfred above.

---

### Post by robin-m-brack on 2022-09-12
Thank you everyone for the replies.

Since I work as a teacher, it sounds like something I should tinker with during the holidays :) It's not a big problem, more of a "comfort-issiue". But again, thanks for all the help

//regads

---

### Post by ivan275 on 2023-03-12
> **oldfred said:**
> Grub cannot see into BCD, to find a second install of Windows.
The work around is to create a new FAT32 partition, move esp,boot flags to it, and install or do Windows boot repair (not Boot-Repair which is for Linux only) of Windows so second FAT32 partition has Windows boot files. Move esp,boot flags back to first FAT32 to boot default Windows & Ubuntu from UEFI.
But now grub can find second install's boot files in second FAT32. Your os-prober may find that or you just create new entry in 40_custom to boot using the efi files in that second partition. You may want to edit descriptions as shown in links above.

you have installed grub customizer which complicates tings. It seems to be ok for minor changes, but for anyone wanting customized grub, better to learn a bit about grub and edit grub files configurate files & 40_custom directly.
From some other posts it looks like it is very difficult to uninstall grub-customizer as it replaces the standard grub file with its own proxy files. It becomes both uninstall & then erase files. And when grub files are erased, system is not bootable. And then a total new install of grub to restore defaults.

Not sure if I should start a new topic or just tag onto this one. I'm in a very similar boat wanting to directly boot into 2 windows versions... Laptop, 1 hard drive, GPT, Secure Boot off, EFI...

hd0,gpt1 NTFS Recovery
hd0,gpt2 FAT32 System (EFI Partition)  \EFI\ubuntu\shimx64.efi and \EFI\Microsoft\Boot\bootmgfw.efi
hd0,gpt3 Unknown 16MB
hd0,gpt4 NTFS C:Windows 10
hd0,gpt5 NTFS D:Windows 10
hd0,gpt6 Ext4 Ubuntu
hd0,gpt7 Ext4 100MB I want to say I made it for Ubuntu bootloader but I didn't know what I was doing.
hd0,gpt8 500MB Recovery Partition

I spent 2 weeks so far trying to get this to work, many many hours, fallowed multiple guides, killed grub a few times, killed windows bootloader twice, killed the 2nd windows bootloader entry a few times, reinstalled gpt5 and gpt6 3 times, tried to get 4 other bootloaders to do this all without success. 

Could you walk me through this step by step as if I was five?

---

### Post by oldfred on 2023-03-12
Convert hd0,gpt7 to FAT32 and move boot,esp flags to it from gpt2. You can use gparted or Windows tools.
Then with Windows repair flash drive /repair/reinstall Windows boot files for second install.
It should put boot files into gpt7.
Then move boot,esp flags back to gpt2.
Grub's os-prober should then find & add those boot files in gpt7 to grub menu.
I prefer to then manually copy that boot stanza into 40_custom & turn off os-prober.

Dual boot two Windows UEFI from grub, two efi partitions.
[http://askubuntu.com/questions/653101/boot-repair-windows-not-listed](http://askubuntu.com/questions/653101/boot-repair-windows-not-listed)

If you want more specific help, better to start your own thread.

[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by ivan275 on 2023-03-13
Thanks, worked perfectly

---

### Post by oldfred on 2023-03-13
Part of reason I prefer to copy grub's boot stanza's into 40 custom is that I can edit descriptions.

I also have a lot of old installs, mostly Ubuntu and do not want those in my grub menu. With os-prober off, the update to grub with each kernel & major update is a lot quicker without os-prober running thru every partition.

---

