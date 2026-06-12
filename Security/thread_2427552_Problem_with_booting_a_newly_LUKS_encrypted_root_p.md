---
title: "Problem with booting a newly LUKS encrypted root partition"
date: 2019-09-24
forum: Security
---

### Post by luksbootproblem on 2019-09-24
I didn't encrypt my root partition when I was installing my Ubuntu 18.04 when 18.04 first came out (first few months of it's release)
So for reasons I decided to encrypt it now.

I don't know if this is the right/best forum section for my issue, sorry if it isn't and please move it to the right place, thank you. And I do know there has been articles and asked questions and th before (Actually I posted the links of some of the asked questions!) but I posted this because this issue is specific to me. I did not find anyone who had an issue exactly same as mine, and after doing some MAJOR linux stuff, I had to ask for help since I was unable to solve this by myself. (Which hasn't happened a lot over my past 11 years of GNU/Linux-*nix experience. I solved/fixed my problems by myself and dear Google like 99% of the times... and as you know problems happen a lot in linux! :D )

Anyway, Here are the steps of which I did it: (In a 18.04 live usb)
```

    sudo cryptsetup -v -y -c aes-xts-plain64 --key-size 512 --hash sha512 luksFormat --uuid=049172c6-5376-4b9c-bd27-b503b6f25423 /dev/sda5
    sudo cryptsetup -v luksOpen /dev/sda5 myroot
    sudo mkfs.ext4 -m 0 /dev/mapper/myroot
    #Then for copying the contents of my root partition I used dd:
    sudo dd if=/dev/sda6 of=/dev/mapper/myroot bs=4M
    #/dev/sda6 is a duplicate of my original sda5 root...
    #After I dd'ed, there was unallocated space on the partition so I did a check on it in GParted (Which also applies cryptsetup resize command to it)
    sudo mount /dev/mapper/myroot /media/myroot #I created /media/myroot beforehands
```

Then after this I did A LOT of things I thought would help for booting this new encrypted root of mine with GRUB, and also A LOT OF MORE things I found by searching. So I basically tried everything people suggested in these links:

[https://askubuntu.com/questions/1134998/booting-19-04-from-luks-system-drive](https://askubuntu.com/questions/1134998/booting-19-04-from-luks-system-drive)
[https://unix.stackexchange.com/questions/345898/set-initramfs-to-prompt-for-luks-passowrd-on-startup-on-mint-18](https://unix.stackexchange.com/questions/345898/set-initramfs-to-prompt-for-luks-passowrd-on-startup-on-mint-18)
[https://askubuntu.com/questions/1006867/cant-get-ubuntu-to-boot-from-luks-lvm-group-on-external-drive-on-imac-with-re](https://askubuntu.com/questions/1006867/cant-get-ubuntu-to-boot-from-luks-lvm-group-on-external-drive-on-imac-with-re)
[https://askubuntu.com/questions/729673/ubuntu-full-disk-encryption-with-encrypted-boot](https://askubuntu.com/questions/729673/ubuntu-full-disk-encryption-with-encrypted-boot)
[https://askubuntu.com/questions/450895/mount-luks-encrypted-hard-drive-at-boot](https://askubuntu.com/questions/450895/mount-luks-encrypted-hard-drive-at-boot)
[https://askubuntu.com/questions/1082131/how-to-get-grub-to-boot-from-a-newly-encrypted-partition](https://askubuntu.com/questions/1082131/how-to-get-grub-to-boot-from-a-newly-encrypted-partition)

(And a lot of more links)

Here's the output of fdisk -l:
```

    Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: gpt
    Disk identifier: FE0857E8-E0DE-40A0-96C5-C4FEC80B8742
    
    Device         Start       End   Sectors   Size Type
    /dev/sda1       2048    534527    532480   260M EFI System
    /dev/sda2     534528   1067007    532480   260M EFI System
    /dev/sda3    2582528   4630527   2048000  1000M Lenovo boot partition
    /dev/sda4    4892672 259438591 254545920 121.4G Microsoft basic data
    /dev/sda5  259438592 332343295  72904704  34.8G Linux filesystem
    /dev/sda6  332343296 400898047  68554752  32.7G Linux filesystem
    /dev/sda7  410068992 425521151  15452160   7.4G Microsoft basic data
```

These are my UUIDs:

```
    /dev/sda5:
    LUKS UUID: 049172c6-5376-4b9c-bd27-b503b6f25423
    Partition UUID: 1db5df50-7000-48df-a281-74bad5689ce1
    
    /dev/sda6:
    Former UUID which I recently changed it to a new one because it was same as sda5's due to using dd for copying root filesystem to new LUKS partition: 1db5df50-7000-48df-a281-74bad5689ce1
    New UUID: 7876a195-7219-4440-892a-61b57c706443
```

And finally the things I tried in GRUB:
[ attached file ]

Any help will be much appreciated I really don't want to reinstall and encrypt from the installer, I need the things I have on my ubuntu and I really can't do a reinstall, this ubuntu install of mine is just so perfect, I've had a lot of experience with GNU/Linux (Over 10 years now) and had a lot of linux installations and I'm no noob, but I just can't loose all my data or configurations or customizations I made... I know I can back them up but I just... you know?

---

### Post by TheFu on 2019-09-24
> **luksbootproblem said:**
>  
Any help will be much appreciated I really don't want to reinstall and encrypt from the installer, I need the things I have on my ubuntu and I really can't do a reinstall, this ubuntu install of mine is just so perfect, I've had a lot of experience with GNU/Linux (Over 10 years now) and had a lot of linux installations and I'm no noob, but I just can't loose all my data or configurations or customizations I made... I know I can back them up but I just... you know?

No, I don't know. If your backup can't be restored to a fresh machine and behave the same as before then, IMHO, you don't have a backup. If you have less than 50G of data, the entire setup and restore should take less than 45 min with a system working exactly as it did before.  Your data, system data, your settings, and system settings fully restored.  It should be YOUR system, even if moving to a new computer.  The underlying storage setup isn't important. Let the installer handle that and all the boot parts.  I've changed the number, size, and types of partitions used a few times when moving systems.  Provided that everything appears in the correct directories, it should be fine.  Abstracting away the storage makes all sorts of things easier.

 When the installer sets up encryption, it creates an encrypted container inside a partition, then uses LVM inside it so management of the storage inside that encrypted container is much easier.  I can't believe that choice was made without lots and lots of consideration concerning adding the complexities of LVM or not.  In the end, they decided it was best.  

At the step where you created the file system, that's where they create a PV, VG, and 2 LVs (root and swap).  Then a mkfs and mkswap.  I'm confused why dd would be used, when rsync would be much faster to move your data into the LV.  

All my attempts to get manual setups booting encrypted+LVM areas have failed, but there is an extensive thread about manually doing that.  I didn't follow all those links to see if you'd found Paddy's links in these forums. The mysteries of the crypttab + initird have eluded my knowledge.  I've always found Ask Ubuntu's format to be too short for complex issues.

One of the most useful commands today is **lsblk**.  It quickly shows disk, partition, and underlying storage object relationships.

Sorry that I'm probably not any real help here. Good luck.

---

### Post by luksbootproblem on 2019-09-24
> **TheFu said:**
> No, I don't know. If your backup can't be restored to a fresh machine and behave the same as before then, IMHO, you don't have a backup. If you have less than 50G of data, the entire setup and restore should take less than 45 min with a system working exactly as it did before.  Your data, system data, your settings, and system settings fully restored.  It should be YOUR system, even if moving to a new computer.  The underlying storage setup isn't important. Let the installer handle that and all the boot parts.  I've changed the number, size, and types of partitions used a few times when moving systems.  Provided that everything appears in the correct directories, it should be fine.  Abstracting away the storage makes all sorts of things easier.

 When the installer sets up encryption, it creates an encrypted container inside a partition, then uses LVM inside it so management of the storage inside that encrypted container is much easier.  I can't believe that choice was made without lots and lots of consideration concerning adding the complexities of LVM or not.  In the end, they decided it was best.  

At the step where you created the file system, that's where they create a PV, VG, and 2 LVs (root and swap).  Then a mkfs and mkswap.  I'm confused why dd would be used, when rsync would be much faster to move your data into the LV.  

All my attempts to get manual setups booting encrypted+LVM areas have failed, but there is an extensive thread about manually doing that.  I didn't follow all those links to see if you'd found Paddy's links in these forums. The mysteries of the crypttab + initird have eluded my knowledge.  I've always found Ask Ubuntu's format to be too short for complex issues.

One of the most useful commands today is **lsblk**.  It quickly shows disk, partition, and underlying storage object relationships.

Sorry that I'm probably not any real help here. Good luck.

Thank you very much.

No, actually; it did help! After like 3 days of kind of wasting my time and effort for keeping my current installation and just encrypting it, and after doing a lot of stuff, and also after some stuff people suggested me to do in sites like askubuntu or stackexchange's unix section, I finally realized and decided that I should just let go of my current Ubuntu installation and just reinstall with encryption enabled this time... and restore my settings and configs and customizations and everything to the new installation.

And I DID say that I know I can backup everything and restore them in the new installation, I just meant that I prefered not doing that and keeping my current setup. But now I've changed my mind.

So, in order to restore like totally EVERYTHING I have on my current setup to a new one I'm going to install in the near future, I think (If I'm not mistaken) I have to backup everything in the /etc, /bin, /lib&lib64, /opt. /root. /sbin, /snap, /srv, /usr, /var and obviously the home dir. Is this right? are these directories I just mentioned the right ones to backup for restoring my exact same system to a new installation? Am I missing any dirs? or perhaps did I mention any dirs that are not needed for this purpose?

And before you say anything, I DID search about this, I found some stuff but didn't find exactly what I was looking for! IDK why! Everything I found either suggested apps that can backup stuff and restore, and stuff like that. I didn't find something that explained what exactly I need to do/and-or keep (backup) in order to completely/fully restore my current setup into a new installation. So can you please assist me about this?

I'm just tired of being stranded in live systems and boot screens and... I need my Linux back! I'm like in a Linux withdrawal! and as all withdraws, this is also very hard! I need my stable linux box back! :( So as a fellow Linux junkie to another, I ask you to please help me get my system back but this time with an encryption. Besides this whole thing is near an end since I just need some conformation about what exactly I should do/backup in order to fully restore my current setup. So it won't take too much of your time to help me, just saying so you know that I'm not making a big deal out of this by stuff I said in the past couple of lines about withdraw and etc.
Thank you in advance so so much for your awesome guidances.

---

### Post by TheFu on 2019-09-24
Everyone has their own backup needs.  1 size doesn't fit all.

I do not backup anything in the core OS, booting, programs or libraries that can trivially be installed. What needs to be installed completely depends on the system.  On a desktop, I don't backup anything in /var/ - there's nothing there interesting.  On a server, it is likely THE MOST IMPORTANT area to be backed up on the system.

There must be at least 50 different threads here about backups.  Encryption has zero to do with my backup methods. It doesn't matter anymore.  I stopped using HOME directory encryption because I was unable to figure out a way to do backups without being logged in.  Switched to whole drive encryption and never regretted it.  I've had a few SSDs fail on laptops with whole drive encryption. The failures were minor inconvenience only. The encryption had zero bearing on the restore.

Anyway ... search for rdiff-backup, apt-mark, snapshot and my username. Here's one of the more advanced discussions.
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)  since you seem ready for that.

For me, the way that storage is setup and how LVM LVs are created is all about making backups easier while also being flexible for unknown growth, as needed, where needed.

Probably best to ask a specific backup question in a new thread.

---

