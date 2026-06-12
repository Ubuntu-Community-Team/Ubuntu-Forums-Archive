---
title: "Switching Installations"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-04-17
I've been testing raring on my external usb hdd, doing the apt-get update, upgrade, dist-upgrade on a daily basis. I keep it cleaned out also. :)

Once raring has been 'fully' blessed I'm positive that I'm going to use it vs 12.10 - I really have raring configured exactly how I like it and don't really want to do a fresh install. Since I can access both 12.10 and 13.04 simultaneously I can easily copy any files saved on 12.10 (/dev/sda) to 13.04 (/dev/sdb). 

I'm exploring how to 'move':confused: 13.04 from /dev/sdb to /dev/sda. I've successfully used Remastersys to backup and restore /dev/sda; is it possible to do this to move the existing /dev/sdb installation to /dev/sda? Any other suggestions? 

TIA

---

### Post by dino99 on 2013-04-17
[http://www.sudo-juice.com/how-to-clone-a-hard-drive-in-ubuntu-linux/](http://www.sudo-juice.com/how-to-clone-a-hard-drive-in-ubuntu-linux/)
[https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)
[http://askubuntu.com/questions/106527/how-to-move-ubuntu-installation-from-one-hdd-to-another](http://askubuntu.com/questions/106527/how-to-move-ubuntu-installation-from-one-hdd-to-another)

also see the "partclone" package into the archive (man partclone)

---

### Post by pfeiffep on 2013-04-17
Thanks dino99 - it appears that dd is an option albeit SLOW. I noticed in the askubuntu link Clonezilla was mentioned, since I have experience with Remastersys do you suppose it will work also?

---

### Post by cariboo on 2013-04-17
I'm a huge fan of Clonezilla, I've used it for several years to clone disks and partitions

---

### Post by oldfred on 2013-04-17
Unless you manually had to configure a few hardware settings in /etc, all your settings are in /home.

So I prefer copying /home and a nice shiny new clean copy. Then even if you have housecleaned you can be sure you have only the new version.

I actually have all data in data partitions and just install to new 25GB / (root) partitions. And I script my basic configurations or copy some settings from my old /home, but do not even reuse /home.

---

### Post by pfeiffep on 2013-04-17
@oldfred  Thanks, follow on - does /home include software installed via apt-get, software center, and Synaptics? (Maybe I mistakenly thought that software was installed in /etc)  If so what steps should I follow - I'm not a prolific scripter.

---

### Post by oldfred on 2013-04-17
If you have installed a lot of apps.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Software is installed to many places in Linux, but the download is here:

        
 Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>
But then you have to be careful of versions.

---

### Post by ping-wu on 2013-04-17
What I often did was:

1.  Boot from a LiveUSB (any live USB but NOT the usb you want to copy 13.04 from)

2.  Do mkdir /mnt/source and /mnt/target

3.  Insert the 13.04 usb and mount the 13.04 usb and the hard drive (preferably after you have created a new partition) onto /mnt/source and /mnt/target, respectively

4.  Do: rsync -a /mnt/source/ (there must be a slash!) /mnt/target

5.  Do a blkid command from a terminal, write down the UUID of the partition in which you have copied 13.04 to

6.  Use gedit to change the UUID of your just copied partition to the correct UUID shown in step 5 in the two files: /mnt/target/etc/fstab and /mnt/target/boot/grub/grub.conf

7.  Do chroot to /mnt/target and run the update-grub command

8.  Exit chroot, eject the 13.04 USB, and Install the bootloader into MBR by:

      sudo grub-install --boot-directory=/mnt/target/boot  /dev/sda

9.  Restart your machine


I know I am getting you totally confused.  I apologize.  I will write a more user-friendly version when I have time, but in the meantime, I am sure others will provide an easier solution.

---

### Post by pfeiffep on 2013-04-17
All, I'm thinking now that my proposal of using Remastersys maybe isn't such a good idea ... although I'm wondering what is the major difference between Clonezilla and Remastersys?
I appreciate the input thus far and the lack of direct response to Remastersys is now motivation for me to TRY to use it. This entire laptop is just a throw away anyhow so I have absolutely nothing to loose and experience to gain.

---

### Post by oldfred on 2013-04-17
I thought Remastersys had not been maintained recently, but I do not use it so I am not totally up to date.

But any image copy from one system to another does require changing UUIDs as you cannot have the same UUID in two drives connected at the same time. And then you have to edit fstab with new UUIDs and totally reinstall grub2 so it will reinstall to same drive.

---

### Post by ping-wu on 2013-04-17
> **pfeiffep said:**
> All, I'm thinking now that my proposal of using Remastersys maybe isn't such a good idea ... although I'm wondering what is the major difference between Clonezilla and Remastersys?
I appreciate the input thus far and the lack of direct response to Remastersys is now motivation for me to TRY to use it. This entire laptop is just a throw away anyhow so I have absolutely nothing to loose and experience to gain.

Actually I have been using Remastersys for some of my machines, and it has been pretty good to me.  The only thing you need to be aware of is that when adding the Remastersys repository, you need to change "raring" to "precise" (I suspect you already knew that).  For some machines in which the backlight doesn't work without some workaround, Remastersys is pretty much the only way to install Ubuntu properly.

 The reason I am using the "cp (or rsync) -a" command to duplicate a Ubuntu installation from a mounted partition to another mounted but virgin partition, is that, for production machines, I want to have exact copy.  I feel very confident that Remastersys has done a very good job (!!!)  But sometimes a copying job is much easier to do.  Typically, I copy a fully updated installation to an external drive, and then copy the entire directory to a target, freshly reformatted partition.

---

### Post by cariboo on 2013-04-17
> **pfeiffep said:**
> All, I'm thinking now that my proposal of using Remastersys maybe isn't such a good idea ... although I'm wondering what is the major difference between Clonezilla and Remastersys?
I appreciate the input thus far and the lack of direct response to Remastersys is now motivation for me to TRY to use it. This entire laptop is just a throw away anyhow so I have absolutely nothing to loose and experience to gain.

The real difference between Remastersys and Clonezilla, is that Remastersys allows you to create a bootable live cd/dvd of your installation, while Clonezillz allows you to backup an installation to another location, or create an exact duplicate of your installation, on a different partition/disk

> **pfeiffep said:**
> @oldfred  Thanks, follow on - does /home include software installed via apt-get, software center, and Synaptics? (Maybe I mistakenly thought that software was installed in /etc)  If so what steps should I follow - I'm not a prolific scripter.

No packages/programs are installed in /etc, that directory is used for system-wide configuration files. The majority of packages/programs are install to either /usr/bin or /usr/sbin. Personal configurations for programs are kept in /Home/$USER.

---

### Post by pfeiffep on 2013-04-18
> **oldfred said:**
> I thought Remastersys had not been maintained recently, but I do not use it so I am not totally up to date.

But any image copy from one system to another does require changing UUIDs as you cannot have the same UUID in two drives connected at the same time. And then you have to edit fstab with new UUIDs and totally reinstall grub2 so it will reinstall to same drive.

Thanks ofdfred - Perhaps you can point me in the direction to perform the UUID trick.  I tried remastersys and I believe it failed due to /dev/sdb = usb as it never completed making the image. I needed to install the older version. I'll test this later from raring on an internal drive!

I tried clonezilla and it had to be started in other than normal mode I suppose do to incompatible graphics - it failed possibly because the source drive is a bit larger than destination. I'll test this later by cloning to a slightly larger drive.

I reverted to dd and it worked! After finishing the system booted just fine - performed some tests (first of which was updating grub) all passed EXCEPT gparted reports this a unallocated space. I suspect because of the identical UUIDs. GRUB2 works, system updated just fine using apt-get. I'm surprised that I can boot and run with the entire drive listed as unallocated. :confused: I'm posting this from this *'magic'* system.

Once again loosing anything is not a concern no matter the outcome - this is my 'learning machine' I'm gaining experience. 

Output of blkid, df -h, and fdisk -l commands:
```
pfeiffep@de:~$ blkid
/dev/sda1: UUID="b1d2880c-303a-4315-ac6b-d5f488ec47ac" TYPE="ext4" 
/dev/sda5: UUID="e1f6ce5b-a8f9-48c3-993b-1c957adc89f8" TYPE="ext4" 
/dev/sda6: UUID="c866f67a-f1e6-409e-b8fd-c39b845f081c" TYPE="swap" 
pfeiffep@de:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.1G  3.3G  5.4G  39% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            989M  8.0K  989M   1% /dev
tmpfs           201M  788K  201M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1005M  844K 1004M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda5        23G  7.8G   14G  36% /home
pfeiffep@de:~$ sudo fdisk -l


Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2db9


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19648511     9823232   83  Linux
/dev/sda2        19650558    78241791    29295617    5  Extended
/dev/sda5        19650560    68476927    24413184   83  Linux
/dev/sda6        68478976    78241791     4881408   82  Linux swap / Solaris

```


Thanks to all for their input!

---

### Post by dino99 on 2013-04-18
to get uuid(s) list:

> sudo blkid

---

### Post by pfeiffep on 2013-04-18
Thanks dino99, apparently blkid doesn't require sudo - both methods on this single hdd system produced the same outcome

---

### Post by pfeiffep on 2013-04-19
Thank You all for your postings and willingness to help. I carefully considered all advice and merged that with my 40+ years computing experience.

1)[ Remastersys]("http://www.remastersys.com/") does not work on my 13.04 installation as it fails to finish creating the ISO file with a message process was interrupted. I mistakenlythought this was due to USB external HDD, but had the same error on13.04 from internal. In all fairness to Remastersys I used an old version.

2) [Clonezilla]("http://clonezilla.org/")  worked perfectly when cloning from /dev/sda to /dev/sdb (sdb isslightly larger in size); empirically this indicates my assumption oflarger to smaller (albeit a couple of Mb) was the cause of earlierfailure. Much faster than dd.

