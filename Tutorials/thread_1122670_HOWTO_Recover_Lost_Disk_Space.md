---
title: "HOWTO: Recover Lost Disk Space"
date: 2009-04-11
forum: Tutorials
---

### Post by drs305 on 2009-04-11
[COLOR="MAROON"]**[SIZE="4"][CENTER]*Disk Space Problems & Solutions*[/CENTER][/SIZE]**[/COLOR]
This guide was created to help users who are having issues with disk space, or lack thereof. It presents various reasons why free space may have unexpectedly disappeared or changed, and how to locate and remove the files which now may be occupying this space. 

The primary focus is on restoring space on the system partition ( **[COLOR="Blue"]/[/COLOR]** ) but the commands can easily be modified for other partitions as well. Although Linux 'thinks' of everything as a file, I will often refer to *folders*, *partitions*, and *devices* to keep things simpler for users transitioning from other operating systems.

This guide is an outgrowth of a tutorial covering residual Trash files. If you know your issue is related to Trash, please refer to [_Disk Full? - Check Your Trash Bin(s)_]("http://ubuntuforums.org/showthread.php?t=898573") for a more comprehensive treatment of that subject. 

**[COLOR="DarkGreen"][SIZE="3"]In a Rush? ... Go Directly to # [COLOR="Red"]6[/COLOR] for possible solutions or to # [COLOR="Red"]8[/COLOR] for a step-by-step summary.[/SIZE][/COLOR]**

**[COLOR="DarkRed"][SIZE="3"]A Note to Wubi Users:[/SIZE][/COLOR]** While the same things that steal disk space from a normal Ubuntu installation can occur in Wubi, and the methods below will work, it is also possible that you did not allocate enough space within Windows for the Wubi file. If you find you need to increase the size of the Wubi folder, please visit this site: [HOWTO: Resize the WUBI virtual disk]("http://ubuntuforums.org/showthread.php?t=1625371")

**[COLOR="Navy"][SIZE="3"]1. Error Messages - Why You Are Here?[/SIZE][/COLOR] **
*"There is not enough room on the disk to save ..."* or perhaps you received an error message about "insufficient disk space". Perhaps you looked at your system with a file browser or Disk Usage Analyzer and realized that you were running out of disk space. Maybe your system is reporting a partition full when you *know* it isn't. This thread presents ways to discover what is using large portions of your disk space and how to regain some free space.

