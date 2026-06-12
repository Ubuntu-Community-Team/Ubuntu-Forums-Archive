---
title: "Auto mount with odd issue"
date: 2021-03-21
forum: Virtualisation
---

### Post by RichJacot on 2021-03-21
Hello,

I'd posted:  [https://ubuntuforums.org/showthread.php?t=2459425](https://ubuntuforums.org/showthread.php?t=2459425).  and it appeared to have fixed my problem.  Meaning they NAS shares mounted as I cd'd to them or one of my applications needed them.  And...that part does work. 

The problem is for some reason now I can't write to them but it's' not a permissions issue. See below:

```
rjacot@ubuntu:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
udev                     1.9G     0  1.9G   0% /dev
tmpfs                    394M  1.4M  393M   1% /run
/dev/vda5                245G   33G  200G  15% /
tmpfs                    2.0G  8.0K  2.0G   1% /dev/shm
tmpfs                    5.0M     0  5.0M   0% /run/lock
tmpfs                    2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop2                56M   56M     0 100% /snap/core18/1944
/dev/loop3               256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop4               219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop0                99M   99M     0 100% /snap/core/10823
/dev/loop1               100M  100M     0 100% /snap/core/10859
/dev/loop9               9.2M  9.2M     0 100% /snap/canonical-livepatch/95
/dev/loop10               50M   50M     0 100% /snap/snap-store/467
/dev/loop7                63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop6                32M   32M     0 100% /snap/snapd/11036
/dev/loop5                56M   56M     0 100% /snap/core18/1988
/dev/loop8                65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop11               52M   52M     0 100% /snap/snap-store/518
/dev/loop12               33M   33M     0 100% /snap/snapd/11107
/dev/vda1                511M  4.0K  511M   1% /boot/efi
//192.168.1.6/Torrents   466G  101G  366G  22% /mnt/Torrents
//192.168.1.6/Downloads  466G  101G  366G  22% /mnt/Downloads
//192.168.1.11/Misc       45T   18T   28T  40% /mnt/Misc
//192.168.1.11/Music      45T   18T   28T  40% /mnt/Music
//192.168.1.11/Media      45T   18T   28T  40% /mnt/Media
//192.168.1.11/Backups    45T   18T   28T  40% /mnt/Backups
//192.168.1.11/Download   45T   18T   28T  40% /mnt/Download
tmpfs                    394M   24K  394M   1% /run/user/1000
/dev/sr0                 2.6G  2.6G     0 100% /media/rjacot/Ubuntu 20.04.1 LTS amd64
```

I can see them:

```
rjacot@ubuntu:~$ ls -al /mnt/Media/
total 40
drwxr-xr-x 2 rjacot root     0 Mar 21 08:10  .
drwxrwxrwx 9 root   root  4096 Feb 19 08:07  ..
drwxr-xr-x 2 rjacot root     0 Mar 13 18:58  4k
drwxr-xr-x 2 rjacot root     0 Jul 28  2020  Download
-rwxr-xr-x 1 rjacot root 24580 Mar 21 07:56  .DS_Store
drwxr-xr-x 2 rjacot root     0 Mar  7 19:15  Kids
drwxr-xr-x 2 rjacot root     0 Mar 20 08:55  Movies
-rwxr-xr-x 1 rjacot root     0 Mar 21 08:10  rj.delete.this
drwxr-xr-x 2 rjacot root     0 Mar 20 01:29  TV
drwxr-xr-x 2 rjacot root     0 Dec 24 09:13  Videos

rjacot@ubuntu:~$ ls -al /mnt/Media/Movies/
total 72400796
drwxr-xr-x 2 rjacot root           0 Mar 20 08:55  .
drwxr-xr-x 2 rjacot root           0 Mar 21 08:10  ..drwxr-xr-x 2 rjacot root           0 Jan 17  2020  1917.2019.DVDSCR.x264-TOPKEK
.....  lots more in here
```

But I get this error when I try to write something:

```
rjacot@ubuntu:~$ touch /mnt/Media/Movies/rj.delete.this
touch: cannot touch '/mnt/Media/Movies/rj.delete.this': No such file or directory
rjacot@ubuntu:~$ 

```
As you can see above it let me touch the /mnt/Media/rj.delete.this.  I just can't do it in the subdirs.

