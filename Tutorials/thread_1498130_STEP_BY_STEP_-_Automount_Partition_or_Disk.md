---
title: "STEP BY STEP - Automount Partition or Disk"
date: 2010-05-31
forum: Tutorials
---

### Post by WinRiddance on 2010-05-31
Alright, I'm seeing lots of posts about **automounting** with this disk or that partition, being able to establish access privileges on disks, and so on. This tutorial will explain to you step by step how to automount any partition or disk drive, to include external ones such as USB drives. This can be done with USB sticks too _but I would not recommend doing so_ if the USB stick is not permanently attached to the machine. The following tutorial will cause your machine to automatically locate, mount, and provide _full access privileges_ to a particular disk/partition after every restart. This will work on NTFS partitions too! **You can not under any circumstances make a mistake** ... **if you do your disk may become inaccessible to you !!!**

[COLOR=DarkRed]**NOTE:**[/COLOR][COLOR=Indigo] This tutorial causes for the automounted disk/partition to vanish from your desktop by hiding it under File System i.e. /mnt permanently. As a result you may want to later use your Nautilus File Manager in order to set yourself some bookmarks to various portions of your automounted disk. [/COLOR][COLOR=DarkRed]**If you already have bookmarks**[/COLOR][COLOR=Indigo] to particular areas of that disk right now, those will be lost and you'll have to set them up again, just once of course. Taking a screenshot of your current File Manager setup with its bookmarks might be a wise idea. That's what I did. [/COLOR][COLOR=DarkRed]**Anyway, ready or not, here we go ....**[/COLOR]

First we're going to create the directory/folder where access to the automount partition will be provided. I gave my own partition a label which is Ubuntu-Spare. Having a label for a partition is definitely handy to have for easy recognition purposes. This can be done via START ... SYSTEM ... ADMINISTRATION ... DISK UTILITY. Consequently my command looked like this:
```
sudo mkdir /mnt/Ubuntu-Spare
```Then I needed to know what the **UUID** and other info. for the automount disk/partition is. Since I had no idea how to do this the easy way for individual partitions, I went ahead and used this command **to show me all** of the connected drives/partitions on my machine:
```
sudo blkid
```Now go ahead and find the entire line that pertains to the disk/partition that you wish to permanently automount. If your disk has a label finding it is a no-brainer. Highlight and copy the entire line for that particular disk or partition and paste it into a text file for the time being (Start menu ... Accessories ... Gedit Text Editor). On my machine that line looked like this:
**[COLOR=DarkSlateGray]/dev/sda5: LABEL="Ubuntu-Spare" UUID="d897577c-187f-46b2-86a1-1f118f9a414a" TYPE="ext3"[/COLOR]**

[COLOR=DarkRed]**SIDE NOTE:**[/COLOR]  [COLOR=Indigo]UUIDS for Windows are generally shorter and may look something like this: 924A26734A2653EF
(as opposed to d897577c-187f-46b2-86a1-1f118f9a414a)[/COLOR]

Now we need to edit the fstab file correctly. This file tells the Operating System (Ubuntu) which drives/partitions to seek and mount during each startup process. To edit the fstab file we'll be using this command which will temporarily change the appearance of your terminal:
```
sudo nano /etc/fstab
```Use your arrow keys to scroll down to the bottom. **Since the fstab file is critical** to the system I like to add a little comment, to remind me of what I'm responsible for in case I need to access that file later on. This first line does not need to be added, it's just my preference (The pound symbol in the beginning **is** required):
**[COLOR=DarkSlateGray]#Added line as a reminder that following automount command was added by myself![/COLOR]**

Then I added the following line directly below my comment line. Making a spelling error or leaving something out here **may have dire consequences!** Your UUID number must be perfect - no quotation marks just like here - and your label must be spelled perfectly as well. Copy this exactly and then simply replace the 12345 UUID and label with your own:
**[COLOR=DarkSlateGray]UUID=1234numberofyourownautomountdiskgoeshere1234 /mnt/Ubuntu-Spare          ext3    defaults        0       2[/COLOR]**

[COLOR=DarkRed]**SIDE NOTE:**[/COLOR]  [COLOR=Indigo]Use your Windows label for an NTFS partition and replace the existing ext3 with **ntfs** instead if you copied from this tutorial for your Windows partition. If your Ubuntu automount partition happens to be ext2 or ext4 you'd obviously want to change that accordingly as well.[/COLOR]

**Now we're finished with the fstab file.** Use the **CTRL** + **X** keys on your keyboard to save and quit the session. You'll be asked to verify that you want to do this. Verify by entering the capital letter **Y** for yes and the session should end automatically. If you were to type the sudo nano fstab command from above once more you'd be able to double-check that your entry was indeed saved.

