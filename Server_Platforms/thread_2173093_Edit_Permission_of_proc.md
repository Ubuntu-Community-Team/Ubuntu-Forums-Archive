---
title: "Edit Permission of /proc"
date: 2013-09-08
forum: Server Platforms
---

### Post by rL7M8d8 on 2013-09-08
Hello,

I am running Ubuntu 10.04.2 LTS.
I noticed that the directories in my /proc directory have their permission set to 500, while on a standard distribution it is set to 555. 
I am unable to simply chmod 555 the directories as I will get a message saying "Operation not permitted". 

I have searched other similar threads. Unfortunately, I have not found a solution.

Here is what I have in my /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>/dev/md2        /       ext3    errors=remount-ro,relatime      0       1
/dev/md4        /home   ext3    defaults,relatime       1       2
/dev/sda3       swap    swap    defaults        0       0
/dev/sdb3       swap    swap    defaults        0       0
proc            /proc   proc    nodev,noexec,nosuid            0      0
sysfs           /sys    sysfs   defaults                0       0
devtmpfs        /dev    devtmpfs        rw      0       0



```

Here is what I have with the command mount:

```
rootfs on / type rootfs (rw)/dev/root on / type ext3 (rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=writeback)
devtmpfs on /dev type devtmpfs (rw,relatime,size=32966764k,nr_inodes=8241691,mode=755)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
none on /lib/init/rw type tmpfs (rw,nosuid,relatime,mode=755)
/dev/md4 on /home type ext3 (rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=writeback)



```

Could anyone please provide me pointers regarding how to change the default permission for the directories in the /proc directory?

Thanks in advance!

---

### Post by M!K3_$ on 2013-09-08
Hello!

Good question! I didn't know the answer but I thought it was worthwhile to find out so I spent a chunk of time tonight on this.

I found the answer in the Kernel source documentation for the proc filesystem under section 4.1 (Mount Options):
[https://www.kernel.org/doc/Documentation/filesystems/proc.txt](https://www.kernel.org/doc/Documentation/filesystems/proc.txt)

> 
hidepid=0 means classic mode - everybody may access all /proc/<pid>/ directories
(default).

hidepid=1 means users may not access any /proc/<pid>/ directories but their
own.  Sensitive files like cmdline, sched*, status are now protected against
other users.  This makes it impossible to learn whether any user runs
specific program (given the program doesn't reveal itself by its behaviour).
As an additional bonus, as /proc/<pid>/cmdline is unaccessible for other users,
poorly written programs passing sensitive information via program arguments are
now protected against local eavesdroppers.

hidepid=2 means hidepid=1 plus all /proc/<pid>/ will be fully invisible to other
users.  It doesn't mean that it hides a fact whether a process with a specific
pid value exists (it can be learned by other means, e.g. by "kill -0 $PID"),
but it hides process' uid and gid, which may be learned by stat()'ing
/proc/<pid>/ otherwise.  It greatly complicates an intruder's task of gathering
information about running processes, whether some daemon runs with elevated
privileges, whether other user runs some sensitive program, whether other users
run any program at all, etc.


Simply set the mount option you want in your /etc/fstab file and after a reboot you should be good to go!

---

### Post by rL7M8d8 on 2013-09-08
Thanks for the reply!
Unfortunately, I was unable to figure out how to set the option.
I have tried the following fstab configurations to no avail:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>/dev/md2        /       ext3    errors=remount-ro,relatime      0       1
/dev/md4        /home   ext3    defaults,relatime       1       2
/dev/sda3       swap    swap    defaults        0       0
/dev/sdb3       swap    swap    defaults        0       0
**proc            /proc   proc    nodev,noexec,nosuid,hidepid=0           0      0**
sysfs           /sys    sysfs   defaults                0       0
devtmpfs        /dev    devtmpfs        rw      0       0

```

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/md2        /       ext3    errors=remount-ro,relatime      0       1
/dev/md4        /home   ext3    defaults,relatime       1       2
/dev/sda3       swap    swap    defaults        0       0
/dev/sdb3       swap    swap    defaults        0       0
**proc            /proc   proc    hidepid=0               0       0**
sysfs           /sys    sysfs   defaults                0       0
devtmpfs        /dev    devtmpfs        rw      0       0

