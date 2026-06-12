---
title: "Werid Bug, Virus or spyware?"
date: 2010-02-28
forum: Security
---

### Post by smackc on 2010-02-28
Hello, ill start my explaining my problem then ill tell why what i did to get here. The only question is how do i fix it?

 I have 1tb My Book I keep all my iso's and somewhat important files on it. Only the problem is i cant write to it any more because its read-only. Easy fix right ... wrong. The permissions change back. 
 This happened because i the idoit that i am used My Book to backup a friends files from his pc os - Windows Vista. As luck would have it i couldnt copy the files over. Because they were read only. Actually 8 images were copied over and then noticed everything was read only. Werid but easy enough to fix so i changed it. It was still read only have changing it. Well his entire C:\ was read only werid. So i fixed it by reformatting his system. No biggie.

 Back to the matter at hand the My Book is read-only and changes back. I dont want to reformat it, its ntfs, also heres what ive tried so far.

-----------------------------------------------------------------
terminal:/media$ ls -l
total 10
lrwxrwxrwx 1 root     root        6 2010-02-25 23:06 cdrom -> cdrom0
dr-xr-xr-x 2 root     root     2048 2010-02-27 15:48 cdrom0
drwx------ 1 calvinux calvinux 8192 2010-02-27 23:39 My Book
-----------------------------------------------------------------
terminal:/media$ chmod 755 "My Book"
-----------------------------------------------------------------
terminal:/media$ ls -l
total 10
lrwxrwxrwx 1 root     root        6 2010-02-25 23:06 cdrom -> cdrom0
dr-xr-xr-x 2 root     root     2048 2010-02-27 15:48 cdrom0
drwx------ 1 calvinux calvinux 8192 2010-02-27 23:39 My Book
-----------------------------------------------------------------

 notice it didnt change any ideas?

---

### Post by kerry_s on 2010-02-28
are you root?
did you try " **sudo** chmod 755 "My Book" "?

---

### Post by smackc on 2010-02-28
Yup i tired root. It didnt work. I even get an error when i try to create a folder 

"Error while creating directory untitled folder.
There was an error creating the directory in /media/My Book.

show error 
Error creating directory: Input/output error"

---

### Post by cariboo on 2010-02-28
The input/output error sounds like the drive isn't mounted.

---

### Post by smackc on 2010-02-28
I can view it from my desktop. When right click i have the unmount option available.

---

### Post by cariboo on 2010-03-01
Are you sure the drive it self is healthy, I've heard of quite a few people in my area having problems with those external drives.

If everything is OK with the drive, you should be able to mount the drive with world read/write permissions just to see if you can copy files to the drive, I don't advise it for security reason, but just for testing purposes try this. Once the drive is mounted, open a terminal and type the following command:

```
sudo chmod -R 777 /media/"My Book"
```

Note the quotes around the drive label. What the above command does is recursively change read/write permissions so that anyone can read and write to the disk.

---

### Post by smackc on 2010-03-01
I tried it :D.
```
calvinux@Calvin-Linux:~$ sudo chmod -R 777 /media/"My Book"
[sudo] password for calvinux: 
chmod: cannot access `/media/My Book/Movies/DataJockey-ol.ogg': Input/output error
chmod: cannot access `/media/My Book/Movies/Incomplete Downloads': Input/output error
chmod: cannot access `/media/My Book/Programs/putty.exe': Input/output error
chmod: cannot access `/media/My Book/Steve Pictures/2009-07-07': Input/output error
chmod: cannot access `/media/My Book/Work/Code/Java/File IO Demo Final': Input/output error

```
```
calvinux@Calvin-Linux:~$ cd ../../media/
calvinux@Calvin-Linux:/media$ ls -l
total 12
lrwxrwxrwx 1 root     root        6 2010-02-25 23:06 cdrom -> cdrom0
dr-xr-xr-x 2 root     root     2048 2010-02-27 15:48 cdrom0
drwx------ 1 calvinux calvinux 8192 2010-02-27 23:39 My Book
drwx------ 5 calvinux calvinux  408 2009-10-14 17:49 WD SmartWare

```

---

### Post by bodhi.zazen on 2010-03-01
> **smackc said:**
> <clip>. I dont want to reformat it, its ntfs </clip>

You can not use chown or chmod with ntfs partitions. Ownership and permissions are set at the time of mounting.

It sounds as if the drive has errors on it.

with nfts my advice is that you connect it to a windows box and check the file system for errors.

Unfortunately the tools to fix the problem with Linux are not great, you can try ntfsfix

unmount the device, then run

```
ntfsfix /dev/sdb1
```

change sdb1 to the partition you need to fix.

If that fails, try windows.

If that fails you can try to copy the data or testdisk and reformat the partition.

---

### Post by cariboo on 2010-03-01
It might me worth your while to install ntfsprogs, it is in the repositories. Ntfsmount is included in the package, this may help with your problem.

---

### Post by smackc on 2010-03-01
You were there are errors. As i just ran CHKDSK without /f first. It reported back some errors.
Im currently running CHKDSK /f from my windows machine ill tell you how it goes.

---

### Post by smackc on 2010-03-01
It worked Im not exactly sure how we put SOLVED on the thread but its solved. thanks :D

---

### Post by bodhi.zazen on 2010-03-01
w00t =)

---