3) Munged partition was easily repairedby using [sfdisk]("http://www.rodsbooks.com/missing-parts/").

4) dd copying individual partitionsworked perfectly, but was slower than Clonzilla.

**Next Steps**
&#8211; after raring is fully blessed I'mgoing to follow oldfred's advice to perform a fresh install.
&#8211; install the correct version ofRemastersys &#8211; I had 3.0.4-1

[TABLE="width: 463"]
[TR]
[TD="width: 62"]**[FONT=inherit]Distro[/FONT]**[/TD]
[TD="width: 126"]**[FONT=inherit]Release[/FONT]**[/TD]
[TD="width: 263"]**[FONT=inherit]Remastersys[/FONT]**[/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Ubuntu[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]10.04 Lucid[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for ubuntu 3.0.4-2[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Ubuntu[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]10.10 Maverick[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for ubuntu 3.0.4-2[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Ubuntu[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]11.04 Natty[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for ubuntu 3.0.4-2[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Ubuntu[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]11.10 Oneric[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for ubuntu 3.0.4-2[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Ubuntu[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]12.04 Precise[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for ubuntu 3.0.4-2[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Ubuntu[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]12.10 Quantal[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for ubuntu 3.0.4-2[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]**[FONT=inherit]Ubuntu[/FONT]**[/TD]
[TD="width: 126"]**[FONT=inherit]13.04 Raring[/FONT]**[/TD]
[TD="width: 263"]**[FONT=inherit]remastersys            for ubuntu 3.0.4-2[/FONT]**[/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Debian[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]Squeeze[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for debian 2.0.24-1[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Debian[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]Wheezy[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for debian 3.0.0-1[/FONT][/TD]
[/TR]
[TR]
[TD="width: 62"]            [FONT=inherit]Debian[/FONT][/TD]
[TD="width: 126"]            [FONT=inherit]Testing[/FONT][/TD]
[TD="width: 263"]            [FONT=inherit]remastersys for debian 3.0.0-1[/FONT][/TD]
[/TR]
[/TABLE]

---

### Post by ping-wu on 2013-04-19
It's probably not very fair to summarily dispose off Remastersys.  I have successfully made backup iso images from VirtualBox and USB drive.  Some tweaking of the configuration is required if your system is not a "typical" system.

If you're running Remastersys from a USB stick, you probably need to write the output image to a different drive (preferably on a mounted hard drive partition).  Then you need to "exclude" certain partitions, especially the partition that is going to contain your image, from the source.  Otherwise the image would exceed the 4 GB vfat limit, causing the process to fail.

Remastersys is pretty much a one-person operation and is much more powerful than I could have expected.  It's probably not easy if you have a non-typical system, but again if your system is atypical, it takes some learning curve to make it work, just like everything else.

Ed.: Actually, because of the need to change UUIDs, it is way easier to use Remastersys to clone an installed Ubuntu to another partition/drive.  And I am greatly indebted to its creator!  The main reason I am not using it as often for my own work is that I have mastered the process of automatically modify UUIDs in the cloned partition.  If anyone wants to create a custom-made Ubuntu iso, for one's own consumption or to spread the Ubuntu gospel, nothing beats Remastersys.

---

### Post by pfeiffep on 2013-04-19
> [COLOR=#000000]It's probably not very fair to summarily dispose off Remastersys. I have successfully made backup iso images from VirtualBox and USB drive. Some tweaking of the configuration is required if your system is not a "typical" system.[/COLOR]

I think you may have missed (or misunderstood) some of my post. I certainly did NOT *'summarily dispose'* - quite the contrary I went to the site and posted that exact version to use! Additionally I use Remastersys frequently on both of my systems!

> [COLOR=#000000]In all fairness to Remastersys I used an old version.
[/COLOR][B]Next Steps
&#8211; after raring is fully blessed I'm going to follow oldfred's advice to perform a fresh install.[/B][B]
&#8211;[COLOR=#ff0000] install the correct version of Remastersys [/COLOR]&#8211; I had 3.0.4-1[/B]

---

### Post by ping-wu on 2013-04-19
Sorry, I was not talking about you, I was criticizing myself.  You were the one who brought up Remastersys to our attention.  It is a great utility program, and is one of many great strengths of Ubuntu.  Apologize I did not explicitly make it clear.  My bad.

---

### Post by pfeiffep on 2013-04-19
> **ping-wu said:**
> Sorry, I was not talking about you, I was criticizing myself.  You were the one who brought up Remastersys to our attention.  It is a great utility program, and is one of many great strengths of Ubuntu.  Apologize I did not explicitly make it clear.  My bad.

We're good:cool:, the latest version of remastersys created the .iso file on my Dell laptop just fine! Instead of the gui version I executed from cli...just executing the command without options provides a short, comprehensive set of instructions. Last step - wait for final release and perform clean install!

---