```

```


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/md2        /       ext3    errors=remount-ro,relatime      0       1
/dev/md4        /home   ext3    defaults,relatime       1       2
/dev/sda3       swap    swap    defaults        0       0
/dev/sdb3       swap    swap    defaults        0       0
**proc            /proc   proc    defaults,hidepid=0              0       0**
sysfs           /sys    sysfs   defaults                0       0
devtmpfs        /dev    devtmpfs        rw      0       0



```

Was there something that I did wrong?

---

### Post by M!K3_$ on 2013-09-08
That should have done it. Perhaps the kernel which you are using isn't new enough. I unfortunately don't have the resources to test this myself currently.
If you have access to a test box or virtual machine try installing a 3.x series kernel and giving a shot.

I also see that Lucid (10.04) has packages available in the lucid-updates repository for back-ported 3.x series kernels.


Good Luck!

---

### Post by hawkmage on 2013-09-09
Once you have added the hidepid=0 mount option have you tried actually accessing the directories under /proc?  The documentation for the proc mount options is from around the same time as Ubuntu 10.04 so is through be relevant.  

The proc file system is a virtual file system and the file/directory modes may not show the actual permissions allowed.  I am downloading the 10.04 iso right now and will do a test install in a VM and test it to see of I see a difference.

Update:
Installed 10.04 and the hidepid doesn't seem to have an effect with the default install of 10.04.  Updateing to the latest 10.04 patches and will test again.

Update 2:
Even with the latest kernel for 10.04 the hidepid doesn't make a difference.  With 12.04 hidepid=2 does hide the PID directories that are not owned by the account accessing /proc, hisepid=1 allows you to see all of the PID directories but you can not access them and with hidepid=0 allows access all of the PID directories.  

What part of the /proc filesystem are you trying to access?

---

### Post by rL7M8d8 on 2013-09-09
> **hawkmage said:**
> Once you have added the hidepid=0 mount option have you tried actually accessing the directories under /proc?  The documentation for the proc mount options is from around the same time as Ubuntu 10.04 so is through be relevant.  

The proc file system is a virtual file system and the file/directory modes may not show the actual permissions allowed.  I am downloading the 10.04 iso right now and will do a test install in a VM and test it to see of I see a difference.

Update:
Installed 10.04 and the hidepid doesn't seem to have an effect with the default install of 10.04.  Updateing to the latest 10.04 patches and will test again.

Update 2:
Even with the latest kernel for 10.04 the hidepid doesn't make a difference.  With 12.04 hidepid=2 does hide the PID directories that are not owned by the account accessing /proc, hisepid=1 allows you to see all of the PID directories but you can not access them and with hidepid=0 allows access all of the PID directories.  

What part of the /proc filesystem are you trying to access?

Hello.

I am trying to access the directories within the /proc filesystem. It is my understanding that they represent the current running processes, and commands such as *ps *utilise the /proc to determine what processes are running.

I tried using ps -A w on a non-root account. I was unable to see any processes except my own, or daemon processes. I believe this is evidence that the permission was not fixed because with a 555 permission, I do not have such problems on non-root accounts.

---

### Post by hawkmage on 2013-09-10
That is odd here is the output from the 10.04 LTS VM I created:
```
hawkmage@u10server:~$ cat /etc/lsb-release DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

hawkmage@u10server:~$ mount | grep procproc on /proc type proc (rw,noexec,nosuid,nodev,hidepid=0)


