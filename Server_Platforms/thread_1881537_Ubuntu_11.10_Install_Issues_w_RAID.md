---
title: "Ubuntu 11.10 Install Issues w RAID"
date: 2011-11-15
forum: Server Platforms
---

### Post by jason2713 on 2011-11-15
Hi All -
Any help would be greatly appreciated.  I am attempting to install Ubuntu 11/10 onto a server I've custom built and I'm having issues setting up the partitioning.


Here is the hardware set up I'm attempting:
2x 250GB HDDs in a RAID1 array
7x 2T HDDs in a RAID5 array
1x 1T HDD in no RAID setup

When I attempted to install the O/S on the 250GB array, the boot sector could not be installed.  I've searched far and wide and apparently there are 4 partitions you must make.

/boot on the non-RAID HDD Size: 300MB
swap on the non-RAID HDD Size: 18GB
/ on the RAID1 Array Size: 35GB
/home on the RAID5 Array Size: 9T

This didnt' work what so ever.

So I deleted all the RAID arrays, tried to do it simple by installing Ubuntu on just a single non-RAIDed 250GB HDD with the same sizes as above, just on one hard drive.  It booted into the O/S perfectly, with no problems.

However, when I try to recreate the RAID5 array (the O/S is not installed on these drives), Ubuntu does not boot and the server just hangs after the POST.  
When I delete the RAID5 array, it boots fine again.  It's as though it doesn't know what to boot from?

My question is, I can't figure out how to install the O/S on a RAID1 array.  What am I doing wrong?  Is my partitioning making sense what so ever (I'm new to this)?  If the RAID1 array is not possible, why can I not even get it to boot when there is a RAID5 array?  What am I doing wrong?  Any help will be much appreciated and if you need more information/details, please let me know.

---

### Post by darkod on 2011-11-15
First and most important, are you using the standard desktop cd or the alternate or server cd?

If you want to install the standard desktop version but on a RAID, you need to use the alternate install cd, not the standard desktop cd. It has raid support which the desktop cd doesn't.

Of course, if installing a server system you use the server cd, that has raid support too.

Otherwise, having /boot as separate partition outside the array is only needed in RAID0 if I'm not mistaken. Since you plan to use RAID1 for the / partition, no need for separate /boot.

If you used the desktop cd I think this was the reason the bootloader install failed. Try it again with the alternate cd, it should work fine.

---

### Post by jason2713 on 2011-11-15
> **darkod said:**
> First and most important, are you using the standard desktop cd or the alternate or server cd?

If you want to install the standard desktop version but on a RAID, you need to use the alternate install cd, not the standard desktop cd. It has raid support which the desktop cd doesn't.

Of course, if installing a server system you use the server cd, that has raid support too.

Otherwise, having /boot as separate partition outside the array is only needed in RAID0 if I'm not mistaken. Since you plan to use RAID1 for the / partition, no need for separate /boot.

If you used the desktop cd I think this was the reason the bootloader install failed. Try it again with the alternate cd, it should work fine.

I believe its the desktop CD actually, is the server version free?  I'll have to look for it.

---

### Post by darkod on 2011-11-15
They are all free.

Another question is what do you plan to use the machine for, if you want it to be a server, using the server cd is the first choice. However you have to be aware that like most linux server, the default install is only a text based system, it doesn't have a GUI.

If you feel more comfortable with the desktop system and you want to add components to use it as a server, the alternate cd installs the same desktop system, but the installer is text based and it has support for raid as already said.

