---
title: "Help New Server Saga"
date: 2008-07-20
forum: Server Platforms
---

### Post by sil3nt on 2008-07-20
Hi all,
       On the weekend I converted my father-in-laws Windows desktop into a ubuntu 8.04 server. He was keen on doing so as I had done the same at home and was running a virtuallized windows domain environment.

Unlike my own setup this one has turned into a nightmare, first off it would not accept a serial (fixed now) secondly it seems to be installed ok but I can't get access to the VMware console.

I have tried to telnet to 902 but I cant get a connection? when I run vmware mui install it fails saying VMware server is not installed but its running....

When I envoke the vmware command from the command line I get the following 
```
/usr/lib/vmware/bin/vmware: error while loading shared libraries: libXi.so.6: cannot open shared object file: No such file or directory

``` 

I have a feeling this has something to do with ia32-libs which I cant seem to install. I am using 64 Bit Hardware with the 32bit install of hardy.

Any help would be appreciated I feel like banging my head against the wall I have spent so much time messing with it :(

---

### Post by tinny on 2008-07-20
What Ubuntu version? Hardy LTS server?

What version of VMWare??? You may have to run a patch.

Check out this sticky...

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

I followed these instructions for my Ubuntu Hardy LTS server and have been happy with the install. (You will have to re-run the patch after a Kernel / Headers update)

---

### Post by sil3nt on 2008-07-20
Wow that was quick, I am using Ubuntu 8.04 LTS and Vmware Server 1.06.

I can't seem to install the ia32 libs I get the following

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs

```

I have the universal repos enabled i am pretty certain? I just did a apt-get update but still no joy...

---

### Post by sil3nt on 2008-07-20
Here is my enabled repo list 

```
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://au.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy main restricted

```

No idea why I can't find this damned library

---

### Post by tinny on 2008-07-20
> **sil3nt said:**
> Wow that was quick, I am using Ubuntu 8.04 LTS and Vmware Server 1.06.

I can't seem to install the ia32 libs I get the following

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs

```

I have the universal repos enabled i am pretty certain? I just did a apt-get update but still no joy...

Umm...

This tells me its in the "universe"

[http://packages.ubuntu.com/search?suite=hardy&searchon=names&keywords=ia32-libs](http://packages.ubuntu.com/search?suite=hardy&searchon=names&keywords=ia32-libs)

Have you tried this?

```

sudo apt-get clean
sudo apt-get update
sudo install ia32-libs

```

If this doesn't work can you please post the contents of your /etc/apt/sources.list file

---

### Post by sil3nt on 2008-07-20
No go unfortunately :(

here is the contents of my sources.list

```
#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hary main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hard main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted univrse multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

```

---

### Post by tinny on 2008-07-20
What is the output of...

```

sudo apt-get update

```

---

### Post by sil3nt on 2008-07-20
Here you go ...

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.24-16-server is already the newest version.
xinetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
dave@ubuntuserver:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_AU
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_AU
Hit http://au.archive.ubuntu.com hardy Release.gpg
Ign http://au.archive.ubuntu.com hardy/main Translation-en_AU
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_AU
Hit http://us.archive.ubuntu.com hardy Release
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_AU
Ign http://security.ubuntu.com hardy-security/universe Translation-en_AU
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com hardy-security Release
Ign http://au.archive.ubuntu.com hardy/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com hardy/universe Translation-en_AU
Ign http://au.archive.ubuntu.com hardy/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com hardy-updates Release.gpg
Ign http://au.archive.ubuntu.com hardy-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/universe Translation-en_AU
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages
Ign http://au.archive.ubuntu.com hardy-updates/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://au.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://au.archive.ubuntu.com hardy/main Packages
Hit http://au.archive.ubuntu.com hardy/restricted Packages
Hit http://au.archive.ubuntu.com hardy/main Sources
Hit http://au.archive.ubuntu.com hardy/restricted Sources
Hit http://au.archive.ubuntu.com hardy/universe Packages
Hit http://au.archive.ubuntu.com hardy/universe Sources
Hit http://au.archive.ubuntu.com hardy/multiverse Packages
Hit http://au.archive.ubuntu.com hardy/multiverse Sources
Hit http://au.archive.ubuntu.com hardy-updates/main Packages
Hit http://au.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://au.archive.ubuntu.com hardy-updates/main Sources
Hit http://au.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://au.archive.ubuntu.com hardy-updates/universe Packages
Hit http://au.archive.ubuntu.com hardy-updates/universe Sources
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done

```

---

### Post by sil3nt on 2008-07-21
I'm lost should I consider starting again? and reinstall the whole OS?

I have removed and reinstalled vmware also with no joy.

---

### Post by tinny on 2008-07-21
:confused:

Maybe first start a "installing ia32 package" thread.

---

### Post by windependence on 2008-07-21
Just FYI reinstalling isn't a universal fix especially on Linux/Unix. :)

I posted some good tutorials in your ia32 thread. See what you think. Unfortunately, I have found Ubuntu not to be the best OS for a VMware host. CentOS and SuSE have been best for me, but of course, YMMV.

You may want to try VMware 1.05 or 1.04 instead of 1.06. I have had some issues with it.

I am curious though how you fixed the serial # issue because I just ran into this the other day and just used 1.05 instead to fix it, but I would love to know if there is a real fix for that.

-Tim

---