Here's my stab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/vda5 during installation
UUID=09db9129-f5b3-4726-97cc-19a0d3d2b5e9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/vda1 during installation
UUID=93A5-BB65  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
//192.168.1.11/Media /mnt/Media cifs credentials=/home/rjacot/.smbcredentials1,uid=rjacot,noauto,x-systemd.automount 0 0
//192.168.1.11/Misc /mnt/Misc cifs credentials=/home/rjacot/.smbcredentials2,uid=rjacot,noauto,x-systemd.automount 0 0
//192.168.1.11/Download /mnt/Download cifs credentials=/home/rjacot/.smbcredentials3,uid=rjacot,noauto,x-systemd.automount 0 0
//192.168.1.11/Backups /mnt/Backups cifs credentials=/home/rjacot/.smbcredentials4,uid=rjacot,noauto,x-systemd.automount 0 0
//192.168.1.11/Music /mnt/Music cifs credentials=/home/rjacot/.smbcredentials5,uid=rjacot,noauto,x-systemd.automount 0 0
//192.168.1.6/Downloads /mnt/Downloads cifs credentials=/home/rjacot/.smbcredentials6,uid=rjacot,noauto,x-systemd.automount 0 0
//192.168.1.6/Torrents /mnt/Torrents cifs credentials=/home/rjacot/.smbcredentials7,uid=rjacot,noauto,x-systemd.automount 0 0

