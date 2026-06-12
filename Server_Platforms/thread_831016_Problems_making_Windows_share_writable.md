---
title: "Problems making Windows share writable"
date: 2008-06-16
forum: Server Platforms
---

### Post by derdud on 2008-06-16
I'm having some troubles mounting a Windows share drive on my Ubuntu 8.04 machine. It works, but the problem is that it's not writable. If I try to create a test file "testing.txt" on the share, nano gives me an error that says:

**Error writing /mnt/fs_backup/test.txt: No such file or directory**

1. The first thing I did was edit my /etc/fstab file and add the drive. The server name is **fileserv** and the share name is **backup-disk**. It's a 2-terabyte external hard drive.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/cciss/c0d0p1
UUID=b540af75-18cf-4f2a-8e00-03d2b46a70a2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/cciss/c0d0p5
UUID=8acb4aab-1490-4dca-9cf7-c20ddd34a326 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//fileserv/backup-disk  /mnt/fs_backup  cifs    exec,credentials=/etc/cifspw    0       0
```

2. Next, I created the credentials file at /etc/cifspw:
```
username=daemon
password=mysecretpassword
```

3. I ran the command **mount -a**.

4. I went into the /mnt/fs_backup folder and everything appears correct so far.

5. Used nano to create a new file: testing.txt

6. Typed some random letters and hit CTRL-X to exit and save. When I tell it to save, that's when it gives the error message.

I know I'm probably doing something wrong but I've never needed to mount a network share for anything more than read-only before, so this is new to me. Thanks :)


EDIT: I also tried adding rw to the fstab:
```
//fileserv/backup-disk  /mnt/fs_backup  cifs    exec,rw,credentials=/etc/cifspw    0       0
```

It still gives the same error

---

### Post by iskatyel on 2008-06-17
Try it manually,
```
sudo mount -t cifs -v -o remount,rw,credentials=/etc/cifspw //fileserv/backup-disk /mnt/fs_backup
```
and see if there are any errors.  
A couple more thoughts: 
Could it be mounting with guest rights and what are the permissions on the credentials file?
Also, you could use touch to see if you can write without going into nano.

---

### Post by randy_crowe on 2008-06-19
I'm having similar problems.  You need to make the mount point writable (777).  That along with making sure the credentials are sufficient to allow writing took care of the problem for me.  However now I can't change a file.  If I execute:
"cd /mnt/where_the_share_is_mounted"
touch file.txt

the file file.txt is created no problem.
if I then rm file.txt it is deleted.

if i gedit file.txt it is created and can be saved.
if i gedit file.txt again it can be edited but not saved.  It can be saved under a new file name just fine.

So....
I can create a file by any method...touch, gedit, copy file, whatever.
I can delete a file.
I can't change a file.  If I cp ~/file.txt to the share and the file exists it will not be replaced.  BTW executing any of the above commands as sudo does not make any difference.

Any thoughts

Ubuntu 8.4
Windows Server 2003 share mounted under /mnt/server/share and /mnt and /mnt/server have permissions set to 777
login credentials are the administrator account on the server domain.

Randy
[email]rcrowe@wvu.edu[/email]

---

### Post by doogy2004 on 2008-06-19
install smbfs then try this line in fstab

Replace the following:
USER=username of the user who will have access
GROUP=group name of the group who will have access (I typically make it the same as USER
credentials can point to any file you want, i just have it in my example

```
//fileserver/storage /media/storage smbfs credentials=/home/USER/.smbcredentials,uid=USER,gid=GROUP 0 0
```

If the locations have spaces in them – use \040 in place of the space

---

