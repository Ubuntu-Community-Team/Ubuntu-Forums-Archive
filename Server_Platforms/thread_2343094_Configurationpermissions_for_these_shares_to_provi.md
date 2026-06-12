---
title: "Configuration/permissions for these shares to provide correct user access as below?"
date: 2016-11-13
forum: Server Platforms
---

### Post by agarwaldvk on 2016-11-13
Hi Everyone


My current Ubuntu Desktop 16.04 LTS machine has the following directory structure :-

/media/dataplusmediafiles/share4media/
                                  /share4data/

Each of the 2 sub-folders viz “share4data” and “share4media” are physical hard disk drives mounted like so :-

/dev/sda1 /media/dataplusmediafiles/share4media/ ntfs-3g defaults 0 0
/dev/sdb1 /media/dataplusmediafiles/share4data/ ntfs-3g defaults 0 0

The current share definition of the “dataplusmediafiles” share is as follows :-

[dataplusmediafiles]
path = /media/dataplusmediafiles
browsable = yes
writable = yes
guest = ok
read only = no
public = yes
guest account = nobody
force user = nobody
create mask = 777
admin users = agarwaldvk

My understanding (flawed as it might be) is that the default umask is 002 in Ubuntu. With this setting, I would have thought that the permissions for the sub-folders “share4data” and “share4media” would be 775 with the world not having write permissions? But as at now, anyone (as in any user) can access these shares from within Windows Explorer and can read, write and execute on all the files and directories in there without having to enter a password. This can be seen from the output of the below commands.

The output of the commands :-
“ls –ld /media/dataplusmediafiles/share4media/” and
“ls –ld /media/dataplusmediafiles/share4data/”

show 777 permissions for both of these sub folders. How is that?

agarwaldvk@MyHomeServer:~$ ls -ld /media/dataplusmediafiles/share4media/
drwxrwxrwx 1 root root 4096 Nov 4 09:10 /media/dataplusmediafiles/share4media/

agarwaldvk@MyHomeServer:~$ ls -ld /media/dataplusmediafiles/share4data
drwxrwxrwx 1 root root 4096 Nov 12 07:18 /media/dataplusmediafiles/share4data

Question 1
What should my configuration be like  for the share "dataplusmediafiles" so that only myself, as the administrator (user – agarwaldvk), can make modifications to the files and directories within the sub-folder “share4media” with everyone else able to read and browse through it and all of its sub directories and execute all of the files there as well without requiring a password. All the files therein are media files in that they are either image, video or music files.

