---
title: "ubuntu-server update issue..."
date: 2007-11-16
forum: Virtualisation
---

### Post by Zack McCool on 2007-11-16
I am running vmware-server on Feisty Fawn 32-Bit.  It works great, but I have a wierd issue...

The Ubuntu update manager is showing an update available for vmware-server.  From Version 1.0.4-1feisty1 to 1.0.4-1feisty1

I have already installed it, a couple of times, actually, but the update never goes away.

I'd love to find a way to eliminate this, as it is quite annoying...

---

### Post by dj1120 on 2007-11-16
I have the same issue as well I can't make the update notification go away!!

---

### Post by MrFSL on 2007-11-16
Are there any errors?

What is the output if you try to do an upgrade from the command line:

EX.
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Zack McCool on 2007-11-16
> **MrFSL said:**
> Are there any errors?

What is the output if you try to do an upgrade from the command line:

EX.
```
sudo apt-get update
sudo apt-get upgrade
```

No errors.  Here is the output of sudo apt-get upgrade (ran update, too, but no need for that here.  worked fine)...

```

joe@barada:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  vmware-server
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 79.4MB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://archive.canonical.com feisty-commercial/main vmware-server 1.0.4-1feisty2 [79.4MB]
Fetched 79.4MB in 4m4s (324kB/s)                                               
Preconfiguring packages ...
(Reading database ... 202932 files and directories currently installed.)
Preparing to replace vmware-server 1.0.4-1feisty1 (using .../vmware-server_1.0.4-1feisty2_i386.deb) ...
Stopping VMware virtual machines...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
Unpacking replacement vmware-server ...
Setting up vmware-server (1.0.4-1feisty2) ...

Configuration file `/etc/pam.d/vmware-authd'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** vmware-authd (Y/I/N/O/D/Z) [default=N] ? D

Configuration file `/etc/pam.d/vmware-authd'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** vmware-authd (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/pam.d/vmware-authd ...
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
   Starting VMware virtual machines...                                 done


```

---

### Post by Zack McCool on 2007-11-19
No ideas from anyone?

I suppose I can live with it, it's not much more than an annoyance...

---

### Post by kaffe_02 on 2007-11-23
I am getting the same thing with vmware server showing up in my update list.

Im using 7.04 I wonder if this issue is fixed in 7.10?

---

### Post by Ankara23 on 2007-12-01
I have this same problem, however I am using gutsy 64bit...

---

### Post by portmanteau on 2007-12-01
I'm in the same boat.  7.10, 32-bit.  vmware-server wants to upgrade from 1.0.4-1gutsy1 to 1.0.4-1gutsy1.

---

### Post by AndersGnistrup on 2007-12-02
Jeps, same problem. I got a ubuntu gutsy (32 bit) so the the problem is also present in 7.10

---

### Post by Delvien on 2007-12-02
Its prob. an error or a mistake in the packaging, just wait it out, it will either go away, or allow you to update it in a couple days.

ubuntu devs are good about getting things working in a decent amount of time, it's patience that is the problem : ). (I'm guilty too ! :P)

---

### Post by Ankara23 on 2007-12-02
Actually it's some kind of error in the upgrade system itself.
My vmware starts and runs....and it **is** the latest version.
Update manager just thinks that it is not somehow.
and if you look at the screenshot I posted above, you can see that update 
manager wants to update to the *same* version.

---

### Post by MrFSL on 2007-12-02
Please post the output to the following:
```
cat /etc/apt/sources.list
```

Also, how did you initially install vmware-server?

---

### Post by Ankara23 on 2007-12-02
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://archive.canonical.com/ubuntu gutsy partner
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
# deb http://giss.tv/~vale/ubuntu64 ./

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs

