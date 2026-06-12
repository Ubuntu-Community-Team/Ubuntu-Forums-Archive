---
title: "Root filesystem full? That's unpossible..."
date: 2010-06-05
forum: Server Platforms
---

### Post by garfonzo on 2010-06-05
Hey folks,

I thought I would install something on my server and when I did the apt-get install, it spit back the following:

```

Need to get 259MB of archives.
After this operation, 654MB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.

```

This shocked me because my OS sits on a 20GB hard drive with nothing else. I don't store anything in the home directories so I was confused. I tried the following command to get a feel for where the full directories were:

```
root@Jean:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              18G   18G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  2.0M 1005M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  184K 1007M   1% /dev
tmpfs                1007M     0 1007M   0% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-16-server/volatile
/dev/sdd1             294G  249G   31G  90% /garfonzo/320Alpha
/dev/sda1             294G  134G  146G  48% /garfonzo/320Charlie
/dev/sdb1             459G  320G  116G  74% /garfonzo/500Alpha
overflow              1.0M     0  1.0M   0% /tmp
/dev/sdh1             459G  320G  116G  74% /garfonzo/500Betta
/dev/sdf1             294G  249G   31G  90% /garfonzo/320Betta
/dev/sde1             294G  134G  146G  48% /garfonzo/320Delta

```

As you can see, /dev/sdc1 is full (this is the OS hard drive - size =18G used = 18GB). After some googling, I tried the command:

```
apt-get clean
```
as well as:
```
apt-get autoclean
```
and finally:
```
aptitude clean
```

Still no room.

I'm a little confused here. Any thoughts as to what is going on? 

Thanks!

---

### Post by Ryan Dwyer on 2010-06-05
Obviously the disk is full. Run this command to see where your data is:

cd /
du -h --max-depth=1

Then cd into the biggest directory and run the du command again to examine in. And so on.

---

### Post by garfonzo on 2010-06-05
Here's the output:

```
root@Jean:/# du -h --max-depth=1
607M    ./usr
214M    ./lib
52K     ./lost+found
60K     ./root
4.0K    ./selinux
1.4T    ./garfonzo
207M    ./var
0       ./tmp
5.6M    ./etc
8.0K    ./media
7.3M    ./sbin
4.0K    ./srv
26M     ./boot
4.0K    ./opt
6.1M    ./bin
4.0K    ./mnt
du: cannot access `./proc/26176/task/26176/fd/3': No such file or directory
du: cannot access `./proc/26176/task/26176/fdinfo/3': No such file or directory
du: cannot access `./proc/26176/fd/3': No such file or directory
du: cannot access `./proc/26176/fdinfo/3': No such file or directory
0       ./proc
696K    ./home
184K    ./dev
0       ./sys
2.8G    ./.Trash-0
1.4T    .

```

So, it would seem that /usr and /lib make up close to a GB, then /.Trash-0 pulls in the rear at 2.8GB. That still doesn't make up the 18GB for the hard drive. 

Do you think the /garfonzo at 1.4TB is a problem somehow? That is where I mount my 6 hard drives for data. So, technically they shouldn't be included in the calculation for the OS hard drive space.

---

### Post by garfonzo on 2010-06-05
Interesting..

I went into the .Trash-0 directory and found two video files which I must have deleted from the command line at some point. Deleting this gives me some hard drive room:

```

root@Jean:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              18G   16G  1.9G  89% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  2.0M 1005M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  184K 1007M   1% /dev
tmpfs                1007M     0 1007M   0% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-16-server/volatile
/dev/sdd1             294G  249G   31G  90% /garfonzo/320Alpha
/dev/sda1             294G  134G  146G  48% /garfonzo/320Charlie
/dev/sdb1             459G  320G  116G  74% /garfonzo/500Alpha
overflow              1.0M     0  1.0M   0% /tmp
/dev/sdh1             459G  320G  116G  74% /garfonzo/500Betta
/dev/sdf1             294G  249G   31G  90% /garfonzo/320Betta
/dev/sde1             294G  134G  146G  48% /garfonzo/320Delta

```

I'm still a bit confused as to where the other 16GB of data is.

---

### Post by Groodles on 2010-06-08
```

cd /garfonzo

ls -lt

```

Please post the output. My reasoning is, that 1.4TB is a large number and very easy to hide 16GB (0.016TB).

I'm guessing you've got files as well as the mount points for your HDDs in /garfonzo

---

### Post by oldfred on 2010-06-08
Were you running backups to a default inside root? That often is a cause.

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by VinDSL on 2012-10-21
> **oldfred said:**
> Were you running backups to a default inside root? That often is a cause.

#check for large files:
**[COLOR="Red"]sudo du -h --max-depth=1 / | grep '[0-9]G\>'[/COLOR]**   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
**[COLOR="Red"]gksudo nautilus /root/.local/share/Trash/files[/COLOR]**  # Be sure to enable viewing of hidden files.
Sorry for bumping a >= 2 year-old thread, but...

The above procedure(s) saved my bacon.  Thanks!  ;)

---

