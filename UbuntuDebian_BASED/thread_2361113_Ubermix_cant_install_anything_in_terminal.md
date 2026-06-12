---
title: "Ubermix: cant install anything in terminal"
date: 2017-05-12
forum: Ubuntu/Debian BASED
---

### Post by ethangolde2602 on 2017-05-12
Anytime I try to do basically anything Terminal shows this message. E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. I have  tried sudo dpkg --configure -a and the -f install thing. Both dont work. When I do them I get either the same message as before or this. dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error. I tried this too sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available and I tried sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status. None of it works it all gives the second or first message. Please help me.

---

### Post by Autodave on 2017-05-12
Is this a fresh install? Have you given it time to update itself with all the updates? What version did you install?

---

### Post by Impavidus on 2017-05-12
The input/output error indicates that dpkg is unable to read the file, despite the file being present and dpkg having permission to read it. This suggests file system damage. Try running a file system check. Use```
sudo touch /forcefsck
```and reboot, then the check should run automatically.

---

### Post by gordintoronto on 2017-05-13
Is the disk healthy?

---

### Post by ethangolde2602 on 2017-05-13
no clue what you mean gordin as for dave no clue as well,  buy impavidus when i type what u said it does this sudo: unable to resolve host system-4de54a

---

### Post by vasa1 on 2017-05-14
Maybe we should start from the beginning.

Please run the following commands, one at a time, and post the entire output, **including the commands and the terminal prompt**, here:

```
uname -a
```

```
lsb_release -a
```

```
env | grep XDG_CURRENT_DESKTOP
```

```
echo $DESKTOP_SESSION
```

```
df -h
```

```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl
```
None of the above commands require *sudo*.

---

### Post by ethangolde2602 on 2017-05-15
uname -a
```
Linux system-4de54a 4.10.0-14-generic #16~16.04.1-Ubuntu SMP Fri Mar 17 17:28:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
lsb_release -a
```
No LSB modules are available.Distributor ID:	Ubuntu
Description:	ubermix 3.22lv12 (Ubuntu 16.04.2 LTS)
Release:	16.04
Codename:	xenial
```

```
env | grep XDG_CURRENT_DESKTOP= XDG_CURRENT_DESKTOP=X-Cinnamon
```

```
echo $DESKTOP_SESSION= cinnamon
```
df -h
```

 Filesystem                       Size  Used Avail Use% Mounted on