[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

At the bottom of the page are the links for all ISOs. Look carefully in the file name, it will say if it's desktop, alternate or server. Also, if it's 32bit or 64bit. Choose what you want.

I usually download the .torrent file, and use torrent to download, it's faster and the torrent program checks for corruption during download.

---

### Post by jason2713 on 2011-11-15
> **darkod said:**
> They are all free.

Another question is what do you plan to use the machine for, if you want it to be a server, using the server cd is the first choice. However you have to be aware that like most linux server, the default install is only a text based system, it doesn't have a GUI.

If you feel more comfortable with the desktop system and you want to add components to use it as a server, the alternate cd installs the same desktop system, but the installer is text based and it has support for raid as already said.

[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

At the bottom of the page are the links for all ISOs. Look carefully in the file name, it will say if it's desktop, alternate or server. Also, if it's 32bit or 64bit. Choose what you want.

I usually download the .torrent file, and use torrent to download, it's faster and the torrent program checks for corruption during download.

Well yea, I'll want to use the GUI version, I am attempting to install a wiki software to make it a web server.

My goal was to RAID1 the system drive and RAID5 the data drives. This is how I set up all my windows based systems.  I'll have to get this alternative CD to install it then.  Thanks so much!  I'll let you know how this goes.  Fingers crossed.

---

### Post by jason2713 on 2011-11-16
ok so the alternative CD wouldn't load when the SATA raid array is made, but boots when its deleted.

I let the CD partition the drive.

Should I not let that happen?  Im kind of at a loss.

---

### Post by jason2713 on 2011-11-16
I am struggling to figure out how to partition all these drives. 

The alternative CD does recognize the SATA RAID array.

My goal is to partition the drives as follows:
RAID5 array holds all the data and if possible, all my software installs

I am having issues understanding the different mount points:
/root
/boot
/home
swap

I put the /root, swap and /boot on the 250GB drive
I put the /home on the 9TB RAID array.

Does not work.

I figure I'm doing something obvious wrong.  Any help will be greatly appreciated.

---

### Post by darkod on 2011-11-17
Do you actually put /root as mount point? The root partition mount point is simply the '/' without the word root. They are the same.

In fact without specifying / the installer shouldn't even continue because it's the main system partition.

/home is where all users home directories will be created automatically unless you specifically create it otherwise. It's an equivalent of My Documents lets say.

/boot is where the boot files go, and doesn't need to be very large. In reality, you don't actually need to use it these days, I think it was more useful earlier.

swap is temporary space on the HDD that the system uses if the RAM gets full, same like the swap file in windows only in linux is a separate partition on the HDD (it can also be a file, by default it's partition). With a lot of RAM you can also use the system without it but it's nice to have it if you have the space. On desktop/laptop it's mostly used for putting the computer into sleep, the data is guarded there but you don't put servers to sleep...

Can you somehow take a photo of the partitioning step when you are all done and just before you click Finished to close that step, so we can have a better look how you are trying to set it up and where might be the error? Post it here.

---

### Post by jason2713 on 2011-11-17
> **darkod said:**
> Do you actually put /root as mount point? The root partition mount point is simply the '/' without the word root. They are the same.


Yea, no /root, just /

> **darkod said:**
> 
/home is where all users home directories will be created automatically unless you specifically create it otherwise. It's an equivalent of My Documents lets say.

OK, well if I want the /home on the RAID5 volume, I take it I specify it to go there then, which is exactly what I did.

> **darkod said:**
> 
/boot is where the boot files go, and doesn't need to be very large. In reality, you don't actually need to use it these days, I think it was more useful earlier.

OK, well that's just what I read.  And since it wasn't booting after the POST of the server, I just figured it needed it.

> **darkod said:**
> 
swap is temporary space on the HDD that the system uses if the RAM gets full, same like the swap file in windows only in linux is a separate partition on the HDD (it can also be a file, by default it's partition). With a lot of RAM you can also use the system without it but it's nice to have it if you have the space. On desktop/laptop it's mostly used for putting the computer into sleep, the data is guarded there but you don't put servers to sleep...

right so was basically feeling like this was a virtual RAM in Windows world.  The best practices said to make it 1.5-2x the amount of RAM you have in the machine.  Is that wrong?

> **darkod said:**
> 
Can you somehow take a photo of the partitioning step when you are all done and just before you click Finished to close that step, so we can have a better look how you are trying to set it up and where might be the error? Post it here.
Definitely will tonight when I try again.  Very much appreciate your help.

---

### Post by darkod on 2011-11-17
Yeah, 1.5 x RAM is usually the norm.

I think you got it right by putting /home to the RAID5, but in short it would go like:
1. You set up the RAID5 array from the partition you want to use for it.
2. You set up a partition on the raid device. Usually it would be ext4 type and set as mount point /home.

That's it.

---

### Post by jason2713 on 2011-11-17
> **darkod said:**
> Yeah, 1.5 x RAM is usually the norm.

I think you got it right by putting /home to the RAID5, but in short it would go like:
1. You set up the RAID5 array from the partition you want to use for it.
2. You set up a partition on the raid device. Usually it would be ext4 type and set as mount point /home.

That's it.

Awesome thanks.  Do you ever sleep?  I'm seeing all this European madness in the markets regarding Spain, Italy, and Greece.  I hope you're not mixed up in rioting and mayhem!

---

### Post by jason2713 on 2011-11-18
Ok here is how I have this set up:


On a NON-RAID 250GB volume - 
500MB /boot volume as a primary partition as EXT4
18GB swap volume as a logical partition
231GB / volume as a logical partition as EXT4

On the SATA RAID5 10TB volume - 
10TB /home volume as a logical partition as EXT4

On a NON-RAID 2TB volume -
2TB /var volume as a logical partition as EXT4


I have a spare 250GB drive I wanted to RAID1 the system drive, but just can not get it to work.

Getting an error now that:
The ext4 file system creation in partition #1 of the RAIDmd126 DEVICE #:RAIDactive device # (read-only) RAIDraid5 device #sda[5]RAIDsdb[4] device #sdc[3]RAIDsdd[2] device #sde[1]RAIDsdf[0] device #126 failed.


pictures:

Before anything is partitioned
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01502.jpg[/IMG]

After partitions are made
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01503.jpg[/IMG]

When I try to commit changes
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01505.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01508.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01509.jpg[/IMG]


I'm at a loss.

---

### Post by darkod on 2011-11-19
That message about GPT tables might be the issue. If you are asking me, I would use msdos tables on all 2TB disks. msdos can work with up to 2TB, and since you will be using them in raid anyway, gpt doesn't give you any benefits at all.

It seems you are using raid card or bios raid, not software raid. I would enter the raid setup, delete the array and remove all the raid5 created. Then I would boot with ubuntu desktop cd in live mode, open Gparted and selecting disk by disk, go into Device - Create Partition table. That creates msdos by default.

Do that for all 7 disks and you will have all of them with msdos tables. Then again go into the raid setup and create the raid5 array again.

Try the ubuntu server install again. This time I recommend creating the raid1 of 250GB as you planed originally. That way if the install succeeds you have the system as you wanted.

---

### Post by jason2713 on 2011-11-19
> **darkod said:**
> That message about GPT tables might be the issue. If you are asking me, I would use msdos tables on all 2TB disks. msdos can work with up to 2TB, and since you will be using them in raid anyway, gpt doesn't give you any benefits at all.

It seems you are using raid card or bios raid, not software raid. I would enter the raid setup, delete the array and remove all the raid5 created. Then I would boot with ubuntu desktop cd in live mode, open Gparted and selecting disk by disk, go into Device - Create Partition table. That creates msdos by default.

Do that for all 7 disks and you will have all of them with msdos tables. Then again go into the raid setup and create the raid5 array again.

Try the ubuntu server install again. This time I recommend creating the raid1 of 250GB as you planed originally. That way if the install succeeds you have the system as you wanted.

Did what you asked and still getting the same error.

1) went back into the partition manager and deleted all partitions
2) rebooted and deleted the RAID5 array
3) went back into partition manager and selected each individual 2TB drive and it asked me to make another table.  I said yes.
4) Attempted as a test, to install ubuntu without RAID5, placed /, /boot, swap on a 250GB drive.  Attempted to put the /home partition on a 2TB drive that was in that RAID5 array.  Still got the same error.

