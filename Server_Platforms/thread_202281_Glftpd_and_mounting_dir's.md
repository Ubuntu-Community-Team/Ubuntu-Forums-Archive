---
title: "Glftpd and mounting dir's"
date: 2006-06-23
forum: Server Platforms
---

### Post by Lycaon on 2006-06-23
Well hello people who are willing to help me,

Revisited:P I couldnt find a move button so i made this post here. (first thread was in the beginners forum)

I installed ubuntu dapper drake server edittion on my server. That went well. A main daemon i am using in the server is glftpd. A pretty nice and good working ftp daemon. While installing dapper drake asks me for the partitioning table. I got 2 s-ata maxtor hdd's (sda and sdb). Here is the layout i chose to create:
> 
  SCSI1 (0,0,0) (sda) - 163.9 GB ATA Maxtor 6Y160M0
    #1 primary      2.0 GB    F  swap     swap
    #2 primary    20.0 GB  BF  ext3      /
    #3 primary  141.9 GB    F  ext3      /disc1
  SCSI2 (0,0,0) (sdb) - 160.0 GB ATA Maxtor 6Y160M0
    #1 primary  160.0 GB    F  ext3      /disc2


and the fstab after the install looks like this

> 
# <file system> <mount point>    <type>  <options>         <dump>  <pass>
proc                    /proc                    proc      defaults                  0            0
/dev/sda2           /                          ext3      defaults,errors=remount-ro 0 0
/dev/sda3           /disc1                  ext3      defaults                   0            2
/dev/sdb1           /disc2                  ext3      defaults                   0            2
/dev/sda1           none                   swap     sw                           0            0


So i continued installing some libs etc. After that i could install glftpd. Glftpd mkdirs this layout for the server dir's.
 /glftpd/site/
This dir is on /dev/sda2. When a user logs into the ftp server they will end up by default in the root directory of the server. That is /glftpd/site/.

While partioning earlier i created to big partions for my data. sda3 on hdd1 and sdb1 on hdd2 -> /disc1 & /disc2.
The thing i actually want is this:
[example]
  * i create directory called 'upload' on disc2: /disc2/upload
  * now i would like to have, when a user logs in he/she can see the dir upload in the ftp. If the user enters the directory it will be not in /glftpd/site/upload, but actually working in /disc2/upload.
  * Why? now i can have directories that dont have anything to do with the ftp on disc2 also. So I can specify what dirs ar shown in glftpd.
[/example]

This is what i have already tried:

> 
* Making a symlink from /disc2/upload to /glftpd/site/. This works i can see a shortcut when i loging called'upload'. However when i try to enter this dir it says: [2] CWD upload [2] 550 upload: No such file or directory.
   I can't enter it...and i just dont know why.  Everyone has all rights on that dir/disc
* Mounting in fstab, well after reading i figuered  out i cannot mount directories in fstab only filesystems. (thnx  mlind)
* i tried to bind a directory to another with: mount --bind /disc2/upload/ /glftpd/site/upload/
   and yes this fails too:( It seems to be uploading on the /glftpd/upload map instead of  /disc2/...


other things i noticed:
*when typing mount in the terminal it doesnt display /dev/sdb1
  when i try to mount it normally it just say's:
  /dev/sb1 already mounted or /disc2 busy
*if i do : df -h i get results but the sdb1 is missing..


I hope this makes it some easier to read. Please give it another shot

---

