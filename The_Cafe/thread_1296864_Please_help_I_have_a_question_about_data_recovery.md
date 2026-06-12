---
title: "Please help: I have a question about data recovery"
date: 2009-10-21
forum: The Cafe
---

### Post by navneeth on 2009-10-21
A few days ago, I accidentally deleted a few-hundred-gigabytes-worth of data from an external hard-drive. This happened while I was trying to install Windows XP and I used the tool that comes with the installer CD to create partitions. **The drive ever since has been disconnected and with no new data written to it**.

Now, I have found many softwares online to perform data recovery (like Undelete Plus, Recuva, etc.). The problem is, I'm not able to mount the hard-drive, both in XP and in Ubuntu. In XP, however, it shows up as an 'Unallocated' memory space in the Disk Management tool. (And, obviously, no drive letter is assigned to it.) 

Now to the question: if I format the external hard-drive -- all 500 GB of it -- to NTFS, will I still be able to recover all the deleted files? 

I await your responses. And please don't hesitate to suggest other methods of data retrieval or to recommend other (freeware) data recovery tools.

---

### Post by bryncoles on 2009-10-21
As far as I understand it, formatting the drive to NTFS will made it harder to recover data, so I wouldn't recommend doing that. I would say boot into ubuntu, open synaptic and search for [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). note that photorec also includes testdisk. the website linked has a detailed [walkthrough]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") which should help you recover your data. 

You'll need a hard drive at least as big as the one you're recovering data from, in order to write your recovered files to. 

Good luck!

*edit*

If you cant mount the drive in order to do this, then try the [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") functionality of photorec to [recover the drive]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") before attempting to recover the files. But I'm leaving my comfort zone now... I have helped all I can. Let us all know if you are met with success though! (and maybe consider donating to the project which recovers your data in the end...?)

*edit 2* 

+1 to handy, below!

---

### Post by handy on 2009-10-21
Whatever you do, don't do ANYTHING to the drive with the data on it that you want to salvage, as doing so can be all it takes for you to loose what would otherwise be easily recoverable.

I saw what you said in bold print, I'm just reinforcing it as it is critical for data recovery, it seems that you already know this golden rule. :)

Don't format the drive.

Have a look at this one:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Also, if you have the drive/partition space, if you clone the drive & then try whatever it takes on the copy, you still have the untouched original to clone again & try something else on.

It all comes down to how valuable the data is on the corrupt drive.

From what you have said, I think you will get all of your data back again, so don't give up too easily?

---

### Post by navneeth on 2009-10-21
Thanks, guys, for the replies. :) Guess what: I installed TestDisk last night, but since it was a bit late and the interface a bit unusual for that hour of the night, I didn't "play" with it for too long. I'll go through their documentation now and see what I can do. 

I don't have enough space to transfer all the stuff at once, though. I hope I can do this in parts.

---

### Post by navneeth on 2009-10-21
Update 1: all my stuff still listed there! Yes! :D

---

### Post by az on 2009-10-21
> **navneeth said:**
> A few days ago, I accidentally deleted a few-hundred-gigabytes-worth of data from an external hard-drive. This happened while I was trying to install Windows XP and I used the tool that comes with the installer CD to create partitions. **The drive ever since has been disconnected and with no new data written to it**.

Now, I have found many softwares online to perform data recovery (like Undelete Plus, Recuva, etc.). The problem is, I'm not able to mount the hard-drive, both in XP and in Ubuntu. In XP, however, it shows up as an 'Unallocated' memory space in the Disk Management tool. (And, obviously, no drive letter is assigned to it.) 

Now to the question: if I format the external hard-drive -- all 500 GB of it -- to NTFS, will I still be able to recover all the deleted files? 

I await your responses. And please don't hesitate to suggest other methods of data retrieval or to recommend other (freeware) data recovery tools.

If all you did was parition your drive, then all of your data is still there.  A tool like Testdisk will be able to restore your previous partition setup and you will then access the previous fileystsem.

If you not only partitioned but formatted the disk, then you will probably have to use file-carving software like photorec (which is installed with Testdisk).  Photorec is as good as, if not superior to the proprietary file-carving software you mentioned.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by navneeth on 2009-10-21
> **az said:**
> If all you did was parition your drive, then all of your data is still there.  A tool like Testdisk will be able to restore your previous partition setup and you will then access the previous fileystsem.

If you not only partitioned but formatted the disk, then you will probably have to use file-carving software like photorec (which is installed with Testdisk).


Hi. **Final update**: all data are up and accessible! There was nothing much to do, even in terms of recovery. All I did was follow the simple [TestDisk step-by-step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) and then reboot. (It was one single partition.) Voila! Drive automatically mounted in Ubuntu and XP and every file was there as I had left it.


Once again, thanks for your help, everyone. :)

---

### Post by JillSwift on 2009-10-21
[SIZE=4]***Backup!***[/SIZE] :)

---

### Post by navneeth on 2009-10-21
> **JillSwift said:**
> [SIZE=4]***Backup!***[/SIZE] :)


It *was* my back-up! :D

(:oops:)

I hadn't been this stupid for a long time. :D

---

### Post by JillSwift on 2009-10-21
> **navneeth said:**
> It *was* my back-up! :D

(:oops:)Yip!

> **navneeth said:**
> I hadn't been this stupid for a long time. :D
Friend, if we didn't have a moment of head-desk worthy stupidity once in along while we'd never truly appreciate it when we were being smart about things. :)

---

### Post by navneeth on 2009-10-21
> **jillswift said:**
> 
Friend, if we didn't have a moment of head-desk worthy stupidity once in along while we'd never truly appreciate it when we were being smart about things. :)


QFT.


[SIZE="1"]Why should I be required to type more for the "QFT" to show in caps?[/SIZE]

---