---

### Post by darkod on 2011-11-19
Hold on, not sure if we understand each other correctly. Did it ask you to MAKE another blank table, or to WRITE the changed table to the disk?

Deleting partitions and creating new ones does NOT change the partition table type. It simply deletes the list of partitions and creates a new list but with the same table type.

The easiest way I know how to do it, with GUI tool, is booting up with the desktop cd into the live mode, and using Gparted to actually CREATE a new partition table, selecting msdos as the type.

It obviously has some issue creating the ext4 filesystem for /home on the RAID5 array. If you tried for example just / and swap on the 250GB disk I guess it will install straight away. But creating the filesystem on the RAID5 array is making it choke.

It clearly said the disks have GPT table but not "fake msdos table as it should". That means it does not have some component it should. It's beyond my knowledge whether this is an error of ubuntu, or of how the RAID5 was created since you are not using ubuntu software raid for it.

One option is to simply create the raid5 array also as ubuntu software raid, not with your raid card.
Another option which will probably make that warning go away, is using msdos tables on all disks. They don't benefit from gpt anyway since they will be used in raid array.

Just make sure you actually create a new blank msdos table, not just deleting the partitions and creating new ones.

---

### Post by jason2713 on 2011-11-19
> **darkod said:**
> Hold on, not sure if we understand each other correctly. Did it ask you to MAKE another blank table, or to WRITE the changed table to the disk?

