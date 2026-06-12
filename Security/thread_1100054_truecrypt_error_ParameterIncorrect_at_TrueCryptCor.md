---
title: "truecrypt error: ParameterIncorrect at TrueCrypt::CoreUnix::MountVolume:517"
date: 2009-03-18
forum: Security
---

### Post by samdc on 2009-03-18
Hi,

I want to start using truecrypt to encrypt one of my drives.  I was able to install the new version 6.1a from the truecrypt website without any issues.  The thing is when I try to use it and encrypt a volume, I get this error message: "ParameterIncorrect at TrueCrypt::CoreUnix::MountVolume:517".  Did anybody get this error before?  Am I the only one experiencing this error.  I tried to google but didn't get much results.

---

### Post by lensman3 on 2009-03-18
The code in Truecrypt hints that the user doesn't have stroke to create a directory in which you have read and execute permission for the newly created mount point.  An error get thrown (517) because it is greater that 255. 

Are you sure you can create a directory where you think you should? Can you do a "touch filename" in the directory/location where the encrypted container is supposed to go.

Also truecrypt.org has a great Linux help area.

---

### Post by antdude on 2011-07-29
> **samdc said:**
> Hi,

I want to start using truecrypt to encrypt one of my drives.  I was able to install the new version 6.1a from the truecrypt website without any issues.  The thing is when I try to use it and encrypt a volume, I get this error message: "ParameterIncorrect at TrueCrypt::CoreUnix::MountVolume:517".  Did anybody get this error before?  Am I the only one experiencing this error.  I tried to google but didn't get much results.Did you ever get this resolved? I am having this problem right now!

I think something broke from my daily apt-get update and upgrade in my old Debian box since TrueCrypt v7.0a used to work (last usage was a few weeks ago) through command line:

$ ./truecrypt /foo/bar/tc
Enter mount directory [default]:
Enter password for /foo/bar/tc:
Enter keyfile [none]:
Protect hidden volume (if any)? (y=Yes/n=No) [No]:
Enter your user password or administrator password:
Error: ParameterIncorrect at TrueCrypt::CoreUnix::MountVolume:569
    
I tried again:
$ ./truecrypt /foo/bar/tc
Enter mount directory [default]:
Enter password for /foo/bar/tc:
Enter keyfile [none]:
Protect hidden volume (if any)? (y=Yes/n=No) [No]:
Enter your user password or administrator password:
Error: device-mapper: create ioctl failed: Device or resource busy
Command failed

dmesg showed (seen this one before when TC worked so I think we can ignore this?):
[1960840.725830] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

/var/log/syslog showed:
Jul 29 12:46:18 FOObar kernel: [1960840.725830] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

$ uname -a
Linux FOObar 2.6.32-5-686 #1 SMP Mon Jun 13 04:13:06 UTC 2011 i686 GNU/Linux

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1               280003    185924     79623  71% /
tmpfs                     5120         0      5120   0% /lib/init/rw
tmpfs                   207424       952    206472   1% /run
udev                   1032780         0   1032780   0% /dev
tmpfs                   414848         0    414848   0% /run/shm
/dev/sda5             14421344   1202752  12486032   9% /foo
/dev/sda6              4807056   3415608   1147264  75% /usr
/dev/sda7               964500    615088    300416  68% /var
/dev/sda8               964500     17692    897812   2% /tmp
/dev/sda9              4807056    209148   4353724   5% /usr/local
/dev/sda11            47383396  42299732   2676728  95% /extra
/dev/sda12              918322     16452    852874   2% /others
/dev/sdb1             14436960   4528984   9174612  34% /storage
Note the missing /media/truecrypt1.

$ ls /media
cdrom  cdrom0  floppy  floppy0  truecrypt1
Oh, it's there.

$ ./truecrypt -d
$ ps aux |grep truecrypt
root      5298  0.0  0.0  22072  1244 ?        S    12:46   0:00 /foo/bar/truecrypt --core-service
root      5301  0.0  0.0  71496  1764 ?        Ssl  12:46   0:00 /foo/bar/truecrypt --core-service
root      5567  0.0  0.0  22072  1244 ?        S    12:46   0:00 /foo/bar/truecrypt --core-service
root      5569  0.0  0.0  71496  1704 ?        Ssl  12:46   0:00 /foo/bar/truecrypt --core-service
ant       8770  0.0  0.0   3348   744 pts/2    S+   12:51   0:00 grep --color truecrypt

I tried to dismount with root/sudo, but same problem so I had to kill them all. :(

However, I still can access /media/truecrypt! Help! 

Thank you in advance. :)

P.S. I changed some directories/paths for extra security when posting.

---

