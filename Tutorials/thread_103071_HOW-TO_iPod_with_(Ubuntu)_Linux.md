---
title: "HOW-TO iPod with (Ubuntu) Linux"
date: 2005-12-13
forum: Tutorials
---

### Post by KingOfNowhere on 2005-12-13
Using an iPod with (Ubuntu) Linux
-----------------------------------------

			By KingOfNowhere

This is a How-To for using the Apple iPod with Ubuntu Linux. For reference, my machine is an x86 running Ubuntu 5.10 (Breezy Badger). This How-To assumes that you are using USB to connect the iPod to your system and that the iPod is Windows Format (FAT32). Linux support for the iPod is still in its early stages and not all of the features of the iPod are usable. However, it is possible to use any iPod with Linux, but not all iPod models are created equally.

*UPDATE 2/22/06*
I have made some revisions to state the recent support changes. 
*UPDATE 4/19/06*
Formatting Revisions

------------------------------------
1. LINUX IPOD CAPABILITIES
------------------------------------

Here are all the different iPod Models and thier features, along with the tool needed to use the feature.

1st - 4th Gen iPods, Mini iPods, iPod Shuffle (All iPods without color screens)
-----------------------------------------------------------------
These models have Linux Support. 
FEATURE --> TOOL NEEDED

*Audio File Syncing (MP3,AAC,Audiobook)          
[INDENT]--> gtkpod[/INDENT] 
*Podcast Subscribing/Syncing
[INDENT]--> iPodder / Amarok or a simalar program (to subscribe to the Podcast) and gtkpod (to sync to iPod)[/INDENT]
*Calendar Syncing                                       
[INDENT]--> any calendar program that can "Save As" iCal files (ex. Kontact, Ximian Evolution)[/INDENT]
*Contact Syncing
[INDENT]--> any contact program that can "Save As" vCard files (ex. Kontact, Ximian Evolution)[/INDENT]
-------------------------------------------------------

iPod Photo, iPod Nano
-----------------------------------------------------------------
These models also have Linux support.  
FEATURE --> TOOL NEEDED

*Audio File Syncing (MP3,AAC,Audiobook)
[INDENT]--> gtkpod[/INDENT] 
*Album Artwork Syncing
[INDENT]--> gtkpod (cvs version)[/INDENT] 
*Photo Syncing
[INDENT]--> GPixPod or similar program[/INDENT]
*Podcast Subscribing/Syncing
[INDENT]--> iPodder / Amarok or a simalar program (to subscribe to the Podcast) and gtkpod (to sync to iPod)[/INDENT]
*Calendar Syncing
[INDENT]--> any calendar program that can "Save As" iCal files (ex. Kontact, Ximian Evolution)[/INDENT]
*Contact Syncing
[INDENT]--> any contact program that can "Save As" vCard files (ex. Kontact, Ximian Evolution)[/INDENT]
------------------------------------------------------

-------------------------------------------------------

5th Gen iPod (iPod Video) 
-----------------------------------------------------------------
The newest model of iPod is finally usable with linux. 
FEATURE --> TOOL NEEDED

*Audio File Syncing (MP3,AAC,Audiobook)
[INDENT]--> gtkpod[/INDENT] 
*Album Artwork Syncing
[INDENT]--> gtkpod (cvs version)[/INDENT] 
*Photo Syncing
[INDENT]--> GPixPod or similar program[/INDENT]
*Podcast Subscribing/Syncing
[INDENT]--> iPodder / Amarok or a simalar program (to subscribe to the Podcast) and gtkpod (to sync to iPod)[/INDENT]
*Calendar Syncing
[INDENT]--> any calendar program that can "Save As" iCal files (ex. Kontact, Ximian Evolution)[/INDENT]
*Contact Syncing
[INDENT]--> any contact program that can "Save As" vCard files (ex. Kontact, Ximian Evolution)[/INDENT]
*Video Syncing
[INDENT]--> gtkpod (cvs version)[/INDENT]
-------------------------------------------------------

Okay, so this is what can be done with and iPod and a Linux box. If the desired feature you are looking for has no tool, check the bottom of this how-to in the "Additional Features" section.

-----------------------------
2. IPOD CONNECTIVITY
-----------------------------

Well, now that we know what can be done using Linux, the first step is gaining proper connectivity between the iPod and the Linux box.

- First - 
Connect the iPod to the computer. If automount is running, your iPod may appear on the desktop, mounted, auto-magically. If this is the case, go ahead and skip to Section 3.
*Kubuntu NOTE: Kubuntu users (or KDE users) will need to install the kioslave for the ipod, then reconnect your ipod. This can be done with this command:
```

sudo apt-get install ipodslave

```

If you plug your iPod in and nothing happens, follow this section of the guide. As long as your iPod screen says do not disconnect or the Status Light is blinking (Shuffle) then the iPod has connectivity with the computer.

- Second -
type the following command:

```
dmesg
```

Toward the end of this command's output should be the device name of your iPod, it should look something like this:

```

[4301791.359000] usb 3-2: new high speed USB device using ehci_hcd and address 3
[4301791.461000] usb 3-2: configuration #1 chosen from 2 choices
[4301793.195000] SCSI subsystem initialized
[4301793.201000] Initializing USB Mass Storage driver...
[4301793.204000] scsi0 : SCSI emulation for USB Mass Storage devices
[4301793.206000] usb-storage: device found at 3
[4301793.206000] usb-storage: waiting for device to settle before scanning
[4301793.206000] usbcore: registered new driver usb-storage
[4301793.206000] USB Mass Storage support registered.
[4301798.206000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4301798.206000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4301798.216000] usb-storage: device scan complete
[4301798.385000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[4301798.386000] sda: Write Protect is off
[4301798.386000] sda: Mode Sense: 6c 00 00 08
[4301798.386000] sda: assuming drive cache: write through
[4301798.390000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[4301798.391000] sda: Write Protect is off
[4301798.391000] sda: Mode Sense: 6c 00 00 08
[4301798.391000] sda: assuming drive cache: write through
[4301798.391000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2
[4301798.408000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0

```

For this instance, the iPod is detected as /dev/sda. The /dev/sda device has 2 partitions which are:

/dev/sda1 -> iPod firmware partition (Not Important for this How-To)
/dev/sda2 -> iPod storage partition (for storing music, photos, videos, etc.)  
  
The part of the iPod that needs to be accessed is the partition /dev/sda2

- Third -
Create a folder to mount the iPod to:

```

sudo mkdir /mnt/ipod

```

Then you must edit your /etc/fstab to include your iPod:

```

sudo gedit /etc/fstab

```

Then add the following line to /etc/fstab, change /dev/sda2 to your iPod 
device if necessary

```

/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0

```

Finally, mount your iPod:

```

sudo mount /dev/sda2

```

---------------------------------------------
3. INSTALLING AND USING GTKPOD
---------------------------------------------	  

Now that your iPod is connected to your machine and correctly mounted, we need to install the nessessary tools for using it.

