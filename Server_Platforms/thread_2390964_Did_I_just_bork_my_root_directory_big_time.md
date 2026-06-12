---
title: "Did I just bork my root directory big time?"
date: 2018-05-04
forum: Server Platforms
---

### Post by Drone4four on 2018-05-04
Yikes! Did I just totally bork my system? 

I was innocently changing user and group ownership permissions for my new Apache public_html directories for my 3 vhosts. But in the process I accidentally pressed enter on my absolute home root directory.  Here is what I entered:
```
$ sudo chown -R <regular_user>:<group> /
```
With my cursor all the way on the right, I meant to press backspace but pressed enter instead.  My shell&#8217;s output included a million lines which looked something like this:
```

... 
chown: changing ownership of '/var/lib/lxcfs/proc/stat': Operation not permitted 
...

```
So it looks like the system still protects directories from / even if a sudo user attempts to change user and group permissions.  `ls -la` on my root directory now reads:
```
 $ ls -la
total 88
drwxr-xr-x  23 root   root       4096 May  4 12:15 .
drwxr-xr-x  23 root   root       4096 May  4 12:15 ..
drwxr-xr-x   2 root   root       4096 Apr 26 05:15 bin
drwxr-xr-x   4 <user> <group> 4096 Apr 26 05:15 boot
drwxr-xr-x  16 <user> <group>  3620 May  4 12:15 dev
drwxr-xr-x  94 root   root       4096 May  4 14:32 etc
drwxr-xr-x   3 root   root       4096 May  4 10:41 home
lrwxrwxrwx   1 root   root         33 Apr 26 05:11 initrd.img -> boot/initrd.img-4.15.0-20-generic
lrwxrwxrwx   1 root   root         33 Apr 26 05:11 initrd.img.old -> boot/initrd.img-4.15.0-20-generic
drwxr-xr-x  20 root   root       4096 May  4 11:31 lib
drwxr-xr-x   2 root   root       4096 Apr 26 05:10 lib64
drwx------   2 root   root      16384 Apr 26 05:14 lost+found
drwxr-xr-x   2 root   root       4096 Apr 26 05:10 media
drwxr-xr-x   2 root   root       4096 Apr 26 05:10 mnt
drwxr-xr-x   2 root   root       4096 Apr 26 05:10 opt
dr-xr-xr-x 109 <user> <group>     0 May  4 12:15 proc
drwx------   5 root   root       4096 May  4 11:03 root
drwxr-xr-x  26 root   root        900 May  4 13:19 run
drwxr-xr-x   2 root   root       4096 Apr 26 05:12 sbin
drwxr-xr-x   2 root   root       4096 May  4 10:21 snap
drwxr-xr-x   2 root   root       4096 Apr 26 05:10 srv
dr-xr-xr-x  13 root   root          0 May  4 14:34 sys
drwxrwxrwt  10 root   root       4096 May  4 14:34 tmp
drwxr-xr-x  10 root   root       4096 Apr 26 05:10 usr
drwxr-xr-x  14 root   root       4096 May  4 11:18 var
lrwxrwxrwx   1 root   root         30 Apr 26 05:11 vmlinuz -> boot/vmlinuz-4.15.0-20-generic
lrwxrwxrwx   1 root   root         30 Apr 26 05:11 vmlinuz.old -> boot/vmlinuz-4.15.0-20-generic
$
```
It looks like `boot`, `dev` and `proc` are affected. Does this mean my O/S won't boot now?  It would obviously be very stupid to invoke:
```
$ sudo chown -R root:root / 
```
But what about this?
```
$ sudo chown -R root:root  /boot/ 
```

Would this fix it?

Do I have to scrap this server and start over?

Can someone please advise?

Thanks for your attention.

---

### Post by SeijiSensei on 2018-05-04
You don't know what might have gone awry in directories below the root.  I'd reinstall a new image rather than try and fix the problem piecemeal.

/proc is a filesystem that is recreated at boot.  I believe /dev is the same.  All of /boot should be owned by root:root, as should all of the directories at the top of the tree.  You could try changing the ownership of /boot and rebooting.

Take a look at a directory like /usr/.  What user owns /usr/bin and the files therein?  Even more problematic would be directories like /var/lib where many subdirectories are owned by root, but some are owned by pseudo-users like "sddm" and "avahi-autoipd".  These are daemon processes that start as root but switch to an unprivileged user when running for security reasons.  They need to be able to write into these directories.

---

### Post by QIII on 2018-05-04
Sometimes people resist the recommendation to reinstall because it is very rarely really necessary.  In the case of compromise or a wholesale change to ownership and permissions, I heartily second SeijiSensei's advice.

This is one of two cases where blasting off and nuking from orbit really is the best answer.

---

### Post by Drone4four on 2018-05-04
Phew!  (Or maybe it’s slightly premature to be so relieved?)

I checked inside `/usr` (along with some of its subdirectories) and all the files are showing as owned by root and grouped in root.

Since `/proc` and `/dev` ownership permissions are re-assigned at boot, the only outstanding directory (from the perspective of top level `/`) is `/boot`. So I dutifully entered:
```
$ sudo chown -R root:root /boot
```
I held my breath, rebooted and no kernel panic or any permissions errors. Everything seems to have loaded just fine.  Apache is serving one of my vhosts and it continues to hum along as it should without issue: [https://www.angeles4four.info/](https://www.angeles4four.info/) 

I was going to ask you people next about what I could to to “stress test” or verify that there are no corrupted files and directories below the top level directories at `/`. I have a tech friend who I asked about this and he wasn’t sure about a Linux equivalent to Windows’ `sfc c:/`.  I did some searching on Google which turned up [a pretty ancient Ubuntu forum thread]("https://ubuntuforums.org/showthread.php?t=855615") where one user recommends taking a look at the man page for `fsck`, while other users explain that if there was a serious permissions issue, Linux would let me know. 

What else would some of you recommend I could try to verify the integrity of my file system?

On a somewhat unrelated note but still worth mentioning, my mode permissions were untouched and remain healthy.  See here:
```
$ stat -c '%A %a %n' /*
drwxr-xr-x 755 /bin
drwxr-xr-x 755 /boot
drwxr-xr-x 755 /dev
drwxr-xr-x 755 /etc
drwxr-xr-x 755 /home
lrwxrwxrwx 777 /initrd.img
lrwxrwxrwx 777 /initrd.img.old
drwxr-xr-x 755 /lib
drwxr-xr-x 755 /lib64
drwx------ 700 /lost+found
drwxr-xr-x 755 /media
drwxr-xr-x 755 /mnt
drwxr-xr-x 755 /opt
dr-xr-xr-x 555 /proc
drwx------ 700 /root
drwxr-xr-x 755 /run
drwxr-xr-x 755 /sbin
drwxr-xr-x 755 /snap
drwxr-xr-x 755 /srv
dr-xr-xr-x 555 /sys
drwxrwxrwt 1777 /tmp
drwxr-xr-x 755 /usr
drwxr-xr-x 755 /var
lrwxrwxrwx 777 /vmlinuz
lrwxrwxrwx 777 /vmlinuz.old
```
I suppose maybe if everything here were set to `lrwxrwxrwx` then nuking my Droplet would be necessary, but it’s not.

Thanks for your attention.

---

### Post by Drone4four on 2018-05-08
Could it be AppArmor that is responsible for protecting user and group permissions even from a sudo user?

---

