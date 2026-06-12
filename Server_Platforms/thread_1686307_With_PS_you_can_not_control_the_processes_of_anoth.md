---
title: "With PS you can not control the processes of another user"
date: 2011-02-12
forum: Server Platforms
---

### Post by bellotranzi on 2011-02-12
Hi everybody,
 
I have a problem with the permission of the directories under /proc, they are readable and accessible only by Owner (they have permission 500 instead of the usual 555) As a consequence, the processes are visible only to the Owners or to Root. For exampleif I want to check if there is mysql
 
# ps -ef | grep mysqld
mysql 2611 1 0 12:14 ? 00:00:06 /usr/sbin/mysqld
 
I see it only with the user mysql or with root because the directory has permission 500
dr-x------ 6 mysql mysql 0 2011-02-11 12:14 /proc/2611/
 
this problem obstacles the functioning of some applications that should check the existence of some processes managed by other users. At the beginning all was working well. But after a while the problem appeared and I don’t know which is the reason of it.
 
 
Can you tell me how to restore the standard management of permissions of / proc?]
 
I have a Ubuntu server Maverick 10:10.

Thanks.

---

### Post by bellotranzi on 2011-02-13
Any help please?!?!?!?
 
has it never happened to anyone?
 
thanks!

---

### Post by sammie12340 on 2011-02-13
got any file manager ? trough their you can change the rights.
OR you have to change every thing with the chmod command.

---

### Post by CharlesA on 2011-02-13
Normally you don't mess with any files in the /proc directory.

See [here]("http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379") for an explanation.

Why are you looking at /proc to manage services?

Normally you'd stop a service such as mysql by running this:

```
sudo service mysql stop
```

---

### Post by bellotranzi on 2011-02-13
@ sammie12340 
I can't change permissions:
 
# chmod 555 /proc/2896
chmod: changing permissions of `/proc/2896': Operation not permitted 
 
Because /proc it is a pseudo file system read only , directly managed by kernel

@ CharlesA 
 
You are right, usually /proc is not used by any applications.
The problem is that with the 'ps' command i can see only the processes of the user i'm logged in.
The explanation of this is that directories under /proc doesn't  have the usual 555 permissions but 500 ( and ps command can see only these directories)

I don't want to stop mysql service.It was only an example : i mean that if i make a 'ps' with a different user than mysql user , i can't see the deamon mysqld.
 
The problem is that i've got some applications that doesn't work because they use 'ps' to control if there are some processes and they don't find them even if actually they are running(with another user)

---

### Post by CharlesA on 2011-02-13
I usually use ps aux | grep somename

Maybe try that?

---

### Post by bellotranzi on 2011-02-13
It's the same.With 'ps -aux' i see only my processes. That 's the point!

---

### Post by CharlesA on 2011-02-13
You'd have to explain it a little better.

I just tryed running ps aux and got this:

```
charles@thor:~$ ps aux | head -n 1
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
charles@thor:~$ ps aux | grep apache2
www-data  8399  0.0  0.0 122528  5408 ?        S    06:35   0:00 /usr/sbin/apache2 -k start
www-data  8400  0.0  0.0 122528  5408 ?        S    06:35   0:00 /usr/sbin/apache2 -k start
www-data  8401  0.0  0.0 122528  5408 ?        S    06:35   0:00 /usr/sbin/apache2 -k start
www-data  8402  0.0  0.0 122528  5408 ?        S    06:35   0:00 /usr/sbin/apache2 -k start
www-data  8403  0.0  0.0 122668  5952 ?        S    06:35   0:00 /usr/sbin/apache2 -k start
charles   9332  0.0  0.0   7624   924 pts/1    S+   08:37   0:00 grep --color=auto apache2
root     29027  0.0  0.1 122528 10204 ?        Ss   Feb11   0:02 /usr/sbin/apache2 -k start

```

```
charles@lucid:~$ ps aux | grep mysql
mysql    20345  0.0  3.8 177888 19264 ?        Ssl  07:18   0:02 /usr/sbin/mysqld