Since we're now back in the terminal screen enter the following command, telling the machine i.e. Operating System to automount the added fstab partition:
```
sudo mount -a
```If I recall correctly, for Windows based partitions there's nothing left to do ... you're finished. However, if you're automounting an Ubuntu partition and you wish to have **full access privileges to that partition** at all times, then you have to add one final terminal command which is this one here (obviously use your own user name and the correct path to your automount partition label:
```
sudo chown -R winriddance:winriddance /mnt/Ubuntu-spare
```[COLOR=DarkRed]**This will take some time to complete**[/COLOR] [COLOR=Indigo]since the entire automount disk/partition has to be indexed once. If you look at the hard disk light on your machine it should be pretty busy. If the automount partition is empty this should take no time at all. When the indexing is completely finished you should see something like the following in the terminal screen (where winriddance would be replaced by your user name):[/COLOR]
**[COLOR=DarkSlateGray]winriddance@winriddance-laptop:~$[/COLOR]**

Go ahead and type EXIT in the terminal, followed by rebooting your computer. **Afterwards go to** START ... PLACES ... and click on COMPUTER in order to open up the Nautilus File Manager. Go to EDIT and then PREFERENCES to enable the single-click option under BEHAVIOR to save time. Now look for _File System_ on the upper left side, and via this locate the **mnt** folder to view your automounted disk/partition upon opening up that mnt folder by clicking on it. **To make bookmarks** simply locate the desired folders within your automounted disk and create a bookmark when you see the contents of the opened folder in front of you. The bookmark will appear at the lower left and can be renamed, deleted, and so on without impacting the physical disk/partition itself that's located in the mnt folder.

[COLOR=DarkRed]**Now you're done!**[/COLOR]
[COLOR=Indigo]If you messed this up I cannot help you. It is critical that all of the above steps be followed perfectly and without any spelling mistakes or missing numbers in the UUID. Good luck and **be totally proud of yourself for having accomplished this** if you've never had to wrestle with a terminal screen before![/COLOR]

---

### Post by nilarimogard on 2010-06-01
Here is a script which automatically writes the fstab file to automount NTFS drives on startup: [http://www.webupd8.org/2010/04/ubuntu-script-to-automatically-mount.html]("http://www.webupd8.org/2010/04/ubuntu-script-to-automatically-mount.html")

---

### Post by WinRiddance on 2010-06-02
That's great. I'm trying real hard to provide information that even total beginners won't mess up as long as they're paying attention to what they're reading. Would be awesome if a script such as yours also included a label search and/or a label creation, something simple like **Disk_Automount1_ntfs** [COLOR=DarkRed]**Disk_Automount2_ext3**[/COLOR] [COLOR=Navy]**Disk_Automount3_ext2**[/COLOR] and so on.

Particularily people switching from windows, and most especially people who are somewhat new to computers in the first place, often have a very difficult time relating to 3 letter abbreviations like dev or sda3 or whatever. A label would go a long way, allowing people to understand much faster what the heck they're looking at in the mnt or media folder. As Ubuntu evolves more and more into something that doesn't require a terminal, details like that could become more and more important. That's way beyond my own mediocre skills though ....

---

### Post by Captain_Falafel on 2010-06-13
Thanks for this! :)

---

### Post by SoFl W on 2010-06-23
Thank you, this helped and I learned a thing or two.

---

### Post by lokojones on 2010-08-16
> **WinRiddance said:**
> 
```
sudo chown -R winriddance:winriddance /mnt/Ubuntu-spare
```[COLOR=DarkRed]**This will take some time to complete**[/COLOR] [COLOR=Indigo]since the entire automount disk/partition has to be indexed once. If you look at the hard disk light on your machine it should be pretty busy. If the automount partition is empty this should take no time at all. When the indexing is completely finished you should see something like the following in the terminal screen (where winriddance would be replaced by your user name):[/COLOR]
**[COLOR=DarkSlateGray]winriddance@winriddance-laptop:~$[/COLOR]**


I wouldnt change the whole partition permission, just the mount point, before mounting the filesystem on it: you may have more than one user storing files on the partition, and you may want to keep the owners.

By the way, why do you call that "indexing"? isn't it just changing all the perms on that directory recursively?

But anyways, nice guide :)

PD: Anyone else having 2 entries refering to the same disc in nautilus? One alredy mounted because of fstab, and another beeing a gnome auto-entry?

---

### Post by pils92 on 2010-12-12
Check out, [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html), very helpful information how to write your /etc/fstab:popcorn:

---

### Post by eferox on 2012-05-01
Works great, just I sugest add **uid=1000** to mount options, it will let move files to trash for default users and in 6th column use **0** it will skip filesystem check on startup. 
```
UUID=FE28BEAF28BE65F5 /mnt/Data ntfs defauls,uid=1000 0 0
```

---

