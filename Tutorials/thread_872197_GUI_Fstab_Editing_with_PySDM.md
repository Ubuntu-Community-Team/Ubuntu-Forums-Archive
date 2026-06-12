---
title: "GUI Fstab Editing with PySDM"
date: 2008-07-27
forum: Tutorials
---

### Post by drs305 on 2008-07-27
[CENTER]**[COLOR=MAROON][SIZE=3]Storage Device Manager - Fstab Configuration[/SIZE][/COLOR]**[/CENTER]
***
NOTE: pySDM has been around a while and is getting dated. An alternative which does much the same thing is Mount Manager (although even it is getting older, as it uses HAL, which is no longer required by Ubuntu). You can install it with "sudo apt-get install mountmanager". Start it via System > Administration > MountManager. If you use it, make sure you make a backup copy of your current */etc/fstab* file before making changes with Mount Manager.
***

Storage Device Manager provides an GUI method to make changes to mounting options without manually editing any files. It is a bit old and fails to take advantage in improvements to the linux filesystem, such as using UUIDs and labels to identify partitions. Even when using this app, the user will need to make some changes to /etc/fstab to incorporate these improvements. It can serve as the *basis* for creating a new line in your /etc/fstab file but it isn't the complete solution it used to be. *ntfs-config* is an excellent and much simpler tool for creating a new fstab listing for NTFS partitions, which is the formatting used by Windows. It is discussed later. Users are encouraged to use the "5 Minute Guide" and reference the remainder for background information or if clarification is desired.

Note that pySDM does not make a back up copy of the */etcfstab* file! 
Before proceeding, please note that there are some excellent references for further information regarding fstab located at the bottom of this guide. 

Users may also wish to consider the KDE application *mountmanager*, which is similar to PySDM but has greater capabilities and has been updated more recently. Here is one link to a site discussing [mountmanager]("http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html").


Sections:
[CENTER][COLOR=MAROON][B]5 Minute Guide ---  Installing & Starting ---  Fstab Backup  ---  Using PySDM
When You Will Need Fstab ---  Notes --- Partition Commands ---  Links[/B][/COLOR][/CENTER]
> 
[CENTER]**[COLOR=Navy][SIZE=3]The 5 Minute Guide - I Don't Have Time for All The Rest of This Stuff ![/SIZE][/COLOR]**[/CENTER]

[COLOR=MAROON]**Stop the Presses!**[/COLOR] If you only need to configure an NTFS drive, have you considered ntfs-config? "sudo apt-get install ntfs-config", then start it via System Tools, NTFS Configuration Tool. This app will set up NTFS partitions to allow read/write access, if that is all you are looking for. Now back to our regular programming...

If you run into problems, read the rest of this guide. Let's get started:

