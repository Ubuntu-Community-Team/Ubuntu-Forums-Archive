---
title: "btrfs makes old hdds appear to operate faster"
date: 2013-02-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-02-05
I was just doing a followup on a suggestion in another thread and achieved a successful install using btrfs.

The hdd is a Maxtor 5T020H2 (TAH71D0P), 20GB (older).

---

### Post by ventrical on 2013-02-05
at bootup I am still getting :

error: sparse file not allowed

---

### Post by castrojo on 2013-02-05
It's a bug, it's nothing to be worried about: [http://askubuntu.com/questions/100329/message-sparse-file-not-allowed-after-installing-on-a-btrfs-filesystem](http://askubuntu.com/questions/100329/message-sparse-file-not-allowed-after-installing-on-a-btrfs-filesystem)

You can just hit a key and it'll keep booting.

---

### Post by tgalati4 on 2013-02-05
Those older Maxtors are good drives.  I've had one spinning for over 118,000 hours now.

Mine is a 20GB, Maxtor 92049U3.

Sounds like it's time to do some experimenting with btrfs.

---

### Post by ventrical on 2013-02-06
> **castrojo said:**
> It's a bug, it's nothing to be worried about: [http://askubuntu.com/questions/100329/message-sparse-file-not-allowed-after-installing-on-a-btrfs-filesystem](http://askubuntu.com/questions/100329/message-sparse-file-not-allowed-after-installing-on-a-btrfs-filesystem)

You can just hit a key and it'll keep booting.

Yes .. it is booting well in fact.

Thanks for the bug link.

---

### Post by ventrical on 2013-02-06
> **tgalati4 said:**
> Those older Maxtors are good drives.  I've had one spinning for over 118,000 hours now.

Mine is a 20GB, Maxtor 92049U3.

Sounds like it's time to do some experimenting with btrfs.


   I loaded up some programs and then rebooted.  Some programs seems to be indexed after the next boot, so they load real fast , ie; System Monitor, but it was not the case for Libre' Office Writer.

  I am going to swap this drive into another system and then do an install on a faster hdd. 

  I cannot say , definitively for sure, that the one install so far is actually faster , but, by eyeballing it from previous installs, it appears to be working faster. More experiments needed.

---

### Post by celluloid on 2013-02-06
> **ventrical said:**
> I loaded up some programs and then rebooted.  Some programs seems to be indexed after the next boot, so they load real fast , ie; System Monitor, but it was not the case for Libre' Office Writer.

  I am going to swap this drive into another system and then do an install on a faster hdd. 

  I cannot say , definitively for sure, that the one install so far is actually faster , but, by eyeballing it from previous installs, it appears to be working faster. More experiments needed.

I've done a fair bit of testing of btrfs, partly because of pure curiosity & partly because I specialise in Linux storage technologies for work.

Are you using default mount flags in your fstab or are you specifying specific mount flags? See: [https://btrfs.wiki.kernel.org/index.php/Mount_options](https://btrfs.wiki.kernel.org/index.php/Mount_options) for your options, I found that the defrag and compression specific flags made some difference back when I was testing (late 12.04/12.10 dailies)

---

### Post by pressureman on 2013-02-06
Most computer slowness these days is caused by waiting for IO (unless you have an SSD), so disk compression makes good sense. The CPU(s) have enough idle time that the computational overhead of compression isn't noticeable, and the nice side effect is that it means the HDD has to read/write fewer blocks - hence IO will generally be faster.

This fact was trumpeted rather loudly by the Solaris crowd when ZFS compression first arrived on the scene.

---

### Post by ventrical on 2013-02-06
> **celluloid said:**
> I've done a fair bit of testing of btrfs, partly because of pure curiosity & partly because I specialise in Linux storage technologies for work.

Are you using default mount flags in your fstab or are you specifying specific mount flags? See: [https://btrfs.wiki.kernel.org/index.php/Mount_options](https://btrfs.wiki.kernel.org/index.php/Mount_options) for your options, I found that the defrag and compression specific flags made some difference back when I was testing (late 12.04/12.10 dailies)


 I am stricktly using (/) root while using 'somthing else' option in Ubiquity.

---

### Post by castrojo on 2013-02-06
You might want to install `apt-btrfs-snapshot`, it'll create a snapshot every time you upgrade, which means theoretically you can undo a bad apt upgrade.

I've had it installed for a month now but I haven't found the time to actually try rolling back.

---

### Post by ventrical on 2013-02-06
> **castrojo said:**
> You might want to install `apt-btrfs-snapshot`, it'll create a snapshot every time you upgrade, which means theoretically you can undo a bad apt upgrade.

I've had it installed for a month now but I haven't found the time to actually try rolling back.


 I installed it on a DT.  Could you share with us a few commands on how to operate it? I assume it is running (at current) How do I roll it back (any links please).

thankyou.

edit :

Ok .. found this ..
[http://www.howtoforge.com/rollback-to-a-working-state-with-btrfs-plus-apt-btrfs-snapshot-on-ubuntu-12.10](http://www.howtoforge.com/rollback-to-a-working-state-with-btrfs-plus-apt-btrfs-snapshot-on-ubuntu-12.10)

---

### Post by ventrical on 2013-02-06
This has been just an awesome experience:

```

Supported
Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-an2qd2/@' in '/tmp/apt-btrfs-snapshot-mp-an2qd2/@apt-snapshot-2013-02-06_10:12:55'

```

```

Reading package lists... Done
root@ventrical-P4M266A-8237:/home/ventrical# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  language-selector-common language-selector-gnome syslinux syslinux-common
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,361 kB of archives.
After this operation, 797 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring-proposed/main language-selector-gnome all 0.100 [20.2 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ raring-proposed/main language-selector-common all 0.100 [331 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ raring-proposed/main syslinux-common all 2:5.01+dfsg-1 [879 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ raring-proposed/main syslinux i386 2:5.01+dfsg-1 [131 kB]
Fetched 1,361 kB in 6s (219 kB/s)                                              
Supported
Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-an2qd2/@' in '/tmp/apt-btrfs-snapshot-mp-an2qd2/@apt-snapshot-2013-02-06_10:12:55'
(Reading database ... 157178 files and directories currently installed.)
Preparing to replace language-selector-gnome 0.99 (using .../language-selector-gnome_0.100_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.99 (using .../language-selector-common_0.100_all.deb) ...
Unpacking replacement language-selector-common ...
dpkg: considering deconfiguration of syslinux-common, which would be broken by installation of syslinux ...
dpkg: yes, will deconfigure syslinux-common (broken by syslinux)
Preparing to replace syslinux 2:4.06+dfsg-3 (using .../syslinux_2%3a5.01+dfsg-1_i386.deb) ...
De-configuring syslinux-common ...
Unpacking replacement syslinux ...
Preparing to replace syslinux-common 2:4.06+dfsg-3 (using .../syslinux-common_2%3a5.01+dfsg-1_all.deb) ...
Unpacking replacement syslinux-common ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up syslinux-common (2:5.01+dfsg-1) ...
Setting up syslinux (2:5.01+dfsg-1) ...
Setting up language-selector-common (0.100) ...
Setting up language-selector-gnome (0.100) ...
root@ventrical-P4M266A-8237:/home/ventrical# mount /dev/sda1 /mnt
root@ventrical-P4M266A-8237:/home/ventrical# ls -l /mnt/
total 0
drwxr-xr-x 1 root root 208 Feb  5 19:14 @
drwxr-xr-x 1 root root 208 Feb  5 19:14 @apt-snapshot-2013-02-06_10:12:55
drwxr-xr-x 1 root root  18 Feb  5 19:11 @home
root@ventrical-P4M266A-8237:/home/ventrical# mv /mnt/@ /mnt/@_badroot
root@ventrical-P4M266A-8237:/home/ventrical# mv /mnt/@apt-snapshot-2013-02-06_10:12:55 /mnt/@
root@ventrical-P4M266A-8237:/home/ventrical# 

```

```

Ign http://ca.archive.ubuntu.com raring-proposed/multiverse Translation-en_CA  
Ign http://ca.archive.ubuntu.com raring-proposed/restricted Translation-en_CA  
Fetched 13.8 MB in 1min 19s (173 kB/s)                                         
Reading package lists... Done
ventrical@ventrical-P4M266A-8237:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gir1.2-signon-1.0 language-selector-common language-selector-gnome
  libsignon-glib1 syslinux syslinux-common
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.1 kB/1,409 kB of archives.
After this operation, 797 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

 Then , theoretically , if I did an install of Quantal Quetzal using btrfs and then Upgraded to raring after install the snapshot, then, I should be able to rollback to Quantal !!

---

### Post by castrojo on 2013-02-06
No manpage. :(

But this has the basic commands: 

sudo apt-btrfs-snapshot --help

---

### Post by grahammechanical on 2013-02-06
I thought that I would give today's daily image ago on btrfs. Bad experience.

Messages 

executing 'grub-install' /dev/sda failed.

At least it did not mess up the Grub menu controled by another Raring.

Installer Crash

When I tried to boot into that partition I got no such device need to load kernel first /boot/vmlinuz-3.8.0-4-generic not found

I guess it overwrote the Raring install that I put in that partition yesterday. I was hoping there might have an installation there that would boot. Disks utility is showing the partition as formatted as btrfs. I wonder if a re-install without a format will produce something.

First, I will try and update grub to see if it picks up the broken install. No. It does not find a Raring Ringtail on sda9. At least I have removed the broken menu link.

---

### Post by ventrical on 2013-02-06
> **castrojo said:**
> No manpage. :(

But this has the basic commands: 

sudo apt-btrfs-snapshot --help

Thanks. Already found a link as posted in previous. Rollback is a success.

  Now my attempt to install Quantal with btrfs, upgrade to Raring and then rollback to Quantal.

---

### Post by ventrical on 2013-02-06
> **grahammechanical said:**
> I thought that I would give today's daily image ago on btrfs. Bad experience.

Messages 

executing 'grub-install' /dev/sda failed.

At least it did not mess up the Grub menu controled by another Raring.

Installer Crash

When I tried to boot into that partition I got no such device need to load kernel first /boot/vmlinuz-3.8.0-4-generic not found

I guess it overwrote the Raring install that I put in that partition yesterday. I was hoping there might have an installation there that would boot. Disks utility is showing the partition as formatted as btrfs. I wonder if a re-install without a format will produce something.

First, I will try and update grub to see if it picks up the broken install.


I am having great success, Keep trying. I just used 'something else'. I deleted all the partitions and got 'free-space'. Then choose 'change'. Choose btrfs, format and '/' as mount point. Can't go wrong.

  I am now going to attempt to upgrade from a fresh install of Quantal to Raring and then rollback to Quantal.

This is more fun that I had in a long time. :)

Doh!
:)

---

### Post by The Cog on 2013-02-06
I just abandoned btrfs a couple of weeks ago. It had been getting slower and slower (all the firefox sqlite tables and cached images I suspect) and so I tried a defrag. Since you can only defrag one file at a time, I did something like:
find /home - exec btrfs defrag '{}' \;
When I came back after dinner, the PC had shut down (desktop, not on batteries) and the partition would not mount - invalid superblock etc.
So I restored a backup to jfs and now it feels like a new machine, much faster.

---

### Post by ventrical on 2013-02-06
> **The Cog said:**
> I just abandoned btrfs a couple of weeks ago. It had been getting slower and slower (all the firefox sqlite tables and cached images I suspect) and so I tried a defrag. Since you can only defrag one file at a time, I did something like:
find /home - exec btrfs defrag '{}' \;
When I came back after dinner, the PC had shut down (desktop, not on batteries) and the partition would not mount - invalid superblock etc.
So I restored a backup to jfs and now it feels like a new machine, much faster.


Did you attempt to do the rollback proceedure while you were experimenting with it?

---

### Post by ventrical on 2013-02-06
Upgrade to raring.

---

### Post by ventrical on 2013-02-06
Attempting to rollback to quantal was an absolute and complete failure. All I have now is the Grub Rescue menu :) Thats what you get when you forget to :
sudo update grub

---

### Post by grahammechanical on 2013-02-07
I tried again to get a Raring install on btrfs (yesterday's daily) Same result even though I choose to continue without installing a bootloader. I get an installer crashed message at the end and sudo update-grub from another Ubuntu does not detect an OS in the partition.

Is this because the format is btrfs? Or is it a problem with this particular daily? Will this happen on Ext4?

Update: This daily image installs without any problems when the file system is Ext4, including installing Grub into the MBR. I have just done it. So, it is an issue between Grub and the btrfs file system.

Regards.

---

### Post by The Cog on 2013-02-07
> **ventrical said:**
> [QUOTE=The Cog;12495614]I just abandoned btrfs a couple of weeks ago. It had been getting slower and slower (all the firefox sqlite tables and cached images I suspect) and so I tried a defrag. Since you can only defrag one file at a time, I did something like:
find /home - exec btrfs defrag '{}' \;
When I came back after dinner, the PC had shut down (desktop, not on batteries) and the partition would not mount - invalid superblock etc.
So I restored a backup to jfs and now it feels like a new machine, much faster.


Did you attempt to do the rollback proceedure while you were experimenting with it?[/QUOTE]No. This was on a separate /home partition. Although / was also on btrfs, I never tried to defrag it. I'm sure I rolled back a root partiton apt-get intsall once though. It's the defrag that scuppered me.

---

### Post by jerrylamos on 2013-02-08
> **The Cog said:**
> No. This was on a separate /home partition. Although / was also on btrfs, I never tried to defrag it. I'm sure I rolled back a root partiton apt-get intsall once though. It's the defrag that scuppered me.

We defrag on Microsoft XP wjocj actually seems to do something, however the result is not what you'd expect.  XP allocates files by the "scatter" method all over the disk with gaps in between, which causes a lot of grief trying to push it down to resize.  

Booting Windows 7 first thing I did after seeing it worked was to boot Ubuntu live and resize to make space for Linux.  Did not want to run Windows 7 hardly any so Windows 7 wouldn't allocate files here and there and everywhere.

Never had to defrag Ubuntu and haven't noticed the need, even when I do some resizes.

---

### Post by castrojo on 2013-02-08
> **ventrical said:**
> Attempting to rollback to quantal was an absolute and complete failure. All I have now is the Grub Rescue menu :) Thats what you get when you forget to :
sudo update grub

Did it only fail because of not upgrading grub or did the entire thing blow up? So basically if we remember to update grub then it will work?

---

### Post by grahammechanical on 2013-02-08
An update to my attempts to use btrfs.

I tried installing 12.10 on a btrfs partition. Same problem of not being able to install grub into MBR /dev/sda. This time I told it to install grub into a partition (sda9 which 12.10 was being installed on). Result = Grub rescue - unknown file system and without a Grub menu at all. Options: 

1) Press Esc to bring up the Grub menu. Failed. Still Grub rescue.
2) Get some experience using Ubuntu Secure Remix - Boot Repair utility.
3) Simply re-install Ubuntu into that btrfs partition but as Ext4.

I tried using Boot Repair. What a brilliant utility! It got me booting into my standby 12.04 on sda1. Did not pick up the other Ubuntus but update-grub has fixed that.

I am coming to the conclusion that the problem is with Grub and btrfs. On reflection and from an uneducated persons view point, I think that os-prober cannot read btrfs formatted partitions. All the folders and files seem to be on the partition but os-prober when run from Ubuntu on another partition does not detect the Ubuntu on the btrfs partition.

Regards.

---

### Post by scradock on 2013-02-09
> **grahammechanical said:**
> An update to my attempts to use btrfs.

...

I am coming to the conclusion that the problem is with Grub and btrfs. On reflection and from an uneducated persons view point, I think that os-prober cannot read btrfs formatted partitions. All the folders and files seem to be on the partition but os-prober when run from Ubuntu on another partition does not detect the Ubuntu on the btrfs partition.

Regards.

I concur. I have a perfectly sound install of 12.04 on a btrfs partition, but os-prober never sees it from another Ubuntu install. I have simply added the relevant grub menu entries using /etc/grub.d/40_custom, and it boots fine.

---

### Post by grahammechanical on 2013-02-10
> I have simply added the relevant grub menu entries using /etc/grub.d/40_custom, and it boots fine.

I cannot do this as I installed 12.10 on Ext4 over that btrfs partition. I had to do that because the boot process was more messed up than I thought. Boot Repair got me into 12.04 on sda1 but after clicking Restart the machine went into a loop = reboot - flash of purple - reboot.

An new install of something was the only way to straighten things out. I did give this new 12.10 install its own btrfs /home partition. So, that is something.

I am thinking that the solution would be to have a small /boot partition formatted as Ext4, Ext3 or even FAT32. I think that Ubuntu will run on btrfs but Grub cannot read the boot configuration file if it is on btrfs.

I am not sure that I want to do this experiment as I would then have sda11 before sda1. And that is not logical.

Regards.

---

### Post by oldfred on 2013-02-10
We have seen os-prober not see other types like LVM. On default Fedora installs you have to install the lvm2 driver and mount the Fedora partition. Then os-prober finds the Fedora.

It may be because grub2 now has all the add in modules to load drivers for just about everything. But if module is not loaded or it does not know to auto load it then it does not work?

---

### Post by ventrical on 2013-02-10
> **castrojo said:**
> Did it only fail because of not upgrading grub or did the entire thing blow up? So basically if we remember to update grub then it will work?

Good question casrojo.

Please allow me to rephrase my most recent comment. I  *assumed* that it was not updating Grub which caused the fail. I see it now that this is highly unlikely. I then assume that there would have to be a sort of weaving method with the sources.list.

  I think the actual snapshot (of original quantal) is still on the drive but I am only getting
grub rescue > prompt.

 I tried to repair it with SuperGrub rescue but that failed.

---

### Post by ventrical on 2013-02-11
Ok..yes .. the snapshot is still on the drive. I used a Quantal 'live' USB and nautilus shows it  there.

@ is the snapshot ..but it beats me how to load it at bootup. No terminal .. just Grub Rescue>

And further more I have no idea what happened to the 'upgraded' raring ringtail!

---

### Post by ventrical on 2013-02-11
And it still recognizes the drive as Btrfs format.
so why won't it boot up?

---

### Post by ventrical on 2013-02-11
> **grahammechanical said:**
> I tried again to get a Raring install on btrfs (yesterday's daily) Same result even though I choose to continue without installing a bootloader. I get an installer crashed message at the end and sudo update-grub from another Ubuntu does not detect an OS in the partition.

Is this because the format is btrfs? Or is it a problem with this particular daily? Will this happen on Ext4?

Update: This daily image installs without any problems when the file system is Ext4, including installing Grub into the MBR. I have just done it. So, it is an issue between Grub and the btrfs file system.

Regards.


I took the drive and hooked it up as secondary master. There is no way that GRUB will detect and index that (btrfs) file. It works well if you are just using apt.. but when you try to upgrade from QQ to RR then the whole install seems to go south and  grub rescue> prompt is all you get.

btw .. I am not an expert on grub rescue>

geesh...

---

### Post by grahammechanical on 2013-02-11
Thanks ventrical for explaining the mystery of the @home folder that is on my btrfs /home partition.

Well, I have given my uneducated guess that Grub cannot read the boot configuration files that are in /boot when the partition is btrfs. The Grub message is "unknown file system" after all.

I have an old IDE drive of 3.24Gb and a couple from the days when drives came in MBs. I am tempted to hook one up (as you put it), format it as Ext4 and give it a mount point of /boot when installing Ubuntu onto a btrfs partition. If that works then I will take that as evidence that Grub cannot read btrfs.

Regards.

---

### Post by |{urse on 2013-02-11
I have a bunch of old Quantum Fireball and Bigfoot drives, Think i may have to not throw them away if this is as good as it sounds.

---

### Post by ventrical on 2013-02-11
> **grahammechanical said:**
> Thanks ventrical for explaining the mystery of the @home folder that is on my btrfs /home partition.

Well, I have given my uneducated guess that Grub cannot read the boot configuration files that are in /boot when the partition is btrfs. The Grub message is "unknown file system" after all.

I have an old IDE drive of 3.24Gb and a couple from the days when drives came in MBs. I am tempted to hook one up (as you put it), format it as Ext4 and give it a mount point of /boot when installing Ubuntu onto a btrfs partition. If that works then I will take that as evidence that Grub cannot read btrfs.

Regards.

The error I am getting is:

error : file '/@/boot/grub/i386-pc/normal.mod ' not found
grub rescue>

---

### Post by cariboo on 2013-02-11
@ventrical, have you tried using btrfs with a separate ext4 boot partition? It only needs to be about 100MiB in size.

---

### Post by ventrical on 2013-02-11
> **cariboo907 said:**
> @ventrical, have you tried using btrfs with a separate ext4 boot partition? It only needs to be about 100MiB in size.


  I'll have to start all over again   because partman/ubiquity will not allow me to resize the btrfs which is 30GBs (the whole disk with the excption of a 792MB Swap Area I tried to use the swap area (for ext4) but it wants more space and there is no way I can budge it. Also , Ubiquity does recognize the existing Btrfs filesystem but does not recognize any operating system (hence why it will not give me the option to do a side by side install.

When I first ventured off on this experiment I took these steps:

Use Quantal Live USB to install base system with Btrfs format. (no updates, upgrades).
sudo apt-get install apt-btrfs-snapshot (do test to see if installed - all ok)
 **sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list**
**sudo apt-get update && sudo apt-get dist-upgrade**
Upon entering the above the snapshot was registered. My  experiment was to see if I could roll back to quantal from Raring upgrade. Of course, after the reboot it has failed. I have researched a lot of grub rescue sites .. they are mostly fragmented, do not work and likewise supergrub Rescue disk fails also.
one moment.

  I think the trick may be that the ext4 filesystem has to be installed first and then btrfs journal as a resized partition.

  Here we go again ..

---

### Post by ventrical on 2013-02-11
btw .. here is ventrical  - hard at work on my KVM rack  :) totally dedicated to U+1!!

---

### Post by ventrical on 2013-02-11
I am back at this on a larger drive/faster machine. Be back in a bit :)

---

### Post by ventrical on 2013-02-11
Ok... after upgrading to raring it registered the snapshot using apt-btrfs-snapshot.

ntu1 [42.5 kB]
Fetched 589 MB in 42min 19s (232 kB/s)                                         
Supported
Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-ypT3WB/@' in '/tmp/apt-btrfs-snapshot-mp-ypT3WB/@apt-snapshot-2013-02-11_19:14:23'
Extracting templates from packages: 100%

so all I have to do is wait until all the packages are installed and then try to 'rollback' to quantal.

edit:

 I am suspecting that there are some intracacies in the migration process from one version to another that may inadvertently break the install but otherwise the apt-btrfs-snapshot works excellently.  I am assuming this time around there may be a better chance of a rollback to quantal since I have an ext4 jounal filesystem install on the same hdd.

---

### Post by ventrical on 2013-02-11
Ok .. it seamlessly upgraded from Quantal to Raring and that horrible "sparse error" is now gone and only 'Scanning for Btrfs...'

And now for rollback to Quantal ! :)

---

### Post by ventrical on 2013-02-11
Here is the snapshot of the fresh Quantal Install:

root@ventrical-PY028AA-ABA-A1106N:~# apt-btrfs-snapshot supported
Supported
root@ventrical-PY028AA-ABA-A1106N:~# apt-btrfs-snapshot list
Available snapshots:
@apt-snapshot-2013-02-11_19:14:23
root@ventrical-PY028AA-ABA-A1106N:~#

---

### Post by ventrical on 2013-02-11
Mount the btrfs filesystem to another location:

root@ventrical-PY028AA-ABA-A1106N:~# mount /dev/sda1 /mnt
root@ventrical-PY028AA-ABA-A1106N:~# ls -l /mnt/
total 0
drwxr-xr-x 1 root root 230 Feb 11 20:22 @
drwxr-xr-x 1 root root 208 Feb 11 18:06 @apt-snapshot-2013-02-11_19:14:23
drwxr-xr-x 1 root root  18 Feb 11 17:57 @home
root@ventrical-PY028AA-ABA-A1106N:~#

---

### Post by ventrical on 2013-02-11
In order to make it boot we have to rename the snapshot:

root@ventrical-PY028AA-ABA-A1106N:~# mv /mnt/@ /mnt/@_badroot
root@ventrical-PY028AA-ABA-A1106N:~# mv /mnt/@apt-snapshot-2013-02-11_19:14:23 /mnt/@
root@ventrical-PY028AA-ABA-A1106N:~# 


and then .. reboot!! Here goes...

---

### Post by ventrical on 2013-02-11
Completely wiped out everything .. even other installs.

---

### Post by grahammechanical on 2013-02-12
> **ventrical said:**
> btw .. here is ventrical  - hard at work on my KVM rack  :) totally dedicated to U+1!!

Is that a floppy disc I see before me? Alas, poor floppy I knew them well. And again so tidy a work area. Please, please promise to never set up a photo gallery of work areas. Otherwise I will have to drop out of U+1.

Great stuff ventrical.

---

### Post by ventrical on 2013-02-12
> **grahammechanical said:**
> Is that a floppy disc I see before me? Alas, poor floppy I knew them well. And again so tidy a work area. Please, please promise to never set up a photo gallery of work areas. Otherwise I will have to drop out of U+1.

Great stuff ventrical.

  I had to use it to flash a BIOS. :)

As for Btrfs and Rolling back from one distro to another?.. does not look good. I learned my lesson.

However, if one is using Btrfs for rolling back to a previous state(somewhat like Windows System Restore) then it is an excellent file system and the apt-btrfs-snapshot is an excellent tool to use. It would save a lot of time with backups.

---

### Post by balloons on 2013-02-12
This reads like a good novel! Don't stop now ventrical..

---

### Post by ventrical on 2013-02-12
> **guitara said:**
> This reads like a good novel! Don't stop now ventrical..

;)

Thanks nick. I'll keep 'having at it' as they say in jolly olde England! :)

---

### Post by castrojo on 2013-02-12
> **ventrical said:**
> ;)
As for Btrfs and Rolling back from one distro to another?.. does not look good. I learned my lesson.


Thanks for taking one for the team, I've been wondering if this would actually work!

---

### Post by celluloid on 2013-02-12
> **ventrical said:**
> I had to use it to flash a BIOS. :)

As for Btrfs and Rolling back from one distro to another?.. does not look good. I learned my lesson.

However, if one is using Btrfs for rolling back to a previous state(somewhat like Windows System Restore) then it is an excellent file system and the apt-btrfs-snapshot is an excellent tool to use. It would save a lot of time with backups.

Good stuff Ventrical!
I've been using btrfs-apt-snapshot quiet regularly over the last few days while I'm messing with 13.04 and some pretty unstable apps and tweaking things - it's incredibly handy!

---

### Post by ventrical on 2013-02-12
> **castrojo said:**
> Thanks for taking one for the team, I've been wondering if this would actually work!


You're welcome ! Actually  this issue will not let me sleep.  Theoretically it should work. Only problem is that it takes a little downtime to get this all set up. I'll keep trying.  I am going to try a different method. I think one of the problems is , is that apt-btrfs-snapshot is also being upgraded during the raring upgrade from quantal and I am curious if this upgrade of apt-btrfs-snapshot (when run in the raring terminal) is corrupting the original btrfs format etc... so I would then have to try and pin the quantal apt-btrfs-snapshot or boot into the 3.5.x.x kernel (of quantal) and not the 3.8.0-4 of raring.

don't mind me .. I'm just writing a crude psuedo-code to myself :)

---

### Post by ventrical on 2013-02-12
Yes .. the quantal version is 0.3.3 and the latest raring version is 0.3.4.1 .. however .. I doubt now that  this is the problem.  I do not think this is a bug.. but more a protocol of some sort during migration of upgrade or some other transition process during the renaming procedure of the apt-snapshot image.

---

### Post by ventrical on 2013-02-12
> **celluloid said:**
> Good stuff Ventrical!
I've been using btrfs-apt-snapshot quiet regularly over the last few days while I'm messing with 13.04 and some pretty unstable apps and tweaking things - it's incredibly handy!


 I absolutely agree. On an installed system it is invaluable.  But just thinking ahead .. if and when during a distribution upgrade is engaged automatically or manually (and apt-btrfs-snapshot is installed) THEN it is most likely that the same results I have been experiencing during upgrade migration and rollback will be reproduced and in this particular scenario , then, it can be considered a major bug because it will bork (assumedly) any system that would attempt to roll back to a previous distro.

---

### Post by ventrical on 2013-02-13
Just for the sake of having some measure of exactness to my assumptions, I decided to take a backstep and do this process while upgrading to Quantal from Precise. I know at this statge that this may be slightly off-topic but the outcome may be beneficial to raring ringtail in the long run. If I can pin the problem  using this method then I may be able to do it with raring.

---

### Post by ventrical on 2013-02-13
So no we try ... 
sudo apt-get update && sudo apt-get upgrade

This may work because it is an apt command and not a sudo sed which changes the sources list. That may be a contributing factor to the previous fails.

Here we go .....!!

Edit:

Ok nothing happened... it did not call the Update manager.

just a sec..

---

### Post by ventrical on 2013-02-13
Ok.. I think I may have the solution.  I created a snapshot with apt:

```

Fetched 3,698 kB in 16s (226 kB/s)                                             
Supported
Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-laE5i1/@' in '/tmp/apt-btrfs-snapshot-mp-laE5i1/@apt-snapshot-2013-02-13_07:20:46'
Selecting previously unselected package sgml-data.
(Reading database ... 142243 files and directories currently installed.)
Unpacking sgml-data (from .../sgml-data_2.0.6_all.deb) ...
Selecting previously unselected package docbook-xml.
Unpacking docbook-xml (from .../docbook-xml_4.5-7ubuntu1_all.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.6~exp1ubuntu1_i386.deb) ...
Selecting previously unselected package libvte-common.
Unpacking libvte-common (from .../libvte-common_1%3a0.28.2-3ubuntu2_all.deb) ...
Selecting previously unselected package libvte9.
Unpacking libvte9 (from .../libvte9_1%3a0.28.2-3ubuntu2_i386.deb) ...
Selecting previously unselected package librarian0.
Unpacking librarian0 (from .../librarian0_0.8.1-5_i386.deb) ...
Selecting previously unselected package rarian-compat.
Unpacking rarian-compat (from .../rarian-compat_0.8.1-5_i386.deb) ...
Selecting previously unselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.9ubuntu1_i386.deb) ...
Processing triggers for doc-base ...
Scrollkeeper was installed, forcing re-registration of all documents.
Unregistering 29 doc-base files, re-registering 29 doc-base files...
Registering documents with scrollkeeper...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up sgml-data (2.0.6) ...
Setting up docbook-xml (4.5-7ubuntu1) ...
Setting up libept1.4.12 (1.0.6~exp1ubuntu1) ...
Setting up libvte-common (1:0.28.2-3ubuntu2) ...
Setting up libvte9 (1:0.28.2-3ubuntu2) ...
Setting up librarian0 (0.8.1-5) ...
Setting up rarian-compat (0.8.1-5) ...
Setting up synaptic (0.75.9ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@ventrical-PY028AA-ABA-A1106N:~# 

```

before I upgrade to quantal/raring (don't matter) , what I will do now is disable apt-btrfs-snapshot before I do the upgrade .. and this should work! :) then renable it and do the rollback.

fun! :)

---

### Post by ventrical on 2013-02-13
Update:

  I removed apt-btrfs-snapshot and then upgraded to quantal.

Thje quantal *upgrade* boots OK but is in really bad shape with graphics (so it was a borked upgrade)

The good thing is that the two *snapshots* I took prior to upgrading are still there!

root@ventrical-PY028AA-ABA-A1106N:~# apt-btrfs-snapshot list
Available snapshots:
@apt-snapshot-2013-02-13_07:20:46  
@apt-snapshot-2013-02-13_08:54:12
root@ventrical-PY028AA-ABA-A1106N:~# 

So now I am going to reinstall apt-btrfs-snapshot and once again employ the rollback procedure.

Here I am now in very *unstable* quantal upgrade:

---

### Post by ventrical on 2013-02-13
Ok... I had two partitons.. one an ext4 with Precise on it and the other a Btrfs with Precise upgraded to Quantal. I went through the *rollback* process and I got grub rescue> prompt.  However, this time the Grub Rescue CD worked and gave me back my Precise install. However, I can't seem to get the Btrfs partition to boot but it's still there !!!

I am open to suggestions or ideas.

---

### Post by ventrical on 2013-02-13
FLASH!!

I can't believe it . I did it!! I successfully rolled back to Precise 12.04.02 from a Quantal upgrade!! Also I have my other ext4 Precise install on a 200GB SATA hdd.

  I found the right solution here at this link:

[http://nicksworld69.blogspot.ca/2012/08/i-couldnt-find-simple-guide-for-this-so.html](http://nicksworld69.blogspot.ca/2012/08/i-couldnt-find-simple-guide-for-this-so.html)

or
[FONT=&quot] sudo mount -t btrfs -o subvol=@ /dev/sda6 /mnt/ [/FONT]
 [FONT=&quot] 
[/FONT]
 [FONT=&quot] sudo mount --bind /dev /mnt/dev/[/FONT]
 [FONT=&quot] 
[/FONT]
 [FONT=&quot] sudo mount --bind /proc /mnt/proc[/FONT]
 [FONT=&quot] 
[/FONT]
 [FONT=&quot] sudo chroot /mnt/[/FONT]
 [FONT=&quot] 
[/FONT]
 [FONT=&quot] grub-install --recheck /dev/sda

After running this code in terminal on the ext4 partition it gave me an error and told me to try mounting /sys

sudo mount /sys

Then a reboot and I got the error:sparse , then , scanning for Btrfs and it booted right into the *rolledback* snapshop of Precise.(but the other ext4 was not available in grub until I:

sudo udpate-grub

 This is absolutely fascinating that this can be done. I know the procedure is very tedious and painstaking but just from my own perspective it has been a milestone because I think a system restore tool has been on the Ubuntu wish list for sometime.

  I am still stunned that it worked! :)

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
ventrical@ventrical-PY028AA-ABA-A1106N:~$ apt-btrfs-snapshot supported
Sorry, you need to be root to run this program
ventrical@ventrical-PY028AA-ABA-A1106N:~$ sudo -i
root@ventrical-PY028AA-ABA-A1106N:~# apt-btrfs-snapshot list
Available snapshots:
@apt-snapshot-2013-02-13_07:20:46
root@ventrical-PY028AA-ABA-A1106N:~# 

```rolled back from previous:

And thanks everyone for your interest and comments of moral support. That  makes all the difference


[/FONT]

---

### Post by grahammechanical on 2013-02-13
Yes it does seem complicated but all it needs to become official is a couple of scripts. After all update-grub is just an x-shellscript that calls grub-mkconfig.

> #! /bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

Something similar can be done to turn this roll back to a previous version into a single command.


Well done. Superb testing!

P.S. Message for ventrical and anyone interested. I found this link with this possibly useful information.

[http://www.howtoforge.com/how-to-convert-an-ext3-ext4-root-file-system-to-btrfs-on-ubuntu-12.10]("http://www.howtoforge.com/how-to-convert-an-ext3-ext4-root-file-system-to-btrfs-on-ubuntu-12.10")

It gives instruction on how to convert ext3 or ext4 root file system to btrfs. I might test this out with my recently installed 12.10 ext4 to see if I can get a bootable 12.10 btrfs system. Which I seem unable to do. And it can be rolled back from a snapshot. The link also says this

> If you don't do this, you will get the error...

error: sparse file not allowed

That is to comment out line 93 in /etc/grub.d/00_header

---

### Post by ventrical on 2013-02-13
Thanks for the extra info grahamechanical. That will come in handy.

regards,
ventrical

---

### Post by ventrical on 2013-02-19
I had been reading up on some info about the 'other' file systems available for Ubuntu, especially XFS and JFS. It is said that XFS is the fastest. I had just done an install on an old maxtor, 20GB 4800rpm hdd and it certainly is faster than btrfs by a long shot.

  There are certainly faster desktop response times and other apps can be opened without logjam while ubuntu is doing other chores. This all on a single core non HT 2.8GHz Pentium.

  The data says that XFS filesystem is unstable , especially in power down events ... so my first experiment will be to .. well .. pull the power plug out ! Here goes.!

---

### Post by ventrical on 2013-02-19
Obviously some of the info at this link:

[http://ubuntuforums.org/showthread.php?t=246969](http://ubuntuforums.org/showthread.php?t=246969)

is inaccurate as I just pulled the plug out and it rebooted fine with no loss of data .

Now to swap the hdd onto a duplicate machine with HT capability.

---

### Post by ventrical on 2013-02-19
It is actually slower on the HT system. I think it is because I do not have the right memory installed.... but I am convinced that because the response time on the single core non HT system that XFS and JFS warrant further experimentation. So I will install raring on a faster hdd.

---

### Post by celluloid on 2013-02-20
I'm still using btrfs on my Raring install and I'm absolutely loving the apt-btrfs-snapshot functionality!
However, I'm finding that performance is degrading terribly. I'm coming across many instances where my HDD light goes solid and I appear completely I/O bound while I have to sit & wait for whatever transactions are happening to finish. 
Have you seen anything like this Ventrical or been able to work around it? I should note that I'm using a quad-core i5, 8GB DDR3 & a 256GB Vertex SSD - so this laptop is no slouch..
My mount options look like this;
compress=lzo,ssd,discard,space_cache,relatime,subvol=@ 0       1

---

### Post by ventrical on 2013-02-20
No .. I haven't seen anything of that sort yet .. but, as I had been testing I noticed that (while using Disks>Benchmark) that there is not much of a difference in data transfer speeds but this would not affect how the btrfs handles files and data.

With your machine,being quad with nitro lol, :) I would wonder if one could really tell the difference between ext4 and btrfs . I am planning to do some more experimentation with btrfs while also testing JFS and XFS.

For the normal end_user and noob  I do not think btrfs would be very helpful as it is very complex to work and  a lot of terminal entries plus there are some issues with Grub (with some machines) atm.

---

### Post by celluloid on 2013-02-20
> **ventrical said:**
> No .. I haven't seen anything of that sort yet .. but, as I had been testing I noticed that (while using Disks>Benchmark) that there is not much of a difference in data transfer speeds but this would not affect how the btrfs handles files and data.

With your machine,being quad with nitro lol, :) I would wonder if one could really tell the difference between ext4 and btrfs . I am planning to do some more experimentation with btrfs while also testing JFS and XFS.

For the normal end_user and noob  I do not think btrfs would be very helpful as it is very complex to work and  a lot of terminal entries plus there are some issues with Grub (with some machines) atm.

I've had a really good experience with btrfs so far - I had nil of any install or grub related issues at install and everything's been fairly smooth.
Performance is probably on par with ext4 - or close enough that I don't notice it. It's only when something happens in the background and I become locked up that it's a pain.

That being said, snapshots, checksumming etc are so worth it, especially when I insist on running development versions of Ubuntu :P

---

### Post by ventrical on 2013-02-20
I tired to set raring up on my dual core machine with nvidia and  it just locks up. That was the Feb 12th raring-desktop-i386.. so I zsynced today and will try again.

---

### Post by benmoran on 2013-05-01
I've been testing btrfs on-and-off for about a year or so, and just recently switched back to it for my home pc and workstation at work. The snapshotting is so convenient, and online scrubbing is awesome. 
I haven't experienced much slowdown from fragmentation in my previous tests, but I decided to give the "autodefrag" mount option a try anyhow. I have my fstab as follows:

UUID=xxxxx	/               btrfs  	subvol=@,compress=lzo		0 0
UUID=xxxxx	/home	btrfs  	subvol=@home,autodefrag		0 0

I have my / on an SSD, so fragmentation doesn't matter as much. My /home is a standard 1TB HDD, so I'm going to see how it holds up over the next 6 months or so with the autodefrag enabled. I've been filling up my HDD with recordered digital TV, so it should be a good fragmentation test.

---

### Post by ventrical on 2013-05-01
I still have it running here on one of my main installs. So far, so good. Iv'e been too busy to do any serious experimenting (other than that which I have already done). It's a real sweet install... and thanks for the bump. This reminds me that no matter how comfy-cozy that install is atm I have to now upgrade to /saucy/ and see where that goes.

---

### Post by ventrical on 2013-05-01
A smooth transition with no adverse effects.

ventrical@ventrical-AcerAMD64bitDual:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Saucy Salamander (development branch)
Release:    13.10
Codename:    saucy
ventrical@ventrical-AcerAMD64bitDual:~$

---

### Post by ventrical on 2013-05-02
I also reminded myself to install:

sudo apt-get install apt-btrfs-snapshot.

 It may come in real handy during this cycle.

---

### Post by kevpan815 on 2013-05-02
@Ventrical: I just tried Btrfs with my 128 GB Crucial M4 SSD System (Saucy) and it fixed my problem with the SSD Not being ready right away. :-)

---

### Post by ventrical on 2013-05-02
> **kevpan815 said:**
> @Ventrical: I just tried Btrfs with my 128 GB Crucial M4 SSD System (Saucy) and it fixed my problem with the SSD Not being ready right away. :-)


Great !


 I read your thread in the other forum and it reminded me to install  'apt-btrfs-snapshot' .. just in  case.  :)

Thanks 

Regards,
Ventrical

---

### Post by kevpan815 on 2013-05-02
> **ventrical said:**
> at bootup I am still getting :

error: sparse file not allowed

I got that error in Saucy.

---

### Post by kevpan815 on 2013-05-02
> **ventrical said:**
> Great !


 I read your thread in the other forum and it reminded me to install  'apt-btrfs-snapshot' .. just in  case.  :)

Thanks 

Regards,
Ventrical

Are you talking about the post where I said that my Boot Folder hit 100%? If so, you should know that there might have been other causes for that to occur, for one thing my Crucial M4 SSD is only 128 GB Total Storage Available (I plan to Upgrade to a larger size Crucial M500 SSD hopefully some time soon, possibly the 960 GB M500 SSD if I can find a Website that sells it with out charging me Illinois Sales Tax, otherwise I won't be able to afford the $599 Price Tag.

---

### Post by ventrical on 2013-05-02
> **kevpan815 said:**
> Are you talking about the post where I said that my Boot Folder hit 100%? If so, you should know that there might have been other causes for that to occur, for one thing my Crucial M4 SSD is only 128 GB Total Storage Available (I plan to Upgrade to a larger size Crucial M500 SSD hopefully some time soon, possibly the 960 GB M500 SSD if I can find a Website that sells it with out charging me Illinois Sales Tax, otherwise I won't be able to afford the $599 Price Tag.

Yes .. that is what I was referring to. apt-btrfs-snapshot will let me get back to before the bad update - somewhat like a system restore.It is also a good tool if there is major breakage from an update.  You can go back to before the update.

---

### Post by roly33 on 2013-05-03
Is it worth using btrfs over ext4?

Roland

---

### Post by ventrical on 2013-05-03
> **roly33 said:**
> Is it worth using btrfs over ext4?

Roland

 That would depend . If you are worried about borking an install then it is good to familiarize yourself with.  I actually was able to roll back from one distro to another. In all honesty I find it much easier to just  do a re-install on a badly bokred system. But it is a great tool to learn how to use.

Regards,
Ventrical

---

### Post by roly33 on 2013-05-03
> **ventrical said:**
> That would depend . If you are worried about borking an install then it is good to familiarize yourself with.  I actually was able to roll back from one distro to another. In all honesty I find it much easier to just  do a re-install on a badly bokred system. But it is a great tool to learn how to use.

Regards,
Ventrical

I might just stick with ext4 for now & try btrfs when I need to do a re-install as everything is working fine for now, but the roll back feature sounds good for working with the Development releases.

Roland

---

### Post by benmoran on 2013-05-04
I would recommend trying it out on a spare partition (or usb drive) and play around with the functionality. Especially making subvolumes and snapshots, and mounting them. Once you're familiar with how it all works, you'll know if it's worth it to you.

---

### Post by Slug71 on 2013-05-15
> **ventrical said:**
> at bootup I am still getting :

error: sparse file not allowed

I have this same issue with 13.04. Just hit any key and it will look for a BTRFS filesystem and then continue to boot.

Just curious, is any updates are made to BTRFS between now and 13.10, will my filesystem be updated with an inplace update to 13.10 or will I need to do a reinstall? Especially thinking about if new features are enabled by default.

---

### Post by ventrical on 2013-05-16
> **Slug71 said:**
> I have this same issue with 13.04. Just hit any key and it will look for a BTRFS filesystem and then continue to boot.

Just curious, is any updates are made to BTRFS between now and 13.10, will my filesystem be updated with an inplace update to 13.10 or will I need to do a reinstall? Especially thinking about if new features are enabled by default.


Good  question. I would assume however, that  an actual update to the format infrastructure would not be likely but there may be an append  of features and I would wonder how they would solve depends without having to re-install or reformatting the  storage device.

---

### Post by kevpan815 on 2013-05-16
Just a small Warning about BTRFS: When I spoke to some of the other M500 Users on Crucial's SSD Forum, They said that they do NOT recommend using BTRFS yet as it is less than 5 years old, and may Trash your SSD!

---

### Post by cariboo on 2013-05-16
> **kevpan815 said:**
> Just a small Warning about BTRFS: When I spoke to some of the other M500 Users on Crucial's SSD Forum, They said that they do NOT recommend using BTRFS yet as it is less than 5 years old, and may Trash your SSD!

Was there any explanation as to why and how, this is supposed to happen, as I'm sure if this is true the developers would like to know about it.

---

### Post by kevpan815 on 2013-05-16
I am not sure why this particular user said all these things but he was one of the Veterans of the Forum and he made a reference to BTRFS as still being Experimental in Nature when compared to EXT 4.0. He instead recommended that I use EXT 4.0 with a Swap File.

---

### Post by kevpan815 on 2013-05-16
I did tell him that I had no Severe problems with BTRFS and that I planned to continue using it by the way! :-)

---

### Post by ventrical on 2013-05-17
> **kevpan815 said:**
> I am not sure why this particular user said all these things but he was one of the Veterans of the Forum and he made a reference to BTRFS as still being Experimental in Nature when compared to EXT 4.0. He instead recommended that I use EXT 4.0 with a Swap File.

  I have found 'btrfs' to be one of the more stable formats (with some added speed).  It also has the advantage of a system restore tool (apt-btrfs-snapshot) where a user can  roll back to a previous mirror of itself. I was also able to roll-back from one distribution (quantal) to a previous fresh install (precise). No other file format offers this capability. It is exclusive to BTRFS. Therefore it is a *power-tool* for developers and testers alike. 

  I did have some glitches with GRUB on a few occasions but GRUB rescue disk quickly solved that problem.

---

### Post by ventrical on 2013-05-18
Thankfully, on one of my faster machines and an install (partition) that I have been working (building) on from since Oneric, I had installed the BTRFS filesystem and enabled it quite some time ago. Yesterday I updated and got the 3.9.0-2 kernel and the desktop was smoked after a hard shutdown. Also, fortunately for me, I have a KVM which makes it easier to study and apply the btrfs code needed to do a rollback on any given machine (within the array that had btrfs installed). This saved me hours of downtime trying to troublshoot and eventually most probably having to do a fresh install. apt-btrfs-snapshot took me back to a more stable time.Also, I had not turned off the tool and so each time I had update/upgraded I have a snapshot at those stages so I can literally switch between snapshots.
Edit:

But I was not able to get the Unity Panel  in saucy for whatever reason. Started another thread on that.

---

### Post by benmoran on 2013-05-18
> **Slug71 said:**
> Just curious, is any updates are made to BTRFS between now and 13.10, will my filesystem be updated with an inplace update to 13.10 or will I need to do a reinstall? Especially thinking about if new features are enabled by default.

Just by matter of using the newer Kernel, the filesystem will be automatically "upgraded". 
If you create a btrfs filesystem with Ubuntu 12.04 for example, and then mount it with a 13.04 live USB, you'll see some references to this in the /var/log/syslog (or dmesg output). I forget exactly off the top of my head, but you'll see the system detecting the older format and handling it seamlessly.
Also, I've done this is reverse as well. You can usually still mount a newer btrfs filesystem with an older kernel without trouble. I think for now it's unlikely to break compatibility.

---

### Post by Slug71 on 2013-05-20
> **ventrical said:**
> Good  question. I would assume however, that  an actual update to the format infrastructure would not be likely but there may be an append  of features and I would wonder how they would solve depends without having to re-install or reformatting the  storage device.

> **benmoran said:**
> Just by matter of using the newer Kernel, the filesystem will be automatically "upgraded". 
If you create a btrfs filesystem with Ubuntu 12.04 for example, and then mount it with a 13.04 live USB, you'll see some references to this in the /var/log/syslog (or dmesg output). I forget exactly off the top of my head, but you'll see the system detecting the older format and handling it seamlessly.
Also, I've done this is reverse as well. You can usually still mount a newer btrfs filesystem with an older kernel without trouble. I think for now it's unlikely to break compatibility.

Thanks.

I don't like doing new installs on my production machines every release. Prefer to wait and stick to LTS releases. If I do upgrade between LTS releases, I usually do in-place upgrades. So would be nice to take advantages of updates/features without having to do a reinstall unless I really have to. Becomes a PITA trying to stay on top of numerous devices/machines and testing... 


Anyway, 13.04 is notably faster on my Netbook over 12.10. Not sure if it's the OS or BTRFS or both, but I'm happy. Now on to 13.10.

---

### Post by ventrical on 2013-06-05
I just had a major btrfs crash on one of my raring installs.  I think it was prompted by intermittent power supply problems with connector. That install is now locked in a frozen , perpetual install.  I cannot uninstall apt-btrfs-snapshot nor can I update/upgrade current install but I can roll_back to old_root, however, rolling back does not fix btrfs lock problem. I will try Recovery mode/mount and see if I can update from there.

---

