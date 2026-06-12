---
title: "Server doesn't reboot after restore"
date: 2017-01-19
forum: Server Platforms
---

### Post by Mike_Hughes on 2017-01-19
I am running a Ubuntu 14.04 LTS  web Server tuning Wordpress. I have a plugin that managed Sermon files I put on it I had modified. An update came in for the plugin. Once I updated the plugin I lost my modes. I thought a simple solution would be to restore the server with my backup clone I had made using HD clone 5. 
Now that I restored the Server will not boot. It presents a Grub loader with three choices, none of which boot the Server. The choices I have are Ubuntu, which does nothing but set there. Th other two choices read loading RAM disk and never loads. Any suggestions on how to solve this problem? I don't won't to have to rebuild the server. Is there any way I might be able to run Ubuntu from a CD and repair the boot record? I live in Springhill, LA now.

---

### Post by darkod on 2017-01-20
I guess a clone should have restored grub correctly too, but the first thing I would try is booting the server in live mode (if possible) and reinstall grub on the MBR of the disk.
Now with UEFI boot around, it might make a difference whether you are using legacy boot or uefi boot. I work more with legacy and haven't used uefi on ubuntu yet.

To reinstall grub from live mode, you only need to temporarily mount the root partition (and the boot partition if there is one), and tell grub to install on the MBR. Lets say your server disk is /dev/sda and the root partition is /dev/sda1. From live mode you would do:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will reinstall it telling it where did you temporarily mounted the root.

---

### Post by Mike_Hughes on 2017-01-21
How do I boot the server in live mode? Also notice this  [COLOR=#111111][FONT=Ubuntu] I had originally set my Ubuntu Web Server up on a Dell computer before anyone, maybe except Bill Gates, new what EFI was. So that says originally it had been Legacy. Ubuntu Server 14.04 LTC. So a couple of years ago in my work as a Broadcast Engineer I replaced a Streaming Computer with a 1TB drive newer than my Dell. The computer was given to me by the company. This computer a HP had EFI, I didn't know what it was at the time. Any way I used HDClone and installed my Ubuntu Server Clone backup onto the HP computer wiping the Windows 8 that was on it completely out. Worked fine lasted a long time. Till I had a problem and decided to try and restore the backup I had religiously made of my now Ubuntu Server now on my HP computer. At first when I restored it would not boot. So it was suggested I got Boot-Repair hoping to repair the issue. It gave me an error message that I needed Boot-Repair on a disk to do a repair on the EFI boot, which I didn't know I had. But that the Boot-Repair had to run on a USB Flash Drive. I went trying to find software to create that on my trusty Macbook Pro since I don't want any part of a Windoze system in my house. Can't find. So it dawned on me my whole issue may be that I should have disabled EFI before I installed the now long gone original Server Clone from the old Dell computer. I turned off EFI in my setup. Decided to try the restore again. Did now I run Boot-Repair I now receive this error GPT detected. Please Created a BIOS-Boot partition. Says I can use Gparted, which I don't have any experience using. I read your responses that show lines to put in through command line. I can't get to a command line to enter anything since I can't get the bloody thing to the point of putting in any command. Now I have thought of 2 possibiliies. 1. Put Ubuntu on another computer and try and hook up my clone drive to it and some how created a the Bios-Boot Partition there. Or run the command line commands suggested in the other post. 2. What if I took Ubuntu Server I think 16.X LTS and try to get it to update would that created the MBR file? I hated to ask this again but I don't think my particular circumstance is covered in the previous answer.[/FONT][/COLOR]

---

### Post by darkod on 2017-01-21
If you have physical access to the server you can use Ubuntu Desktop live cd/usb to boot into live mode (Try Ubuntu). That would be easiest. Note that if you boot with cd your first HDD stays /dev/sda but if you boot with usb stick depending on the system the stick might be /dev/sda and the primary HDD to be /dev/sdb. So you have to take that into account before running any commands.

You would only need bios-boot partition if you have gpt table on the disk and are running legacy boot.
I don't use EFI but if I'm not mistaken you need both EFI system partition and bios-boot partition if you are running UEFI boot and the disk is gpt.

Which partitions you actually have on your server hdd?

---

### Post by Mike_Hughes on 2017-01-23
Question: I booted up on live CD. I see both Hard Drives in the File Explorer. Now when I try to drag files from the Backup Hard Drive, where the Website files that were working are located, I get a message I am not the owner and don't have permission to copy and paste. I need to get my apache2 configuration, sites enabled, wordpress directory with all the Website files and configuration plus data, the directories from www over to the new server. I know the key is getting permission for me to do that on both Drives but need to know how.
[COLOR=#000000] have legacy now. That was the issue before. The reason I had to reinstall the server software. I booted with a live CD as I don't have it on USB and don't have the software to create one on my MacBook pro.[/COLOR]

---

### Post by #&amp;thj^% on 2017-01-23
> **Mike_Hughes said:**
> Question: I booted up on live CD. I see both Hard Drives in the File Explorer. Now when I try to drag files from the Backup Hard Drive, where the Website files that were working are located, I get a message I am not the owner and don't have permission to copy and paste. I need to get my apache2 configuration, sites enabled, wordpress directory with all the Website files and configuration plus data, the directories from www over to the new server. I know the key is getting permission for me to do that on both Drives but need to know how.
[COLOR=#000000] have legacy now. That was the issue before. The reason I had to reinstall the server software. I booted with a live CD as I don't have it on USB and don't have the software to create one on my MacBook pro.[/COLOR]

Have you tried as root yet to copy the files and folders off?
IE:
```
sudo nautilus
```
Or the File manager native to the system.

---

### Post by darkod on 2017-01-24
You never specifically replied to the partitions question. Please post the output so we can see what you have on the disks:
```
sudo parted -l
```

As for the copying permissions, like it was said in the previous post you can run Nautilus with elevated permissions with 'sudo nautilus' or 'gksu nautilus'. But it also matters how did you make the backup, with rsync or something similar that keeps ownership and permissions, or by simple copy? You never do backups/restore with simple copy because in such case you will lose the ownership and maybe permissions. So after you do the restore you again have to chase up which permissions to set on which files. The restore process you use depends on the backup process you used.

---

