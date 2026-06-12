---
title: "FTP Directory from another Machine"
date: 2010-11-29
forum: Server Platforms
---

### Post by jaya28inside on 2010-11-29
Geeez, i tot by using FTP Directory mounted, thus
it could make my life easier. And the fact, it's not.

OMG. 
Is there anyone have ever solved what I encountered?

well, I'm putting in the **/etc/fstab** file
to be like this;

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/omega-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e0b93d1a-3cc4-4e3d-8593-b2c5c74bd011 /boot           ext2    defaults
  0       2
/dev/mapper/omega-swap_1 none            swap    sw              0       0
curlftpfs#ofadmin:P4ssw0rd@192.168.1.27/craftsan/nas/crm/backup /usr/share/serverware/windowsShare fuse rw,allow_other,auto,user,_netdev 0 0

```

and yes after i test it out
using ;
```
$> mount -a
```

it could be mounted perfectly!
but once I do operating someting on it, on that 
**windowsShare** directory seems failed as always!

even when i do copying files from another directory into it.
like this one

```
$> cp /home/superadmin/something.txt /usr/share/serverware/windowsShare 
```

it gave me this one;

```
 cp closing something.txt Input/Output error 
```

**waaah...!!**

in a conclusion;
 every file i copy, move, to that mounted directory will fail.
 and the error given is that Input/Output error message only.

Is it this effect, due to the script i put on fstab is wrongly?

NB: I'm using Ubuntu Server here.

---

### Post by ikonia on 2010-11-30
can you please re-think your question and try to post it in a clear way as a clear question.

you reference ftp and windows shares - they are two separate things, which is causing you the problem ?


does the output of the command 

```
 mount 
``` show the file system as for your ftp file server as mounted ?

---

### Post by jaya28inside on 2010-11-30
> **ikonia said:**
> can you please re-think your question and try to post it in a clear way as a clear question.

you reference ftp and windows shares - they are two separate things, which is causing you the problem ?


does the output of the command 

```
 mount 
``` show the file system as for your ftp file server as mounted ?

here the result...

> 
superadmin@alpha:~$ sudo mount
[sudo] password for superadmin:
/dev/mapper/alpha-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
curlftpfs#[ftp://ofadmin:P4ssw0rd@192.168.1.27/craftsan/nas/crm/backup/](ftp://ofadmin:P4ssw0rd@192.168.1.27/craftsan/nas/crm/backup/) on /usr/s
hare/serverware/windowsShare type fuse (rw,noexec,nosuid,nodev,allow_other)
/dev/sda1 on /boot type ext2 (rw)

---

### Post by jaya28inside on 2010-12-02
so how? is there 
anybody know about this?

Even when I tried to changed the last line at the 
/etc/fstab into like this

```
curlftpfs#ofadmin:P4ssw0rd@192.168.1.27/craftsan/nas/crm/backup /usr/share/serve
rware/windowsShare fuse rw,allow_other,auto,user,direct_io 0 0
```

and then mount 'em all. It works (mounted)...!
But, if I copy something into it.... it gave me I/O error, again, and again... Jeeez.....

does anybody know which part of it 
that makes this error occured?

---

### Post by jaya28inside on 2010-12-02
I heard that if the Input Output error occured, probably it's due to the lack of the freespace.

So then I execute this command

```
$> df -h
```

and the output was...

```

superadmin@alpha:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/alpha-root
                      9.2G  2.7G  6.1G  31% /
none                 1001M  176K 1000M   1% /dev
none                 1005M     0 1005M   0% /dev/shm
none                 1005M  300K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda1             228M   48M  168M  23% /boot
curlftpfs#ftp://ofadmin:P4ssw0rd@192.168.1.27/craftsan/nas/crm/backup/
                      7.5T     0  7.5T   0% /usr/share/serverware/windowsShare 
```

it's all HAve enough freespace...!
So then what's the thing I forgotten? :(

---