```

How did I initially install it? I cant remember, but I *may* very well have downloaded it from the vmware site itself....just not sure.
(this was quite a while ago, it's not the version I currently have installed)

---

### Post by MrFSL on 2007-12-02
Alright here is my suggestion and I hope it works for you.

I had a similar issue happen quite awhile ago and I had installed vmware-server using a 3rd party installation script.

What I wanted to do at the time was uninstall and reinstall using the package directly downloaded from vmware's website:
[http://download3.vmware.com/software/vmserver/VMware-server-1.0.3-44356.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.3-44356.tar.gz)

However, I could not get the original to uninstall correctly. So I downloaded the package, extracted it, and ran the installation script.

It installed, compiled the modules for my kernel, and problem went away.

When asked if I wanted to keep my current configuration I chose "NO" - and used the setup script to redefine my setup configurations.

Hope this helps someone. It is not the a good fix (I would much rather uninstall the older version first) but it worked for me.

---

### Post by StevenHarper on 2007-12-03
I am seeing the same problem, my installation was NEVER from the downloaded version, it came from the Repositories.

I'm running Ubuntu 7.10 32bit

As above 1.0.4-1gutsy1 is stuck in apt

Synaptic gives the hint that

1.0.4-1gutsy1(gutsy)

needs to be updated against the current

1.0.4-1gutsy1(now)

---

### Post by kevykev on 2007-12-03
I have this issue too. I also tried a 

```
sudo dpkg-reconfigure vmware-server 
```

but to no avail...

---

### Post by ferrocene on 2007-12-03
deleteme!

---

### Post by ferrocene on 2007-12-03
I as well have the same problem, vmware-server 1.0.4-1:

```
ferrocene@linux-desktop:~$ dpkg -s vmware-server
Package: vmware-server
Status: install ok installed
Priority: optional
Section: partner/misc
Installed-Size: 127612
Maintainer: VMware Build Team <vmware-builds@vmware.com>
Architecture: amd64
Version: 1.0.4-1gutsy1
Depends: netbase, xinetd | netkit-inetd | inetd, update-inetd, vmware-server-kernel-modules, psmisc, ia32-libs (>= 0.2), ia32-libs-gtk, libc6-i386 (>= 2.3.4-1), libssl0.9.7
```


I read on the bugtraq site that Gutsy comes with SSL 0.9.8, and vmware is looking for 0.9.7, if that helps anyone.

[https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/173114](https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/173114)

[https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/173261](https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/173261)

---

### Post by Ankara23 on 2007-12-03
Yeah it's still there....went past the updates today for cairo as well, and tried to update the vmware server too, and failed again (or maybe not, when I start vmware server it SAYS it's the newest version)

Oh I tried a uninstall/reinstall...still a problem

---

### Post by scxtt on 2007-12-03
odd, i don't have it ... i haven't done a system-wide update tho and i do see one for libssl0.9.8 ...

i'm using 1.0.4 built from the .tar.gz ...
installed on 7.10 64-bit ubuntu ...
i did add the repo so that i could install vmware-server via apt ... not sure why i didn't.

```
scxtt @ vmware [ /home/scxtt ]
:> aptitude search vmware
p   vmware-server                   - Free virtual machine server from VMware
p   vmware-server-kernel-modules    - vmware-server kernel module dependency pac
p   vmware-server-kernel-modules-2. - vmware-server modules for Linux (kernel 2.
p   vmware-server-kernel-source     - Kernel modules for VMware Server.
i A xserver-xorg-video-vmware       - X.Org X server -- VMware display driver
scxtt @ vmware [ /home/scxtt ]
:> whereis vmware
vmware: /usr/bin/vmware /etc/vmware /usr/lib/vmware /usr/lib64/vmware /usr/share/man/man4/vmware.4.gz /usr/share/man/man1/vmware.1.gz
```

---

### Post by kowal on 2007-12-04
Same problem here..

---

### Post by sfagerhaug on 2007-12-04
I have the same issue on 7.10.    It apparently is taking them a while to fix this one.    In the meantime,  I unchecked the Canonical "partner" entry on  the Third Party tab in the Software Sources.     I'll probably wait a month before adding it back in.   That means I won't get updates on other third party packages like vmware-server, but I'd rather not have the annoyance right now.

<rant>I wish there was a way to tell package manager that one doesn't want a particular update and have it stick.</rant>

---

### Post by Ankara23 on 2007-12-04
OK, with todays updated packages (*other* packages, i.e.  open office updated, etc) the vmware server cleared out, and no longer appears as a pending update...whatever it was, they FIXED it...
So to sfagerhaug, you might want to enable canonical partner and do a full update today,
it might very well clear out for you.
(although I am using 64bit Ubuntu, the other versions might not all be fixed at the same time as mine was)
However, even if  today doesnt fix yours, it's ON THE WAY!! :)

---

