---
title: "Encrypt SSD with user home on separate SSD"
date: 2023-02-28
forum: Security
---

### Post by upchucky on 2023-02-28
At present, Ubuntu 22.04 is installed on one partition of my first 2TB SSD.
I have my "User Home" on a different partition of my first SSD.
I know that I can choose to encrypt the entire SSD that Ubuntu is on if I re-install Ubuntu.
I know that I must back up my existing "User Home" before encrypting the first SSD when I re-install Ubuntu.

I already encrypted the Second 2TB SSD and I have about 700 GB of files on it.
I also have a 3TB external drive that I can temporarily move the files to.
I can also back up my existing "User Home" to the external drive.

I can't find any verbose instructions on how to set up an encrypted Ubuntu installation on the first SSD, and at the same time enable the Installation to work with my "User Home" directory which I want to have on my second already encrypted 2TB SSD.

I would like Ubuntu to be installed on the first 2TB SSD, but a 2TB SSD is way too much space just for Ubuntu.
I need to know if I can create a 200GB partition just for Ubuntu during the encrypting/installation phase.
I need to know if I can also set up a second partition that would utilize the remaining SSD space for my files.
I also need to know if I can resize my second encrypted SSD with three partitions, one for Main Storage, one for Temp Storage and the other for testing other flavors of Linux.
I do not use a Swap Space.
I tried to use encryptfs with the recommended alternate administrative user account to encrypt my existing "User Home" partition and it failed with an error of some files not being allowed.
Encryptfs advised to check the logs for further information but the logs said "null"
Encryptfs would not proceed further, I was stuck with a non responsive computer and forced to reboot.
I was able to restore my "User Home" from my Time Shift backup, however Timeshift synced my back up with the failed ecryptfs files and Thunderbird would not start.
It took me several hours to get rid of the corrupted ecryptfs files so I could restore my original settings.
In retrospect I should have guessed that Timeshift would automatically sync a set of newly corrupted files with the original files.
Any Ideas out there?

---

### Post by TheFu on 2023-03-01
When you say "encryption", you realize there are 20 different MAJOR types, correct?  They are not all equal.  For example, encryptfs and encfs both have some major flaws.  I found neither useful since they didn't allow system-wide backups.  I ended up using LUKS, which is built-into the Ubuntu installer.  Also, the default install under Ubuntu places the LUKS container in a partition, then sets up an LVM PV, VG, and LVs inside it.  See this image attached to this post (way at the bottom).

Setting up a LUKS encrypted partition is relatively straight forward.  There are things you won't like when doing it the way outlined below.  It won't mount at boot unless it was setup that way using the installer. That's a big one for me.  The good news is that a few file managers will prompt to mount the storage if you dbl-click on the partition with the LUKS container.  The bad news is that HOME directories need to be mounted BEFORE a login to be useful.

See Two videos and 1 text location:
[LIST]
[*] Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
[*] Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.
[*] Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)         
[/LIST]

Ok, so now that's handled, even with the limits. There are 2 options for the other LUKS container that is outside what was used during installation.
 a Use the normal installation and have the HOME directory located on the internal storage with symbolic links to the external, LUKS encrypted, storage.  This assumes you have /home/ with the normal install encryption ... but /home/thefu/Documents/ and other directories with lots of data on the other LUKS encrypted storage ... with a symlink.  You'll need to open the encrypted storage before accessing those areas, which could become a hassle.  Or use the Links above so it is automatically unlocked when on THIS specific system.
 b Setup the /etc/crypttab to unlock the 2nd LUKS storage at boot too.  There's an example and I wish I had more details about it. I use LUKS on laptops and mine have just 1 internal SSD, so I've never needed to figure it out.  