udev                             1.9G     0  1.9G   0% /dev
tmpfs                            384M   16M  368M   5% /run
/dev/sda2                         15G  8.8G  5.9G  60% /ro
/root/dev/disk/by-label/USER      12G  559M   11G   6% /rw
aufs                              12G  559M   11G   6% /
tmpfs                            1.9G  1.7M  1.9G   1% /var/log
tmpfs                            1.9G  3.3M  1.9G   1% /tmp
tmpfs                            1.9G   28K  1.9G   1% /var/tmp
/root/ro/dev/disk/by-label/HOME  267G  8.2G  245G   4% /home
tmpfs                            1.9G  255M  1.7G  14% /dev/shm
tmpfs                            5.0M  4.0K  5.0M   1% /run/lock
tmpfs                            1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs                            384M   40K  384M   1% /run/user/1000
```

grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl=  
```
1	/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted     
     2 /etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
     3	/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
     4	/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
     5	/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
     6	/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
     7	/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
     8	/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
     9	/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    10	/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    11	/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    12	/etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list:deb [http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu](http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu) xenial main
    13	/etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list.save:deb [http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu](http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu) xenial main
    14	/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
    15	/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
    16	/etc/apt/sources.list.d/google-webdesigner.list:deb [arch=amd64] [http://dl.google.com/linux/webdesigner/deb/](http://dl.google.com/linux/webdesigner/deb/) stable main
    17	/etc/apt/sources.list.d/google-webdesigner.list.save:deb [arch=amd64] [http://dl.google.com/linux/webdesigner/deb/](http://dl.google.com/linux/webdesigner/deb/) stable main
    18	/etc/apt/sources.list.d/haraldhv-ubuntu-shotcut-xenial.list:deb [http://ppa.launchpad.net/haraldhv/shotcut/ubuntu](http://ppa.launchpad.net/haraldhv/shotcut/ubuntu) xenial main
    19	/etc/apt/sources.list.d/haraldhv-ubuntu-shotcut-xenial.list.save:deb [http://ppa.launchpad.net/haraldhv/shotcut/ubuntu](http://ppa.launchpad.net/haraldhv/shotcut/ubuntu) xenial main
    20	/etc/apt/sources.list.d/jklein-ubuntu-ubermix-xenial.list:deb [http://ppa.launchpad.net/jklein/ubermix/ubuntu](http://ppa.launchpad.net/jklein/ubermix/ubuntu) xenial main
    21	/etc/apt/sources.list.d/jklein-ubuntu-ubermix-xenial.list.save:deb [http://ppa.launchpad.net/jklein/ubermix/ubuntu](http://ppa.launchpad.net/jklein/ubermix/ubuntu) xenial main
    22	/etc/apt/sources.list.d/minecraft-installer-peeps-ubuntu-minecraft-installer-xenial.list:deb [http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu](http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu) xenial main
    23	/etc/apt/sources.list.d/minecraft-installer-peeps-ubuntu-minecraft-installer-xenial.list.save:deb [http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu](http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu) xenial main
    24	/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
    25	/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
    26	/etc/apt/sources.list.d/webupd8team-ubuntu-atom-xenial.list:deb [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial main
    27	/etc/apt/sources.list.d/webupd8team-ubuntu-atom-xenial.list.save:deb [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial main
    28	/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main
```

---

### Post by vasa1 on 2017-05-19
What does this part of the **lsb_release -a** output:```
Description:	ubermix 3.22lv12 (Ubuntu 16.04.2 LTS)
```mean?

In any case, please post the entire output of```
sudo apt-get update
```and```
sudo apt-get upgrade
``` You can press "N" at the prompt you get at the second command.

---

### Post by vasa1 on 2017-05-19
Moved thread here because of "the ubermix project, a lightweight Ubuntu build designed to be fast and easy to use" from [https://launchpad.net/~jklein/+archive/ubuntu/ubermix](https://launchpad.net/~jklein/+archive/ubuntu/ubermix). For more, see [http://ubermix.org/about.html](http://ubermix.org/about.html)

---

### Post by vasa1 on 2017-05-19
This lengthy quote from the [ubermix page]("http://ubermix.org/about.html") may explain why you "can't install anything in terminal":> While most focus on preventing problems with systems by locking them down, we chose to focus instead on rapid recovery and give students full access to their computer for experimentation and discovery. This enables both students and teachers to explore without fear, knowing that they can quickly get their system back to a default state (literally in seconds), should something go wrong. To accomplish this, we use a storage scheme called UnionFS. The way this works is as follows:

Logically, the storage on the system is divided into two slices: the system software and settings on the left, and the user's files on the right (commonly referred to as the user's "home"). Physically, however, the storage is actually divided into three slices. The two that we care about for this discussion are the left, labeled "User Changes" and "Default System". What UnionFS allows us to do is create a single logical storage space by combining two physical partitions, one of which is read only ("Default System" above) and one which is read/write ("User Changes" above). Any time the user makes any changes, they are all written to the "User Changes" space. No changes are ever made to the "Default System" space. So, when we want to restore the system to its default settings, we simply erase the "User Changes" space, and all is back to normal. The beauty of this is two-fold: the system can be restored to default settings in a matter of seconds, and the action is relatively non-destructive, as none of the user's documents in "User Home" are touched.

A system restore is accomplished by pressing a key at startup and selecting "Restore Factory Settings" from the menu that appears.

---

### Post by ethangolde2602 on 2017-05-19
no clue what that part means it just came out as the output. Here are the entire outputs for these two commands.

```
sudo apt-get update: 

Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Ign:3 [http://dl.google.com/linux/webdesigner/deb](http://dl.google.com/linux/webdesigner/deb) stable InRelease              
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]           
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Hit:7 [http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu](http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu) xenial InRelease       
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11.5 kB]           
Hit:10 [http://dl.google.com/linux/webdesigner/deb](http://dl.google.com/linux/webdesigner/deb) stable Release               
Get:11 [http://ppa.launchpad.net/haraldhv/shotcut/ubuntu](http://ppa.launchpad.net/haraldhv/shotcut/ubuntu) xenial InRelease [18.1 kB]
Get:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [916 B]        
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB] 
Hit:14 [http://ppa.launchpad.net/jklein/ubermix/ubuntu](http://ppa.launchpad.net/jklein/ubermix/ubuntu) xenial InRelease         
Hit:15 [http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu](http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu) xenial InRelease
Get:16 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial InRelease [17.6 kB]
Get:17 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner Sources [2,796 B]    
Get:19 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial InRelease [17.5 kB]
Get:20 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner amd64 Packages [3,340 B]
Get:21 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial/partner i386 Packages [3,620 B]
Get:22 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,453 B]
Hit:23 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [249 kB]
Get:25 [http://ppa.launchpad.net/haraldhv/shotcut/ubuntu](http://ppa.launchpad.net/haraldhv/shotcut/ubuntu) xenial/main amd64 Packages [460 B]
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [154 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Sources [5,672 B]
Get:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [540 kB]
Get:29 [http://ppa.launchpad.net/haraldhv/shotcut/ubuntu](http://ppa.launchpad.net/haraldhv/shotcut/ubuntu) xenial/main i386 Packages [460 B]
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [525 kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [218 kB]
Get:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [298 kB]
Get:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [191 kB]
Get:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [468 kB]
Get:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [71.2 kB]
Get:36 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [453 kB]
Get:37 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial/main amd64 Packages [3,280 B]
Get:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [183 kB]
Get:39 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:40 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial/main i386 Packages [3,276 B]
Get:41 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:42 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 Packages [8,928 B]
Get:43 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [7,996 B]
Get:44 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Translation-en [4,460 B]
Get:45 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources [27.6 kB]
Get:46 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:47 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Sources [2,604 B]
Get:48 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:49 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages [4,512 B]
Get:50 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [267 kB]
Get:51 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages [4,516 B]
Get:52 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en [1,968 B]
Get:53 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial/main amd64 Packages [608 B]
Get:54 [http://ppa.launchpad.net/webupd8team/atom/ubuntu](http://ppa.launchpad.net/webupd8team/atom/ubuntu) xenial/main i386 Packages [612 B]
Get:55 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [3,980 B]
Get:56 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons [2,716 B]
Get:57 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [254 kB]
Get:58 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [112 kB]
Get:59 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [54.5 kB]
Get:60 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [45.7 kB]
Get:61 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [115 kB]
Get:62 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [101 kB]
Get:63 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [59.1 kB]
Get:64 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:65 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Fetched 5,250 kB in 6s (797 kB/s)                                              


** (appstreamcli:3375): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

sudo apt-get upgrade: 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by ethangolde2602 on 2017-05-19
tried lsb-release -a again, I got this

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	ubermix 3.22lv12 (Ubuntu 16.04.2 LTS)
Release:	16.04
Codename:	xenial

---

### Post by QIII on 2017-05-19
Hello!

Based on vasa1's comments, it might be more likely that you will get better answers [here]("http://forums.ubermix.org/").

While we are happy to have you look for support here, ubermix is *not* an official Ubuntu flavor and they apparently have done a lot of modification.  We can't really speak to that.  Someone may yet come along with a great answer, but your chances are better on ubermix' forum.

Cheers!

---