GTKPOD - a utility used to update an iPod - [http://www.gtkpod.org](http://www.gtkpod.org) (PROJECT HOMEPAGE)

gtkpod is the major utility for iPod usage in Linux, so we will need to install it:

```

sudo apt-get install gtkpod

```

Once the install is complete, launch gtkpod like this:

```

gtkpod

```

Using gtkpod, you can create a playlist of all the audio files you want on you iPod. There are 2 default playlists in gtkpod, Local and gtkpod. The Local playlist is to consist of your entire music library. The gtkpod playlist is to consists of the current/desired contents of the iPod. Here are a few easy steps to get started with gtkpod:

1.- Plug in iPod and mount it
2 - Open gtkpod and select "Read iTunesDB", this allows gtkpod to fetch the current contents of the iPod
3 - Add your music library to the local playlist be selecting the Local playlist and using "Add Directory"
4 - Modify the gtkpod list with the desired contents of your iPod
5 - Finally, click "Sync" or "Sync iTunesDB" to update the iPod

At this point, we are now able to connect and sync an iPod on a Linux system.

---------------------------------
4. ADDITIONAL FEATURES
---------------------------------
Here is the state of the other features of the iPod. Not all of them work yet, but progress is being made.

- Podcast Subscribing/Syncing -

This feature is possible under Linux, however there is not one app that does it all. In order to subscribe to a podcast, you need a Podcast catcher tool, like iPodder. The iPodder software just keeps track of all your podcast subscriptions and downloads new episodes. [http://ipodder.sourceforge.net](http://ipodder.sourceforge.net) (PROJECT HOMEPAGE). Once you have downloaded your podcasts, all that is left to do is to sync them with gtkpod.
*UPDATE* 
Amarok now supports Podcasts and Podcast syncing. If this is important to you, Amarok is worth checking out.

- Calendar and Contact Syncing - 

This feature can be done in Linux, as long as the programs used to handle calendars and contacts can "Save As" iCal files and vCard files. These are the only extensions the iPod will recognize. Once you have saved your calendars and contacts as the appropriate file, just copy them to the appropriate folder on the iPod:

EXAMPLE
```

mv /path/to/calendars/*.ical /mnt/ipod/Calendars/
mv /path/to/contacts/*.vcard /mnt/ipod/Contacts/

```

And that is all it takes to sync calendars and contacts on Linux.

- Album Art/Photo Syncing -

[GPixPod]("http://sourceforge.net/projects/gpixpod") is a program designed specifically for managing photos on your iPod. Using it allows you to encode, sync, and manage your ipod photo library.

- Video Syncing -

All Video features (encoding and syncing) has been covered in another, very nice how-to:

[HowTo: Encode Video for iPod Video ]("http://ubuntuforums.org/showthread.php?t=114946")

-------------------------
5. WORK-AROUNDS
-------------------------
If you are not happy with just these options, then here are the workarounds I have tried and what worked.

wine + iTunes
--------------
This doesn't work at all, don't bother.

virtual machine + Windows + iTunes
----------------------------------
This was also unsuccessful, a virtual Windows installation will not correctly identify an iPod on a USB Bus.
*UPDATE*
However I was unsuccessful with this, vibes has report that it is possible when reformatting the ipod in VMWARE. any further info on this would be welcomed.

Dual-Boot + Windows + iTunes
----------------------------
This does work but Windows needs to be installed on your machine. This does kinda defeat the purpose of this How-To but here is what I found out. I resently purcahsed an iPod Video and was upset that there was no way to sync videos with Linux. So, I used gtkpod to put all music on my iPod, rebooted, and sync'ed my videos with iTunes. This works but it is kind of a pain.

*NOTE ABOUT ITUNES* - If you use gtkpod to update your iPod, gtkpod does not use the exact same method of writing the iTunesDB file that iTunes does. So, if you use your iPod with both windows and linux, you may make your iTunesDB unreadable by gtkpod.
---------
6. END
---------

Well, that should be all you need to know to get your iPod working with Linux. I hope everyone finds this helpful.

- KingOfNowhere

---

### Post by Petrush on 2006-01-17
Thanks for a very good howto.

Do you know how to automatically sync podcasts from ipodder to gtkpod and get it to sync to the ipod? :)

It should be possible with the "advanced" section, post processing command, i think - either thought gtkpod or by gnupod_addsong (didn't get that to work though)

---

### Post by MihaiM on 2006-01-17
Banshee is also nice

---

### Post by Ninnghizidha on 2006-01-17
How can i format the hdd of my ipod with fat32? :confused:

---

### Post by Heliode on 2006-01-17
[QUOTE=Ninnghizidha]How can i format the hdd of my ipod with fat32? :confused:[/QUOTE]

When you first connect your iPod in Windows and install the iPod software, the gets formatted fat32. Not sure how to convert it to fat32 when you first connected it on a Mac though. 

Nice howto. About the video, I recall another howto in this forum which involves compiling the latest GTKPod to get video support. You might want to link to that.

---

### Post by TecnoVM64 on 2006-01-17
Use amaroK for the music syncing, it's amazing, it even copies the cover artwork :)

---

### Post by endersshadow on 2006-01-17
Just want to let you know that there *is* a way to sync videos to the iPod Video.  You can check out the HowTo [here](http://ubuntuforums.org/showthread.php?t=114946), or even on the Wiki [here](https://wiki.ubuntu.com/iPodVideo).

---

### Post by Suzan on 2006-01-17
With the new version of gtkpod (0.99.2) you can also handle artwork on your iPod. Works nicely!

---

### Post by Seaman on 2006-01-17
[QUOTE=TecnoVM64]Use amaroK for the music syncing, it's amazing, it even copies the cover artwork :)[/QUOTE]
So amaroK has no problem with iPod? Like normal Computer --> iPod-transfers?

---

### Post by ddumanis on 2006-01-17
Amarok 1.37 for Breezy works great for syncing tunes to my Shuffle. It's the latest version (a backport, I think).

---

### Post by kurokikaze on 2006-01-19
This really works great on my iPod Mini!! :)

---

### Post by berserker on 2006-01-19
[QUOTE=ddumanis]Amarok 1.37 for Breezy works great for syncing tunes to my Shuffle. It's the latest version (a backport, I think).[/QUOTE]

Where's your iPod mounted?  Mine's at /media/ipod and Amarok 1.3.7 doesn't recognize it.  Is there a way to point amarok to the correct mount point?

TIA

UPDATE:  This worked for me:

```
sudo ln -s /media/ipod /mnt/ipod
```

---

### Post by Dr Gonzo on 2006-01-20
[QUOTE=Seaman]So amaroK has no problem with iPod? Like normal Computer --> iPod-transfers?[/QUOTE]
Well, unless you use the [SVN version](http://www.ubuntuforums.org/showthread.php?t=80492&highlight=amarok+aac), you won't be able to transfer any AAC files, like from iTunes, because amaroK doesn't handle the tags yet.

Hopefully the version in Dapper will soon, and it'll be backported.

---

### Post by jetpeach on 2006-01-23
You mention the following: 
*NOTE ABOUT ITUNES* - If you use gtkpod to update your iPod, and you plug it into a Windows machine with an up-to-date iTunes, GTKPOD WILL NO LONGER READ YOUR ITUNESDB. You will need to restore your iPod and update with gtkpod (or use iTunes from that point on). 

I have this problem, could someone tell me how do I restore my ipod and set it up in linux?  Do I need to restore it in Windows again?

---

### Post by danish_demon on 2006-01-23
alright, i'm trying to move music from my ipod to my desktop, but when i try "Export Tracks from Database" i get this error message regardless of the template/format i use: "Template ('') does not match file type '/media/ipod/iPod_Control/Music/F40/UVSX.m4a'
Failed to write 'Ryan Adams-Oh My Sweet Carolina'".  In case you can't tell, the example uses a ryan adams' song :)  .

---

### Post by woodb on 2006-01-24
Is there a way to make gtkpod (99.2) automatically fetch album artwork the way Banshee or Amarok does?

I like Banshee, but I get "database locked" sqllite errors when I try and import a complete folder.  Only about 1/8th of the folder gets imported.   It also allows duplicates, as I found out when I tried to add the folder again :(

Amarok is nice as well, but the interface has quite a bit going on.  I had to mount /dev/sda2 to /mnt/ipod for it to work, but the iPod intergration seemed quite buggy (a few times it torked my itunesdb file leaving with no songs in the ipod interface, even though there were quite a few mp3s on the device).

I am hoping I don't have to manually fetch all my album artwork.

Thanks in advance for any pointers..

-Brendan

---

### Post by benplaut on 2006-01-24
surely someone read this as 'running ubuntu on an ipod' ;)

---

### Post by captain.kipper on 2006-02-11
I thought I should let peopleknow how I got on with an ipod shuffle. 

I had problems mounting the device, using the instructions (page1), but were quite easy to fix. Firstly the drive containing the mp3s was /dev/sda1 not /dev/sda2, and it was mounted by gtkpod into /media/ipod not /mnt/ipod. changing /etc/fstab with these parameters, then remounting allowed gtkpod to see the shuffle.

Perhaps gtkpod recognised the device when it installed and did the mounting bit automatically... anyway it is now working fine.



(I am running Breezy)

---

### Post by AusIV4 on 2006-02-11
What about protected songs purchased from iTMS? I have tons of music I purchased from the music store, and from what I can tell none of the linux software offers compatibility for DRMed music.

JHymn is also not a viable option. Legality aside, it won't function with accounts that have ever used iTunes 6.

Anybody have a way of syncing iPods with Protected AAC files?

---

### Post by vibes on 2006-02-12
virtual machine + Windows + iTunes
----------------------------------
This was also unsuccessful, a virtual Windows installation will not correctly identify an iPod on a USB Bus.

this does work btw, i reformatted my ipod using VMware :cool:

---

### Post by kenailes on 2006-02-17
okay, so i think something is hella goofed up on my ipd. when i type dmesg, this is what i get--notice all the errors. what the heck am i doing wrong?

[4304234.051000] USB Mass Storage support registered.
[4304239.050000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4304239.050000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4304239.058000] usb-storage: device scan complete
[4304239.262000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4304239.264000] sda: Write Protect is off
[4304239.264000] sda: Mode Sense: 6c 00 00 08
[4304239.264000] sda: assuming drive cache: write through
[4304239.267000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4304239.269000] sda: Write Protect is off
[4304239.269000] sda: Mode Sense: 6c 00 00 08
[4304239.269000] sda: assuming drive cache: write through
[4304239.269000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2
[4304239.290000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4304254.825000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304255.399000] UDF-fs: No partition found (1)
[4304255.547000] UDF-fs: No partition found (1)
[4304255.671000] Unable to identify CD-ROM format.
[4304255.728000] Unable to identify CD-ROM format.
[4304255.733000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4304255.733000] FAT: bogus logical sector size 2
[4304255.733000] VFS: Can't find a valid FAT filesystem on dev sda.
[4304255.739000] FAT: bogus logical sector size 2
[4304255.739000] VFS: Can't find a valid FAT filesystem on dev sda.
[4304255.744000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4304255.744000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4304255.744000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4304255.744000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4304255.750000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4304255.750000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4304255.750000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4304255.769000] HFS+-fs: unable to find HFS+ superblock
[4304255.775000] HFS+-fs: unable to find HFS+ superblock
[4304255.794000] VFS: Can't find a HFS filesystem on dev sda.
[4304255.799000] VFS: Can't find a HFS filesystem on dev sda.
[4304255.805000] VFS: Can't find ext3 filesystem on dev sda.
[4304255.810000] VFS: Can't find ext3 filesystem on dev sda.
[4304255.816000] VFS: Can't find an ext2 filesystem on dev sda.
[4304255.821000] VFS: Can't find an ext2 filesystem on dev sda.
[4304255.843000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4304255.850000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4304255.893000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[4304255.894000] SGI XFS Quota Management subsystem
[4304255.900000] XFS: bad magic number
[4304255.900000] XFS: SB validate failed
[4304255.906000] XFS: bad magic number
[4304255.906000] XFS: SB validate failed
[4304255.920000] JFS: nTxBlock = 3905, nTxLock = 31245
[4304259.676000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304259.684000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304259.691000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304266.180000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304266.189000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304266.196000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304272.717000] FAT: Unrecognized mount option "gid=autofs" or missing value
[4304272.751000] UDF-fs: No partition found (1)
[4304272.774000] UDF-fs: No partition found (1)
[4304272.828000] Unable to identify CD-ROM format.
[4304272.887000] Unable to identify CD-ROM format.
[4304272.892000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4304272.893000] FAT: bogus logical sector size 2
[4304272.893000] VFS: Can't find a valid FAT filesystem on dev sda.
[4304272.898000] FAT: bogus logical sector size 2
[4304272.898000] VFS: Can't find a valid FAT filesystem on dev sda.
[4304272.903000] NTFS-fs warning (device sda): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4304272.904000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4304272.904000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4304272.904000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[4304272.912000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4304272.912000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4304272.918000] HFS+-fs: unable to find HFS+ superblock
[4304272.924000] HFS+-fs: unable to find HFS+ superblock
[4304272.930000] VFS: Can't find a HFS filesystem on dev sda.
[4304272.936000] VFS: Can't find a HFS filesystem on dev sda.
[4304272.941000] VFS: Can't find ext3 filesystem on dev sda.
[4304272.946000] VFS: Can't find ext3 filesystem on dev sda.
[4304272.953000] VFS: Can't find an ext2 filesystem on dev sda.
[4304272.958000] VFS: Can't find an ext2 filesystem on dev sda.
[4304272.965000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4304272.972000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4304272.978000] XFS: bad magic number
[4304272.978000] XFS: SB validate failed
[4304272.984000] XFS: bad magic number
[4304272.984000] XFS: SB validate failed

---

### Post by KingOfNowhere on 2006-02-23
please post your /etc/fstab and are you using gnome or kde?

it seems that your ipod is being hotplugged correctly but it is unable to mount with the appropriate filesystem.

was your ipod originally formatted for windows or mac?

---

### Post by KingOfNowhere on 2006-02-23
AusIV,

i am not aware of any linux programs that support the iTMS DRM. sorry. To my knowledge, quicktime is what is used to validate the DRM of iTMS purchases.

my advice to you is to burn your purchased music to cd (using iTunes), and re-rip the tracks. this will elliminate the DRM

---

### Post by topper_harley on 2006-02-23
Is there a way to make Amarok svn automatically fetch missing ipod covers as it does with local files?

---

### Post by ddonky on 2006-02-24
This works real well with the Shuffle. 

[http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/) 

For some reason I can't click the executable to run the script, but it works great from the command line.

---

### Post by ren wins on 2006-03-20
when i start up gtkpod, i get the error "/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted."

i've got a .ext file called iTunesDB in ~/.gtkpod   (~/.gtkpod/iTunesDB.ext). it seems that, without this file, gtkpod won't remember what's on my ipod, and /media/ipod/ doesnt exist.  Can i mkdir and put iTunesDB.ext into it to make everything happy?

---

### Post by ddonky on 2006-04-01
I'm pretty sure that /media/ipod is a directory that is created by the system when it mounts your ipod. 

If you mkdir the directory then mount your ipod the system will then create and use /media/ipod2.

---

### Post by sinaen on 2006-04-09
How do you get it to work so easily in AmaroK? for me it was one of the most worriedsome programs in the list of ipod-able programs but id love to get it to work because it's my  main music-program....

---

### Post by jms830 on 2006-05-02
In order to make this howto complete, I would add the new GTKpod version w/ a howto install to the video section. There are debs that I have used for video at the following links:

[http://box.go.dyndns.org/dev/libgpod_0.3.0-1_i386.deb](http://box.go.dyndns.org/dev/libgpod_0.3.0-1_i386.deb)

[http://box.go.dyndns.org/dev/gtkpod_0.99.3-0cvs_i386.deb](http://box.go.dyndns.org/dev/gtkpod_0.99.3-0cvs_i386.deb)

all I did was install them
```
sudo dpkg -i libgpod_0.3.0-1_i386.deb
sudo dpkg -i gtkpod_0.99.3-0cvs_i386.deb
```

I haven't tried using version 0.99.4 debs but the ones above (0.99.3) do work.
-------------------------------------------------------------------------------------------
my original source that I found these links was here
[http://www.ubuntuforums.org/showpost.php?p=806170&postcount=34](http://www.ubuntuforums.org/showpost.php?p=806170&postcount=34)

---

### Post by smallguy on 2006-05-04
Did anybody have trouble copying .mp4 (video) files to their iPod video?

gtkpod doesn't seem to recognize .mp4 files!

---

### Post by endersshadow on 2006-05-04
[QUOTE=smallguy]Did anybody have trouble copying .mp4 (video) files to their iPod video?

gtkpod doesn't seem to recognize .mp4 files![/QUOTE]

See [this thread](http://ubuntuforums.org/showthread.php?t=114946) for instructions of use with the iPod Video :)

---

### Post by jms830 on 2006-05-04
if I rename my mp4 files to mpg, then gtkpod will let me put them on.

---

### Post by bugme on 2006-05-05
Anybody know anything about .m4v files?  Is it okay to change the
extension of these files to .mpg also?

---

### Post by endersshadow on 2006-05-05
[QUOTE=bugme]Anybody know anything about .m4v files?  Is it okay to change the
extension of these files to .mpg also?[/QUOTE]

Yes, or you can change them to .mov.

---

### Post by isaacf on 2006-05-05
//edit

A simple reboot fixed my problem.

---

### Post by CameronCalver on 2006-05-06
how do you unmount your ipod so it does not reck it

---

### Post by blackjack6.21.91 on 2006-05-06
a very good how-to, thank you

i'd also consider checking out Yamipod (i found gtkpod a bit confusing at first and this was very clear)

---

### Post by ChrisNTR on 2006-05-08
How can I stop Rhythm box from running every time I plug my iPod in?

---

### Post by endersshadow on 2006-05-08
[QUOTE=ChrisNTR]How can I stop Rhythm box from running every time I plug my iPod in?[/QUOTE]

System>Preferences>Removable Drives and Media

Multimedia tab.

Uncheck the iPod checkbox.

Screenshot attached :-D

---

### Post by campidg on 2006-05-14
I am having trouble loading files onto my Shuffle.  When I sychronise in gtkpod I get this error message:
> iPod directory structure must be present before synching to the iPod can be performed.
I suspect that my pod has been corupted somehow but I don't know haow to fix it.
Can anyone Help?

Cheers

Cam

---

### Post by ruudiculus on 2006-05-14
Hi,

I've got a small problem (I hope) which is I think just related to ipod access permissions.

When I plug in my ipod nano it is being automounted to /media/ipod. My dmesg is as follows (only the last few lines are different from that of the howto):

```
usb-storage: device found at 2
[4299264.353000] usb-storage: waiting for device to settle before scanning
[4299264.354000] usbcore: registered new driver usb-storage
[4299264.354000] USB Mass Storage support registered.
[4299269.354000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4299269.354000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4299269.358000] usb-storage: device scan complete
[4299269.388000] Driver 'sd' needs updating - please use bus_type methods
[4299269.391000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[4299269.392000] sda: Write Protect is off
[4299269.393000] sda: Mode Sense: 68 00 00 08
[4299269.393000] sda: assuming drive cache: write through
[4299269.417000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[4299269.418000] sda: Write Protect is off
[4299269.418000] sda: Mode Sense: 68 00 00 08
[4299269.418000] sda: assuming drive cache: write through
[B][4299269.418000]  sda: sda1 sda2
[4299269.423000] sd 2:0:0:0: Attached scsi removable disk sda
[4299269.464000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[4299269.969000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive![/B]
```

When I use gtkpod or Amarok, they both have read/write problems. they say the device is read only.

My mtab entry for the nano is as follows:
```
/dev/sda2 /media/ipod vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

Furthermore, this is what **ls -la **gives in /media
```
drwx------  6 ruud ruud 4096 1970-01-01 01:00 ipod
```

What is the nicest way to do here in order to properly automount my ipod nano for use with gtkpod? I figure I have to modify an automount setting somewhere, but where and how exactly?

Thanks in advance!

---

### Post by ruudiculus on 2006-05-14
I should note that I discovered that when I format (FAT32) my ipod in Windows and then create directories using gtkpod in Ubuntu, these directories ARE created.

Also: (probably after sync'ing) directories F00 - F19 are present, but with no content.

So it might not be a permission issue at all, but still I don't know what to do...

---

### Post by ruudiculus on 2006-05-14
I just tried to sync and 40% of my playlist seem to sync fine, but then my ipod seems to be invisible to my system.

The (auto-)mount point still exists (/media/ipod/), but I **ls /media/ipod** returns no directories.

After these 40% a message like  "read/write failed due to input/output error occurred" pops up for the resting 60%.

Is it possible that the ipod goes into some strange mode during sync'ing? I tried the same on an Ubuntu laptop I have and things are the same, so I guess it is not a hardware (interrupt related) issue.

Someone familiar with this kind of problem? (Has the nano's hold switch got to be on or off during sync'ing?)

---

### Post by ruudiculus on 2006-05-28
Someone still here? It's so quiet...

It looks as if gtkpod/nano is able to upload a few files at a time when sync'ing (instead of 4 GB at once), but then again I don't know that for sure too.

Any ideas how to solve this?
No one else having this problem with his/her ipod nano?

---

### Post by hippyjim on 2006-06-03
I keep seeing people mentioning that you need to format your iPod in windoze or Mac. My rubbish windoze laptop CD drive has died, so I can't install the software from the CD to deal with the iPod shuffle.

Can it be done from scratch on my Linux desktop box (the one with all the music)? How? I tried plugging it in, and all I get is the alternating amber and green error warning lights.

Typing dmesg gives me:

[```
4296511.865000] usb 4-1: new full speed USB device using uhci_hcd and address 103
[4296511.978000] usb 4-1: device descriptor read/64, error -71
[4296512.192000] usb 4-1: device descriptor read/64, error -71
[4296512.395000] usb 4-1: new full speed USB device using uhci_hcd and address 104
[4296512.508000] usb 4-1: device descriptor read/64, error -71
[4296512.722000] usb 4-1: device descriptor read/64, error -71
[4296512.925000] usb 4-1: new full speed USB device using uhci_hcd and address 105
[4296513.333000] usb 4-1: device not accepting address 105, error -71
[4296513.435000] usb 4-1: new full speed USB device using uhci_hcd and address 106
[4296513.843000] usb 4-1: device not accepting address 106, error -71
[4296518.615000] usb 4-1: new full speed USB device using uhci_hcd and address 107
[4296518.728000] usb 4-1: device descriptor read/64, error -71
[4296518.942000] usb 4-1: device descriptor read/64, error -71
[4296519.145000] usb 4-1: new full speed USB device using uhci_hcd and address 108
[4296519.258000] usb 4-1: device descriptor read/64, error -71
[4296519.472000] usb 4-1: device descriptor read/64, error -71
[4296519.675000] usb 4-1: new full speed USB device using uhci_hcd and address 109
[4296520.083000] usb 4-1: device not accepting address 109, error -71
[4296520.185000] usb 4-1: new full speed USB device using uhci_hcd and address 110
[4296520.593000] usb 4-1: device not accepting address 110, error -71
[4296526.365000] usb 4-1: new full speed USB device using uhci_hcd and address 111
[4296526.478000] usb 4-1: device descriptor read/64, error -71
[4296526.692000] usb 4-1: device descriptor read/64, error -71
[4296526.895000] usb 4-1: new full speed USB device using uhci_hcd and address 112
[4296527.008000] usb 4-1: device descriptor read/64, error -71
[4296532.115000] usb 4-1: new full speed USB device using uhci_hcd and address 113
[4296532.228000] usb 4-1: device descriptor read/64, error -71
[4296532.442000] usb 4-1: device descriptor read/64, error -71
[4296532.645000] usb 4-1: new full speed USB device using uhci_hcd and address 114
[4296532.758000] usb 4-1: device descriptor read/64, error -71
[4296532.972000] usb 4-1: device descriptor read/64, error -71
[4296537.865000] usb 4-1: new full speed USB device using uhci_hcd and address 116
[4296537.978000] usb 4-1: device descriptor read/64, error -71
[4296538.192000] usb 4-1: device descriptor read/64, error -71
[4296538.395000] usb 4-1: new full speed USB device using uhci_hcd and address 117
[4296538.508000] usb 4-1: device descriptor read/64, error -71
[4296538.722000] usb 4-1: device descriptor read/64, error -71
[4296538.925000] usb 4-1: new full speed USB device using uhci_hcd and address 118
[4296539.333000] usb 4-1: device not accepting address 118, error -71
[4296539.435000] usb 4-1: new full speed USB device using uhci_hcd and address 119
[4296539.843000] usb 4-1: device not accepting address 119, error -71
[4296544.615000] usb 4-1: new full speed USB device using uhci_hcd and address 120
[4296544.728000] usb 4-1: device descriptor read/64, error -71
[4296544.942000] usb 4-1: device descriptor read/64, error -71
[4296545.145000] usb 4-1: new full speed USB device using uhci_hcd and address 121
[4296545.258000] usb 4-1: device descriptor read/64, error -71
[4296545.472000] usb 4-1: device descriptor read/64, error -71
[4296545.675000] usb 4-1: new full speed USB device using uhci_hcd and address 122
[4296546.083000] usb 4-1: device not accepting address 122, error -71
[4296546.185000] usb 4-1: new full speed USB device using uhci_hcd and address 123
[4296546.593000] usb 4-1: device not accepting address 123, error -71
[4296552.365000] usb 4-1: new full speed USB device using uhci_hcd and address 124
[4296552.478000] usb 4-1: device descriptor read/64, error -71
[4296552.692000] usb 4-1: device descriptor read/64, error -71
[4296552.895000] usb 4-1: new full speed USB device using uhci_hcd and address 125
[4296553.008000] usb 4-1: device descriptor read/64, error -71

```

Any suggestions - I wanna play with my new toy!

---

### Post by Beej on 2006-06-04
I would like to know the answer too I was considering an ipod as a purchace but I gave up windows over ayear ago and don't really want to have to install it just for an initial ipod sync.

---

### Post by lukew on 2006-06-08
[QUOTE=ruudiculus]Someone still here? It's so quiet...

It looks as if gtkpod/nano is able to upload a few files at a time when sync'ing (instead of 4 GB at once), but then again I don't know that for sure too.

Any ideas how to solve this?
No one else having this problem with his/her ipod nano?[/QUOTE]

Hi, i was having this problem with breezy and dapper.

FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive! It turns out that it is a kernel issue, there are a couple of work arounds, these are mentione in the links below.

[http://gentoo-wiki.com/HARDWARE_iPod](http://gentoo-wiki.com/HARDWARE_iPod)
[http://ipodlinux.org/Mounting_on_Linux](http://ipodlinux.org/Mounting_on_Linux)


However.....

In GTKPod I went into Edit --> Edit Preferences --> General. 

Then into the section Adding/Updationg/Synching. --> Encoding (IDS, files): And selected UTF8 

This seems to have fixed it. I copied over 10 gb onto my 2nd gerneration ipod without crashing.

I hope this helps.

Luke

---

### Post by benk on 2006-06-10
Hi all, I'm having a problem with my ipod. Everything works under linux. I have a 3g ipod, Dapper detects is perfectly when I hook it up via usb, amarok can read and write to the ipod.

BUT, when I boot back into windows and use iTunes with the ipod, iTunes now crashes as soon as it detects the ipod.

This only started happening once I used amarok to write/read fromthe ipod. Has amarok fudged something on my ipod that makes it useless with iTunes now?

I'm guessing it has something to do with this:
> *NOTE ABOUT ITUNES* - If you use gtkpod to update your iPod, gtkpod does not use the exact same method of writing the iTunesDB file that iTunes does. So, if you use your iPod with both windows and linux, you may make your iTunesDB unreadable by gtkpod.

Anybody else have this problem/knows how to fix it? It would seriously be bad if I can't sync with iTunes in windows anymore...no more music store purchases, no more hooking up the ipod on a different computer...

---

### Post by Skia_42 on 2006-06-30
Has anyone been able to use gtkpod on PPC? If so are there any tricks to it? I read somewhere that .ogg files are not supported so that leaves .mp3 files. I am able to add a .mp3 file to a playlist on the iPod but when I sync the iPod it give me this message:> 
Error opening '/media/ipod/iPod_Control/Music/F38/gtkpod712591.mp3' for writing (Read-only file system).
Anyone know how to fix it?

---

### Post by ruudiculus on 2006-07-08
Hi,

I have the same problem Skia_42! My ipod nano is being auto-mounted just as my USB-memorystick does. The difference is that I can write to and read from this USB-stick, but I can't write to the ipod. Very strange...

Can it be that the embedded Operating System on the other partition of the ipod nano is preventing users from writing to the ipod?

Anyone? Any idea? (maybe some other way of mounting you'd suggest to try?)

---

### Post by Skia_42 on 2006-07-09
I was able to get rid off the read-only file system problem.
ruudiculus: I am assumuing your ipod is formatted for PPC. I booted my ipod onto my old mac and repaired the permissions. (make sure to apply these changes to the contents) When I boot my ipod onto my Ubuntu System I am the owner and that read, write and execute privledges are allowed to the owner the group and others. One more issue that you must disable journaling on your ipod using Disk Utility. (As someone already mentioned) Hope that helps...

---

### Post by ruudiculus on 2006-07-09
Thanks Skia_42,

 I'm using a normal PC with Ubuntu. I've formatted it once under Windows (just like my USB-stick) and then, when I return to Ubuntu and use GtkPod, I am able to write some things to the Ipod nano. But soon after uploading a few files to the ipod, the "this is a read-only file system" messages occur.

So my guess is that something is going wrong after formatting the ipod to FAT. When I look to the permissions I can see that All files belong to me as user and as group, with read, write and execute permissions. No other users and groups are allowed as far as I can see, so maybe you've got a point there.

I'll format the ipod nano again to see what permissions are present in the beginning. Maybe something changes using GtkPod in combination with the Apple software running on the ipod. I'll give it a try tomorrow and return here...

---

### Post by Skia_42 on 2006-07-09
> **ruudiculus said:**
> Thanks Skia_42,

 I'm using a normal PC with Ubuntu. I've formatted it once under Windows (just like my USB-stick) and then, when I return to Ubuntu and use GtkPod, I am able to write some things to the Ipod nano. But soon after uploading a few files to the ipod, the "this is a read-only file system" messages occur.

So my guess is that something is going wrong after formatting the ipod to FAT. When I look to the permissions I can see that All files belong to me as user and as group, with read, write and execute permissions. No other users and groups are allowed as far as I can see, so maybe you've got a point there.

I'll format the ipod nano again to see what permissions are present in the beginning. Maybe something changes using GtkPod in combination with the Apple software running on the ipod. I'll give it a try tomorrow and return here...
I have found that permissions can do wierd things, format it so that everyone has full permssions and see what happens.

---

### Post by Floola on 2006-07-12
floola is a new iPod manager, [http://www.floola.com/BETA](http://www.floola.com/BETA)

It's still beta but it should work.

Tomas

---

### Post by linuxted on 2006-07-13
> **Suzan said:**
> With the new version of gtkpod (0.99.2) you can also handle artwork on your iPod. Works nicely!

Is there a way to have gtkpod grab album art from mp3s that I've ripped from my CD collection?

Amorak seems to get them but I'm clueless of how to get them to the ipod.


Thanks

---

### Post by ericesque on 2006-07-13
@ floola

are you kidding me?  Who would honestly install software from a site like that?  Chumps.  That's who!  Polly wanna virus?

---

### Post by Floola on 2006-07-13
Now it has a nicer homepage: [www.floola.com](www.floola.com)

Cheers,
Tomas

---

### Post by Lord Dagoth on 2006-07-14
I keep getting this:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtkpod

```

---

### Post by ruudiculus on 2006-07-15
Lord Dagoth,

gtkpod may be in a packages repository that you haven't enabled yet.

In Synaptic Package Manager go to "Settings" --> "Repositories" to enable more repositories and try again for gtkpod.

However I'd also recommend trying Floola, it works great for me and it is an easier program than gtkpod!

Bye,
Ruud

---

### Post by Skia_42 on 2006-07-15
Hey Everyone, I started a new thread containign my problem [here]("http://ubuntuforums.org/showthread.php?t=216133") but I am not sure it was the best place to post.

My problem is that I opened up amaroK to play around with the "media device" menu. The encoding for the song titles, artists e.t.c. have changed on both the computer display of the ipod contents and the ipod itself. Anyone know how to fix this? Screenshot attatched.

---

### Post by ruudiculus on 2006-07-15
I think you'll have to use gtkpod again and set the encoding you use back
to some default or try UTF-8.

I'm not sure it is THE solution but just write down everything you change and you can always change it back to before you read this ;) 

Good luck!

---

### Post by Skia_42 on 2006-07-15
> **ruudiculus said:**
> I think you'll have to use gtkpod again and set the encoding you use back
to some default or try UTF-8.

I'm not sure it is THE solution but just write down everything you change and you can always change it back to before you read this ;) 

Good luck!

I fixed it, I simply deleted all of the tracks on the ipod, changed the encoding to UTF-8 and reimported the tracks. Thank you.

---

### Post by ruudiculus on 2006-07-17
While Floola is more intuitive and works great I still seem to have the same problem with my ipod nano as I had with Gtkpod.

The ipod nano is mounted and I can add my music, but then on a random moment adding a directory fails (somewhere halfway the progress bar) and the files in that directory that were already transferred become Orphans (probably since they're not in the iTunesDB).

Floola continues to run, but it seems that all connection to the ipod nano is gone. Unmounting the ipod nano after quitting Floola is not possible: the device is busy.

Although it is very random, could it be some kind of mounting or file transfer time-out? I've ruled out permission problems, unless the nano's small embedded operating system is taking some actions by itself during a transfer.

Could it perhaps be an Ubuntu linux problem? Since the ipod nano can't be unmounted even when Floola or Gtkpod have exit, it looks like some **file descriptor** is still in use by a process.

Is there someone who has managed to get an ipod **nano** flawlessly?

---

### Post by Lord Dagoth on 2006-07-17
I'm trying to dpwnload Floola, but it's saying it can't find the file on the server.

---

### Post by ruudiculus on 2006-07-18
I noticed that too. I've sent [www.floola.com](www.floola.com) a mail. Hopefully the download page will be up again soon.

---

### Post by Floola on 2006-07-18
link fixed.

Tomas

---

### Post by imageburn on 2006-07-20
Okay, don't have the luxury of formatting on another OS, and *now* I don't even have permission to write/delete so I can move to UTF8. Saw something earlier about this but didn't quite understand it. Posted elsewhere 
with more detail a couple'a hours ago.

---

### Post by imageburn on 2006-07-20
About changing permission, not UTF8.

---

### Post by ruudiculus on 2006-07-21
Imageburn,

If you're using Ubuntu Dapper Drake, the ipod will be automounted correctly, with access permissions for you as user. You can easily check this by plugging in a USB pen drive AND your ipod and look at the last two added lines in the **/etc/mtab** file. If the drives are treated equally, there should be no big differences between these lines. If you're unsure, post the two lines here :)

What you should do in case you want to use GtkPod or Floola is to run iTunes once on a Windows/Mac system in order to get an appropriate iTunesDB file.

Good luck!

---

### Post by imageburn on 2006-07-21
[SIZE=1][SIZE=2]Well, don't have an extra device. But here is the mtab output:[/SIZE]

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=imageburn 0 0
/dev/sda3 /media/ipod hfsplus  rw,nosuid,nodev,uid=1000,gid=1000 0 0                 


[SIZE=2] Now, I see a 'rw' as in read/write(?), but [/SIZE][/SIZE][SIZE=1][SIZE=2]when writing to the db w/ gtkpod it tells me it can't open to write. And simply opening the ipod to use as a hard drive doesn't work either.[/SIZE]
[/SIZE]

---

### Post by Saltydog17 on 2006-07-22
I am having a couple problems getting gtkpod to work:

1. Should your iPod be empty when following the instructions in the initial post?  If not,...
2. Is there a way to export my playlists and info regarding the songs on the iPod to the gtkpod local playlist so I won't duplicate songs on my hard drive?  

I have a 5G 30GB iPod that is currently full of songs.  My library is alot larger than that, so in the past I have used the checkboxes in iTunes to manage the music on my iPod (versus manually dragging playlists and songs over to my iPod).  I would like to do the same in Linux by importing the info from the iPod into gtkpod.

Any help anyone could offer would be appreciated.

---

### Post by jfefhjsdf on 2006-07-25
I get the following error:

$ sudo apt-get install gtkpod
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtkpod

I have uncommented everything in /etc/apt/sources.list

Could somebody clue me in on what is wrong?

Thank you.

---

### Post by Edward The Bonobo on 2006-07-25
Hmm.  The Floola documentation isn't quite there yet, is it?  And there's only a tiny thumbnail of a screenshot.

Has anyone used it succesfully?  Will I be able to get it to play with my 5G 'Pod?  How good is it with album art?...etc. etc.

---

### Post by Floola on 2006-07-26
Yep, docs aren't still there as I haven't enough time. Album art support will be available in next version, I'll post here when it's ready.

Tomas

---

### Post by ruudiculus on 2006-07-28
**Imageburn:**
I get the same messages as you describe! Sometimes writing to the ipod works, but sometimes not. I asked Floola about this and he says it has more likely got something to do with the (auto)mounting of the ipod or the part of the operating system that is keeping up the conversation with the mounted ipod than with the application software (Floola or GtkPod). I don't know more for now either...(but I'll find it out :p soon I hope)

**jfefhjsdf:**
Looks like a repository problem. GtkPod is in a Universe - Multiverse repository, so you should either enable this repository in Synaptics Package Manager, or you can install it using the Add/Remove applications program. If I remember correctly it will add the needed repository for you.

---

### Post by Floola on 2006-07-31
New version of Floola available! This version includes artwork support and many stability issues, including the high cpu usage problem.

Tomas

---

### Post by Edward The Bonobo on 2006-08-01
> **linuxted said:**
> Is there a way to have gtkpod grab album art from mp3s that I've ripped from my CD collection?

Amorak seems to get them but I'm clueless of how to get them to the ipod.


Thanks

Yes...but it has some wrinkles that I found by trial and error.

To add a .jpg as album art, select the track in your libray list, Right-Click and 'Change Details'.  This lets you add the art from wherever the .jpg is stored.

If you want to add it to more than one track at a time (eg a whole album) make sure you 'change all tracks simultaneously' (or some such) **before ** you select the .jpg.

You can get a .jpg to add automatically along with the .mp3 files by naming it folder.jpg (and keeping it in the same folder as the .jpg's).

What it lacks...and I hope Floola will do this better...is any way of telling whether a track has a .jpg associated with it, other than by right clicking and looking at the details.

---

### Post by Floola on 2006-08-02
New release once again!

**shuffle users**, try the reorder playback order.

How to use this feature:
enable it under preferences->advanced.

now simply change song order redragging songs in main song listbox. Please note that this works only when all artists, albums and genres are selected.

**video users**, try adding movie files to iPod.

**artwork** artwork read from files improved. Next version will be able to store artwork in mp3.

Download it here: [www.floola.com](www.floola.com)

Tomas

---

### Post by itazuki on 2006-08-04
Hey. I have my ipod setup in itunes to be used as a hard disk and xferring music from amarok to my ipod in KDE works fine but I just tried exporting my contacts from Kontact onto my nano and it's not working. I've tried exporting my contacts as multiple 2.1 vcf and 3.0 vcf files into /media/ipod/Contacts but when i safely remove the ipod after doing that and go into Extras>Contacts on the nano all that's in there is Instruction and Sample. Any thoughts? Also, I read another post in this thread that mentioned that amarok puts the album covers on your ipod. I have the photos option enabled in itunes but amarok is not copying album covers to the ipod. Is that an option I have to enable in amarok or something? Thank's in advance for your help.

---

### Post by Floola on 2006-08-06
New version of Floola available!

Added m4a support
Added notes support, you can add/remove notes to iPod. If too big they will be automatically splitted over different pages.

BTW, this version was compiled for mac and windows (98 and above) as well.

Tomas

---

### Post by cuboconojos on 2006-08-10
> **Floola said:**
> New version of Floola available!

Added m4a support
Added notes support, you can add/remove notes to iPod. If too big they will be automatically splitted over different pages.

BTW, this version was compiled for mac and windows (98 and above) as well.

Tomas

Dear Floola, Floola looks great... but when I run it (Floola for Linux), it says: "This Beta has expired get a new one... bla bla". Are you sure the version in the website is the newest one, because in a previous post you say that you fixed the high use of CPU problem, but when Floola starts, it also says "please wait..." but nothing happens and the CPU is at 100% all the time.

By the way, I try to use Floola bacause when I use Banshee, I don't know how to cpy songs FROM the iPod. Does anybody know if there's something I'm missing here.

Greettings from Chile

---

### Post by Floola on 2006-08-11
Should be fixed in a4.

BTW, guys at ipod-fun.de made a nice preview video of the windows version, so if you want to check out how it looks like see: [http://www.youtube.com/watch?v=hmESuB45Kc4](http://www.youtube.com/watch?v=hmESuB45Kc4)

Tomas

---

### Post by cuboconojos on 2006-08-12
Thanks, Tomas. I think I got confused, I thought that Floola a4 was released, that's why I asked if you had the newest version online.
So well, I'll be waiting for Floola a4... I'm sure it'll work great.

Greetings

---

### Post by Floola on 2006-08-13
Floola (a5) available! 

[LIST]
[*]WAV support added.
[*]playback should work now (ALSA required).
[*]some other minor enhancement.
[/LIST]

[http://www.floola.com](http://www.floola.com)

Tomas

---

### Post by njzillest on 2006-08-14
Thanks for the Tutorial, do you know how to rip songs from the ipod?

---

### Post by Floola on 2006-08-15
Good news everyone! Floola is now localizable! 

It's easy and FUN.

It's easy because you don't need any programming knowledge (there' a simple application that helps you do the translation).
Translation take some time as there are approximately 300 phrases to translate.

So only if really really interested:
- register to site ([http://www.floola.com](http://www.floola.com))
- email me your username

I'll activate a translator account.

Tomas

---

### Post by c1ean on 2006-08-15
Floola looks great.  Thanks :)

---

### Post by Floola on 2006-08-16
Floola (a6) available.

[http://www.floola.com](http://www.floola.com)

**I'm looking for translators**.

Tomas

---

### Post by Floola on 2006-08-18
Floola (a7) available!

Dutch and spanish translation added.

Tomas

---

### Post by Rebeca on 2006-08-19
I just tried to use Floola, but I keep getting errors... I did move the 2 libfmodex.so to usr/lib but I still get an error:

[b]Warning
Fmex error: Internal Fmod error (code #52)
No audio will be available...[/b]

Then, I tried creating/editing a playlist, and got the following:

**Event getitemsByPlsThread.Run()**

Am I doing something wrong?

---

### Post by Floola on 2006-08-20
The warning about audio is probably caused because you're not using ALSA. The other error is a bit more difficult to determine. You may contact me directly by email.

Cheers,
Tomas

---

### Post by lucidite on 2006-08-22
> **ren wins said:**
> when i start up gtkpod, i get the error "/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted."

i've got a .ext file called iTunesDB in ~/.gtkpod   (~/.gtkpod/iTunesDB.ext). it seems that, without this file, gtkpod won't remember what's on my ipod, and /media/ipod/ doesnt exist.  Can i mkdir and put iTunesDB.ext into it to make everything happy?

Well, I have this problem as well, however when I searched this thread, I didn't find the way to fix it.
How did you fix it?

---

### Post by bamend on 2006-08-22
using the thread [http://www.ubuntuforums.org/showthre...ghlight=itunes](http://www.ubuntuforums.org/showthre...ghlight=itunes)
I made the /mnt/ipod directory. I plugged the ipod in and found out the ipod is recognized as sdb2, I added this line to the /etc/fstab
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0
then I mounted the ipod with: sudo mount /dev/sda2
Now in my media folder I have two subfolders: ipod which is blank and ipod-1 which has all the information from the ipod in it. Then when I try to access the ipod from amaroK or gtkpod, neither program recognizes the ipod. What am I doing wrong? I've messed with this for two complete days and tried several different ways to do this without success. please help as I'm extremely frustrated.

---

### Post by paul20111 on 2006-08-24
(see post below)

---

### Post by paul20111 on 2006-08-24
Hi,

This thread seems to have discussed a number of problems however I, like many of the users here, was getting the "read only filesystem" error in gtkpod.  I then found this article [http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu]("http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu") which suggests that the problem lies in the FAT filesystem which can be repaired very simply by:

$ sudo dosfsck -a /dev/sdc2

(change /dev/sdc2 to which ever /dev node your ipod resides at)

This found a number of errors in the filesystem on my iPod which have crept in whilst trying out a number of linux apps for syncing with the device.  It corrects them automatically and non-destructively - all my songs remain on the ipod.  Furthermore, gtkpod now writes to the device with no probs!

I hope this works for some of you suffering the same problem!

---

### Post by imageburn on 2006-08-24
Thank you, thank you, thank you, beautiful. . .

---

### Post by Floola on 2006-08-27
Floola a9 available!

Motorola phones compatible
artwork fixed and optimized
new gui layout
many bug fixed

[http://www.floola.com](http://www.floola.com)

Enjoy,
Tomas

---

### Post by Edward The Bonobo on 2006-08-28
I'd love to try Floola...but I'm still reluctant.  2 reasons:

[LIST=1]
[*]I'm using gtkpod now.  I know that some people have had problems using gtkpod, then switching to something else, then going back to gtkpod.  Has anyone tried using gtkpod again after trying Floola?  Does it still work?
[*]This one is a moan to Tomas ;) :  In general, I am very reluctant to use any software that does not have end-user documentation.  This is not *only *because I'm a non-techie, nearly-newbie.  When developers write the user manual *at the same time* as developing, it makes them think about their software from the users' viewpoint, and they develop better software as a result.  Yes, I know that Tomas is concentrating on building a great package - but trust me - the documentation isn't a distraction.  At very minimum - some screenshots on floola.com to illustrate the basic operations would be useful. (End of moan).
[/LIST]

---

### Post by micmic on 2006-08-28
Possible bug with a10:
    with iPod mini (4Gb) -- no jpg support: when I add a directory with covers (jpg)... frozen, if there isn't jpg no problem

@Edward The Bonobo: I try gtkpod after and it works fine :)

---

### Post by ruudiculus on 2006-08-28
Mr Bonobo,

I may have a banana for you :)

I just finished writing a quick guide to Floola, which might be handy for the time being until an official Floola User Guide is released.

It can be downloaded from my site: [www.ruudbeukema.nl]("http://www.ruudbeukema.nl")

---

### Post by Edward The Bonobo on 2006-08-29
Mmm!  Tasty banana.  Thanks.

(And you know what bononos do with bananas...;) )

---

### Post by ruudiculus on 2006-08-29
I just DON'T want to know :mrgreen: 

Anyway, glad I could provide you with some help!

---

### Post by ruudiculus on 2006-08-30
Updated Floola Quick Guide available on [www.ruudbeukema.nl](www.ruudbeukema.nl)!

Comments, tips and tricks from the master himself have been added ;)

---

### Post by Sentinel on 2006-08-31
doe some reason im getting the sda3 thing instead of 2 this ipod situation is really getting on my nerves](*,) ](*,) ](*,)

---

### Post by Floola on 2006-08-31
a11 released!

Fixed several bugs (audio pop, artwork window and many more, freespace errror on startup). Added BPM column. Artwork should finally work.

Enjoy,
Tomas

---

### Post by Floola on 2006-09-10
a12 available!

artwork bug fixed
png library problem fixed
minor improvements here and there

Enjoy,
Tomas

---

### Post by Laterix on 2006-09-13
Apple released new iPod nano players. Apple's website says that you need iTunes to use them. So my question is, if I buy a 8Gb version, does it work with ubuntu at all?

---

### Post by geckomind on 2006-09-13
I dunno. Apple always says you need iTunes. Corporate crap in my opinion. I bought a 4GB green nano for my girlfriend. Will report on Ubuntu usability once it's here...

---

### Post by Laterix on 2006-09-13
> **geckomind said:**
> Apple always says you need iTunes. Corporate crap in my opinion.
I think your right, but I want to be sure before I order one.
> 
I bought a 4GB green nano for my girlfriend. Will report on Ubuntu usability once it's here...
Thanks, I'm waiting your comments impatiently. :)

---

### Post by Paul41 on 2006-09-13
> Apple released new iPod nano players. Apple's website says that you need iTunes to use them. So my question is, if I buy a 8Gb version, does it work with ubuntu at all?
I have been able to use my nano with Banshee

---

### Post by ruudiculus on 2006-09-13
My 4 GB nano works perfectly with Floola, and since the technology/communication interface will be the same for the 8GB ipod's, I'd say your 8GB ipod will just work with Floola as it does with iTunes!

---

### Post by brucevangeorge on 2006-09-15
Is this necessary for Dapper 6.06?

I can see the iPod, I can read and write from it as any other USB device... but synching with anything is messed.

---

### Post by ruudiculus on 2006-09-16
Brucevangeorge,

You have the mess up experience while using GtkPod? Or also with Floola?

I had this too at first while still using GtkPod. Sync'ing went ok for the first few MB's, but then suddenly everything stalled and the iTunes database file on the ipod was corrupted.

With Floola I never have this problem.

---

### Post by æþeling on 2006-09-18
I'm having trouble with gpixpod: I downloaded the latest version .deb (which is supposted to work with dapper according to their site), and I get an error saying "Error: Dependency is not satisfiable: python-support" (even though I have the backage "python-support" installed. What's wrong here?

---

### Post by rackne on 2006-09-18
the thing with using gktpod is that it doesnt read iTunes database properly if you have used your iPob in M$ Windows before. my iPod is one the main reasons that i still do dual-boot. if any linux distro had a good iPod and iTunes support i'd've got rid off M$ software for good long time ago.

---

### Post by ruudiculus on 2006-09-19
Already tried Floola? [www.floola.com](www.floola.com)

---

### Post by rackne on 2006-09-19
nope, i haven't but ill give it a try. thanks.

---

### Post by deldredge on 2006-09-22
Can I suggest adding "sudo modprobe -r ehci_hcd" to the original howto? I tried all sorts of things to get my shuffle to work, and it worked right off the bat, as it's supposed to, after I did that. 

I know it's a more of a general USB tip, and it's not neccessary for most people, but I think that for people just switching to ubuntu, getting their ipod to work is one of the first things. USB wouldn't even recognize that I plugged anything in until I issued that command.

---

### Post by ruudiculus on 2006-09-23
Strange that your hotplugging doesn't work as it supposed to! You're having this problem with all USB devices (e.g. memory stick, USB hub, etc)?

Why would you want to remove (modprobe's "-r" argument) the ehci_hcd module?

Please, give me a little bit more info about why you do this "remove-modprobing" except from that it just works after you do it (or give me link to the site where you found this solution, so that I can find out myself;) ). I then may indeed add it to the Floola Quick Guide!

---

### Post by deldredge on 2006-09-23
Unfortunately, I have no idea how it works. hotplugging works fine with basically everything for me except my ipod shuffle. I have a video ipod that works fine as well. When I was plugging in the shuffle, dmesg wasn't outputting anything at all. after I removed the module, it worked without any trouble at all. I got the idea from this thread, but of course there's no explanation behind it.

[http://ubuntuforums.org/showthread.php?p=1531176#post1531176](http://ubuntuforums.org/showthread.php?p=1531176#post1531176)

---

### Post by ruudiculus on 2006-09-23
OK, after some searching I found out: it seems that some USB controllers don't work properly with the ehci_hcd module loaded. This is a bug that should get fixed in the future.

For now, what you can do is:
a) sudo modprobe -r ehci_hcd every time you have restarted
b) add "blacklist ehci_hcd" to the /etc/modprobe.d/blacklist file

Option b makes sure the ehci_hcd module is unloaded every time you reboot. This should help until the problem is fixed.

I'll add this to the Floola Quick Guide too!

Bye!

---

### Post by whitegorilla on 2006-09-24
I have a problem.  I used to be able to sync my ipod using gtkpod and amarok but amarok installed an update and then amarok decided that it couldn't see my ipod.  I did something (can't remember what as it was a month ago and I went on holiday!) but it was to try and get amarok to see the ipod.  Now when I connect my ipod it's screen tells me "do not disconnect" so I know that it's connected ok and it charges, but the ipod doesn't appear on the desktop like it used to.  Any ideas?

I have an external hard drive which mounts ok, but my SD card reader no longer mounts either.

Thanks

---

### Post by ruudiculus on 2006-09-24
Have you perhaps also updated your kernel? Try an older kernel and see if it works with that one. It doesn't directly seem to be an Amarok problem...

If it works using an older kernel, try the latest kernel again and type Deldredge's suggestion in your terminal:
```
sudp modprobe -r ehci_hcd
```

---

### Post by almostlinux on 2006-09-25
New version of gtkpod 0.99.8 has been released:


[http://www.gtkpod.org/news.html](http://www.gtkpod.org/news.html)

---

### Post by sannong on 2006-09-26
I tried installing the new gtkpod from source but when I try and run it in terminal I get:

gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_device_set_mountpoint

Anybody else have the same problem?

---

### Post by pertti on 2006-09-27
> **sannong said:**
> I tried installing the new gtkpod from source but when I try and run it in terminal I get:

gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_device_set_mountpoint

Anybody else have the same problem?

Woops! Same problem here.

I really look forward to this release, since it seems that artwork support has been improved (I haven't been able to include cover artwork on my 1st gen iPod Nano yet).

---

### Post by Floola on 2006-09-27
Floola a13 is out!

A performance problem under linux was fixed, so now it should be way faster than before.
iTunes 7 compatibility added (was a problem with iPod videos only)

Enjoy,
Tomas

---

### Post by pertti on 2006-09-28
> **sannong said:**
> I tried installing the new gtkpod from source but when I try and run it in terminal I get:

gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_device_set_mountpoint

Anybody else have the same problem?

I found a solution in the [gtkpod mailing list]("http://sourceforge.net/mailarchive/forum.php?thread_id=30646345&forum_id=40459"). To fix this, first add the following line to /etc/ld.so.conf (or create that file, if doesn't exist already):

```
/usr/local/lib
```

Then run:

```
sudo ldconfig
```

And that's it. Gtkpod now runs ok on my computer, and writes album artwork to the iPod :D.

---

### Post by Compwiz on 2006-09-28
I recently updated my kernel, which prompted me to hook my iPod up to my windows machine to get the iTunes DB so banshee would be able to write to it again. before i did that, i updated iTunes, and my iPod to versions 7(iTunes) and 1.2(nano) respectively ... i get it mounted on Ubuntu, but banshee seems to have forgotten to load the iPod. iTunes works really well with it, however, banshee is still amnesiatic. it was working fine before i updated all of these things. does anyone know why the update to my ipod makes it invisible to my sinching program?

---

### Post by shanepardue on 2006-09-28
my 4g ipod will transfer files, but if it's a pretty big transfer, it will error and not allow any more changes. also, the songs it transferred before it went crazy, disappear (orphaned). i've tried floola, amarok, and gtkpod. they all do the same thing. please help!

---

### Post by pertti on 2006-09-29
> **Compwiz said:**
> I recently updated my kernel, which prompted me to hook my iPod up to my windows machine to get the iTunes DB so banshee would be able to write to it again. before i did that, i updated iTunes, and my iPod to versions 7(iTunes) and 1.2(nano) respectively ... i get it mounted on Ubuntu, but banshee seems to have forgotten to load the iPod. iTunes works really well with it, however, banshee is still amnesiatic. it was working fine before i updated all of these things. does anyone know why the update to my ipod makes it invisible to my sinching program?

Apparently, the latest firmware (1.2) changes the way in which the kind of iPod is detected. More info from two Banshee developers [here]("http://www.snorp.net/log/2006/09/14/why-i-hate-apple-still/") and [here]("http://abock.org/2006/09/14/we-need-you-and-apple-sucks-part-2/").

Banshee 0.11 was realeased a few days ago. Maybe this one will recognize your iPod correctly. 0.11 is already in Edgy Eft (due to the end of october), but no in Dapper.

If you need another program meanwhile, gtkpod worked ok with my 1.2 iPod Nano (but album artwork didn't work until last version, see previous post).

---

### Post by Compwiz on 2006-09-29
OOH ok, well i dropped banshee in favour of amarok anyway, and im liking it quite a bit, i downloaded it before i read about the new version of banshee ... oh well i might look into that new version anyway.  Thanks again for the reply and suggestions :)

---

### Post by AleXit on 2006-10-01
> **pertti said:**
> I found a solution in the [gtkpod mailing list]("http://sourceforge.net/mailarchive/forum.php?thread_id=30646345&forum_id=40459"). To fix this, first add the following line to /etc/ld.so.conf (or create that file, if doesn't exist already):

```
/usr/local/lib
```

Then run:

```
sudo ldconfig
```

And that's it. Gtkpod now runs ok on my computer, and writes album artwork to the iPod :D.

Thank you very much !!! :D

---

### Post by Floola on 2006-10-07
New version is available (b3). It's now much faster when browsing iPod content, it has a much better smart playlist decode engine and many many bug were fixed.

Enjoy,
Tomas

---

### Post by Floola on 2006-10-13
Floola beta 6 released. Various bug fixed.

---

### Post by kkuzia on 2006-10-18
I am having a problem that appears to be somewhat different from others on this thread.  First off, this HOWTO was incredibly helpful to get my iPod going, so kudos!

Onto the problem: I cannot seem to get either of my iPods (my 3G 40GB or my 512MB Shuffle) to automatically mount when I pop them in.  Anyone have any ideas on what could be wrong?  Here is my /etc/mtab:

> /dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-686/volatile tmpfs rw 0 0
/dev/sda2 /mnt/ntfs ntfs rw,uid=1000,gid=100 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdd2 /mnt/ipod vfat rw,noexec,nosuid,nodev,umask=000 0 0

Any ideas?

---

### Post by rgsproductions on 2006-10-19
I have a 60 g ipod video with 12 g of music and videos.  I can convert and format video and Itunes will transfer video.  Floola works the best , but will not transfer video.  I have tried banshee 11, gtkpod 99.4 and floola b7. Amorok and yamipod, i don't like.  
Simple question,  does any one have a solution on how to add files to ipod with out syncing the entire unit and does any program do video transfer?

---

### Post by Floola on 2006-10-21
Floola b7 available. Video upload should work now. If anybody finds other m4v or mp4 that aren't uploaded correctly please let me know via email.

[http://www.floola.com](http://www.floola.com)

Thanks!

---

### Post by rgsproductions on 2006-10-23
Not sure if this belongs here.  In response to my question about programs, Floola came out on top.  With the video issues fixed.  The program allows me to retain my purchased itunes files and the 12 gig I had on the ipod.  I dragged and dropped 400m of music and videos with no issues.  With the ffmpeg post on formatting ipod videos and Floola for transferring music, pod cast files and video, and gpixpod for photos, and ippoder for pod cast catching.  All work hand in hand on my 60g ipod video perfectly.  Even though these are way more steps than gtkpod and Itunes, my solutions have worked just as fast, with no issues and I do not have to leave linux.  

Hope this helps.

---

### Post by shizow on 2006-10-29
i have a new ipod nano second generation 8 GB
i use kubuntu edgy
i installed ipodslave
i cannot mount the ipod

```

sudo mount /dev/sdb2 /mnt/ipod/
mount: unknown filesystem type 'via_raid_member'

```

*UPDATE*
this seems to be a error in the detection of the file system type on the ipod
[http://www.nabble.com/forum/ViewPost.jtp?post=6786511&framed=y](http://www.nabble.com/forum/ViewPost.jtp?post=6786511&framed=y)

when i mount it as vfat type i can at least mount it
```

sudo mount -t vfat /dev/sdb2 /mnt/ipod/

```

but when i try to start Floola, there is still no ipod connected
any suggestions?

---

### Post by ruudiculus on 2006-10-29
Can you actually read the content on the ipod after you mounted it? (Using your file browser I mean...)

---

### Post by shizow on 2006-10-29
> **ruudiculus said:**
> Can you actually read the content on the ipod after you mounted it? (Using your file browser I mean...)

Yes
```

/mnt/ipod$ ls -l
total 64K
drwxr-xr-x 2 root root 16K Jul 20 17:10 Calendars
drwxr-xr-x 2 root root 16K Jul 20 17:10 Contacts
drwxr-xr-x 2 root root 16K Jul 20 17:10 Notes
drwxr-xr-x 5 root root 16K Sep 22 18:53 iPod_Control

```

---

### Post by ruudiculus on 2006-10-29
Hmm, I don't know if it is good that only the root can write on the ipod. You may want to try to run Floola with sudo as well. If it works then it's probably permission-related.

Otherwise I wouldn't know (maybe Floola Pod-detection is only scanning for sda's and not for sdb's :confused: Don't think so, but just maybe...)

Good Luck!

---

### Post by Floola on 2006-10-29
You probably didn't run iTunes once. Running it once (on mac/win) correctly setups iPod, after that you won't need iTunes anymore. Take a look at the Floola's user guide ruudiculus made. Get it from [www.floola.com](www.floola.com) in the help->docs section.

HTH,
Tomas

---

### Post by shizow on 2006-10-29
Update:

that was the problem, i just now plugged the ipod on a window machine
and now Floola works

but is the ipod nano 2nd gen supported by floola?
it could not detect my ipod version 

i get a error at the start of floola
FMEX error FMOD libary is missing No audio will be available

---

### Post by ruudiculus on 2006-10-29
You have to copy the libfmodex* files provided in the Floola .tar to /usr/lib. This should do the trick

Please read the getting started section of the 
[Floola Quick Guide]("http://www.ruudbeukema.nl/public/ubuntu/floola/Floola_quickguide.pdf") for more info

---

### Post by Zhukov on 2006-11-10
Shizou, just mount it with the option umask=0000 or umask=000, im not sure if it has 3 or 4 0s... Kinda sleepy now... :S

---

### Post by gritstone on 2006-11-13
I'm going to give this a try, thanks for the information.

---

### Post by Zhukov on 2006-11-23
I made some packages with a patched HAL that will detect your iPod, if you are interested...

---

### Post by teeleef on 2006-11-28
Thank you for a clear insight into the iPod.  The sda partition one and two description was a revelation, as I'd tried and tried mounting only sda itself...

Well done it is much appreciated when someone in the know takes time to explain to us mere mortals who no little about the command line and mounting in general.


Teeleef

---

### Post by Golgoth on 2006-11-28
and [Yamipod]("http://www.yamipod.com")?!

[IMG]http://www.yamipod.com/images/main.PNG[/IMG]

---

### Post by Zhukov on 2006-11-29
Yamipod: As interesting as it may be, its closed source.
Plus, it does nothing Amarok can't do. In fact, Amarok does a lot more. No, don't start with the usual "It's KDE!! Death to the K!" I'm a Gnome user for years and I love my Gnome desktop as much as I hate KDE. But Amarok is a very nice app ;)

---

### Post by Golgoth on 2006-12-02
Yep, but you just start with the usual "It's closed source!! Death to the non free software...".

Plus, I did not say anything about Amarok...

I don't have an Ipod,I just wanted to give the name of a software I know and which can be run on linux.

It's closed source, but you are maybe kind of "closed-minded"...

---

### Post by SuperMike on 2006-12-02
I received a new nano and tried Rhythmbox right away. It crashed immediately. So, to find out the source of the crash, I went to command line and typed sudo rhythmbox and it loaded up and crashed again, but this time it told me why. The reason it crashed was because it didn't have this file:

/media/ipod/iPod_Control/iTunes/iTunesDB

So, I recreated it by going to command line and typing:

sudo apt-get install gtkpod
sudo touch /media/ipod/iPod_Control/iTunes/iTunesDB
sudo gtkpod

Then, I chose Create iPod's Directories, then added a [sample MP3 file]("http://www.metacrawler.com/info.metac/search/audio/british_pop.mp3") and clicked the button to resync.

When I closed gtkpod down and brought it back up, the file I added to the iPod was still there and not just in the local directory. I then used 'ls' at a command prompt and checked the iTunesDB and found that it had been updated with new data and now had other files in the same directory.

After that, I could use Rhythmbox with no problem. Hopefully this will help you be able to recreate the iTunesDB if yours is corrupt or if you simply don't want to use the iTunes service or Windows and just want to do everything purely the Linux way, putting MP3 and other kinds of files on yourself.

---

### Post by Zhukov on 2006-12-02
> **Golgoth said:**
> Yep, but you just start with the usual "It's closed source!! Death to the non free software...".

Plus, I did not say anything about Amarok...

I don't have an Ipod,I just wanted to give the name of a software I know and which can be run on linux.

It's closed source, but you are maybe kind of "closed-minded"...

You did well pointing some software you found to be ok :)
Although I have to admit I started with the "non free software" stuff I don't want to pull nobody from Yamipod and alikes! :D

This forum is visited both by experienced linux users and 1 day users, some of which may not know neither Amarok nor the open/closed source issue.
This is (roughly) the same as using binary drivers. It doesn't encourages open software developers to continue doing so nor facilitates the integration of current software.

To a new user (as my sister, for example) I recommend her to use Amarok to manage her music collection. There is a good trade between usability and available functions. But this is just my opinion! I am a Gnome user, so I could also recommend Banshee if you don't want Kde libs.

Don't misunderstand me! :D

Cheers!

---

### Post by Floola on 2006-12-06
beta 20 is available! Greatly improved. Relies on gstreamer or xine so playback shouldn't be a problem anymore.

---

### Post by Floola on 2006-12-17
beta 23 available. Update strongly suggested as this version comes with many fixes and a new interesting feature, fast-mode. Under preferences->advanced you can enable this option which should significally increase speed of application.

[http://www.floola.com](http://www.floola.com)

---

### Post by bwalsh on 2006-12-25
I found this thread while searching for a solution to my ipod problem, not sure if anyone can help me out. I just got a 4 GB Nano, but I can't get my system to recognize it. Here's my mtab after plugging it in:

/dev/sda2 / reiserfs rw,notail 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.17-10-386/volatile tmpfs rw 0 0
/dev/sda3 /home reiserfs rw 0 0
/dev/sdb2 /media/sdb2 reiserfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0


And here's my dmesg output:

[17179739.036000] usb 5-6: new high speed USB device using ehci_hcd and address 2
[17179739.168000] usb 5-6: configuration #1 chosen from 2 choices
[17179739.264000] usbcore: registered new driver libusual
[17179739.304000] Initializing USB Mass Storage driver...
[17179739.304000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179739.304000] usb-storage: device found at 2
[17179739.304000] usb-storage: waiting for device to settle before scanning
[17179739.304000] usbcore: registered new driver usb-storage
[17179739.304000] USB Mass Storage support registered.
[17179744.304000] usb-storage: device scan complete
[17179744.304000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17179744.304000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179744.308000] SCSI device sdc: 1982464 2048-byte hdwr sectors (4060 MB)
[17179744.308000] sdc: Write Protect is off
[17179744.308000] sdc: Mode Sense: 68 00 00 08
[17179744.308000] sdc: assuming drive cache: write through
[17179744.308000] SCSI device sdc: 1982464 2048-byte hdwr sectors (4060 MB)
[17179744.312000] sdc: Write Protect is off
[17179744.312000] sdc: Mode Sense: 68 00 00 08
[17179744.312000] sdc: assuming drive cache: write through
[17179744.312000]  sdc: sdc1 sdc2
[17179744.312000] sd 2:0:0:0: Attached scsi removable disk sdc
[17179744.312000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[17183999.204000] usb 5-6: reset high speed USB device using ehci_hcd and address 2
[17184010.748000] usb 5-6: device not accepting address 2, error -110
[17184010.916000] usb 5-6: USB disconnect, address 2
[17184010.916000]  2:0:0:0: scsi: Device offlined - not ready after error recovery
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000] sdc : READ CAPACITY failed.
[17184010.920000] sdc : status=0, message=00, host=1, driver=00 
[17184010.920000] sdc : sense not available. 
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000] sdc: Write Protect is off
[17184010.920000] sdc: Mode Sense: 00 00 00 00
[17184010.920000] sdc: assuming drive cache: write through
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000] sdc : READ CAPACITY failed.
[17184010.920000] sdc : status=0, message=00, host=1, driver=00 
[17184010.920000] sdc : sense not available. 
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000] sdc: Write Protect is off
[17184010.920000] sdc: Mode Sense: 00 00 00 00
[17184010.920000] sdc: assuming drive cache: write through
[17184010.920000]  sdc:<3> 2:0:0:0: rejecting I/O to dead device
[17184010.920000] Buffer I/O error on device sdc, logical block 0
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184010.920000] Buffer I/O error on device sdc, logical block 0
[17184010.920000]  unable to read partition table
[17184010.920000]  2:0:0:0: rejecting I/O to dead device
[17184017.240000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[17184028.784000] usb 5-6: device not accepting address 3, error -110
[17184028.896000] usb 5-6: new high speed USB device using ehci_hcd and address 4
[17184040.440000] usb 5-6: device not accepting address 4, error -110
[17184040.552000] usb 5-6: new high speed USB device using ehci_hcd and address 5
[17184050.976000] usb 5-6: device not accepting address 5, error -110
[17184051.088000] usb 5-6: new high speed USB device using ehci_hcd and address 6
[17184061.512000] usb 5-6: device not accepting address 6, error -110
[17184129.380000] usb 5-6: new high speed USB device using ehci_hcd and address 7
[17184140.924000] usb 5-6: device not accepting address 7, error -110
[17184141.036000] usb 5-6: new high speed USB device using ehci_hcd and address 8
[17184152.580000] usb 5-6: device not accepting address 8, error -110
[17184152.692000] usb 5-6: new high speed USB device using ehci_hcd and address 9
[17184163.116000] usb 5-6: device not accepting address 9, error -110
[17184163.228000] usb 5-6: new high speed USB device using ehci_hcd and address 10
[17184173.652000] usb 5-6: device not accepting address 10, error -110
[17184621.788000] usb 5-6: new high speed USB device using ehci_hcd and address 11
[17184633.332000] usb 5-6: device not accepting address 11, error -110
[17184633.444000] usb 5-6: new high speed USB device using ehci_hcd and address 12
[17184644.988000] usb 5-6: device not accepting address 12, error -110
[17184645.100000] usb 5-6: new high speed USB device using ehci_hcd and address 13
[17184655.524000] usb 5-6: device not accepting address 13, error -110
[17184655.636000] usb 5-6: new high speed USB device using ehci_hcd and address 14
[17184666.060000] usb 5-6: device not accepting address 14, error -110
[17185018.688000] usb 5-6: new high speed USB device using ehci_hcd and address 15
[17185030.232000] usb 5-6: device not accepting address 15, error -110
[17185030.344000] usb 5-6: new high speed USB device using ehci_hcd and address 16
[17185041.888000] usb 5-6: device not accepting address 16, error -110
[17185042.000000] usb 5-6: new high speed USB device using ehci_hcd and address 17
[17185052.424000] usb 5-6: device not accepting address 17, error -110
[17185052.536000] usb 5-6: new high speed USB device using ehci_hcd and address 18
[17185062.960000] usb 5-6: device not accepting address 18, error -110
[17185229.108000] usb 5-1: new high speed USB device using ehci_hcd and address 19
[17185240.652000] usb 5-1: device not accepting address 19, error -110
[17185240.764000] usb 5-1: new high speed USB device using ehci_hcd and address 20
[17185252.308000] usb 5-1: device not accepting address 20, error -110
[17185252.420000] usb 5-1: new high speed USB device using ehci_hcd and address 21
[17185262.844000] usb 5-1: device not accepting address 21, error -110
[17185262.956000] usb 5-1: new high speed USB device using ehci_hcd and address 22
[17185273.380000] usb 5-1: device not accepting address 22, error -110
[17186362.100000] usb 5-6: new high speed USB device using ehci_hcd and address 23
[17186373.644000] usb 5-6: device not accepting address 23, error -110
[17186373.756000] usb 5-6: new high speed USB device using ehci_hcd and address 24
[17186385.300000] usb 5-6: device not accepting address 24, error -110
[17186385.412000] usb 5-6: new high speed USB device using ehci_hcd and address 25
[17186395.836000] usb 5-6: device not accepting address 25, error -110
[17186395.948000] usb 5-6: new high speed USB device using ehci_hcd and address 26
[17186406.372000] usb 5-6: device not accepting address 26, error -110
[17189134.604000] usb 5-6: new high speed USB device using ehci_hcd and address 27
[17189146.148000] usb 5-6: device not accepting address 27, error -110
[17189146.260000] usb 5-6: new high speed USB device using ehci_hcd and address 28
[17189157.804000] usb 5-6: device not accepting address 28, error -110
[17189157.916000] usb 5-6: new high speed USB device using ehci_hcd and address 29
[17189168.340000] usb 5-6: device not accepting address 29, error -110
[17189168.452000] usb 5-6: new high speed USB device using ehci_hcd and address 30
[17189178.876000] usb 5-6: device not accepting address 30, error -110
[17189782.756000] ehci_hcd 0000:00:10.4: remove, state 1
[17189782.756000] usb usb5: USB disconnect, address 1
[17189782.760000] ehci_hcd 0000:00:10.4: USB bus 5 deregistered
[17189782.760000] ACPI: PCI interrupt for device 0000:00:10.4 disabled

I tried editing fstab and using the modprobe suggestion, but neither have helped. My ipod charged fine, but it just isn't getting recognized. Any ideas?

---

### Post by Zhukov on 2006-12-25
Are you using a HUB or a front usb port? Try using a different one, maybe on the back of the machine.

---

### Post by mhancoc7 on 2006-12-25
This may have already been mentioned.

I believe the problem with Vmware and iTunes is the fact that Vmware does not support USB 2.0 and that is required by iTunes. However, the new Vmware 6.0 Beta is supposed to have support for USB 2.0!

Jereme

---

### Post by merxzzz on 2006-12-31
Hi,

I'm having problems with my new 30GB iPod Video that I got for Christmas. I'm running Dapper Drake on an AMD64 processor, which might be the problem, but anyway, my computer detects it and stuff, just that it seems that each time I try to do something with it using either Rhythmbox or Amarok, those programs crash. Gtkpod gives me an error "Segmentation fault" and Floola doesn't seem to work at all. So, I'm kind of stuck here, having no idea what to do.

Any help would be greatly appreciated,
Liz

---

### Post by SmiLey497 on 2006-12-31
did you format your ipod drive in windows first?

---

### Post by SuperMike on 2006-12-31
Liz,

My daughter had an iPod and had the same problem. I hope you haven't uploaded any songs to it, because I have some advice that may fix you, but may remove any previous songs you have on the device. Consider this carefully before proceeding.

* I opened the folder for the iTunes and renamed the one containing the iTunes database. I renamed it to iTunes.OLD.

* If you haven't installed the MPEG encoder/decoders, consider using Automatix or some of the other scripts posted here on this site to do that.

* I installed gtkpod from the 'apt' command:

$ sudo apt-get --purge remove gtkpod
$ sudo apt-get install gtkpod

(I didn't know how to compile it properly from source with the latest version from CVS.)

* I launched gtkpod and I get an error like yours and a few others. I then went to the File menu and did "Create iPod Directories". It created these. I then clicked the Sync button and quit the app. If you get an error on the "Create iPod Directories" part, it might be because somehow your PC is not mounting the iPod in read/write mode. If you have the Hold button flipped on, switch that off. Then, reboot your PC and insert the iPod. It will probably show up as read/write. Then, retry the "Create iPod Directories" part. This will recreate an empty database.

* Remove the device and plug it back in again.

* Launch gtkpod and it probably will work okay without error this time.

* Add new songs to the device. Click Sync when done. DO NOT CLOSE THE APP DOWN until it is finished synchronizing and the iPod's upper lefthand corner "busy" icon has finished spinning.

* I wouldn't recommend adding more than about 8 songs at a time. I had trouble when trying to add more than that at a time. Perhaps other people have had better luck, but I didn't.

* I found I could rename song titles, album titles, and so on by clicking in the fields in the bottom grid, waiting a second, and the field would go into edit mode like on a spreadsheet.

* Close gtkpod.

* Rightclick your iPod icon off the desktop and choose Unmount Volume. You'll get an error. DO NOT PULL OUT YOUR USB CABLE YET until it is finished synchronizing and the iPod's upper lefthand corner "busy" icon has finished spinning. NOTE ALSO that the busy icon on the iPod may stop a couple seconds and repeat itself as much as 3-4 times until finished. Click OK on the error to just ignore it. Hopefully this error will be fixed in a later-release of the usb mounter for the iPod.

* Ignore the fact that your iPod says, "Do Not Disconnect Device". Pull out the USB cable for the device out of your PC. Disconnect the cable from your iPod. All should be okay again.

---

### Post by ruudiculus on 2007-01-01
Liz, there is no Floola for amd64 processors available yet. So, you might want to try the suggested method (SuperMike) of compiling GtkPod yourself for your amd64 processor.

Good luck!

---

### Post by Bruckout22 on 2007-01-01
Hey guys I tried this tutorial with Ubuntu 6.10 automount works picked up I pod and songs But i was unable to listen to any of my music form gtkpod all had that cant play symbol next to it any suggestions

---

### Post by merxzzz on 2007-01-01
SmiLey497, yeah, I did that.

SuperMike, I did everything you suggested up until the "Create iPod Directories" part. Gtkpod gave me an error "** (gtkpod:30004): CRITICAL **: ipod_directories_head: assertion `mountpoint' failed". My brother also tried compiling Gtkpod, but it didn't work either. We thought about upgrading to Edgy so that we could install the newest version of Banshee to see if maybe that works. If not, then I guess I'll either have to replace my current version of Linux with a 32-bit one, or go back to using Windows. ;)

Thanks heaps for helping, though!

---

### Post by Floola on 2007-01-08
Beta 26 available. Since last posted version there's new folder sync feature, which should be fairly easy to use. Many bug fixes as well.

[http://www.floola.com](http://www.floola.com)

---

### Post by Zaphod on 2007-01-08
I have a ipod nano 2GB . I never expected to use it in my computer (running ubuntu 6.10) just thought id use wifes comp for that . 

Tonight I decided to try , after seeing this tutorial . Works like a charm , automounted and opened up Rythmbox (Amorok still a no go though still trying) GTKpod works well too ..

kinda nice surpise :D

---

### Post by Edward The Bonobo on 2007-01-09
> **SuperMike said:**
> 
* I wouldn't recommend adding more than about 8 songs at a time. I had trouble when trying to add more than that at a time. Perhaps other people have had better luck, but I didn't.

....

* Ignore the fact that your iPod says, "Do Not Disconnect Device". Pull out the USB cable for the device out of your PC. Disconnect the cable from your iPod. All should be okay again.

I usually find it difficult to add many songs at the same time (but I usually manage more than 8!).  When I have a big album loading session, I usually get a crash at least once every five albums.  Then I have to unplug, delete the songs, re-synch and add them again.  It's especially painful because gtkpod hangs for a while before it gives you the Warning dialog.  **BUT**...a long time ago I read about a fix for this on the forum.  I can't find it now.  Does anyone know what it is?  It would be very useful to be able to simply add lots of albums and then hit Synch once.

Do Not Disconnect...  You're right, it doesn't seem to make any difference.  However, if anyone is worried, if you go File.../Offline in gtkpod you can eject the iPod 'properly' with a right-click.  But remember to untick the Offline when you plug it back in or you'll think you've added songs when you haven't.  ](*,) 

btw...One thing I find very frustrating about gtkpod is the time it takes to display my songs list.  It reads the database quickly, but when I click on the device name (on the Left-hand list), it takes minimum 1s to read each song's details - and I have 3600+ songs!  (this is on a PII 333MHz with approx 256Kb).  Does anyone know if I can add songs *without *displaying the songs list?

---

### Post by andstuff on 2007-01-09
Is there a way to make songs that are right now on my iPod but were put on by iTunes work in Linux, The ACC stuff I can get around because I have them, but my mp3s were gathered by other method. I copied the song from my iPod to my computer and they just don't seem to work in anything in ubuntu... [amaroK, juK and Rhythm Box]

---

### Post by Edward The Bonobo on 2007-01-10
Try here:
[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)

---

### Post by merxzzz on 2007-01-13
Well, in case anyone's having the same problem I did, upgrading to Edgy will solve it. Gtkpod works fine, haven't tried out other programs yet.

On an unrelated note, does anybody know a way to convert Musepack to mp3?

---

### Post by Edward The Bonobo on 2007-01-15
Edgy upgrade hasn't fixed gtkpod for me.

---

### Post by merxzzz on 2007-01-16
Heh, how about you try Amarok or Rhythmbox or something of the sort, when it comes to iPod support they both have the same basic features as Gtkpod if not more, as far as I'm aware.

---

### Post by Edward The Bonobo on 2007-01-18
> **Edward The Bonobo said:**
> Edgy upgrade hasn't fixed gtkpod for me.

I was wrong.  Now it displays my database in about a minute.  Before it was over an hour.  But it still crashes every five albums or so.

Amarok...Rhythmbox...I'm not sure if you can use these 'standalone' - ie I don't keep all my music on my hard drive (it's too small).  I add a few albums at a time and then back them up to CD.  Has anyone used gtkpod this way?  I like the idea of them - eg automatic import of album art from Amazon.

---

### Post by KingOfNowhere on 2007-01-19
Hi all, this thread is in dire need of updating (mostly because I wrote it using breezy). So dont worry, an update will be comming down the pipe in the near future

- KingOfNowhere

---

### Post by thefoxcatch on 2007-01-23
I followed the directions on the first page, and now my ipod does not work. It was formatted with windows and that is probably the problem. But a couple of other things seem to be happening.
When i'm in Place -> Computer
and i click on Apple iPod Music Player , this message shows up
"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted." which i figure is do to it being formatted with windows....
details of this message say
"mount: wrong fs type, bad option, bad superblock on /dev/sda,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount"

Now , when my ipod is connected, I can open Amarok and it reads it fine with no problems, and I can listen to music on it thru Amarok, but I cannot use the iPod regulary. When I click on a song, this black screen with a white apple shows up and I can't listen to music. But amarok seems to be able to access it for whatever reason.

As for gtkpod, this happens when i try to read the iPod
"'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted."

Also, I went into terminal and put it this code 
sudo ln -s /media/ipod /mnt/ipod

help me please!

---

### Post by thefoxcatch on 2007-01-23
also, i put in this code
sudo dosfsck -a /dev/sda2
and this came out
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda2: 846 files, 239565/240853 clusters

but gtkpod still is giving me this message
'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.

---

### Post by cantormath on 2007-01-23
<bump> same problem....

it seems that it recognizes the format of your Ipod....

---

### Post by thefoxcatch on 2007-01-23
its a 4gb iPod, i got it in december, so whatever generation that is

---

### Post by ubernoob on 2007-01-31
I'm having 2 problems with ipod and calendar:

- The calendar on the ipod starts the week on sunday instead of monday which is usual here in my country.

- I'm getting 1 hour offset on the calendar when syncronizing with korganizer.

Any ideas?

---

### Post by thefoxcatch on 2007-02-01
i resolved my own problems

---

### Post by Floola on 2007-02-04
Next version of floola will feature native iPod podcast support. I'm looking for beta testers, if interested contact me via email, [http://www.floola.com](http://www.floola.com)

---

### Post by Floola on 2007-02-06
For those interested in trying the podcast feature: [http://www.floola.com/modules/newbb/viewtopic.php?topic_id=32&forum=1](http://www.floola.com/modules/newbb/viewtopic.php?topic_id=32&forum=1)

Tomas

---

### Post by D_Murdock on 2007-02-06
I actually had mine formatted under Mac OS X Tiger, I plugged it into my Ubuntu box and it picked everything up, All I had to install was RhythmBox which it auto prompted me to install.

---

### Post by umuntu_ngabantu on 2007-02-07
Hello King of nowhere

I have tried to follow your how-to (mount ipod) to the T, but I'm not winning. I've installed gtkpod. I have a problem mounting my ipod. It does not appear to be mounted on my desktop. The ipod however is recognised as some sort of storage disk by the computer. When I try to right click on it and "mount volume", it refuses to mount it.:confused: 
 
I then ran this up:

dmesg | tail  
[17179663.672000] hfs: can't find a HFS filesystem on dev sda.
[17179663.680000] VFS: Can't find ext3 filesystem on dev sda.
[17179663.684000] VFS: Can't find ext3 filesystem on dev sda.
[17179663.724000] VFS: Can't find an ext2 filesystem on dev sda.
[17179663.732000] VFS: Can't find an ext2 filesystem on dev sda.
[17179663.776000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17179663.784000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17179663.932000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179663.932000] SGI XFS Quota Management subsystem
[17179663.988000] JFS: nTxBlock = 3894, nTxLock = 31158


Any ideas please? My Ipod is a Nano 4GB
 
Your help would be appreciated.

---

### Post by Skeorx13 on 2007-03-01
I'm on Ubuntu 6.10 (I more or less just dove headfirst into Linux a few days ago with no prior experience so forgive my ignorance) and my 60GB 5th gen ipod automounts to ubuntu and rhythmbox automatically tries to access it (I subsequently shut the autoload for it off in the removable drives and media menu) and gtkpod sees it and synchs to it and allows me to edit and update but amarok doesn't see it automatically. I went to configure amarok menu and the media devices submenu and clicked add device, and set the plugin to apple ipod media device. I directed it to the correct mounting point and assigned it the same name I gave it when I was connected to windows xp. When I go to the media devices tab in amarok and click the connect button I get this window: 

> Remove iTunes Lock File?
Media Device: iPod mounted at /media/ipod already locked! If you are sure that this is an error, then remove the file /media/ipod/iPod_Control/iTunes/iTunesLock and try again.

What in the world do I do with this to get my ipod to work with amarok? When I try to autodetect devices I get this error: 

> No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.

I ran dcop kded mediamanger fullList in the terminal and got "call failed" as a response. Anyone able to help me out on this one?

---

### Post by ruudiculus on 2007-03-01
I really have not good idea, but have you installed the **ipodslave** package?

---

### Post by iPirates on 2007-03-01
Hey

When I try starting gtkpod, I get this error message:

gtkpod: error while loading shared libraries: libgpod.so.1: cannot open shared object file: No such file or directory

Would anybody know how to fix this?  I've tried reinstalling gtkpod, through the repositories, but i still get the same message.

---

### Post by ruudiculus on 2007-03-01
You could try Floola: [www.floola.com](www.floola.com)

---

### Post by iPirates on 2007-03-01
Floola definately looks promising... i just need access to itunes first... i'll try that later.
But just for peace of mind, does anyone know how to fix my problem? (see 2 posts above).
It was working fine earlier (by working, I mean the program booted up), but now it wont, and when I try and launch if from the terminal, it gives me that error....
**Edit: haha, this isn't a major problem, i don't care if I actually get it to work or not, but i'm tryin to learn from my mistakes here  ;)

---

### Post by linuxnoob123 on 2007-03-01
I was wondering if there is a way for me to convert my videos in .mpg format to .avi or mp4?:confused: :confused: :confused: :confused:

---

### Post by Skeorx13 on 2007-03-01
Still can't figure out why I keep getting this error. When I had my ipod connected in windows I used winamp. I've never even used itunes before. Anyone able to help?

---

### Post by sshetye on 2007-03-08
> **iPirates said:**
> Hey

When I try starting gtkpod, I get this error message:
[FONT="Courier New"][INDENT]
gtkpod: error while loading shared libraries: libgpod.so.1: cannot open shared object file: No such file or directory[/INDENT][/FONT]

Would anybody know how to fix this?  I've tried reinstalling gtkpod, through the repositories, but i still get the same message.

Ubuntu puts its libraries at /usr/lib/* while manually compiling libgpod puts it at /usr/local/lib/*. Gtkpod searches the library path for the library and doesn't find it, complains. Simply move the needed library where GTKPod can find it, type

[INDENT][FONT="Courier New"]sudo mv /usr/local/lib/libgpod* /usr/lib/[/FONT][/INDENT]

---

### Post by Floola on 2007-03-28
Beta 35 is available. Huge performance boost with large artwork libraries. Many podcast issues fixed.

[http://www.floola.com](http://www.floola.com)

---

### Post by Narutolinspire on 2007-05-28
i mount my ipod and go onto lsongs and it sasy uploading ipod library, Is it gonna work?

---

### Post by adt41287 on 2007-06-02
for anybody using Amarok,
how do you sync ratings from ipod to reflect on the collection??
for example if i want to rate a song on the go, how do i make it sync on the collection rather than doing it manually??

---

### Post by Do0odz on 2007-07-06
I don't know if someone have posted something similar to my problem .. I just didn't feel like going through 20 pages to check lol .. 

whenever I plug my ipod photo .. and open amarok I get this error msg ( remove itunes lock file ) : ipod mounted at media/NAME already locked . if you are sure this is an error, then remove the file media/NAME/ipod_control/itunes/itunes lock and try again .. 

I want to import music from the ipod to my desktop ..

---

### Post by zutronius on 2007-07-12
I did not have any luck with the Ipod tutorial.

After the dsmeg command, I get:

[ 5145.978524] powernow-k8: failing targ, change pending bit set
[ 5147.217134] powernow-k8: failing targ, change pending bit set
[ 5148.455746] powernow-k8: failing targ, change pending bit set
[ 5149.694357] powernow-k8: failing targ, change pending bit set
[ 5150.932960] powernow-k8: failing targ, change pending bit set
[ 5152.171576] powernow-k8: failing targ, change pending bit set
[ 5153.410178] powernow-k8: failing targ, change pending bit set
[ 5154.648786] powernow-k8: failing targ, change pending bit set
[ 5155.887400] powernow-k8: failing targ, change pending bit set
[ 5157.126005] powernow-k8: failing targ, change pending bit set
[ 5158.364612] powernow-k8: failing targ, change pending bit set
[ 5159.607221] powernow-k8: failing targ, change pending bit set
[ 5160.845830] powernow-k8: failing targ, change pending bit set
[ 5162.088430] powernow-k8: failing targ, change pending bit set
[ 5163.327039] powernow-k8: failing targ, change pending bit set


this occurs for a couple of hundred lines. Any advice on what to do?

---

### Post by wyrdvans on 2007-07-27
> **Do0odz said:**
> I don't know if someone have posted something similar to my problem .. I just didn't feel like going through 20 pages to check lol .. 

whenever I plug my ipod photo .. and open amarok I get this error msg ( remove itunes lock file ) : ipod mounted at media/NAME already locked . if you are sure this is an error, then remove the file media/NAME/ipod_control/itunes/itunes lock and try again .. 

I want to import music from the ipod to my desktop ..

I too would like to know this using either gtkpod or amarok.

---

### Post by cimex on 2007-08-12
I can't mount partition sda2. When i attach my Ipod it is detected as device /dev/sda  (see dmesg below), but after creating dir /mnt/ipod and modifying /etc/fstab . I can't mount  the Ipod, I get the message:

mount: special device /dev/sda2 does not exist

Is there some way to create a missing sda2 device?


" usb 3-4: new high speed USB device using ehci_hcd and address 3
[  277.656000] usb 3-4: configuration #1 chosen from 1 choice
[  277.656000] scsi1 : SCSI emulation for USB Mass Storage devices
[  277.656000] usb-storage: device found at 3
[  277.656000] usb-storage: waiting for device to settle before scanning
[  282.656000] usb-storage: device scan complete
[  282.656000] scsi 1:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  282.660000] SCSI device sda: 12000555 512-byte hdwr sectors (6144 MB)
[  282.660000] sda: Write Protect is off
[  282.660000] sda: Mode Sense: 64 00 00 08
[  282.660000] sda: assuming drive cache: write through
[  282.660000] SCSI device sda: 12000555 512-byte hdwr sectors (6144 MB)
[  282.664000] sda: Write Protect is off
[  282.664000] sda: Mode Sense: 64 00 00 08
[  282.664000] sda: assuming drive cache: write through
[  282.664000]  sda:<6>usb 3-4: USB disconnect, address 3
[  282.996000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[  282.996000]  printing eip:
[  282.996000] c0258355
[  282.996000] *pde = 00000000
[  282.996000] Oops: 0000 [#1]
[  282.996000] SMP "

---

### Post by cimex on 2007-08-13
> **cimex said:**
> I can't mount partition sda2. When i attach my Ipod it is detected as device /dev/sda  (see dmesg below), but after creating dir /mnt/ipod and modifying /etc/fstab . I can't mount  the Ipod, I get the message:

mount: special device /dev/sda2 does not exist

Is there some way to create a missing sda2 device?


" usb 3-4: new high speed USB device using ehci_hcd and address 3
[  277.656000] usb 3-4: configuration #1 chosen from 1 choice
[  277.656000] scsi1 : SCSI emulation for USB Mass Storage devices
[  277.656000] usb-storage: device found at 3
[  277.656000] usb-storage: waiting for device to settle before scanning
[  282.656000] usb-storage: device scan complete
[  282.656000] scsi 1:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  282.660000] SCSI device sda: 12000555 512-byte hdwr sectors (6144 MB)
[  282.660000] sda: Write Protect is off
[  282.660000] sda: Mode Sense: 64 00 00 08
[  282.660000] sda: assuming drive cache: write through
[  282.660000] SCSI device sda: 12000555 512-byte hdwr sectors (6144 MB)
[  282.664000] sda: Write Protect is off
[  282.664000] sda: Mode Sense: 64 00 00 08
[  282.664000] sda: assuming drive cache: write through
[  282.664000]  sda:<6>usb 3-4: USB disconnect, address 3
[  282.996000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[  282.996000]  printing eip:
[  282.996000] c0258355
[  282.996000] *pde = 00000000
[  282.996000] Oops: 0000 [#1]
[  282.996000] SMP "

The problems were solved after I restored the Ipod in iTunes, that also updated the software on the Ipod.

---

### Post by soxs on 2007-08-14
> **Ninnghizidha said:**
> How can i format the hdd of my ipod with fat32? :confused:
use google, there is a howto in the www (do not have the adress handy right now) it *should* work for you. Another option is, to reset your iPod to factory state and then connect the first time to an winbox (just this first time). I've done it via the second method, as it is newbe-proof. The first one comes in handy, when you have no instant access to an winbox.

i am using exaile! & Amarok. (exaile! aims to be Amarok for gnome, but this will take some time, but has fast develpoment..)

---

### Post by pistolpants on 2007-09-10
I have a real emergency with my 80 gig ipod. It seems in the process of going from windows to ubuntu my ipod was cleaned out. there is not one thing left on my ipod. is there any way to recover said library though ubuntu?:(

---

### Post by Camron-roks on 2007-10-06
[http://frankscorner.org/index.php?p=itunes6](http://frankscorner.org/index.php?p=itunes6)

shows you how to use itunes with wine :) CD burning doesn't work tho, i'm not sure about the ipod part

---

### Post by bford16 on 2008-02-06
> **zutronius said:**
> I did not have any luck with the Ipod tutorial.

After the dsmeg command, I get:

[ 5145.978524] powernow-k8: failing targ, change pending bit set
[ 5147.217134] powernow-k8: failing targ, change pending bit set
[ 5148.455746] powernow-k8: failing targ, change pending bit set
[ 5149.694357] powernow-k8: failing targ, change pending bit set
[ 5150.932960] powernow-k8: failing targ, change pending bit set
[ 5152.171576] powernow-k8: failing targ, change pending bit set
[ 5153.410178] powernow-k8: failing targ, change pending bit set
[ 5154.648786] powernow-k8: failing targ, change pending bit set
[ 5155.887400] powernow-k8: failing targ, change pending bit set
[ 5157.126005] powernow-k8: failing targ, change pending bit set
[ 5158.364612] powernow-k8: failing targ, change pending bit set
[ 5159.607221] powernow-k8: failing targ, change pending bit set
[ 5160.845830] powernow-k8: failing targ, change pending bit set
[ 5162.088430] powernow-k8: failing targ, change pending bit set
[ 5163.327039] powernow-k8: failing targ, change pending bit set


this occurs for a couple of hundred lines. Any advice on what to do?

This is a known issue with cpu frequency scaling (powernowd).  As far as I know, there is no fix for this issue.  It may have somethiing to do with memory, but I haven't seen that confirmed.  You can stop the error messages by doing "sudo /etc/init.d/powernowd stop" in the terminal.  This won't solve the problem, though.

---

### Post by Sixtyin3 on 2008-02-24
Hey,

Fairly new Ubuntu user here.  I have been unlocking my iPhone since summer and never had a problem with the phone.  However I can't for the life of me get it to sync up with my Ubuntu 7.10.  I have FW 1.1.3 unlocked and JB'd on the iPhone.  I downloaded everything and ran everything and I can connect ot the phone, but it NEVER shows my phones library in gtkpod or Amarok.  I think its a hashing problem?  It won't load my phones songs.

Thanks,
Steve

---

### Post by etlpkby on 2008-04-03
what is it with amaroK? All I want is to copy (mp3) tracks to my 4GB mini-ipod and it just doesn't want to play.

Utter rubbish - and gtkpod isn't much better

Can't anyone just get a decent, **stable**, application that just copies tracks from disk to removable media?

---

### Post by IHATEDLINK on 2008-05-08
> **etlpkby said:**
> what is it with amaroK? All I want is to copy (mp3) tracks to my 4GB mini-ipod and it just doesn't want to play.

Utter rubbish - and gtkpod isn't much better

Can't anyone just get a decent, **stable**, application that just copies tracks from disk to removable media?

Go to the iTunes Linux Project (link in my signature) for everything iTunes related on Linux.
(HOWTO's, alternatives and more)

---

### Post by Saint Angeles on 2008-05-08
im confused... i installed ubuntu on my (retarded) sister's computer and the iPod worked with no config needed at all.

---

### Post by anders.ostling on 2008-05-08
> **Saint Angeles said:**
> im confused... i installed ubuntu on my (retarded) sister's computer and the iPod worked with no config needed at all.

Good for you. But how is your sisters health condition related to your iPod's function on Ubuntu?

---

### Post by ikt on 2008-05-08
Got ubuntu hardy 8.04 here, back in 7.10 you would goto removable devices and media and you could tell it which program to load the ipod with, that option is no longer there.

Now rythembox opens up everytime, how can I change it so that it opens with Amarok not rythembox?

---

### Post by ibootindos on 2008-08-03
oot@joshua-laptop:~# sudo mount /dev/sda2
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

what's this mmeeeaan??!?!?!?!

---

### Post by ibootindos on 2008-08-03
also when I run dmesg.. this is my output??

[ 2765.835774] sd 9:0:0:0: [sdd] Spinning up disk......................................................................................................not responding...
[ 3057.565049] FAT: bogus number of reserved sectors
[ 3057.565062] VFS: Can't find a valid FAT filesystem on dev sda2.
[ 3059.843435] sd 9:0:0:0: [sdd] READ CAPACITY failed
[ 3059.843445] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3059.843453] sd 9:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 3059.843461] sd 9:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 3059.844217] sd 9:0:0:0: [sdd] Write Protect is off
[ 3059.844224] sd 9:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 3059.844229] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 3067.908356] sd 9:0:0:0: [sdd] Spinning up disk......................................................................................................not responding...
[ 3361.872891] sd 9:0:0:0: [sdd] READ CAPACITY failed
[ 3361.872910] sd 9:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3361.872921] sd 9:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 3361.872931] sd 9:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 3361.873608] sd 9:0:0:0: [sdd] Write Protect is off
[ 3361.873615] sd 9:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 3361.873621] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 4454.661413] FAT: bogus number of reserved sectors
[ 4454.661424] VFS: Can't find a valid FAT filesystem on dev sda2.
[ 5773.810564] usb 6-3: USB disconnect, address 4
[ 5777.003328] usb 6-3: new high speed USB device using ehci_hcd and address 5
[ 5777.135808] usb 6-3: configuration #1 chosen from 2 choices
[ 5777.143718] scsi10 : SCSI emulation for USB Mass Storage devices
[ 5777.143980] usb-storage: device found at 5
[ 5777.143984] usb-storage: waiting for device to settle before scanning
[ 5782.141464] usb-storage: device scan complete
[ 5782.149087] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5782.168891] sd 10:0:0:0: [sdd] Spinning up disk.....

---

### Post by rockprincess on 2008-08-21
hello everyone,

i tried to sync the ipod with Kontact, I've created events and exported them as ical and then transfered them onto my iPod into the "calendars" folder. i am not getting any error messages, it just doesn't show up when i click on "calendars" on the ipod itself.

address contacts work perfectly fine when being exported/imported as a vcard file.

any ideas what i'm doing wrong here?

i want to be able to sync my events/todos with my ipod. Please help me here! :))))

---

### Post by rockprincess on 2008-08-22
any ideas?!

---

### Post by vikpaul on 2008-08-31
Hi,

Is this How-to applicable only to Ipods that have been used atleast once with Windows/Mac? I have a new Ipod that has never been used before, I am wondering
 whether this how-to is applicable? thanks

---

### Post by rockprincess on 2008-08-31
it is vikpaul!

---

### Post by luckyuser on 2008-08-31
> **vikpaul said:**
> Hi,

Is this How-to applicable only to Ipods that have been used atleast once with Windows/Mac? I have a new Ipod that has never been used before, I am wondering
 whether this how-to is applicable? thanks

@vikpaul: Whatu kind of iPod do you have?
You may have some trouble if you have a newer iPod (i.e. a 6th generation classic, or the new nano). The firmware on those models has made it difficult for 3rd party applications (aka everything but iTunes) to add songs and such to the iPods. I know I had tons of trouble with mine for a couple of days, but this info helped a lot:


[http://ubuntuforums.org/showthread.php?t=804761]("http://ubuntuforums.org/showthread.php?t=804761")
[http://amarok.kde.org/wiki/Media_Device:IPod]("http://amarok.kde.org/wiki/Media_Device:IPod")

I am not a big fan of Amarok (loads slowly and cluttered interface), but when it comes to adding/removing songs from my iPod i prefer Amarok over gtkpod. Hope this helps.

---

### Post by dentaku65 on 2008-08-31
I just make a tutorial for Ipod on Hardy, I'm waiting for approval.
I'll let this thread if/when will be available.

---

### Post by dentaku65 on 2008-09-01
Here my Howto on Ipod, approved today:
[http://ubuntuforums.org/showthread.php?t=906217](http://ubuntuforums.org/showthread.php?t=906217)

Pls, post there questions and hints if any

:guitar:

---

### Post by Imoen on 2009-03-26
On Step 2, I am not finding my ipod. Any idea how to get it to be detected?

```
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)                                                   
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)                                                   
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)                                                   
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)                                                   
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                         
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated                                                
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                            
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.98 BogoMIPS (lpj=9575972)                                                                                                              
[    0.004035] Security Framework initialized                                                                      
[    0.004044] SELinux:  Disabled at boot.                                                                         
[    0.004071] AppArmor: AppArmor initialized                                                                      
[    0.004084] Mount-cache hash table entries: 512                                                                 
[    0.004315] Initializing cgroup subsys ns                                                                       
[    0.004320] Initializing cgroup subsys cpuacct                                                                  
[    0.004324] Initializing cgroup subsys memory                                                                   
[    0.004345] CPU: Trace cache: 12K uops, L1 D cache: 8K                                                          
[    0.004350] CPU: L2 cache: 512K                                                                                 
[    0.004354] CPU: Physical Processor ID: 0                                                                       
[    0.004371] Checking 'hlt' instruction... OK.                                                                   
[    0.022507] ACPI: Core revision 20080609                                                                        
[    0.024926] ACPI: Checking initramfs for custom DSDT                                                            
[    0.423565] ENABLING IO-APIC IRQs                                                                               
[    0.423751] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1                                                
[    0.463445] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09                                                 
[    0.464029] Booting processor 1/1 ip 6000                                                                       
[    0.004000] Initializing CPU#1                                                                                  
[    0.004000] Calibrating delay using timer specific routine.. 4788.35 BogoMIPS (lpj=9576710)                     
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K                                                          
[    0.004000] CPU: L2 cache: 512K                                                                                 
[    0.004000] CPU: Physical Processor ID: 0                                                                       
[    0.548243] CPU1: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09                                                 
[    0.548270] checking TSC synchronization [CPU#0 -> CPU#1]: passed.                                              
[    0.552064] Brought up 2 CPUs                                                                                   
[    0.552070] Total of 2 processors activated (9576.34 BogoMIPS).                                                 
[    0.552096] CPU0 attaching sched-domain:                                                                        
[    0.552100]  domain 0: span 0-1 level SIBLING                                                                   
[    0.552104]   groups: 0 1                                                                                       
[    0.552115] CPU1 attaching sched-domain:                                                                        
[    0.552118]  domain 0: span 0-1 level SIBLING                                                                   
[    0.552122]   groups: 1 0                                                                                       
[    0.552231] net_namespace: 840 bytes                                                                            
[    0.552231] Booting paravirtualized kernel on bare hardware                                                     
[    0.552473] Time: 23:18:06  Date: 03/24/09                                                                      
[    0.552514] NET: Registered protocol family 16                                                                  
[    0.552551] EISA bus registered                                                                                 
[    0.552551] ACPI: bus type pci registered                                                                       
[    0.553386] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2                                            
[    0.553390] PCI: Using configuration type 1 for base access                                                     
[    0.557483] ACPI: EC: Look up EC in DSDT                                                                        
[    0.570241] ACPI: Interpreter enabled                                                                           
[    0.570249] ACPI: (supports S0 S1 S4 S5)                                                                        
[    0.570277] ACPI: Using IOAPIC for interrupt routing                                                            
[    0.580408] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                              
[    0.580408] PCI: 0000:00:00.0 reg 10 32bit mmio: [f0000000, f03fffff]                                           
[    0.580408] PCI: 0000:00:1d.0 reg 20 io port: [cc00, cc1f]                                                      
[    0.580408] PCI: 0000:00:1d.1 reg 20 io port: [d000, d01f]                                                      
[    0.580408] PCI: 0000:00:1d.2 reg 20 io port: [d400, d41f]                                                      
[    0.580408] PCI: 0000:00:1d.3 reg 20 io port: [d800, d81f]                                                      
[    0.580469] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffa00000, ffa003ff]                                           
[    0.580529] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                                               
[    0.580536] pci 0000:00:1d.7: PME# disabled                                                                     
[    0.580624] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000                                                  
[    0.580632] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO                             
[    0.580637] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO                                      
[    0.580660] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]                                                            
[    0.580668] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]                                                            
[    0.580677] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]                                                            
[    0.580685] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]                                                            
[    0.580694] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]                                                      
[    0.580703] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]                                                       
[    0.580734] PCI: 0000:00:1f.2 reg 10 io port: [ec00, ec07]                                                      
[    0.580742] PCI: 0000:00:1f.2 reg 14 io port: [e800, e803]                                                      
[    0.580750] PCI: 0000:00:1f.2 reg 18 io port: [e400, e407]                                                      
[    0.580758] PCI: 0000:00:1f.2 reg 1c io port: [e000, e003]                                                      
[    0.580766] PCI: 0000:00:1f.2 reg 20 io port: [dc00, dc0f]                                                      
[    0.580824] PCI: 0000:00:1f.3 reg 20 io port: [c800, c81f]                                                      
[    0.580881] PCI: 0000:00:1f.5 reg 18 32bit mmio: [ffa00400, ffa005ff]                                           
[    0.580890] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [ffa00800, ffa008ff]                                           
[    0.580921] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold                                               
[    0.580927] pci 0000:00:1f.5: PME# disabled                                                                     
[    0.580990] PCI: 0000:01:00.0 reg 10 64bit mmio: [d0000000, dfffffff]                                           
[    0.581004] PCI: 0000:01:00.0 reg 18 64bit mmio: [ff820000, ff82ffff]                                           
[    0.581013] PCI: 0000:01:00.0 reg 20 io port: [a800, a8ff]                                                      
[    0.581026] PCI: 0000:01:00.0 reg 30 32bit mmio: [ff800000, ff81ffff]                                           
[    0.581050] pci 0000:01:00.0: supports D1                                                                       
[    0.581053] pci 0000:01:00.0: supports D2                                                                       
[    0.581091] PCI: 0000:01:00.1 reg 10 64bit mmio: [ff830000, ff83ffff]                                           
[    0.581133] pci 0000:01:00.1: supports D1                                                                       
[    0.581136] pci 0000:01:00.1: supports D2                                                                       
[    0.581181] PCI: bridge 0000:00:01.0 io port: [a000, afff]                                                      
[    0.581187] PCI: bridge 0000:00:01.0 32bit mmio: [ff800000, ff8fffff]                                           
[    0.581192] PCI: bridge 0000:00:01.0 32bit mmio pref: [d0000000, efffffff]                                      
[    0.581235] PCI: 0000:02:03.0 reg 10 io port: [bc00, bc3f]                                                      
[    0.581282] pci 0000:02:03.0: supports D2                                                                       
[    0.581285] pci 0000:02:03.0: PME# supported from D0 D2 D3hot D3cold                                            
[    0.581291] pci 0000:02:03.0: PME# disabled                                                                     
[    0.584054] PCI: 0000:02:04.0 reg 10 32bit mmio: [f0401000, f0401fff]                                           
[    0.584135] PCI: 0000:02:04.1 reg 10 32bit mmio: [f0400000, f0400fff]                                           
[    0.584219] PCI: 0000:02:07.0 reg 10 32bit mmio: [ff900000, ff900fff]                                           
[    0.584265] pci 0000:02:07.0: supports D1                                                                       
[    0.584268] pci 0000:02:07.0: supports D2                                                                       
[    0.584271] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot                                                
[    0.584277] pci 0000:02:07.0: PME# disabled                                                                     
[    0.584313] PCI: 0000:02:08.0 reg 10 32bit mmio: [ff901000, ff901fff]                                           
[    0.584322] PCI: 0000:02:08.0 reg 14 io port: [b800, b83f]                                                      
[    0.584362] pci 0000:02:08.0: supports D1                                                                       
[    0.584365] pci 0000:02:08.0: supports D2                                                                       
[    0.584368] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold                                         
[    0.584374] pci 0000:02:08.0: PME# disabled                                                                     
[    0.584406] pci 0000:00:1e.0: transparent bridge                                                                
[    0.584412] PCI: bridge 0000:00:1e.0 io port: [b000, bfff]                                                      
[    0.584418] PCI: bridge 0000:00:1e.0 32bit mmio: [ff900000, ff9fffff]                                           
[    0.584425] PCI: bridge 0000:00:1e.0 32bit mmio pref: [f0400000, f04fffff]                                      
[    0.584440] bus 00 -> node 0                                                                                    
[    0.584451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                 
[    0.584660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]                                            
[    0.584802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]                                            
[    0.588283] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)                                  
[    0.588564] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)                                  
[    0.588843] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)                                  
[    0.589122] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)                                  
[    0.589402] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)                                  
[    0.589682] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.                     
[    0.589965] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.                     
[    0.590246] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)                                  
[    0.592122] ACPI: Power Resource [URP1] (off)                                                                   
[    0.592188] ACPI: Power Resource [FDDP] (off)                                                                   
[    0.592248] ACPI: Power Resource [LPTP] (off)                                                                   
[    0.592301] Linux Plug and Play Support v0.97 (c) Adam Belay                                                    
[    0.592301] pnp: PnP ACPI init                                                                                  
[    0.592301] ACPI: bus type pnp registered                                                                       
[    0.596849] pnp: PnP ACPI: found 11 devices                                                                     
[    0.596854] ACPI: ACPI bus type pnp unregistered                                                                
[    0.596861] PnPBIOS: Disabled by ACPI PNP                                                                       
[    0.600084] PCI: Using ACPI for IRQ routing                                                                     
[    0.608048] NET: Registered protocol family 8                                                                   
[    0.608053] NET: Registered protocol family 20                                                                  
[    0.608084] NetLabel: Initializing                                                                              
[    0.608084] NetLabel:  domain hash size = 128                                                                   
[    0.608084] NetLabel:  protocols = UNLABELED CIPSOv4                                                            
[    0.608095] NetLabel:  unlabeled traffic allowed by default                                                     
[    0.608199] hpet clockevent registered                                                                          
[    0.608205] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                                             
[    0.608214] hpet0: 3 64-bit timers, 14318180 Hz                                                                 
[    0.610108] tracer: 772 pages allocated for 65536 entries of 48 bytes                                           
[    0.610113]    actual entries 65620                                                                             
[    0.610285] AppArmor: AppArmor Filesystem Enabled                                                               
[    0.610307] ACPI: RTC can wake from S4                                                                          
[    0.616081] system 00:07: ioport range 0x4d0-0x4d1 has been reserved                                            
[    0.616095] system 00:09: ioport range 0x400-0x47f has been reserved                                            
[    0.616099] system 00:09: ioport range 0x680-0x6ff has been reserved                                            
[    0.616103] system 00:09: ioport range 0x500-0x53f has been reserved                                            
[    0.616108] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved                                   
[    0.616113] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved                                   
[    0.616118] system 00:09: iomem range 0xfed20000-0xfed9ffff could not be reserved                               
[    0.616129] system 00:0a: iomem range 0x0-0x9ffff could not be reserved                                         
[    0.616133] system 00:0a: iomem range 0xc0000-0xd7fff could not be reserved                                     
[    0.616138] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved                                     
[    0.616142] system 00:0a: iomem range 0x100000-0x3fffffff could not be reserved                                 
[    0.651930] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01                                                 
[    0.651936] pci 0000:00:01.0:   IO window: 0xa000-0xafff                                                        
[    0.651944] pci 0000:00:01.0:   MEM window: 0xff800000-0xff8fffff                                               
[    0.651950] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000efffffff                              
[    0.651959] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02                                                 
[    0.651964] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff                                                        
[    0.651972] pci 0000:00:1e.0:   MEM window: 0xff900000-0xff9fffff                                               
[    0.651978] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0400000-0x000000f04fffff                              
[    0.652000] pci 0000:00:1e.0: setting latency timer to 64                                                       
[    0.652006] bus: 00 index 0 io port: [0, ffff]                                                                  
[    0.652010] bus: 00 index 1 mmio: [0, ffffffff]                                                                 
[    0.652014] bus: 01 index 0 io port: [a000, afff]                                                               
[    0.652017] bus: 01 index 1 mmio: [ff800000, ff8fffff]                                                          
[    0.652021] bus: 01 index 2 mmio: [d0000000, efffffff]                                                          
[    0.652024] bus: 01 index 3 mmio: [0, 0]                                                                        
[    0.652040] bus: 02 index 0 io port: [b000, bfff]                                                               
[    0.652043] bus: 02 index 1 mmio: [ff900000, ff9fffff]                                                          
[    0.652047] bus: 02 index 2 mmio: [f0400000, f04fffff]                                                          
[    0.652050] bus: 02 index 3 io port: [0, ffff]                                                                  
[    0.652053] bus: 02 index 4 mmio: [0, ffffffff]                                                                 
[    0.652069] NET: Registered protocol family 2                                                                   
[    0.664119] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                   
[    0.664551] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                
[    0.665080] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)                                         
[    0.665538] TCP: Hash tables configured (established 131072 bind 65536)                                         
[    0.665543] TCP reno registered                                                                                 
[    0.672173] NET: Registered protocol family 1                                                                   
[    0.672342] checking if image is initramfs... it is                                                             
[    1.108334] Switched to high resolution mode on CPU 1                                                           
[    1.112069] Switched to high resolution mode on CPU 0                                                           
[    1.504687] Freeing initrd memory: 8009k freed                                                                  
[    1.506255] audit: initializing netlink socket (disabled)                                                       
[    1.506289] type=2000 audit(1237936686.505:1): initialized                                                      
[    1.511806] highmem bounce pool size: 64 pages                                                                  
[    1.511818] HugeTLB registered 4 MB page size, pre-allocated 0 pages                                            
[    1.516480] VFS: Disk quotas dquot_6.5.1                                                                        
[    1.516654] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                          
[    1.516842] msgmni has been set to 1761                                                                         
[    1.517090] io scheduler noop registered                                                                        
[    1.517095] io scheduler anticipatory registered                                                                
[    1.517099] io scheduler deadline registered                                                                    
[    1.517122] io scheduler cfq registered (default)                                                               
[    9.516015] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001                                    
[    9.516153] pci 0000:01:00.0: Boot video device                                                                 
[    9.516177] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling                                  
[    9.516969] isapnp: Scanning for PnP cards...                                                                   
[    9.870642] isapnp: No Plug & Play device found                                                                 
[    9.944478] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                               
[    9.944640] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                
[    9.945886] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                     
[    9.946224] serial 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19                                     
[    9.953317] brd: module loaded                                                                                  
[    9.953447] input: Macintosh mouse button emulation as /devices/virtual/input/input0                            
[    9.953833] PNP: No PS/2 controller found. Probing ports directly.                                              
[    9.958106] serio: i8042 KBD port at 0x60,0x64 irq 1                                                            
[    9.958118] serio: i8042 AUX port at 0x60,0x64 irq 12                                                           
[    9.960274] mice: PS/2 mouse device common for all mice                                                         
[    9.960542] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0                                               
[    9.960569] rtc0: alarms up to one month, hpet irqs                                                             
[    9.960877] EISA: Probing bus 0 at eisa.0                                                                       
[    9.960928] EISA: Detected 0 cards.                                                                             
[    9.960933] cpuidle: using governor ladder                                                                      
[    9.960937] cpuidle: using governor menu                                                                        
[    9.961838] TCP cubic registered                                                                                
[    9.961878] Using IPI No-Shortcut mode                                                                          
[    9.962319] registered taskstats version 1                                                                      
[    9.962518]   Magic number: 1:497:353                                                                           
[    9.962659] rtc_cmos 00:02: setting system clock to 2009-03-24 23:18:15 UTC (1237936695)                        
[    9.962664] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                
[    9.962667] EDD information not available.                                                                      
[    9.963033] Freeing unused kernel memory: 424k freed                                                            
[    9.963104] Write protecting the kernel text: 2580k                                                             
[    9.963147] Write protecting the kernel read-only data: 940k                                                    
[   10.334323] fuse init (API version 7.9)                                                                         
[   10.361982] processor ACPI0007:00: registered as cooling_device0                                                
[   10.361995] ACPI: Processor [CPU1] (supports 8 throttling states)                                               
[   10.362179] processor ACPI0007:01: registered as cooling_device1                                                
[   10.362191] ACPI: Processor [CPU2] (supports 8 throttling states)                                               
[   10.616898] usbcore: registered new interface driver usbfs                                                      
[   10.616953] usbcore: registered new interface driver hub                                                        
[   10.624112] usbcore: registered new device driver usb                                                           
[   10.629313] USB Universal Host Controller Interface driver v3.0                                                 
[   10.629384] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                   
[   10.629399] uhci_hcd 0000:00:1d.0: setting latency timer to 64                                                  
[   10.629407] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                                         
[   10.629491] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1                                
[   10.629537] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00                                                   
[   10.629801] usb usb1: configuration #1 chosen from 1 choice                                                     
[   10.629872] hub 1-0:1.0: USB hub found                                                                          
[   10.629887] hub 1-0:1.0: 2 ports detected                                                                       
[   10.652269] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after                   
[   10.840671] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                   
[   10.840689] uhci_hcd 0000:00:1d.1: setting latency timer to 64                                                  
[   10.840697] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                                         
[   10.840767] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2                                
[   10.840812] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000                                                   
[   10.841070] usb usb2: configuration #1 chosen from 1 choice                                                     
[   10.841148] hub 2-0:1.0: USB hub found                                                                          
[   10.841166] hub 2-0:1.0: 2 ports detected                                                                       
[   10.949040] usb 1-2: new full speed USB device using uhci_hcd and address 2                                     
[   11.052405] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                   
[   11.052422] uhci_hcd 0000:00:1d.2: setting latency timer to 64                                                  
[   11.052430] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                                         
[   11.052491] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3                                
[   11.052535] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400                                                   
[   11.052737] usb usb3: configuration #1 chosen from 1 choice                                                     
[   11.052817] hub 3-0:1.0: USB hub found                                                                          
[   11.052832] hub 3-0:1.0: 2 ports detected                                                                       
[   11.103931] No dock devices found.                                                                              
[   11.119184] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI                                               
[   11.119192] e100: Copyright(c) 1999-2006 Intel Corporation                                                      
[   11.126519] usb 1-2: configuration #1 chosen from 1 choice                                                      
[   11.209927] SCSI subsystem initialized                                                                          
[   11.258228] usb 2-1: new full speed USB device using uhci_hcd and address 2                                     
[   11.259331] libata version 3.00 loaded.                                                                         
[   11.260576] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                   
[   11.260593] uhci_hcd 0000:00:1d.3: setting latency timer to 64                                                  
[   11.260601] uhci_hcd 0000:00:1d.3: UHCI Host Controller                                                         
[   11.260667] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4                                
[   11.260700] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800                                                   
[   11.260939] usb usb4: configuration #1 chosen from 1 choice                                                     
[   11.261012] hub 4-0:1.0: USB hub found                                                                          
[   11.261030] hub 4-0:1.0: 2 ports detected                                                                       
[   11.368946] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23                                   
[   11.368977] ehci_hcd 0000:00:1d.7: setting latency timer to 64                                                  
[   11.368987] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                                         
[   11.369094] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5                                
[   11.373060] ehci_hcd 0000:00:1d.7: debug port 1                                                                 
[   11.373075] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported                                      
[   11.373114] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa00000                                                    
[   11.389046] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004                               
[   11.389366] usb usb5: configuration #1 chosen from 1 choice                                                     
[   11.389464] hub 5-0:1.0: USB hub found                                                                          
[   11.389485] hub 5-0:1.0: 8 ports detected                                                                       
[   11.599612] ata_piix 0000:00:1f.1: version 2.12                                                                 
[   11.599630] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)                                               
[   11.599643] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                   
[   11.599719] ata_piix 0000:00:1f.1: setting latency timer to 64                                                  
[   11.600139] scsi0 : ata_piix                                                                                    
[   11.601452] scsi1 : ata_piix                                                                                    
[   11.605407] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14                                     
[   11.605415] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15                                     
[   11.785043] usb 2-1: device not accepting address 2, error -71                                                  
[   11.792690] ata1.00: ATA-8: WDC WD3200AAJB-00WGA0, 00.02C01, max UDMA/100                                       
[   11.792699] ata1.00: 625142448 sectors, multi 16: LBA48                                                         
[   11.805024] ata1.00: configured for UDMA/100                                                                    
[   11.841124] hub 2-0:1.0: unable to enumerate USB device on port 1                                               
[   11.994844] ata2.00: ATAPI: LITE-ON DVDRW SHM-165H6S, HS06, max UDMA/66                                         
[   11.994900] ata2.01: ATAPI: MATSHITADVD-RAM LF-D211A, A109, max UDMA/33                                         
[   12.025316] ata2.00: configured for UDMA/66                                                                     
[   12.041399] ata2.01: configured for UDMA/33                                                                     
[   12.041581] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJB-0 00.0 PQ: 0 ANSI: 5                        
[   12.042615] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SHM-165H6S HS06 PQ: 0 ANSI: 5                        
[   12.044119] scsi 1:0:1:0: CD-ROM            MATSHITA DVD-RAM LF-D211A A109 PQ: 0 ANSI: 5                        
[   12.044318] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                   
[   12.044328] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]                                                          
[   12.044400] ata_piix 0000:00:1f.2: setting latency timer to 64                                                  
[   12.044502] scsi2 : ata_piix                                                                                    
[   12.057854] scsi3 : ata_piix                                                                                    
[   12.060337] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18                                   
[   12.060346] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18                                   
[   12.096056] usb 1-2: USB disconnect, address 2                                                                  
[   12.389555] ata4.00: ATA-6: WDC WD2000JD-22HBC0, 08.02D08, max UDMA/133                                         
[   12.389561] ata4.00: 390721968 sectors, multi 16: LBA48                                                         
[   12.405544] ata4.00: configured for UDMA/133                                                                    
[   12.405718] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2000JD-22H 08.0 PQ: 0 ANSI: 5                        
[   12.405886] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20                                       
[   12.427973] e100 0000:02:08.0: PME# disabled                                                                    
[   12.428690] e100: eth0: e100_probe: addr 0xff901000, irq 20, MAC addr 00:13:20:2f:a3:03                         
[   12.429087] ohci1394 0000:02:07.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                   
[   12.449031] usb 5-3: new high speed USB device using ehci_hcd and address 3                                     
[   12.480961] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[ff900000-ff9007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]                                                                                                   
[   12.527715] scsi 0:0:0:0: Attached scsi generic sg0 type 0                                                      
[   12.527797] scsi 1:0:0:0: Attached scsi generic sg1 type 5                                                      
[   12.527882] scsi 1:0:1:0: Attached scsi generic sg2 type 5                                                      
[   12.527965] scsi 3:0:0:0: Attached scsi generic sg3 type 0                                                      
[   12.582649] usb 5-3: configuration #1 chosen from 1 choice                                                      
[   12.582944] Driver 'sd' needs updating - please use bus_type methods                                            
[   12.583242] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)                                   
[   12.583289] sd 0:0:0:0: [sda] Write Protect is off                                                              
[   12.583297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                           
[   12.583391] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA             
[   12.583581] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)                                   
[   12.583636] sd 0:0:0:0: [sda] Write Protect is off                                                              
[   12.583645] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                           
[   12.583737] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA             
[   12.583751]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods                        
[   12.606347]  sda5 >                                                                                             
[   12.606676] sd 0:0:0:0: [sda] Attached SCSI disk                                                                
[   12.606877] sd 3:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)                                   
[   12.606917] sd 3:0:0:0: [sdb] Write Protect is off                                                              
[   12.606923] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00                                                           
[   12.606988] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA             
[   12.607130] sd 3:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)                                   
[   12.607171] sd 3:0:0:0: [sdb] Write Protect is off                                                              
[   12.607178] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00                                                           
[   12.607250] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA             
[   12.607260]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray                          
[   12.612599] Uniform CD-ROM driver Revision: 3.20                                                                
[   12.612774] sr 1:0:0:0: Attached scsi CD-ROM sr0                                                                
[   12.615765] sr1: scsi3-mmc drive: 0x/0x dvd-ram cd/rw xa/form2 cdda tray                                        
[   12.615919] sr 1:0:1:0: Attached scsi CD-ROM sr1                                                                
[   12.622255]  sdb1                                                                                               
[   12.622434] sd 3:0:0:0: [sdb] Attached SCSI disk                                                                
[   12.760035] usb 5-5: new high speed USB device using ehci_hcd and address 5                                     
[   12.888600] usb 5-5: configuration #1 chosen from 1 choice                                                      
[   12.888744] hub 5-5:1.0: USB hub found                                                                          
[   12.888922] hub 5-5:1.0: 4 ports detected                                                                       
[   13.097466] usbcore: registered new interface driver libusual                                                   
[   13.113525] Initializing USB Mass Storage driver...                                                             
[   13.145805] PM: Starting manual resume from disk                                                                
[   13.145811] PM: Resume from partition 8:5                                                                       
[   13.145815] PM: Checking hibernation image.                                                                     
[   13.146044] PM: Resume from disk failed.                                                                        
[   13.215943] kjournald starting.  Commit interval 5 seconds                                                      
[   13.215957] EXT3-fs: mounted filesystem with ordered data mode.                                                 
[   13.337046] usb 1-2: new full speed USB device using uhci_hcd and address 3                                     
[   13.510299] usb 1-2: configuration #1 chosen from 1 choice                                                      
[   13.752028] usb 2-2: new low speed USB device using uhci_hcd and address 4                                      
[   13.761239] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00132000002fa303]                                     
[   13.929539] usb 2-2: configuration #1 chosen from 1 choice                                                      
[   13.933457] scsi4 : SCSI emulation for USB Mass Storage devices                                                 
[   13.933631] usb-storage: device found at 3                                                                      
[   13.933635] usb-storage: waiting for device to settle before scanning                                           
[   14.021122] usb 5-5.4: new high speed USB device using ehci_hcd and address 6                                   
[   14.130776] usb 5-5.4: configuration #1 chosen from 1 choice                                                    
[   14.131444] scsi5 : SCSI emulation for USB Mass Storage devices                                                 
[   14.131587] usb-storage: device found at 6                                                                      
[   14.131593] usb-storage: waiting for device to settle before scanning                                           
[   14.131615] usbcore: registered new interface driver usb-storage                                                
[   14.131621] USB Mass Storage support registered.                                                                
[   18.492242] udevd version 124 started                                                                           
[   18.936396] usb-storage: device scan complete                                                                   
[   18.981059] scsi 4:0:0:0: Direct-Access     ST340083 2A               0811 PQ: 0 ANSI: 0                        
[   19.056302] sd 4:0:0:0: [sdc] 781422768 512-byte hardware sectors (400088 MB)                                   
[   19.057554] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled                                              
[   19.057562] sd 4:0:0:0: [sdc] Assuming drive cache: write through                                               
[   19.058550] sd 4:0:0:0: [sdc] 781422768 512-byte hardware sectors (400088 MB)                                   
[   19.059797] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled                                              
[   19.059805] sd 4:0:0:0: [sdc] Assuming drive cache: write through                                               
[   19.059859]  sdc: sdc1                                                                                          
[   19.080703] sd 4:0:0:0: [sdc] Attached SCSI disk                                                                
[   19.080978] sd 4:0:0:0: Attached scsi generic sg4 type 0                                                        
[   19.132359] usb-storage: device scan complete                                                                   
[   19.149044] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0                        
[   19.165046] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0                        
[   19.177050] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0                        
[   19.185051] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0                        
[   19.209504] Linux agpgart interface v0.103                                                                      
[   19.220437] sd 5:0:0:0: [sdd] Attached SCSI removable disk                                                      
[   19.220727] sd 5:0:0:0: Attached scsi generic sg5 type 0                                                        
[   19.222059] sd 5:0:0:1: [sde] Attached SCSI removable disk                                                      
[   19.222351] sd 5:0:0:1: Attached scsi generic sg6 type 0                                                        
[   19.308364] agpgart-intel 0000:00:00.0: Intel 865 Chipset                                                       
[   19.308924] agpgart-intel 0000:00:00.0: AGP aperture is 4M @ 0xf0000000                                         
[   19.408351] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                     
[   19.487945] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4                                        
[   19.548880] iTCO_vendor_support: vendor-support=0                                                               
[   19.584297] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)                                       
[   19.584509] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)                              
[   19.591486] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                                                
[   19.717964] intel_rng: Firmware space is locked read-only. If you can't or                                      
[   19.717969] intel_rng: don't want to disable this in firmware setup, and if                                     
[   19.717973] intel_rng: you are certain that your system has a functional                                        
[   19.717977] intel_rng: RNG, try using the 'no_fwh_detect' option.                                               
[   19.768567] sd 5:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)                                       
[   19.769571] sd 5:0:0:2: [sdf] Write Protect is off                                                              
[   19.769579] sd 5:0:0:2: [sdf] Mode Sense: 03 00 00 00                                                           
[   19.769586] sd 5:0:0:2: [sdf] Assuming drive cache: write through                                               
[   19.771567] sd 5:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)                                       
[   19.772566] sd 5:0:0:2: [sdf] Write Protect is off                                                              
[   19.772574] sd 5:0:0:2: [sdf] Mode Sense: 03 00 00 00                                                           
[   19.772580] sd 5:0:0:2: [sdf] Assuming drive cache: write through                                               
[   19.772643]  sdf: sdf1                                                                                          
[   19.934217] sd 5:0:0:2: [sdf] Attached SCSI removable disk                                                      
[   19.934474] sd 5:0:0:2: Attached scsi generic sg7 type 0                                                        
[   19.935633] sd 5:0:0:3: [sdg] Attached SCSI removable disk                                                      
[   19.935847] sd 5:0:0:3: Attached scsi generic sg8 type 0                                                        
[   20.425516] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1                           
[   20.456056] ACPI: Power Button (FF) [PWRF]                                                                      
[   20.456334] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2                  
[   20.488043] ACPI: Sleep Button (CM) [SLPB]                                                                      
[   20.599088] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel. 
[   21.021043] [fglrx] Maximum main memory to use for locked dma buffers: 925 MBytes.                              
[   21.022204] [fglrx]   vendor: 1002 device: 71c2 count: 1                                                        
[   21.024829] [fglrx] ioport: bar 4, base 0xa800, size: 0x100                                                     
[   21.024850] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                        
[   21.026626] [fglrx] PAT is enabled successfully!                                                                
[   21.026679] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors                                    
[   21.690482] parport_pc 00:06: reported by Plug and Play ACPI                                                    
[   21.690545] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]                                                 
[   21.726446] Linux video capture interface: v2.00                                                                
[   21.888522] bttv: driver version 0.9.17 loaded                                                                  
[   21.888530] bttv: using 8 buffers with 2080k (520 pages) each for capture                                       
[   21.890743] bttv: Bt8xx card found (0).                                                                         
[   21.890770] bttv 0000:02:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                       
[   21.890788] bttv0: Bt878 (rev 17) at 0000:02:04.0, irq: 18, latency: 32, mmio: 0xf0401000                       
[   21.890814] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb                           
[   21.890824] bttv0: using: Hauppauge (bt878) [card=10,autodetected]                                              
[   21.890865] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]                                           
[   21.893363] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]                                                
[   21.958273] tveeprom 0-0050: Hauppauge model 44811, rev D123, serial# 6130045                                   
[   21.958283] tveeprom 0-0050: tuner model is Philips FM1236 (idx 23, type 2)                                     
[   21.958292] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)                                                 
[   21.958298] tveeprom 0-0050: audio processor is None (idx 0)                                                    
[   21.958304] tveeprom 0-0050: has radio                                                                          
[   21.958309] bttv0: Hauppauge eeprom indicates model#44811                                                       
[   21.958316] bttv0: tuner type=2                                                                                 
[   21.958324] bttv0: i2c: checking for MSP34xx @ 0x80... not found                                                
[   22.144245] bttv0: i2c: checking for TDA9875 @ 0xb0... not found                                                
[   22.147630] bttv0: i2c: checking for TDA7432 @ 0x8a... not found                                                
[   22.412327] usbcore: registered new interface driver hiddev                                                     
[   22.440758] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input3     
[   22.481360] input,hidraw0: USB HID v1.11 Keyboard [A4Tech RF USB Receiver] on usb-0000:00:1d.1-2                
[   22.521843] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.1/input/input4     
[   22.568320] input,hidraw1: USB HID v1.11 Mouse [A4Tech RF USB Receiver] on usb-0000:00:1d.1-2                   
[   22.568377] usbcore: registered new interface driver usbhid                                                     
[   22.568387] usbhid: v2.6:USB HID core driver                                                                    
[   22.620786] tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])                                                    
[   22.727469] input: PC Speaker as /devices/platform/pcspkr/input/input5                                          
[   22.869830] tuner-simple 0-0061: creating new instance                                                          
[   22.869841] tuner-simple 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))                   
[   22.879563] bttv0: registered device video0                                                                     
[   22.879679] bttv0: registered device vbi0                                                                       
[   22.879771] bttv0: registered device radio0                                                                     
[   22.879798] bttv0: PLL: 28636363 => 35468950 .. ok                                                              
[   22.912828] Bt87x 0000:02:04.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                      
[   22.913348] bt87x0: Using board 1, analog, digital (rate 32000 Hz)                                              
[   23.512284] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                  
[   23.512315] Intel ICH 0000:00:1f.5: setting latency timer to 64                                                 
[   23.937044] intel8x0_measure_ac97_clock: measured 54237 usecs                                                   
[   23.937051] intel8x0: clocking to 48000                                                                         
[   27.426122] lp0: using parport0 (interrupt-driven).                                                             
[   27.649736] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k                           
[   28.033809] EXT3 FS on sda1, internal journal                                                                   
[   30.325504] type=1505 audit(1237936716.032:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4337                                                                                      
[   30.548907] type=1505 audit(1237936716.252:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4342                                                                                             
[   30.549213] type=1505 audit(1237936716.256:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4342                                                                                                            
[   30.607625] type=1505 audit(1237936716.312:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4346                                                                                                           
[   30.661913] type=1505 audit(1237936716.367:6): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=4350                                                                                                   
[   30.826046] ip_tables: (C) 2000-2006 Netfilter Core Team                                                        
[   31.822729] ACPI: WMI: Mapper loaded                                                                            
[   33.063623] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)                            
[   35.309158] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)                                            
[   35.309172] apm: disabled - APM is not SMP safe.                                                                
[   35.653996] ppdev: user-space parallel port driver                                                              
[   38.832867] vboxdrv: Trying to deactivate the NMI watchdog permanently...                                       
[   38.832876] vboxdrv: Successfully done.                                                                         
[   38.832882] vboxdrv: Found 2 processor cores.                                                                   
[   38.833132] vboxdrv: fAsync=0 offMin=0x3e4 offMax=0x2078                                                        
[   38.833144] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.                                  
[   38.833152] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).                              
[   39.096159] NET: Registered protocol family 10                                                                  
[   39.097512] lo: Disabled Privacy Extensions                                                                     
[   41.478041] Bluetooth: Core ver 2.13                                                                            
[   41.479430] NET: Registered protocol family 31                                                                  
[   41.479444] Bluetooth: HCI device and connection manager initialized                                            
[   41.479453] Bluetooth: HCI socket layer initialized                                                             
[   41.525643] Bluetooth: L2CAP ver 2.11                                                                           
[   41.525654] Bluetooth: L2CAP socket layer initialized                                                           
[   41.555808] Bluetooth: RFCOMM socket layer initialized                                                          
[   41.557188] Bluetooth: RFCOMM TTY layer initialized                                                             
[   41.557201] Bluetooth: RFCOMM ver 1.10                                                                          
[   41.577398] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                                                        
[   41.577412] Bluetooth: BNEP filters: protocol multicast                                                         
[   41.626072] Bridge firewalling registered                                                                       
[   41.678342] Bluetooth: SCO (Voice Link) ver 0.6                                                                 
[   41.678351] Bluetooth: SCO socket layer initialized                                                             
[   43.148114] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)                            
[   45.073951] agpgart-intel 0000:00:00.0: AGP 3.0 bridge                                                          
[   45.074000] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode                                      
[   45.074077] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode                                          
[   45.074158] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)                                       
[   45.074314] [fglrx] Setup AGP aperture                                                                          
[   45.103927] [fglrx] CMM init INV FB MC:0xd0000000, length:0x10000000                                            
[   45.103955] [fglrx] Reserved FB block: Shared offset:0, size:1000000                                            
[   45.103964] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000                                       
[   45.103971] [fglrx] Reserved FB block: Unshared offset:ffbf000, size:41000                                      
[   45.746234] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                        
[   45.749123] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex                                            
[   45.786319] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                   
[   45.913871] NET: Registered protocol family 17                                                                  
[  136.952198] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[  168.647589] ppdev0: registered pardevice                                                                        
[  168.696060] ppdev0: unregistered pardevice                                                                      
[  198.948158] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[  632.936223] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[  664.949193] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1090.953845] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1104.948130] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1242.952112] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1268.953430] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1446.941137] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1642.953111] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1662.940201] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1712.953144] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1878.956626] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 1982.952195] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2132.936211] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2186.948228] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2426.936097] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2638.936188] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2660.945318] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2694.948260] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2695.696238] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2822.948121] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 2876.937254] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 3020.948595] usb 5-5.4: reset high speed USB device using ehci_hcd and address 6                                 
[ 3021.172963] usb 5-5.4: USB disconnect, address 6                                                                
[ 3021.175994] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176027] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176085] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176103] scsi 5:0:0:2: [sdf] READ CAPACITY failed                                                            
[ 3021.176108] scsi 5:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[ 3021.176116] scsi 5:0:0:2: [sdf] Sense not available.                                                            
[ 3021.176127] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176138] scsi 5:0:0:2: [sdf] Write Protect is off                                                            
[ 3021.176143] scsi 5:0:0:2: [sdf] Mode Sense: 00 00 00 00                                                         
[ 3021.176148] scsi 5:0:0:2: [sdf] Assuming drive cache: write through                                             
[ 3021.176165] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176178] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176193] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176208] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176217] scsi 5:0:0:2: [sdf] READ CAPACITY failed                                                            
[ 3021.176222] scsi 5:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[ 3021.176229] scsi 5:0:0:2: [sdf] Sense not available.                                                            
[ 3021.176239] scsi 5:0:0:2: rejecting I/O to dead device                                                          
[ 3021.176249] scsi 5:0:0:2: [sdf] Write Protect is off                                                            
[ 3021.176254] scsi 5:0:0:2: [sdf] Mode Sense: 00 00 00 00                                                         
[ 3021.176258] scsi 5:0:0:2: [sdf] Assuming drive cache: write through                                             
[ 3021.176293] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176310] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176325] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176334] scsi 5:0:0:0: [sdd] READ CAPACITY failed                                                            
[ 3021.176339] scsi 5:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[ 3021.176346] scsi 5:0:0:0: [sdd] Sense not available.                                                            
[ 3021.176356] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176365] scsi 5:0:0:0: [sdd] Write Protect is off                                                            
[ 3021.176371] scsi 5:0:0:0: [sdd] Mode Sense: 00 00 00 00                                                         
[ 3021.176375] scsi 5:0:0:0: [sdd] Assuming drive cache: write through                                             
[ 3021.176387] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176400] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176414] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176428] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176437] scsi 5:0:0:0: [sdd] READ CAPACITY failed                                                            
[ 3021.176442] scsi 5:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[ 3021.176449] scsi 5:0:0:0: [sdd] Sense not available.                                                            
[ 3021.176458] scsi 5:0:0:0: rejecting I/O to dead device                                                          
[ 3021.176468] scsi 5:0:0:0: [sdd] Write Protect is off                                                            
[ 3021.176473] scsi 5:0:0:0: [sdd] Mode Sense: 00 00 00 00                                                         
[ 3021.176477] scsi 5:0:0:0: [sdd] Assuming drive cache: write through                                             
[ 3021.176874] sd 5:0:0:3: [sdg] READ CAPACITY failed                                                              
[ 3021.176882] sd 5:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                   
[ 3021.176892] sd 5:0:0:3: [sdg] Sense not available.                                                              
[ 3021.176932] sd 5:0:0:3: [sdg] Write Protect is off                                                              
[ 3021.176939] sd 5:0:0:3: [sdg] Mode Sense: 00 00 00 00                                                           
[ 3021.176944] sd 5:0:0:3: [sdg] Assuming drive cache: write through                                               
[ 3021.177126] sd 5:0:0:3: [sdg] READ CAPACITY failed                                                              
[ 3021.177132] sd 5:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                   
[ 3021.177141] sd 5:0:0:3: [sdg] Sense not available.                                                              
[ 3021.177184] sd 5:0:0:3: [sdg] Write Protect is off                                                              
[ 3021.177190] sd 5:0:0:3: [sdg] Mode Sense: 00 00 00 00                                                           
[ 3021.177196] sd 5:0:0:3: [sdg] Assuming drive cache: write through                                               
[ 3021.186454] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186480] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186499] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186512] scsi 5:0:0:1: [sde] READ CAPACITY failed                                                            
[ 3021.186517] scsi 5:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[ 3021.186527] scsi 5:0:0:1: [sde] Sense not available.                                                            
[ 3021.186542] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186555] scsi 5:0:0:1: [sde] Write Protect is off                                                            
[ 3021.186561] scsi 5:0:0:1: [sde] Mode Sense: 00 00 00 00                                                         
[ 3021.186567] scsi 5:0:0:1: [sde] Assuming drive cache: write through                                             
[ 3021.186591] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186608] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186626] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186643] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186655] scsi 5:0:0:1: [sde] READ CAPACITY failed                                                            
[ 3021.186660] scsi 5:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[ 3021.186670] scsi 5:0:0:1: [sde] Sense not available.                                                            
[ 3021.186682] scsi 5:0:0:1: rejecting I/O to dead device                                                          
[ 3021.186694] scsi 5:0:0:1: [sde] Write Protect is off                                                            
[ 3021.186700] scsi 5:0:0:1: [sde] Mode Sense: 00 00 00 00                                                         
[ 3021.186706] scsi 5:0:0:1: [sde] Assuming drive cache: write through                                             
[ 3021.402155] usb 5-5.4: new high speed USB device using ehci_hcd and address 7                                   
[ 3021.511224] usb 5-5.4: configuration #1 chosen from 1 choice                                                    
[ 3021.512825] scsi6 : SCSI emulation for USB Mass Storage devices                                                 
[ 3021.515309] usb-storage: device found at 7                                                                      
[ 3021.515323] usb-storage: waiting for device to settle before scanning                                           
[ 3026.512286] usb-storage: device scan complete                                                                   
[ 3026.512880] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0                        
[ 3026.513916] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0                        
[ 3026.514751] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0                        
[ 3026.515381] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0                        
[ 3026.520166] sd 6:0:0:0: [sdd] Attached SCSI removable disk                                                      
[ 3026.525185] sd 6:0:0:0: Attached scsi generic sg5 type 0                                                        
[ 3026.527953] sd 6:0:0:1: [sde] Attached SCSI removable disk                                                      
[ 3026.529542] sd 6:0:0:1: Attached scsi generic sg6 type 0                                                        
[ 3027.081047] sd 6:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)                                       
[ 3027.083664] sd 6:0:0:2: [sdf] Write Protect is off                                                              
[ 3027.083679] sd 6:0:0:2: [sdf] Mode Sense: 03 00 00 00                                                           
[ 3027.083686] sd 6:0:0:2: [sdf] Assuming drive cache: write through                                               
[ 3027.089411] sd 6:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)                                       
[ 3027.091385] sd 6:0:0:2: [sdf] Write Protect is off                                                              
[ 3027.091432] sd 6:0:0:2: [sdf] Mode Sense: 03 00 00 00                                                           
[ 3027.091447] sd 6:0:0:2: [sdf] Assuming drive cache: write through                                               
[ 3027.091470]  sdf: sdf1                                                                                          
[ 3027.253198] sd 6:0:0:2: [sdf] Attached SCSI removable disk                                                      
[ 3027.253487] sd 6:0:0:2: Attached scsi generic sg7 type 0                                                        
[ 3027.259348] sd 6:0:0:3: [sdg] Attached SCSI removable disk                                                      
[ 3027.259582] sd 6:0:0:3: Attached scsi generic sg8 type 0                                                        
[ 3207.953203] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 3503.938125] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 3665.949168] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 4223.952259] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 4497.952167] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 4623.957106] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 5047.947466] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 5345.932155] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 5549.950942] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6153.949208] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6269.956169] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6313.956185] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6477.948428] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6511.954282] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6523.941108] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6731.952104] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6737.952133] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 6819.953202] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 7089.957236] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 7443.949157] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 7823.949321] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 7845.952209] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 7869.953149] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 8081.954489] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 8082.157216] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 8421.949190] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 8649.949329] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 8665.960180] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 9261.937381] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 9291.961190] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 9319.953255] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 9563.949700] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[ 9879.940730] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[10479.936141] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[10763.953183] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[10909.949104] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11165.949834] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11255.953583] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11335.936197] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11389.952092] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11401.936128] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11651.933355] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11745.939310] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11845.952146] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[11961.955118] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[12387.948220] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[12561.933415] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[12575.949498] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[12793.949104] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[12853.954135] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[13111.935806] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[13189.949160] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[13553.933541] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[13707.951876] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[13717.939989] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[13993.936306] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[14043.948131] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[14683.934885] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[15169.953262] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[15219.933291] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[15457.956120] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[16495.953335] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[16527.949188] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[16545.950861] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[16563.952151] usb 5-5.4: reset high speed USB device using ehci_hcd and address 7                                 
[16564.177985] usb 5-5.4: USB disconnect, address 7                                                                
[16564.178998] sd 6:0:0:1: [sde] READ CAPACITY failed                                                              
[16564.179010] sd 6:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                   
[16564.179020] sd 6:0:0:1: [sde] Sense not available.                                                              
[16564.180491] scsi 6:0:0:2: rejecting I/O to dead device                                                          
[16564.180517] scsi 6:0:0:2: [sdf] READ CAPACITY failed                                                            
[16564.180523] scsi 6:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[16564.180533] scsi 6:0:0:2: [sdf] Sense not available.                                                            
[16564.180546] scsi 6:0:0:2: rejecting I/O to dead device                                                          
[16564.180560] scsi 6:0:0:2: [sdf] Write Protect is off                                                            
[16564.180566] scsi 6:0:0:2: [sdf] Mode Sense: 00 00 00 00                                                         
[16564.180572] scsi 6:0:0:2: [sdf] Assuming drive cache: write through                                             
[16564.180593] scsi 6:0:0:2: rejecting I/O to dead device                                                          
[16564.180611] scsi 6:0:0:2: rejecting I/O to dead device                                                          
[16564.180630] scsi 6:0:0:2: rejecting I/O to dead device                                                          
[16564.180647] scsi 6:0:0:2: rejecting I/O to dead device                                                          
[16564.180659] scsi 6:0:0:2: [sdf] READ CAPACITY failed                                                            
[16564.180665] scsi 6:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[16564.180674] scsi 6:0:0:2: [sdf] Sense not available.                                                            
[16564.180687] scsi 6:0:0:2: rejecting I/O to dead device                                                          
[16564.180700] scsi 6:0:0:2: [sdf] Write Protect is off                                                            
[16564.180706] scsi 6:0:0:2: [sdf] Mode Sense: 00 00 00 00                                                         
[16564.180712] scsi 6:0:0:2: [sdf] Assuming drive cache: write through                                             
[16564.181730] scsi 6:0:0:3: rejecting I/O to dead device                                                          
[16564.181749] scsi 6:0:0:3: [sdg] READ CAPACITY failed                                                            
[16564.181754] scsi 6:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[16564.181764] scsi 6:0:0:3: [sdg] Sense not available.                                                            
[16564.181778] scsi 6:0:0:3: rejecting I/O to dead device                                                          
[16564.181792] scsi 6:0:0:3: [sdg] Write Protect is off                                                            
[16564.181798] scsi 6:0:0:3: [sdg] Mode Sense: 00 00 00 00                                                         
[16564.181805] scsi 6:0:0:3: [sdg] Assuming drive cache: write through                                             
[16564.181829] scsi 6:0:0:3: rejecting I/O to dead device                                                          
[16564.181846] scsi 6:0:0:3: rejecting I/O to dead device                                                          
[16564.181864] scsi 6:0:0:3: rejecting I/O to dead device                                                          
[16564.181882] scsi 6:0:0:3: rejecting I/O to dead device                                                          
[16564.181893] scsi 6:0:0:3: [sdg] READ CAPACITY failed                                                            
[16564.181898] scsi 6:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[16564.181908] scsi 6:0:0:3: [sdg] Sense not available.                                                            
[16564.181921] scsi 6:0:0:3: rejecting I/O to dead device                                                          
[16564.181932] scsi 6:0:0:3: [sdg] Write Protect is off                                                            
[16564.181938] scsi 6:0:0:3: [sdg] Mode Sense: 00 00 00 00                                                         
[16564.181944] scsi 6:0:0:3: [sdg] Assuming drive cache: write through                                             
[16564.182147] scsi 6:0:0:1: [sde] Write Protect is off                                                            
[16564.182155] scsi 6:0:0:1: [sde] Mode Sense: 00 00 00 00                                                         
[16564.182161] scsi 6:0:0:1: [sde] Assuming drive cache: write through                                             
[16564.182190] scsi 6:0:0:1: rejecting I/O to dead device                                                          
[16564.182213] scsi 6:0:0:1: rejecting I/O to dead device                                                          
[16564.182234] scsi 6:0:0:1: rejecting I/O to dead device                                                          
[16564.182255] scsi 6:0:0:1: rejecting I/O to dead device                                                          
[16564.182266] scsi 6:0:0:1: [sde] READ CAPACITY failed                                                            
[16564.182272] scsi 6:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[16564.182282] scsi 6:0:0:1: [sde] Sense not available.                                                            
[16564.182297] scsi 6:0:0:1: rejecting I/O to dead device                                                          
[16564.182310] scsi 6:0:0:1: [sde] Write Protect is off                                                            
[16564.182317] scsi 6:0:0:1: [sde] Mode Sense: 00 00 00 00                                                         
[16564.182322] scsi 6:0:0:1: [sde] Assuming drive cache: write through                                             
[16564.182867] scsi 6:0:0:0: rejecting I/O to dead device                                                          
[16564.182882] scsi 6:0:0:0: [sdd] READ CAPACITY failed                                                            
[16564.182886] scsi 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[16564.182892] scsi 6:0:0:0: [sdd] Sense not available.                                                            
[16564.182904] scsi 6:0:0:0: rejecting I/O to dead device                                                          
[16564.182913] scsi 6:0:0:0: [sdd] Write Protect is off                                                            
[16564.182917] scsi 6:0:0:0: [sdd] Mode Sense: 00 00 00 00                                                         
[16564.182920] scsi 6:0:0:0: [sdd] Assuming drive cache: write through                                             
[16564.182936] scsi 6:0:0:0: rejecting I/O to dead device                                                          
[16564.182948] scsi 6:0:0:0: rejecting I/O to dead device                                                          
[16564.182985] scsi 6:0:0:0: rejecting I/O to dead device                                                          
[16564.182997] scsi 6:0:0:0: rejecting I/O to dead device                                                          
[16564.183005] scsi 6:0:0:0: [sdd] READ CAPACITY failed                                                            
[16564.183009] scsi 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                 
[16564.183014] scsi 6:0:0:0: [sdd] Sense not available.                                                            
[16564.183022] scsi 6:0:0:0: rejecting I/O to dead device                                                          
[16564.183031] scsi 6:0:0:0: [sdd] Write Protect is off                                                            
[16564.183035] scsi 6:0:0:0: [sdd] Mode Sense: 00 00 00 00                                                         
[16564.183038] scsi 6:0:0:0: [sdd] Assuming drive cache: write through                                             
[16564.401246] usb 5-5.4: new high speed USB device using ehci_hcd and address 8                                   
[16564.514985] usb 5-5.4: configuration #1 chosen from 1 choice                                                    
[16564.517938] scsi7 : SCSI emulation for USB Mass Storage devices                                                 
[16564.519880] usb-storage: device found at 8                                                                      
[16564.519890] usb-storage: waiting for device to settle before scanning                                           
[16569.517922] usb-storage: device scan complete                                                                   
[16569.518880] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0                        
[16569.519524] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0                        
[16569.520144] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0                        
[16569.523598] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0                        
[16569.526106] sd 7:0:0:0: [sdd] Attached SCSI removable disk                                                      
[16569.526415] sd 7:0:0:0: Attached scsi generic sg5 type 0                                                        
[16569.528700] sd 7:0:0:1: [sde] Attached SCSI removable disk                                                      
[16569.543893] sd 7:0:0:1: Attached scsi generic sg6 type 0                                                        
[16570.094058] sd 7:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)                                       
[16570.098179] sd 7:0:0:2: [sdf] Write Protect is off                                                              
[16570.098201] sd 7:0:0:2: [sdf] Mode Sense: 03 00 00 00                                                           
[16570.098209] sd 7:0:0:2: [sdf] Assuming drive cache: write through                                               
[16570.108558] sd 7:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)                                       
[16570.111812] sd 7:0:0:2: [sdf] Write Protect is off                                                              
[16570.111826] sd 7:0:0:2: [sdf] Mode Sense: 03 00 00 00                                                           
[16570.111833] sd 7:0:0:2: [sdf] Assuming drive cache: write through                                               
[16570.114826]  sdf: sdf1                                                                                          
[16570.276443] sd 7:0:0:2: [sdf] Attached SCSI removable disk                                                      
[16570.276721] sd 7:0:0:2: Attached scsi generic sg7 type 0                                                        
[16570.288771] sd 7:0:0:3: [sdg] Attached SCSI removable disk                                                      
[16570.290149] sd 7:0:0:3: Attached scsi generic sg8 type 0                                                        
[18476.948162] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[19454.936194] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[21506.940113] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[21780.949673] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[25294.948082] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[25594.936127] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[26926.952194] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[27162.952098] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[28776.952151] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[28842.952198] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[29466.952189] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[29936.953203] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[30974.949264] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[37080.933406] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[38452.933172] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[40244.949135] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[41132.956204] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[42956.952158] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[46838.957484] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[48278.952198] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[48572.948198] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[49028.949880] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[49584.933918] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[50018.953093] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[50836.953223] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[51720.956182] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[52100.952218] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[53120.961673] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[57818.949156] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[58878.969881] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[59982.949229] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[61356.944273] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[62306.940121] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[63474.952226] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[64152.948118] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[65964.948275] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[68732.953149] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[69666.940148] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[71242.940196] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[72570.939404] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[73396.606729] type=1505 audit(1238010096.746:7): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=15483                                                                                  
[73397.183617] type=1505 audit(1238010097.322:8): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=15488                                                                                         
[73397.184414] type=1505 audit(1238010097.322:9): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=15488                                                                                                        
[73397.310927] type=1505 audit(1238010097.450:10): operation="profile_replace" name="/usr/sbin/mysqld" name2="default" pid=15492                                                                                                      
[73397.424842] type=1505 audit(1238010097.562:11): operation="profile_replace" name="/usr/sbin/mysqld-akonadi" name2="default" pid=15496                                                                                              
[73468.953207] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[74148.952130] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[75816.948190] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[77366.952137] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[80052.948680] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[84438.944160] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[85644.948143] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[87418.942987] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[88480.948416] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[89022.948127] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[89490.957346] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[90116.957145] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[93186.949162] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[93528.952233] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[93742.952182] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[95906.961113] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                 
[102328.952181] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[103550.960166] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[103892.949573] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[104692.948156] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[104828.944232] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[111376.948748] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[111684.936200] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[112508.953251] usb 5-5.4: reset high speed USB device using ehci_hcd and address 8                                
[112510.980941] usb 5-5.4: USB disconnect, address 8                                                               
[112510.984531] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.984563] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984586] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984606] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984618] scsi 7:0:0:1: [sde] READ CAPACITY failed                                                           
[112510.984624] scsi 7:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                
[112510.984634] scsi 7:0:0:1: [sde] Sense not available.                                                           
[112510.984648] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984662] scsi 7:0:0:1: [sde] Write Protect is off                                                           
[112510.984668] scsi 7:0:0:1: [sde] Mode Sense: 00 00 00 00                                                        
[112510.984674] scsi 7:0:0:1: [sde] Assuming drive cache: write through                                            
[112510.984693] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984711] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984729] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984747] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984758] scsi 7:0:0:1: [sde] READ CAPACITY failed                                                           
[112510.984764] scsi 7:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                
[112510.984773] scsi 7:0:0:1: [sde] Sense not available.                                                           
[112510.984786] scsi 7:0:0:1: rejecting I/O to dead device                                                         
[112510.984798] scsi 7:0:0:1: [sde] Write Protect is off                                                           
[112510.984804] scsi 7:0:0:1: [sde] Mode Sense: 00 00 00 00                                                        
[112510.984810] scsi 7:0:0:1: [sde] Assuming drive cache: write through                                            
[112510.984996] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985039] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985058] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985076] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985088] scsi 7:0:0:2: [sdf] READ CAPACITY failed                                                           
[112510.985093] scsi 7:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                
[112510.985103] scsi 7:0:0:2: [sdf] Sense not available.                                                           
[112510.985116] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985129] scsi 7:0:0:2: [sdf] Write Protect is off                                                           
[112510.985135] scsi 7:0:0:2: [sdf] Mode Sense: 00 00 00 00                                                        
[112510.985141] scsi 7:0:0:2: [sdf] Assuming drive cache: write through                                            
[112510.985158] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985174] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985193] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985211] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985222] scsi 7:0:0:2: [sdf] READ CAPACITY failed                                                           
[112510.985228] scsi 7:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                
[112510.985238] scsi 7:0:0:2: [sdf] Sense not available.                                                           
[112510.985250] scsi 7:0:0:2: rejecting I/O to dead device                                                         
[112510.985262] scsi 7:0:0:2: [sdf] Write Protect is off                                                           
[112510.985268] scsi 7:0:0:2: [sdf] Mode Sense: 00 00 00 00                                                        
[112510.985274] scsi 7:0:0:2: [sdf] Assuming drive cache: write through                                            
[112510.997722] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997758] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997771] scsi 7:0:0:3: [sdg] READ CAPACITY failed                                                           
[112510.997777] scsi 7:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                
[112510.997787] scsi 7:0:0:3: [sdg] Sense not available.                                                           
[112510.997802] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997815] scsi 7:0:0:3: [sdg] Write Protect is off                                                           
[112510.997821] scsi 7:0:0:3: [sdg] Mode Sense: 00 00 00 00                                                        
[112510.997827] scsi 7:0:0:3: [sdg] Assuming drive cache: write through                                            
[112510.997852] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997870] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997890] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997909] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997921] scsi 7:0:0:3: [sdg] READ CAPACITY failed                                                           
[112510.997927] scsi 7:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK                
[112510.997936] scsi 7:0:0:3: [sdg] Sense not available.                                                           
[112510.997948] scsi 7:0:0:3: rejecting I/O to dead device                                                         
[112510.997961] scsi 7:0:0:3: [sdg] Write Protect is off                                                           
[112510.997967] scsi 7:0:0:3: [sdg] Mode Sense: 00 00 00 00                                                        
[112510.997974] scsi 7:0:0:3: [sdg] Assuming drive cache: write through                                            
[112511.197321] usb 5-5.4: new high speed USB device using ehci_hcd and address 9                                  
[112511.308034] usb 5-5.4: configuration #1 chosen from 1 choice                                                   
[112511.308974] scsi8 : SCSI emulation for USB Mass Storage devices                                                
[112511.310375] usb-storage: device found at 9                                                                     
[112511.310384] usb-storage: waiting for device to settle before scanning                                          
[112516.308221] usb-storage: device scan complete                                                                  
[112516.309173] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0                       
[112516.309808] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0                       
[112516.310430] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0                       
[112516.311063] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0                       
[112516.315561] sd 8:0:0:0: [sdd] Attached SCSI removable disk                                                     
[112516.316793] sd 8:0:0:0: Attached scsi generic sg5 type 0                                                       
[112516.320831] sd 8:0:0:1: [sde] Attached SCSI removable disk                                                     
[112516.321917] sd 8:0:0:1: Attached scsi generic sg6 type 0                                                       
[112516.879711] sd 8:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)                                      
[112516.880701] sd 8:0:0:2: [sdf] Write Protect is off                                                             
[112516.880715] sd 8:0:0:2: [sdf] Mode Sense: 03 00 00 00                                                          
[112516.880722] sd 8:0:0:2: [sdf] Assuming drive cache: write through
[112516.885365] sd 8:0:0:2: [sdf] 2048000 512-byte hardware sectors (1049 MB)
[112516.886349] sd 8:0:0:2: [sdf] Write Protect is off
[112516.886364] sd 8:0:0:2: [sdf] Mode Sense: 03 00 00 00
[112516.886373] sd 8:0:0:2: [sdf] Assuming drive cache: write through
[112516.886388]  sdf: sdf1
[112517.048354] sd 8:0:0:2: [sdf] Attached SCSI removable disk
[112517.048640] sd 8:0:0:2: Attached scsi generic sg7 type 0
[112517.054994] sd 8:0:0:3: [sdg] Attached SCSI removable disk
[112517.055229] sd 8:0:0:3: Attached scsi generic sg8 type 0
[113811.949455] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[115751.956406] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[115849.953443] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[116063.948191] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[116919.957760] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[116985.952410] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[118503.950469] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[122347.945246] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[127687.952203] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[130839.948156] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[136463.953124] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[138157.961178] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[138765.949298] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[141287.936277] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[141423.949309] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[142633.952352] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
[150545.944217] usb 5-5.4: reset high speed USB device using ehci_hcd and address 9
```

---

### Post by Paul Vega on 2009-03-31
Kia Ora 

I have followed the instructions but encounter the following error on trying to mount my itouch;
paul@paul-desktop:~$ sudo mount /dev/sda2
[sudo] password for paul: 
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I had my itouch jail-broken at a trusted Computer store in my home town.I am running ubuntu 8.04 (hardy). Can someone please offer suggestions to help?

Paul Vega


Further information 

On running Code: $ dmesg, I get the following lines of relevence when my itouch is plugged in:

[  404.008118] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  404.010828] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  404.011984] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  408.991393] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  408.994166] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  408.994677] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  422.639648] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  422.642403] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  422.643836] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  447.383263] eth1: no IPv6 routers present
[ 2295.019630] FAT: bogus number of reserved sectors
[ 2295.019647] VFS: Can't find a valid FAT filesystem on dev sda2.
[ 3117.874580] usb 5-1: USB disconnect, address 2
[ 3127.560370] usb 5-1: new high speed USB device using ehci_hcd and address 7
[ 3127.694849] usb 5-1: configuration #1 chosen from 3 choices

I then get the following lines of relevence when my itouch is not plugged in:
[  404.008118] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  404.010828] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  404.011984] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  408.991393] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  408.994166] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  408.994677] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  422.639648] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  422.642403] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  422.643836] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  447.383263] eth1: no IPv6 routers present
[ 2295.019630] FAT: bogus number of reserved sectors
[ 2295.019647] VFS: Can't find a valid FAT filesystem on dev sda2.
[ 3117.874580] usb 5-1: USB disconnect, address 2
[ 3127.560370] usb 5-1: new high speed USB device using ehci_hcd and address 7
[ 3127.694849] usb 5-1: configuration #1 chosen from 3 choices
[ 3587.280771] usb 5-1: USB disconnect, address 7

---

### Post by Paul Vega on 2009-04-07
Has this thread finished? Is there anyone who can recommend to me a plan of action?

---

### Post by cmcginty on 2009-06-08
gtkpod is not usable on my system. It runs excessively slow, to the point where any action takes 30 seconds or more.

1st) has anyone else noticed this in gtkpod?
2nd) what other programs can be used to sync files to the ipod.

---

### Post by pyrofreak99 on 2009-07-04
i was wondering if somebody could help me out i am using ipod nano 3rd gen on my kubuntu  and so far i cant get it to work i have tried everything

it wont even show up on the computer    could somebody please help

---

### Post by Floola on 2009-08-21
Floola 5.3 is out now. [http://www.floola.com](http://www.floola.com)

Now much faster than before.

---

### Post by chill32 on 2010-03-03
someone help me because i have the ipod nano 5th gen and it wont work

---

### Post by quirkification on 2010-06-16
AWESOME!!!
well I have a second gen iPod, so AWESOME!!!

---

### Post by ODECiF on 2010-06-23
It seems that this thread wasn't dead after all :o)

I have an issue on my iPod Video (5th gen, 60GB upgraded from 30 with original harddrive) and I can't seem to find the solution anywhere.

I have added music videos to my iPod with gtkpod, but I can't get them to show up under the "Music Videos"-tab on the iPod. This is quite annoying, since I have a lot of these music videos and some videos now in the same folder/tab (Videos/Movies(I think it is on the english iPods, have a Swedish one myself)).

Now, is there anyone who has managed to make their music videos (or anything at all) shoe up under the "Music Videos"-tab?

Thanks in advande

//ODECiF

---

### Post by vishal khialani on 2010-07-13
> **ODECiF said:**
> It seems that this thread wasn't dead after all :o)

I have an issue on my iPod Video (5th gen, 60GB upgraded from 30 with original harddrive) and I can't seem to find the solution anywhere.

I have added music videos to my iPod with gtkpod, but I can't get them to show up under the "Music Videos"-tab on the iPod. This is quite annoying, since I have a lot of these music videos and some videos now in the same folder/tab (Videos/Movies(I think it is on the english iPods, have a Swedish one myself)).

Now, is there anyone who has managed to make their music videos (or anything at all) shoe up under the "Music Videos"-tab?

Thanks in advande

//ODECiF

U are lucky I can't even get my 5gen ipod to work on my ubuntu how did u get it done ?

---

### Post by michael.the.bone on 2010-07-30
I've gone through the steps on page one, but when i get to the final step of mounting my ipod again i cant...

So, 

I added the command

/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0 

Into the document when it comes up, then save it. 

Then this message  appears in my terminal when i try to mount my ipod finally...

" michael@ubuntu:~$ sudo mkdir /mnt/ipod
mkdir: cannot create directory `/mnt/ipod': File exists
michael@ubuntu:~$ sudo gedit /etc/fstab
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0

michael@ubuntu:~$ /dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0
bash: /dev/sda2: Permission denied
michael@ubuntu:~$ "

Any ideas?

Cheers

---

### Post by TheStroj on 2010-07-30
> **michael.the.bone said:**
> I've gone through the steps on page one, but when i get to the final step of mounting my ipod again i cant...

So, 

I added the command

/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0 

Into the document when it comes up, then save it. 

Then this message  appears in my terminal when i try to mount my ipod finally...

" michael@ubuntu:~$ sudo mkdir /mnt/ipod
mkdir: cannot create directory `/mnt/ipod': File exists
michael@ubuntu:~$ sudo gedit /etc/fstab
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0

michael@ubuntu:~$ /dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0
bash: /dev/sda2: Permission denied
michael@ubuntu:~$ "

Any ideas?

Cheers

'File exists' means that the directory was already made
'Permission denied' means you don't have permission to acces that directory (usualy solved by making yourself root).

---

### Post by michael.the.bone on 2010-07-30
> **TheStroj said:**
> 'File exists' means that the directory was already made
'Permission denied' means you don't have permission to acces that directory (usualy solved by making yourself root).

Yeah, the file exists because this is the second time i have been through the steps because it didnt work first time round.

How do i make a root myself?

---

### Post by TheStroj on 2010-07-30
> **michael.the.bone said:**
> Yeah, the file exists because this is the second time i have been through the steps because it didnt work first time round.

How do i make a root myself?

By adding 'sudo' infront of command, example:

```
sudo command
```

then you must type your password (which will not be displayed).

OR

by running

```
sudo su
```

and type your password, the the rest of the commands

---

### Post by michael.the.bone on 2010-07-30
Thanks.

Still no ipod though, it says its mounted, but it doesn't show on my computer...

Is there any other options i can try ? - i have an old white ipod shuffle...

---

### Post by rob22941 on 2010-08-06
I have my ipod running with Amarok, Rhythmbox and gtkpod.

I'd like to be able to create a playlist and be able to randomize the playlist. Is there any way of doing this. I've tried in all 3 programs. Banshee wants to do something with the ipod database but I'd rather not erase my ipod and start from scratch right now-just don't have the time. Also I just ripped songs as a flac type and gtkpod will not copy to my ipod any ideas?

---

### Post by ubunter1 on 2010-08-12
so ive followed your tutorial the best i could, i just bought a ipod nano video 16gb, but am having a problem, when i get to the- sudo gedit /etc/fstab, you suggested to command, where do i put it in here-
 # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=77992d7a-b8ac-4e32-be3a-894e3c842dc6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2d45801a-e55f-488f-9f34-4317534fa8c9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 .

if i run the next line-/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0
in the terminal, it does nothing,
any help i would appreciate, would love to listen to my music at work again. thanks.

---

### Post by spegru on 2010-08-15
weirdly, i have been working with 3 fairly new ipods recently an the *just worked* on my (ubuntu based) linux mint 9 setup. they just appear in rhythmbox.
I guess this could be something extra that the mint guys did?
One thing I noticed in this thread though is talk of fstab etc. I'm surprised you would have to do that because afaik that is what you have to go to mount an internal hard disc (and I had to do that even on mint for one of my machines). I would expect ipod to mount automatically when plugged in - like a usb stick - at least so you can see inside.
BTW did you know you can get at your music as a simple usb drive - although file names are deliberately scrambled by apple


Heck even my kids like it because unlike windose or max you can copy all the music onto another pc.


I did have one problem though. One pc apparently crashed while transferring 13000 songs (I say apparently because I was out of the room at the time and my kids rebooted it mid-flow. I am not convinced it as not simply busy with so many songs). Anyway, although the PC and Rhythmbox came back ok, and the PC could still see into the music collection on the ipod, the ipod itself said it was empty - which it clearly wasn't really. This had me scratching my head for a couple of hours in  an embarrased way (the belonged to a friend of one of my kids). However I fixed that. When I last fiddled with ipods a couple of years ago (on opensuse and amarok) I remembered that syncing  and ejecting are very important for the ipod because apple seem to have gone out of their way to make things difficult. It seems there is an internal databased in  the ipod that needs some tag to be set properly for it to work.
Unfortunately the simple mount and eject method didnt work from rhythmbox so I tried gtkpod which although it seems a  bit more clunky as a music player in its own right, seems to have more features as an ipod controller. Anyway, i installed that from the repositories, and plugged in the ipod (and ignored the system requesting what to open the ipod with). gtkpod 'saw' the device and asked which model it was (a 6th gen ipod classic), even down to the colour! I selected the model and after a few moments all the music appeared in the gtkpod window.
I then ejected the ipod *from within gtkpod* and a little messgae popped up saying (something like) 'synchronising' (I then also ejected to ipod from the OS just to be sure).
Hey presto - all the music and album art etc (that was always there really) is now visible from the ipod again (end of embarrassment)!

As I said, normally, rhythmbox seems to do all this ok and certainly another, identical but perhaps not so full device was fine with just rhythmbox without resorting to gtkpod, but it had gone wrong fo soem reason and gtkpod fixed it.


Well maybe all this ease was because of something the mint guys did, or maybe not, but the 2 versions of mint I used (8&9) are based on Ubuntu 9.10 and 10.04 respectively so if you are using anything older it ight be worth trying them (or Mint)

---

### Post by dan06 on 2010-08-29
Running Lucid Lynx, With a freshly restored (through a friend's computer with itunes) 5th Gen iPod:

Nothing shows up on any music programs (banshee, rhythmbox, gtkpod) or on the desktop

I tried to use this how-to but I get the following errors when I use the dmesg command:

```
[12623.875368] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[12623.876330] sd 4:0:0:0: Attached scsi generic sg2 type 0
[12623.892362] sd 4:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[12623.895340] sd 4:0:0:0: [sdb] Write Protect is off
[12623.895349] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[12623.895355] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12623.904429] sd 4:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[12623.907419] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12623.907433]  sdb: sdb1
[12623.940770] sd 4:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)
[12623.943785] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12623.943792] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[12638.990830] sd 4:0:0:0: [sdb] Unhandled sense code
[12638.990839] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12638.990847] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12638.990858] Info fld=0x0
[12638.990861] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12638.990871] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e c0 00 00 01 00
[12638.990892] end_request: I/O error, dev sdb, sector 155907584
[12638.990902] Buffer I/O error on device sdb, logical block 19488448
[12649.013150] sd 4:0:0:0: [sdb] Unhandled sense code
[12649.013158] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12649.013167] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12649.013177] Info fld=0x0
[12649.013181] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12649.013190] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e c0 00 00 01 00
[12649.013212] end_request: I/O error, dev sdb, sector 155907584
[12649.013222] Buffer I/O error on device sdb, logical block 19488448
[12659.031485] sd 4:0:0:0: [sdb] Unhandled sense code
[12659.031494] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12659.031502] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12659.031512] Info fld=0x0
[12659.031516] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12659.031526] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d5 00 00 01 00
[12659.031547] end_request: I/O error, dev sdb, sector 155907752
[12659.031557] Buffer I/O error on device sdb, logical block 19488469
[12669.053806] sd 4:0:0:0: [sdb] Unhandled sense code
[12669.053815] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12669.053823] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12669.053833] Info fld=0x0
[12669.053837] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12669.053847] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d5 00 00 01 00
[12669.053868] end_request: I/O error, dev sdb, sector 155907752
[12669.053878] Buffer I/O error on device sdb, logical block 19488469
[12679.073136] sd 4:0:0:0: [sdb] Unhandled sense code
[12679.073144] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12679.073153] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12679.073163] Info fld=0x0
[12679.073167] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12679.073176] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[12679.073197] end_request: I/O error, dev sdb, sector 8
[12679.073206] Buffer I/O error on device sdb, logical block 1
[12689.093450] sd 4:0:0:0: [sdb] Unhandled sense code
[12689.093458] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12689.093467] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12689.093477] Info fld=0x0
[12689.093481] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12689.093491] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[12689.093512] end_request: I/O error, dev sdb, sector 8
[12689.093521] Buffer I/O error on device sdb, logical block 1
[12699.114770] sd 4:0:0:0: [sdb] Unhandled sense code
[12699.114779] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12699.114787] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12699.114798] Info fld=0x0
[12699.114801] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12699.114811] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12699.114832] end_request: I/O error, dev sdb, sector 155907760
[12699.114842] Buffer I/O error on device sdb, logical block 19488470
[12709.138103] sd 4:0:0:0: [sdb] Unhandled sense code
[12709.138112] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12709.138121] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12709.138131] Info fld=0x0
[12709.138135] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12709.138144] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12709.138165] end_request: I/O error, dev sdb, sector 155907760
[12709.138175] Buffer I/O error on device sdb, logical block 19488470
[12719.165426] sd 4:0:0:0: [sdb] Unhandled sense code
[12719.165435] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12719.165443] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12719.165453] Info fld=0x0
[12719.165457] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12719.165467] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12719.165488] end_request: I/O error, dev sdb, sector 155907760
[12719.165497] Buffer I/O error on device sdb, logical block 19488470
[12729.187759] sd 4:0:0:0: [sdb] Unhandled sense code
[12729.187768] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12729.187777] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12729.187787] Info fld=0x0
[12729.187791] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12729.187800] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12729.187821] end_request: I/O error, dev sdb, sector 155907760
[12729.187831] Buffer I/O error on device sdb, logical block 19488470
[12739.211047] sd 4:0:0:0: [sdb] Unhandled sense code
[12739.211054] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12739.211059] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12739.211065] Info fld=0x0
[12739.211067] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12739.211072] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12739.211084] end_request: I/O error, dev sdb, sector 155907760
[12739.211090] Buffer I/O error on device sdb, logical block 19488470
[12749.238392] sd 4:0:0:0: [sdb] Unhandled sense code
[12749.238401] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12749.238410] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12749.238420] Info fld=0x0
[12749.238424] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12749.238433] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[12749.238454] end_request: I/O error, dev sdb, sector 504
[12749.238496] FAT: unable to read boot sector
[12759.258732] sd 4:0:0:0: [sdb] Unhandled sense code
[12759.258741] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12759.258749] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12759.258759] Info fld=0x0
[12759.258763] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12759.258773] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12759.258794] end_request: I/O error, dev sdb, sector 155907760
[12759.258803] Buffer I/O error on device sdb, logical block 19488470
[12776.641287] sd 4:0:0:0: [sdb] Unhandled sense code
[12776.641296] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12776.641305] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12776.641315] Info fld=0x0
[12776.641319] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12776.641329] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e cf 00 00 01 00
[12776.641350] end_request: I/O error, dev sdb, sector 155907704
[12776.641360] Buffer I/O error on device sdb, logical block 19488463
[12786.667616] sd 4:0:0:0: [sdb] Unhandled sense code
[12786.667625] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12786.667633] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12786.667643] Info fld=0x0
[12786.667647] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12786.667657] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d5 00 00 01 00
[12786.667678] end_request: I/O error, dev sdb, sector 155907752
[12786.667688] Buffer I/O error on device sdb, logical block 19488469
[12796.687945] sd 4:0:0:0: [sdb] Unhandled sense code
[12796.687953] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12796.687962] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12796.687972] Info fld=0x0
[12796.687976] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12796.687985] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[12796.688037] end_request: I/O error, dev sdb, sector 8
[12796.688046] Buffer I/O error on device sdb, logical block 1
[12806.711272] sd 4:0:0:0: [sdb] Unhandled sense code
[12806.711281] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12806.711289] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12806.711300] Info fld=0x0
[12806.711303] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12806.711313] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[12806.711334] end_request: I/O error, dev sdb, sector 8
[12806.711343] Buffer I/O error on device sdb, logical block 1
[12816.735582] sd 4:0:0:0: [sdb] Unhandled sense code
[12816.735591] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12816.735600] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12816.735610] Info fld=0x0
[12816.735614] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12816.735624] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12816.735645] end_request: I/O error, dev sdb, sector 155907760
[12816.735655] Buffer I/O error on device sdb, logical block 19488470
[12826.758919] sd 4:0:0:0: [sdb] Unhandled sense code
[12826.758928] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12826.758937] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12826.758948] Info fld=0x0
[12826.758951] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12826.758961] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[12826.758982] end_request: I/O error, dev sdb, sector 504
[12826.759021] FAT: unable to read boot sector
[12836.779229] sd 4:0:0:0: [sdb] Unhandled sense code
[12836.779237] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12836.779246] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[12836.779256] Info fld=0x0
[12836.779260] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[12836.779270] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 01 29 5e d6 00 00 01 00
[12836.779291] end_request: I/O error, dev sdb, sector 155907760
[12836.779301] Buffer I/O error on device sdb, logical block 19488470

```

Also, I checked the /dev/ folder and there is no folder called sdb2/. There is only sdb/ and sdb1/.

Of course, attempting to mount either of these did not work as well. I get a "can't read superblock" error.

Any thoughts? Everything worked fine on Karmic Koala, so I may just go back to that if I can't find a solution.

---

### Post by Bobbyrne01 on 2010-09-16
rhythmbox works grand with my ipod touch :)

---

### Post by Newbie_777 on 2010-10-19
I have Banshee, Rythmbox and Amarok also. They are all great with the music. How about adding videos? What should I do? Or try?

---

### Post by Wobblybob on 2010-10-19
> **Newbie_777 said:**
> I have Banshee, Rythmbox and Amarok also. They are all great with the music. How about adding videos? What should I do? Or try?

Have a look at [[COLOR="Blue"]Floola[/COLOR]]("http://www.floola.com/home/") it does most things on my 6th gen classic video.

---

### Post by heyjean on 2010-10-20
Banshee is wonderful.:)

---

### Post by Newbie_777 on 2010-10-20
I will certainly try Floola. I have also installed gtkiPod Manager and another one (I think it is called hippo or something) but they lack options for video sync. I have read that there is a program call iPod Linux, designed by some German science student. Has anyone checked or tried it out?

---

### Post by Tim_Crandall on 2010-10-29
Hey. Can anyone you tell me how to get my 6g 80gb ipod classic to mount to me computer. I'm running Ubuntu 10.04 on an IBM thinkpad T40. I'm pretty new to Ubuntu. I can get my ipod to recognize that it is plugged into my computer, but the computer is not showing it anywhere and it is not syncing. I would appreciate any help. Thanks a lot

Tim

---

### Post by Jechem on 2010-10-30
It should be in rythmbox if you have the default 10.04 installation. try clicking rythmbox under Applications>Sound & Video>Rythmbox Music Player. It should be recognized and you can sync it with your music files

---

### Post by LeslieL on 2010-11-12
My flaky iPod Classic is doing exactly the same thing as dan06's. I suspect a bad connection inside - iTunes on Windows will copy about 300 files and then claim the iPod doesn't exist. I guess it's a transient fault in the connection hardware. I was hoping to at least use it as a super-sized USB key on Ubuntu, but now it's not even visible. My dmesg results are like dan06's.

---

### Post by d3v1150m471c on 2010-11-25
> **Ninnghizidha said:**
> How can i format the hdd of my ipod with fat32? :confused:

why on earth would you do that?

---

### Post by whalogreg on 2010-11-26
> **Bobbyrne01 said:**
> rhythmbox works grand with my ipod touch :)

I just got an ipod touch and have managed to get the files onto it (drag and drop in rhythmbox), but they don't show up in the music player's library. If I open the ipod in nautilus I can find the files, so I know they're on the player. What am I missing in getting them to show up in the library on the player so I can actually play them?

---

### Post by inobe on 2010-11-30
clementine will sync and is very well capable of adding and removing tunes.


[http://code.google.com/p/clementine-player/](http://code.google.com/p/clementine-player/)

[http://www.clementine-player.org/](http://www.clementine-player.org/)

a few mentioned video, searching for the same solution.

---

### Post by ubunter1 on 2010-12-09
hi, i seem to be having problems getting music on and off my ipod nano, it just says i cannot delete the file or folders. when trying to put music on it gives this-
 Error opening '/media/STREET ROB/iPod_Control/Music/F24/libgpod655975.mp3' for writing (Read-only file system).
 im using ubuntu 10.04 lucid
ive tried all the other programs, i imagine its the same problem, something in my ipod or permissions to read and write.

is there a way to change this so i can add and remove music?.thanks. rob.

---

### Post by r-senior on 2010-12-09
I discovered this week that gtkpod in 10.10 now supports my 4GB Shuffle, which it didn't in 10.04. If you have the diddy Nano touch it looks like it doesn't yet work (neither does my iPhone 4). Check versions and see if an upgrade to 10.10 is likely to help:

[http://www.gtkpod.org/wiki/Libgpod](http://www.gtkpod.org/wiki/Libgpod)

---

### Post by ubunter1 on 2010-12-09
thanks for that, im still having problems adding or removing music even using the gtkpod latest version, it appears as an error about reading and writing files, and i cannot figure out how to change this. 
thanks.
rob.

---

### Post by ajack38 on 2011-02-13
Hi, I have a 160GB Classic Ipod with firmware version 1.62 which accidently got upgraded when it was last connected to a windows machine with itunes on it, and ever since then it won't connect to ubuntu correctly. I tried to put music in via Gtkpod, clementine and 99% of the other Applications suggested here and none worked. Is there a patch that I can get that will fix this? :confused:

---

### Post by tom957 on 2011-02-14
Did you try Rhythmbox? I accidentally did a firmware update to my 80GB classic a while back. Rhythmbox is the only player that will work properly with my pod.

---

### Post by ajack38 on 2011-02-14
I've tried that, None of it works. Is there a way to downgrade an IPODs Firmware so that linux recognises it?

---

### Post by MyKonstantine on 2011-02-15
Is the verdict out yet on if Ubuntu 10.10 works with the iPhone4?

---

### Post by dentaku65 on 2011-02-16
> **ubunter1 said:**
> thanks for that, im still having problems adding or removing music even using the gtkpod latest version, it appears as an error about reading and writing files, and i cannot figure out how to change this. 
thanks.
rob.

Should be a permission configuration; can you make a screenshot of your advanced user settings? Under user manager....

---

### Post by slickytail on 2011-05-17
when i connect my ipod, it says this: ```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Aaron_Carter on 2011-05-18
Hello,
This is what I have looked so far. I have been in my licensed computer shops and they still cannot manage with this question. I have an Ipad 2 (the tablet) and I cannot link it with my Lap Top which owns Linux software. Any ideas?

Aaron,

---

### Post by Rodney9 on 2011-05-18
My 4th generation ipod shuffle works perfectly, I am using Xubuntu 11.04 and GTKPod v1.0.0 using libgpod 0.7.93.
I did have to initialise it in itunes on windows first unfortunately.

---

### Post by vanadium on 2011-05-19
For your information, Ipod Touch OS 4.3.1 (current version is 4.3.3) does not work for putting audio on the device. Banshee or gtkpod recognise the device, you can drag files, gtkpod ends with a warning "Unsupported checksum type".
The ipod music app reports that there is no material and that you can use itunes to add music.

The device mounts twice. The first mount "Ipod of user" shows system directories and folders like Books, Photos, Downloads, ... and you can place files on it.
The other mount "Documents on ipod of..." cannot be used.

---

### Post by nucleicacid on 2011-06-05
gtkpod

---

### Post by life in color on 2011-06-07
Ok I manually synced all of my songs by opening up the ipod and finding the media, then dragging it to Rhythmbox, my problem is that after connecting my ipod to my Ubuntu computer my album art is scrambled. I downloaded a cover art finder but I can't move the folder from downloads to /usr/lib/rhythmbox/plugins I get a "Permission Denied" error.

---

### Post by sgk on 2013-04-28
> **KingOfNowhere said:**
> Using an iPod with (Ubuntu) Linux
-----------------------------------------

			By KingOfNowhere

This is a How-To for using the Apple iPod with Ubuntu Linux. For reference, my machine is an x86 running Ubuntu 5.10 (Breezy Badger). This How-To assumes that you are using USB to connect the iPod to your system and that the iPod is Windows Format (FAT32). Linux support for the iPod is still in its early stages and not all of the features of the iPod are usable. However, it is possible to use any iPod with Linux, but not all iPod models are created equally.

*UPDATE 2/22/06*
I have made some revisions to state the recent support changes. 
*UPDATE 4/19/06*
Formatting Revisions

------------------------------------
1. LINUX IPOD CAPABILITIES
------------------------------------

Here are all the different iPod Models and thier features, along with the tool needed to use the feature.

1st - 4th Gen iPods, Mini iPods, iPod Shuffle (All iPods without color screens)
-----------------------------------------------------------------
These models have Linux Support. 
FEATURE --> TOOL NEEDED

*Audio File Syncing (MP3,AAC,Audiobook)          
[INDENT]--> gtkpod[/INDENT] 
*Podcast Subscribing/Syncing
[INDENT]--> iPodder / Amarok or a simalar program (to subscribe to the Podcast) and gtkpod (to sync to iPod)[/INDENT]
*Calendar Syncing                                       
[INDENT]--> any calendar program that can "Save As" iCal files (ex. Kontact, Ximian Evolution)[/INDENT]
*Contact Syncing
[INDENT]--> any contact program that can "Save As" vCard files (ex. Kontact, Ximian Evolution)[/INDENT]
-------------------------------------------------------

iPod Photo, iPod Nano
-----------------------------------------------------------------
These models also have Linux support.  
FEATURE --> TOOL NEEDED

*Audio File Syncing (MP3,AAC,Audiobook)
[INDENT]--> gtkpod[/INDENT] 
*Album Artwork Syncing
[INDENT]--> gtkpod (cvs version)[/INDENT] 
*Photo Syncing
[INDENT]--> GPixPod or similar program[/INDENT]
*Podcast Subscribing/Syncing
[INDENT]--> iPodder / Amarok or a simalar program (to subscribe to the Podcast) and gtkpod (to sync to iPod)[/INDENT]
*Calendar Syncing
[INDENT]--> any calendar program that can "Save As" iCal files (ex. Kontact, Ximian Evolution)[/INDENT]
*Contact Syncing
[INDENT]--> any contact program that can "Save As" vCard files (ex. Kontact, Ximian Evolution)[/INDENT]
------------------------------------------------------

-------------------------------------------------------

5th Gen iPod (iPod Video) 
-----------------------------------------------------------------
The newest model of iPod is finally usable with linux. 
FEATURE --> TOOL NEEDED

*Audio File Syncing (MP3,AAC,Audiobook)
[INDENT]--> gtkpod[/INDENT] 
*Album Artwork Syncing
[INDENT]--> gtkpod (cvs version)[/INDENT] 
*Photo Syncing
[INDENT]--> GPixPod or similar program[/INDENT]
*Podcast Subscribing/Syncing
[INDENT]--> iPodder / Amarok or a simalar program (to subscribe to the Podcast) and gtkpod (to sync to iPod)[/INDENT]
*Calendar Syncing
[INDENT]--> any calendar program that can "Save As" iCal files (ex. Kontact, Ximian Evolution)[/INDENT]
*Contact Syncing
[INDENT]--> any contact program that can "Save As" vCard files (ex. Kontact, Ximian Evolution)[/INDENT]
*Video Syncing
[INDENT]--> gtkpod (cvs version)[/INDENT]
-------------------------------------------------------

Okay, so this is what can be done with and iPod and a Linux box. If the desired feature you are looking for has no tool, check the bottom of this how-to in the "Additional Features" section.

-----------------------------
2. IPOD CONNECTIVITY
-----------------------------

Well, now that we know what can be done using Linux, the first step is gaining proper connectivity between the iPod and the Linux box.

- First - 
Connect the iPod to the computer. If automount is running, your iPod may appear on the desktop, mounted, auto-magically. If this is the case, go ahead and skip to Section 3.
*Kubuntu NOTE: Kubuntu users (or KDE users) will need to install the kioslave for the ipod, then reconnect your ipod. This can be done with this command:
```

sudo apt-get install ipodslave

```

If you plug your iPod in and nothing happens, follow this section of the guide. As long as your iPod screen says do not disconnect or the Status Light is blinking (Shuffle) then the iPod has connectivity with the computer.

- Second -
type the following command:

```
dmesg
```

Toward the end of this command's output should be the device name of your iPod, it should look something like this:

```

[4301791.359000] usb 3-2: new high speed USB device using ehci_hcd and address 3
[4301791.461000] usb 3-2: configuration #1 chosen from 2 choices
[4301793.195000] SCSI subsystem initialized
[4301793.201000] Initializing USB Mass Storage driver...
[4301793.204000] scsi0 : SCSI emulation for USB Mass Storage devices
[4301793.206000] usb-storage: device found at 3
[4301793.206000] usb-storage: waiting for device to settle before scanning
[4301793.206000] usbcore: registered new driver usb-storage
[4301793.206000] USB Mass Storage support registered.
[4301798.206000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4301798.206000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4301798.216000] usb-storage: device scan complete
[4301798.385000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[4301798.386000] sda: Write Protect is off
[4301798.386000] sda: Mode Sense: 6c 00 00 08
[4301798.386000] sda: assuming drive cache: write through
[4301798.390000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[4301798.391000] sda: Write Protect is off
[4301798.391000] sda: Mode Sense: 6c 00 00 08
[4301798.391000] sda: assuming drive cache: write through
[4301798.391000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2
[4301798.408000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0

```

For this instance, the iPod is detected as /dev/sda. The /dev/sda device has 2 partitions which are:

/dev/sda1 -> iPod firmware partition (Not Important for this How-To)
/dev/sda2 -> iPod storage partition (for storing music, photos, videos, etc.)  
  
The part of the iPod that needs to be accessed is the partition /dev/sda2

- Third -
Create a folder to mount the iPod to:

```

sudo mkdir /mnt/ipod

```

Then you must edit your /etc/fstab to include your iPod:

```

sudo gedit /etc/fstab

```

Then add the following line to /etc/fstab, change /dev/sda2 to your iPod 
device if necessary

```

/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0

```

Finally, mount your iPod:

```

sudo mount /dev/sda2

```

---------------------------------------------
3. INSTALLING AND USING GTKPOD
---------------------------------------------	  

Now that your iPod is connected to your machine and correctly mounted, we need to install the nessessary tools for using it.

GTKPOD - a utility used to update an iPod - [http://www.gtkpod.org](http://www.gtkpod.org) (PROJECT HOMEPAGE)

gtkpod is the major utility for iPod usage in Linux, so we will need to install it:

```

sudo apt-get install gtkpod

```

Once the install is complete, launch gtkpod like this:

```

gtkpod

```

Using gtkpod, you can create a playlist of all the audio files you want on you iPod. There are 2 default playlists in gtkpod, Local and gtkpod. The Local playlist is to consist of your entire music library. The gtkpod playlist is to consists of the current/desired contents of the iPod. Here are a few easy steps to get started with gtkpod:

1.- Plug in iPod and mount it
2 - Open gtkpod and select "Read iTunesDB", this allows gtkpod to fetch the current contents of the iPod
3 - Add your music library to the local playlist be selecting the Local playlist and using "Add Directory"
4 - Modify the gtkpod list with the desired contents of your iPod
5 - Finally, click "Sync" or "Sync iTunesDB" to update the iPod

At this point, we are now able to connect and sync an iPod on a Linux system.

---------------------------------
4. ADDITIONAL FEATURES
---------------------------------
Here is the state of the other features of the iPod. Not all of them work yet, but progress is being made.

- Podcast Subscribing/Syncing -

This feature is possible under Linux, however there is not one app that does it all. In order to subscribe to a podcast, you need a Podcast catcher tool, like iPodder. The iPodder software just keeps track of all your podcast subscriptions and downloads new episodes. [http://ipodder.sourceforge.net](http://ipodder.sourceforge.net) (PROJECT HOMEPAGE). Once you have downloaded your podcasts, all that is left to do is to sync them with gtkpod.
*UPDATE* 
Amarok now supports Podcasts and Podcast syncing. If this is important to you, Amarok is worth checking out.

- Calendar and Contact Syncing - 

This feature can be done in Linux, as long as the programs used to handle calendars and contacts can "Save As" iCal files and vCard files. These are the only extensions the iPod will recognize. Once you have saved your calendars and contacts as the appropriate file, just copy them to the appropriate folder on the iPod:

EXAMPLE
```

mv /path/to/calendars/*.ical /mnt/ipod/Calendars/
mv /path/to/contacts/*.vcard /mnt/ipod/Contacts/

```

And that is all it takes to sync calendars and contacts on Linux.

- Album Art/Photo Syncing -

[GPixPod]("http://sourceforge.net/projects/gpixpod") is a program designed specifically for managing photos on your iPod. Using it allows you to encode, sync, and manage your ipod photo library.

- Video Syncing -

All Video features (encoding and syncing) has been covered in another, very nice how-to:

[HowTo: Encode Video for iPod Video ]("http://ubuntuforums.org/showthread.php?t=114946")

-------------------------
5. WORK-AROUNDS
-------------------------
If you are not happy with just these options, then here are the workarounds I have tried and what worked.

wine + iTunes
--------------
This doesn't work at all, don't bother.

virtual machine + Windows + iTunes
----------------------------------
This was also unsuccessful, a virtual Windows installation will not correctly identify an iPod on a USB Bus.
*UPDATE*
However I was unsuccessful with this, vibes has report that it is possible when reformatting the ipod in VMWARE. any further info on this would be welcomed.

Dual-Boot + Windows + iTunes
----------------------------
This does work but Windows needs to be installed on your machine. This does kinda defeat the purpose of this How-To but here is what I found out. I resently purcahsed an iPod Video and was upset that there was no way to sync videos with Linux. So, I used gtkpod to put all music on my iPod, rebooted, and sync'ed my videos with iTunes. This works but it is kind of a pain.

*NOTE ABOUT ITUNES* - If you use gtkpod to update your iPod, gtkpod does not use the exact same method of writing the iTunesDB file that iTunes does. So, if you use your iPod with both windows and linux, you may make your iTunesDB unreadable by gtkpod.
---------
6. END
---------

Well, that should be all you need to know to get your iPod working with Linux. I hope everyone finds this helpful.

- KingOfNowhere

In the late Ubuntus (>12.04) 
1) GtkPod works fine with all iPods. You don't need to do anything. Just install GtkPod and plug in the iPod. Everything works fine (as long as the iPod is formatted as a FAT device, not Mac)

2) You can always install Windows XP on top of VirtualBox and install iTunes in Windows. The Virtual machine will identify the iPod just fine. I use both solutions because I convert mp3 audiobooks to iPod (chaptered AAC) audiobooks and if I load the audiobook onto iPod with GtkPod then the iPod does not see the chapters in the audiobook. The problem is solved if I open the audiobook (on the iPod) with iTunes at least one time. Then the audiobook appers to have chapters!!! Odd solution, but works.

---

### Post by suicideking on 2013-08-01
bump. 

Is GTKPod still the best app to manage an ipod?

---

### Post by sofasurfer on 2013-12-17
sgk - that looks like a good work around. I'll try it.

I also have to save this link here so I remember to try this thread also... [http://ubuntuforums.org/showthread.php?t=1717226&highlight=format+ipod+shuffle](http://ubuntuforums.org/showthread.php?t=1717226&highlight=format+ipod+shuffle)

---