```
$ man crypttab # explains the format of the file
NAME
       crypttab - static information about encrypted filesystems

DESCRIPTION
       The file /etc/crypttab contains descriptive information about
       encrypted filesystems. crypttab is only read by programs (e.g.
       cryptdisks_start and cryptdisks_stop), and not written; it is the
       duty of the system administrator to properly create and maintain this
       file. Each filesystem is described on a separate line; fields on each
       line are separated by tabs or spaces. Lines starting with &#8220;#&#8221; are
       comments, empty lines are ignored. The order of records in crypttab
       is important because the init scripts sequentially iterate through
       crypttab doing their thing.
....
       initramfs
           The initramfs hook processes the root device, any resume devices
           and any devices with the &#8220;initramfs&#8221; option set. These devices
           are processed within the initramfs stage of boot. As an example,
           that allows the use of remote unlocking using dropbear.
...
```

If you use the crypttab, you'll need to update the initramfs config too, so it knows your intention. May need to update grub too. IDK.  Outside my knowledge.

The cryptsetup manpage was all I needed to manually create multiple LUKS encrypted devices and have multiple "open" methods (crazy-long passphrase, challenge-response from a Yubikey device).

To the lurkers, always remember, available storage that is encrypted is only safe when the system is completely at rest, powered off.  Hibernation and standby modes ARE NOT powered off.  I have a rule. If I'm getting into a vehicle with my laptop, I power it down.  I'd probably do that if I was walking between buildings on a college campus too.

BTW, always use the manpages on your local machine, since any blogs, how-to guides and manpages on the internet won't be for your exact version.  Things change.  I know **cryptsetup** changed some parameters last time I needed to touch it.

Lastly for lurkers, if using encryption, please, please, please, ensure you have excellent backups and have tested the restore.  A few times a month, someone wants to get data back from their encrypted storage, doesn't have backup and the device is failing or has a logical corruption problem.  Working and tested backups are the only solution.

---

### Post by upchucky on 2023-03-02
Thank you, TheFU,
I was reading about the many possibilities for encryption.
Because Ubuntu and home were on the same drive but different partitions, reinstalling Ubuntu encrypted "LUKS" means to encrypt the entire drive. Partitioning the drive after encryption was a grey area that instructions did not explain.
The simpler solution seemed to be, choose ecryptfs to encrypt my existing user home.
I did use the text instructions that you referenced in your reply to encrypt the second SSD for all other data.

My best setup would be, encrypted Ubuntu "without Snap" on a 100 GB partition on the first SSD
The remaining partitioned space on the first SSD would be for storage and/or a third partition for testing other flavors of Linux.
The second SSD would be encrypted and Home would be on a 1TB partition.
The remaining encrypted 1TB partitioned space would be for storage.

If I have time this weekend, I am going to back up my home without using Timeshift to avoid the syncing issues when files get corrupted.
I will try your suggestion, "b" , unlock second SSD at boot.
If I have to, I can make my own live Ubuntu with persistent storage on my 3 tb external drive then experiment until I get it working on my computer the way I need it to be.
Wish me luck.

---

### Post by TheFu on 2023-03-02
If you use LVM, then you don't need to worry about partition junk as much.  LVM provides flexibility and encourages setting up an LV (think of an LV as a really, really, really, flexible partition that can be resized without being offline).  Resizing an LV (logical volume) is 5 seconds and the file system can be active and working while that happens. Zero downtime.

Did you look at the image I attached?

100G is much, much, much too large for the OS.  There are plenty of reasons I'd encourage you to reconsider your plans. 
And I'd never consider encryptfs as an option.  Using bad encryption is worse than using no encryption. It leads to a false sense of security that doesn't actually exist.

---

### Post by upchucky on 2023-03-06
So I did reconsider and I used LVM full disk encryption.
Both my SSD's are now Luks encrypted.
However, after much experimenting, during installation I could not find a way to put my home on the second encrypted SSD and get Ubuntu to boot.
Ubuntu would ask for the passphrase and then upon entering the correct passphrase, it would not boot.
Of interest was that Ubuntu luks install produced a separate encryption key for each SSD with the same password for both SSDs during partition set up.

My system as it stands at the moment is all on the first SSD.
I do not care for that scenario, as I like the ability to mess with my OS and not worry about my home.
I once had to remove my SSDs and install them on another machine while mine was sent back for a warranty motherboard replacement.
The other machine's hardware did not like my original ubuntu install so I had to reinstall Ubuntu and then tell it where my home was.