```
(yes I realize now I can/could have used the same .smbcredentials file for all of the mounts.  I just didn't know that when I was doing it and then it was working, so I left it.)

This happens with the other shares also.  I'm just using Movies as a sample.

---

### Post by Morbius1 on 2021-03-21
> //192.168.1.11/Media /mnt/Media cifs credentials=/home/rjacot/.smbcredentials1,uid=rjacot,noauto,x-systemd.automount 0 0
...
drwxr-xr-x 2 rjacot root 0 Mar 20 08:55 Movies

rjacot has the ability to write to everything on that share as long as the user specified in your credentials file has write access to everything on the folder being shared on the server.

So the question is who has write access to the Movies subdirectoy on the server ( NAS )? Is the user in the credentials file one of them?

---

### Post by RichJacot on 2021-03-22
Thank you so much.  That got me fixed!!!   I was using admin in my .smbcredentials files.  (I know bad idea)  It was the first time I was doing this and it was working with the sudo mount -a.  Not sure why this method would change that but I'm working so I'll leave well enough along.

Thanks again!

---

### Post by RichJacot on 2021-03-22
guess I spoke too soon.  Some are working and some aren't.  I'm looking a the NAS share permissions now but rjacot is also an admin on the NAS so....

---

### Post by Morbius1 on 2021-03-22
Just so we are both talking about the same thing I ran an experiment to show you what I'm talking about:

I created a folder at /TestShare and set permissions to 777 on my server. I then created a samba share of the folder:
```
[TestShare]
path = /TestShare
valid users = tester
read only = no
```
I then created a subdirectory called Movies: /TestShare/Movies

Then I mount the share on my client system:
```
sudo mount -t cifs //vubsrv1804.local/TestShare /home/morbius/Public -o username=tester,uid=morbius
```

I can add a file to the mount point easy enough but when I try to add a file to the Movies subdirectory it will not work:
> morbius@xub1804:~$ touch Public/Movies/movies.txt
touch: cannot touch 'Public/Movies/movies.txt': Permission denied
I have to go back to the server and allow a write - in my example to everyone - to the Movies subdirectory:
```
sudo chmod 0777 /TestShare/Movies
```

Now on the client I have write access:
> morbius@xub1804:~$ touch Public/Movies/movies.txt
morbius@xub1804:~$ ls -l Public/Movies
total 0
-rwxr-xr-x 1 morbius root 0 Mar 22 13:48 movies.txt


---

### Post by RichJacot on 2021-03-22
I've narrowed it down some more I think.

In your example I can write to /TestShare but not to /TestShare/Movies.

One of the shares from the NAS is Media.  Under that is that are TV, Movies, Kids, etc, etc.

I can cd to my /mnt/Media and touch a file and it creates it.  If I go to some of the subdirs in /mnt/Media, I CAN touch a file and some I cannot.

rjacot@ubuntu:/mnt/Media$ ll
total 40K
drwxr-xr-x 2 rjacot   0 Mar 22 14:11  4k/
drwxr-xr-x 2 rjacot   0 Mar 10 14:50  Christmas/
drwxr-xr-x 2 rjacot   0 Mar 22 13:55  Download/
-rwxr-xr-x 1 rjacot 31K Mar 22 11:26  .DS_Store
drwxr-xr-x 2 rjacot   0 Mar  7 19:15  Kids/
drwxr-xr-x 2 rjacot   0 Mar 22 13:56  Movies/
drwxr-xr-x 2 rjacot   0 Mar 22 10:50  TV/
drwxr-xr-x 2 rjacot   0 Dec 24 09:13  Videos/

Here are some that work and some that don't.

rjacot@ubuntu:/mnt/Media$ touch ./TV/test
touch: cannot touch './TV/test': No such file or directory
rjacot@ubuntu:/mnt/Media$ touch ./Download/test
rjacot@ubuntu:/mnt/Media$ touch ./4k/test
rjacot@ubuntu:/mnt/Media$ touch ./Movies/test
touch: cannot touch './Movies/test': No such file or directory
rjacot@ubuntu:/mnt/Media$ rm ./Download/test ./4k/test
rjacot@ubuntu:/mnt/Media$

The permissions look right, the same on all subdirs.   I don't understand why some subdirs are okay and some aren't.  Do you think it's a QNAP thing?  I've looked on the QNAP but like I mentioned, the NAS only shares the Media and I have RW there.

---

### Post by Morbius1 on 2021-03-22
CIFS is a virtual fileystem. It creates a "view" of the mounted share with a client users specified permissions setting which can be altered at any time just by remounting the share with different settings.

All the mounted shares have rjacot as the owner because you told it to be that way.
> //192.168.1.11/Media /mnt/Media cifs credentials=/home/rjacot/.smbcredentials1,[COLOR=#ff0000]**uid=rjacot**[/COLOR],noauto,x-systemd.automount 0 0

Those are not the permissions on the server. 

You need to do the equivalent of ll on the server to determine who has write access to the actual folder and subfolder being shared. On the server whoever is specified in your credentials file has write access to the parent folder but not to some of the subfolders.

---

### Post by RichJacot on 2021-03-23
I found spot in the QNAP shared folds section that has a dropdown for "Microsoft Networking Host Access" where I had to specify which hosts have this access.  I did that and it's working again without a reboot.  I'm not exactly sure why this "fixed" it but it is working again, without a reboot.  Like I mentioned the QNAP shares Media and Movies is under that.  If CIFS hosts weren't allowed, I don't know why I would write a file in Media and not Movies.  Once it catches up on my automated downloads I'll reboot and confirm it's still working.  To your point.  On the NAS itself, rjacot is part of the admin group and the admin group has RW on the shared folders.  admin is the owner and administrators is the group of all the shares on the QNAP.  Media and subfolders have that same ownership so I'm confused.

On my Ubuntu VM, is there a better option instead of CIFS?

I'll report back later today after I reboot and make sure it still works.

Thank you yet again.  ;-)

---

### Post by Morbius1 on 2021-03-23
> I don't know why I would write a file in Media and not Movies.  Once it  catches up on my automated downloads I'll reboot and confirm it's still  working.  To your point.  On the NAS itself, rjacot is part of the admin  group and the admin group has RW on the shared folders.  admin is the  owner and administrators is the group of all the shares on the QNAP.   Media and subfolders have that same ownership so I'm confused.
The only reason I asked is because of the nature of Samba.

Samba on the server is a gatekeeper. It determines which client can access the share and what that user can do. But it can't override the Linux ( if qnap uses Linux ) permissions of the folder itself. If I set up a folder that is accessible only to root and create a samba share of it allowing guest access Samba will not block guest access but Linux will.

I guess the only way to find out for sure is if it is possible to access the NAS through ssh - something like this in a terminal:
```
ssh admin@192.168.1.11
```
Then if it is running Linux you can drill down to the Media folder and do an ls -al to find out what permissions are on the subdirectories.

> On my Ubuntu VM, is there a better option instead of CIFS?
NFS. There I can't help you. I haven't used it in more than 20 years. Back then it was "use with prejudice" since it was not considered secure enough for enterprise use.

---

### Post by RichJacot on 2021-03-23
I'll stick with CIFS.

I rebooted and it appears to still be working fine.  

Thank you for your help. It got me pointed in directions I hadn't looked and got me to the solution!

---

