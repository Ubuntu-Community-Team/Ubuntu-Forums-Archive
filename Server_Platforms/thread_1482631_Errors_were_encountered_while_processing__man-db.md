---
title: "Errors were encountered while processing:  man-db"
date: 2010-05-13
forum: Server Platforms
---

### Post by hubblexplore on 2010-05-13
I run a 2 weeks old Ubuntu Server 10.04 LTS (32-bit). Today I wanted to check for eventual updates and install them with the following commands:
```
aptitude update
aptitude safe-upgrade
```Here is the error I get at the end of the update:
```
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.5.7-2) ...
Can't exec "/var/lib/dpkg/info/man-db.config": Permission denied at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of /var/lib/dpkg/info/man-db.config configure 2.5.7-2 failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 man-db
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
```Can someone please help me?

Thank you!

---

### Post by windependence on 2010-05-14
Try:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

without using sudo you don't have enough permission to execute the update.

-Tim

---

### Post by hubblexplore on 2010-05-14
I think there's no need for that, because I was already root with this command ```
sudo su
```

---

### Post by windependence on 2010-05-14
The problem is your /tmp directory is mounted nonexec and executables cannot be run from /tmp. Since apt extracts some packages to /tmp and runs them from there. Try this as root:

```
mount -o remount,exec /tmp
```

Then retry your updates. If you are concerned about security with /tmp, remount with noexec like this after you are done:

```
mount -o remount,noexec /tmp

```
More info here: [http://www.debian-administration.org/article/Making_/tmp_non-executable](http://www.debian-administration.org/article/Making_/tmp_non-executable)

-Tim

---

### Post by hubblexplore on 2010-05-14
It seems /tmp is not mounted already, I get this error:
```
mount: /tmp not mounted already, or bad option
```Don't know if this is the correct approach but I tried:
```
mount -o exec /tmp
```and in response got this error:
```
mount: unknown filesystem type 'none'
```Checked in webmin to see permissions of /tmp:
1777 Ownership, user:root, group:root

L.E.: I can run executables from /tmp, so it can't be mounted nonexec.

L.E.: /var/lib/dpkg/info/man-db.config had owner: root/root, permissions: 644, changed that to 755 and the update resumed ok.

---

### Post by Arachan on 2010-07-30
Greetings,

Sorry to resurrect a dead thread hubblexplore, but did you ever fix this? I now have the exact same problem.

Thanks,
Arachan.

---

### Post by spofer on 2010-09-26
I have the same problem - Did you manage to fix this?

---

### Post by spofer on 2010-10-10
Hello again,

I'm sorry for nagging - But i can't get past this. Does someone has an idea for how to solve it?

Thanks
Spofer

---

### Post by termin on 2010-11-06
me too, i need to know how to fix this so i can do my work again, please, we need some expert.

---

### Post by Paanini on 2010-11-29
Hi I had the same problem a while back. What I did was this :

1. Open a terminal, and login as root : 

```
su
Password :
```#

Make sure you type only 'su' and not 'sudo su'

Incase a root password does not exist, you'll have to assign one by typing :
```
sudo passwd root
<Enter your normal password here>
UNIX Password :
Re-Enter UNIX Passeord:
```

Now login to your root account by typing su

2. run :
```
dpkg --configure -a
```It should say something like rebuilding manual pages or something.

That did it for me !
I'd tried doing ```
sudo dpkg --configure -a
``` earlier but turns out there are some things sudo can't fix.
(For everything else, there's 'su' - Accepted wherever your mischief may take you :P)

Hope that works for you as well :)

---

### Post by kamilkamil on 2011-01-18
> **Paanini said:**
> Hi I had the same problem a while back. What I did was this :

1. Open a terminal, and login as root : 

```
su
Password :
```#

Make sure you type only 'su' and not 'sudo su'

Incase a root password does not exist, you'll have to assign one by typing :
```
sudo passwd root
<Enter your normal password here>
UNIX Password :
Re-Enter UNIX Passeord:
```

Now login to your root account by typing su

2. run :
```
dpkg --configure -a
```It should say something like rebuilding manual pages or something.

That did it for me !
I'd tried doing ```
sudo dpkg --configure -a
``` earlier but turns out there are some things sudo can't fix.
(For everything else, there's 'su' - Accepted wherever your mischief may take you :P)

Hope that works for you as well :)


i have the same problem.i tried everything u said.but still it wont work.it says..

root@kk:/home/kamil# sudo dpkg --configure -a
Setting up man-db (2.5.7-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db

oh yeah.im newbie in ubuntu

---

### Post by NewbieLearnLinux on 2011-06-15
I solved similar issue by killing the locking Process first (dpkg), then build the man-db.

soreco@server15:/opt$ su
[COLOR="orange"]Password: 
Added user root.[/COLOR]

root@server15:/opt# ps -ef | grep dpkg
[COLOR="orange"]root     **15279**     1  0 Jun15 ?        00:00:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst install
root     15292 **15279**  0 Jun15 ?        00:00:00 /bin/sh -e /var/lib/dpkg/tmp.ci/preinst install
root     23636 23613  0 09:22 pts/3    00:00:00 grep --color=auto dpkg[/COLOR]

root@server15:/opt# kill -9 15279

root@server15:/opt# ps -ef | grep dpkg
[COLOR="orange"]root     23639 23613  0 09:23 pts/3    00:00:00 grep --color=auto dpkg[/COLOR]

root@server15:/opt# exit
[COLOR="orange"]exit[/COLOR]

soreco@server15:/opt$ sudo dpkg --configure -a
[COLOR="orange"]Setting up man-db (2.5.9-4) ...
Building database of manual pages ...
Setting up wine1.2 (1.2.2-0ubuntu6) ...
procps stop/waiting
procps stop/waiting
Setting up wine (1.2.2-0ubuntu6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/COLOR]

Hope this helps, 
--NewbieLearnLinux

---

### Post by tripi on 2011-11-19
this worked for me, I have wiped out the cache and /var/log

$ sudo mkdir /var/cache/debconf

hope it helps

---

### Post by jeroenvermeulen on 2012-08-09
I had this "mount /tmp" problem on Ubuntu 12.04 LTS, installed via the Re-Install wizzard of LeaseWeb.nl.
The wizzard normally wants to create a separate partition for /tmp, but I tweaked the partition schedule because I want my /tmp to be just a subdir of / (the root).

After some searching I discovered this file:  [FONT="Courier New"] /etc/apt/apt.conf.d/50invoke[/FONT]
which was containing:
```
DPkg::Pre-Invoke{"mount -o remount,exec /tmp";};
DPkg::Post-Invoke {"mount -o remount /tmp";};

```

So I fixed the problem by doing:
```
mv /etc/apt/apt.conf.d/50invoke /etc/apt/apt.conf.d/.disabled.50invoke
```

I hope this helps some people out.

---