```

Both of those outputs are normal.

What are you using to check to see if a process is running?

---

### Post by bellotranzi on 2011-02-13
if i do a  'ps' i see only my processes:
 
adriano:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
adriano  30540  0.0  0.0  70624  1484 ?        S    17:14   0:00 sshd: adriano@pts/1
adriano  30541  0.0  0.3  27848  6752 pts/1    Ss   17:14   0:00 -bash
adriano  31807  0.0  0.0  18208  1140 pts/1    R+   17:42   0:00 ps aux

and 

adriano@ks357749:~$ ps aux | grep mysql
 
i don't see anything with my user , i can't see the processes of mysql

---

### Post by CharlesA on 2011-02-13
Is that user the same user that was created when Ubuntu was installed?

See [here]("http://askubuntu.com/questions/18862/ps-aux-as-non-root-doesnt-show-all-processes").

EDIT: I am running Lucid and the permissions in /proc are correct - 444 or 555.

---

### Post by bellotranzi on 2011-02-13
Thanks for the link, it was the same problem in 10.04 version.
 
The user i'm using has been created just after the O.S. installation.

---

### Post by CharlesA on 2011-02-13
Can you post the output of this please:

```
cat /etc/fstab
```

It should look something like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
[COLOR="Blue"]proc            /proc           proc    nodev,noexec,nosuid 0       0[/COLOR]
# / was on /dev/sda1 during installation
UUID=97c62292-541c-49af-9dd0-29a9d057da73 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7684e910-dd6b-416b-bf90-7221f0e7f6d1 none            swap    sw              0       0

```

---

### Post by bellotranzi on 2011-02-13
the FS /proc is mounted with defaul options :

```
~$ cat /etc/fstab
/dev/sda1 / ext4 errors=remount-ro 0 1
/dev/sda2 /home ext4 defaults 0 2
/dev/sda3 none swap defaults 0 0
proc /proc proc defaults 0 0
sysfs /sys sysfs defaults 0 0
dev /dev devtmpfs rw 0 0
```

---

### Post by CharlesA on 2011-02-13
Hrm, Can you post the outpost of this:

```
mount
```

Should get something back like this:
```

~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
[COLOR="Blue"]proc on /proc type proc (rw,noexec,nosuid,nodev)[/COLOR]
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
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)

```

---

### Post by bellotranzi on 2011-02-13
```

# mount
rootfs on / type rootfs (rw)
/dev/root on / type ext4 (rw,relatime,errors=remount-ro,barrier=1,data=ordered)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev on /dev type devtmpfs (rw,relatime,size=1006296k,nr_inodes=251574,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
/dev/sda2 on /home type ext4 (rw,relatime,barrier=1,data=ordered)

```

---

### Post by CharlesA on 2011-02-13
Interesting. Was this a clean install or upgrade?

---

### Post by bellotranzi on 2011-02-13
a clean install

---

### Post by CharlesA on 2011-02-13
Hrm. I just had someone else check their fstab and /proc on 10.10 and it looks the same as the one I posted above.

Try editing the proc entry in fstab to read:

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
```

Be sure to make a backup first. :)

---

### Post by bellotranzi on 2011-02-13
i did the modify in fstab 
 
```

# cat /etc/fstab
/dev/sda1       /       ext4    errors=remount-ro       0       1
/dev/sda2       /home   ext4    defaults                0       2
/dev/sda3       none    swap    defaults                0       0
proc            /proc   proc    nodev,noexec,nosuid     0       0
sysfs           /sys    sysfs   defaults                0       0
dev             /dev    devtmpfs        rw      0       0

```
 
and i rebooted the server but /proc still have 500 permission
 
 
output of mount commend still is:
 
```

# mount
/dev/root on / type ext4 (rw,relatime,errors=remount-ro,barrier=1,data=ordered)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev on /dev type devtmpfs (rw,relatime,size=1006296k,nr_inodes=251574,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
/dev/sda2 on /home type ext4 (rw,relatime,barrier=1,data=ordered)

```
 
The options in fstab are the default one.

---

### Post by bellotranzi on 2011-02-14
anyone can help me please?!?!?thanks!

---

### Post by CharlesA on 2011-02-14
I don't know why it's set the permissions to /proc like that.

Try booting off a livecd and check the permissions of /proc there.

---

### Post by bellotranzi on 2011-02-15
We can't do it because is a dedicate server witha provider...

---