Deleting partitions and creating new ones does NOT change the partition table type. It simply deletes the list of partitions and creates a new list but with the same table type.

The easiest way I know how to do it, with GUI tool, is booting up with the desktop cd into the live mode, and using Gparted to actually CREATE a new partition table, selecting msdos as the type.

It obviously has some issue creating the ext4 filesystem for /home on the RAID5 array. If you tried for example just / and swap on the 250GB disk I guess it will install straight away. But creating the filesystem on the RAID5 array is making it choke.

It clearly said the disks have GPT table but not "fake msdos table as it should". That means it does not have some component it should. It's beyond my knowledge whether this is an error of ubuntu, or of how the RAID5 was created since you are not using ubuntu software raid for it.

One option is to simply create the raid5 array also as ubuntu software raid, not with your raid card.
Another option which will probably make that warning go away, is using msdos tables on all disks. They don't benefit from gpt anyway since they will be used in raid array.

Just make sure you actually create a new blank msdos table, not just deleting the partitions and creating new ones.

I have the desktop, server, and the alternative CD. 

I put in the desktop CD.

opening screen, I clicked install ubuntu
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01510.jpg[/IMG]

Click the Something Else option
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01511.jpg[/IMG]

I selected every hard drive listed and clicked New Partition Table... button
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01512.jpg[/IMG]

Clicked continue to make new partition table on each hard drive.  Note: Ive deleted all RAID volumes
[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01513.jpg[/IMG]

Does that put the msdos parition table?  It never gave me the option to change the type.

---

### Post by darkod on 2011-11-19
> Does that put the msdos parition table?  It never gave me the option to change the type.Uh, to be honest I don't have a clue. Just in case, do it the other way. Go with the Try Ubuntu option, not Install.
When it loads live mode from the cd, open Gparted, in the top right corner select disk by disk and create new table in the Device menu.
The window message it will show says that msdos table will be created by default, so you are 100% sure what type it will be. The message of Gparted is slightly different to the message of the install partitioner. Also there is Advanced option for creating table of another type, but in your case you want msdos.

PS. After you are done changing the table type, one way to confirm is while still in live mode, in terminal run:
sudo fdisk -l (small L)

That tool doesn't support GPT tables and it will say so for each GPT disk. So if fdisk simply lists the partitions on the disks, they are msdos. If for some (or all) of them says they have a gpt table, then that's what it detects.

---

### Post by jason2713 on 2011-11-19
> **darkod said:**
> Go with the Try Ubuntu option, not Install.
When it loads live mode from the cd, open Gparted, in the top right corner select disk by disk and create new table in the Device menu.


Right corner, the Attached Devices button is greyed out.

[IMG]http://img.photobucket.com/albums/v626/jason2713/DSC01514.jpg[/IMG]

Did I click the wrong thing?

---

### Post by darkod on 2011-11-19
> Did I click the wrong thing?Yeap. :)

1. In the Unity interface on the left click the first icon, the ubuntu logo. That will open the Dashboard.
2. In the search line enter Gparted. It will locate the Gparted program.
3. Open Gparted.
4. You can select disk by disk in the drop down top right.
5. You can create new partition tables in Device - Create Partition Table...

See screenshot of Gparted.

---

### Post by jason2713 on 2011-11-19
ah got it!  alright here goes :)   fingers crossed!

---

### Post by jason2713 on 2011-11-20
Still no dice.  I put in windows 7 installation media and went to the partitioning section, there are 2 drives that are "inactive" so I'm assuming its still seeing the RAID as still there since I divided the RAID5 10TB drive into 2x 4TB RAID5 thinking maybe 10TB is just too much.
I am using kill disk on all the drives.

---

### Post by darkod on 2011-11-20
But did you create another array after switching the tables to msdos? Or not?

I assumed you will recreate the array again. Otherwise, what I have noticed is that usually raid meta data remains on the disks, so during an install the OS might be confused whether you are using raid or not.