**[COLOR="Navy"][SIZE="3"]2. Where Did My Free Space Go? - Common Causes [/SIZE][/COLOR]**[LIST]
[*]A partition, such as / or  /boot, is too small. (See # 6a).
[*]Backup files were mistakenly saved to the wrong location. (See # 6b)
[*]Deleted files in the trash bin are still on your system taking up disk space. (See # 6c)
[*]You unknowingly created a large file. (See # 6d)
[*]Downloads have accumulated in /var/cache/apt/archives. (See # 6e)
[*]Various log files have increased in size and/or number. (See # 6f)
[*]Your cloned partition doesn't show the new partition's correct size. (See 6g)
[*]Your NTFS partition shows the incorrect size. (See 6h)
[*]The contents of your "*lost+found*" folders have grown. (See #6i)
[*]You just need a bit more space. (See # 6j)
[LIST]
[*]This includes not being able to install a new kernel.
[/LIST]
[/LIST]

**[COLOR="Navy"][SIZE="3"]3.  An Important Note About Mounting Options, Permissions, and Deletions[/SIZE][/COLOR]**
[LIST]
[*]**Mounting**. Many of the commands and applications mentioned in this post present information only on *[COLOR="Blue"]mounted[/COLOR]* partitions. If you execute the command without first running one of the mount/unmount commands below, you will see information on only the devices that are currently mounted. 

For troubleshooting, one of the first things you have to determine is what devices (partitions, drives, etc) you want to look at. If you are having a problem with system space, you would normally want to look only at system folders and not additional devices. At best the additional mounted devices just provide extra results - at worst a mounted device might hide a problem with underlying data on the same mount point (see [COLOR="DarkRed"]du[/COLOR]).

To view only the system folders, first close all open applications and then run the following. It will attempt to unmount all partitions listed in /etc/mtab. You will get messages stating "device is busy" for any system partition or partition currently being used by the system. These messages are normal and can be ignored. 
```
[COLOR="DarkRed"]**sudo umount -a**[/COLOR]
```

To investigate other devices/partitions, you can mount all those listed in /etc/fstab with the following command. Once you have done that, you can manually mount any other devices which are not listed therein.
```
[COLOR="DarkRed"]**sudo mount -a**[/COLOR]
```
[*]**Permissions**. Remember that when running commands or applications as a *user* you will see only files you have permission to see. This may prevent you from seeing files created or stored in system folders that may be taking up the space you have lost. To ensure you can view all the files on your computer if you have 'root' privileges run the commands/applications as 'root'. For command line operations, precede the command with "[COLOR="DarkRed"]sudo [/COLOR]". For graphical applications such as *nautilus* and *baobab/Disk Usage Analyzer* start the command to launch the application with "[COLOR="DarkRed"]gksudo [/COLOR]"


[*]**Deletions**. When deleting folders/files from within a file browser such as nautilus remember that the deleted folders/files are moved to the *Trash* bin. Until you empty the trash, these files will continue to use disk space. To free up space, you can:
[LIST]
[*]In a file browser, use SHIFT-DELETE to bypass the *Trash* bin.
[*]In terminal, use the "[COLOR="DarkRed"]rm[/COLOR]" command.
[*]Empty the *Trash* bins - the user's and root's. Starting with Hardy, these are located at ~/.local/share/Trash and /root/.local/share/Trash, respectively.
[/LIST]
**Warning: SHIFT-DELETE and "[COLOR="DarkRed"]rm[/COLOR]" cannot be reversed. Make sure you are deleting the correct item(s).**
[/LIST]

**[COLOR="Navy"][SIZE="3"]4.  Checking Your Partitions via Terminal (CLI)[/SIZE][/COLOR] **

To open a terminal, either use the Main Menu (Applications, Accessories, Terminal) or use ALT-F2, enter the command(s) in the top input area, and tick/enable "Run in terminal" to open a terminal window, .

A brief note on [COLOR="DarkRed"]df[/COLOR] and [COLOR="DarkRed"]du[/COLOR]: It is beyond the scope of this guide to go into detail about how [COLOR="DarkRed"]df[/COLOR] and [COLOR="DarkRed"]du[/COLOR] report disk usage. They look at disk space differently and the results will not be the same. Generally the results of [COLOR="DarkRed"]df[/COLOR] will show more disk usage than those of [COLOR="DarkRed"]du[/COLOR] since it considers block size rather than just the specific file size. Additionally, [COLOR="DarkRed"]df's[/COLOR] results will include information about *open* files - those which are not currently written to disk but do exist in memory.

Terminal command results may include "/proc" entries. These are virtual file entries, are not the cause of lost disk space, and should be left alone.

[LIST]
[*][SIZE="3"]**[COLOR="DarkRed"] df[/COLOR]** - Report file system disk space usage   (Check your /dev/sdXX's)
[/SIZE]
Since the "[COLOR="DarkRed"]df[/COLOR]" command provides details on *[COLOR="Blue"]mounted[/COLOR]* partitions you should run the "[COLOR="DarkRed"]df[/COLOR]" command after you have decided which devices you wish to investigate and have run the appropriate mount/umount command. If you first run the "[COLOR="DarkRed"]sudo umount -a[/COLOR]" command the "[COLOR="DarkRed"]df[/COLOR]" results will usually report only your system partition information if all other applications are closed. Review Section 3 for mounting/unmounting options. 

Note that *deleted* files in Trash are included in used space until completely removed from the system.

```
**[COLOR="DarkRed"][SIZE="4"]df -Th[/SIZE][/COLOR]**
``` 

Optionally: [COLOR="DarkRed"]**df -h** *[COLOR="Blue"]or[/COLOR]* **df -Th | sort** *[COLOR="Blue"]or[/COLOR]*  **df -Th | grep -v "fs" | sort**[/COLOR]   
 
Here is a sample of the "[COLOR="DarkRed"]df -Th | grep -v "fs" | sort[/COLOR]" command:
```

/dev/sda1     ext3     15G  7.7G  6.3G  55% /
/dev/sda2     ext3     15G  2.1G   12G  15% /media/data
/dev/sdb2     ext3     48G   35G   11G  76% /media/backup
Filesystem    Type    Size  Used Avail Use% Mounted on

```
Note: "[COLOR="DarkRed"]sort[/COLOR]" will order the partition results. The "[COLOR="DarkRed"]T[/COLOR]" switch shows the file type - you can omit it if desired. The "[COLOR="DarkRed"]h[/COLOR]" switch lists file sizes in "human" terms. Mounted NTFS partitions will be displayed as type: "fuseblk".
 

[*][SIZE="3"]**[COLOR="DarkRed"] du[/COLOR]** - Estimate file space usage   (Check your folders)[/SIZE]
This command will show you how much space is being used by the mounted file systems on a given folder. One disadvantage of *du* is that it reports information only on *mounted* files. Additionally, if a device is mounted to a folder which already contains data, the underlying data size will not be included in the results. This means that if /media/data contains 40GB of data, but a 20GB partition is then mounted to /media/data, the results will show only the 20GB of the last-mounted device.

The "[COLOR="DarkRed"]--max-depth[/COLOR]" switch allows you to set how many sub-levels you wish to view. Once you have run the command starting at the top level (**[COLOR="Blue"] /[/COLOR]** ) you can then investigate specific folders by replacing **[COLOR="Blue"]/[/COLOR]** with another starting point (for example, [COLOR="Blue"]/var/log[/COLOR]). This command reads the the disk contents when executed and thus will take a while to complete if the entire disk is to be searched. Using "[COLOR="DarkRed"]grep[/COLOR]" can help display only folders meeting specific criteria. **Use "[COLOR="DarkRed"]sudo[/COLOR]" to gain access to system folders. For best results, umount any non-system partitions first.**

```
[B][COLOR="DarkRed"][B][SIZE="4"]sudo du -h --max-depth=1 /
sudo find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h  # Subfolders in current folder, sorted by size
[/SIZE][/B][/COLOR][/B] 
```

Optionally: [COLOR="DarkRed"]**sudo du -h --max-depth=1 / | grep '[0-9]G\>'**[/COLOR] (This combination reduces returns to folders 1GB or larger)

Folder usage is recursive - that means that the command will report the total usage of the folder *and* its sub-folders. Used with the right switches and run as root, it is a good tool to quickly locate files/folders which use large amounts of disk space. Once the large folders are located, investigating them with other commands or a file browser probably will provide the best results for a new user. Remember that the "[COLOR="DarkRed"]du[/COLOR]" command reports information on *[COLOR="DarkRed"]mounted[/COLOR]* partitions. Refer to Section 3 for mounting/unmounting options.

Here is a sample of the [COLOR="DarkRed"]sudo du / -h --max-depth=1 | grep '[0-9]G\>'[/COLOR] command, which searches for folder/subfolders which use at least 1GB of space:
```

du: cannot access `/proc/6793/fdinfo/3': No such file or directory
1.8G	/media
2.8G	/usr
3.1G	/home
8.9G	/
```
Notes: "[COLOR="DarkRed"]--max-depth[/COLOR]" limits the results to one level but includes the total disk usage of the folder and all subfolders. Once you identify a specific folder to investigate, you can substitute its address for / (e.g. [COLOR="Blue"]/usr[/COLOR] ) and/or increase the "*[COLOR="DarkRed"]--max-depth=1[/COLOR]* to a larger number.


[*][SIZE="3"]**[COLOR="DarkRed"]find**[/COLOR]  (Find a file or folder)[/SIZE]  
The [COLOR="DarkRed"]find[/COLOR] command, used with the appropriate options, is an excellent tool to locate large files. 
```

[COLOR="DarkRed"]**sudo find / -name '*' -size +1G**[/COLOR]
[COLOR="Blue"]*or*[/COLOR]
[COLOR="DarkRed"]**sudo find / -name '*' -size +500M**[/COLOR]

```
In the above examples, [COLOR="Blue"]+1G[/COLOR] searches for files larger than 1GB. [COLOR="Blue"]+500M[/COLOR] looks for files larger than 500MB. You can adjust the sizes to suit your needs. An initial Ubuntu installation will not normally have files larger than 500MB on the system partition. 

Starting with **[COLOR="Blue"]/[/COLOR]** will help ensure a thorough search of your entire system. You can specify a different starting point to speed up the search if you know which folder you want to search. Example: [COLOR="DarkRed"]sudo find /var/log -name '*' -size +1G[/COLOR] 

Strictly speaking, you don't even need to include the "[COLOR="DarkRed"]-name '*'[/COLOR]" option. It is included to show the format should you wish to replace the universal search with a specific file name ( example: [COLOR="DarkRed"]-name 'sbackup.tar.gz'[/COLOR] )

The difference between this command and the "[COLOR="DarkRed"]du[/COLOR]" command discussed previously is that this command will search only for individual files and not for folders. This would be a good choice if you were searching for a backup file you think may have ended up in the wrong place.
[/LIST]
 
**[COLOR="Navy"][SIZE="3"]5.  Checking Your Partitions Graphically (GUI)[/SIZE][/COLOR]**
[LIST]
[*]**[COLOR="DarkRed"][SIZE="3"]Gnome-Device-Manager[/SIZE][/COLOR]** 
System > Administration > System Monitor: File Systems tab. (In terminal: [COLOR="DarkRed"]gnome-system-manager[/COLOR] or preferably [COLOR="DarkRed"]gksudo gnome-system-manager[/COLOR]) 

As with the "[COLOR="DarkRed"]df[/COLOR]" command, the information presented includes only currently [COLOR="Blue"]mounted[/COLOR] devices. Review Section 3 for more information on mounting/unmounting options. Trash is considered *used* space.

This is the information displayed in the File Systems tab. System Monitor will, of course, present it graphically.
```

Device      Dir     Type   Total     Free      Available   Used     %
/dev/sda2   /home   ext3   33.1GiB   31.1GiB   29.4GiB     2.0GiB   6%

```
The "System" tab lists the available disk space on the system ( **[COLOR="Blue"]/[/COLOR]** ) partition.


[*]**[COLOR="DarkRed"][SIZE="3"]Disk Usage Analyzer / baobab[/SIZE][/COLOR]** 
Applications > Accessories > Disk Usage Analyzer. (In terminal: [COLOR="DarkRed"]baobab[/COLOR] or preferably [COLOR="DarkRed"]gksudo baobab[/COLOR] )

Disk Usage Analyzer reports information only on *[COLOR="Blue"]mounted[/COLOR]* devices. Refer to Section 3 for more information on mounting/unmounting options
.
While DUA provides valuable information, it often brings up questions about its use. Here are some things to keep in mind:
[LIST]
[*] Once a scan is complete, the top entry, whether it is the system or a single folder, will *always* show 100%. The sub-folder percentages add up to 100%. 100% does not necessarily mean there is no space left on the partition. 
[*]"Total file system capacity" includes the space on all mounted devices. If you have an external drive mounted, it's contents are included in the totals.
[*]"[COLOR="Blue"]Scan Home[/COLOR]" scans the user's home folder, or root's if baobab is opened with "gksudo". "[COLOR="Blue"]Scan FileSystem[/COLOR]" scans the system whether or not "gksudo" is used. *If DUA is opened without "[COLOR="DarkRed"]gksudo baobab[/COLOR]" not all folders/files will be visible.*
[*]In the top section below the menus, DUA will list the "Total file system capacity". This total is the sum of all reported devices. If DUA sees a **[COLOR="Blue"]/[/COLOR]** partition of 15GB, a data partition of 30GB, and an external drive mounted on /media/backup of 30GB, it will report a total of 75GB. The available space reported is the *total* space available, even if one partition is completely full. This value is the total of partitions selected in "Preferences". You can select or deselect a partition/device by unticking it in the Edit > Preferences section.
[*]The 'Size' column entries reflect actual disk space usage (allocated space), not the apparent folder size. You can change this option via the View menu.
[*]If the disk usage is approximately double the size you expected, *baobad* may be including the .gvfs (a virtual file system). You may be able to de-select it via the Edit, Preferences menu.
[*]Running DUA as root may show different results in the folders section. The reason is that opening DUA as a normal user through the Main Menu will not allow you to view certain folders, such as root's deleted Trash. For the most accurate results, opening DUA with "*[COLOR="DarkRed"]gksudo baobab[/COLOR]* will provide the most accurate assessment of disk usage.
[*]To narrow the search, you can expand a folder to see what amount of disk space each of the sub-folders is *using*.
[/LIST]


[*]**[COLOR="DarkRed"][SIZE="3"]Nautilus[/SIZE][/COLOR]** 
Places > Home Folder. (In terminal: [COLOR="DarkRed"]nautilus[/COLOR] or preferably [COLOR="DarkRed"]gksudo nautilus[/COLOR] )

The familiar file browser is good for reviewing folder contents and deleting specific folders/files. 

[LIST]
[*]Nautilus will show mount points (although not the contents of unmounted devices) even when a device is not mounted on the mount point. [*]Unless nautilus is opened with administrative privileges ( [COLOR="DarkRed"]gksudo nautilus[/COLOR] ) certain folders/files such a root's Trash will not be visible. The folder may show "Empty" even though sub-folders or files exist. For *viewing* the contents of your system, I recommend running nautilus with root privileges ("[COLOR="DarkRed"]gksudo nautilus[/COLOR]").
[*]Right click a folder and select "Properties" to display the size (for files) and free space remaining on the parent partition.
[/LIST]


[*]**[COLOR="DarkRed"][SIZE="3"]Gparted[/SIZE][/COLOR]** 
System > Administration > Partition Editor. (In terminal: [COLOR="DarkRed"]gksudo gparted[/COLOR]) 

For checking total disk usage on a given partition, [COLOR="DarkRed"]gparted[/COLOR] is a simple way of seeing how much of a partition the system thinks is used.
[/LIST]

**[COLOR="Navy"][SIZE="3"]6. PROBLEMS & SOLUTIONS[/SIZE][/COLOR] **
[LIST]

[*]**[COLOR="Red"][SIZE="3"]a.  Partition Is Too Small[/SIZE][/COLOR]** 

**How to Find It**:
If you plan on going throught the list from start to finish a logical starting point is the actual size of your partition. A quick review of the [_Ubuntu System Requirements_]("https://help.ubuntu.com/community/Installation/SystemRequirements") shows that for a standard Ubuntu desktop installation the **bare [COLOR="DarkRed"]minimum[/COLOR]** is 4GB and the **recommended [COLOR="DarkRed"]minimum[/COLOR]** is 8GB. These are recommended *minimums*. Of course, you can get by with less or need much more, depending on how many apps you install. Note: If you have a separate /boot partition, the minimum size depends on how many kernels you have installed, but users who created a separate /boot partition of 50MB often run out of room!

[COLOR="DarkRed"]**Backup any important files before performing any partitioning operations. If the operations involve NTFS partitions, defragment them at least once as well.**[/COLOR]

**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:


[LIST]
[*]**Take Space from Another Partition**. If you drive has another partition with extra space, reduce the size of one or more of them and expand your / partition (or another running out of space). To resize any system partition, the / partition (and perhaps /swap) must not be in use/mounted). Repartitioning in Ubuntu is normally accomplished with an application called "[COLOR="DarkRed"]gparted[/COLOR]". (System > Administration > Partition Editor). You can run [COLOR="DarkRed"]gparted[/COLOR] from the LiveCD. You can also use other CD/DVD/USBs which contain [COLOR="DarkRed"]gparted[/COLOR], such as the [_GParted Live CD_]("http://gparted.sourceforge.net/livecd.php") or a [_SystemRescueCD_]("http://www.sysresccd.org/Main_Page"). 
It is beyond the scope of this guide to present details of how to use [COLOR="DarkRed"]gparted[/COLOR], however [_this guide_]("http://www.howtoforge.com/partitioning_with_gparted") and [_this one_]("http://gparted.sourceforge.net/larry/resize/resizing.htm") can help.


[*]**Move [COLOR="Blue"]/home[/COLOR]**. Move parts of your system, such as [COLOR="Blue"]/home[/COLOR], to another location. Here is a link on how to move your /home folder:
[_Create a separate home partition in Ubuntu_]("http://www.psychocats.net/ubuntu/separatehome")


[*]**Move data files to another location.** Data files, music collections, video files, etc. can take up a lot of space. Creating a separate data partition on the same or another drive can provide more space for critical system files.


[*]**Kernel installation failure**. Some users created very small [COLOR="Blue"]/boot[/COLOR] partitions. If older kernels are not removed the partition may become full and this or a similar message may result:
> gzip: stdout: No space left on device  update-initramfs: failed for /boot/initrd.img
If the user has a separate /boot partition and/or received the previous warning, check the available space and the kernel in use:
```
[COLOR="DarkRed"][B]df -Th | grep 'boot'
uname -r[/B][/COLOR]
```
If you are out of space, the easiest option is to remove older kernels via [COLOR="DarkRed"]synaptic[/COLOR]. Open synaptic, search for "[COLOR="Blue"]linux-image[/COLOR]". Synaptic will display all kernels, current and former. You can safely remove one or more older kernels although many experienced users keep at least one older kernel. You can also remove the same kernel's "linux-headers-..." Ubuntu will not allow you to remove the current kernel while it is in use. 


[*]**Try a *lighter* version of Ubuntu.** If you just have a small hard drive or don't have the space to dedicate to a normal Ubuntu installation, you can try Xubuntu, an official Ubuntu derivative which uses less resources. The minimum space required is only 1.5GB, with the **recommended [COLOR="DarkRed"]minimum[/COLOR]** minimum is 6GB. 

[/LIST]


[*]**[COLOR="Red"][SIZE="3"]b.  Backups Gone Wrong![/SIZE][/COLOR]**
On of the most common causes of disappearing disk space is a backup saved to the wrong location. Besides just improperly designating the backup location, this can also be the result of a file being saved to a mount point on which no device, such as an internal or external backup drive, is mounted.

Example: A script calls for [COLOR="DarkRed"]Simple Backup (sbackup)[/COLOR] to backup a partition and automatically save the result to an external drive mounted on /media/backup. At the given time, the device is neither turned on nor mounted. Since the mount point exists, the backup file is created and saved in /media/backup, using up space on the system partition instead of on the planned external drive. 

**How to Find It**: 
[LIST]
[*]For problems with your system partition, unmount all but your system folders using the "[COLOR="DarkRed"]sudo umount -a[/COLOR]" command discussed in Section 3. 
[*]Run the following command detailed in Section 4. The option searches for ***files*** larger than 1GB. Disregard findings which include "/proc/".
```
[COLOR="DarkRed"]**sudo find / -name '*' -size +1G**[/COLOR]
``` [*]Any file found larger than 1GB is a likely suspect for further investigation, especially any file found on one of the user's mount points. Mount points will normally be empty unless a device is mounted to it.
[*]If the backup contains many smaller folders, such as a music collection, rather than look for one large file the user may wish to look at the combined folder size. In this case, run the following command detailed in Section 4. The command will look for ***folders*** using more than 1GB of space if the "grep" option is included. 
```
[COLOR="DarkRed"]**sudo du -h --max-depth=1 / **| grep '[0-9]G\>'[/COLOR]
``` 
[*]Once large folders are located, you can refine the search by identifying a specific folder as the starting point and/or increase the "[COLOR="DarkRed"]maxdepth[/COLOR]" level. The folders [COLOR="Blue"]/usr, /root[/COLOR], and [COLOR="Blue"]/home[/COLOR] will normally be included in the results. If all your mount points are in the /media folder, your search could might look like "[COLOR="DarkRed"]sudo du -h --max-depth=2 /media[/COLOR]".
[/LIST]


**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:

[LIST]
[*]Once you have found the file, either move it to a location on a different partition or delete it. If you delete it, you must use SHIFT-DEL in a file browser, the "rm" command via terminal, or empty your Trash (or root's for root-owned Trash) before the space is actually recovered and made available for use. Simply highlighting the item and hitting the DELETE key will move it to Trash, where it will continue to take up space. **Warning: These delete methods cannot be reversed! Make sure you are deleting the correct item.**

[*]If the problem was the result of an automatic backup, amend the script or take steps to ensure the backup device is mounted prior to executing the backup script.

[LIST]
*luisjeronimo* offered this tip: To help prevent this when using sbackup, the user can select the "Abort backup if destination directory does not exist" in the "Destination" tab during setup. 
[/LIST]
[/LIST]


[*]**[COLOR="Red"][SIZE="3"]c.  Trash Folders Not Empty[/SIZE][/COLOR]**
When a file or folder is deleted via a file browser in most cases it is not removed from the system. Instead it is placed in *Trash*. Until *Trash* is emptied, these files are recoverable and continue to take up space on the partition. There are several places on the system that deleted files are stored. It varies by which version of Ubuntu is running, the origin of the deleted folders/files, and who deleted them.

Example: A user downloads a collection of large .iso files or installation packages. Deciding not to use the files, the user deletes them using administrative privileges (as root). The user's  *Trash* shows empty, the user can't find the files with his/her browser, but the free space isn't restored. In a different scenario, another user on the same machine deletes files but never empties  *Trash*.

**How to Find It**: 
[LIST]
[*]Run the following command to locate all  *Trash* folders in the system. This will find the  *Trash* folders of all users as well as root. The second part of the command will display the size of the located folders.
```
[COLOR="DarkRed"]**sudo find / -type d -name '*Trash*' **| sudo xargs du -h | sort[/COLOR]
```
[/LIST]
**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:

[LIST]
[*]Items in *Trash* must be deleted in a special manner - otherwise they will be moved to the ...Trash! 
[*]Open a file browser with administrative privileges ( "[COLOR="DarkRed"]gksudo nautilus[/COLOR]" ). Navigate to the Trash folder, highlight it and press SHIFT-DELETE. Using this key combination ensures the Trash folder is permanently deleted, The *Trash* folder contains two sub-folders, "info" and "files". Deleting the parent *Trash* folder will delete both these folders. All three will be restored the next time something is deleted. **Warning: These delete methods cannot be reversed! Make sure you are deleting the correct item.**
[/LIST]

For a detailed tutorial on the Ubuntu *Trash* system, please go to: [_Disk Full? - Check Your Trash Bin(s)_]("http://ubuntuforums.org/showthread.php?t=898573")


[*]**[COLOR="Red"][SIZE="3"]d.  Unexpectedly Large File[/SIZE][/COLOR]**
A single 'rogue' file may be consuming large amounts of space. Use the following command to locate abnormally large files.

**How to Find It**:
As mentioned in Section 4, you can use the "[COLOR="DarkRed"]find[/COLOR]" command to search for large files. If you completed # 6a. you have already run this command.
```
[COLOR="DarkRed"]**sudo find -size +1G /**[/COLOR]
```

**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:
Decide what the files are, if they are in the proper location, and whether or not you wish to retain them. If you delete a large file, either bypass the Trash bin with the "rm" command, SHIFT-DEL in nautilus, or empty the appropriate Trash bin after deleting it.
 

[*]**[COLOR="Red"][SIZE="3"]e.  Too Many Collected Packages[/SIZE][/COLOR]**
Packages (.deb files) downloaded for installation by a user via the system (apt, synaptic, dpkg) are stored in [COLOR="Blue"]/var/cache/apt/archives[/COLOR]. Over time, this folder can become quite large. Under normal circumstances it is not necessary to keep packages locally;  they can be retrieved from a server if re-installation is desired. 

**How to Find It**:
To check the amount of space being used for package storage, run:
```
[COLOR="DarkRed"]**du -h /var/cache/apt/**[/COLOR]
```

**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:

There are several system commands you can use to reduce or eliminate the number of locally stored packages.
[LIST]
[*]To remove all the packages from [COLOR="Blue"]/var/cache/apt/archives[/COLOR] and [COLOR="Blue"]/var/cache/apt/archives/partial[/COLOR] folders: 
```
**[COLOR="DarkRed"][B][SIZE="3"]sudo apt-get clean[/SIZE]**[/COLOR][/B]
```
[*]To remove all expired packages from [COLOR="Blue"]/var/cache/apt/archives[/COLOR] and [COLOR="Blue"]/var/cache/apt/archives/partial[/COLOR] that are no longer available for download: 
```
**[COLOR="DarkRed"][B][SIZE="3"]sudo apt-get autoclean[/SIZE]**[/COLOR][/B]
```
"Not available for download" does *not* mean you should save them - normally you don't.

[*]To remove packages that were installed to satisfy dependencies for other applications but which are no longer needed:

```
**[COLOR="DarkRed"][B][SIZE="3"]sudo apt-get autoremove[/SIZE]**[/COLOR][/B] 
```
There is an application called [_APTonCD_]("http://aptoncd.sourceforge.net/") that can save these packages to a cd/dvd if you want to preserve your .deb files prior to removing them.
[/LIST]


[*]**[COLOR="Red"][SIZE="3"]f.  Check Your Logs[/SIZE][/COLOR]** 

Log files are usually stored in [COLOR="Blue"]/var/log[/COLOR] and its subfolders. An excessive number of small log files or large individual logs can eat up disk space. 

**How to Find It**:
You can run the following to see the size of each [COLOR="Blue"]/var/log/[/COLOR] subfolder:
```
[COLOR="DarkRed"]**sudo du -h /var/log**[/COLOR]
```

**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:

[LIST]
[*]Determine which process is generating the log files and try to change its behavior.
[*]Move or delete unnecessary log files, especially older files with more current entries. Archived *.gz log files are safe to delete.
[*]If you find a particularly large log file and you don't want to delete it, you can remove its contents while keeping the file structure intact with the following command. Change the *[COLOR="DarkGreen"]filename[/COLOR]* to the name of the actual file:
```
**[COLOR="DarkRed"][B][SIZE="3"]sudo cp /dev/null /var/log/*[COLOR="DarkGreen"]log_filename.log[/COLOR]*[/SIZE]**[/COLOR][/B]
```
[*]If you find a large log file, inspect the contents to find out what is generating the messages. Correcting the underlying problem which generated the messages will prevent the log file issue from reoccurring.
[/LIST]


[*]**[COLOR="Red"][SIZE="3"]g.  *Cloned Partitions* Folders[/SIZE][/COLOR]** 
When partitions are cloned to a partition of a different size (such as restoring a Partimage file to a larger partition), the partition table may need to be updated.

**How to Find It**:
The size of a partition after cloning may reflect the original cloned partition size rather than the size of the partition into which it was restored. This is discussed in the Partimage user's manual. Gparted may show the entire partition as used even when you know it isn't. 


**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:
***Note: The following procedure is for [COLOR="DarkRed"]ext2 and ext3[/COLOR] formatted partitions only*** Change "sd[COLOR="DarkRed"]XX[/COLOR]" to the correct device designation (example: sd[COLOR="DarkRed"]b3[/COLOR])
```

sudo umount /dev/sd[COLOR="DarkRed"]XX[/COLOR]        # unmount the new partition  Example: sudo umount /dev/sdb3
sudo e2fsck /dev/sd[COLOR="DarkRed"]XX[/COLOR]        # Optionally, perform a check of the partition
sudo resize2fs -p /dev/sd[COLOR="DarkRed"]XX[/COLOR]  # redraw the partition table to reflect the correct partition size
df -h                        # Check the results

```



[*]**[COLOR="Red"][SIZE="3"]h.  *NTFS* Partition Is Not Correctly Sized[/SIZE][/COLOR]** 
No matter what the cause, it is possible an NTFS partition table fails to indicate the correct size of the partition.

**How to Find It**:
The size of a partition isn't what it should be. You can check the disk size by running "df -Th /dev/sdXX". The command will indicate the file type (NTFS), size in GB, used/remaining space and percentage free.  

**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:
***Note:*** You will be warned in the final stages of the operation to backup data and ensure a reliable power source. The warning may appear a bit intimidating but merely reflects precautions which should be taken any time a partition table is altered.
Replace /dev/sd[COLOR="DarkRed"]XX[/COLOR] with the correct partition designation.
Example: Replace /dev/sd[COLOR="DarkRed"]XX[/COLOR] with /dev/sd[COLOR="DarkRed"]a1[/COLOR] if the device is /dev/sda1
When you remount the NTFS partition after resizing make sure the mount point exists.  Example: /mnt/windows
```

sudo apt-get update 
sudo apt-get install ntfsprogs  # ntfsprogs is included in the '*main*' repository.
sudo umount /dev/sd[COLOR="DarkRed"]XX[/COLOR]
sudo ntfsresize /dev/sd[COLOR="DarkRed"]XX[/COLOR]
sudo mount /dev/sd/[COLOR="DarkRed"]XX[/COLOR] /path/mount_ point  (If listed in fstab, 'sudo mount -a' will mount it.)
df -Th    # Check the results

```



[*]**[COLOR="Red"][SIZE="3"]i.  *lost+found* Folders[/SIZE][/COLOR]** 
Each ext2/3 partition will contain a 'lost+found' folder. This folder contains corrupted files discovered by the system during an fsck check. 

**How to Find It**:
You can run the following to locate each [COLOR="Blue"]lost+found[/COLOR] folder and, optionally, see the size of each folder:
```
[COLOR="DarkRed"]**sudo find / -name "lost+found"** | sudo xargs du -h[/COLOR]
```

**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:

[LIST]
[*]Open a file browser with administrative powers ( "[COLOR="DarkRed"]gksudo nautilus[/COLOR]" ) and inspect the contents of any large "lost+found" folder. If there is nothing recoverable, you may delete the folder. This folder will be recreated after the next fsck check. 

If you delete it, you must use SHIFT-DEL in a file browser, the "rm" command via terminal, or empty your Trash (or root's for root-owned folders) before the space is actually recovered and made available for use. Simply highlighting the item and hitting the DELETE key will move it to Trash, where it will continue to take up space. **Warning: These delete methods cannot be reversed! Make sure you are deleting the correct item.**
[/LIST]


[*]**[COLOR="Red"][SIZE="3"]j.  Gain Just a Bit of Space[/SIZE][/COLOR]** 
You can gain a bit of space by following these steps. Don't expect large free space gains.

**[COLOR="DarkGreen"]How to Fix It[/COLOR]**:

[LIST]
[*]**[COLOR="DarkRed"]Computer Janitor[/COLOR]**. Recent versions of Ubuntu come with an app which can locate unnecessary libraries and other files. Access it via System, Administration, Computer Janitor.  There is another app located in Synaptic called "cruft" that can also locate accumulated 'cruft' - stuff that doesn't need to be on your system. 
[*]**[COLOR="DarkRed"]tune2fs[/COLOR]**. Reduce the space reserved for system use. By default, Ubuntu reserves 5% of linux partitions for use by the operating system. Some commands and applications do not accurately reflect reserved system space ([COLOR="DarkRed"]gparted/baobab[/COLOR]). [COLOR="DarkRed"]Nautilus and the "df"[/COLOR] command accurately display available *usable* space by accounting for reserved system space. 

The amount of partition space reserved for this can be altered with [COLOR="DarkRed"]tune2fs[/COLOR]. Replace "**[COLOR="Red"]X[/COLOR]**" with the percentage of disk space you wish to reserve and "**[COLOR="Red"]XX[/COLOR]**" with the device designation.
```
[COLOR="DarkRed"]**sudo tune2fs -m [B][COLOR="Red"]X[/COLOR]** /dev/sd[COLOR="Red"]XX[/COLOR][/COLOR][/B]

```Example: [COLOR="DarkRed"]sudo tune2fs -m **4** /dev/sd**a1**[/COLOR]
Note: There is a reason Ubuntu reserves this space. Carefully consider if you want to change this setting before doing so.


[*]**[COLOR="DarkRed"]gtkorphan[/COLOR]**. Install "[COLOR="DarkRed"]deborphan[/COLOR]", a command-line application, and "[COLOR="DarkRed"]gtkorphan[/COLOR]", a gui-based application. These programs help find and eliminate orphaned libraries which are no longer needed.
```
**[COLOR="DarkRed"]sudo apt-get install deborphan gtkorphan[/COLOR]**
```
[LIST]
[*]"[COLOR="DarkRed"]deborphan[/COLOR]" can identify orphaned packages.To run it: 
```
**[COLOR="DarkRed"]sudo deborphan[/COLOR]**
```
[*] To run "[COLOR="DarkRed"]gtkorphan[/COLOR]", System > Administration > "Remove orphaned packages". [COLOR="DarkRed"]GtkOrphan[/COLOR] will allow the user to identify and delete selected orphan libraries.
[/LIST]
[*]**[COLOR="DarkRed"]localepurge**[/COLOR]. A number of language packages may be installed on the system.  "[COLOR="DarkRed"]localepurge[/COLOR]" can be installed and run to remove and prevent future installation of extra language packages that the user  does not use. **Read the *man* page for warnings about it's use.** 
[/LIST]
[/LIST]

**[COLOR="Navy"][SIZE="3"]7.  Other Issues[/SIZE][/COLOR]**
When investigating this topic, run everything as root ( [COLOR="DarkRed"]sudo / gksudo[/COLOR]) to ensure as much consistency as possible.
[LIST]
[*]**New Hard Drives**. New hard drives will not contain the space shown on the packaging. For example, a 1TB drive normally starts with about 931GB of space. Additionally, linux file systems by default reserve 5% of the space for system use.

[*]**Reporting Inconsistencies**. Unfortunately disk usage is not uniformly reported throughout the range of applications. Total usable disk space is generally consistent. Space reserved for system use (and thus unavailable) is accounted for with the "[COLOR="DarkRed"]df[/COLOR]" command and in [COLOR="DarkRed"]nautilus[/COLOR] but is shown as available in [COLOR="DarkRed"]GParted[/COLOR] and [COLOR="DarkRed"]baobab/Disk Usage Analyzer[/COLOR]. 
[/LIST]


**[COLOR="Navy"][SIZE="3"]8.  The Five Minute Guide[/SIZE][/COLOR]**
Let's just get on with it!
[LIST]
[*]Determine what you need mounted. 
[*]Run everything with administrative powers ([COLOR="DarkRed"]gksudo nautilus[/COLOR], etc). 
[*]When you discover the problem, refer to the appropriate section above for tips on how to fix it.
[*]When you are done deleting items make sure all Trash is removed from the user's and root's Trash folders. 
[*]If you get stuck, read the guide! *Good luck*.
> 
**For system partition ( / ) troubles:**
[COLOR="DarkRed"]**sudo umount -a**[/COLOR]                      # keep only / mounted, disregard "busy" messages (#3)

**To inspect all partitions:**
[COLOR="DarkRed"]**sudo mount -a**[/COLOR]                       # mount all devices in fstab, then manually mount the rest (#3)

**Confirm partition/disk usage (partition size, used, remaining):**
[COLOR="DarkRed"]**df -Th | grep -v "fs" | sort **[/COLOR]       # confirm partition usage (#4)

**Search generally for large folders/files:**
[COLOR="DarkRed"]**sudo du -h --max-depth=1 / | grep '[0-9]G\>'** [/COLOR] # find large folders > 1GB (#4)
[COLOR="DarkRed"]**sudo find / -name '*' -size +500M**[/COLOR]             # find large files  > 500MB (#4/6c)

**Target Specific Partitions/Folders:**
[COLOR="DarkRed"]**sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort**[/COLOR]    # check for Trash (#6b)
[COLOR="DarkRed"]**sudo du -h /var/cache/apt/**[/COLOR]     # check for a large cache of .deb files (#6d)
[COLOR="DarkRed"]**sudo du -h /var/log**[/COLOR]            # check for large log folders           

**Ensure your Trash bins aren't 'full':**
[COLOR="DarkRed"]**sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort**[/COLOR]    # check for Trash (#6b)

**Recheck your disk space:**
[COLOR="DarkRed"]**df -Th | grep -v "fs" | sort **[/COLOR][/LIST]

---

### Post by zl1ogx on 2010-10-13
Thanks for a good guide for clearing out some unused or un-needed files to free up some space.  Good for us who are using old netbooks with solid state hard drives and have limited space.

Ian

---

### Post by drs305 on 2010-10-13
> **zl1ogx said:**
> Thanks for a good guide for clearing out some unused or un-needed files to free up some space.  Good for us who are using old netbooks with solid state hard drives and have limited space.

Ian

Your welcome. 

Now I'm going to have to figure out how every post from the original posting date from April 2009 until your's has disappeared. 

Now *that's* some kind of clean up!  ;-)

---

### Post by john newbuntu on 2010-10-14
Thanks for the great article drs.

One point to note - There are some instances when cron fails to run or /var/log/syslog or some other log fills up.  It is good for the user to open up these logfiles (system->admin->logfileviewer) to view these files and see what the errors are. Most times it is the same error message repeated over and over indicating a system problem.  Example ufw log mode set to a medium on high logging.  If cron fails to run, logrotate fails too causing massive logfile dumps.  Moving/deleting these does create the space but does not solve the underlying problem.
I would also recommend the use of bleachbit that does some cleaning automatically.

---

### Post by drs305 on 2010-10-14
@ john newbuntu,

Good tip! I've included it in the log file section. Thanks.

---

### Post by aisha123 on 2010-10-14
This is a very useful guide. Thank you for sharing. This will be very handy. :)

---

### Post by typos1 on 2011-01-17
I ve got discc space problems and I suspect its to do with my lost+found folders, but for some reason terminal will not let me do anything-yesterday it said I was typing the wrong password (I wasnt) today the cursor simply moves down the terminal after I enter the password or the password is displayed (usually it isnt) but nothing happens in the terminal.

Anyone got any ideas why it wont let me sign in as root?

Very strange terminal will run some commands but not others, some folders are locked and when I right click most options are greyed out, so I cant for instance delete log files in /va/log and there is apparently 46Gb worth of files in /var/log which seems like it might be the root of my problem. I also now dont get a "delete" option when I right click, I only get move to rubbish bin.

---

### Post by typos1 on 2011-01-18
Anyone?

---

### Post by Trespasser on 2011-01-18
I want to thank you as well for this extensive guide. Obviously it took you a long time to prepare, but, from the looks of it, time well spent. Thank you again. Your efforts are appreciated.

Later...

---

### Post by radiobert on 2011-02-25
Thanks for preparing this guide. Here, I have a hard-disk space related problem --- I suddenly lost all of the disk free space---after some trial and error, I finally address it using the
 ```
sudo touch /forcefsck
```
and then restart to do a disk checking...From this, can I say it is a case of false drive space report? This always happens after a large amount of i/o operations. (I am using Kubuntu 10.04,recently updated)

I hope that this issue can bring attention to users having this problem, and that someone can inform the developers about this bug.:)

---

### Post by drs305 on 2011-02-25
radiobert,

That is a solution I fortunately haven't needed, but perhaps another reader may. 

If it happens to you again, you may want to find out what is happening with your disk. Since you don't want to check mounted disks, boot the LiveCD and then run the following (replace **XY**):
```
e2fsck -f -v -n /dev/sd**XY**
```
That will show you any errors and perhaps give you an indication of why your disk/partition is having problems. If you have errors, run this to repair them:
```
e2fsck -f -v -y /dev/sd**XY**
```

---

### Post by Keith OZ on 2011-05-04
I have a problem with disc space it seems after backing up my laptop incorrectly with SBackup. A back up has been located at /var/backup etc it appears. Thinking the problem was with disc space I shrunk the size of the windows partition with GParted - which didnt help. I found this thread and followed the instructions in point 6 as far as I could. I could identify the file but could not understand how to delete it (sorry novice user). And the computer no longer drops the command line - I have been getting to it via safe mode. Very frustrated how such a simple thing (back up) could cause so much trouble.  Could someone explain a simple way to get remove the offending file and get the system booting again (unless I have caused more trouble in my attempts at repair).

---

### Post by drs305 on 2011-05-04
By 'safe mode' I'll assume you mean Ubuntu's recovery mode and not Window's 'safe mode'.

If you can get the GUI working, the safest way to delete the file would be to use nautilus as root:
```
gksu nautilus /var/backup &
```
If it won't open, try installing an app called *nautilus-gksu*. This will allow you to open Nautilus as a normal user, then right click a folder and enable "open folder as administrator" so you can delete system files.
```
sudo apt-get install nautilus-gksu
```

I'm very hesitant to use "sudo rm" since if you mistype the command you can wipe out your entire system. So next I would try to change ownership of the backup file to yourself, and *then* delete it. Of course, you don't want to make a mistake with this command either:
```
sudo chown <your_username> /<path>/filename
rm /path/filename
```
Example:
sudo chown drs305 /var/mybackupfile
rm /var/mybackupfile

---

### Post by tagMacher on 2011-08-29
Two-and-a-half years later, your post is still a life-saver. I was hit by issue 6(b) in your post on my Ubuntu 10.04 desktop. Tried everything I could think of, but disk space used to get used up faster than I could clear it. I had all but downloaded the 11.04 disk thinking I might as well upgrade if I am going to re-install, but took an early break from work and got thinking & searching the Ubuntu forums from home.

Thanks a lot!

---

### Post by anshulfy on 2011-10-20
Thanks for such a useful guide. :)

---

### Post by ageofsteam on 2012-01-20
> **radiobert said:**
> Thanks for preparing this guide. Here, I have a hard-disk space related problem --- I suddenly lost all of the disk free space---after some trial and error, I finally address it using the
 ```
sudo touch /forcefsck
```
and then restart to do a disk checking...From this, can I say it is a case of false drive space report? This always happens after a large amount of i/o operations. (I am using Kubuntu 10.04,recently updated)

I hope that this issue can bring attention to users having this problem, and that someone can inform the developers about this bug.:)
I've been having a similar problem with a UFD version of Ubuntu; I'll try this.

And to the original poster: thanks for the guide!

---

### Post by WinRiddance on 2012-02-05
> **typos1 said:**
> I ve got discc space problems and I suspect its to do with my lost+found folders, but for some reason terminal will not let me do anything-yesterday it said I was typing the wrong password (I wasnt) today the cursor simply moves down the terminal after I enter the password or the password is displayed (usually it isnt) but nothing happens in the terminal.

Anyone got any ideas why it wont let me sign in as root?

Very strange terminal will run some commands but not others, some folders are locked and when I right click most options are greyed out, so I cant for instance delete log files in /va/log and there is apparently 46Gb worth of files in /var/log which seems like it might be the root of my problem. I also now dont get a "delete" option when I right click, I only get move to rubbish bin.

It sounds to me like you have a bad, or damaged installation. How long ago did you install Ubuntu ... did you understand everything that you were doing ... are you aware of the fact that login passwords and keyring passwords are not used at the same time for the same thing? My Dad had a password issue because he didn't realize that when he installed Ubuntu the keyring password request doesn't look much different than the user login password request for things like the terminal. Consequently he ended up with two different passwords and then it took us a long time before we finally figured that out. He always used his default user login password for everything ... never realizing that he keyring password wasn't the same thing.

Also, did you recently create an upgrade with older backups? Some file corruption may have occurred that way. Last but not least, if you did a new installation with the same user and password as before, is it possible that there's an upper/lower case issue going on, between the original password from your old setup and the password from your new setup? It sounds almost as though your terminal is trying to recognize two different passwords. Just stabbing in the dark since you really didn't offer a lot of information ...

Have you tried cold starting your computer? Power off completely (the proper way), let the system sit for 10 - 15 minutes, and then turn the power back on. Sometimes that helps to reset and "freshen up" things.

.

---

### Post by NM5TF on 2012-02-17
hey drs305.....thanx for such a useful guide on how to recover disk space...
my problem was associated with "simple backup"....

there were backup files going back over 3 years that I didn't even know existed....:confused:

using your instructions I was able to recover over 150 GB of space :P

you rock dude :guitar:

Tommy

---

### Post by Lateralus138 on 2012-06-23
Thank you for this guide, it has given me a whole different view of Ubuntu and Linux in general and I just had a 90 gb partition of ubuntu that was completely full and I deleted 47 gbs with this guide and mostly because I didn't know to delete with shift+del.

Thanx a lot!!!

---

### Post by drs305 on 2012-06-23
> **Lateralus138 said:**
> Thank you for this guide, it has given me a whole different view of Ubuntu and Linux in general and I just had a 90 gb partition of ubuntu that was completely full and I deleted 47 gbs with this guide and mostly because I didn't know to delete with shift+del.

Thanx a lot!!!

Glad it helped.  :-)

Happy Ubuntu-ing !

---