hawkmage@u10server:~$ ps -fAw
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 17:19 ?        00:00:00 /sbin/init
root         2     0  0 17:19 ?        00:00:00 [kthreadd]
root         3     2  0 17:19 ?        00:00:00 [migration/0]
root         4     2  0 17:19 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 17:19 ?        00:00:00 [watchdog/0]
root         6     2  0 17:19 ?        00:00:00 [events/0]
root         7     2  0 17:19 ?        00:00:00 [cpuset]
root         8     2  0 17:19 ?        00:00:00 [khelper]
root         9     2  0 17:19 ?        00:00:00 [netns]
root        10     2  0 17:19 ?        00:00:00 [async/mgr]
root        11     2  0 17:19 ?        00:00:00 [pm]
root        12     2  0 17:19 ?        00:00:00 [sync_supers]
root        13     2  0 17:19 ?        00:00:00 [bdi-default]
root        14     2  0 17:19 ?        00:00:00 [kintegrityd/0]
root        15     2  0 17:19 ?        00:00:00 [kblockd/0]
root        16     2  0 17:19 ?        00:00:00 [kacpid]
root        17     2  0 17:19 ?        00:00:00 [kacpi_notify]
root        18     2  0 17:19 ?        00:00:00 [kacpi_hotplug]
root        19     2  0 17:19 ?        00:00:00 [ata/0]
root        20     2  0 17:19 ?        00:00:00 [ata_aux]
root        21     2  0 17:19 ?        00:00:00 [ksuspend_usbd]
root        22     2  0 17:19 ?        00:00:00 [khubd]
root        23     2  0 17:19 ?        00:00:00 [kseriod]
root        24     2  0 17:19 ?        00:00:00 [kmmcd]
root        26     2  0 17:19 ?        00:00:00 [khungtaskd]
root        28     2  0 17:19 ?        00:00:00 [kswapd0]
root        29     2  0 17:19 ?        00:00:00 [ksmd]
root        30     2  0 17:19 ?        00:00:00 [aio/0]
root        31     2  0 17:19 ?        00:00:00 [ecryptfs-kthrea]
root        32     2  0 17:19 ?        00:00:00 [crypto/0]
root        35     2  0 17:19 ?        00:00:00 [scsi_eh_0]
root        37     2  0 17:19 ?        00:00:00 [scsi_eh_1]
root        39     2  0 17:19 ?        00:00:00 [kstriped]
root        40     2  0 17:19 ?        00:00:00 [kmpathd/0]
root        41     2  0 17:19 ?        00:00:00 [kmpath_handlerd]
root        42     2  0 17:19 ?        00:00:00 [ksnapd]
root        43     2  0 17:19 ?        00:00:00 [kondemand/0]
root        44     2  0 17:19 ?        00:00:00 [kconservative/0]
root       147     2  0 17:19 ?        00:00:00 [scsi_eh_2]
root       169     2  0 17:19 ?        00:00:00 [jbd2/sda1-8]
root       170     2  0 17:19 ?        00:00:00 [ext4-dio-unwrit]
root       213     1  0 17:19 ?        00:00:00 upstart-udev-bridge --daemon
root       215     1  0 17:19 ?        00:00:00 udevd --daemon
root       327   215  0 17:19 ?        00:00:00 udevd --daemon
root       328   215  0 17:19 ?        00:00:00 udevd --daemon
root       329     2  0 17:19 ?        00:00:00 [kpsmoused]
root       330     2  0 17:19 ?        00:00:00 [usbhid_resumer]
syslog     485     1  0 17:19 ?        00:00:00 rsyslogd -c4
root       522     1  0 17:19 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       528     1  0 17:19 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       533     1  0 17:19 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       534     1  0 17:19 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       539     1  0 17:19 tty6     00:00:00 /sbin/getty -8 38400 tty6
root       542     1  0 17:19 ?        00:00:00 cron
daemon     543     1  0 17:19 ?        00:00:00 atd
root       588     1  0 17:19 tty1     00:00:00 /bin/login --        
root       616     2  0 17:19 ?        00:00:00 [flush-8:0]
root       628     1  0 17:19 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root       644     1  0 17:19 ?        00:00:00 /usr/sbin/sshd -D
hawkmage    722   588  0 17:19 tty1     00:00:00 -bash
root       759   644  0 17:22 ?        00:00:00 sshd: hawkmage [priv]
hawkmage    829   759  0 17:22 ?        00:00:00 sshd: hawkmage@pts/0 
hawkmage    830   829  0 17:22 pts/0    00:00:00 -bash
hawkmage    906   830  0 17:24 pts/0    00:00:00 ps -fAw
```

Since the proc files system is a virtual filesystem it doesn't respond to chmod the way a real file system would.

---

### Post by rL7M8d8 on 2013-09-11
Here is what I have

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

```

```

none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)

```

As root i can list all the processes fine, but I can't do so as a non-root user.

I haven't tried changing the kernel. I'll look into that this weekend if there is no other solution.

---

### Post by steeldriver on 2013-09-11
Hmm... do you have an /etc/init/mounted-proc.conf file? if so what are its contents?

---

### Post by hawkmage on 2013-09-11
The file mounted-proc.conf was not part of 10.04.  It is in the mountall package in 12.04 but not 10.04.

---

### Post by rL7M8d8 on 2013-09-11
> **steeldriver said:**
> Hmm... do you have an /etc/init/mounted-proc.conf file? if so what are its contents?

No, i do not have this file.

---

### Post by rL7M8d8 on 2013-09-12
Changing the kernel did solve the problem.
I guess it makes sense since proc is virtual.

Thanks everyone!

---

