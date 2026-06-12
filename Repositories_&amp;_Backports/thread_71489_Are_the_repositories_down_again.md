---
title: "Are the repositories down again?"
date: 2005-10-03
forum: Repositories &amp; Backports
---

### Post by Lurgid on 2005-10-03
I'm getting a bunch of "cannot initiate the connection" errors and such when doing apt-get update. I've fixed the backports thing, commented all but the archive.ubuntu.com ones, changed from us.archive.* to just archive.*, as well as trying ftp instead of http.

Before I pull my hair out, am I doing something wrong? Or are the repositories hosed right now? I'm on deadline here and I've got to get mysql and php installed.

---

### Post by Dennis Laumen on 2005-10-03
I am using the breezy repositories (including universe and multiverse) and eveything is working fine here.

---

### Post by Lurgid on 2005-10-03
I guess i should mention I'm using Hoary.

---

### Post by matthew on 2005-10-03
Just checked. All works fine for me with Hoary. Here's my sources.list for comparison.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports and extras
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by Lurgid on 2005-10-03
Matthew,
I just tried yours copied and pasted, and still nada.
It uses http so everything goes through port 80, right? shouldn
't be any weird setting on my router giving me problems, should there?
Here's my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:90:0B:00:65:4D  
inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::290:bff:fe00:654d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:40815 errors:0 dropped:0 overruns:0 frame:0
TX packets:16612 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:23037131 (21.9 MiB)  TX bytes:1028378 (1004.2 KiB)
Interrupt:15 Base address:0xe400 
lo        Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:134 errors:0 dropped:0 overruns:0 frame:0
TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:96903 (94.6 KiB)  TX bytes:96903 (94.6 KiB)

```

---

### Post by Lurgid on 2005-10-03
Oh, and here are the errors I'm getting:
```
Err http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Cannot initiate the connection to ubuntu-backports.mirrormax.net:80 (0.0.0.10). - connect (22 Invalid argument)
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Cannot initiate the connection to ubuntu-backports.mirrormax.net:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Cannot initiate the connection to ubuntu-backports.mirrormax.net:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Cannot initiate the connection to ubuntu-backports.mirrormax.net:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Cannot initiate the connection to ubuntu-backports.mirrormax.net:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://security.ubuntu.com hoary-security Release.gpg
Cannot initiate the connection to security.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary Release.gpg
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-updates Release.gpg
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-backports Release.gpg
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Ign http://security.ubuntu.com hoary-security Release
Ign http://security.ubuntu.com hoary-security/main Packages
Ign http://security.ubuntu.com hoary-security/restricted Packages
Ign http://security.ubuntu.com hoary-security/main Sources
Ign http://security.ubuntu.com hoary-security/restricted Sources
Ign http://security.ubuntu.com hoary-security/universe Packages
Ign http://security.ubuntu.com hoary-security/universe Sources
Err http://security.ubuntu.com hoary-security/main Packages
Cannot initiate the connection to security.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://security.ubuntu.com hoary-security/restricted Packages
Cannot initiate the connection to security.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://security.ubuntu.com hoary-security/main Sources
Cannot initiate the connection to security.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://security.ubuntu.com hoary-security/restricted Sources
Cannot initiate the connection to security.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://security.ubuntu.com hoary-security/universe Packages
Cannot initiate the connection to security.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://security.ubuntu.com hoary-security/universe Sources
Cannot initiate the connection to security.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Ign http://archive.ubuntu.com hoary Release
Ign http://archive.ubuntu.com hoary-updates Release
Ign http://archive.ubuntu.com hoary-backports Release
Ign http://archive.ubuntu.com hoary/main Packages
Ign http://archive.ubuntu.com hoary/restricted Packages
Ign http://archive.ubuntu.com hoary/main Sources
Ign http://archive.ubuntu.com hoary/restricted Sources
Ign http://archive.ubuntu.com hoary/universe Packages
Ign http://archive.ubuntu.com hoary/universe Sources
Ign http://archive.ubuntu.com hoary/multiverse Packages
Ign http://archive.ubuntu.com hoary/multiverse Sources
Ign http://archive.ubuntu.com hoary-updates/main Packages
Ign http://archive.ubuntu.com hoary-updates/restricted Packages
Ign http://archive.ubuntu.com hoary-updates/main Sources
Ign http://archive.ubuntu.com hoary-updates/restricted Sources
Ign http://archive.ubuntu.com hoary-backports/main Packages
Ign http://archive.ubuntu.com hoary-backports/restricted Packages
Ign http://archive.ubuntu.com hoary-backports/universe Packages
Ign http://archive.ubuntu.com hoary-backports/multiverse Packages
Err http://archive.ubuntu.com hoary/main Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary/restricted Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary/main Sources
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary/restricted Sources
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary/universe Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary/universe Sources
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary/multiverse Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary/multiverse Sources
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-updates/main Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-updates/restricted Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-updates/main Sources
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-updates/restricted Sources
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-backports/main Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-backports/restricted Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-backports/universe Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Err http://archive.ubuntu.com hoary-backports/multiverse Packages
Cannot initiate the connection to archive.ubuntu.com:80 (0.0.0.10). - connect (22 Invalid argument)
Reading package lists...

```

---

### Post by Mustard on 2005-10-03
The mirrormax backports repository has been shut down and replaced by a new 'official' backports.  That should explain why you can't connect to the mirrormax backports.

[http://www.ubuntuforums.org/showthread.php?t=69681](http://www.ubuntuforums.org/showthread.php?t=69681)

After I removed the mirrormax backports the other day, it was necessary for me to go through and 'force version' on a number of packages that I had upgraded from mirrormax, and force them to a version that was available through the new repositories.  You may encounter the same issue, I don't know.

---

### Post by Lurgid on 2005-10-03
[QUOTE=Mustard]The mirrormax backports repository has been shut down and replaced by a new 'official' backports.  That should explain why you can't connect to the mirrormax backports.

[http://www.ubuntuforums.org/showthread.php?t=69681](http://www.ubuntuforums.org/showthread.php?t=69681)

After I removed the mirrormax backports the other day, it was necessary for me to go through and 'force version' on a number of packages that I had upgraded from mirrormax, and force them to a version that was available through the new repositories.  You may encounter the same issue, I don't know.[/QUOTE]

The backports are pointing to the official backports, now. If you look at my listing though, I can't even "initiate the connection" to archive.ubuntu.com.

How do you "force version."?

---

### Post by Lurgid on 2005-10-03
I think I figured out the problem, but still no clue as to how to fix it. On both my ubuntu box and my windows machine. archive.ubuntu.com is resolving to 0.0.0.10. Does Comcast block net repositories?

---

### Post by Lurgid on 2005-10-03
Well, i switched resolv.conf to use "nameserver <my ISPs domain server>" instead of 192.168.1.1 and now it's working. It's not a permanent fix, but it doesn't matter since I'm moving this to a different network after it's done, anyway.

---