And I wonder whether the installation of ubuntu would work now, why testing first with win7?

---

### Post by jason2713 on 2011-11-20
> **darkod said:**
> But did you create another array after switching the tables to msdos? Or not?

I assumed you will recreate the array again. Otherwise, what I have noticed is that usually raid meta data remains on the disks, so during an install the OS might be confused whether you are using raid or not.

And I wonder whether the installation of ubuntu would work now, why testing first with win7?

I deleted the RAID5 array, went into the desktop gparted and put the msdos partition tables on each individual hard drive.

I then rebooted, recreated the RAID5 10TB drive.  Went back into the live desktop gparted and it saw the 10TB drive.  I put the msdos partition on that drive.

Booted into the alternative CD to install ubuntu.  It saw the RAID5 drive, I partitioned the 250GB as outlined previously while putting the /HOME partition on the RAID5 10TB drive.

When I went to commit the changes, I no longer received the error that we were trying to get around earlier.  But then it just hung at a blank screen.  I figured it was just taking a long time because of the sheer size of the volume, and the hard drive was working (i saw the hdd LED on the front panel going nuts), so I left it over night thinking it would be done by the morning.

well i got up this morning, the HDD light is no longer blinking and the installation is still at the blank screen.  I can hit numlock and capslock so the machine isnt' locked up, but its going no where.

---

### Post by darkod on 2011-11-20
Uh, doesn't sound good. :(
I don't have any more ideas, except maybe not using your raid card but instead using software raid. But if you want to dual boot with win7 for example you can't use software raid.

---

### Post by jason2713 on 2011-11-20
going to try the software RAID.
not trying to dual boot, i just wanted to see what windows 7 was seeing.

if this doesnt work, im out of ideas.

---

### Post by darkod on 2011-11-20
> **jason2713 said:**
> going to try the software RAID.
not trying to dual boot, i just wanted to see what windows 7 was seeing.

if this doesnt work, im out of ideas.

Since I haven't tried setting software raid after hardware raid, I'm only not sure if you need to delete all raid meta data which is on the disks now. Formatting them doesn't delete it.

You can do from desktop live mode:

sudo dmraid -E -r /dev/sda

and repeat that for all disks.

---

### Post by sesame on 2011-12-05
I was able to successfully install with RAID 1.  Check out this blog [http://www.cynick.com/2011/12/05/successfully-installing-ubuntu-11-10-with-software-raid/](http://www.cynick.com/2011/12/05/successfully-installing-ubuntu-11-10-with-software-raid/)

---

### Post by darkod on 2011-12-06
> **sesame said:**
> I was able to successfully install with RAID 1.  Check out this blog [http://www.cynick.com/2011/12/05/successfully-installing-ubuntu-11-10-with-software-raid/](http://www.cynick.com/2011/12/05/successfully-installing-ubuntu-11-10-with-software-raid/)

Slight correction of that blog. You need the small partition with the bios_grub flag set only if you use EFI booting. Otherwise, it's not needed.

---

### Post by sesame on 2011-12-06
> **darkod said:**
> Slight correction of that blog. You need the small partition with the bios_grub flag set only if you use EFI booting. Otherwise, it's not needed.

I was not able to get it to boot via BIOS no matter what.  This was the only thing that made it work for me.

---

### Post by darkod on 2011-12-07
> **sesame said:**
> I was not able to get it to boot via BIOS no matter what.  This was the only thing that made it work for me.

I don't doubt that. But still the blog should specify that this is for EFI booting because if someone uses BIOS booting it probably won't work. As far as I know.

At this moment there are many new things in the IT and it seems harder and harder to find the perfect combination of settings.
One change is msdos partition tables vs the new gpt system.
Another is EFI boot vs BIOS.

It might be that BIOS works better with msdos tables, and EFI with GPT (in that blog they are GPT). I still haven't had the occasion to "play" with different disks and all these options.
When you add RAID on top of that, it becomes even more strange. :)

---

### Post by zeljkojagust on 2011-12-07
Jason I would recommend that you boot some Live CD (Ubuntu Desktop, Konppix...), and use dd command to wipe clean all of you disks, and start the whole process again, but on clean disks. And if you don't understand mount points please check File Hierarchy System document: [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

