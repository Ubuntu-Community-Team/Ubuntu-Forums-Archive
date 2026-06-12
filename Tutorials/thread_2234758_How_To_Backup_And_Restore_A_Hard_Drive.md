---
title: "How To Backup And Restore A Hard Drive"
date: 2014-07-16
forum: Tutorials
---

### Post by at_first_light on 2014-07-16
I thought I would make a quick thread on doing a basic backup of a hard drive. This includes your personal files, and any operating systems you have installed on it. There are many better ways of doing backup and restore procedures, but if you are new to such things this basic method with DD is a great place to start.

DD is a sector based backup tool. When using it make sure to type in the correct if and of locations. If you don't **you can accidentally overwrite things forever.** Since DD is a sector based backup tool the source drive must be smaller than the partition you save the image to. **The image size will be the same size as the drive!** Also note that you cannot save the image to the drive you are backing up for obvious reasons.

You might consider setting up a virtual machine of some kind to do some testing, before guinea-pig-experimenting with your real system, and real DATA; just a thought.

[SIZE=3]**_Questions:_**[/SIZE]

1. When would someone do a hard drive backup? 

It's a good idea to do a backup before attempting tasks that might endanger the system
so that if things go wrong you can restore it and pretend it never happened :). You might also want a backup handy in case your OS runs into some fluke problem
like suddenly refusing to boot up.

2. Can I use DD to clone my drive to another drive?

Technically yes the program itself can be used for such, but the commands in this guide aren't intended for that. Cloning to another drive is more complicated, and there are potential problems like partial filesystems. If you are interested in cloning to another drive open a new thread elsewhere to ask about it; **this guide is only for backing up a drive and restoring to the same drive.**

3. What happens if I restore to the wrong drive?

DD overwrites the sectors themselves which is equivalent to zeroing out the drive. The data is gone forever! If you have other drives you may wan to disconnect them before doing a restore. DD must be run as root, so it has the power to overwrite anything and everything, and if you accidentally tell it to it will.

[SIZE=3]_**Steps:**_[/SIZE]

_**Create An Image:**_
1. Boot up an Ubuntu 14.04 - Desktop X86-64 Livecd.
2. Choose "[COLOR=#0000ff]Try Ubuntu[/COLOR]".
3. Once at the desktop, go to the Unity dash, and search for "[COLOR=#0000ff]Gparted[/COLOR]". It will show up in the search results as Gparted Partition Editor; open it.
4. In the top right corner of Gparted there is a list of drives, choose the drive you intend to backup.
5. If there are any swap partitions on this drive right click on them and choose "[COLOR=#0000ff]swap off[/COLOR]". If there are any mounted partitions right click and choose "[COLOR=#0000ff]unmount[/COLOR]".
6. Note down the device name of the drive you wish to backup, and the drive + partition you will save the backup to. In my case I will be backing up drive "[COLOR=#0000ff]sdb[/COLOR]" to partition "[COLOR=#0000ff]sda1[/COLOR]".
7. Exit Gparted, and head once again to the Unity dash. Search for "[COLOR=#0000ff]Terminal[/COLOR]", and open it.
8. In the terminal type "[COLOR=#0000ff]sudo -i[/COLOR]".
9. Keep the terminal open. Go to Unity's dash, search "[COLOR=#0000ff]Nautilus[/COLOR]", and then open Nautilus.
10. In Nautilus there is a list of partitions on the left hand side, click the one you will be saving your image to. In my case it's called "128 GB Volume". When it opens the Window title will either have the same thing, or something different. Note down what it says. In my case it's "16bec086-64a0-4697-a55a-582a5ac6a56a".
11. In Nautilus on the left hand side menu click "computer". Browse to "/media/ubuntu/". You should see a folder with the name you previously noted down. This means it's successfully mounted.
12. Close Nautilus, and go back to the terminal window you have open still.
13. In the terminal type "[COLOR=#0000ff]dd if=/dev/THEDEVICEYOUWANTTOCOPY of="/media/ubuntu/THENAMEYOUPREVIOUSLYNOTED/backup.img"[/COLOR] " In my case it will be "[COLOR=#0000ff]dd if=/dev/sdb of="/media/ubuntu/16bec086-64a0-4697-a55a-582a5ac6a56a/backup.img"[/COLOR] ". Press "[COLOR=#0000ff]enter[/COLOR]" on your keyboard. The cursor will just sit there flashing, and when it finishes it will display some stats. My hard drive was only 1GiB so it took about 22 seconds, but if your drive is quite large then it may take a very long time.

