---
title: "HOWTO: Resize the WUBI virtual disk"
date: 2010-11-19
forum: Tutorials
---

### Post by bcbc on 2010-11-19
The information in this thread has been moved to [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012404](http://ubuntuforums.org/showthread.php?t=2012404)

Thread closed.

[COLOR="Blue"]**This HOWTO has been moved to community-maintained Wikis**[/COLOR]: 
[ResizeandDuplicateWubiDisk]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk")
[ResizeWubiDisk]("https://help.ubuntu.com/community/ResizeWubiDisk")

For the reason why, see [here]("http://ubuntuforums.org/showthread.php?t=1949027").
=============================================================

This HOWTO describes how to resize a Wubi virtual disk. There are two distinct techniques.

The first, described here, is not strictly a resize, but rather a duplication to a larger virtual disk. E.g. if you have a 7GB root.disk, and you want to make it 10GB you need 10GB of free space (plus leave enough for Windows). This is safer than attempting to expand the current root.disk. 
This technique must be run from within the booted Wubi install.

The second technique is a true resize, which must be performed from a live CD. This is much faster and can make better use of the available space. See [post #2]("http://ubuntuforums.org/showpost.php?p=10590851&postcount=2") for details. 

**_Automated resize_**
Download the attached file **wubi-resize_1.5b.sh** and save it to your Downloads directory.
The rest of the resize is run from the Terminal:

For usage instructions:
```
bash wubi-resize_1.5b.sh --help
```To create a new [COLOR="Red"]10[/COLOR]GB virtual disk:
```
sudo bash wubi-resize_1.5b.sh [COLOR="red"]10[/COLOR] 
```After the script is completed it will instruct you to reboot into windows, rename the file \ubuntu\disks\root.disk to \ubuntu\disks\OLDroot.disk and then ename the file \ubuntu\disks\new.disk to \ubuntu\disks\root.disk
Do not delete the OLDroot.disk until you have confirmed the new root.disk is working (or keep OLDroot.disk as a backup).

Note: the script will merge separate virtual disks into a single virtual disk and automatically adjust /etc/fstab accordingly. If this is not desired, use the manual method. The script limits the size of the new virtual disk to 32GB. Please refer to the usage instructions for options if you require a larger size (although I would recommend migrating to a normal install if this is the case).

How long does it take?:
To create a 5GB disk from a freshly installed Ubuntu on my machine, "dd" takes 4 minutes, "mkfs" takes 9 seconds, and "rsync" takes 6 minutes. On an older install with lots of files or a fragmented partition, the rsync will take a lot longer.

New with version 1.5b is the *--resume* option. You can use this if the initial resize failed to complete normally due to an rsync copy error e.g. file corruption. After fixing the corruption rerun with this option.
It can also be used to keep an up to date copy of the root.disk (it synchronizes the new.disk with the current install).

**Known issues**:
1. None. 

**NOTE**: the root.disk is a single file stored on the /host partition. There is a higher risk storing data within this file and I strongly recommend maintaining regular backups. Also [avoid hard shutdowns]("https://wiki.ubuntu.com/WubiGuide#Warning") that can lead to filesystem corruption.

CREDIT... I used the LVPM guide by Gena Kovaks and the scripts by Agostino Russo from the Wubi guide (and lupin package) as reference material.

The code is now hosted on GitHub. You can keep track of new development or contribute. See [https://github.com/bcbc/Wubi-resize](https://github.com/bcbc/Wubi-resize)


**_Manual resize_**
For those interested, I've included the commands to perform the resize manually.
[COLOR=Red]WARNING[/COLOR]... the commands "dd" and "mkfs" are **very dangerous** if used incorrectly (they can destroy all the data on your computer). It is recommended to use the automated resize (the attached script) as there are additional checks and safeguards against errors.

Please ensure you have enough space for the new virtual disk before proceeding. E.g. for a 10GB disk you'll need 10GB free as well as enough space for Windows to operate. Do not use this if your /host is a FAT32 partition.

1. Unmount any partitions that are not mounted under /host or /media. (e.g. sudo umount /windows )

2. Run all commands as root; check free space on /host
```
sudo -i
df -h /host
```3. Create a new virtual disk of e.g. [COLOR=red]10[/COLOR]GB (10,000 MB)
   change count= parameter as appropriate.
```
cd /host/ubuntu/disks
dd if=/dev/zero of=new.disk bs=1MB count=[COLOR=Red]10000[/COLOR]
```4. Format the disk with the ext4 file system
```
mkfs.ext4 -F new.disk
```5. Mount and copy files to new virtual disk
```
mkdir -p /media/newdisk
mount -o loop new.disk /media/newdisk
rsync -av --exclude '/sys/*' --exclude '/proc/*' --exclude '/host/*' --exclude '/mnt/*' --exclude '/media/*/*' --exclude '/tmp/*' --exclude '/home/*/.gvfs' --exclude '/home/*/.cache/gvfs --exclude '/root/.gvfs' --exclude '/var/lib/lightdm/.gvfs' / /media/newdisk
umount /media/newdisk
exit
```6. You're done!
Reboot into windows, rename the file \ubuntu\disks\root.disk to \ubuntu\disks\OLDroot.disk
Rename the file \ubuntu\disks\new.disk to \ubuntu\disks\root.disk
Reboot back into Ubuntu -- only delete the OLDroot.disk if you are sure it worked.

NOTE: if you have previously created separate virtual disks e.g. for /home, this process will merge /home back into the new virtual disk. That means you need to remove the separate entry for /home from your /media/newdisk/etc/fstab (before the umount command)  (or change the rsync command to **--exclude '/home/*'** altogether). 

If you are ready to resize you might also consider [migrating the Wubi install to a normal dual-boot (to partition)]("http://ubuntuforums.org/showthread.php?t=1519354").

---

### Post by bcbc on 2011-03-23
The first post shows how to 'resize' the virtual disk *while* running Wubi. This has the advantage that it can be run from within the Wubi install, plus it creates a new root.disk so you automatically have a backup. And since there is a script, it is simpler and has some built in safeguards and error checks.

There is an alternative method I've found out about (thanks to [ Trooper_Max]("http://ubuntuforums.org/showpost.php?p=10517590&postcount=19")).  This is a true resize and may be the only option if you simply don't have the room to duplicate the root.disk. While I have tested this a number of times - please make a backup of the root.disk first to be safe.

Note that FAT32 partitions have a maximum file size limit of 4GB, so this likely won't be of much use.

_**In place Resize of root.disk**_

1. You have to boot from a live CD/USB. This won't work while running Wubi.

2. Backup the root.disk

3. Mount the NTFS partition that your root.disk is on (this example assumes it's **/dev/sda1** and the mountpoint is [COLOR="Blue"]/media/win[/COLOR] - adjust accordingly in the following instructions):
```
sudo mkdir -p [COLOR="blue"]/media/win[/COLOR]
sudo mount **/dev/sda1** [COLOR="blue"]/media/win[/COLOR]

```3.i. Check the size of the root.disk (not required)
```
du -h --apparent-size [COLOR="blue"]/media/win[/COLOR]/ubuntu/disks/root.disk
```4. Run fsck on the root.disk
```
fsck -f [COLOR="blue"]/media/win[/COLOR]/ubuntu/disks/root.disk
```5. Resize - specify the desired final size (this example resizes to **10** GB)
```
resize2fs [COLOR="blue"]/media/win[/COLOR]/ubuntu/disks/root.disk **10**G
```6. Reboot back into Wubi Ubuntu

---

### Post by Rubi1200 on 2011-03-23
Excellent stuff bcbc and thanks for sharing this information with us.

---

### Post by Sidner on 2011-03-25
I got this when I used the script:

```
seltor@ubuntu:~$ sudo bash wubi-resize_1.3b.sh 20
[sudo] password for seltor: 
wubi-resize_1.3b.sh: A new virtual disk of 20 GB will be created. Continue?
y
wubi-resize_1.3b.sh: Creating new virtual disk (new.disk)...
wubi-resize_1.3b.sh: Formatting new virtual disk as ext4.
wubi-resize_1.3b.sh: Copying files - this will take some time.
wubi-resize_1.3b.sh: Please be patient...
wubi-resize_1.3b.sh: Copying files failed or was canceled
wubi-resize_1.3b.sh: Please wait - cleaning up...
wubi-resize_1.3b.sh: Operation aborted
```

---

### Post by bcbc on 2011-03-25
> **Sidner said:**
> I got this when I used the script:

```
seltor@ubuntu:~$ sudo bash wubi-resize_1.3b.sh 20
[sudo] password for seltor: 
wubi-resize_1.3b.sh: A new virtual disk of 20 GB will be created. Continue?
y
wubi-resize_1.3b.sh: Creating new virtual disk (new.disk)...
wubi-resize_1.3b.sh: Formatting new virtual disk as ext4.
wubi-resize_1.3b.sh: Copying files - this will take some time.
wubi-resize_1.3b.sh: Please be patient...
wubi-resize_1.3b.sh: Copying files failed or was canceled
wubi-resize_1.3b.sh: Please wait - cleaning up...
wubi-resize_1.3b.sh: Operation aborted
```

The copy command is supposed to output the reason for the failure. The only time it didn't for me was when I canceled it manually (CTRL+c).
You could try the --verbose option, and see if rsync (the command used to copy) provides more detail about the error.

---

### Post by ryanh06 on 2011-05-13
Thanks dude. Technique 1 worked beautifully for me the other day. Thanks for the easy to understand commands. Cheers :P

---

### Post by bcbc on 2011-05-13
> **ryanh06 said:**
> Thanks dude. Technique 1 worked beautifully for me the other day. Thanks for the easy to understand commands. Cheers :P

Great, you're welcome! Thanks for the feedback.

---

### Post by guyknt on 2011-05-19
post [#2] worked great (i think), something is a bit wrong with the display but im not sure its because of this... :)

---

### Post by bcbc on 2011-05-19
> **guyknt said:**
> post [#2] worked great (i think), something is a bit wrong with the display but im not sure its because of this... :)

hmm... it seems unlikely. The root.disk is like a partition. If it failed I'd expect it to result in file system corruption, not display changes. What sort of changes are you seeing?

---

### Post by bluszcz on 2011-05-23
> **bcbc said:**
> [COLOR=Red]EDIT[/COLOR]
```
cd /host/ubuntu/disks
dd if=/dev/zero of=new.disk bs=1MB count=[COLOR=Red]10000[/COLOR]
```3.



This is faster :popcorn: :


```
dd if=/dev/zero of=new.disk bs=1MB seek=1000 count=1
```

---

### Post by bcbc on 2011-05-23
> **bluszcz said:**
> This is faster :popcorn: :


```
dd if=/dev/zero of=new.disk bs=1MB seek=1000 count=1
```

That creates a sparse disk that's really only 1MB in size. The actual size increases as you use more space. But that can lead to excessive fragmentation and I see that as a risk to the stability of the wubi install.

You can see the difference if you run:
```
du -h new.disk
du -h --apparent-size new.disk
```

---

### Post by ajaybhat999 on 2011-05-26
Thank you very Much :o
It worked on my system....
I increased the size from 5GB to 10GB...:P

---

### Post by bcbc on 2011-05-26
> **ajaybhat999 said:**
> Thank you very Much :o
It worked on my system....
I increased the size from 5GB to 10GB...:P

Great! You're welcome :)

---

### Post by pfbray on 2011-06-12
I just get this when I try to do the auto method (No.1)
```
 bash: wubi-resize_1.3b.sh: No such file or directory

```

---

### Post by bcbc on 2011-06-12
> **pfbray said:**
> I just get this when I try to do the auto method (No.1)
```
 bash: wubi-resize_1.3b.sh: No such file or directory

```

Most likely you saved it to your Downloads folder. By default terminal opens in your home folder.
```
cd Downloads
bash wubi-resize_1.3b.sh --help
```

See if that works, otherwise determine where you saved it and change to the appropriate folder.

---

### Post by pfbray on 2011-06-13
> **bcbc said:**
> Most likely you saved it to your Downloads folder. By default terminal opens in your home folder.
```
cd Downloads
bash wubi-resize_1.3b.sh --help
```

See if that works, otherwise determine where you saved it and change to the appropriate folder.

Thanks for that! My next problem! Attempting the resize comes up with this:
```
philip@ubuntu:~/Downloads$ sudo bash wubi-resize_1.3b.sh 100
[sudo] password for philip: 
wubi-resize_1.3b.sh: /host/ubuntu/disks/new.disk already exists

```

---

### Post by bcbc on 2011-06-13
> **pfbray said:**
> Thanks for that! My next problem! Attempting the resize comes up with this:
```
philip@ubuntu:~/Downloads$ sudo bash wubi-resize_1.3b.sh 100
[sudo] password for philip: 
wubi-resize_1.3b.sh: /host/ubuntu/disks/new.disk already exists

```

The script creates this file when it duplicates the existing virtual disk(s). Usually, if the script fails it also cleans up and deletes this file (but if it already exists it won't delete it). If you've not run the script before then you might have created it through some other means.

If it's the result of running this script you can just delete it and rerun. If you're not sure what it is, check the time and date it was created or the size - this might give some clues. Browse to /host/disks in the file browser (e.g. nautilus) or from the terminal:
```
nautilus /host/disks
```

PS if you still can't figure out what it is you can always rename it and continue, or even try to mount it and see what is on it. Let me know if you need help with this.

---

### Post by zellyman on 2011-06-22
Resized from 10g to 100g in a bit less than an hour.  Probably should add the --max-override bit to the error for trying to resize more than 32gb (I didn't see it til I went into the script to change it), but otherwise: Well done,  Thanks for the script :D

---

### Post by bcbc on 2011-06-22
> **zellyman said:**
> Resized from 10g to 100g in a bit less than an hour.  Probably should add the --max-override bit to the error for trying to resize more than 32gb (I didn't see it til I went into the script to change it), but otherwise: Well done,  Thanks for the script :D

You're welcome!

I'm still a little undecided about the --max-override option as I'm not sure as to all the reasons the wubi designers decided to limit installs to 30GB max. Please provide feedback if you run into any issues with such a large root.disk. 

In the meantime I'll add back a comment regarding the *--max-override* option to post #1 (it was there initially, but I removed it during a recent rewrite).

PS. I'll also add an "Issue" to the git project to update the message text on a future release.

---

### Post by LLFz on 2011-07-04
I changed mine from 6 GB to 20 GB and I've been on &quot;copying files - this may take some time&quot; for around 1.5 hours (EDIT: Made that 10+ hours!!). :S Thanks for the tut though :D

---

### Post by bcbc on 2011-07-04
> **LLFz said:**
> I changed mine from 6 GB to 20 GB and I've been on &quot;copying files - this may take some time&quot; for around 1.5 hours (EDIT: Made that 10+ hours!!). :S Thanks for the tut though :D

I think something has gone wrong :p If you only started with 6GB then you'll have less than 6GB to copy - so you shouldn't wait any longer. Hit CTRL+c to cancel. Then remove the /host/ubuntu/disks/new.disk and try again, but this time use the --verbose or -v option. It will show the progress of the copy.

Also, make sure that you have unmounted any partitions that are not mounted under /media (or /host). e.g. if you have a custom mountpoint like /mydata or /win etc. (That's also mentioned in the known issues list)

---

### Post by scottcrumpler on 2011-07-08
Hi guys,

I'm try to execute the automated method mentioned here, but when I enter the command in the terminal, it asks for my password, then just returns to the command prompt.  No error message; nothing.  I've saved the script in Downloads, and that's where I'm running the sudo bash command.  Any ideas what's wrong here?


Thanks,
Scott

---

### Post by bcbc on 2011-07-08
> **scottcrumpler said:**
> Hi guys,

I'm try to execute the automated method mentioned here, but when I enter the command in the terminal, it asks for my password, then just returns to the command prompt.  No error message; nothing.  I've saved the script in Downloads, and that's where I'm running the sudo bash command.  Any ideas what's wrong here?


Thanks,
Scott

Please copy and paste the terminal contents so I can see the full command you entered. Thanks

---

### Post by ashton93 on 2011-07-13
The is the msg i am getting:

> 
du -h --apparent-size /media/win/ubuntu/disks/root.disk
du: cannot access `/media/win/ubuntu/disks/root.disk': No such file or directory
:confused:

---

### Post by bcbc on 2011-07-13
> **ashton93 said:**
> The is the msg i am getting:


du -h --apparent-size /media/win/ubuntu/disks/root.disk
du: cannot access `/media/win/ubuntu/disks/root.disk': No such file or directory
:confused:

With this method, you are running from a live CD environment, not your actual wubi install. Then you have to identify and mount the partition that contains the root.disk.

e.g. in my case it's /dev/sda3 (change it for your own)
so you would type:
```
sudo mkdir -p /media/win
sudo mount [COLOR="RoyalBlue"]/dev/sda3[/COLOR] /media/win
```

(first command created the mountpoint, if it didn't already exist. Second command mounts the partition containing the root.disk)

Then, 
```
du -h --apparent-size /media/win/ubuntu/disks/root.disk
```

Please explain in detail all steps you are taking so that I can figure out what the problem is. Thanks

---

### Post by tweek666 on 2011-07-26
```
tweek@ubuntu:~/Downloads$ bash wubi-resize_1.3b.sh 30
wubi-resize_1.3b.sh: Admin rights are required to run this program.
tweek@ubuntu:~/Downloads$ 


```

Help?!? I am the admin account, and it didnt even ask for password...

---

### Post by bcbc on 2011-07-26
> **tweek666 said:**
> ```
tweek@ubuntu:~/Downloads$ bash wubi-resize_1.3b.sh 30
wubi-resize_1.3b.sh: Admin rights are required to run this program.
tweek@ubuntu:~/Downloads$ 


```

Help?!? I am the admin account, and it didnt even ask for password...

Try:
```
sudo bash wubi-resize_1.3b.sh 30
```

With Ubuntu you run with normal user privileges, but can elevate it to root as required with "sudo". See [here]("https://help.ubuntu.com/community/RootSudo")

---

### Post by tweek666 on 2011-07-26
> **bcbc said:**
> Try:
```
sudo bash wubi-resize_1.3b.sh 30
```

With Ubuntu you run with normal user privileges, but can elevate it to root as required with "sudo". See [here]("https://help.ubuntu.com/community/RootSudo")

that worked, thanks alot!

---

### Post by bcbc on 2011-07-26
> **tweek666 said:**
> that worked, thanks alot!

Great! You're welcome.

---

### Post by tweek666 on 2011-07-27
> **bcbc said:**
> ]After the script is completed it will instruct you to reboot into windows, rename the file \ubuntu\disks\root.disk to \ubuntu\disks\OLDroot.disk and then ename the file \ubuntu\disks\new.disk to \ubuntu\disks\root.disk
Do not delete the OLDroot.disk until you have confirmed the new root.disk is working (or keep OLDroot.disk as a backup).


How do i do this??

NEVERMIND, I FOUND OUT,SORRY FOR BEING A NEWB, BUT IM LEARNING FAST.

---

### Post by bcbc on 2011-07-30
> **rongden said:**
> thank you very much . It's very useful :)

You're welcome :)

---

### Post by eros_1983 on 2011-08-10
Thank you very very very much... \\:D/=D>

---

### Post by bcbc on 2011-08-10
> **eros_1983 said:**
> Thank you very very very much... \\:D/=D>

No prob :)

---

### Post by jhatto on 2011-08-11
Hi I am sorry to be so ignorant but I hoped never to get back into Windows but I have had problems trying to use USB-ModeSwitch Wans when abroad, so I thought I would hang on to this new copy of Windows 7 until the ModeSwitching under Ubuntu is more reliable. My question is that I can not get Windows to show me the root.disc.  It is some years since I last struggled with Windows.  I wonder if this 7th incarnation is different.
I have followed bcbc's advice from July 7th, 2011 #418 and I appear to have transferred 100GB of extra Hard Drive to Ubuntu but I can not see how to rename the root files.

Regards
John 

[QUOTE=bcbc;10134374]This HOWTO describes how to resize a Wubi virtual disk. There are two distinct techniques. 

The first, described here, is not strictly a resize, but rather a duplication to a larger virtual disk. E.g. if you have a 7GB root.disk, and you want to make it 10GB you need 10GB of free space (plus leave enough for Windows). This is safer than attempting to expand the current root.disk. 
This technique must be run from within the booted Wubi install.


6. You're done!
Reboot into windows, rename the file \ubuntu\disks\root.disk to \ubuntu\disks\OLDroot.disk
Rename the file \ubuntu\disks\new.disk to \ubuntu\disks\root.disk
Reboot back into Ubuntu -- only delete the OLDroot.disk if you are sure it worked.

NOTE: if you have previously created separate virtual disks e.g. for /home, this process will merge /home back into the new virtual disk. That means you need to remove the separate entry for /home from your /media/newdisk/etc/fstab (before the umount command)  (or change the rsync command to **--exclude '/home/*'** altogether).

---

### Post by bcbc on 2011-08-11
jhatto,
You'll find the root.disk in the C:\ubuntu\disks folder under Windows. You'll find the root.disk and new.disk in there.

PS 100GB is a lot. I have no reason to believe there is a problem with this, however, this means you can store up to 100GB of data (probably important stuff) that will be stored within a single file. If this file is corrupted, or lost through accident or Windows chkdsk cleanup - you stand to lose a lot. (Although I've never had this problem on my Wubi installs, some people have - whether through forced shutdowns or perhaps incompatible hardware or other reasons unknown)

So my personal view is to store personal data files on the /host partition (the Windows host drive - normally C:\ ). You can access any data on your ntfs host through that if you need to.

Or go the real dual boot option - you can still keep both Windows and Ubuntu. Here's a good guide: [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

And don't forget you can migrate your existing wubi without losing any of it's settings, programs, data: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by jhatto on 2011-08-12
Thanks bcbc, very much for such a prompt and full reply::popcorn:

Regards

John

---

### Post by exiledangel420 on 2011-08-12
[U][B]In place Resize of root.disk

[/B][/U]It Worked!!! Thank You Bcbc!!!!

I used it about two weeks ago and it solved the problem.
Except theirs some kind of error when I boot up.
The error message pops up says that ubuntu has encontered a problem do you want to send a report blah, blah, blah.
But it doesn't cause any problems. 
So I'm wondering if it's actually even really an error.
It doesn't crash all programs run fine.
I haven't had single problem with it.
Other then a pop messenge when I logon.
Has this happen to anyone else through this resize?

---

### Post by bcbc on 2011-08-12
> **exiledangel420 said:**
> [U][B]In place Resize of root.disk

[/B][/U]It Worked!!! Thank You Bcbc!!!!

I used it about two weeks ago and it solved the problem.
Except theirs some kind of error when I boot up.
The error message pops up says that ubuntu has encontered a problem do you want to send a report blah, blah, blah.
But it doesn't cause any problems. 
So I'm wondering if it's actually even really an error.
It doesn't crash all programs run fine.
I haven't had single problem with it.
Other then a pop messenge when I logon.
Has this happen to anyone else through this resize?
Hi, thanks for the feedback.

This doesn't sound like a problem with the resize. That prompt you get is usually if an application crashes. So what I'd suggest is follow the prompts and create a bug report (you'll need a [http://launchpad.net/](http://launchpad.net/) account for this).

If there was a problem with the resize - my expectation is that it'd be something like a corruption of the root.disk in which case it wouldn't boot at all. 
However, if the program crash appeared on the first reboot following the resize with no other changes, and switching back to your backed up root.disk prior to the resize doesn't produce the error - then I guess there could be something in it. If that's the case, try another resize and see if you can reproduce the problem. 

But as I say, this doesn't sound like the sort of error I'd expect and it's worth it to figure out whether the crash you are getting is a new bug or an existing one - which would rule out the resize.

Hope that helps.

---

### Post by allen.kempe on 2011-08-16
I have an eMachines with Ubuntu - wubi installed. I tried post #2 but it failed at step 3. I have a usb drive mounted that I used to backup the root.disk. 
/media/win/ubuntu/disks/root.disk no such file or directory.I have a usb drive mounted that I used to backup the root.disk. usb_700_ext4 which is mounted with the name "/media/_usb_700_ext4_"

Here is the procedure that worked for me: 

_**In place Resize of root.disk**_

1. You have to boot from a live CD/USB. This won't work while running Wubi.

2. Backup the root.disk
cp /media/eMachines/ubuntu/disks/root.disk /media/usb_700_ext4_

3.  Check the size of the root.disk (not required)
     Code:
     du -h --apparent-size /media/eMachines/ubuntu/disks/root.disk  
4. Run fsck on the root.disk
     Code:
     fsck -f /media/eMachines/ubuntu/disks/root.disk  
5. Resize - specify the desired final size (this example resizes to **10** GB)
     Code:
     resize2fs /media/eMachines/ubuntu/disks/root.disk  **10**G 
6. Reboot back into Wubi Ubuntu

---

### Post by jhatto on 2011-08-16
Thanks allen.kempe,
I am grateful for the help I am currently exploring various possible solutions but as it is this difficulty is not too pressing other things are taking over!

John:)

---

### Post by bcbc on 2011-08-16
> **allen.kempe said:**
> I have an eMachines with Ubuntu - wubi installed. I tried post #2 but it failed at step 3. I have a usb drive mounted that I used to backup the root.disk. 
/media/win/ubuntu/disks/root.disk no such file or directory.I have a usb drive mounted that I used to backup the root.disk. usb_700_ext4 which is mounted with the name "/media/_usb_700_ext4_"

Here is the procedure that worked for me: 

_**In place Resize of root.disk**_

1. You have to boot from a live CD/USB. This won't work while running Wubi.

2. Backup the root.disk
cp /media/eMachines/ubuntu/disks/root.disk /media/usb_700_ext4_

3.  Check the size of the root.disk (not required)
     Code:
     du -h --apparent-size /media/eMachines/ubuntu/disks/root.disk  
4. Run fsck on the root.disk
     Code:
     fsck -f /media/eMachines/ubuntu/disks/root.disk  
5. Resize - specify the desired final size (this example resizes to **10** GB)
     Code:
     resize2fs /media/eMachines/ubuntu/disks/root.disk  **10**G 
6. Reboot back into Wubi Ubuntu


Great! I am glad it worked and thanks for the feedback.

The instructions in the post were for a specific mountpoint (step 3 from the original post):
> **bcbc said:**
> 3. Mount the NTFS partition that your root.disk is on (this example assumes it's **/dev/sda1**):
```
sudo mkdir -p /media/win
sudo mount **/dev/sda1** /media/win

```

If you already have it mounted, then you need to use your own mountpoint in the rest of the instructions. I'll review the thread to make sure it's clear enough.
Thanks

---

### Post by mrsleeepy on 2011-08-26
The manual resize from a live CD worked a treat for me. I had to run e2fsck though.

Thanks!

---

### Post by bcbc on 2011-08-26
> **mrsleeepy said:**
> The manual resize from a live CD worked a treat for me. I had to run e2fsck though.

Thanks!

Do you mean after running or before the resize? If you mean before, using fsck should be equivalent to e2fsck (if you had issues, let me know what they were). If you needed to run afterwards, let me know as well (I haven't required this in my own usage, but if you did I'd like to know about it).

Thanks for the feedback.

---

### Post by jqlio18 on 2011-09-01
Had this error : 

lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/tmp/wubi-resize/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/radeon/radeon.ko": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]
rsync: connection unexpectedly closed (265019 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
wubi-resize_1.3b.sh: Copying files failed or was canceled
wubi-resize_1.3b.sh: Please wait - cleaning up...
wubi-resize_1.3b.sh: Operation aborted

---

### Post by bcbc on 2011-09-01
> **jqlio18 said:**
> Had this error : 

lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/tmp/wubi-resize/lib/modules/2.6.38-8-generic/kernel/drivers/gpu/drm/radeon/radeon.ko": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]
rsync: connection unexpectedly closed (265019 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
wubi-resize_1.3b.sh: Copying files failed or was canceled
wubi-resize_1.3b.sh: Please wait - cleaning up...
wubi-resize_1.3b.sh: Operation aborted

Please can you post the output of:
```
mount
```

Thanks

---

### Post by Jelision2 on 2011-09-20
Hi
I am trying to resize my disk from 15 GB to 30 GB (I was running out of space)
I download the wubi-resize_1.3b.sh script and run:
"sudo bash wubi-resize_1.3b.sh 30 -v"

It start running, at until now, there has been no error message but I am not sure if the script is running, the last line I got was
dev/shm/pulse-shm-1622839104
And its been like this for almost two hours

Shall I stop the script (Ctrl+C) and run again the script? It wont cause any problems to my computer if I do this? Or is it normal that the script runs for so much time? (Almost three hours now)

Thank you in advance

---

### Post by bcbc on 2011-09-20
> **Jelision2 said:**
> Hi
I am trying to resize my disk from 15 GB to 30 GB (I was running out of space)
I download the wubi-resize_1.3b.sh script and run:
"sudo bash wubi-resize_1.3b.sh 30 -v"

It start running, at until now, there has been no error message but I am not sure if the script is running, the last line I got was
dev/shm/pulse-shm-1622839104
And its been like this for almost two hours

Shall I stop the script (Ctrl+C) and run again the script? It wont cause any problems to my computer if I do this? Or is it normal that the script runs for so much time? (Almost three hours now)

Thank you in advance
Yes Ctrl+C. It shouldn't take that long and if it's in verbose mode it will show you all the files being copied etc. What was the last output from the script? (it would have been prefixed with "wubi-resize_1.3b.sh:")

Also, check whether it created a new virtual disk:
```
ls -l /host/ubuntu/disks/new.disk
```

---

### Post by Jelision2 on 2011-09-20
> **bcbc said:**
> Yes Ctrl+C. It shouldn't take that long and if it's in verbose mode it will show you all the files being copied etc. What was the last output from the script? (it would have been prefixed with "wubi-resize_1.3b.sh:")

Also, check whether it created a new virtual disk:
```
ls -l /host/ubuntu/disks/new.disk
```

Thank you very much for replying
I think it was a problem with my disk
After I stopped the script I tried to delete /host/ubuntu/disks/new.disk before running again the script. But the file never got deleted and my computer froze. So I had to restart my computer.
Then I was able to delete the new.disk file and run again the script. After maybe 30 minutes the script finished and now I running Ubuntu in the new 30 GB disk.

Thank you

---

### Post by hengis on 2011-11-24
On trying to use method 1 and using your advice to find the download in my download folder I get the message    this is not a loopmounted install


What does this mean and what can I do about it?

---

### Post by bcbc on 2011-11-24
> **hengis said:**
> On trying to use method 1 and using your advice to find the download in my download folder I get the message    this is not a loopmounted install


What does this mean and what can I do about it?

This resize is only for Wubi installs (you installed using the windows-installer). If you have a normal install, you can resize using e.g. [gparted]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition").

Just to make sure, post the result of:
```
df -h
cat /etc/fstab
```

---

### Post by hengis on 2011-11-24
Just to make sure, post the result of:
```
df -h
cat /etc/fstab
```[/QUOTE]

Thanks for your reply  here is the result  I hope it means something to you as I do not understand what ti all means

hengis@hengis-ThinkPad-R61:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             7.7G  7.3G   61M 100% /
none                  995M  680K  995M   1% /dev
none                 1002M  688K 1001M   1% /dev/shm
none                 1002M  228K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
hengis@hengis-ThinkPad-R61:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name

---

### Post by bcbc on 2011-11-24
> **hengis said:**
> Thanks for your reply  here is the result  I hope it means something to you as I do not understand what ti all means

hengis@hengis-ThinkPad-R61:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             7.7G  7.3G   61M 100% /
none                  995M  680K  995M   1% /dev
none                 1002M  688K 1001M   1% /dev/shm
none                 1002M  228K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
hengis@hengis-ThinkPad-R61:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
You don't have a Wubi install, you have a normal dual boot. The difference is that Wubi installs Ubuntu onto a virtual disk within the windows host file system (e.g. ntfs or fat32), whereas a normal install creates a dedicated partition for Ubuntu and installs it natively (file system ext2/3/4).

What you have is a real Ubuntu dual boot with a root partition of 7.7G and most of that has  been used. Also, hopefully you just missed the end of the /etc/fstab when copying and pasting because there are some lines missing.

Refer to that link I posted. Since your root partition is a logical (/dev/sda5) you'll probably have to resize the extended partition as well.

See this for a similar example of what you might have to do: [http://askubuntu.com/questions/51272/resize-partition-with-gparted](http://askubuntu.com/questions/51272/resize-partition-with-gparted)

This thread is supposed to be for Wubi - so you'll get more help if you create your own thread. If you post a link here I'll be happy to help if I can.

---

### Post by hengis on 2011-11-24
This thread is supposed to be for Wubi - so you'll get more help if you create your own thread. If you post a link here I'll be happy to help if I can.[/QUOTE]

Thanks for your help and information.  If I get stuck I will call on your excellent help.

---

### Post by hengis on 2011-11-24
Thanks for your help and information.  If I get stuck I will call on your excellent help.[/QUOTE]

I have expanded the partition but I now get 
error:no such partition.
grub rescue>

What do you suggest

---

### Post by bcbc on 2011-11-24
> **hengis said:**
> Thanks for your help and information.  If I get stuck I will call on your excellent help.

I have expanded the partition but I now get 
error:no such partition.
grub rescue>

What do you suggest
Boot an Ubuntu CD, select "Try Ubuntu" and follow the instructions here to reinstall grub: [https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
i.e.:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

If that fails... run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the result in your new thread ;)

Another great resource: [the grub rescue megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by hengis on 2011-11-24
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```If that fails... run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the result in your new thread ;)
nother great resource: [the grub rescue megathread]("http://ubuntuforums.org/showthread.php?t=1594052")[/QUOTE]


After a few tries I seem to be back up with both vista  (UG UG ) and Ubuntu working.  An enormous sigh of relief.  Thank you very nuch for your help.  Apart from the speed and usefulness of Ubuntu the help available is fantastic.  I just hope when I learn a lot more about Ubuntu I can help others.

I have not checked to see how much HD space I have for Ubuntu  yst.  I want to end this session with my laptop working.  Thanks again.

---

### Post by gilnyc on 2011-11-30
Worked great but upon a 'df -h' there was a discrepancy between the 'Avail' + 'Used' and the 'Size'. From the boards I found out that mkfs by default leaves 5% as a 'reserve' to run system commands in case the disk fills up. In my case this seemed excessive so I modified the .sh file in 2 ways: (1) least important, replaced '2%' for '5%' in a test close to the top of the file, and, (2) more importantly, I modified the mkfs command to add a '-m 2' parameter. This worked out well. Thanks for this well thought out script!

---

### Post by bcbc on 2011-12-01
> **gilnyc said:**
> Worked great but upon a 'df -h' there was a discrepancy between the 'Avail' + 'Used' and the 'Size'. From the boards I found out that mkfs by default leaves 5% as a 'reserve' to run system commands in case the disk fills up. In my case this seemed excessive so I modified the .sh file in 2 ways: (1) least important, replaced '2%' for '5%' in a test close to the top of the file, and, (2) more importantly, I modified the mkfs command to add a '-m 2' parameter. This worked out well. Thanks for this well thought out script!
I hadn't noticed that, but you're right it seems pretty excessive. I'll read up on this, but not sure I want to take control of something that should be handled by mkfs. I noticed that you can use tune2fs to modify the reserved percentage after the fact. So this might be the easiest approach for anyone who wants to make changes.

Thanks for the interesting feedback.

---

### Post by gilnyc on 2011-12-01
> **bcbc said:**
> I hadn't noticed that, but you're right it seems pretty excessive. I'll read up on this, but not sure I want to take control of something that should be handled by mkfs. I noticed that you can use tune2fs to modify the reserved percentage after the fact. So this might be the easiest approach for anyone who wants to make changes.
 
Thanks for the interesting feedback.
 
If I wasn't getting down to the wire - that is my Win 7 machine's harddrive is getting close to full - I definitely wouldn't suggest mucking with mkfs to save a few percent on the Wubi disk! Probably foolish regardless even though I backed up everything prior (both Windows work AND Wubi). The reason I didn't use tune2fs after the fact is that I believe it requires to dismount the disk - that is it requires a USB or CD boot which I don't have (I downloaded Wubi from the internet). In any case, it seems to have worked without any ill effect so I'm reporting it as an option. Thanks again for your great work!

---

### Post by DOYL on 2011-12-02
Hi ,
I've made the resize withe the script, it seems to work,
but when I booted for the first time the appearance of ubuntu (i'm using 11.04) changed to a theme more like windows me .
and I got a folder called "proc" and some files on desktop I deleted files but I can't move or delete the folder (( which contains other folders named  from 1 to 1399 and some other folders and files))  it says  that  , (have ne permission ) 

Also the appearance got back to the original theme '(hat I was using before resize) after a while wy itself , actually it logged of suddenly and when I logged in the previous theme was back 

Theanks for your help

---

### Post by bcbc on 2011-12-02
> **DOYL said:**
> Hi ,
I've made the resize withe the script, it seems to work,
but when I booted for the first time the appearance of ubuntu (i'm using 11.04) changed to a theme more like windows me .
and I got a folder called "proc" and some files on desktop I deleted files but I can't move or delete the folder (( which contains other folders named  from 1 to 1399 and some other folders and files))  it says  that  , (have ne permission ) 

Also the appearance got back to the original theme '(hat I was using before resize) after a while wy itself , actually it logged of suddenly and when I logged in the previous theme was back 

Theanks for your help

It sounds like the display manager may have crashed. Usually logging out and back in will fix that. But I'm not sure what created the additional folders and files on the desktop.

I would suggest playing it safe and falling back to the old root.disk and then rerunning the script.

---

### Post by cheg11 on 2011-12-07
Original post worked for me today to increase to 50 gigs, thanks!

---

### Post by bcbc on 2011-12-08
> **cheg11 said:**
> Original post worked for me today to increase to 50 gigs, thanks!

Great! Thanks for the feedback.

Remember to keep important data backed up - the root.disk is just a single file. I like to keep personal files e.g. multimedia synched to an external drive, on Ubuntu One, or stored on my /host partition. Enjoy.

---

### Post by hengis on 2011-12-11
After a few tries I seem to be back up with both vista  (UG UG ) and Ubuntu working.  An enormous sigh of relief.  Thank you very much for your help.  Apart from the speed and usefulness of Ubuntu the help available is fantastic.  I just hope when I learn a lot more about Ubuntu I can help others.

I have not checked to see how much HD space I have for Ubuntu  yet.  I want to end this session with my laptop working.  Thanks again.[/QUOTE]

It would appear some of the links to my USB sockets have got messed up as I can not access usb memory sticks when in Ubuntu.  I can access them in Vista.   

If I reinstall Ubuntu will I lose everything or will the missing links be restored.

Any help will  be much appreciated

---

### Post by bcbc on 2011-12-11
> **hengis said:**
> After a few tries I seem to be back up with both vista  (UG UG ) and Ubuntu working.  An enormous sigh of relief.  Thank you very much for your help.  Apart from the speed and usefulness of Ubuntu the help available is fantastic.  I just hope when I learn a lot more about Ubuntu I can help others.

I have not checked to see how much HD space I have for Ubuntu  yet.  I want to end this session with my laptop working.  Thanks again.

It would appear some of the links to my USB sockets have got messed up as I can not access usb memory sticks when in Ubuntu.  I can access them in Vista.   

If I reinstall Ubuntu will I lose everything or will the missing links be restored.

Any help will  be much appreciated
What happens when you plug in the usb stick? After plugging in go to a terminal and run "dmesg" and see what it says. Or:
```
tail /var/log/syslog -n 20
```

I'd be very surprised if this is due to the 'resize' - and there's no way to know whether reinstalling will help without knowing what the problem is. While it seems logical that it would (assuming they all worked before), there may be a lot of effort associated with a reinstall so it's worth trying to fix the problem first.

---

### Post by hengis on 2011-12-12
> **bcbc said:**
> What happens when you plug in the usb stick? After plugging in go to a terminal and run "dmesg" and see what it says. Or:
```
tail /var/log/syslog -n 20
```I'd be very surprised if this is due to the 'resize' - and there's no way to know whether reinstalling will help without knowing what the problem is. While it seems logical that it would (assuming they all worked before), there may be a lot of effort associated with a reinstall so it's worth trying to fix the problem first.

I got an awful lot of stuff but thought this would be the most useful when I entered dmesg

[23955.567091] scsi 2:0:0:0: Direct-Access     ST650211 CF               3.04 PQ: 0 ANSI: 0 CCS
[23955.567830] sd 2:0:0:0: Attached scsi generic sg2 type 0
[23955.569947] sd 2:0:0:0: [sdb] 9767520 512-byte logical blocks: (5.00 GB/4.65 GiB)
[23955.571050] sd 2:0:0:0: [sdb] Write Protect is off
[23955.571060] sd 2:0:0:0: [sdb] Mode Sense: 00 4a 00 00
[23955.571067] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[23955.573045] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[23955.660764]  sdb: sdb1
[23955.663786] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[23955.663791] sd 2:0:0:0: [sdb] Attached SCSI disk
hengis@hengis-ThinkPad-R61:~$ 
hengis@hengis-ThinkPad-R61:~$ tail /var/log/syslog -n 20
Dec 12 17:52:26 hengis-ThinkPad-R61 NetworkManager[672]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 12 17:52:27 hengis-ThinkPad-R61 kernel: [20341.254354] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input12
Dec 12 17:52:35 hengis-ThinkPad-R61 ntpdate[5022]: adjust time server 91.189.94.4 offset -0.138925 sec
Dec 12 17:52:36 hengis-ThinkPad-R61 kernel: [20350.528020] wlan0: no IPv6 routers present
Dec 12 18:17:01 hengis-ThinkPad-R61 CRON[5083]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 12 18:52:38 hengis-ThinkPad-R61 kernel: [23952.720093] usb 1-3: new high speed USB device using ehci_hcd and address 7
Dec 12 18:52:38 hengis-ThinkPad-R61 kernel: [23953.000449] Initializing USB Mass Storage driver...
Dec 12 18:52:38 hengis-ThinkPad-R61 kernel: [23953.000625] scsi2 : usb-storage 1-3:2.0
Dec 12 18:52:38 hengis-ThinkPad-R61 kernel: [23953.001483] usbcore: registered new interface driver usb-storage
Dec 12 18:52:38 hengis-ThinkPad-R61 kernel: [23953.001486] USB Mass Storage support registered.
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.567091] scsi 2:0:0:0: Direct-Access     ST650211 CF               3.04 PQ: 0 ANSI: 0 CCS
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.567830] sd 2:0:0:0: Attached scsi generic sg2 type 0
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.569947] sd 2:0:0:0: [sdb] 9767520 512-byte logical blocks: (5.00 GB/4.65 GiB)
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.571050] sd 2:0:0:0: [sdb] Write Protect is off
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.571060] sd 2:0:0:0: [sdb] Mode Sense: 00 4a 00 00
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.571067] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.573045] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.660764]  sdb: sdb1
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.663786] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Dec 12 18:52:41 hengis-ThinkPad-R61 kernel: [23955.663791] sd 2:0:0:0: [sdb] Attached SCSI disk


I hope you can make sense of all of this

---

### Post by bcbc on 2011-12-12
It looks like the USB is being picked up okay. After you plug it in, can you enter:
```
mount | grep sdb1
```

That will output a line if the USB has been mounted. If you get no output, try:
```
sudo mount /dev/sdb1 /mnt
nautilus /mnt
```

---

### Post by hengis on 2011-12-12
> **bcbc said:**
> It looks like the USB is being picked up okay. After you plug it in, can you enter:
```
mount | grep sdb1
```That will output a line if the USB has been mounted. If you get no output, try:
```
sudo mount /dev/sdb1 /mnt
nautilus /mnt
```

The first option did not do anything but the second option opened the drive.

Is that the problem fixed?
Is there something else I should do?
What had I done wrong?

A really big thanks

ps where can I learn what your suggestions do?

---

### Post by bcbc on 2011-12-12
> **hengis said:**
> The first option did not do anything but the second option opened the drive.

Is that the problem fixed?
Is there something else I should do?
What had I done wrong?

A really big thanks

ps where can I learn what your suggestions do?
Well usually the USB would automount. And it sounds like it used to. So the problem isn't really fixed. But you should see the USB partition if you open up nautilus (click on the home/folder icon top left on the Unity bar). It should show the drive by size or label even if it's unmounted. Then clicking on it will mount it (the same as I did manually)

Just confirm the release you are on? (Looking back on the thread I realise you don't have a Wubi install... so this is a bit off-topic, however since we've gone down this road, might as well continue. But next time you should create a separate thread ;) )

For more info on those commands I used you can enter:
```
man mount
or 
info mount
```
PS if you're like me you'll switch off after seeing a few lines of the manual, so basically, **mount** with no parameters tells you what is mounted and where. Adding **| grep** takes the mount output and passes it as input to grep (which looks for strings/pattern matching etc.) and that will return any line that contains the string 'sdb1'. 
The other lines: first mounts the /dev/sdb1 partition on the mountpoint /mnt and the second opens a nautilus file browser with the /mnt (i.e. /dev/sdb1) directory as the starting point.

---

### Post by hengis on 2011-12-12
or 
info mount[/CODE]PS if you're like me you'll switch off after seeing a few lines of the manual, so basically, **mount** with no parameters tells you what is mounted and where. Adding **| grep** takes the mount output and passes it as input to grep (which looks for strings/pattern matching etc.) and that will return any line that contains the string 'sdb1'. 
The other lines: first mounts the /dev/sdb1 partition on the mountpoint /mnt and the second opens a nautilus file browser with the /mnt (i.e. /dev/sdb1) directory as the starting point.[/QUOTE]

I will work on it.  I did try to get an answer by starting a new thread on the forum but I got no answers so I thought of you.

Thanks again for your help

---

### Post by bcbc on 2011-12-12
> **hengis said:**
> I will work on it.  I did try to get an answer by starting a new thread on the forum but I got no answers so I thought of you.

Thanks again for your help

I did a quick search and there are a number of threads out there from people having problems automounting USB drives in 11.10. So... I guess it would be better to live with it for a while rather than reinstall (unless you are switching releases). Maybe file a bug.

Actually nevermind, looks like a patch is on the way: [https://bugs.launchpad.net/ubuntu/oneiric/+source/usbmount/+bug/875636](https://bugs.launchpad.net/ubuntu/oneiric/+source/usbmount/+bug/875636)

---

### Post by snipe2531 on 2011-12-24
when i did the terminal thing it came up with this and i downloaded the file in attachments th 1.4b version


androidbuntu@Linux:~$ sudo bash wubi-resize_1.4b.sh 10
[sudo] password for androidbuntu: 
bash: wubi-resize_1.4b.sh: No such file or directory

---

### Post by snipe2531 on 2011-12-24
> **bcbc said:**
> Most likely you saved it to your Downloads folder. By default terminal opens in your home folder.
```
cd Downloads
bash wubi-resize_1.3b.sh --help
```

See if that works, otherwise determine where you saved it and change to the appropriate folder.i did that but doesnt seem to work :( i use ubuntu 11.10 64 bit

---

### Post by bcbc on 2011-12-24
> **snipe2531 said:**
> i did that but doesnt seem to work :( i use ubuntu 11.10 64 bit

The problem is finding the place where you downloaded the script and/or a typo. You can use TAB to autocomplete if that helps. It will quickly show you whether you'r in the right directory.

e.g.
sudo bash wubiTAB

The first time you ran it you were in your home directory, and usually it should be the Downloads directory. But it's wherever you saved it. So download again, and then you'll know.

---

### Post by coldjeanz on 2012-01-15
I'm a bit confused...

I put this into terminal:

```
cd Downloads
bash wubi-resize_1.4b.sh --help
```

And it listed out a bunch of stuff. What do I type in after that? I want to resize to 80 gigs of space.

---

### Post by bcbc on 2012-01-15
> **coldjeanz said:**
> I'm a bit confused...

I put this into terminal:

```
cd Downloads
bash wubi-resize_1.4b.sh --help
```

And it listed out a bunch of stuff. What do I type in after that? I want to resize to 80 gigs of space.
The script limits the max root.disk size to 32GB. You can make it bigger if you supply an override option, but personally I don't recommend this. The reason is that the 'disk' is just one large file, and if it gets corrupted you can lose the contents. However, you can mitigage the risk by keeping regular backups.

So the command would be:
```
sudo bash wubi-resize_1.4b.sh --max-override 80
```

---

### Post by coldjeanz on 2012-01-15
Hm...in that case do you think it would be better to just migrate my wubi to a real dual boot? I've always been apprehensive to do this because I've never tried to do a partition and people say you can wreck your entire system. Wubi has seemed to work very well there's just not enough space.

Is there a guide out there that explains how to do the process easily? Like starting from the partition to the migration?

---

### Post by bcbc on 2012-01-15
Yes there is a link on the first post I a Howto I wrote

---

### Post by bcbc on 2012-01-16
> **coldjeanz said:**
> Hm...in that case do you think it would be better to just migrate my wubi to a real dual boot? I've always been apprehensive to do this because I've never tried to do a partition and people say you can wreck your entire system. Wubi has seemed to work very well there's just not enough space.

Is there a guide out there that explains how to do the process easily? Like starting from the partition to the migration?

The other thing you can do is to save data on the windows /host. Or have a separate NTFS partition for data. The benefit to this is that the data is available to both Ubuntu and Windows, it's safer, and you can keep using Wubi if you prefer. It's even possible to create a link e.g. from your Ubuntu Pictures folder to some folder on your /host or on another partition (in this case, the partition needs to be in /etc/fstab for automounting).

---

### Post by coldjeanz on 2012-01-16
Haha sorry for sounding slow, but how would I go about doing all that :confused:. Which one of those methods would you recommend?

---

### Post by bcbc on 2012-01-16
> **coldjeanz said:**
> Haha sorry for sounding slow, but how would I go about doing all that :confused:. Which one of those methods would you recommend?

I think every situation is different (hard to say which is best). In my case, I have a separate NTFS partition for data since they don't 'belong' to either Ubuntu or Windows (and sharing is easier on NTFS). I haven't bothered setting up links mainly because I don't spend a lot of time working with them. 
With a Wubi install, you have easy access to your data under /host/... and it's already mounted and accessible - so pretty simple to share.

Here's a nice post by *oldfred* that might help setup links and help you decide what to do: [http://ubuntuforums.org/showpost.php?p=11541007&postcount=4](http://ubuntuforums.org/showpost.php?p=11541007&postcount=4)

---

### Post by coldjeanz on 2012-01-16
Oh wow I had no idea all I had to do was click on the host folder and I could access all my files on Windows. That's really handy. Now I can just save all my data into host right? Since the hard drive space there is so much larger.

Thank you for that information, great help :)

---

### Post by boyangcs on 2012-03-05
Thank you very much. It works very well!!

---

### Post by Dalladubb on 2012-03-07
Get this error no matter what I do:

```
rsync warning: some files vanished before they could be transferred (code 24) at main.c(1070) [sender=3.0.8]
```

---

### Post by bcbc on 2012-03-07
> **Dalladubb said:**
> Get this error no matter what I do:

```
rsync warning: some files vanished before they could be transferred (code 24) at main.c(1070) [sender=3.0.8]
```

That normally happens if you're working while rsync is copying files e.g. on your browser and it's manipulating your cache. So it's best to let the copy run without working.

However, it's a bit of a pain to have to restart each time so I've built in a --resume option specifically for copying errors, where you can continue where you left off (usually after correcting, but in your case there's nothing you can correct - just try to resist the urge to do stuff). If you feel like trying this you can get it here: [https://github.com/bcbc/Wubi-resize/zipball/Proposed](https://github.com/bcbc/Wubi-resize/zipball/Proposed) (That's the version I've been using that will be released soon when 12.04 comes out - note it will still fail for error code 24, but you can --resume and it doesn't have to copy everything again so it's quick)

The only other thing you can do is to modify the script to ignore error code 24:
i.e. change this:

```
  rsync "$rsync_opts" --exclude '/sys/*' --exclude '/proc/*' --exclude '/host/*' --exclude '/mnt/*' --exclude '/media/*/*' --exclude '/tmp/*' --exclude '/home/*/.gvfs' --exclude '/root/.gvfs' --exclude '/var/lib/lightdm/.gvfs' / $target
[COLOR="Red"]  if [ "$?" != 0 ]; then[/COLOR]
     echo "$0: Copying files failed or was canceled" 
...
  fi 

```
To this:
```
  rsync "$rsync_opts" --exclude '/sys/*' --exclude '/proc/*' --exclude '/host/*' --exclude '/mnt/*' --exclude '/media/*/*' --exclude '/tmp/*' --exclude '/home/*/.gvfs' --exclude '/root/.gvfs' --exclude '/var/lib/lightdm/.gvfs' / $target
[COLOR="red"]  if [ "$?" != 0 ] && [ "$?" != 24 ]; then[/COLOR]
     echo "$0: Copying files failed or was canceled" 
...
  fi 
```

---

### Post by Dalladubb on 2012-03-08
Thanks. I did what you said about leaving it and it failed 3 more times before I realized I had wallch going. It's a desktop wallpaper slideshow similar to Windows 7's desktop slideshow.

When I disabled that it went like butter. Maybe you could throw a warning a warning in your OP to disable active apps like desktop wallpaper slideshow apps.

Other than that, thank you very much for this incredibly useful script.

---

### Post by bcbc on 2012-03-08
> **Dalladubb said:**
> Thanks. I did what you said about leaving it and it failed 3 more times before I realized I had wallch going. It's a desktop wallpaper slideshow similar to Windows 7's desktop slideshow.

When I disabled that it went like butter. Maybe you could throw a warning a warning in your OP to disable active apps like desktop wallpaper slideshow apps.

Other than that, thank you very much for this incredibly useful script.
Okay - great you got it sorted out, and you're welcome for the script.

I'm thinking I should just put a permanent bypass on return code 24 from rsync. I'm hard pressed to think of a situation where it indicates a serious problem, and so far it does just seem to be a nuisance. Thanks for your feedback!

---

### Post by Dalladubb on 2012-03-08
Maybe put in an optional ignore, similar to verbose asking you to continue each step. Maybe echo a message like like:

WARNING: rsync encountered an error 24 (Some files vanished before they could be transferred). This is probably nothing, however there is a small chance something important caused this error. Continue? (Enter to continue, CRTL+C to abort):

That would be my suggestion. That way the user has a choice and is warned.

---

### Post by bcbc on 2012-03-08
> **Dalladubb said:**
> Maybe put in an optional ignore, similar to verbose asking you to continue each step. Maybe echo a message like like:

WARNING: rsync encountered an error 24 (Some files vanished before they could be transferred). This is probably nothing, however there is a small chance something important caused this error. Continue? (Enter to continue, CRTL+C to abort):

That would be my suggestion. That way the user has a choice and is warned.
Exit code 24 is "Partial transfer due to vanished source files". I don't think that's serious enough to warrant even a warning. Basically either the user deleted a file (in which case it's not needed) or some running process has removed a temporary file. On that subject, I have to wonder why a screensaver needs to write and delete files - seems a bit unnecessary. I know that Chrome does a lot of caching activity - that's why I normally get a 24 if I'm surfing while I wait for it to complete.

So that's why I'm leaning towards ignoring it. But if I did give a choice it'd have to be a Y/N (not Ctrl+C) because I have to do a little cleanup (like unmounting the virtual disk) on exit.

---

### Post by Dalladubb on 2012-03-09
I think Wallch uses a temp folder and a batch copy of the folder of pics I point it at and deletes each file as it's cycled out to avoid repeats before batch copying again once it runs out.

It's kind of old.

---

### Post by bcbc on 2012-03-09
> **Dalladubb said:**
> I think Wallch uses a temp folder and a batch copy of the folder of pics I point it at and deletes each file as it's cycled out to avoid repeats before batch copying again once it runs out.

It's kind of old.
Why don't you [file a bug]("https://bugs.launchpad.net/wallpaper-changer/+filebug"). It seems inefficient. e.g. if it used a database it could probably achieve the same without copying/deleting files. I think Ubuntu comes with couchdb built-in.

---

### Post by xklusivguy on 2012-04-19
Hello..

I just tried resizing my virtual disk to 30GB and I am getting an error I haven't seen yet in this thread. I tried --resume without fixing anything just to see if it will push through but it seems like it is not. This is what the got the first time and after the --resume.

> wubi-resize_1.5b.sh:  Resume previous resize attempt? (Y/N)
Y
wubi-resize_1.5b.sh: Copying files - this will take some time.
wubi-resize_1.5b.sh: Please be patient...
wubi-resize_1.5b.sh: Copying from root (/)
wubi-resize_1.5b.sh: Copying from /boot
wubi-resize_1.5b.sh: Copying from /usr
rsync: read errors mapping "/usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0": Input/output error (5)
rsync: read errors mapping "/usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0": Input/output error (5)
ERROR: usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0 failed verification -- update discarded.
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
wubi-resize_1.5b.sh: Copying files failed or was canceled. Return code: 23
wubi-resize_1.5b.sh: Correct errors and rerun with --resume option
wubi-resize_1.5b.sh: Please wait - cleaning up...
wubi-resize_1.5b.sh: Operation aborted

Any help?

---

### Post by bcbc on 2012-04-19
> **xklusivguy said:**
> Hello..

I just tried resizing my virtual disk to 30GB and I am getting an error I haven't seen yet in this thread. I tried --resume without fixing anything just to see if it will push through but it seems like it is not. This is what the got the first time and after the --resume.



Any help?

rsync doesn't like that file: /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0

Not sure what that's about, but it seems like Input/output error (5) means that either there is a problem with the filesystem or the disk. Maybe it has been corrupted. Try running fsck on the root.disk (from a live CD). Try copying the file manually - see if that gives you errors.

---

### Post by jsiras on 2012-04-20
Hi there,

First of all, thanks for all information here. Very big help to all Ubuntu users especially for newbie like me.

However, I still need you guys advice since my situation is different. 

I installed Ubuntu on my netbook with WUBI at the first time. However, I deleted all related Windows folders from HDD after I got affected by viruses. Now, I have only Ubuntu on my HDD with several partitions (ext and ntfs) and I'm running low on diskspace (10 GB).

I have read threads here but I really don't know if I could increase my limited 10 GB.

My questions are:

[LIST=1]
[*]I don't have a Live CD/USB for booting. Can I create one from my current Ubuntu? or Can I create with my desktop Windows?
[*]If I can, should I forward with Automated technique or go manually?
[*]I understood that I have to Reboot into Windows to rename "root.disk" folder. How could I do this since I don't have Windows OS on my netbook anymore?
[*]Do I have to re-install Windows XP on my netbook again in order to accomplish it?
[/LIST]
Any recommend idea are very welcome and I truly appreciate your all help.

Thanks!!!
jsiras

---

### Post by jsiras on 2012-04-20
Oh, I found my usb stick but it's Fedora 14 live user. Does it help?

---

### Post by bcbc on 2012-04-20
> **jsiras said:**
> Hi there,

First of all, thanks for all information here. Very big help to all Ubuntu users especially for newbie like me.

However, I still need you guys advice since my situation is different. 

I installed Ubuntu on my netbook with WUBI at the first time. However, I deleted all related Windows folders from HDD after I got affected by viruses. Now, I have only Ubuntu on my HDD with several partitions (ext and ntfs) and I'm running low on diskspace (10 GB).

I have read threads here but I really don't know if I could increase my limited 10 GB.

My questions are:

[LIST=1]
[*]I don't have a Live CD/USB for booting. Can I create one from my current Ubuntu? or Can I create with my desktop Windows?
[*]If I can, should I forward with Automated technique or go manually?
[*]I understood that I have to Reboot into Windows to rename "root.disk" folder. How could I do this since I don't have Windows OS on my netbook anymore?
[*]Do I have to re-install Windows XP on my netbook again in order to accomplish it?
[/LIST]
Any recommend idea are very welcome and I truly appreciate your all help.

Thanks!!!
jsiras
I think it's time to [migrate]("http://ubuntuforums.org/showthread.php?t=1519354"). Wubi without Windows ==> Problem (no ability to fix NTFS file system corruption)

> **jsiras said:**
> Oh, I found my usb stick but it's Fedora 14 live user. Does it help?

Yes you could use that, but ... see previous comment. It's important to have something you can boot as a rescue medium, e.g. to run GParted or reinstall a bootloader. If it were me I'd replace Fedora with Ubuntu (same release you are using).

---

### Post by jsiras on 2012-04-21
Thanks bcbc!!!

I found a way to create Ubuntu Live USB stick and was able to load with it. However, I couldn't run Gparted  and couldn't install Knome partition editor either.

I take your advice and will take a look at "migrate".

Thanks again, I will try something on Monday and report back here. Also might need you guys help again.

Really appreciate.

jsiras

---

### Post by bcbc on 2012-04-21
> **jsiras said:**
> Thanks bcbc!!!

I found a way to create Ubuntu Live USB stick and was able to load with it. However, I couldn't run Gparted  and couldn't install Knome partition editor either.

I take your advice and will take a look at "migrate".

Thanks again, I will try something on Monday and report back here. Also might need you guys help again.

Really appreciate.

jsiras

GParted should work on the live desktop. What happened when you tried to run it?

---

### Post by jsiras on 2012-04-21
When I clicked it, it seemed to start like normal. Application window pop up. However, seconds later, GParted window disappeared. There's an exclamination mark on the task bar. I t wrote something about "can't run because ...." I tried it many times and the result repeated.

Umm, I left my netbook at work, otherwise you would capture the screen and post here.

=D>

---

### Post by jsiras on 2012-04-22
Here is a screenshot when I started GParted
[IMG]http://imageshack.us/photo/my-images/40/screenshotbn.png/[/IMG]
[http://imageshack.us/photo/my-images/40/screenshotbn.png/](http://imageshack.us/photo/my-images/40/screenshotbn.png/)
[IMG]http://imageshack.us/photo/my-images/40/screenshotbn.png/[/IMG]
[[IMG]http://imageshack.us/photo/my-images/40/screenshotbn.png/[/IMG]]("http://imageshack.us/photo/my-images/40/screenshotbn.png/")
and here is the screenshot when the crash occured
[IMG]http://imageshack.us/photo/my-images/710/screenshot1mrv.png/[/IMG]
[http://imageshack.us/photo/my-images/710/screenshot1mrv.png/](http://imageshack.us/photo/my-images/710/screenshot1mrv.png/)

---

### Post by bcbc on 2012-04-23
jsiras, I'd file a bug. 
But you can also run GParted from a command line:
```
gksu gparted
```
See if that gives you some more diagnostics.

Also try:
```
sudo parted -l
```
Maybe also:
```
sudo fdisk -l
```

See if you get some clues as to what is going on.

---

### Post by gogo1000 on 2012-04-27
dosnt workkkkkkkkkkkkkk automatic script i have message after i downloaded attached file "there is no such a file or folder" when i try torun this comand sudo bash wubi-resize_1.5b.sh 10

---

### Post by bcbc on 2012-04-27
> **gogo1000 said:**
> dosnt workkkkkkkkkkkkkk automatic script i have message after i downloaded attached file "there is no such a file or folder" when i try torun this comand sudo bash wubi-resize_1.5b.sh 10
Make sure you're in the right directory. If you downloaded it to the default directory (Downloads) then:
```
cd Downloads
sudo bash wubi-resize_1.5b.sh 10
```

If you're not in your default home directory to start with, you can get to the Downloads directory as follows:
```
cd ~/Downloads
```

---

### Post by Steeljack01 on 2012-05-17
I was able to successfully create a 32 GB root.disk (moving from 10 GB), but my file system still reports only having 9.7GB free space. I've followed all of the instructions, and everything was working fine, so I deleted OLDroot.disk, but it still only report 9.7GB free. Should I just try "resizing" to 32GB again?

---

### Post by bcbc on 2012-05-17
> **Steeljack01 said:**
> I was able to successfully create a 32 GB root.disk (moving from 10 GB), but my file system still reports only having 9.7GB free space. I've followed all of the instructions, and everything was working fine, so I deleted OLDroot.disk, but it still only report 9.7GB free. Should I just try "resizing" to 32GB again?
That's a bit puzzling. Can you post the output of:
```
ls -al /host/ubuntu/disks/root.disk

df -h

```

There is a little space (5% I think) that is reserved when the ext4 filesystem is created, but it shouldn't show that much difference (should be less than 2GB on a 32GB virtual disk). 

Anyways - if you post that output then I'll investigate further
Thanks

---

### Post by Steeljack01 on 2012-05-18
Here's the output: 

ls -al /host/ubuntu/disks/root.disk

-rwxrwxrwx 2 root root 32000000000 May 18 19:34 /host/ubuntu/disks/root.disk

df -h

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       30G   20G  8.7G  70% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  824K  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  152K  2.9G   1% /run/shm
/dev/sda3       452G  331G  121G  74% /host

---

### Post by bcbc on 2012-05-18
It looks like it believes you have used 20GB... the only thing I can think is that the script copied something you had mounted. It's not supposed to do that (it copies with the --one-file-system option). But I can't think of any way that 10 extra GB appeared.

Why don't you run the Disk usage analyzer as root:
```
gksu baobab
```

Go to Edit, Preferences and unselect the /host partition before letting it scan. Then look for the extra 10GB and try and figure out where they came from. It shouldn't be hard to miss if it's all within a separate directory.

---

### Post by gambitaw on 2012-05-28
Hello,
I probably miss something.
my df is:


Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/loop0       1532600 1125904    329896  78% /
udev             1965748       8   1965740   1% /dev
tmpfs             789812     840    788972   1% /run
none                5120       0      5120   0% /run/lock
none             1974528     284   1974244   1% /run/shm
/dev/sda2        8174592 6549728   1624864  81% /host
/dev/loop1       3313324 2124736   1022496  68% /usr

and when i try to run it i get:

wubi-resize_1.5b.sh: Insufficient space - only 1 GB available
wubi-resize_1.5b.sh: 8 GB plus a remaining buffer of 0 GB (5%) is required.

how do it knows the real size of the drive ?
is it matter if i moved the files to boot from a diff partition? (set ofcourse the boot path)

Thanks ahead, Amir.

---

### Post by bcbc on 2012-05-28
> **gambitaw said:**
> Hello,
I probably miss something.
my df is:


```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/loop0       1532600 1125904    329896  78% /
udev             1965748       8   1965740   1% /dev
tmpfs             789812     840    788972   1% /run
none                5120       0      5120   0% /run/lock
none             1974528     284   1974244   1% /run/shm
/dev/sda2        8174592 6549728   1624864  81% /host
/dev/loop1       3313324 2124736   1022496  68% /usr
```

and when i try to run it i get:

wubi-resize_1.5b.sh: Insufficient space - only 1 GB available
wubi-resize_1.5b.sh: 8 GB plus a remaining buffer of 0 GB (5%) is required.

how do it knows the real size of the drive ?
is it matter if i moved the files to boot from a diff partition? (set ofcourse the boot path)

Thanks ahead, Amir.

Amir,
It looks like your original Wubi install is on a FAT32 partition, because this results in separate virtual disks (each one is limited to a maximum size of 4GB - this is a filesystem limitation). 
Your root.disk and usr.disk sizes correspond to a minimum 5GB wubi install on a FAT32 partition.

A couple of points:
1. the script won't run on a FAT32 partition so
a) either you moved it to an NTFS partition OR
b) the script is deficient at detecting that it's FAT32 (in this case please post the result of):
```
sudo blkid
```

2. The script will merge the separate virtual disks when it resizes. So your root.disk and usr.disk will be merged (5GB).

3. The script actually duplicates the virtual disk(s) when it resizes. It doesn't modify your current virtual disks when it does this. So that means to resize to an 8GB disk you'd need 8GB of free space on the /host partition (and this won't include the space taken by your current virtual disks).
Since your /host partition is only 8GB in size, there's no way to perform this sort of resize.

In fact you only have 1GB free space available. The best you could do is an [inplace resize]("https://help.ubuntu.com/community/ResizeWubiDisk") of the root.disk to make it, say 2G in size (increase it by 500MB or so). 

The only other option would be to move the install to a new NTFS partition manually as you mentioned (updating grub.cfg to boot) or [migrate]("https://help.ubuntu.com/community/MigrateWubi") the wubi to a normal dual boot.

Hope that helps
bcbc

---

### Post by fayanora on 2012-06-05
I am a complete newbie at this. I'm trying the first option, within wubi. I got as far as Terminal. I did everything right to that point. Terminal's command line says " fayanora@ubuntu:~$ " before the cursor. I tried typing " bash wubi-resize_1.5b.sh --help " and got "no such file or directory." Tried " bash wubi-resize_1.5b.sh" and got the same thing. Friend suggested going to the root directory. Tried CD, CHDIR, even SUDO. SUDO at least got me a password prompt. I put in my password, but everything I try gives me "command not found." I think it's because I have no frakking clue what I'm doing. I don't even know how to specify what folder the file is in (Downloads)! Can someone walk me through this?

---

### Post by bcbc on 2012-06-05
> **fayanora said:**
> I am a complete newbie at this. I'm trying the first option, within wubi. I got as far as Terminal. I did everything right to that point. Terminal's command line says " fayanora@ubuntu:~$ " before the cursor. I tried typing " bash wubi-resize_1.5b.sh --help " and got "no such file or directory." Tried " bash wubi-resize_1.5b.sh" and got the same thing. Friend suggested going to the root directory. Tried CD, CHDIR, even SUDO. SUDO at least got me a password prompt. I put in my password, but everything I try gives me "command not found." I think it's because I have no frakking clue what I'm doing. I don't even know how to specify what folder the file is in (Downloads)! Can someone walk me through this?

It's probably in your Downloads folder:
```
cd ~/Downloads
```
The ~ represents your /home directory so is equivalent to:
```
cd /home/fayanora/Downloads
```

Note that directory/filenames are case-sensitive, and you can use the [TAB] key for autocompletion. In other words you can type:
cd Dow[TAB]
or 
sudo bash wubi-[TAB]
and it will autocomplete (assuming you are in the correct directory).

If you're stuck you can just browse for it and confirm the location before you go to the terminal. Or just download the script again and remember where you save it.

hope that helps

---

### Post by fayanora on 2012-06-05
Thanks, I'll try it!

---

### Post by drs305 on 2012-06-26
Thread closed per request of the OP. Please visit the Ubuntu community docs linked in the first post.

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012404](http://ubuntuforums.org/showthread.php?t=2012404)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