Or should I be creating a separate share for "/media/dataplusmediafiles/share4media" path with the appropriate configuration parameters (you all may need to help me specify the right parameters for this share as I don't know any better) and delete the share for "/media/dataplusmediafilese4media" path altogether to meet the above need?

Question 2
What should my share configuration be like for the "share4data" path so that the following access can be  provided to the users :-
i.  Each of the users and myself (as the administrator) to have full to their files and folders
ii. Everyone to have full access to the "common" folder

To realize the above, I was wondering if it would be better if the share for "/media/dataplusmediafiles/" path be deleted altogether and a separate share for "/media/dataplusmediafilese4data" path be created  with the appropriate configuration parameters (you all may need to help me specify the right parameters for this share as I don't know any better).

Not sure if this is a viable option for this share to realize the above access permissions :-
1. this share to have a directory mask of 1770 (sticky bit enabled) to permit root and user to have full access to each of the user folders
2. the "common" folder to have overriding 777 permissions



Best regards


Deepak

---

### Post by darkod on 2016-11-13
Why are you using ntfs on linux server?

I think it might limit the control of permissions. I have never tried it on ntfs, only on linux filesystems.

---

### Post by agarwaldvk on 2016-11-13
Hi darkod


The reason that  I had ntfs format was because I read somewhere that I should be using ntfs format if both Windows and Linux O/S are likely to use the partition. I interpreted that to mean that if both Windows machines are also supposed to access it then use ntfs otherwise ext4. Given that this has been specified and the "share4media" has 1.4 tb of data on it, I am not so sure if its a good idea to reformat it to ext4 and reload all that much of data.

However I can format the other partition ("share4data") - that is currently empty, if that helps.


Do the permissions however get affected by the partition format?



Best regards


Deepak

---

### Post by volkswagner on 2016-11-13
"Partition Format" = filesystem.

NTFS is not a native Linux filesystem. This certainly will have an impact on available permissions and
other file system related properties.

References to sharing a partition or file system between Windows and Linux generally
are specific cases for dual boot/multiboot, where the computer will have boot options to 
boot into Windows or Linux OS.  Hopefully this is not your case, so SAMBA mounted
file systems should not be on NTFS partition.

You may run into other issues in the future due to NTFS, so it's advisable to correct this issue sooner than later.

You may find some work arounds [here]("http://askubuntu.com/questions/113733/how-do-i-correctly-mount-a-ntfs-partition-in-etc-fstab"), but I'm with darkod (suggest reformat to native Linux filesystem)

---

### Post by agarwaldvk on 2016-11-13
Hi Guys


Thanks for your response. Greatly appreciated.

But really....

Do I need to reformat the drive and reload the entire 1.4 tb of data - mate! That's gonna take me forever.

But given that you all feel so strongly about it and believe that I should, I will. But please be with me as I go through this - I don't want to loose my 1.4 tb of data.

Process wise, is it OK If I were to :-
1. first format the other share (sub-directory) called "share4data" - which is currently empty

Do I now need to restart the server to remount these drives again, particularly the one which would now have been reformatted to ext4 format. By the way, how to I mount the drive as ext4?


Is it just this command :-
/dev/sdb1 /media/dataplusmediafiles/share4data/ ext4 defaults 0 0



2. then copy all my data from the "share4media" folder on to this newly formatted folder (drive as such as its a physical drive). Would I be able to do from within Windows Explorer?
3. then format the other share (sub-directory) called "share4media to ext4 format - this again is a physical drive

Having implemented the steps above, to avoid having to copy the data back from the data share to the media share, could I interchange the mount points names for these 2 drive in the fstab file or will that stuff it up and I would need to do that one at a time?


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-13
Hi Guys


Just an update. I formatted the "share4data" drive in ext4 partition. The fstab file configuration is attached. Having done that, I am not able to access this share from windows machine anymore.

Haven't made any changes to the original share definition.

The output from the sudo fdisk -lu is also attached - part


Further update (4 hours after initial formatting of the data drive) :-
I am currently full reformatting (not the quick format) the drive to ext4 format. Its gonna take around 9 hours from now!

I am intending to then :-
1. mount this drive from the terminal using "sudo mount /dev/sdb1 /media/dataplusmediafiles/share4data/ ext4 defaults 0 0" command
2. assign 777 permissions to this sub-directory as a starting point to at least make it visible from Windows machine using "chmod -R 777 //media/dataplusmediafiles/share4data" command
3. test accessibility from Windows machine (test for read/write/execute permissions) by copying/pasting some data in to this drive (folder)
4. if successful, change fstab to auto mount the drive with "/dev/sdb1 /media/dataplusmediafiles/share4data/ ext4 defaults 0 0"
5. restart the server machine
6. copy the entire data from the ntfs partition to this ext4 partition
7. test accessibility of this data from windows machine
8. if successful, quick format the ntfs partition to ext4 partition
9. update corresponding entries in fstab file for this drive
10. restart machine

After this, with the media data now residing on the "data" drive (share) and the "media" share being empty,  would it then be possible to rename the shares accordingly without losing any data?



Please advise what can I do. I am hoping that I am not being too much of a pest here but I might need a little more than a little help given my current limited knowledge of the linux based systems but I am trying.


Best regards


Deepak

---

### Post by darkod on 2016-11-14
I would give you couple of advices, if you want to accept them...

1. Create a shorter path for the share (mount point). There is really no need to be so long. Something like /data/media and /data/data (or /share/media and /share/data) would be enough. So,
```
sudo mkdir /share
sudo mkdir /share/data
sudo mkdir /share/media
```

2. Running chmod 777 is OK on empty folders, first time you create them. But when your folder already has loads of data, I really don't like that command (and many tutorials have it inside). The reason is because 777 is actually used on folders, and to give RW access to files it's 666. But because the data is a mix of subfolders and files, you shouldn't use one or the other. Another way to give Write permissions to everyone using chmod is:
```
sudo chmod -R a+w /share
```

Note that samba needs the write permissions to be present from the first folder in the path, not just the actual shared folder. So if you make the main mount point /share, run the write permission recursively from there.

And about your questions about temporarily storing data in the other share and then renaming them, yes, you can do that. Samba and the clients don't mind what the share is called. You can do that...

Also by giving write to all recursively you have to think about whether you want any permissions limitation or not. Because that will give everyone the possibility to modify and delete files.

3. Mounting from the command line is only:
```
sudo mount /dev/sdb1 /share
```

For ext4 partitions you don't need anything else. Those additional options are only for inside fstab.

---

### Post by agarwaldvk on 2016-11-14
Hi darkod


Genuinely appreciate your responses. Mate, look if I am seeking help from those that I believe are in the know, the likes of you, then it becomes incumbent upon me to take your advice to the letter. And I would be doing it - otherwise there is no point me seeking help!

As an example, despite my initial apprehension to copy and paste 1.4 tb of data from one drive to another to format the drives to ext4 format, I would certainly be doing that (after of course the formatting is completed - its just taking its own time - the formatting didn't finish until this morning when I left for work.) because you all believe its the right thing to do. You can take if from granted that I am going to be following your advice to the end. 

I will create shorter share names - no problem.  Tell me this though, is it a good idea to create a kind of a personal share at the 'root'. Everything that I had read online recommended that the shares be created at '/media/' level and drives be mounted either at /media/' or at best '/mnt/'. That was why I created the parent share at the '/media/ location and the dedicated shares for data and media (even though there are separate physical hard drives) under the parent folder but nevertheless.

If you think its OK, could I rename (you will have to tell me how) the share "dataplusmediafiles" to "sharedfiles"? With the "sharedfiles" name, please advise which of the following two options would you recommend and I will follow your recommendation :-

sudo mkdir /media/sharedfiles/
sudo mkdir /media/sharedfiles/data/
sudo mkdir /media/sharedfiles//media/

or 

sudo mkdir /sharedfiles/
sudo mkdir /sharedfiles/data/
sudo mkdir /sharedfiles//media/

Whichever way, it wouldn't involve movement of the media data that I have (1.4 tb) to another location, would it?


Your comment about mounting - no problem. I will test it using the standard command on the terminal as you have shown me but I will need those options when I make the entries in the fstab file, wouldn't I?

Finally, about the permissions - this is the hardest bit for me to understand and implement. Mate, please help me out here.

The thinking behind my giving 777 permission at the "/sharedfiles/" level was this :-
Ubuntu has a default umask of 002, which, I thought would then assign the permissions of 775 to the paths "/media/sharedfiles/media/" and "/media/sharedfiles/data/". This would be perfectly fine for me for the "/media/sharedfiles/media/" path as it is intended for me (as the administrator) to be the only one to be able to add/delete/rename/modify files and folders therein with everybody else able to view and execute these files from within Windows Explorer from their Windows machine without having to enter any password. This share will only hold media files, no data files.

For the other share (data share), the intent is that the 3 users will have their own folders (initially create by me) which they (and I) will have full access to). In addition to these,  there would be a common folder with full access to everybody. To realize this, for the sake of my convenience, given my limited knowledge of Linux based systems, I was looking at specifying the 1775 permissions at the share level (that is at the "/media/sharedfiles/data/" level) after changing the ownership of these folders to the respective users. This, I presume would override the 775 permission afforded by Samab/Ubuntu following the application of its default umask of 002 at the parent folder level. Subsequently, I will grant 0777 permission to the "common" folder to enable everyone full access to add/delete/modify files and folders therein.

This is just to ensure that user specific files/folders are not inadvertently deleted/modified by other users.

Will this work?????????? 


Does "sudo chmod -R a+w /share" give the user access to read and to delete their own folders in the data share?


Let me know what you think of what I have said. I shall look forward to knowing. I would be working on it once I get home in the evening tonight.


Best regards


Deepak

---

### Post by darkod on 2016-11-15
You are not actually "creating a share at the root". The filesystem in linux always starts with / and after that you have the folder (directory) structure. Any empty folder can be used as a mount point. The important thing is the folder to be empty.

Using it as mount point you simply "attach" the partition to that folder and browse its content by using that folder path. So it doesn't really matter if that path is short or long. So why typing long paths and risk syntax errors when it can be short.

You can also have the mount points for your two disks without them being in the same parent folder. Like for example /data1 and /data2. Organize it how ever you want and how it makes more sense to you, just be careful with the folder structure you create.

If you apply 777 then that is what is going to be applied. It has no relevance to the ubuntu default mask of 002 and the permissions applied will not be 775, they will be 777 because that is the command you are issuing. So if you run -R 777 from the shares parent folder in fact you will be giving everyone Write rights on both media share and data share. Which is not what you want to do according to what you said, that only you want to modify the media files.

Before even adding or removing permissions, what you need is to check current permissions because most folders are created as 775 or 755, so everyone would already have read permissions. In such case you only need to add write permissions on the data share, for example. Or anywhere where you need users to have write permissions.

You also need to be careful how you plan to structure the data share. If users will have their own folders and if you want only that user to be able to modify his folder, again you can't run -R 777 or -R a+w on the whole share. That will give everyone write/modify permissions. In such case leave the folders as 775 or 755 and modify the user owner of the folder where needed. Like that, with 775, only the user owner or group owner will have W, while all others will have only R. If you don't want other users to even be able to browse the folder that doesn't belong to them, you will have to use something like 770 or 750.

Don't forget, it's always a combination of two things: ownership and permissions. Not just permissions. It matters which user and group own that folder too. That is how you adjust access.

---

### Post by agarwaldvk on 2016-11-15
Hi darkod


Something terrible has  happened.

Remember you said that I should format my drive to ext4 format. So I was doing that yesterday (last night) and for some reason it stopped at 87%. Now I can't boot the computer - it says it can't even find /dev/sdb - this is the drive that was being formatted.

I even tried to disconnect this drive physically but that doesn't work either. I can't boot the machine. I get these options at startup :-

Ubuntu
Advanced options for Ubuntu
Memory test (nemtest86+)
Memory test (nemtest86+ serial console 115200)


At end, Enter to boot, e to edit or c for command line.


What do I do? Pleeeeeeeeese help!


Best regards


Deepak

---

### Post by darkod on 2016-11-15
Hmmm formatting should take that long. How were you doing it, with:
```
sudo mkfs.ext4 /dev/sdb1
```

That should format sdb1 as ext4 and it finishes in 5-10mins if the partition is 2-3TB.

Anyway, if the computer can't boot even with the disk disconnected, then it doesn't look like it is related to the sdb disk or the formatting.

The machine has ubuntu OS installed, not any kind of windows, right?

In the grub menu you described, what happens if you select the Ubuntu entry?

---

### Post by agarwaldvk on 2016-11-15
Hi darkod


Firstly, which part of the world are you in  - just for the timing difference. I am in Melbourne, Australia. Its about 6.45 here now!

Anyhow! I was formatting (the full format, not the quick format) using the 'Disks' GUI facility from the Mate remote desktop that I have installed. It was doing at the rate of around 50 MB per second and it said about 9 hours. Sounded OK to me and so I let it be. It stopped the following morning. I even tried Gparted last night. I couldn't format the drive and it couldn't even delete the partition - said 'Input/Output/ Error'

The machine only has Ubuntu 16.04 LTS Desktop, nothing else. It is installed on the SSD.

If I were to select the 'Ubuntu' option it goes back to the 'Welcome to Emergency Mode' giving a few options. The only option that seemed to work was 'systemctl reboot' which would reboot. I tried 'journalctl -xk' (I think) and it showed a whole stack of lines going past the screen and I didn't follow a word of it and so I rebooted. I once selected the 'c' option and it took me to the command line but I didn't know what command to type to get going.

I am not so worried about the data as I know that this was the empty that I was formatting - as a test.

Also, this machine currently doesn't have an optical drive. I am going to buy one today and see if I can install it off it (Live CD apparently) and then try and access the fstab file. I think that maybe if I could get to it and comment out the two lines with reference to the mounting of the 2 physical drives and then reboot (removing the CD ROM) from the SSD, it should be OK, shouldn't it. The question though is that how do I get to the fstab file from the previous installation because that would be on the '/etc/' of the SSD, wouldn't it? These 2 lines are the only difference between the original fstab file and one that is being used. I make a backup of the original file.

Even otherwise, with the way things are, is there a way to get to this fstab file anyway, given that it doesn't even fully boot?

Not sure with what I have told you, if its of any help to you to tell you any more than what you already do of what might have happened.




Best regards


Deepak

---

### Post by darkod on 2016-11-15
Ah, I didn't know you are actually running the Desktop version with a GUI... Even on the desktop version, the best way to format quickly is simply using terminal and command line. It might have worked out better.

What if you select the Advanced options in the grub menu, and then the most recent recovery mode entry? That should open small submenu where you need to select "drop to root shell". If that works, you will be presented with a read-only root shell (command line). That allows you to remount as read-write and modify the fstab. Assuming you only need to comment out the entries in fstab, that could allow the system to boot.

Once in the root shell (if you get that far), to remount rw do:
```
mount -o remount,rw /
```

After that open fstab with nano:
```
nano /etc/fstab
```

Put # in front of the two lines for the data disks, then to save changes do Ctrl+O, Enter, Ctrl+X.

If the machine still can't boot, you can boot it with the desktop live CD and usb dvd-rom or usb stick. No need to buy dvd drives, you can use usb stick. But from the live CD there are further steps you will need to take to mount and read the root partition from the HDD. You are right, inside live mode the /etc/fstab is not the /etc/fstab from your HDD OS. It's from the live mode.

PS. Notice how the above commands don't have sudo in front. That's because you are working from a root shell. Otherwise system commands like those must have sudo in front.

---

### Post by agarwaldvk on 2016-11-15
Hi darkod


Thanks for your response. Mate, I am so sorry to have put you through this!

I will try these once I get home tonight. I did actually install Ubuntu on this PC using the USB stick (needed 2 of them from the link I followed to create the bootable USB) but I subsequently formatted both of them thinking that I wouldn't need them now! I will have to go through the process again, which I found quite tedious but nevertheless. If that has to be done, then I will do it. Is making a bootable disk and then installing it off it just as tedious? Just checking, I will first follow what you  have advised anyhow.

Hence, I will format the drive using the terminal command. I just thought that might as well use if I have got it and then it gives me a more definitive view that I am actually formatting the right drive.

Trying to mount all the drives in rw mode - what if this drive has issues since it came up with "input/output" error when I was trying to delete the partitions - if its not able to read this drive for whatever reason it won't allow me to mount it , would it! If the 2 drives are physically disconnected, obviously it won't see them. Would it still try to mount then as per the directives in the fstab file or will it ignore it and move on?

I was also wondering if I could actually take it out from that PC and then temporarily connect to another windows PC and format it in ext4 format - can we do that from windows?


Shall keep you posted.


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-16
Hi darkod


This is the latest update as at 7.51 pm Melbourne time.

I have been able to boot the machine as per your instructions, having physically disconnected the 2 drives beforehand . I have after reboot commented out the 2 lines for mounting the 2 drives from the fstab file.

I am not able to login.

Both these drives are pretty much identical in terms of size and brand - the model number of course is different.

So how do I now go about first connecting the good one and then connecting the other one and reformatting the empty one (currently the problematic one), copy the content from one to the other and then reformat the other  and so on.

Or can I just physically connect the 2 drives and not mount them at first and then try mounting one at time, is it?. What do I do - if this is the correct next step?


As a backup plan I did burn the disk with the iso image just in case I need to boot from it and reinstall the whole thing again but nevertheless!



Best regards


Deepak

---

### Post by darkod on 2016-11-16
Sorry, is that a typo? You say "I am NOT able to log in", but it sounds like you can now?

If you can log in, leave the disks commented out in fstab and connect them (both). Boot like that and it should boot correctly because the OS will not try to mount the disks (one of them has the partitioning messed up now).

You can see all disks/partitions listed in terminal with:
```
sudo parted -l (that's small L)
```

After you check which is the correct disk to format, we can create new partition table and new partition, and format it. Post the output of that parted command.

---

### Post by agarwaldvk on 2016-11-16
Hi darkod


Sorry for the delay - just got home!

Yes, that is a type. I am infact able to login.

Will this command 

sudo parted -l (that's small L)

tell me which disk has the partitions messed up?


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-16
Hi darkod


Sorry for the delay - just got home!

Yes, that is a type. I am infact able to login.

Will this command 

sudo parted -l (that's small L)

tell me which disk has the partitions messed up?


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-16
Hi darkod


So from the parted command output I can now tell that the /dev/sdv is the bad one!

At your convenience, just let me know how to we go about totally wiping everything on it and formatting it to ext4 format.

This is what I am looking at doing once of course this drive is correctly formatted :-

1. Copy the entire contents of the other drive on to this newly formatted drive
2. Format the other drive to ext4 after of course ensuring that the data from this drive has been fully and successfully copied over to the other drive and is accessible from windows machine
3. Hopefully then be able to get away by renaming these shares/drive appropriately to the data and media share as after formatting they would get interchanged.


Going to bed now!


Best regards


Deepak

---

### Post by darkod on 2016-11-16
Yes, it's dev/sdb.

To create new gpt table and partition:
```
sudo parted /dev/sdb   (that will open it in parted prompt)
unit MiB   (set display units to MiB)
print   (check again if that is the correct disk and how many total MiB it has capacity)
mklabel gpt   (new blank gpt table)
mkpart DATA 1 <end>   (the DATA is just a label for the partition, not relevant, use anything, the 1 is starting point 1MiB and for <end> use value just below the max capacity, I usually leave 10-15MiB free at the end)
quit   (quit parted, now you have created partition sdb1)
sudo mkfs.ext4 /dev/sdb1
```

The last command, outside parted, will format sdb1 with ext4.

After that it is ready to be mounted at the mount point you decided to use.

---

### Post by agarwaldvk on 2016-11-17
Hi darkod


So far so good. Following your instructions to the letter, I have been able to format the sdb drive in ext4 format. Checked it with parted command - which I will include in the post now.

Now I want to go back to where we were before all this happened, copying and moving files and formatting the other drive to ext4 format. To that end, I have so far 

1. created a directory "/sharedfiles"
2.created 2 sub-directories under it called "data" and "media"

Output from ls command after creating folders
agarwaldvk@MyHomeServer:~$ ls -ld /sharedfiles
drwxr-xr-x 4 root root 4096 Nov 17 18:09 /sharedfiles
agarwaldvk@MyHomeServer:~$ ls -l /sharedfiles
total 8
drwxr-xr-x 2 root root 4096 Nov 17 18:09 data
drwxr-xr-x 2 root root 4096 Nov 17 18:09 media


Now, I would like to mount the 2 drives that appear as "/dev/sda" and "/dev/sdb" at the "/sharedfiles/data" and "/sharedfiles/media" paths. To do that, can I just enter these commands :-


mount /dev/sdb /sharedfiles/media - this should be ok from what you has said earlier (we don't need to specify anything for ext4 partitions) as this is now formatted with ext4 format

What about the other one - this is the one that has 1.4 tb of data on an ntfs-3g partition.
do I need to mount it like so :-
mount /dev/sda /sharedfiles/data ntfs-3g defaults 0 0

Once both these drives are mounted, would I be able to copy files from /dev/sda (with ntfs format) to /dev/sdb (ext4) format from Windows PC or do I need to do from the server itself?

Whenever you get some time, if you could please advise me further, I can start the process, no hurry at all but I do not want to  proceed until I hear from you - I am too scared to stuff it up again.


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-17
Hi darkod


So far so good. Following your instructions to the letter, I have been able to format the sdb drive in ext4 format. Checked it with parted command - which I will include in the post now.

Now I want to go back to where we were before all this happened, copying and moving files and formatting the other drive to ext4 format. To that end, I have so far 

1. created a directory "/sharedfiles"
2.created 2 sub-directories under it called "data" and "media"

Output from ls command after creating folders
agarwaldvk@MyHomeServer:~$ ls -ld /sharedfiles
drwxr-xr-x 4 root root 4096 Nov 17 18:09 /sharedfiles
agarwaldvk@MyHomeServer:~$ ls -l /sharedfiles
total 8
drwxr-xr-x 2 root root 4096 Nov 17 18:09 data
drwxr-xr-x 2 root root 4096 Nov 17 18:09 media


Now, I would like to mount the 2 drives that appear as "/dev/sda" and "/dev/sdb" at the "/sharedfiles/data" and "/sharedfiles/media" paths. To do that, can I just enter these commands :-


mount /dev/sdb /sharedfiles/media - this should be ok from what you has said earlier (we don't need to specify anything for ext4 partitions) as this is now formatted with ext4 format

What about the other one - this is the one that has 1.4 tb of data on an ntfs-3g partition.
do I need to mount it like so :-
mount /dev/sda /sharedfiles/data ntfs-3g defaults 0 0

Once both these drives are mounted, would I be able to copy files from /dev/sda (with ntfs format) to /dev/sdb (ext4) format from Windows PC or do I need to do from the server itself?

Whenever you get some time, if you could please advise me further, I can start the process, no hurry at all but I do not want to  proceed until I hear from you - I am too scared to stuff it up again.


[SIZE=3]Just realized that I got the numbers wrong in the partitioning of the drive - instead of 1999985 as the end I wrote 1985 (MiB) and hence the partition is only 1.9 gb - can this be fixed easily either by reformatting or resizing the partition - I have noting on the drive yet![/SIZE]


Best regards


Deepak

---

### Post by darkod on 2016-11-17
Open it in parted again and delete the first partition with:
```
rm 1
```

After that recreate it with correct values and format it again.
I will reply to the other questions later, the commands you posted need small modifications.

---

### Post by agarwaldvk on 2016-11-17
Hi darkod


Just so that you have the full information before you respond. No worries at all. Take your time. You have been so great a help - I will forever remain indebted to you!

I resized the partition after googling a bit - hopefully correctly! I initially tried to do it via command line but wasn't so sure so used Gparted as they said online. That process looked reasonably safe to do. 

It said the maximum size that this partition could grow to was 1907727 MB - so I used that number. With that number there there was no space available after the partition.

It resized the partition successfully - output attached.

Currently coping some media files as a test from the other drive to this drive - about 100 gb. It that works I will copy the remaining data from the other drive to this one and then you will need to tell me how do I reformat the "sda" partition to ext4.

Once that is done, then we are nearly done except for the permissions bit! That will come later but I will try your instructions/advice from earlier posts.


Best regards


Deepak

---

### Post by darkod on 2016-11-17
Yes, that would be the fastest way to copy, locally... But after you copy all data you will probably need to modify all permissions recursively.

If you take a look, the owner of /sharedfiles is root:root, and the permissions are rwxr-xr-x. That means that no one except root has W permissions.

To give others W permission you can do:
```
sudo chmod -R o+w /sharedfiles/media
```

But if you do that now, it will do it only for current files, and the files you copy later will be again owned by root and without W permission for others. So I suggest to copy first, and then fix permissions. Or better yet, fix permissions at the end, when you have reformatted sda too and put the data files back to the data disk and the media files to the media disk. That way when you fix the permissions they will be correct, according to the files type.

For reformatting sda use the same procedure like for sdb.

---

### Post by agarwaldvk on 2016-11-17
Hi darkod


That sounds good!

Out of interest from the screenshot that I posted after resizing the partition, have I lost 200 Gb of space - because the output that the capacity is 1.8 Tb and used 176 K.

If that is the case, just wanted to know, howcome, because it did say that by taking end point of the partition to 1907727, there wouldn't be any space available after the partition - so what happened to the other bit...not that I am overly concerned about it but jutt...


Hopefully I should finish copying data by tomorrow morning, my time. For it to be visible over the network, do I only create a share just like my current share (obviously not getting used at the moment) and with the same permission - although, I do realize that they are too generous but just to ensure that these files have copied over OK and I can play and view them over the network.


Best regards


Deepak

---

### Post by darkod on 2016-11-17
No, you didn't lose space. When talking about disk space, you have to make a difference between something like this:
Disk manufacturers declare GB as 1000x1000x1000 bytes.
While true binary GB (or to make a distinction GiB) is of course 1024x1024x1024 bytes.

So, a disk of 2TB has in fact about 1.8TiB. And df -h shows the info in the binary form. You can say that the difference is more or less 10%. It was always like that, only that earlier with smaller disks it did not catch the eye so much. The same is true in windows. Format any disk as ntfs and it will never show 2TB space... (or depending what size it is, it will always be smaller for those 10%).

That's why I said to use unit MiB in parted, to be true megabyte in binary terms. You could have used MB too, which would be different measurement.

Yes, after you create a samba share that shares that folder, it will be visible to any client on the network...

---

### Post by agarwaldvk on 2016-11-20
Hi darkod


This is the latest update - pretty good, I think - thanks to a lot of patience and help from you!

I was finally able to transfer all of the 1.4 tb of data from the ntfs formatted partition to the ext4 formatted partition. I also tested if the files could be accessed and opened using any other PC on the network and using my WD Live TV box. All good!

I was also able to format that ntfs partition to ext4 partition.

The question that I now have is that this partition (share) that I copied all the data to formatted in ext4 format - whilst it has the permissions of 755, it could not be accessed from my Windows PC from within Windows Explorer - I could see the share but couldn't access it - it said permission denied. 755 should give anyone read and  execute acesss , shouldn't it? But because I had to do some testing to ensure that the files have been copied over correctly, I changed that access to 777, following which I was able to access it both from my Windows PC and from the WD Live TV box.

I would prefer that the settings for this share to be such that only myself, as the administrator, should be able to add/delete/modify files/folders from this share and everyone else should be able to read and open all the files without needing to enter any password - they are only music, photo and video files. How do we achieve this?

I have attached the outputs showing the permissions for the "media" share, the output from "parted" command and share configurations as they are now for your immediate reference.

I will talk to you about the permissions requirements for the other share - the data share later - once I am able to get this one right - this should be relatively easier to realize compared to the other one, I would think!


Best regards


Deepak

---

### Post by darkod on 2016-11-20
You have to be careful with samba shares and permissions, because there are separate linux filesystem permissions and separate samba permissions.

As I already mentioned, all parent folders of the mount point should cover the permissions of the below folders which means you also need to run something like:
```
sudo chmod 777 /sharedfiles
```

On the next folder level you will adjust the different permissions for the media files and the data files.

Also, in your smb.conf you have too many parameters that seem redundant. Like 'writeable' and 'read only'. And I believe the 'guest' parameter is not correct as it is, it should be 'guest ok'. In my public shares I only have:
```
guest ok = yes
read only = no
```

As for your other parameters, if you want the media files not to be writeable by all, you can use create mask of 777, that makes the files writeable to all. Use something like 775 or 755.

Also, why are you forcing user nobody on the media share? In such case, all will connect as nobody and if you create the files as nobody too, that means all will have rights to modify files because any user connecting will be considered the owner of the files.

I'm not real expert on all samba options because there are really lots of options that help you configure your samba in fine details... But I would start with something simpler, like using username/password to access the shares, and then just adjust little by little the exact options you want.

For example if your windows PC user didn't have access did you try setting up samba user identical to it, and check if that allowed access?

---

### Post by agarwaldvk on 2016-11-20
Hi


Thanks for your response.



First, I realize that there would be a lot of redundant parameters in my share configuration - that is because I didn't know any better then and I was desperately trying to get the share to be visible to the other devices on my network back then with the intent to later change them to suit desired requirements - I never got around to do that - got stuck with the other issues. Remember, I am an absolute novice with all this stuff. On a scale of 1 - 10, I am probably at 0.5. I am looking up to you all to get me start learning to do the right things.


So, I will do this later this evening

sudo chmod 777 /sharedfiles

Also, because I have already changed the permissions for /sharefiles/media to 777 last evening, I believe I should revert it back to 755 by

sudo chmod 755 /sharedfiles/media


Also, will it work the way I would like it to if I were to remove the following lines from my conf file:- 

read only = no
force user = nobody
create mask = 777

I will also correct the "guest = ok" entry to "guest ok = yes"


Do I need to change anything else to at least get this one working with everyone else able to access and execute files and myself to add/delete/modify files/folders in that share?



Best regards


Deepak

---

### Post by darkod on 2016-11-20
I don't think you need to change anything else. Try it and we'll see.

Also note that folder/file owner seems to be root (probably because you copied data using sudo), so 755 gives RW only to root, not to your linux user. Using sudo you will still be able to modify those files, but not using your standard linux user.

---

### Post by agarwaldvk on 2016-11-20
Hi darkod


Thanks again!

Then the linux user "agarwaldvk" (that's me) won't be able to write without using sudo, yeah.

From what I remember, this user's group is 'root' - I will check this when I get home this evening - and if it is so then if I were to change the permissions to 775 instead of 755 then this user would be able to write/read without having to use sudo, wouldn't it?



Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-21
Hi darkod


I tried addressing the permissions for the media share and it worked perfectly. Let me once again thank you profusely for all your assistance, persistence and support to get me to this point. You must be a very patient man! Greatly appreciated.

Now the only thing remaining is to get the permissions correct for the data share. I may have indicated that the idea is to have user specific folders (4 off) and 1 common folder. I can manage the permissions for the common folder - this is going the same as the media folder, no problems.

For the other user specific folders, I was wondering if this will work :-

1. Create these users as both Ubuntu/Samba users assigning them a password(s) as required - I will do some reading to find out how can I do this!
2. Create one (1) folder for each of these users - these would be named by the users' names - under the "/sharedfiles/data/" like so :-

"/sharedfiles/data/user1/" - for example

3. Change owner of these user specific folders to these specific users by issuing the following command :-

chown -R user1:user1 /sharedfiles/data/user1/

4. Assign a permission of 1700 recursively to the "/sharedfiles/data/" share - this is on my understanding (and correct me if you think I am wrong here and I may well be) that with the sticky bit enabled only the user (owner) and root can add/delete/modify files and folders under that share. So only the user "user1" and myself (user = agarwaldvk) as the administrator can add/delete/modify files and folders under that folder "/sharedfiles/data/user1/"


This way the share "/sharedfiles/data/" - which is not owned by any of the users by root,they wouldn't be able to add/delete/modify anything (files and folders) to the share itself  and to any other files/folder under it except their own, yeah?


Will this work?


Best regards


Deepak

---

### Post by darkod on 2016-11-21
Yes, it should work. Just to mention that at the start when a folder is empty you don't need to use -R (recursive). That is only when folder has data inside and you want to apply on all files/folders inside.

Also about the sticky I'm not sure about the 1700 command since I have never used it. When setting up group sticky bit I use g+s and for user sticky bit there is also the command chmod u+s so it might be more suitable if you want all files inside that folder to inherit the user owner. Test it out...

---

### Post by agarwaldvk on 2016-11-21
Hi


Thanks.

Makes sense about the -R on empty folder - wouldn't do any good, would it? You are right, there is noting there in the folder anyway!

Will try that tonight.

By the way, what does the 's' stand for in the 'g+s'. I know 'g' stands for group.

Don't worry about it - just googled about it! Sorry, should have checked before asking!




Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-22
Hi darkod


I changed the permissions on a user specific folder for user 'aratideepak' as shown in the attachment but I am not able to connect to this folder.

The command issued was :-

sudo chmod -R 5770 /sharedfiles/data/aratideepak                (This I understand is the same as what you were suggesting u+s and g+s)

I can see the folder in Windows Explorer but when I try to access it, it says 'Windows cannot access this folder' rather than coming up with the dialog box requesting for user credentials. What needs to happen so that when I am trying to access this folder, it comes up with the dialog box requesting for user credentials?


Best regards


Deepak

---

### Post by darkod on 2016-11-22
I don't know about -R 5770, why didn't you simply use u+s or g+s? And it's not u+g, but either u+s (to set sticky bit to user) or g+s (to set sticky bit to group).

Also it can be related to samba share options, depends how you have this share declared. I assume there is a samba user with this identical username, right?

Try giving others read only access to the folder, to see if you can access it that way. If you can, the linux permissions need investigation. If you still can't, the samba share options probably. You can give others read only on a folder with o+rx. You don't need -R, just try the top folder if you can open it. I don't like using +x with -R because that also makes all files executable recursively.

---

### Post by agarwaldvk on 2016-11-22
Hi


Thanks for your response. Let me try it again as per your instructions and see what happens. I will come back shortly!


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-22
Hi darkod


OK, this is what I did and this is what I get.


I issued

sudo chmod u+s /sharedfiles/data/aratideepak

Then

sudo chmod 775 /sharedfiles/data/aratideepak

With these, the permissions are as follows :-

agarwaldvk@MyHomeServer:~$ ls -ld /sharedfiles/data/aratideepak
drwsrwxr-x 2 aratideepak aratideepak 4096 Nov 22 20:03 /sharedfiles/data/aratideepak

I can now access it from windows pc but I cannot modify anything in that folder.

The samba share configurations are as follows :-

[datafiles]
path = /sharedfiles/data
browsable = yes
writable = yes
guest ok = yes
public = yes
guest account = nobody
admin users = agarwaldvk

There is a Ubuntu user called 'aratideepak' and a samba user by the same name and password created like so :-

adduser -a aratideepak

smbpasswd -a aratideepak

password provided when requested for!

I still do not get the dialog box to enter credentials to authenticate the user - which I thought Windows would present when read only access is provided all but write access to specific user.

Does it give you any more clues?


Best regards


Deepak

---

### Post by darkod on 2016-11-22
I thought you want the data share to be only for authenticated users. Why do you leave guest ok and public parameters on it? Also this might be why you are not getting login screen. And if your windows username is identical to the linux username, it will not ask you for credentials, it uses the windows ones automatically.

Now that you can open the folder, check the permissions of the folders and files in it. Because the latest chmod 775 was not run recursively, permissions of files and folders inside might be different. And the owner too...

So go few levels inside, and check ownership and permissions.

With the guest ok and public, you might be actually accessing it as guest user, and because others have Read only access, it allows you to read files but not modify.

---

### Post by agarwaldvk on 2016-11-22
Hi


I just commented out the lines in the smb.conf for guest ok, guest account and pubic and restarted both smbd and nmbd services and now I can't even access the /sharedfiles/data folders. The permissions on both the folders

/sharedfiles/
/sharedfiles/data.

are 777

The linux and samba login for this user is the same. The windows login that I am using is mine - this is different to the user that we trying to access the folder for (aratideepak)

agarwaldvk@MyHomeServer:~$ ls -ld /sharedfiles/data
drwxrwxrwx 3 root root 4096 Nov 22 20:03 /sharedfiles/data
agarwaldvk@MyHomeServer:~$ ls -ld /sharedfiles/data/aratideepak
drwsrwxr-x 2 aratideepak aratideepak 4096 Nov 22 20:03 /sharedfiles/data/aratideepak


conf file share configurations
[datafiles]
path = /sharedfiles/data
browsable = yes
writable = yes
#guest ok = yes
#public = yes
#guest account = nobody
admin users = agarwaldvk


After changing the conf files to retain the public = yes allows me to read only access the "\sharedfiles\data\aratideepak" folder but I can't edit it and it doesn't ask for credentials.

Not sure if this helps you at all but it must have something to do with the windows permissions rather than folder permissions in Ubuntu, doesn't it?





Best regards


Deepak

---

### Post by darkod on 2016-11-22
See if something like this can help you:
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)
[https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html)

---

### Post by agarwaldvk on 2016-11-23
Hi darkod


Mate, I tried everything I could but nothing seems to work. The only thing I haven't done is to add this line (I believe that this is to be added in the global section - or is it to added to each of the individual share section???) in the smb.conf file :-

security = user

because my understanding is that this is the default setting.

I also see that in my media share, no one including myself can modify any folder from within Windows Explorer. Whilst my Ubuntu server machine is on, no one is logged on it as such.

The owner and group of /sharedfiles/, /sharedfiles/data. /sharedfiles/media is root and root. So, do I need to enable 'root' although everyone says that it is almost never necessary to do do? So how do I connect to the server from within Windows Explorer as a certain Ubuntu user from a Windows machine if I am logged on to this Windows machine as a certain user regardless of whether or not this username is same as the Ubuntu user? If I am trying to access a certain folder on the Ubuntu machine, shouldn't it ask me for credentials if whatever login it currently uses to authenticate this connection doesn't match the folder permissions? I somehow don't get this login request - it just tells me that I don't have access to it.


The other thing is that :-

do I need to install "libpam-winbind" and also then specify 'guest ok = no' in each of the share definitions? 


Best regards



Deepak

---

### Post by darkod on 2016-11-23
Since you want user logins, I would put the
security = user

in the global section. It goes there, not in the share sections.

I would also change the owner and group to be your username/group on all the shared folders (and parents). When creating folders with sudo mkdir it puts root by default, but you should change it later to your name for example. That's why I always mention, it's not just permissions, you need to adjust ownership too because only in combination with that permissions make sense. Especially when not giving full write rights to everyone.

According to that samba info try installing the libpam-winbind package and specify the guest ok = no on the data shares (because you don't want guest access there). Give that a shot too...

There are many many tutorials for samba and examples on he internet. Very often you will have to take bits and pieces from various examples to make it work for your needs.

---

### Post by agarwaldvk on 2016-11-23
Hi darkod


Thanks for your explanation. I will now try and give it a go first without installing libpam-winbind - I will install that after trying the other options that you have recommended.

I will change the ownership of the folders '/sharedfiles', '/sharedfiles/media' and '/sharedfiles/data' to 'agarwaldvk (this is the user that would operate as admin).

For the group, how do I assign root permissions to user 'agarwaldvk' - is there a group that is already available in Ubuntu that has root access by default I can made this user a part of? I will try and find this out myself  as well but just in case I may not succeed.

I think I have got it - could you please confirm if I am on the right track - either add 'agarwaldvk' to the group 'admin' or create a new group with admin privileges in the '/etc/sudoers' file. I will try the first option first.

Best regards


Deepak

---

### Post by darkod on 2016-11-23
You can change the group ownership too with chown or chgrp. chgrp changes only the group while chown can change both in format chown username:groupname.

By default, a group identical to your username is also created. So, you can change ownership with something like:
```
chown -R agarwaldvk:agarwaldvk /sharedfiles
```

Don't forget that if you run that it will change ownership of all files and folders. Instead you can run three separate commands for different folders which ownership you want to change.

About user root (sudo) permissions, the first user created already has them. For other users, if needed, you can simply add them to the sudo group running the command as a user that already has sudo rights:
```
sudo usermod -aG sudo <username>
```

After that the user <username> will be able to run sudo system commands.

---

### Post by agarwaldvk on 2016-11-23
Hi darkod


That was exactly what I was about to point out. Before I tried what you had recommended last evening, I wanted to check the existing groups and users and, to my surprise I found that I had 'agarwaldvk' and 'aratideepak' both as users and as groups. I thought that was weird but that has now been clarified. Also, in the 'sudoers' file, I noted that there was group called 'admin' shown as '%admin' with the 'ALL...' access privileges but in the groups listing it didn't have a group called 'admin' although it did show a group by the name of 'adm' - isn't that a problem? Also, I found that both 'root' and 'agarwaldvk' were in the 'adm' group as users.

Was this  because this was the first user created when I installed Ubuntu or because I specified 'admin users = agarwaldvk' in the share definitions?

I also saw a group called 'sudo' in the 'sudoesr' file. I was thinking that I will actually make 'agarwaldvk' a part of the 'sudo' group and proceed  from there. Hopefully it will get me there.

Just as an FYI, I was looking at adding 'agarwaldvk' to the 'sudo' group and then runing the chown command without the -R option separately 3 times once each the 3 folders '/sharedfiles', '/sharedfiles/data' and 'sharedfiles/media'  like so :-

sudo usermod -aG sudo agarwaldvk

and then this :-

chown agarwaldvk:sudo /sharedfiles
chown agarwaldvk:sudo /sharedfiles/data
chown agarwaldvk:sudo /sharedfiles/media
 


Once the is done, with the with the ownership and permissions of the folders that I (with your extensive help) now have given, do you think that I would be presented with the dialog box requesting for fresh credentials if I am logged on as a certain user on a certain windows PC and trying to access and modify a particular folder on the Ubuntu server that is owned by a specific Ubuntu/Samba user other than the folder owner?  Of course, I will soon find out when I try it out this evening but who know it mightn't because I might have make a mistake and not because it wasn't supposed to - that's why I am asking!


Best regards


Deepak

---

### Post by agarwaldvk on 2016-11-24
Hi darkod


I am trying to chown agarwaldvk:sudo /sharedfiles/media and it comes up with operation not permitted error. I have already added agarwaldvk to sudo group.

What can I do?

[SIZE=3]Edit
I don't think its working for me - there is nothing that I can now that will allow me to access the 'aratideepak' folder from windows explorer to modify it - no matter what I do. I am almost at the point of giving up! I think you need to be an Einstein to be able to work this! I will have to work with 777 permissions for all folders - nothing else seems to work!

Sorry for the trouble that I have caused you. This stuff is obviously not for me![/SIZE]


Best regards


Deepak

---

### Post by darkod on 2016-11-24
Go back and check the chown in my post #46. I never said to chown to sudo group. Just use your group/username. You don't chown to sudo as far as I know, you don't use sudo like that.

As for the rest, what ownership do you have on the data folders? It's probably needed to have ownership of username:agarwaldvk because the folder and files need to belong to the respective user but they also need to belong to your group (to administer them). If you put 775 permissions on that, it will give RW to the owner, RW to you and read-only to the rest. Something like that...

Sorry it's not working as you expect it, but as I said, there are many different setups and it's not always easy to get it right... You need to separate it into smaller bits and work it out one by one. Try following the path of the traffic how will it go, and check the ownership and permissions on each point.

---

### Post by agarwaldvk on 2016-11-24
Hi darkod


Sorry about my frustrations. Mate, I am genuinely trying and trying very hard. Every waking free moment I am either thinking how to get it working or trying to make it work. Believe me, I want to learn to make it work.

I will try it again!


Edit :-
I have changed the ownership for the parent folder '/sharedfiles' and for both the sub-folders '/sharedfiles/data' and 'sharedfiles/media' to agarwaldvk:agarwaldvk
I have also now created a new folder called 'aratideepak' as a sub-folder under '/sharedfiles/data/' folder - at the moment the ownership of this sub-folder is also agarwaldvk:agarwaldvk. The permission on this folder is 775. With this current permissions and ownership, I cannot modify this folder at all from my windows pc. I am logged in on my windows PC with user id of 'agarwaldvk' - it says it requires permission for me to modify this folder (aratideepak) but doesn't bring up the credentials entry dialog box.

As it so happens that my windows user id on my windows machine, my ubuntu first user id and samba user id are all 'agarwaldvk'. 

Do I need to change the user to 'aratideepak' for this folder as it already has 'agarwaldvk' as the group?




Best regards


Deepak

---

### Post by darkod on 2016-11-24
No, you would need to change the user... As member of the group you should have access even if your user was not owner of that folder (which it is right now).

Did you try adding the libpam-winbind package as suggested? You said you will leave it for later, but the description in those links actually said that is the package allowing correct authentication of the samba and linux users. Maybe that's what you are missing?

---

### Post by agarwaldvk on 2016-11-24
Hi darkod


Getting somewhere after all.

Yep, you are correct - I did change the  user to 'aratideepak' with the group as 'agarwaldvk' (that's me, the administrator). With that, in my windows machine where I am logged in as 'agarwaldvk', it allowed me to modify the folder, no problems. I also logged in as some other windows user on another windows pc and whilst I could browse the 'aratideepak' folder I couldn't modify it, which means that I am half way there. I now just need to restrict users other than the folder owner and the administrator from being able to browse the same. To that end, I am thinking to change the permissions of this folder from 775 to 770 - hopefully that might work.

It nonetheless doesn't bring up the credentials dialog box anyhow!

So tomorrow, I will try and change the permissions of this folder and see what happens.

Also, I will try and install libpam-winbind - I really don't know what that does but I will try and see what happens.


Best regards


Deepak

---

### Post by darkod on 2016-11-24
I think that is samba standard behavior, or rather said windows. It sends its login with the request.

If it matches a user in linux/samba, it doesn't ask you for credentials, it just looks what that user can or cannot do.

I think maybe it asks you for credentials only if the windows user does not exist in samba. Maybe then it asks you which username you want to use to connect.

---

### Post by agarwaldvk on 2016-11-25
Hi darkod


This seems to now work. This is what I have done :-

1. Create these specific users as Ubuntu users and then add them to Samba with their passwords
2. Create their user specific sub-folders under the '/sharedfiles/data/' folder
3. For each of these users run the command chown <username>:agarwaldvk <user specific folder path>
4. For each of these users run the command chmod 770 <user specific folder path>

Then on their Windows machine, get them to create a Windows user to match their Ubuntu/Samba user and password. Apparently, the way it works is that when you try and access a Ubuntu folder with restricted permissions, it will use the windows user's login and try and authenticate user credentials. It will only bring up the credential dialog box if you are logged in Windows PC as an user without a password. So that is good and seems to work the way I expect it to work.

With reference to libpam-winbind, I don't think that is relevant in my case as from what I understood that is applicable when you have AD - which in turn is relevant in the context of a domain based server and mine isn't. Apparently you can have a standalone server set up as domain server with AD but you have then configure DHCP etc etc that I do not know anything about and more than likely don't need it for my home setup. I don't intend to have a career in corporate network administration.

My interest was always with reference to providing a nearly always available single source of data for the family (with reasonable degree of user access and privacy restrictions) with an accepatable sort of backup facility to prevent data loss.

This has taken me to the point of providing the first. Hopefully, I might be able to set up the backup facility using Bacula - some others are helping on that count.

Once again, please accept my most sincere thanks and great appreciation for your knowledge, patience and persistence in helping me out.

Words fail me but be it known that I feel almost indebted to you for all your assistance getting me have a better understanding and appreciation of this system to the extent that I now have - although I do realize that I still have a veeeeerrrrrrrry long way to go.

I am hopeful that you would be able to assist me with my futures posts - there would at least one more coming in the context of "replacement of an existing internal drive full of data with another of bigger capacity" retaining all file/folder/drive permissions and identifiers so that no or as little as possible changes need to be made so that all existing systems work as they are!




Best regards


Deepak

---

### Post by darkod on 2016-11-25
You are welcome, glad it works now as you want it. If you are happy with it, you can mark the thread as Solved in Thread Tools above the first post. It helps others too...

---

