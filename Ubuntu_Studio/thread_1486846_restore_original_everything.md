---
title: "restore original everything"
date: 2010-05-18
forum: Ubuntu Studio
---

### Post by matthus on 2010-05-18
Hi is there a way I can restore all the settings for everything after twiddling I've pretty much found out what software I want and what I don't, it seems some clash with others. I would like to restore everything to how it was on installation, not with deleting any of the files I have moved from my windows partition to my home folder

---

### Post by Dkkline on 2010-05-18
Hmm try this,

Go "System -> Adminstration -> Computer Janitor"

Hope that will do

---

### Post by atomizer on 2010-05-18
Yes it is possible if your have a seperate home partition.

Do you want to keep your settings?

If you do, you just have to choose to NOT format your home-partition and use THE SAME username as in your first install

If you want to delete your settings (with seperate home partition) then you have to mount your home with the live cd and delete every file that starts with a "." eg .config. (they are hidden files) and unmount the partition afterwards.
Use THE SAME USERNAME as in your first install else you can't acces them afterwards without tweaking.

If you don't have a seperate home partition, you will have to copy your /home to a flashdrive. again, if you don't want the old settings, delete the files that start with a "."

Use  the same usermane for ease of use, else you have to chown your files to the right user.

I would reccomendn to make a seperate home partition to keep your documents save when your system borks.

---

### Post by matthus on 2010-05-18
hmmm, computer janitor shows only three things I have installed I have twiddled a hell of alot more than that.
I have copied everything to my ubuntustudio partition, was hoping I could find a way to make just the os and components that came along with it revert to how they were originally without wiping my home folder as copied quite alot of stuff from the old windows one and copying back and forth is not one of my favorite hobbies. I still have the disk, thankyou anyhow

---

### Post by sgx on 2010-05-18
Like atomizer says, you should put the things you need on usbsticks, an external hard-drive, or CDs/dvds. Then copy them back to your new install.

Again, if you have a separate /home partition, you can choose not to
partion it during the new install process, and most, (but not all)
of your configurations will be intact, usually email, webrowser,
and eyecandy reappear as you left them.

To creat a separate /home partition during the install, the mountpoint you would choose, is

/home

and use the same filesystem
as your root partition. The standard root partition mountpoint is a single

/

If you have a separate /home partition now, and a .wine folder full of windows things, rename it to oldwine or similar, install the new wine, then copy the needed folders back from the oldwine

Before you access websites, install rkhunter, chkrootkit, etc, so they
can chronicle your clean system, as a basis to compare against a potentially invaded system in the future.
Cheers

---

### Post by matthus on 2010-05-18
ok I'm mildly confused now
My windows partition is basically out of use and I am not planning on using anything from it.
I'm not worried about any settings at all just that I have a large wad of music files, poems, notes, photos and other bits and bobs which are already in my ubuntustudio home folder which I'd rather not move if nessasary.
Anyhow got time to mull it over as won't change it till I get some top up for my net

---

### Post by matthus on 2010-05-18
I read somewhere its good to have a drive partitioned into two so after reading your replys maybe I could format my windows to an ext4 then copy all my stuff to it that I wanna keep then delete swaps and ubuntustudio partition to then install ubuntustudio from scratch? would be a headache seems might be worth it, was just tryin to save some time like, thankyou

---

### Post by sgx on 2010-05-18
> **matthus said:**
> I read somewhere its good to have a drive partitioned into two so after reading your replys maybe I could format my windows to an ext4 then copy all my stuff to it that I wanna keep then delete swaps and ubuntustudio partition to then install ubuntustudio from scratch? would be a headache seems might be worth it, was just tryin to save some time like, thankyou

Once all your important data is backed up, during the install, you can delete the windows partition, choose the size and create the root partition, make a new partition with a mountpoint
like /art or /data. I would choose the same filesystem as your root
partition for luck. Once installed, change its permissions if so desired. It will be owned by root by default.

(For emergencies, I also leave 400 meg freespace, in case a rescue partition is ever needed)

Cheers

---

### Post by matthus on 2010-05-25
cool I have taken your advice on keeping most things on a separate partition it makes perfect sense for future, the partition I made is ext4.
All I need to know now is how to have it always mounted to evade putting my password in all the time when I first access it.
Thank you so far and for future :0)

---

### Post by oldfred on 2010-05-25
I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Other similar versions:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://linuxtipstricks.wordpress.com/2008/10/05/how-to-create-a-separate-home-partition-in-linux-ubuntu-opensuse-mandriva-gentoo-fedora-and-so-on/](http://linuxtipstricks.wordpress.com/2008/10/05/how-to-create-a-separate-home-partition-in-linux-ubuntu-opensuse-mandriva-gentoo-fedora-and-so-on/)
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by sgx on 2010-05-26
> **matthus said:**
> cool I have taken your advice on keeping most things on a separate partition it makes perfect sense for future, the partition I made is ext4.
All I need to know now is how to have it always mounted to evade putting my password in all the time when I first access it.
Thank you so far and for future :0)

Hi, the file /etc/fstab details the boot-time access to your
drives and partitions. copy that file for safety, comment out the existing line that references that drive, and change it to the details
listed for the drive holding /home

here is an example fstab. Not all systems use UUID in fstab yet,
using /dev info like the dvd entries in the same example.

Atip on finding UUID is here:

[http://tuxtweaks.com/2010/03/command-line-basics-list-hard-drives-by-uuid/](http://tuxtweaks.com/2010/03/command-line-basics-list-hard-drives-by-uuid/)

Cheers

---

### Post by matthus on 2010-05-26
I don't mind about keeping my settings anymore as the things I actually use over others are minimal and everything else I will store is nothing to do with settings. I gave up on the idea of getting it exactly how it was and reinstalled ubuntustudio once again. Is there some ubuntu start up / boot up script I can add a mount command to I quite like having the idea of everything on my extra partition being things I can open under various os's. And although I have not listened to exactly what you guys have said I have indeed now have it inwardly registered to never give my whole hard drive to an os which for me is progress :0) - sorry early in the morning just read the fstab bit will get back

---

### Post by sgx on 2010-05-26
> **matthus said:**
> I don't mind about keeping my settings anymore as the things I actually use over others are minimal and everything else I will store is nothing to do with settings. I gave up on the idea of getting it exactly how it was and reinstalled ubuntustudio once again. Is there some ubuntu start up / boot up script I can add a mount command to I quite like having the idea of everything on my extra partition being things I can open under various os's. And although I have not listened to exactly what you guys have said I have indeed now have it inwardly registered to never give my whole hard drive to an os which for me is progress :0) - sorry early in the morning just read the fstab bit will get back

fstab is actually laid out in invisible columns, if you comment out a line, and make one to experiment with, you'll likely notice colors of certain characters change, when your edits move them across one of the column borders

This:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

describes the items that make up this file, and how to make it
sensible to mere mortals :)

Cheers

---

### Post by oldfred on 2010-05-26
You can directly mount your /data into your home for access using fstab to make it permanent every time you boot or you can mount it else where and link it in. I delete the default data folder like music, pictures, videos and made folders in my /data partition. I then link those in so the system looks like and acts like a standard system but all the data is in the data partition. Often used for those with more than one operating system to allow data to be in both/all systems.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

