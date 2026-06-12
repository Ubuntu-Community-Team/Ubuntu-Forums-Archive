---
title: "Does the warning against writing to ntfs from Linux still apply?"
date: 2018-01-03
forum: Ubuntu, Linux and OS Chat
---

### Post by raphaell2 on 2018-01-03
Years ago, I read a piece somewhere on the internet that said that in principle, you can both read from and write to ntfs partitions from modern major Linux distros, but that the author of the piece would not recommend actually using the write to functionality, for technical reasons I can't remember. So now I wonder: is that still the case? Or have things changed? Or was it overly cautious advice in the first place?

(If the answer to this is in any way controversial, please don't start a flame war here.)

---

### Post by howefield on 2018-01-03
Not a Hardware question, moved to "*Ubuntu, Linux and OS Chat*"

---

### Post by deadflowr on 2018-01-03
What does write to functionality mean?

---

### Post by raphaell2 on 2018-01-03
I mean the ability to write to ntfs partitions from Linux.

---

### Post by VanillaMozilla on 2018-01-03
> **raphaell2 said:**
> Does the warning against writing to ntfs from Linux still apply?

No.  That was patched years ago--by Microsoft, no less.

---

### Post by Cavsfan on 2018-01-03
You should never write to a Windows partition from Linux. I did it early on as I learned Linux and it worked.
But, it caused my weekly backup on Windows to fail and I had to re-install Windows. I've never had to re-install Windows before.

So, just because you can do it, doesn't mean you should. You'll find most people agree with me on that too.

Some Ubuntu versions could not open a Windows partition but, the latest 2 or 3 versions have been able to. It is then in read-only mode.

Arch Linux uses a utility written by a guy named *IgnorantGuru* and it is called **udevil**. It is a command that will mount different kinds of partitions. 
I automount my always on USB drive with udevil at boot. I mount/unmount my Windows partition as needed by typing commands in terminal (alias) and it's purposefully mounted as read only.

---

### Post by oldfred on 2018-01-03
The only remaining consideration is Windows fast start up or always on hibernation.
Windows still boots slow, so has to use hibernation to make it seem like it is not so slow.

But Windows sets hibernation on all NTFS partitions if Windows 8 or later, even a shared NTFS data partition.
And the Linux NTFS driver will not write to NTFS partitions that are hibernated, as you would lose data anyway when hiberfile is restored with old file structure or if NTFS needs chkdsk.
So you must have Windows fast start up off.

Best to also have Windows repair disk so you can repair it when needed, whether dual booting or not.

---

### Post by QIII on 2018-01-03
^This.

There is no inherent danger in the fs itself.

---

### Post by MartyBuntu on 2018-01-03
I have (a few) NTFS partitioned drives that I write to all the time...and I don't even have a Windows installation on any of my machines.

Two reasons:

1. Formatting to NTFS was a simpler solution for me years ago when I ran into permission problems
2. I copy large size raw audio and video files to external 2.5" drives that I lend to friends, so they can take the drives home and copy to their Windows machines

---

### Post by raphaell2 on 2018-01-04
Very interesting to see the different views on that matter. I think for now I won't write to ntfs from Linux, just to be on the safe side. 



> You should never write to a Windows partition from Linux. 

Do you mean **any** Windows partition, or just ntfs? In order to avoid writing to ntfs from Linux, I made an FAT32 partition on my pc years ago, mainly to move things back and forth between the Windows and Linux sides. As far as I can remember, I never had any problems with that.

---

### Post by sudodus on 2018-01-04
"You should never write to a Windows partition from Linux" means that you should not write to the partition, where Windows is installed, usually C:

But it is perfectly safe to write to another partition with NTFS. Many people use such **data partitions** to share data between Ubuntu and Windows.

---

### Post by raphaell2 on 2018-01-04
Thank you, good to know!

---

### Post by C.S.Cameron on 2018-01-04
I occasionally forget the rule and save stuff to my Windows partition, or modify a file on it, so far so good, (knock on wood).

---

### Post by litlesam on 2018-01-04
> **sudodus said:**
> "You should never write to a Windows partition from Linux" means that you should not write to the partition, where Windows is installed, usually C:

But it is perfectly safe to write to another partition with NTFS. Many people use such **data partitions** to share data between Ubuntu and Windows.

^^ This is the rule I used for years.

Thanks for that post.

---

### Post by Cavsfan on 2018-01-05
Sorry, I meant to specify writing to the partitiion with the operating system for Windows (the C: drive) causes problems; not every NTFS partition. 
My FANTOM USB drive (which just happens to be F: in Windows) that I mentioned is always on and gets automounted in which ever OS I boot into is NTFS.
It is also F: in Ubuntu and Arch if no other USB drive is connected at boot, otherwise it could become a different letter and I have to be careful to know which drive I am accessing in that case.

If I have something in Linux that I want to see in Windows, I put it on that and vice versa if I have something on Windows that I want to access in Linux, I put it on that USB drive.

Of course if it is a text file created in Linux, the line feed characters need to be converted for it to be read in Windows.

---

### Post by VanillaMozilla on 2018-01-09
Oldfred is right.  I forgot about and the fast startup.  I can't remember what happens with fast startup--I think maybe writing just fails.

Seriously, Linux is perfectly capable of reading and writing to NTFS disks without problem.  The old ntfs driver had a problem, but the ntfs-3g driver has been around and patched for probably 10 years.  As far as I know, there's nothing wrong with writing to the C: drive either.  It's just like any other drive, and can hold any kind of data.  I've been doing that too for about 10 years with no problem.  Just don't write over system or program files.

---

### Post by Cavsfan on 2018-01-10
> **VanillaMozilla said:**
> As far as I know, there's nothing wrong with writing to the C: drive either.  It's just like any other drive, and can hold any kind of data.  I've been doing that too for about 10 years with no problem.  Just don't write over system or program files.

Good luck with that. My then Windows 7 system didn't cause me any problems whatsoever that I could notice but, all of a sudden my system backup started to fail. I opened up a thread in a Windows 7 forum and eventually got a windows admin looking at my problem. I tried about 17 different things that *should have corrected the problem *but, did not. I had mentioned that I had written to the C: drive from Ubuntu. Then came the only way out: re-install Windows. I have Windows 10 now and I will never write directly to my C: drive from Linux again period. It may not cause you any problems, you may not use it's built in backup system, it may cause problems in other parts of Windows that you do not notice at the time. 

It's just as easy to have a rule that you write to another NTFS partition like a USB drive or hard drive other than C: and then transfer that to to C: drive from within Windows. 

Has any one else experienced a problem writing directly to the C: drive that Windows is running on from a Linux system?

---

### Post by oldfred on 2018-01-10
With my old XP system, the first things I did was turn on extension & see all the system files & folders.
The Linux NTFS driver defaults to that type of setting.

But then in clicking around in XP I would move an entire system folder or some critical file. Or do not work fast and click and  move mouse at same time.
Learned to repair XP many times.
So when I installed Linux, I set c: drive as read only and used a shared NTFS data partition for read/write.

---

### Post by djchandler on 2018-01-13
I write to NTFS on my laptop often. Only problem I ever had was after upgrading to Win 10 on it. Always RESTART from Windows if you want to go to Linux and access your Windows 10 NTFS partition. SHUTDOWN hibernates it.

---

### Post by Cavsfan on 2018-01-13
I believe in versions prior to and including Xenial Xerus 16.04 LTS, the C: partition would not mount by simply clicking on it.
I had to make a mount point and use aliases to mount and unmount it (this is in 16.04):
```
#Mount C: drive
alias mountc='sudo mount -t ntfs-3g -o ro /dev/sda1 /media/windows'


#Unmount C: drive
alias umountc='sudo umount /dev/sda1'

```

But, in Zesty, Artful and Bioinic it mounts just by clicking on it as read only:

[ATTACH=CONFIG]278180[/ATTACH]

---