[COLOR=MAROON]**A. Permanent Drives**[/COLOR]
1. Install Storage Device Manager (pysdm) via *Synaptic* or : **sudo apt-get install pysdm**
2. Make a backup of fstab (you may be in a rush, but you aren't reckless!): **sudo cp /etc/fstab /etc/fstab.bak**
3. Start PySDM: *System > Administration > Storage Device Manager* or **gksu pysdm &**
4. The devices are listed in the left panel (sda, sdb, etc). If you click on the white triangle to the left of one of the devices (sda, sdb, etc) it will expand to show each partition on the device (sda1, sda2, etc). 
[LIST]
[*]Expand the device by clicking the white triangle to the left and select the partition you wish to set up.  If there is no previous SDM setup for this partition, a 'Configure Now' window appears. Select 'OK' to continue. Hit 'Refresh' if you don't see the device. If it's an external drive there is a good chance it will be listed last. If you aren't sure, see Section 5 for some hints for locating the correct partition.
[/LIST]
5. Type the name of a mountpoint in the 'Name' window. The mountpoint you name will create and/or select your mountpoint in /media 
[LIST]
[*]Example: If you enter *my-data* in the window, it will be mounted on */media/my-data* 
If you want a mountpoint other than /media, click on the 'folder' icon and select another folder.
[/LIST]
6. Into the Options window, copy/paste the bold portion of the applicable line (there should be no spaces). The copy/paste information replaces the default entry of *Defaults*
[LIST]
[*][COLOR="MAROON"]**ext2/3**[/COLOR] data partitions:
```

*root* partition ( / ):    **relatime,errors=remount-ro**
*home* partition (/home):  **nodev,nosuid,relatime**
*other* partitions:        **defaults,users**
```
After mounting, if necessary you can run *chown* and *chmod* on mounted ext3 mountpoints.
[LIST]
[*]sudo chown -R *username:groupname* /media/*yourmountpoint*
[LIST]Example: sudo chown -R *drs305:mygroup* /media/my-data[/LIST]
[*]chmod -R 755 /media/*yourmountpoint*  (Run previous command first or preceed command with 'sudo')
[LIST]chmod -R 755 /media/*my-data*[/LIST]
[/LIST]
[/LIST]

[LIST]
[*]**[COLOR="MAROON"]ntfs/vat[/COLOR]** partitions : ```
**[B]auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137**[/B]
```
[LIST]
[*]uid 1000 is owner - 1000 is the first user (created at install). Adjust to another uid if desired.
[*]group is uid 1000's group (rw for directories, r for files), others have no access. Group id can be set to any existing group. Common groups include 0 root, 46 plugdev (removable drives), 100 (often set to 'users'), and 100X (1000 is normally first user's group, 1001 second, etc).
[*]Ownership of ntfs and fat32 partitions is set at mounting - *chown* and *chmod* will not 'stick'.
[*]NTFS Note: An ntfs partition fstab entry should work with a simple 'ntfs-3g defaults' entry. The mountpoint will be owned by root, as will subfolders and files. However, the user can write and save these files. If the uid/gid etc are added to fstab, the mountpoint will still be owned by root but the subfolders and files will show they are owned by the user (uid=).
[/LIST]
[/LIST]
7. **Click on "*Assistant*"  and _uncheck_ "Mount file system in read-only mode".**
8. Hit '*Apply*'. Fstab has just been updated.
9. Hit the Unmount, then Mount Button. The device/partition should now reflect your selections.
10. Done.

**Note: Fsck will not be run on this partition. Consider editing fstab to add this option for ext2/3 partitions. See Section 4.**

[COLOR=MAROON]**B. Removable Drives**.[/COLOR] (*Skip this paragraph if you are trying to keep under 5 minutes! ;-) ) *These drives should work without an entry in fstab. They are not mounted automatically but are mounted by going to *Places > Removable Media* and selecting the removable device you wish to mount. There is a reason these devices are not normally listed in fstab - their designations are dynamic. As an example, the same removable device could be *sdc* one time and and *sdg* another. Fstab would not recognize the changed designation.

If you want to include a removable or external drive in fstab: 
Since their designations (dev/sdXX) are not fixed entering them in fstab takes a little more work. Your fstab entry should identify the device with either a UUID or a label. This ensures that the fstab setting will still be valid whether the device is mapped as *sdc, sdh*, etc. Create the fstab entry via SDM [noparse](steps 1-8)[/noparse], then manually edit fstab to 'lock in' the device label by replacing the *sdXX* with either a label or UUID.
[LIST]
[*]**[COLOR="MAROON"]By UUID[/COLOR]**:
Find the UUID: **sudo blkid | grep 'UUID'**
[/LIST]

[LIST]
[*]**[COLOR="MAROON"]By Label[/COLOR]**:
Check for a label: **sudo blkid | grep 'LABEL'**
If no label exists there are several options for labeling a partition. It can be done from within Gparted (Partition, Label) or via Ubuntu's "Disk Utility" (System, Administration, Disk Utility: Edit Filesystem Label in lower right). 

You can also use the command line for labeling linux partitions using "tune2fs" or, for other formats, install labeling apps: **sudo apt-get install ntfsprogs e2fsprogs**
If making a new label, save yourself some trouble by NOT using a label name with spaces! (my-data or my_data, not 'my data')
[LIST]
[*]ntfs: **sudo ntfslabel /dev/<device> LABELNAME**  Example:  sudo ntfslabel /dev/sdg1 my-data
**[COLOR="MAROON"]ext2/3[/COLOR]**: **sudo tune2fs -L <label> <dev>**  # Example: sudo tune2fs -L /dev/sdg1 my-data
**[COLOR="MAROON"]fat32[/COLOR]**: Labeling a fat32 device with data on it will put us over 5 minutes -sorry. Go to [Label fat partitions]("http://ubuntuforums.org/showthread.php?&t=283131")
[/LIST]
 
[/LIST]
Run Steps 1-9 above. When you have completed Step 9 the fstab file will be updated to include the partition. However, it will be defined as /dev/sdXX. You now must change this designation to a label or uuid listing:
[LIST]
[*]Open fstab: **gksu gedit /etc/fstab**
Change '/dev/sdXX' to 'LABEL=LABELNAME' or 'UUID=123-abc'
Example of change: 
*/dev/sdg1  /media/my-data ...* to  *UUID=123-abc /media/my-data ...* 
or 
*LABEL=LABELNAME  /media/my-data ...*
[/LIST]
**[COLOR=Navy][SIZE=3]1. Installing & Starting Storage Device Manager (PySDM)[/SIZE][/COLOR]**
Storage Device Manager is accessed via [COLOR=MAROON]System > Administration > Storage Device Manager[/COLOR]. From the command line, start it with "*gksu pysdm*". Root privilege is required since PySDM makes changes to system files. *gksu* is the cousin of *sudo* and should be used with graphical apps. 

If Storage Device Manager is not in your menu, install it via synaptic ( [COLOR=MAROON] System > Administration > Synaptic Package Manager[/COLOR] ). If you don't see 'pysdm' listed in synaptic or the following command line method is not successful, go to *Synaptic > Settings > Repositories > Ubuntu Software* and make sure the '*universe*' repository is checked. Hit the 'Reload' button to refresh the package list and then select *pysdm*. You can also install it via command line with:
```
sudo apt-get install pysdm 
```**[COLOR=Navy][SIZE=3]2. Backup Fstab[/SIZE][/COLOR] **
[COLOR=MAROON]**Before modifying any system file, it is good practice to make a backup copy.**[/COLOR] If you intend to make multiple changes 
within a short time, I'd recommend assigning each backup a unique number (fstab.bak1, bak2, etc). To make a backup:
```
sudo cp /etc/fstab /etc/fstab.bak1 
```**[COLOR=Navy][SIZE=3]3. Using PySDM[/SIZE][/COLOR] **
The PySDM interface consists of 3 sections: the *Partition* window for selecting the partition, the *General Configuration* window for setting fstab options, and the *Dynamic configuration rules* window for modifying hot-plug device and removable settings. 

**[COLOR=MAROON][SIZE=3]*Partition List*[/SIZE][/COLOR] **
When Storage Device Manager starts, it reads the devices/partitions available to it and displays them in the far left window. Starting with Hardy, Ubuntu no longer refers to devices as *hda* even for IDE drives. 

**Select the partition which you want to mount by expanding the drive (sda, sdb, etc) and clicking on the triangle to the left of the individual partition (sda, sdb, etc).** *Until you select a partition the right side of PySDM will be grayed out and unavailable for input*. If you don't know which partition you want to select, go to the *Which Partition?* section at the bottom of this page for help. The first time PySDM works with a partition, even if an entry already exists in fstab, it will ask '*Configure Now?* - click OK. 

**[COLOR=MAROON][SIZE=3]*General Configuration*[/SIZE][/COLOR] **
[LIST]
[*][COLOR=NAVY]***Name***[/COLOR] 
*Name* is the mountpoint you wish to use, by default a subfolder of /media and named the same as the partition (e.g. 'sda3'). You can choose a more descriptive name, such as 'my-data' or whatever you wish. The folder will be created if it does not exist. **[COLOR=MAROON]The folder created and/or selected should be empty - do not select a folder already containing files or subfolders.[/COLOR]**
[*][COLOR=NAVY]***Mountpoint***[/COLOR] 
If you do not want to use /media as the base mountpoint you can choose a different folder by clicking on the *folder icon* and navigating to another folder. If you wish to make a new folder while navigating your system, click the '*new folder*' at the top right of the navigation window. If you get 'lost' while navigating the folders, '*File System*' in the left window will get you back to **/** .
[*][COLOR=NAVY]***Type***[/COLOR] 
Take a breath and relax - you don't have to make a decision here. *Type* is just informing you the type of partition you are working with (e.g. ext3, ntfs, vfat).
[*][COLOR=NAVY]***Options***[/COLOR] 
Here's the meat of the program. Initially '*Options*' is set to '*defaults'*. Clicking the '**Set Defaults**' button also resets this window to '*defaults'*. Selecting '*defaults'* sets the following options: *rw, suid, dev, exec, auto, nouser, async*. Starting with Hardy, '*relatime*' is also a default on native linux (i.e. ext2/3) partitions. For information on each of these settings, refer to the links at the bottom of this guide. If you add or change any options, '*defaults*' will not be shown but will apply to any setting not overridden. One other note, in addition to automatic entries, anything you type in this window will be input in the options section of fstab. For instance, there is no option to set *dmask* or *fmask* but you can add them to the options line and they will be applied along with the other settings. All options are joined by commas with no spaces in the entire section.
[*][COLOR=NAVY]***Assistant***[/COLOR]
This section could also be called '*More Options*' since it is the section in which you can change settings from '*defaults*'. Most of the settings are self-explanatory. The setting options presented vary with the type of partition selected (ext3, ntfs, fat32, etc). I will comment on a few of the options you may wish to consider changing. Any change you make in these sections will remove the '*defaults*' option from the main window and non-default options will be displayed. Default settings will still apply to those settings which are not overridden. 

[COLOR=Blue]Auto-selected items are colored blue.[/COLOR] **Black Bold** items are the actual  designations that appear in the fstab options section when selected. _Default options_ are underlined. They will NOT appear in fstab but apply unless the associated non-default option is entered. 
[SIZE=3][COLOR=RED]* [/COLOR][/SIZE] Items which should be considered. Author recommendations are listed in [COLOR=GREEN]**green**[/COLOR].
[LIST]
[*]Mounting Tab
[LIST]
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Mount read-only* *. **_ro_** The Read-Only option is OFF (rw) for linux ext2/3 partitions and ON* (ro) by default for VFAT/NTFS partitions. _For VFAT/NTFS partitions, this option must be *unchecked* to enable read/write._ For non-linux partitions, the PySDM umask (and dmask/fmask manual entries) setting can allow RW access for non-linux partitions even if RO is enabled.
[*]*Allow group mount*. **group=**  Allow any group member to mount. Enter group id.
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Allow any user to mount*. **[COLOR=GREEN]users[/COLOR]** Normally the option would allow a user to click on a partition icon or use the 'mount /dev/sdXX' option to mount the partition without root privileges. If this option doesn't work for NTFS partitions try mounting via terminal. [COLOR=MAROON]If you get an 'Unprivileged user' message, see the section at the bottom of the page on NTFS-3g errors.[/COLOR]
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Allow a user mount*. **_nouser_/user**
[*]*[COLOR=Blue]File system mounted at boot time[/COLOR]*. **_auto_/noauto**
[*]*Owner of device can mount*. **owner**
[*]*Owner user of filesystem *. **uid=** Enter uid in window. Whoever mounts the device owns it. Your uid is normally 1000 if you are the primary user. To check, run the following command in terminal: *id*. You may wish to select this option.
[*]*Support extended attributes*. **--/user_xattr** (Linux partitions only).
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Check file system on mount time*. (Linux partitions only). [COLOR=Red]**This command is no longer supported and may produce an error message. Do not select it.**[/COLOR] Fsck checks are no longer included in the *options* section; they are now handled by the last digit on the line (normally 0, 1 or 2).
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*[COLOR=Blue]Umask[/COLOR]*. ***000*** (Non-linux partitions only). This is an entire subject in itself. The PySDM menu does not offer dmask and fmask value inputs for ntfs/fat partitions. You can manually enter them them in the *Options* window if you wish. 
On NTFS partitions, if the fstab options are left at "defaults" the mountpoint and all folders/files will be owned by root but readable/writable by the user. If uid/gid options are used, the mountpoint is still owned by root but all subfolders and files are owned by the user specified by "uid=".
Refer to the *Permissions* link at the bottom of the page for more information. Here are some common umask settings you may wish to consider:
000 (Permissions 777) - Default PySDM setting. Anyone can do anything! 
022 (Permissions 755) - Owner read/write/execute (rwx), group (rx), others (rx). 
**[COLOR=GREEN]027[/COLOR]** (Permissions 750) - Owner rwx, group rx, others can't access partition.
077 (Permissions 700) - Only the owner can rwx, group and others cannot access partition.  
** **[I]Instead* of umask, dmask & fmask can be used but must be entered manually on the *Options* line.** Two useful settings would be:[/I]
dmask 027,fmask137 - Owner has rwx for directories, rw for files. Group has rx for dirs and r for files.
dmask 000,fmask111 - Owner rwx dirs, rw files. Group rwx dirs, rw files. Others rwx dirs, rw files.
*Deselect* umask if dmask/fmask settings are entered in the *Options* window.
[*]*Owner group of filesystem*. **gid=**
[/LIST]
 
[*]Special Files
[LIST]
[*]*[COLOR=Blue]Permit execution of binaries[/COLOR]*. **_exec_/noexec** If unchecked, this option prevents execution of program files within the partition. This may be desirable for a storage or data partition which nevertheless contains executable files. Unchecking this box will also disable the warning message in nautilus and other applications which asks if you want to run the file or open it. If not checked, the file will open without the query.
[*]*[COLOR=Blue]Permit executables to change user/group identity[/COLOR]*. **_suid_/nosuid** Relates to scripts. Note: If you need to know about this, you probably don't need PySDM!
[*]*[COLOR=Blue]Interpret character or special block devices[/COLOR]*. **_dev_/nodev** See note in previous entry!
[/LIST]
 
[*]Journaling (Linux partitions only)
[LIST]
[*]*Specify a journaling mode*. **/data=**  Ordered, journal or writeback.
[*]*Update journal or specify the inode where it is*. **journal=**
[*]*Do not load journal on mounting*. **_noload_**
[/LIST]
 
[*]Performance
This section deals with recording data access times and synchronization matters. User input is not normally required. Many items apply to linux partitions only.
[LIST]
[*]*[COLOR=Blue]Update directory time for each access[/COLOR]*. **_diratime_/nodiratime**
[*]*I/O to file system should be done synchronously*. **_async_/sync**
[*]*All directory updates should be done synchronously *. **_nodirsync_/dirsync**
[*]*[COLOR=Blue]Update file time for each access[/COLOR]*. **_atime_/noatime**
[*]*[COLOR=Blue]Specify what to do in case of errors=[/COLOR]*. **_remount-ro_/continue/panic** Really, panic is an option..
[*]*Do not attach buffer_heads to file pagecache*.
[*]*Get group id from the directory for a new file*.
[*]*Synchronize data and metadata every specified seconds*. **commit=**
[*]*Use a especific block as superblock*. **sb=**
[*]*Use old new inode allocator*.
[/LIST]
 
[*]Miscellaneous
This section deals with network file systems, default character encoding, UFT-8 file name conversion, upper/lower case interpretation, and escape sequences. The default character set is the older iso8859-1. If your system is having trouble reading the directory or file names, changing these settings may help.
[LIST]
[*]*File system requires network*. **_netdev** 
Linux partitions (ext2/ext3) only:
[*]*User allowed to use reserved space*. **resuid=**
[*]*Group allowed to use reserved space*. **resgid=**
[*]*Support POSIX access list*.
[*]*Disables 32 bit user and group id*.
[*]*Print debugging info*.
[*]*Minix behavior for stat information*. 
Non-Linux only:
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*[COLOR=Blue]Character set to use for file names[/COLOR]*. **nls=iso8859-1**  The english-speaking standard of iso8859-1 is the default and checked, The *mount* man page uses the  iocharset=8859-1 . If this is listed in the Options window, I recommend changing **nls=** to **iocharset=** I personally turn it **[COLOR=GREEN]off by deselecting it.[/COLOR]**.
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Use UTF-8 for converting file names*. **utf8**  **[COLOR=GREEN]Select this[/COLOR]** for ntfs and vfat (fat16/32) partitions.
[*]*Update file time for each access*. **posix**
[*]*Use escape sequences for unknown characters*. **uni_xlate=**
[/LIST]
[/LIST]
 
[*][COLOR=NAVY]***Mount Button***[/COLOR] 
You can mount and unmount the selected partition by clicking on this button. Cycling Unmount > Mount will allow the options you have designated to take effect. It is equivalent to running the 'sudo umount' and 'sudo mount' commands on the particular partition.
[*][COLOR=Red]***Apply Button***[/COLOR] 
Finallly! Clicking this button applies the changes. In fstab, the revised or new entries are placed at the bottom of the file. PySDM at present does not use UUID's or LABEL designations. If you have entries in fstab that use either of these designations, they will either remain unchanged or become comments. The '/dev/sdXX' line generated by PySDM will appear below previous entries in the /etc/fstab file. In this case, even though there are multiple entries for the same partition, the PySDM lines will be loaded last and thus will take precedence over earlier lines.
[/LIST]

**[COLOR=MAROON][SIZE=3]*Dynamic Configuration Rules*[/SIZE][/COLOR] **
This section enables you to set *udev* rules. Click on the '*New*' button and you can set the conditions of Name, Model, Vendor, and bus type.
After setting specifications to identify the device, you can set the user, group, device file name, and specify user's rights. You can also create a link with a name of your choosing. The settings are stored in /etc/udev/user.rules. For more information about udev configuration refer to the man page ( *man udev*) or the link at the bottom of this guide.


**[COLOR=Navy][SIZE=3]4. When You Will Need Fstab (and How to Do It)[/SIZE][/COLOR] **
While PySDM offers an easy and safe way to change or create partition mounting instructions, there are several reasons why you might wish to edit fstab manually. [COLOR=MAROON] **Before modifying any system file, it is good practice to make a backup copy.**[/COLOR] 
```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab 
``` 
[LIST]
[*]Refer to the instructions in the '3 Minute Guide' *Removable Drives* section for how to make the following changes.
[*]UUIDs. PySDM currently does not use UUIDs. If your fstab contains a UUID entry and you attempt to create a new listing for the same partition PySDM will create a "/dev/sdXX" entry at the bottom of the file. PySDM will either place a comment (#) symbol at the start of the original line and/or will override the UUID entry by placing the PySDM-generated entry at the bottom of fstab. A technique if you would like to retain the UUID entry would be to generate an fstab entry with PySDM, copy the options to the UUID line, and then delete the remainder of the PySDM entry. Remember that since PySDM does not use UUIDs, it will not update them if they are changed due to repartitioning.
[*]LABELS. PySDM currently does not use labels. Read the previous entry on UUIDs. The same technique applies for labels.
[*]*/dev* Designations. Some users prefer not to use /dev designations. In the past some updates/upgrades changed the letter designations of partitions. Since Hardy now uses the /dev/sdXX designation, there should be no more unrequested changes from /dev/hdXX to /dev/sdXX or vice versa. If you don't want to use the /dev designations run PySDM and then replace the /dev/sdXX designation with the UUID or label. (see commands below for determining these)
[*]FSCK Entries. The last digit in an fstab entry is provides instructions for *fsck* (disk checking).
The last digit relays the following instructions to *fsck*:
0 - Do not check. (This should always be the setting for non-linux partitions.)
1 - Check first. (Root)
2 - Perform check with a lower priority than 1 (when running during the same session).
PySDM always creates a listing with the FSCK option set at '0'. If you want to change this you will need to edit fstab and change the setting.
[/LIST]

**[COLOR=Navy][SIZE=3]5. Notes & Additional Information[/SIZE][/COLOR] **

**[COLOR=MAROON][SIZE=3]How Do I Know Which Partition to Choose?[/SIZE][/COLOR] **
When adding a new device or after partitioning a drive, you may not be sure which partition you want to select. One method you can try is to watch the list as the device is plugged in. If it may be mounted, run "sudo umount -a". There will be some busy messages but it won't hurt anything. Then plug in the device and see if it mounts by watching the *Partition List* window to see if it appears. Normally PySDM will place this 'new' device at the bottom of the list, even if the letter designation is lower than some already displayed. You can use some of the commands listed later in this section to help you investigate your system's partition information. Some of the following characteristics may help you determine the partition:
[LIST]
[*]Size - Approximate size of the partition: **df -h**
[*]Formatting - Type of formatting: **df -T | grep "/dev/"**
[*]Bootable - Bootable Partitions: **sudo fdisk -l | grep "*"**
[*]View Everything - **sudo fdisk -l && sudo blkid && df -Th && cat /etc/fstab && mount**
[/LIST]

**[COLOR=MAROON][SIZE=3]*'Unprivileged User' NTFS Errors*[/SIZE][/COLOR] **
NTFS-3g was incorporated in Hardy and is enabled by default. Nevertheless, it is possible to get an error message when trying to mount an NTFS partition as a specific user. The error message is:
[LIST]
[*]Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
To correct this condition:
```

sudo chown root $(which ntfs-3g)
sudo chmod 4755 $(which ntfs-3g)

```
[/LIST]
**[COLOR=Navy][SIZE=3]6. Useful Partition Commands (Results in italics)[/SIZE][/COLOR]**

What partitions are currently mounted?
**mount**
*/dev/sda5 on / type ext3 (rw,errors=remount-ro)*

What is contained in my fstab (to exclude commented lines, add [ **| grep -v "#"** ]?
**cat /etc/fstab**
[I]# Entry for /dev/sda5 :
UUID=4d33bfe6  /  ext3  defaults,errors=remount-ro  0  1 [/I]

What is  the UUID / LABEL of my partition?
**sudo blkid -c /dev/null**
*/dev/sda1: UUID="CEECFF9EECFF7F51" TYPE="ntfs"*

What partitions are on my computer (note the switch is a small L)?
**sudo fdisk -l**
*/dev/sda5   *        2804        4078    10241406   83  Linux*

How much space do I have on my partitions?
**df -Th**
*/dev/sda5     ext3    9.7G  3.9G  5.4G  42% /*

How do I make a label for my NTFS partition? (Install *ntfsprogs* first)
sudo ntfslabel <device> <label>
*sudo ntfslabel /dev/sda5 MYLABEL*

How do I make a label for my ext2/3 partition? (Install *e2fsprogs* first)
**sudo tune2fs -L <label> <dev>**
*sudo tune2fs -L MYLABEL /dev/sda5*

How do I make a label for my fat32 partition? 
[COLOR="Red"]Warning: This overwrites any data on the partition.[/COLOR]
**sudo mkfs.vfat -F32 -n <label> <device>**
*sudo mkfs.vfat -F 32 -n MYLABEL /dev/sda5*
sudo mkfs.vfat -F32 -n /dev/sdc 1 usb.5

**[COLOR=Navy][SIZE=3]7. Links[/SIZE][/COLOR] **

**[COLOR=MAROON][SIZE=3]Ubuntu Community Related Links[/SIZE][/COLOR] **
[Introduction to Fstab]("https://help.ubuntu.com/community/Fstab")
[UsingUUID]("https://help.ubuntu.com/community/UsingUUID")
[LinuxFilesystemsExplained]("https://help.ubuntu.com/community/LinuxFilesystemsExplained")
[RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive") (Really - How to Label Any Format)
[MoveMountpointHowto]("https://help.ubuntu.com/community/MoveMountpointHowto")
[MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")


**[COLOR=MAROON][SIZE=3]Other Links[/SIZE][/COLOR] **
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131") [How to edit & understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html") [Understanding & Using File Permissions]("https://help.ubuntu.com/community/FilePermissions")
[PyGTK Storage Device Manager]("http://pysdm.sourceforge.net/")
[Writing udev Rules]("http://reactivated.net/writing_udev_rules.html")
For KDE users or those wishing to install the KDE dependencies, *[mountmanager]("http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html")* is said to be a comparable application with more advanced features than PySDM. It is available in the "universe" repository.


**[COLOR=MAROON][SIZE=3]What's With the Name PySDM?[/SIZE][/COLOR] **
PySDM runs a PyGTK graphical interface = py for the python wrapper and GTK for the Gimp Tool Kit.

---

### Post by Rocket2DMn on 2008-07-27
Moved to Tutorial & Tips.  Looks like a nice guide.

You may consider adding links to some of these wiki guides where appropriate, since they are relevant and on topic:
[uhelp]community/Fstab[/uhelp]
[uhelp]community/UsingUUID[/uhelp]
[uhelp]community/LinuxFilesystemsExplained[/uhelp]
[uhelp]community/RenameUSBDrive[/uhelp]
[uhelp]community/MoveMountpointHowto[/uhelp]
[uhelp]community/MountingWindowsPartitions[/uhelp]
-> [uhelp]community/MountingWindowsPartitions/ThirdPartyNTFS3G[/uhelp]

---

### Post by drs305 on 2008-07-27
Thanks for the input.

---

### Post by caljohnsmith on 2008-07-29
I really like the idea of a GUI for modifying fstab, but I have few questions about pysdm:

[LIST=1]
[*]I'm just wondering why doesn't pysdm make a backup of fstab itself? Why does the user need to do that manually? Or couldn't that be added as an option somewhere that the user could choose?
[*]As you mention in your "How Do I Know Which Partition to Choose?" section, pysdm doesn't presently offer any way of helping the user determine which partition to choose; the user is left with going to the CLI again, which seems to undermine the idea of using a GUI to begin with. Are you by chance planning on incorporating this functionality into maybe a future release?
[/LIST]

Anyway, I like your program and think it has alot of potential, but it still is not quite "GUI enough" yet for a true noob. :) What do you think about this and do you have future plans for incorporating more features into pysdm?

---

### Post by drs305 on 2008-07-29
> **caljohnsmith said:**
> I really like the idea of a GUI for modifying fstab, but I have few questions about pysdm:

[LIST=1]
[*]I'm just wondering why doesn't pysdm make a backup of fstab itself? Why does the user need to do that manually? Or couldn't that be added as an option somewhere that the user could choose?
[*]As you mention in your "How Do I Know Which Partition to Choose?" section, pysdm doesn't presently offer any way of helping the user determine which partition to choose; the user is left with going to the CLI again, which seems to undermine the idea of using a GUI to begin with. Are you by chance planning on incorporating this functionality into maybe a future release?
[/LIST]

I agree. I am not associated with the program. It's been around several years but I just stumbled across it after another user mentioned it.

I was thinking the same thing about making a backup. You shouldn't have to go to the command line at all. In fact, your observation prompted me to get into /etc to make sure it *didn't* make a backup. There is a remnant .swp backup but nothing else :(  You could always make a backup with through a file manager but a few lines of code in the original app would have made things a lot easier... One solution would be to make a launcher which included a command to backup fstab.

There are a couple of other major things needing updating: allowing labels and uuid's being two of them.

Added:
Here are some of the deficiencies. They are more annoyances except for # 3:
1. No automatic or selectable backup of fstab.
2. No recognition or use of labels or UUIDs.
3. Uses defunct Options setting of 'Clean' presumably for fsck checking, but this will now produce errors if used.
4. Uses nls for language support rather than more commonly used iocharset.

---

### Post by unutbu on 2008-08-13
drs305, thank you for writing this excellent guide!

One small question: should gid=1000 in this line?
```

auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137
```

---

### Post by drs305 on 2008-08-13
> **unutbu said:**
> drs305, thank you for writing this excellent guide!

One small question: should gid=1000 in this line?
```

auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137
```


You will find many different gid id's used in examples. Here are some of the more common groups:
  0 root
 46 plugdev (group for removable drives)
100 users
110 admin
1000 first user's group

So in the cited example, the group id of 100 is for members of "users". In many ubuntu/linux examples gid=100 is equated with the group "users" and this is what is referenced in this thread's examples. 

The gid can be set to any group you feel appropriate - you could assign it to your group (normally 1000), a 'removable drive' group - plugdev - (46), or a new group you create to allow only certain users access to the partition. Groups can be created with the command "addgroup" or via System > Admin > Users and Groups, where you can assign the actual gid name AND number.

Thanks for asking the question - I will elaborate a bit on the group id's in the main text.

---

### Post by Leo Simon on 2008-10-08
Hi
I'm running Ubuntu 8.04 with kernel
Linux D630 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux


I'm trying to set up ntfs-3g so that I can mount an ntfs partition as a user.    When I mount, I get the error everybody reports. i.e., 
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

Your post says to fix this, chown root /bin/ntfs-3g and chmod 4755 /bin/ntfs-3g.   But when I do this, I get the following error message:

Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

All the posts say to rebuild ntfs-3g with integrated FUSE support but
    a) i don't know how to do this
    b) I believe with Ubuntu 8.04 this is standard 
Help would be ost appreciated.


This problem is now SOLVED, though I don't know how to mark it as such in the proper way.   Thanks to PM help from drs305, I edited the options column of my /etc/fstab to the following
     defaults, umask=007, uid=1000
for the two ntsf partitions that I was trying to mount.    They were mounted at boot time, but now when I log in as a user I, rather than root, own the mounted directories!    No idea how it worked, but heh it worked so I'm happy.    Thanks to drs305.

---

### Post by NTolerance on 2008-10-16
I hope that eventually network mount support can be added to this program.  Getting reliable and decent performing network mounts is harder than ever these days due to GVFS regressions.

---

### Post by zika on 2009-02-09
I've just installed pySDM. if I start it either through System->Administration->Storage_Device_Manager or with Alt-F2->"gksudo pysdm &" I get the window but clicking on sda (which is the only option on left, OK I have only one disk, no partition (out of 3) are shown ...) produces nothing. whole right part is grayed. what am I doing wrong? it did not offer any configuration and I've tried to log-out and log-in as a root but everything is the same. it was installed through synaptic without problems, from repositories.

---

### Post by drs305 on 2009-02-09
Did you click on the white triangle to try to expand the sda list? If you do that you should see the partitions. You would then click on the specific partition (sda1, sda2, etc).

If you aren't getting that to work, please post:
```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```
and tell us what you are trying to accomplish (including desired mount point(s) ).

---

### Post by zika on 2009-02-09
sorry, I've uninstalled it after futile attempts. there was no white triangle that I remember now. I was just wanting to have a nice GUI editor of fstab but I'll stick with nano for that purpose. ... ;)

just for the sake of the argument:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9434e9d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18244   146540039+   7  HPFS/NTFS
/dev/sda2           18245       29793    92767342+  83  Linux
/dev/sda3           29794       30401     4883760   82  Linux swap / Solaris
```

```
/dev/sda1: UUID="BECC3BE3CC3B951D" TYPE="ntfs" 
/dev/sda2: UUID="7e8ce743-2191-42ed-bfa1-ebb8298be377" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="b1fde2cc-6961-4b94-8799-c981f6d3346d"
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7e8ce743-2191-42ed-bfa1-ebb8298be377 /               ext3    errors=remount-ro,noatime 0       1
# /dev/sda3
UUID=b1fde2cc-6961-4b94-8799-c981f6d3346d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by drs305 on 2009-02-09
You can add this line to mount /dev/sda1 (ntfs):
```

UUID=BECC3BE3CC3B951D /media/*yourmountpoint* ntfs auto,users,uid=1000,umask=027,uft8 0 0

```

This gives you:
Mounts to /media/*yourmountpoint* (change this)
Automounts
Users can mount/unmount
Mount point owned by user 1000 (check to see if you are 1000 with "id" in terminal)
Group can read/execute, no access for Others
utf8

If the mount point doesn't already exist, create it and make yourself the owner:
```

sudo mkdir /media/*yourmountpoint*yourmountpoint
sudo chown -R *your-user-name:your-user-name* /media/*yourmountpoint*
Example: sudo chown -R dave:dave /media/mydata

```

Postscript: I have no connection with pysdm other than having written the tutorial after trying to use it. The app is a bit dated and could stand some improvement but there isn't any indication the developer will be updating it. I will review the tutorial and make sure the partition selection directions are clearer.

---

### Post by zika on 2009-02-09
thanks for a quick and thorough reply.
I am not trying to change anything in my /etc/fstab. I keep my ntfs partition with Vista just as a safety net if something goes wrong with ubuntu and I store my music and photos there ... mounting it when needed for listening or viewing. this way I can mess less :). it helped on upgared from 8.04 to 8.10 when networking issues surfaced and I was able to read UbuntuForum to find a quick solution.
I just liked the idea of having a GUI way of doing job of playing with noatime vs. atime, data=writeback vs. ordered and similar (seems that I've grown over that urge)... ;) but, as in most of the cases, "terminal-way" beats all GUI ... ;)
I'll store Your explanation for later use ... very clear and comprehensive.

---

### Post by Dies on 2009-02-09
> **drs305 said:**
> 
Here are some of the deficiencies. They are more annoyances except for # 3:
1. No automatic or selectable backup of fstab.
2. No recognition or use of labels or UUIDs.
3. Uses defunct Options setting of 'Clean' presumably for fsck checking, but this will now produce errors if used.
4. Uses nls for language support rather than more commonly used iocharset.

Agreed.

1 & 2 are bad enough but even more troubling to me is the fact that it will prompt you to set up your root and swap partitions if you click on them. 

That makes absolutely no sense. #-o

It's too bad too, because the interface is nice and clean, should be forked/fixed/updated and installed by default IMHO.

Anyone? :)

---

### Post by jonim8or on 2009-06-18
I've got the same problem as zika:
I've installed PySDM, I run it as root, but I can't select any harddisk or partition. 
My only harddisk shows up in the list, (sda) but there is no triangle next to it to show the partitions. SO basically I can't do anything with it. 

This is on Ubuntu Jaunty (upgraded from Ibex).
This is my harddisk:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89121ac9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       35616   244139805    b  W95 FAT32
/dev/sda3           35617       36832     9767520   83  Linux
/dev/sda4           36833       38913    16715632+   5  Extended
/dev/sda5           37941       38913     7815622+  82  Linux swap / Solaris
/dev/sda6           36833       37939     8891914+  83  Linux

```

---

### Post by drs305 on 2009-06-18
> **jonim8or said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       35616   244139805    b  W95 FAT32
/dev/sda3           35617       36832     9767520   83  Linux
/dev/sda4           [COLOR="DarkRed"]36833       38913[/COLOR]    16715632+   5  Extended
/dev/sda5           [COLOR="RoyalBlue"]37941[/COLOR]       38913     7815622+  82  Linux swap / Solaris
/dev/sda6           36833       [COLOR="RoyalBlue"]37939[/COLOR]     8891914+  83  Linux


I do not know why pySDM isn't displaying the ability to expand sda but it could be the partition table. I notice that there is a very small gap between sda5 and sda6, and also that sda6 comes before sda5 in the partition table. Does gparted work normally? ("gksudo gparted /dev/sda").

If you run "sudo fdisk -l" (lowercase L) do you get the "Partition table entries are not in disk order" message. I don't know if pySDM could be influenced by this or not.

To fix the "disk order" message, you can run the following. Note that anytime you write to a partition table things can go wrong.
```
sudo fdisk /dev/sda
```
Then enter the following options:
*at the prompt:*
m [I](for help)
at the prompt:[/I]
x *(extra functionality - experts only)*
f  *(fix)*
w *(write to disk and exit)*
You may get a warning that devices are in use and the new table will be used at the next boot.  
Check fstab and menu.lst before rebooting if either sda5 or sda6 are listed in these files. If they are, you may need to change the entries to point to the correct partition.

Note that running the above should eliminate the "order" message. There will still be a 1 cylinder difference between the end of the original sda5 and the beginning of sda6 which may affect pySDM.

---

### Post by ticket on 2009-06-20
should pysdm be run using sudo?

i.e. "sudo pysdm" ?

Or does pysdm ask for root privileges at the point one commits the changes?

---

### Post by drs305 on 2009-06-20
> **ticket said:**
> should pysdm be run using sudo?

i.e. "sudo pysdm" ?

Or does pysdm ask for root privileges at the point one commits the changes?

Since it is a graphical app, start it with:
```

gksudo pysdm
```

---

### Post by ticket on 2009-06-21
Ah, thanks!

The how-to says you can start pysdm this way via the system menus:

System > Administration > Storage Device Manager

In that case, is it true that pysdm then runs without root privileges, and so would not be able to make changes to fstab?
 
One final thing, this is what I get when running gksu pysdm:
Warning: Unknown option: rw
Warning: nouser is not suitable for user
Warning: Unknown option: async

Program still does its stuff ok, though.

---

### Post by drs305 on 2009-06-21
> **ticket said:**
> Ah, thanks!

The how-to says you can start pysdm this way via the system menus:

System > Administration > Storage Device Manager

In that case, is it true that pysdm then runs without root privileges, and so would not be able to make changes to fstab?
 
One final thing, this is what I get when running gksu pysdm:
Warning: Unknown option: rw
Warning: nouser is not suitable for user
Warning: Unknown option: async

Program still does its stuff ok, though.

When you start a program via *System > Administration* it will ask for your password before continuing (unless you have already entered it recently). That being the case, it *will* be run as 'root'.

I don't know at what point you are getting those Warning messages. pySDM has it's limitations. I didn't write it and have no real connections to it except for creating this guide. It's really too bad it hasn't been updated.

---

### Post by ticket on 2009-06-21
> **drs305 said:**
> When you start a program via *System > Administration* it will ask for your password before continuing (unless you have already entered it recently). That being the case, it *will* be run as 'root'.


Yes, I can confirm it asks for the root password. Must have done a sudo previously and forgot!

In the end, pysdm wasn't that helpful.  The entry in put into fstab let me mount my new hard data disk, and I could put files on it, but executable programs wouldn't run.  In the end, the following worked for me - I think this is standard practice (but new for guys like me!) - this is just a very simplified how-to:

Make a mount point directory in /media  (e.g. assuming we use the name "MyData" - could be anything, e.g. "Photos", etc)
```
sudo mkdir /media/MyData
```

Back-up and then edit fstab (```
gksu gedit /etc/fstab
```) and add following line to make the disc partition always mount (in this example, assuming the partition id is /dev/sdb1 and has been formatted using ext3)
```
/dev/sdb1  /media/MyData    ext3    defaults  0  0
```

or use this variation if you want the user to have permissions to mount & unmount the partition:
```
/dev/sdb1  /media/MyData    ext3    defaults,users  0  0
```

If you do edit fstab, this command actions any changes:
```
sudo mount -a
```

To fix permission problems:

```
sudo chown -R USERNAME:USERNAME /media/MyData
sudo chmod -R 755 /media/MyData
```

where USERNAME is the name of the user ( as seen in /home/USERNAME )
..........................................
The line that pysdm put into fstab had a more complicated entry than 'defaults', as a result of my also clicking options to allow the user to mount, etc (sorry - I have lost that line now). If I had stuck to the pysdm offered 'defaults', I guess I would have been alright.  Anyway, it seems to me that fstab only needs the 'defaults' option, and the permissions stuff is adequately handled by the chown and chmod commands.

---

### Post by jonim8or on 2009-06-22
fdisk -l does give me the partition tables message:
```

Partition table entries are not in disk order

```
But your commands don't work.
```

$ sudo fdisk sda

Unable to open sda

```

I can use parted.

---

### Post by drs305 on 2009-06-23
jonim8or:

Change the first command to:
```

sudo fdisk /dev/sda

```

Original post is updated. It should work now.

---

### Post by ticket on 2009-06-27
After installing a new data disc, I noticed that the '\lost+found' folder on the new disc was owned by me, as a result of issuing the chown command.
This makes \lost+found easily 'delete-able'.   Normally it is owned by root (as in the system disc).  Should I change the ownership of '\lost+found' to root?

---

### Post by drs305 on 2009-06-27
> **ticket said:**
> After installing a new data disc, I noticed that the '\lost+found' folder on the new disc was owned by me, as a result of issuing the chown command.
This makes \lost+found easily 'delete-able'.   Normally it is owned by root (as in the system disc).  Should I change the ownership of '\lost+found' to root?

I don't believe it will make a difference. If you delete it the 'lost+find' folder will be recreated when fsck is run the next time. I have "chown'd" folders before and never noticed who owned the folder after an fsck check. I expect it continues to be owned by the user. In either case, it still works normally so I wouldn't take any additional action one way or the other.

---

### Post by Aen107 on 2009-10-11
I have followed the tutorial for a integrated NTFS partition.
The problem is that pysdm is forgetting my settings.

"Mount file system in read-only mode" is checked even though I have unchecked it and clicked on apply.

I guess thats the reason why Deluge is not able to download files on this partition?

Thanks for any hints!

Regards

---

### Post by drs305 on 2009-10-11
> **Aen107 said:**
> I have followed the tutorial for a integrated NTFS partition.
The problem is that pysdm is forgetting my settings.

"Mount file system in read-only mode" is checked even though I have unchecked it and clicked on apply.

I guess thats the reason why Deluge is not able to download files on this partition?

Thanks for any hints!

Regards

pysdm has its limitations. Perhaps the easiest method to correct your fstab is just open and edit it manually:
```

sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab

```

Find the partition/mountpoint entry pysdm created and look at the options. You will probably find "ro" among them. Remove "ro", and you can make yourself the owner of the mountpoint by adding "uid=1000" to the list of options. This assumes you are user 1000, which you can check with the "id" command.

If you aren't sure of how to do this, just post your fstab and we can take a look at it:
```

cat /etc/fstab

```

Here is an excellent guide to fstab settings:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Aen107 on 2009-10-11
Thanks for your answer.
Here is my fstab. I want partition sda2 to be read/writeable for deluge.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc     defaults                                              0  0  
# Entry for /dev/sda5 :
UUID=757a706b-4b6f-4885-afc4-74c281599e23  /               ext3     relatime,errors=remount-ro                            0  1  
# Entry for /dev/sda6 :
UUID=c97d900a-603a-4555-8d61-3c1e11f303ad  none            swap     sw                                                    0  0  
/dev/sda1                                  /media/windows  ntfs-3g  defaults,locale=en_US.UTF-8                           0  0  
/dev/sdb1                                  /media/sdb1     ntfs     nls=iso8859-1,umask=000                               0  0  
/dev/sda2                                  /media/sda2     ntfs     nls=iso8859-1,users,umask=000,utf8,gid=1000,uid=1000  0  0  
/dev/sda5                                  /media/sda5     ext3     defaults                                              0  0  
/dev/sda6                                  /media/sda6     swap     defaults                                              0  0  
```

---

### Post by Aen107 on 2009-10-12
I have now found the solution.
When I mounted the partition in pysdm, I did not adapt the name. So deluge and vuze tried to access the old folder/path media/Daten/Download. Pysdm changed it automatically to media/sda2 which was the reason why vuze/deluge was not able to find the torrent and gave me a strange error message.

thanks for the replies!

---

### Post by Ian Clark on 2010-01-17
> **ticket said:**
> In the end, the following worked for me - I think this is standard practice (but new for guys like me!) - this is just a very simplified how-to...

This is the best solution I've seen so far. I still get a mounted device icon on the desktop, but I don't have to enter a password, and there's a nice new name for the partitions. I'll have to test Kdenlive to see if file links to these partitions will hold, however.

Thanks, ticket!

---

### Post by sinhanikhil.5 on 2010-03-25
> **drs305 said:**
> [CENTER]**[COLOR=MAROON][SIZE=3]Storage Device Manager - Worry-Free Fstab Configuration[/SIZE][/COLOR]**[/CENTER]
Storage Device Manager provides an easy, non-technical GUI method to make changes to mounting options without manually editing any files. It does for mounting partitions what [StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177") does for editing grub's menu.lst. Storage Device Manager (PySDM) allows the full range of options available to those who manually edit fstab while simplifying the steps so that even beginners will feel comfortable making the same changes through Storage Device Manager. You no longer have to wonder if *relatime* is really the correct spelling.

Note that pySDM is an older application that hasn't been updated recently. It has some limitations. For one, it does not make a back up copy of the */etcfstab* file. Secondly, it uses the older method of identifying partitions with "sdXX" in the fstab file. The preferred method, using UUIDs or labels, must be done outside of the pySDM application if desired.

Before proceeding, please note that there are some excellent references for further information regarding fstab located at the bottom of this guide. 

Sections:
[CENTER][COLOR=MAROON][B]5 Minute Guide ---  Installing & Starting ---  Fstab Backup  ---  Using PySDM
When You Will Need Fstab ---  Notes --- Partition Commands ---  Links[/B][/COLOR][/CENTER]
**[COLOR=Navy][SIZE=3]1. Installing & Starting Storage Device Manager (PySDM)[/SIZE][/COLOR]**
Storage Device Manager is accessed via [COLOR=MAROON]System > Administration > Storage Device Manager[/COLOR]. From the command line, start it with "*gksu pysdm*". Root privilege is required since PySDM makes changes to system files. *gksu* is the cousin of *sudo* and should be used with graphical apps. 

If Storage Device Manager is not in your menu, install it via synaptic ( [COLOR=MAROON] System > Administration > Synaptic Package Manager[/COLOR] ). If you don't see 'pysdm' listed in synaptic or the following command line method is not successful, go to *Synaptic > Settings > Repositories > Ubuntu Software* and make sure the '*universe*' repository is checked. Hit the 'Reload' button to refresh the package list and then select *pysdm*. You can also install it via command line with:
```
sudo aptitude install pysdm 
```**[COLOR=Navy][SIZE=3]2. Backup Fstab[/SIZE][/COLOR] **
[COLOR=MAROON]**Before modifying any system file, it is good practice to make a backup copy.**[/COLOR] If you intend to make multiple changes 
within a short time, I'd recommend assigning each backup a unique number (fstab.bak1, bak2, etc). To make a backup:
```
sudo cp /etc/fstab /etc/fstab.bak1 
```**[COLOR=Navy][SIZE=3]3. Using PySDM[/SIZE][/COLOR] **
The PySDM interface consists of 3 sections: the *Partition* window for selecting the partition, the *General Configuration* window for setting fstab options, and the *Dynamic configuration rules* window for modifying hot-plug device and removable settings. 

**[COLOR=MAROON][SIZE=3]*Partition List*[/SIZE][/COLOR] **
When Storage Device Manager starts, it reads the devices/partitions available to it and displays them in the far left window. Starting with Hardy, Ubuntu no longer refers to devices as *hda* even for IDE drives. 

**Select the partition which you want to mount by expanding the drive (sda, sdb, etc) and clicking on the triangle to the left of the individual partition (sda, sdb, etc).** *Until you select a partition the right side of PySDM will be grayed out and unavailable for input*. If you don't know which partition you want to select, go to the *Which Partition?* section at the bottom of this page for help. The first time PySDM works with a partition, even if an entry already exists in fstab, it will ask '*Configure Now?* - click OK. 

**[COLOR=MAROON][SIZE=3]*General Configuration*[/SIZE][/COLOR] **
[LIST]
[*][COLOR=NAVY]***Name***[/COLOR] 
*Name* is the mountpoint you wish to use, by default a subfolder of /media and named the same as the partition (e.g. 'sda3'). You can choose a more descriptive name, such as 'my-data' or whatever you wish. The folder will be created if it does not exist. **[COLOR=MAROON]The folder created and/or selected should be empty - do not select a folder already containing files or subfolders.[/COLOR]**
[*][COLOR=NAVY]***Mountpoint***[/COLOR] 
If you do not want to use /media as the base mountpoint you can choose a different folder by clicking on the *folder icon* and navigating to another folder. If you wish to make a new folder while navigating your system, click the '*new folder*' at the top right of the navigation window. If you get 'lost' while navigating the folders, '*File System*' in the left window will get you back to **/** .
[*][COLOR=NAVY]***Type***[/COLOR] 
Take a breath and relax - you don't have to make a decision here. *Type* is just informing you the type of partition you are working with (e.g. ext3, ntfs, vfat).
[*][COLOR=NAVY]***Options***[/COLOR] 
Here's the meat of the program. Initially '*Options*' is set to '*defaults'*. Clicking the '**Set Defaults**' button also resets this window to '*defaults'*. Selecting '*defaults'* sets the following options: *rw, suid, dev, exec, auto, nouser, async*. Starting with Hardy, '*relatime*' is also a default on native linux (i.e. ext2/3) partitions. For information on each of these settings, refer to the links at the bottom of this guide. If you add or change any options, '*defaults*' will not be shown but will apply to any setting not overridden. One other note, in addition to automatic entries, anything you type in this window will be input in the options section of fstab. For instance, there is no option to set *dmask* or *fmask* but you can add them to the options line and they will be applied along with the other settings. All options are joined by commas with no spaces in the entire section.
[*][COLOR=NAVY]***Assistant***[/COLOR]
This section could also be called '*More Options*' since it is the section in which you can change settings from '*defaults*'. Most of the settings are self-explanatory. The setting options presented vary with the type of partition selected (ext3, ntfs, fat32, etc). I will comment on a few of the options you may wish to consider changing. Any change you make in these sections will remove the '*defaults*' option from the main window and non-default options will be displayed. Default settings will still apply to those settings which are not overridden. 

[COLOR=Blue]Auto-selected items are colored blue.[/COLOR] **Black Bold** items are the actual  designations that appear in the fstab options section when selected. _Default options_ are underlined. They will NOT appear in fstab but apply unless the associated non-default option is entered. 
[SIZE=3][COLOR=RED]* [/COLOR][/SIZE] Items which should be considered. Author recommendations are listed in [COLOR=GREEN]**green**[/COLOR].
[LIST]
[*]Mounting Tab
[LIST]
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Mount read-only* *. **_ro_** The Read-Only option is OFF (rw) for linux ext2/3 partitions and ON* (ro) by default for VFAT/NTFS partitions. _For VFAT/NTFS partitions, this option must be *unchecked* to enable read/write._ For non-linux partitions, the PySDM umask (and dmask/fmask manual entries) setting can allow RW access for non-linux partitions even if RO is enabled.
[*]*Allow group mount*. **group=**  Allow any group member to mount. Enter group id.
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Allow any user to mount*. **[COLOR=GREEN]users[/COLOR]** Normally the option would allow a user to click on a partition icon or use the 'mount /dev/sdXX' option to mount the partition without root privileges. If this option doesn't work for NTFS partitions try mounting via terminal. [COLOR=MAROON]If you get an 'Unprivileged user' message, see the section at the bottom of the page on NTFS-3g errors.[/COLOR]
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Allow a user mount*. **_nouser_/user**
[*]*[COLOR=Blue]File system mounted at boot time[/COLOR]*. **_auto_/noauto**
[*]*Owner of device can mount*. **owner**
[*]*Owner user of filesystem *. **uid=** Enter uid in window. Whoever mounts the device owns it. Your uid is normally 1000 if you are the primary user. To check, run the following command in terminal: *id*. You may wish to select this option.
[*]*Support extended attributes*. **--/user_xattr** (Linux partitions only).
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Check file system on mount time*. (Linux partitions only). [COLOR=Red]**This command is no longer supported and may produce an error message. Do not select it.**[/COLOR] Fsck checks are no longer included in the *options* section; they are now handled by the last digit on the line (normally 0, 1 or 2).
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*[COLOR=Blue]Umask[/COLOR]*. ***000*** (Non-linux partitions only). This is an entire subject in itself. The PySDM menu does not offer dmask and fmask value inputs for ntfs/fat partitions. You can manually enter them them in the *Options* window if you wish. 
On NTFS partitions, if the fstab options are left at "defaults" the mountpoint and all folders/files will be owned by root but readable/writable by the user. If uid/gid options are used, the mountpoint is still owned by root but all subfolders and files are owned by the user specified by "uid=".
Refer to the *Permissions* link at the bottom of the page for more information. Here are some common umask settings you may wish to consider:
000 (Permissions 777) - Default PySDM setting. Anyone can do anything! 
022 (Permissions 755) - Owner read/write/execute (rwx), group (rx), others (rx). 
**[COLOR=GREEN]027[/COLOR]** (Permissions 750) - Owner rwx, group rx, others can't access partition.
077 (Permissions 700) - Only the owner can rwx, group and others cannot access partition.  
** **[I]Instead* of umask, dmask & fmask can be used but must be entered manually on the *Options* line.** Two useful settings would be:[/I]
dmask 027,fmask137 - Owner has rwx for directories, rw for files. Group has rx for dirs and r for files.
dmask 000,fmask111 - Owner rwx dirs, rw files. Group rwx dirs, rw files. Others rwx dirs, rw files.
*Deselect* umask if dmask/fmask settings are entered in the *Options* window.
[*]*Owner group of filesystem*. **gid=**
[/LIST]
 
[*]Special Files
[LIST]
[*]*[COLOR=Blue]Permit execution of binaries[/COLOR]*. **_exec_/noexec** If unchecked, this option prevents execution of program files within the partition. This may be desirable for a storage or data partition which nevertheless contains executable files. Unchecking this box will also disable the warning message in nautilus and other applications which asks if you want to run the file or open it. If not checked, the file will open without the query.
[*]*[COLOR=Blue]Permit executables to change user/group identity[/COLOR]*. **_suid_/nosuid** Relates to scripts. Note: If you need to know about this, you probably don't need PySDM!
[*]*[COLOR=Blue]Interpret character or special block devices[/COLOR]*. **_dev_/nodev** See note in previous entry!
[/LIST]
 
[*]Journaling (Linux partitions only)
[LIST]
[*]*Specify a journaling mode*. **/data=**  Ordered, journal or writeback.
[*]*Update journal or specify the inode where it is*. **journal=**
[*]*Do not load journal on mounting*. **_noload_**
[/LIST]
 
[*]Performance
This section deals with recording data access times and synchronization matters. User input is not normally required. Many items apply to linux partitions only.
[LIST]
[*]*[COLOR=Blue]Update directory time for each access[/COLOR]*. **_diratime_/nodiratime**
[*]*I/O to file system should be done synchronously*. **_async_/sync**
[*]*All directory updates should be done synchronously *. **_nodirsync_/dirsync**
[*]*[COLOR=Blue]Update file time for each access[/COLOR]*. **_atime_/noatime**
[*]*[COLOR=Blue]Specify what to do in case of errors=[/COLOR]*. **_remount-ro_/continue/panic** Really, panic is an option..
[*]*Do not attach buffer_heads to file pagecache*.
[*]*Get group id from the directory for a new file*.
[*]*Synchronize data and metadata every specified seconds*. **commit=**
[*]*Use a especific block as superblock*. **sb=**
[*]*Use old new inode allocator*.
[/LIST]
 
[*]Miscellaneous
This section deals with network file systems, default character encoding, UFT-8 file name conversion, upper/lower case interpretation, and escape sequences. The default character set is the older iso8859-1. If your system is having trouble reading the directory or file names, changing these settings may help.
[LIST]
[*]*File system requires network*. **_netdev** 
Linux partitions (ext2/ext3) only:
[*]*User allowed to use reserved space*. **resuid=**
[*]*Group allowed to use reserved space*. **resgid=**
[*]*Support POSIX access list*.
[*]*Disables 32 bit user and group id*.
[*]*Print debugging info*.
[*]*Minix behavior for stat information*. 
Non-Linux only:
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*[COLOR=Blue]Character set to use for file names[/COLOR]*. **nls=iso8859-1**  The english-speaking standard of iso8859-1 is the default and checked, The *mount* man page uses the  iocharset=8859-1 . If this is listed in the Options window, I recommend changing **nls=** to **iocharset=** I personally turn it **[COLOR=GREEN]off by deselecting it.[/COLOR]**.
[*][SIZE=3][COLOR=RED]* [/COLOR][/SIZE]*Use UTF-8 for converting file names*. **utf8**  **[COLOR=GREEN]Select this[/COLOR]** for ntfs and vfat (fat16/32) partitions.
[*]*Update file time for each access*. **posix**
[*]*Use escape sequences for unknown characters*. **uni_xlate=**
[/LIST]
 
[/LIST]
 
[*][COLOR=NAVY]***Mount Button***[/COLOR] 
You can mount and unmount the selected partition by clicking on this button. Cycling Unmount > Mount will allow the options you have designated to take effect. It is equivalent to running the 'sudo umount' and 'sudo mount' commands on the particular partition.
[*][COLOR=Red]***Apply Button***[/COLOR] 
Finallly! Clicking this button applies the changes. In fstab, the revised or new entries are placed at the bottom of the file. PySDM at present does not use UUID's or LABEL designations. If you have entries in fstab that use either of these designations, they will either remain unchanged or become comments. The '/dev/sdXX' line generated by PySDM will appear below previous entries in the /etc/fstab file. In this case, even though there are multiple entries for the same partition, the PySDM lines will be loaded last and thus will take precedence over earlier lines.
[/LIST]

**[COLOR=MAROON][SIZE=3]*Dynamic Configuration Rules*[/SIZE][/COLOR] **
This section enables you to set *udev* rules. Click on the '*New*' button and you can set the conditions of Name, Model, Vendor, and bus type.
After setting specifications to identify the device, you can set the user, group, device file name, and specify user's rights. You can also create a link with a name of your choosing. The settings are stored in /etc/udev/user.rules. For more information about udev configuration refer to the man page ( *man udev*) or the link at the bottom of this guide.


**[COLOR=Navy][SIZE=3]4. When You Will Need Fstab (and How to Do It)[/SIZE][/COLOR] **
While PySDM offers an easy and safe way to change or create partition mounting instructions, there are several reasons why you might wish to edit fstab manually. [COLOR=MAROON] **Before modifying any system file, it is good practice to make a backup copy.**[/COLOR] 
```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab 
``` 
[LIST]
[*]Refer to the instructions in the '3 Minute Guide' *Removable Drives* section for how to make the following changes.
[*]UUIDs. PySDM currently does not use UUIDs. If your fstab contains a UUID entry and you attempt to create a new listing for the same partition PySDM will create a "/dev/sdXX" entry at the bottom of the file. PySDM will either place a comment (#) symbol at the start of the original line and/or will override the UUID entry by placing the PySDM-generated entry at the bottom of fstab. A technique if you would like to retain the UUID entry would be to generate an fstab entry with PySDM, copy the options to the UUID line, and then delete the remainder of the PySDM entry. Remember that since PySDM does not use UUIDs, it will not update them if they are changed due to repartitioning.
[*]LABELS. PySDM currently does not use labels. Read the previous entry on UUIDs. The same technique applies for labels.
[*]*/dev* Designations. Some users prefer not to use /dev designations. In the past some updates/upgrades changed the letter designations of partitions. Since Hardy now uses the /dev/sdXX designation, there should be no more unrequested changes from /dev/hdXX to /dev/sdXX or vice versa. If you don't want to use the /dev designations run PySDM and then replace the /dev/sdXX designation with the UUID or label. (see commands below for determining these)
[*]FSCK Entries. The last digit in an fstab entry is provides instructions for *fsck* (disk checking).
The last digit relays the following instructions to *fsck*:
0 - Do not check. (This should always be the setting for non-linux partitions.)
1 - Check first. (Root)
2 - Perform check with a lower priority than 1 (when running during the same session).
PySDM always creates a listing with the FSCK option set at '0'. If you want to change this you will need to edit fstab and change the setting.
[/LIST]

**[COLOR=Navy][SIZE=3]5. Notes & Additional Information[/SIZE][/COLOR] **

**[COLOR=MAROON][SIZE=3]How Do I Know Which Partition to Choose?[/SIZE][/COLOR] **
When adding a new device or after partitioning a drive, you may not be sure which partition you want to select. One method you can try is to watch the list as the device is plugged in. If it may be mounted, run "sudo umount -a". There will be some busy messages but it won't hurt anything. Then plug in the device and see if it mounts by watching the *Partition List* window to see if it appears. Normally PySDM will place this 'new' device at the bottom of the list, even if the letter designation is lower than some already displayed. You can use some of the commands listed later in this section to help you investigate your system's partition information. Some of the following characteristics may help you determine the partition:
[LIST]
[*]Size - Approximate size of the partition: **df -h**
[*]Formatting - Type of formatting: **df -T | grep "/dev/"**
[*]Bootable - Bootable Partitions: **sudo fdisk -l | grep "*"**
[*]View Everything - **sudo fdisk -l && sudo blkid && df -Th && cat /etc/fstab && mount**
[/LIST]

**[COLOR=MAROON][SIZE=3]*'Unprivileged User' NTFS Errors*[/SIZE][/COLOR] **
NTFS-3g was incorporated in Hardy and is enabled by default. Nevertheless, it is possible to get an error message when trying to mount an NTFS partition as a specific user. The error message is:
[LIST]
[*]Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
To correct this condition:
```

sudo chown root $(which ntfs-3g)
sudo chmod 4755 $(which ntfs-3g)

```
[/LIST]
**[COLOR=Navy][SIZE=3]6. Useful Partition Commands (Results in italics)[/SIZE][/COLOR]**

What partitions are currently mounted?
**mount**
*/dev/sda5 on / type ext3 (rw,errors=remount-ro)*

What is contained in my fstab (to exclude commented lines, add [ **| grep -v "#"** ]?
**cat /etc/fstab**
[I]# Entry for /dev/sda5 :
UUID=4d33bfe6  /  ext3  defaults,errors=remount-ro  0  1 [/I]

What is  the UUID / LABEL of my partition?
**sudo blkid -c /dev/null**
*/dev/sda1: UUID="CEECFF9EECFF7F51" TYPE="ntfs"*

What partitions are on my computer (note the switch is a small L)?
**sudo fdisk -l**
*/dev/sda5   *        2804        4078    10241406   83  Linux*

How much space do I have on my partitions?
**df -Th**
*/dev/sda5     ext3    9.7G  3.9G  5.4G  42% /*

How do I make a label for my NTFS partition? (Install *ntfsprogs* first)
sudo ntfslabel <device> <label>
*sudo ntfslabel /dev/sda5 MYLABEL*

How do I make a label for my ext2/3 partition? (Install *e2fsprogs* first)
**sudo tune2fs -L <label> <dev>**
*sudo tune2fs -L MYLABEL /dev/sda5*

How do I make a label for my fat32 partition? 
[COLOR=Red]Warning: This overwrites any data on the partition.[/COLOR]
**sudo mkfs.vfat -F32 -n <label> <device>**
*sudo mkfs.vfat -F 32 -n MYLABEL /dev/sda5*
sudo mkfs.vfat -F32 -n /dev/sdc 1 usb.5

**[COLOR=Navy][SIZE=3]7. Links[/SIZE][/COLOR] **

**[COLOR=MAROON][SIZE=3]Ubuntu Community Related Links[/SIZE][/COLOR] **
[Introduction to Fstab]("https://help.ubuntu.com/community/Fstab")
[UsingUUID]("https://help.ubuntu.com/community/UsingUUID")
[LinuxFilesystemsExplained]("https://help.ubuntu.com/community/LinuxFilesystemsExplained")
[RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive") (Really - How to Label Any Format)
[MoveMountpointHowto]("https://help.ubuntu.com/community/MoveMountpointHowto")
[MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

**[COLOR=MAROON][SIZE=3]Other Links[/SIZE][/COLOR] **
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131") [How to edit & understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html") [Understanding & Using File Permissions]("https://help.ubuntu.com/community/FilePermissions")
[PyGTK Storage Device Manager]("http://pysdm.sourceforge.net/")
[Writing udev Rules]("http://reactivated.net/writing_udev_rules.html")

**[COLOR=MAROON][SIZE=3]What's With the Name PySDM?[/SIZE][/COLOR] **
PySDM runs a PyGTK graphical interface = py for the python wrapper and GTK for the Gimp Tool Kit.


](*,) after reading u i have done something to my comp. prolly i'll start a new thread in few days after i figure out what exactly looks like happened.:cry:



[COLOR=White].[/COLOR]

---

### Post by drs305 on 2010-03-25
> **sinhanikhil.5 said:**
> ](*,) after reading u i have done something to my comp. prolly i'll start a new thread in few days after i figure out what exactly looks like happened.:cry:
[COLOR=White].[/COLOR]

Sorry you are having problems. I and others will be glad to help.

If you followed the instructions you should have a backup of your original fstab called fstab.bak or fstab.bak1. If so, you can restore the original fstab with the following command (example with fstab.bak1):
```
sudo mv /etc/fstab /etc/fstab.bad
sudo mv /etc/fstab.bak1 /etc/fstab
```

If you can't boot at all, boot to the recovery mode command line and then run the commands above.

There isn't really the need to quote the entire original post in your previous post. Merely stating that you followed the instructions in post #1 would be sufficient and makes your post much easier to read.

---

### Post by sinhanikhil.5 on 2010-03-26
> **drs305 said:**
> Sorry you are having problems. I and others will be glad to help.

If you followed the instructions you should have a backup of your original fstab called fstab.bak or fstab.bak1. If so, you can restore the original fstab with the following command (example with fstab.bak1):
```
sudo mv /etc/fstab /etc/fstab.bad
sudo mv /etc/fstab.bak1 /etc/fstab
```

If you can't boot at all, boot to the recovery mode command line and then run the commands above.

There isn't really the need to quote the entire original post in your previous post. Merely stating that you followed the instructions in post #1 would be sufficient and makes your post much easier to read.
Sure thanks for your help offer and I am sure I'll need it. I'll work on my system on saturday. I really don't wanna mess up today(weekday) as already did a lot. I am unable to boot my Ubuntu. 
:(
I am using window again, well its fine.
 
 
 
 
[COLOR=white].[/COLOR]

---

### Post by skript_teaze on 2010-07-18
I'm trying to get my Vista NTFS Partition to auto-mount so that the links I have in my share directory work. I ran the following command in terminal to work out whats what:

sudo fdisk -l && sudo blkid && df -Th && cat /etc/fstab && mount

I got this back...

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf54813e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004d910

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9356    75146240   83  Linux
/dev/sdb2            9356        9730     3002369    5  Extended
/dev/sdb5            9356        9730     3002368   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5d4527d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS
[1]+  Done                    gksu pysdm
/dev/sda1: LABEL="Matts Disk" UUID="36F89EFDF89EBB17" TYPE="ntfs" 
/dev/sdb1: UUID="1bd3f1ab-6730-4b6a-9a21-9a9cfc506a37" TYPE="ext4" 
/dev/sdb5: UUID="b1950a40-1fde-4733-b69f-fc69f11cfc09" TYPE="swap" 
/dev/sdc1: UUID="D4FC9F52FC9F2E2C" TYPE="ntfs" 
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb1     ext4     71G   23G   45G  34% /
none      devtmpfs    497M  384K  497M   1% /dev
none         tmpfs    501M  216K  501M   1% /dev/shm
none         tmpfs    501M  196K  501M   1% /var/run
none         tmpfs    501M     0  501M   0% /var/lock
none         tmpfs    501M     0  501M   0% /lib/init/rw
/dev/sr0   iso9660    105M  105M     0 100% /media/Xbox360_1_1
/dev/sda1  fuseblk    932G  383G  550G  42% /media/Matts Disk

I've worked out that my NTFS Partition is sda1. (The other NTFS partition is my Windows installation partition.)

What do I do to get this to mount when I start Ubuntu so that I dont have to keep clicking the drive for the folder links to work?

---

### Post by drs305 on 2010-07-18
> **skript_teaze said:**
> 
What do I do to get this to mount when I start Ubuntu so that I dont have to keep clicking the drive for the folder links to work?

1. Create a mountpoint. (/media will display on the desktop, /mnt will not - it's your choice. For this example, I'll use "mnt" and call it 'vista'. Name it whatever you want, but save yourself headaches by having no spaces in the name). You might as well make yourself the owner of the new mount point, although this won't affect ntfs permissions.
```
sudo mkdir /mnt/vista
sudo chown $USER: /mnt/vista
```
Open fstab for editing:
```
gksu gedit /etc/fstab
```

Add this line for your vista partition (sda1). It assumes you are the original user of Ubuntu with a "uid" of 1000. You can check by running "id" in a terminal.
> UUID=36F89EFDF89EBB17   /mnt/vista ntfs  auto,users,uid=1000,gid=1000,umask=027,uft8 0  0
Save the file. Then run these commands. The first will unmount your Vista partition if it is already mounted. The second will attempt to mount it with your new fstab entry. If it works, the Vista partition will be mounted on /mnt/vista and you will see no messages about sda1 after you press ENTER to execute the command.
> sudo umount /dev/sda1
sudo mount -a

There are several links in the original post if you want to learn more about the ntfs options available to use and/or what they mean.
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by oni5115 on 2010-08-19
I noticed I was having some weird issues with my NTFS data partition when using the settings in the opening post.  Specifically, I had issues running installers or programs.  Nothing would run in Wine and I could not run the catalyst install scripts.  Note that copying them to my /home partition allowed me to run them fine.  Even stranger, I could run bash scripts fine, while the ccc installer and wine would tell me the execute bit was not properly set (even when files were marked "executable").

After playing with it for a few I settled on:
"nls=iso8859-1,umask=000,gid=1000,uid=1000"

I have no idea if this can or will cause any issues on my system, but at least everything is working as I want it too for the moment.

---

### Post by drs305 on 2010-08-19
oni5115,

I suspect setting the umask value to 000 is what fixed your problem. It sounds like there was a permission problem that wasn't allowing you to run things that weren't in your home partition. Changing umask probably worked around that.

---

### Post by Linuxforall on 2010-08-27
On a related note, those looking for its equivalent in KDE should check out mountmanager which is in the repos, its full KDE app with many more features than pysdm.

---

### Post by drs305 on 2010-08-27
> **Linuxforall said:**
> On a related note, those looking for its equivalent in KDE should check out mountmanager which is in the repos, its full KDE app with many more features than pysdm.

Thanks Linuxforall. Even though I wrote the original post, I often think PySDM is more trouble than it's worth. I'll put a mention of *mountmanager* in the links section.

---

### Post by Linuxforall on 2010-08-27
> **drs305 said:**
> Thanks Linuxforall. Even though I wrote the original post, I often think PySDM is more trouble than it's worth. I'll put a mention of *mountmanager* in the links section.

You are welcome,actually mountmanager is pysdm with more, having used both, never ran into any issues. When I switched over to KDE, I was looking for a pure KDE utility, pysdm is primarily written for gnome.

---

### Post by amjjawad on 2010-11-20
[SIZE=2]Thanks as always, drs305 for this great guide :)

I followed your instructions and I was able to auto mount two partitions which I need to be mounted. However, I'm having a bit of a problem here. These two partitions are NTFS partitions and PySDM is refusing to change the "read-only" option so I can't even rename any file there or make new folder.
Is there any way I could fix that?

If not, how do I disable Auto Mounting? just clear all the info and reset to the default settings or there's a specific procedure for that?

Thanks a lot :)





[/SIZE]

---

### Post by drs305 on 2010-11-20
> **amjjawad said:**
> However, I'm having a bit of a problem here. These two partitions are NTFS partitions and PySDM is refusing to change the "read-only" option so I can't even rename any file there or make new folder.
Is there any way I could fix that?


The ownership of NTFS partitions is done at the time of mouting. You can make yourself the owner, which should allow you to read/write:

```

id # Confirm you are uid=1000, if not, change the number below.
gksu gedit /etc/fstab &
```
The first command checks your user id. The first user is 1000, so I will use that in the example.

On your fstab line for the NTFS partitions, use these as the options. That should make you the owner and give you rw privileges:

> auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137

---

### Post by amjjawad on 2010-11-21
> **drs305 said:**
> The ownership of NTFS partitions is done at the time of mouting. You can make yourself the owner, which should allow you to read/write:

```

id # Confirm you are uid=1000, if not, change the number below.
gksu gedit /etc/fstab &
```The first command checks your user id. The first user is 1000, so I will use that in the example.

On your fstab line for the NTFS partitions, use these as the options. That should make you the owner and give you rw privileges:

Ok, this is what I have on my fstab file:

> /dev/sda5
/media/data
[COLOR=Red]ntfs  nls=iso8859-1,ro,users,umask=000,utf8  0  0  [/COLOR]

/dev/sdb2
/media/data2
[COLOR=Red]ntfs  nls=iso8859-1,ro,users,umask=000,utf8  0  0[/COLOR]
Shall I replace the two [COLOR=Red]***red lines***[/COLOR] with:

>                               auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=  137                      The whole two red lines with 0 0 or just: "[COLOR=Red]ntfs  nls=iso8859-1,ro,users,umask=000,utf8" ?


[B][COLOR=black]_Edit:_ THANKS A LOT, it's working now :D

[/COLOR][/B] 
[/COLOR]

---

### Post by drs305 on 2010-11-21
> /dev/sda5  /media/data [COLOR=Red]ntfs  auto,users,uid=1000,gid=1000,utf8,umask=000  0  0  [/COLOR]

/dev/sdb2  /media/data2 [COLOR=Red]ntfs  auto,users,uid=1000,gid=1000,utf8,umask=000  0  0[/COLOR]


I would recommend changing the device names to UUIDs (or even better, LABELs). You can get the UUIDs with this command:
```
sudo blkid -c /dev/null
```
You can give your partitions labels via Disk Utility or Gparted.

The format would then look like the following, replacing the UUID numbers to the ones returned from the above command. For a label, the format would be "LABEL=<label name>", such as: LABEL=mydata
> 
UUID=[COLOR="Red"]78A42E452734F6FF [/COLOR] /media/data [COLOR=Red]ntfs  auto,users,uid=1000,gid=1000,utf8,umask=000   0  0  [/COLOR]

UUID=[COLOR="Red"]452734F6FF78A42E[/COLOR]  /media/data2 [COLOR=Red]ntfs  auto,users,uid=1000,gid=1000,utf8,umask=000   0  0[/COLOR]


Note in my example I used "utf8". You used "nls=iso8859-1". I believe you should have one or the other - I've not seen both in an fstab setting.

Also note that the umask=000 gives everyone access to rw your files. It may be what you want but normally the setting is a bit more restrictive.

---

### Post by amjjawad on 2010-11-23
> **drs305 said:**
> I would recommend changing the device names to UUIDs (or even better, LABELs). You can get the UUIDs with this command:
```
sudo blkid -c /dev/null
```You can give your partitions labels via Disk Utility or Gparted.

But I already have that. I mean, both partitions that I'm auto-mounting are having Labels. So, I'm afraid I didn't really understand what do you mean?

> 
Note in my example I used "utf8". You used "nls=iso8859-1". I believe you should have one or the other - I've not seen both in an fstab setting.

Yes, I have "utf8" and I don't have "nls=iso8859-1" anymore.

This is how fstab looks after I followed your instructions from the previous post:

> /dev/sda5
/media/data1            
ntfs  auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask= 137   0  0  

/dev/sdb2
/media/data2  ntfs  auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask= 137   0  0  


> 
Also note that the umask=000 gives everyone access to rw your files. It may be what you want but normally the setting is a bit more restrictive.

Everyone who is able to use my PC? if someone knows the password and able to access my PC Physically, he/she will be able to RW from these two partitions. Is that what you mean?

---

### Post by drs305 on 2010-11-23
> **amjjawad said:**
> But I already have that. I mean, both partitions that I'm auto-mounting are having Labels. So, I'm afraid I didn't really understand what do you mean?

What I meant was that you can use labels in fstab. Instead of:
> UUID=<some UUID>
You can use:
> LABEL=mydata
In this example, the advantage is that in Nautilus Places and Desktop instead of seeing the partition as "30GB" it would display it as "mydata". The UUID and label are unique and won't change (unlike device names such as sda,sdb), which is the important thing. I just find labels more convenient.

> 
Everyone who is able to use my PC? if someone knows the password and able to access my PC Physically, he/she will be able to RW from these two partitions. Is that what you mean?
Read, write, execute. These functions will be available to anyone who accesses your files. Permissions are given the the user, a group, and others. "000" gives the read/write/execute permissions to all three. Often users restrict 'others' from some or all the permissions. 

Many linux systems have multiple users and permissions are used to prevent or grant access to certain folders/files on the same system. 

Here is more information:
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by amjjawad on 2010-11-23
> **drs305 said:**
> In this example, the advantage is that in Nautilus Places and Desktop instead of seeing the partition as "30GB" it would display it as "mydata". The UUID and label are unique and won't change (unlike device names such as sda,sdb), which is the important thing. **I just find labels more convenient.**

That's exactly what I have done :)
It's so confusing to read sda1, sda2, etc and it's so much easier to read something like "mydata" so yes, already done :) Thank you!

> 
Read, write, execute. These functions will be available to anyone who accesses your files. Permissions are given the the user, a group, and others. "000" gives the read/write/execute permissions to all three. Often users restrict 'others' from some or all the permissions. 

Many linux systems have multiple users and permissions are used to prevent or grant access to certain folders/files on the same system. 

Here is more information:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Aha, but again, someone has to be in front of my PC so he/she could do that, right? he/she must have physical access to the PC in order to access these files.
I'm going to check that link, thanks a lot :)

---

### Post by drs305 on 2010-11-23
> **amjjawad said:**
> Aha, but again, someone has to be in front of my PC so he/she could do that, right? he/she must have physical access to the PC in order to access these files.

Access could be from a remote computer, not just physical presence.

---

### Post by amjjawad on 2010-11-23
> **drs305 said:**
> Access could be from a remote computer, not just physical presence.

Ops!
Okay then, have to start reading that link you provided it :)

Thanks again, drs305 :)

---

### Post by Muzafsh on 2011-02-06
Well i messed it all...

I wanted to have my partitions mount automatically on startup.

Installed PySDM and kept exploring(messing as it has turned out) with it :(

I did not make a backup of my fstab. And now my Ubuntu 10.10 wont boot.

However i was able to boot from my USB and lay my hands on the fstab file on my system. It turned out there were quite a few lines that were inserted apart from the default. I deleted all those extra lines and hoped my Ubuntu would now boot up. But it turned out, i was wrong. i think while exploring PySDM i seem to have messed up the default partition settings too.

Without a clue as to what the right settings were. I am posting the current contents of my fstab file

[HTML]

# /etc/fstab: static file system information.
## Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).


## <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid           0  0

# / was on /dev/sda9 during installation
UUID=788635c5-9871-4881-a478-891931214420  /            ext4  user                          0  0

# /home was on /dev/sda11 during installation
UUID=9dd626f5-3b50-4353-8b32-80eb992aa0cc  /home        ext4  defaults                      0  0

# swap was on /dev/sda10 during installation
UUID=7884cc73-a90f-4a96-974b-79ac51b0ef18  none         swap  sw                            0  0
[/HTML]

Can somebody help me in fixing the messed up settings ?

Please provide me a working fstab file so that i can replace it with the messed up one from my system.

thanks.

---

### Post by drs305 on 2011-02-06
> **Muzafsh said:**
> 
Please provide me a working fstab file so that i can replace it with the messed up one from my system.

thanks.

Sure, we can fix it up. The easiest way for us to get the correct information is to have you run the boot info script from the LiveCD. Go to the site, read the directions, download and run the script. 

Then start a post here, press the # icon, and paste the contents of the RESULTS.txt between the code tags.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Elfy on 2011-02-06
Possibly pysdm did a backup, if it didn't it should ;)

Do 

```
ls -al /etc/fstab*
```

See what you have.

---

### Post by Muzafsh on 2011-02-07
Thanks for the response 'forestpikie' and 'drs305'


[B]@drs305

[/B]Please find the contents of results.txt below
Kindly advise me on instructions to replace my erroneous fstab with a working fstab


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for (,msdos9)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    41,992,191    41,785,344   7 HPFS/NTFS
/dev/sda3          41,996,286   312,576,704   270,580,419   f W95 Ext d (LBA)
/dev/sda5         174,144,663   197,213,939    23,069,277   7 HPFS/NTFS
/dev/sda6         197,214,003   220,283,279    23,069,277   b W95 FAT32
/dev/sda7         220,283,343   243,352,619    23,069,277   7 HPFS/NTFS
/dev/sda8         243,352,683   312,576,704    69,224,022   7 HPFS/NTFS
/dev/sda9          41,996,288    65,062,911    23,066,624  83 Linux
/dev/sda10         65,064,960    73,453,567     8,388,608  82 Linux swap / Solaris
/dev/sda11         73,455,616   174,143,487   100,687,872  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2017 MB, 2017525248 bytes
64 heads, 63 sectors/track, 977 cylinders, total 3940479 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            129     3,907,007     3,906,879   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       7884cc73-a90f-4a96-974b-79ac51b0ef18   swap                                     
/dev/sda11       9dd626f5-3b50-4353-8b32-80eb992aa0cc   ext4                                     
/dev/sda1        9AAEAD98AEAD6E07                       ntfs       System Reserved               
/dev/sda2        2274BCD874BCB041                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        5A3031133030F799                       ntfs       AIDEEN                        
/dev/sda6        1E0F-1B56                              vfat       STORAGE                       
/dev/sda7        01CA0E4402864780                       ntfs       My Storage                    
/dev/sda8        01CA0E44041488A0                       ntfs       AI My J                       
/dev/sda9        788635c5-9871-4881-a478-891931214420   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4C99-A6D3                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda9/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=788635c5-9871-4881-a478-891931214420 ro  splash  quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=788635c5-9871-4881-a478-891931214420 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=788635c5-9871-4881-a478-891931214420 ro  splash  quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=788635c5-9871-4881-a478-891931214420 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=788635c5-9871-4881-a478-891931214420 ro  splash  quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=788635c5-9871-4881-a478-891931214420 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 788635c5-9871-4881-a478-891931214420
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9aaead98aead6e07
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
# / was on /dev/sda9 during installation
UUID=788635c5-9871-4881-a478-891931214420  /            ext4  user                          0  0  
# /home was on /dev/sda11 during installation
UUID=9dd626f5-3b50-4353-8b32-80eb992aa0cc  /home        ext4  defaults                      0  0  
# swap was on /dev/sda10 during installation
UUID=7884cc73-a90f-4a96-974b-79ac51b0ef18  none         swap  sw                            0  0  

=================== sda9: Location of files loaded by Grub: ===================


  28.3GB: boot/grub/core.img
  24.3GB: boot/grub/grub.cfg
  22.9GB: boot/initrd.img-2.6.35-23-generic
  23.4GB: boot/initrd.img-2.6.35-24-generic
  23.1GB: boot/initrd.img-2.6.35-25-generic
  28.4GB: boot/vmlinuz-2.6.35-23-generic
  28.5GB: boot/vmlinuz-2.6.35-24-generic
  28.5GB: boot/vmlinuz-2.6.35-25-generic
  23.1GB: initrd.img
  23.4GB: initrd.img.old
  28.5GB: vmlinuz
  28.5GB: vmlinuz.old
```
**@forestpikie**
---------------

Please find the results of the command you have stated.

```
ubuntu@ubuntu:~/Desktop$ ls -al /etc/fstab*
-rw-r--r-- 1 root root 87 2011-02-07 13:36 /etc/fstab
```

---

### Post by drs305 on 2011-02-07
Here you are:

> # /etc/fstab: static file system information.
## Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).


## <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid           0  0

# / was on /dev/sda9 during installation
UUID=788635c5-9871-4881-a478-891931214420   /   ext4  errors=remount-ro   0 1

# /home was on /dev/sda11 during installation
UUID=9dd626f5-3b50-4353-8b32-80eb992aa0cc  /home  ext4  defaults  0  2

# swap was on /dev/sda10 during installation
UUID=7884cc73-a90f-4a96-974b-79ac51b0ef18  none   swap   0  0

I made only one change to your / line and a couple of minor tweaks. 

If you don't have a separate /home folder any longer for some reason, place a # symbol in the front of the "/home" line.

If it doesn't boot, please try to provide us with the error messages generated during boot.

Added:
If it does boot, it's possible there are errors on the / partition. One change I made was to include the option to remount / if errors were found on during boot. If it doesn't boot, it still may be due to errors, although it would be a high coincidence that the errors occurred at the same time you edited fstab.

In either case, you might consider booting the LiveCD and running one of the following two sets of commands. The first will force a normal disk check when you reboot, the second two will make sure /dev/sda9 is unmounted and accomplish a check immediately from the LiveCD. 

```

sudo mount /dev/sda9 /mnt && sudo touch /mnt/forcefsck && sudo umount /dev/sda9  # Check at next boot
*or* 
sudo umount /dev/sda9  # Make sure /dev/sda9 is not mounted. You should get a message stating the same.
sudo e2fsck -p -f -v /dev/sda9 # Check immediately

```

---

### Post by Muzafsh on 2011-02-07
Fantastic !!!

Your modified fstab did the trick :) :) :)

[B][COLOR="YellowGreen"]Firstly i would like to compliment you on this fantastic thread.

Primarily because you have started this thread way back in july 2008. Even almost 3 years down the line you have kept it active with precise and timely response especially from **you** as the thread starter/maintainer.

Its just un-imaginably helpful to noobs like us.

You are maintaining it with absolute honesty i must say.

A Big Thanks to you on behalf of the community.[/COLOR]
[/B]
PS : Though your modified fstab did restore my Ubuntu 10.10. Please let me know if you want to diagnose my system for any hidden errors. If so please provide me with the commands/steps and i'll provide you the output for the same. I just want to ensure my system has fully recovered from the PySDM act.

---

### Post by drs305 on 2011-02-07
> **Muzafsh said:**
> 
PS : Though your modified fstab did restore my Ubuntu 10.10. Please let me know if you want to diagnose my system for any hidden errors. If so please provide me with the commands/steps and i'll provide you the output for the same. I just want to ensure my system has fully recovered from the PySDM act.

You are welcome - glad it is working.

The main change we made was to add the "errors=remount-ro" option to your / partition. If this is what fixed your fstab, it may mean that the disk has errors on it. Simply running fsck or e2fsck in the manner I described in the earlier post should fix those errors.

Since you are probably in your normal Ubuntu OS, the easiest thing would be to just run this command to force an fsck check on the next boot:
```
sudo touch /forcefsck
```
As your system boots it will pause to run the check - normally from 30 seconds to several minutes, depending on the file format, partition size, etc. If it finds errors it can't fix it will tell you.  

Happy Ubuntu-ing !

---

### Post by Muzafsh on 2011-02-08
thanks,

i ran the following command
```
sudo touch /forcefsck

```

My system booted normally, is there some log where i can check for errors if any, that may need attention ? or should i assume that all's well.

Shall i remove the errors criteria you have introduced in my fstab and try booting ?

If yes kindly tell me what needs to be deleted from my fstab.

thanks,

---

### Post by drs305 on 2011-02-08
> **Muzafsh said:**
> thanks,

i ran the following command
```
sudo touch /forcefsck

```

My system booted normally, is there some log where i can check for errors if any, that may need attention ? or should i assume that all's well.

Shall i remove the errors criteria you have introduced in my fstab and try booting ?

If yes kindly tell me what needs to be deleted from my fstab.

thanks,

There is a /var/log/fsck folder. I've not found anything meaningful in mine but you could take a look at the files therein.

I would leave things as they are. If fsck ran without problems on boot then you shouldn't need to do anything unless you have further problems.

The fstab entry for / includes a periodic fsck check (I think the default is every 30 boots) so the system should take care of this automatically.

---

### Post by Muzafsh on 2011-02-08
> There is a /var/log/fsck folder.

both the log files found here carry only the following line

> (Nothing has been logged yet.)

So i think all's well, and I'll let it be.


This whole issue occurred while trying to mount my other partitions automatically on boot.
I wanted the following partitions to be mounted automatically on boot.

Can you please help me in creating the lines for the following partitions to add to fstab.
```

Device           UUID                                   TYPE       LABEL                         
/dev/sda2        2274BCD874BCB041                       ntfs                                     
/dev/sda5        5A3031133030F799                       ntfs       AIDEEN                        
/dev/sda6        1E0F-1B56                              vfat       STORAGE                       
/dev/sda7        01CA0E4402864780                       ntfs       My Storage                    
/dev/sda8        01CA0E44041488A0                       ntfs       AI My J            
```

thanks,

---

### Post by drs305 on 2011-02-08
A few of observations: 

1. Confirm the UUIDs are current and not cached:
```
sudo blkid -c /dev/null
```

2. LABELS are great, and I use them in fstab. They offer all the advantages of UUIDs, *plus* they are reader-friendly. 
I didn't use them in the first example because some of your labels have spaces. You can still use labels with spaces, but I stuck with the more standard UUID convention. Although this isn't literally true, I've come to regard labels with spaces in the name as an unnecessary invitation to problems.

3. The mount point for each of the following entries must exist. You must change each entry for "/mountpoint-X" to the actual mount point, such as "/media/myfiles" or "/mnt/myfiles". Note Edit: vfat options changed from *fmask* & *dmask* to *umask*

> 
UUID=2274BCD874BCB041 /*mountpoint-1* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
UUID=5A3031133030F799 /*mountpoint-2* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
UUID=1E0F-1B56 /*mountpoint-3* vfat auto,users,uid=1000,gid=1000,utf8,umask=027 0 0
UUID=01CA0E4402864780  /*mountpoint-4* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
UUID=01CA0E44041488A0 /*mountpoint-5* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0


Here are the entries using your LABELS:
> 
UUID=2274BCD874BCB041 /*mountpoint-1* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
LABEL=AIDEEN /*mountpoint-2* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
LABEL=STORAGE /*mountpoint-3* vfat auto,users,uid=1000,gid=1000,utf8,umask=027 0 0
LABEL=My\040Storage  /*mountpoint-4* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
LABEL=AI\040My\040J /*mountpoint-5* ntfs auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0


Once you have saved fstab with the changes, before you reboot, open a terminal and run this command to mount all fstab entries:
```
sudo mount -a
```
If there are no errors in your fstab instructions, you will get no response once the command is executed (but all the partitions will be mounted).

If you get errors, fix the problem. If you can't fix the problem, place a # comment at the start of the line until you can figure it out so it doesn't generate an error when you boot.

---

### Post by Muzafsh on 2011-02-08
thanks for taking time to create the entries.

Please note the following observations that need your attention...

1. except
> LABEL=STORAGE /mountpoint-3 vfat auto,users,uid=1000,gid=1000,utf8,dmask=027,fmask= 137 0 0

giving the following error
> mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


all other partitions are getting mounted on boot.



2. However you'll notice in the following screenshot...


[IMG]http://i410.photobucket.com/albums/pp184/muzafsh/mount.png[/IMG]



On the left side of the window you can see duplicate labels of
the mounted partitions without the mounted icon besides and when
i click on these duplicates i get the following error


[IMG]http://i410.photobucket.com/albums/pp184/muzafsh/Error1.png[/IMG]


How do i resolve this?
Also is it possible to have mountpoints with spaces in the
/media folder ?
Eg. /media/My Storage. If so how do i do it ?

3. Also in the /media folder (where i have defined my mount
points) i can see that there are a lot of junk folders with names
such as the 'sda' series and 2 more folders which when opened are
empty.
How do i keep my /media clean with only the mounted folders
showing there ?

---

### Post by drs305 on 2011-02-09
First, let's get the questions out of the way.

> 
Also is it possible to have mountpoints with spaces in the
/media folder ?
Eg. /media/My Storage. If so how do i do it ?

If you insist on spaces in the names ;-) you can do this via GUI or command line:
a. Open a file browser as root (gksu nautilus). Then File, Create Folder. You need to be root since you will probably be creating the entry in a system folder (/media or /mnt).
b. Via command line. Note the format is different than how it is written in fstab.
```
sudo mkdir /media/My\ AJ
```


> 
giving the following error
Try changing the entry to this (and of course change "mountpoint-3" to the proper designation):
> LABEL=STORAGE /mountpoint-3 vfat auto,users,uid=1000,gid=1000,utf8,umask=027 0 0 

I'll get to the viewing format in the next post when I have a bit of time.

---

### Post by drs305 on 2011-02-09
Nautilus Displays:

I'll try not to get too deep ...

In the left pane, Nautilus will display:
[LIST=1]
[*]Any LABELed  partition not listed in fstab
[*]Any LABELed partition in fstab with a mount point on /media
[*]Any /media mount point listed in fstab
[/LIST]

The duplicate listings is what I consider a bug. It's been around for a long time and there are numerous posts about it. I don't know how to solve it using your current setup.

Keeping in mind the way labels/mount points are listed, and the second paragraph, here is what I do. It is a workaround, not a solution. 
Since I have my partitions mounted on boot, I don't care about the mounted symbol in the upper left Places panel.

1. *All* my permanent drive partitions are referenced in fstab and are mounted in the /mnt folder instead of /media. This keeps them out of the top left Nautilus panel entirely. Make a backup copy of fstab, then replace /media with /mnt in each fstab listing. Save the file.

2. Create a folder under /mnt for each partition. 
In your case, this command will do it (and I've made you the owner). Be sure to replace "yourusername:" in the second command:
```
sudo mkdir /mnt/AIDEEN /mnt/AI\ My\ J /mnt/My\ Storage /mnt/STORAGE
sudo chown -R *yourusername:* /mnt/AIDEEN /mnt/AI\ My\ J /mnt/My\ Storage /mnt/STORAGE

```

3. I open Nautilus and navigate to /mnt. I drag each mount point to the lower left Nautilus panel. This creates a shortcut in that panel, and that is how I access the partitions.

4. As for all the "sdaX" entries, I would try to remove them. *First, make sure they are empty!* Close all apps and run:
```
sudo umount -a
```
Disregard the 'busy' messages.
Next open Nautilus, navigate to /media and check each sdaX entry to ensure it is empty. If it is, delete it. I don't know how they were created, and they may appear again if they are auto-generated, but I'd try to get rid of them at least once.

5. Now run "sudo mount -a". Check the contents of each partition (now mounted in /mnt) by clicking on the link in the lower left panel of Nautilus. If everything looks good, check to make sure the same folders in /media *are empty* and delete them.

There are other solutions - other ways to simlink, other file managers such as pcmanfm, etc. This is just one way and others may find it not to their liking, which is fine.

---

### Post by Muzafsh on 2011-02-09
**@drs305**

You are one committed and helpful member of this community.
People like you are assets for the Ubuntu open source community.

You promptness and preciseness in providing solutions 
**is truly unmatched !!!**

> LABEL=STORAGE /mountpoint-3 vfat auto,users,uid=1000,gid=1000,utf8,umask=027 0 0

the 'umask' attribute loaded my partition(STORAGE) that was
not mounting earlier.

and

Your workaround for removing duplicates on the left side of
the nautilus window by mounting partitions in

> /mnt

instead of

> /media

and dragging partitions to the left side to have their shortcuts
created is just fabulous.

It worked like a Charm !!!!!!!

**I am so glad i came to your thread after my PySDM debacle !!!**

**Truuuuuuuly Satisfied & Grateful**

PS : If you are maintaining any other threads on other
topics/issues commonly encountered in Ubuntu please do message
me the link to those threads. I would surely like to
subscribe/bookmark them. **You are certainly a valuable resource.**

**Khudos !!!**

---

### Post by drs305 on 2011-02-09
> **Muzafsh said:**
> If you are maintaining any other threads on other topics/issues commonly encountered in Ubuntu please do message me the link to those threads. I would urely like to subscribe/bookmark them. 

Glad you are happy with the results.

Many of my major threads are listed in my signature line and concern Grub2, which seems to generate a lot of posts. You can always see what other members have posted by clicking on their username and opting to see other posts by ...

---

### Post by Rebelli0us on 2012-01-25
I've added the options (in bold below) which give me exclusive access to my NTFS partition. Works fine.

```
UUID=B8C87616C875D2EC /media/211 ntfs-3g defaults,**uid=1000,umask=077**,locale=en_US.utf8 0 0
```

There are now 2 more "Admin" users that can't access the NTFS partition. Is there a way to remove the current permissions to only 1 user and instead give exclusive access to a group? e.g the "Admin" group. Then, instead of editing fstab I could just go to "Users and Groups" and add/remove a user from the group.

Alternatively can I enable more users in fstab by simply appending their uid in the line above? e.g. uid=1002,uid=1003..


Thanks.

---

### Post by drs305 on 2012-01-25
> **Rebelli0us said:**
> 
There are now 2 more "Admin" users that can't access the NTFS partition. Is there a way to remove the current permissions to only 1 user and instead give exclusive access to a group? e.g the "Admin" group. Then, instead of editing fstab I could just go to "Users and Groups" and add/remove a user from the group.

Although I've not done it, replacing the UID option with a GID (group ID) should do it (gid=xxx).

---

### Post by Rebelli0us on 2012-01-25
> **drs305 said:**
> Although I've not done it, replacing the UID option with a GID (group ID) should do it (gid=xxx).

Thank you. What about:

"Storage Device Manager" > "Dynamic Configurations Rules" > "New" rule > has an option "Specify owner group". Can I just type-in "Admin"?

---

### Post by drs305 on 2012-01-25
> **Rebelli0us said:**
> Thank you. What about:

"Storage Device Manager" > "Dynamic Configurations Rules" > "New" rule > has an option "Specify owner group". Can I just type-in "Admin"?

You can use the actual group name rather than the gid, I assume PySDM would import it correctly. Just verify the spelling/case with the 'groups' command. You would probably want to use "admin"

Let us know how the 'group' entry works out.

---

### Post by Rebelli0us on 2012-01-25
> **drs305 said:**
> Although I've not done it, replacing the UID option with a GID (group ID) should do it (gid=xxx).

Just to clarify, in fstab replace

uid=1000,umask=077

with 

gid=Admin,umask=077

??

---

### Post by drs305 on 2012-01-25
> **Rebelli0us said:**
> Just to clarify, in fstab replace

uid=1000,umask=077

with 

gid=Admin,umask=077

??

I believe you'd need "admin" rather than "Admin".

---

### Post by Rebelli0us on 2012-01-25
> **drs305 said:**
> You can use the actual group name rather than the gid, I assume PySDM would import it correctly. Just verify the spelling/case with the 'groups' command. You would probably want to use "admin"

Let us know how the 'group' entry works out.

Thank you.

I tried PySDM "Storage Device Manager" > "Dynamic Configurations Rules" > "New" rule > "Specify owner group". I entered "admin" and then clicked "Apply" but there was **NO** change in fstab.

---

### Post by WinRiddance on 2012-02-04
This happened to me recently, so here's a word to the wise ...
There are situations where PySDM is completely useless.

If, during restarts, you see a startup screen with a text line at the bottom that reads something like ... keys: Press I to ignore, S to skip, and so on ... you may have had Linux hijack the permissions on your external NTFS drive as a safety precaution. In that case even PySDM will not be able to help. It will look as though it works but after you apply/save the settings, followed by rebooting, you'll be right back where you were before, without read/write permission to your NTFS drive.
To my knowledge this strictly applies to drives or partitions with the NTFS (Windows) file system. I spent a week looking for a real solution, but ultimately I ended up reformatting all of my NTFS drives to Ext3 instead, to get my permissions back again. No more Windows for me, and now no more NTFS either. That's what generic USB sticks are for, when I need access to NTFS related things.
PEACE.

.

---