For now, I will have to do weekly backups of home and the files in storage (at present over 2TB)
This is problematic because the backups do not restore all user/configuration settings for Thunderbird, Firefox, HP Printers and a few other common applications.
This issue became more tedious with the switch to "Snaps"
I end up reinstalling a few applications and having to tweak them to my liking.
 
I am thinking that I should leave this post open in case someone figures out how to have the OS on one SSD and home on a different SSD with both SSD being encrypted during the installation of Ubuntu, and being enabled upon boot.

---

### Post by TheFu on 2023-03-06
Did you consider this?
>  This assumes you have /home/ with the normal install encryption ... but /home/thefu/Documents/ and other directories with lots of data on the other LUKS encrypted storage ... with a symlink. You'll need to open the encrypted storage before accessing those areas, which could become a hassle. Or use the Links above so it is automatically unlocked when on THIS specific system.
That's how long time users keep there HOME directories small, but have easy access to lots of storage on different physical storage - use symlinks.  If you search these forums, you'll see many of the forum moderators use that method.

As for backing up snaps and data assigned to snaps, there's a built-in snap tool for that. It isn't eligant and doesn't support versioning, but it will export the snap and all data for it and for the specific users, if you ask.
[https://snapcraft.io/blog/how-to-create-snapshots-of-your-snaps](https://snapcraft.io/blog/how-to-create-snapshots-of-your-snaps)  For example, 
```
$ snap save --users=thefu,upchucky
```

As for system-backups, I've posted 50+ posts here about that. Encryption doesn't matter with the technique provided and what I use.

A little background on LUKS encryption.  There are 8 "slots" in the LUKS header for different unlock keys/methods.  The actual data is encrypted the same, regardless.  This means that it is 1 level of redirection to unlock a LUKS container.  When we are challenged for the unlock code/method, that just unlocks the header where the real key to unlock the full LUKS container is stored.  I use 3-5 of the "slots" in my encrypted laptop.  
[LIST=1]
[*] 75 random character passphrase that I doubt I could type even if I wanted.
[*] "Yubikey A" challenge/response - the yubikey software prompts me for input (challenge), and that input outputs over the HID connection a passphrase that nobody knows which is used to attempt to unlock the LUKS header.
[*] "Yubikey B" - ... same as "Yubikey A"; I've lost yubikeys before.
[*] 44 random character passphrase kept with my lawyer.
[*] 44 random character passphrase that is split 50/50 between 2 trusted relatives who have to agree to unlock the storage in an emergency. They are executors of my estate and have medical power of attorney should my better half die.  These people also have access to my home password manager DB under the same situation.  Every few years, I change their half of the passphrase. The USB key for their use is hidden, so they have to ask a specific person for the location, neither knows it.
[/LIST]

Had a relative die about 10 yrs ago with a few years of prior knowledge it was coming. She had worked through a checklist for ensuring her estate was handled the way she wished.  She wasn't big on the internet, but did have some online accounts.  We never needed them, not really.  With a death certificate, every business closed accounts and disbursed refunds with next to zero hassles.

Debian has detailed how-to encrypt stuff guides, but when you do it manually, don't expect Ubuntu OS upgrades to work.  You've been warned.  As soon as you do non-default things, you get what you get.

With proper backups and restores that have been practiced, there's very little worry in starting fresh with a new install of Ubuntu.  2TB really isn't THAT much data.  
```
$ inxi -d
Drives:    Local Storage: total: 37.13 TiB used: 22.56 TiB (60.8%) 

```Just sayin'.

---

### Post by upchucky on 2023-03-11
Ureka!
After much beard growing my solution was amazingly simple.
I could not get gparted or Ubuntu Disks to resize the encrypted root or home partitions.
Reinstalling did not let me create a reasonable partition size for home or root and by default it set up a hidden swap partition that is contrary to good data protection principles.
All the instructions that I found said that you can't use gparted to resize a LUKS Partition but you can do it by way of Fdsk and in the terminal.
After many backups and "Wile E. Coyote" experiments that led nowhere, I found that the latest KDE Partition Manager can handle LUKS partitions.
I now have only Ubuntu process files on home to allow booting after entering passphrase.
All other home files are now on the second LUKS encrypted SSD.
The exception is Thunderbird mail, for some reason the Mozzilla instructions to set the mail profile on a different location do not work.
I have regular scheduled email backups, so I can live with that for now.
I can live with entering the passphrase to access my files after booting because the drive stays active until shutdown.
I can now encrypt the 3TB external drive that I use for backups.
When I find a solution to the Thunderbird issue, I will post it in the appropriate forum.
My solution is not pretty but it solved my intent to have all my data and files encrypted.
I thank you The Fu for your time and effort, One day when I have more time I will take another look at symlinking as you suggest.
I think this thread can be marked solved.

---

### Post by TheFu on 2023-03-11
The default Ubuntu LUKS install uses LVM inside a LUKS container.  I included an image in post #2 which shows how LUKS and LVM PVs, VGs, and LVs are related in a single disk setup.
  LVM is amazing, if you know how to use it. Things that you see as "hidden" were probably just logical volumes, LVs.  LVs are like really, really, really, flexible partitions that can be resized.

Anyway, if you are happy, we are happy, but it would be nice if you would run a few commands and post the output here for the solution you have today. Those commands are:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
sudo pvs
sudo vgs
sudo lvs

```

From those commands, we'd know what setup you have so we can help others if you aren't around to offer the help.

---

### Post by oldfred on 2023-03-11
I do not use LVM nor encryption. And I have totally unstalled snaps so both Firefox & Thunderbird are from ppa.

But since about 2006 have had both Firefox & Thunderbird in different partitions & linked into /home.
Originally in a NTFS partition shared with XP & Ubuntu. Slightly different versions made no difference. 
Then after XP uninstalled only in ext4 partition.
But since about 20.04, Firefox linking stopped working. And lots of complaints about versions not matching.

Thunderbird for now still works. (Have not linked in latest install.) Last link was from 20.04 to 22.04 install using same data partition.
Entire profile is in a data partition and that is linked.

Cannot share Firefox profiles anymore
[https://support.mozilla.org/en-US/kb/dedicated-profiles-firefox-installation](https://support.mozilla.org/en-US/kb/dedicated-profiles-firefox-installation)

thunderbird:
[https://support.mozilla.org/en-US/products/thunderbird](https://support.mozilla.org/en-US/products/thunderbird)
[https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer](https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer)
[https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data)
[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location)

---

### Post by upchucky on 2023-03-13
itsme@itsme:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4  144G  117G   20G  86% /
/dev/nvme1n1p2            ext4  459M  270M  155M  64% /boot
/dev/nvme1n1p1            vfat  511M  6.1M  505M   2% /boot/efi
/dev/dm-3                 ext4  2.7T   28K  2.6T   1% /media/itsme/f70cf4ee-ead6-498b-b7b4-6cb93a19228d
itsme@itsme:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                                            SIZE TYPE  FSTYPE      MOUNTPOINT
sda                                           931.5G disk              
&#9492;&#9472;sda5                                        931.3G part  ext4        
sdb                                             2.7T disk              
&#9492;&#9472;sdb1                                          2.7T part  crypto_LUKS 
  &#9492;&#9472;luks-a727520d-7a60-4e41-9b78-d8b3e3beb489   2.7T crypt ext4        /media/itsme/f70cf4ee-ead6-498b-b7b4-6cb93a19228d
nvme0n1                                         1.9T disk  crypto_LUKS 
nvme1n1                                         1.8T disk              
&#9500;&#9472;nvme1n1p1                                     512M part  vfat        /boot/efi
&#9500;&#9472;nvme1n1p2                                     501M part  ext4        /boot
&#9492;&#9472;nvme1n1p3                                     1.8T part  crypto_LUKS 
  &#9492;&#9472;nvme1n1p3_crypt                             1.8T crypt LVM2_member 
    &#9500;&#9472;vgubuntu-root                           146.5G lvm   ext4        /
    &#9492;&#9472;vgubuntu-itsmeFiles                       1.7T lvm   crypto_LUKS 
itsme@itsme:~$ sudo pvs
[sudo] password for itsme: 
  PV                          VG       Fmt  Attr PSize  PFree 
  /dev/mapper/nvme1n1p3_crypt vgubuntu lvm2 a--  <1.82t <1.18g
itsme@itsme:~$ sudo vgs
  VG       #PV #LV #SN Attr   VSize  VFree 
  vgubuntu   1   2   0 wz--n- <1.82t <1.18g
itsme@itsme:~$ sudo lvs
  LV         VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  itsmeFiles vgubuntu -wi-a-----   1.67t                                                    
  root       vgubuntu -wi-ao---- 146.50g                                                    
itsme@itsme:~$ 

The SDA is an old HD that I use as a junk drawer when testing or downloading unknown/unverified stuff.
I do not put files in the default user home, they go in the second SSD where I set up my own file management system.
I have had more success with Firefox and Thunderbird settings/troubleshooting information by searching the web rather than using Mozilla's site.

---

### Post by TheFu on 2023-03-13
'code tags' for the post above, please.  Just edit it.
 [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) a how-to, if you don't understand. Columns matter. Without forum code tags, the columns are lost. Too hard to read.

---

### Post by upchucky on 2023-03-13
I ran the codes in the order that you posted them in.

Code:
> df -hT -x squashfs -x tmpfs -x devtmpfs

Filesystem Type Size Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4 144G 117G 20G 86% /
/dev/nvme1n1p2 ext4 459M 270M 155M 64% /boot
/dev/nvme1n1p1 vfat 511M 6.1M 505M 2% /boot/efi
/dev/dm-3 ext4 2.9T 28K 2.6T 1% /media/itsme/3TbStorage

Code:
> lsblk -e 7 -o name,size,type,fstype,mountpoint

NAME SIZE TYPE FSTYPE MOUNTPOINT
sda 931.5G disk
&#9492;&#9472;sda5 931.3G part ext4
sdb 2.9T disk
&#9492;&#9472;sdb1 2.9T part crypto_LUKS
&#9492;&#9472;luks-a727520d-7a60-4e41-9b78-d8b3e3beb489 2.9T crypt ext4 /media/itsme/3TbStorage
nvme0n1 1.9T disk crypto_LUKS
nvme1n1 1.8T disk
&#9500;&#9472;nvme1n1p1 512M part vfat /boot/efi
&#9500;&#9472;nvme1n1p2 501M part ext4 /boot
&#9492;&#9472;nvme1n1p3 1.8T part crypto_LUKS
&#9492;&#9472;nvme1n1p3_crypt 1.8T crypt LVM2_member
&#9500;&#9472;vgubuntu-root 146.5G lvm ext4 /
&#9492;&#9472;vgubuntu-itsmeFiles 1.7T lvm crypto_LUKS

Code:
> sudo pvs

PV VG Fmt Attr PSize PFree
/dev/mapper/nvme1n1p3_crypt vgubuntu lvm2 a-- <1.82t <1.18g

Code:
> sudo vgs

VG #PV #LV #SN Attr VSize VFree
vgubuntu 1 2 0 wz--n- <1.82t <1.18g

Code:
> sudo lvs

LV VG Attr LSize Pool Origin Data% Meta% Move Log Cpy%Sync Convert
itsmeFiles vgubuntu -wi-a----- 1.67t
root vgubuntu -wi-ao---- 146.50g

The SDA is an old HD that I use as a junk drawer when testing or downloading unknown/unverified stuff.
I do not put files in the default user home, they go in the second SSD where I set up my own file management system.
I have had more success with Firefox and Thunderbird settings/troubleshooting information by searching the web rather than using Mozilla's site.

---

### Post by oldfred on 2023-03-13
Code Tags preserve formatting of text or terminal output.

How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

