---
title: "No space left on disk errors...but I know this isn't true..."
date: 2011-05-03
forum: Server Platforms
---

### Post by daled on 2011-05-03
Whenever I try to insert a record into MySQL or nano a file I keep getting errors that tell me that my disk is full.
[FONT=Verdana]
When I first boot the system and run [/FONT][FONT=Verdana][FONT=Courier New]df -h[/FONT] [/FONT][FONT=Verdana]returned is:
[/FONT]```

[FONT=Courier New]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  4.3G  130G   4% /
none                  997M  192K  997M   1% /dev
none                 1004M     0 1004M   0% /dev/shm
none                 1004M  280K 1003M   1% /var/run
none                 1004M     0 1004M   0% /var/lock[/FONT]

```[FONT=Verdana][FONT=Courier New]

[FONT=Verdana]After a day or two of little or no interaction with the system [FONT=Courier New]df -h[FONT=Verdana] looks like:
[/FONT][/FONT][/FONT][/FONT][/FONT]```

[FONT=Courier New]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  134G     0 100% /
none                  997M  192K  997M   1% /dev
none                 1004M     0 1004M   0% /dev/shm
none                 1004M  280K 1003M   1% /var/run
none                 1004M     0 1004M   0% /var/lock[/FONT]

```[FONT=Verdana][FONT=Courier New][FONT=Verdana][FONT=Courier New][FONT=Verdana][FONT=Courier New]

[FONT=Verdana]As you can see, the root filesystem somehow became full.  All I have no this system is the OS and a few websites (running Apache, MySQL, PHP).  Absolutely nothing that could take all 142 GB.  This same problem is occurring on a system with a 2 TB of storage.

Both systems are running Ubuntu Server 10.10

What could be the cause of the this and how can I ensure it doesn't happen again?
[/FONT][/FONT]
[/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by Demented ZA on 2011-05-03
I would first check my sub directories to see if the size matches up. Could be some suspiciously big files taking up your space.

I did the following on my system:
```
$ cd /
$ ls
bin   etc         initrd.img.old  lib64       mnt   ProgramData  selinux  tmp  vmlinuz
boot  home        lib             lost+found  opt   root         srv      usr  vmlinuz.old
dev   initrd.img  lib32           media       proc  sbin         sys      var  
$
```

From that I gather the following directories:
bin boot dev etc home lib lib32 lost+found media mnt opt ProgramData root sbin selinux srv sys tmp usr var

I omitted proc as it'll give reading errors.

I then did the followingto get my dir sizes:
```
$ sudo du -hs bin boot dev etc home lib lib32 lost+found media mnt opt ProgramData root sbin selinux sys tmp usr var

7.5M    bin
43M     boot
264K    dev
12M     etc
3.1G    home
312M    lib
12M     lib32
16K     lost+found
12K     media
8.0K    mnt
145M    opt
12K     ProgramData
100K    root
6.9M    sbin
4.0K    selinux
0       sys
88K     tmp
1.9G    usr
1.2G    var

```

It took a small while to yield answers on my bigger directories.

I'd first see if your results match up with your fdisk usage. If not, you're one step closer to isolating the cause of the problem.

---

### Post by dtfinch on 2011-05-03
There could be one file using all that space, like a log file. If something's logging errors in an infinite loop, it could fill up a drive very fast. And if the file's been deleted (often happens if something's rotating the logs, but failing to restart the service that's writing them), it can still consume space and grow until the program that has it open either closes it or quits.

The lsof command can give a list of open files, including deleted files.

---

### Post by daled on 2011-05-03
@Demented ZA
I ran those commands and got the following results:

```

[FONT=Courier New]7.7M    bin
20M     boot
192K    dev
7.8M    etc
17M     home
0       initrd.img
164M    lib
0       lib64
16K     lost+found
8.0K    media
4.0K    mnt
4.0K    opt
388M    root
5.2M    sbin
4.0K    selinux
8.0K    srv
0       sys
16K     tmp
987M    usr
2.6G    var
0       vmlinuz
4.0K    webmin-setup.out[/FONT]

```

@dtfinch
[FONT=Courier New]lsof [FONT=Verdana]yielded a long list of files, many without sizes.  There are three unusually large files, that it says are deleted.  The rest of the files that are open total no where near this number.

```

COMMAND    PID       USER   FD      TYPE DEVICE     SIZE/OFF    NODE NAME
...
php       1488       dale    1u      REG    8,1 139119775744 3670033 /tmp/tmpfbpDsZW (deleted)
php       1488       dale    2u      REG    8,1 139119775744 3670033 /tmp/tmpfbpDsZW (deleted)
php       1488       dale    5u      REG    8,1 139119775744 3670033 /tmp/tmpfbpDsZW (deleted)
...

```

Thanks for your help and suggestions.
[/FONT][/FONT]

---

### Post by dtfinch on 2011-05-03
Looks like a long-running php script, rather than a php web page. "ps -A v" might tell you the full command line, including which script is responsible, if you haven't killed it already.

---

### Post by daled on 2011-05-03
Thanks so much.  I targeted the php script and will fix it.

---