_**Restore An Image:**_
1. Boot up an Ubuntu 14.04 - Desktop X86-64 Livecd.
2. Choose "[COLOR=#0000ff]Try Ubuntu[/COLOR]".
3. Go to Unity's dash, search "[COLOR=#0000ff]Nautilus[/COLOR]", and then open Nautilus.
4. In Nautilus there is a list of partitions on the left hand side, click the one where you saved your img file. In my case it's called "128 GB Volume". When it opens the Window title will either have the same thing, or something different. Note down what it says. In my case it's "16bec086-64a0-4697-a55a-582a5ac6a56a".
5. In Nautilus on the left hand side menu click "computer". Browse to "/media/ubuntu/". You should see a folder with the name you previously noted down. This means it's successfully mounted. You can close Nautilus.
6. Go to Unity's dash, search "[COLOR=#0000ff]Gparted[/COLOR]", and then open it. 
7. On the right side there is a list of disks, choose the one you will be restoring to.
8. If the drive has any active swap partitions you will need to right click and choose "[COLOR=#0000ff]swap off[/COLOR]". If the drive has any mounted partitions you will need to right click and choose "[COLOR=#0000ff]unmount[/COLOR]".
6. Close Gparted, go to the Unity dash, and search for "[COLOR=#0000ff]Terminal[/COLOR]". Open the terminal.
8. In the terminal type "[COLOR=#0000ff]sudo -i[/COLOR]".
7. In the terminal type "[COLOR=#0000ff]dd if="/media/ubuntu/THENAMEYOUPREVIOUSLYNOTED/backup.img" of=/dev/THEDEVICEYOUWANTTOCOPY[/COLOR]" In my case it will be "[COLOR=#0000ff]dd if="/media/ubuntu/16bec086-64a0-4697-a55a-582a5ac6a56a/backup.img" of=/dev/sdb[/COLOR]". Press "[COLOR=#0000ff]enter[/COLOR]" on your keyboard. The cursor will just sit there flashing, and when it finishes it will display some stats. My hard drive was only 1GiB so it took about 24 seconds, but if your drive is quite large then it may take a very long time.

---

### Post by livewirebt2 on 2014-07-16
I'm sorry, but was there really a need for creating another thread for this topic?
[LIST]
[*][General Help - [all variants] Cloning a hard drive using dd]("http://ubuntuforums.org/showthread.php?t=1162706") 
[*][HOWTO: Create, Recover and Automate System Images]("http://ubuntuforums.org/showthread.php?t=581680") 
[*]and possibly other tutorial-like threads 
[/LIST]

It's more like that there are to many guides that contain slightly different intructions where a user would want to find all information in one place. I would suggest [updating or improving information on the Wiki instead]("https://help.ubuntu.com/community/BackupYourSystem").

---

### Post by at_first_light on 2014-07-17
Yesterday I created a thread for warning messages, and ideally these messages will link to relevant threads. I've created a warning about creating backups before partitioning, and I could not find any new-user-friendly dd threads for backing up and restoring hard drive images so I made this one.

These didn't come up in my search results, but I still think mine has it's place.
[http://ubuntuforums.org/showthread.php?t=1162706](http://ubuntuforums.org/showthread.php?t=1162706) deals with direct drive to drive cloning, my thread is about making an image to restore to the source drive.
[http://ubuntuforums.org/showthread.php?t=581680](http://ubuntuforums.org/showthread.php?t=581680) is an advanced post, and my goal was to make something to cover the basics.

---

### Post by GrammatonCleric on 2014-08-17
Yeay!  Someone read my post... =)

---

