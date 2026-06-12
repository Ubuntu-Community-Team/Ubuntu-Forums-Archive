---
title: "Can't install from backports"
date: 2005-06-24
forum: Repositories &amp; Backports
---

### Post by evs on 2005-06-24
For some reason I am unable to install anything from the backports using apt.  For example, I have Mono 1.0.5-1 installed, but 1.1.7-0 is in backports, which I checked by browsing manually at [http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/](http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/) .  I'm  guessing that this is an apt problem and not a problem backports repositories because I have tried different repos and nothing new shows up in Synaptic, it still shows the newest version of Mono as 1.0.5-1.  I'm running 32-bit Hoary on an AMD Sempron and here is my /etc/apt/sources.list:

```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```
It's pretty standard from the guide.  Anybody have any ideas what my problem might be?

Thanks

---

### Post by Xian on 2005-06-24
Open a terminal (Applications>System Tools>Terminal) & issue the commands below. 
What is the output?

```
$ sudo apt-get update
$ sudo apt-get install mono
```

---

### Post by evs on 2005-06-24
```
root@Acer:~# apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Fetched 4B in 6s (1B/s)
Reading package lists... Done
root@Acer:~# apt-get install mono
Reading package lists... Done
Building dependency tree... Done
mono is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


I then ran apt-cache show mono and this was the output (I cut out the descriptions to save space):
```
root@Acer:~# apt-cache show mono
Package: mono
Version: 1.1.7-0ubuntu4~5.04ubp1
Priority: optional
Section: interpreters
Maintainer: Debian Mono Group <pkg-mono-group@lists.alioth.debian.org>
Depends: mono-common (= 1.1.7-0ubuntu4~5.04ubp1), mono-jit (= 1.1.7-0ubuntu4~5.04ubp1)
Architecture: i386
Filename: dists/hoary-backports/universe/binary-i386/mono_1.1.7-0ubuntu4~5.04ubp1_i386.deb
Size: 1190
MD5sum: 6a0cb8411cc19a5f3a821ac79fe8891a
Description: ...
installed-size: 4

Package: mono
Priority: optional
Section: universe/interpreters
Installed-Size: 36
Maintainer: Debian Mono Group <pkg-mono-group@lists.alioth.debian.org>
Architecture: i386
Version: 1.0.5-1
Depends: mono-jit (= 1.0.5-1) | mono-mint (= 1.0.5-1), mono-utils (= 1.0.5-1), mono-mcs, mono-assemblies-arch
Filename: pool/universe/m/mono/mono_1.0.5-1_i386.deb
Size: 1368
MD5sum: 12142abb1389cd408afd9d09e3d1551b
Description: ...
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

Does that help at all?  Is there any way to force it to go with the higher version #?  Shouldn't it do that by default anyway?  Or is there something else I'm missing here?

Thanks for your help.

---

### Post by Xian on 2005-06-24
This is interesing. I gather from what you are describing that Apt tells you the latest mono version is installed but Synaptic lists the older release? Let's do the attempted upgrade with dpkg and see what happens.

Download these files to a newly created folder in your /home directory.
Also, make sure that you already have binfmt-support installed.

[mono_1.1.7-0ubuntu4~5.04ubp1_i386.deb](http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/mono_1.1.7-0ubuntu4~5.04ubp1_i386.deb)
[mono-common_1.1.7-0ubuntu4~5.04ubp1_i386.deb](http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/mono-common_1.1.7-0ubuntu4~5.04ubp1_i386.deb)
[mono-jit_1.1.7-0ubuntu4~5.04ubp1_i386.deb](http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/mono-jit_1.1.7-0ubuntu4~5.04ubp1_i386.deb)
[mono-assemblies-base_1.1.7-0ubuntu4~5.04ubp1_all.deb](http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/mono-assemblies-base_1.1.7-0ubuntu4~5.04ubp1_all.deb)

Open a terminal and cd to the folder location. 
Then issue the command below.
What happens?
```
$ sudo dpkg -i *
```

---

### Post by evs on 2005-06-24
[QUOTE=Xian]This is interesing. I gather from what you are describing that Apt tells you the latest mono version is installed but Synaptic lists the older release? [/QUOTE]

Actually,  I was trying to show that 'apt-cache show mono' shows both versions available, 1.0.5 in universe and 1.1.7 in backports.  But I only have 1.0.5 installed.  In Synaptic, only 1.0.5 is visible when I do a search.

[QUOTE=Xian]Then issue the command below.
What happens?
```
$ sudo dpkg -i *
```[/QUOTE]

Here's my output:
```
root@Acer:/downloads/repository# dpkg -i *
(Reading database ... 141615 files and directories currently installed.)
Preparing to replace mono 1.1.7-0ubuntu4~5.04ubp1 (using mono_1.1.7-0ubuntu4~5.04ubp1_i386.deb) ...
Unpacking replacement mono ...
Preparing to replace mono-assemblies-base 1.1.7-0ubuntu4~5.04ubp1 (using mono-assemblies-base_1.1.7-0ubuntu4~5.04ubp1_all.deb) ...
Unpacking replacement mono-assemblies-base ...
Preparing to replace mono-common 1.1.7-0ubuntu4~5.04ubp1 (using mono-common_1.1.7-0ubuntu4~5.04ubp1_i386.deb) ...
Unpacking replacement mono-common ...
Preparing to replace mono-jit 1.1.7-0ubuntu4~5.04ubp1 (using mono-jit_1.1.7-0ubuntu4~5.04ubp1_i386.deb) ...
Unpacking replacement mono-jit ...
Setting up mono-common (1.1.7-0ubuntu4~5.04ubp1) ...

Setting up mono-assemblies-base (1.1.7-0ubuntu4~5.04ubp1) ...
Setting up mono-jit (1.1.7-0ubuntu4~5.04ubp1) ...

Setting up mono (1.1.7-0ubuntu4~5.04ubp1) ...
``` 

Everything updated properly, and Synaptic also shows the newer version numbers as being installed.  But mono is not the only thing not updating properly, there's plenty more.  Any idea why apt-cache shows the packages available in the backports repo, but I can't actually install anything via apt from backports?

Thanks

---

### Post by Xian on 2005-06-24
[QUOTE=evs]Everything updated properly, and Synaptic also shows the newer version numbers as being installed.  But mono is not the only thing not updating properly, there's plenty more.  Any idea why apt-cache shows the packages available in the backports repo, but I can't actually install anything via apt from backports?
[/QUOTE]
I do not have an answer at present.
Open a terminal and issue this command:
```
$ sudo apt-get clean
$ sudo apt-get update
```
Now try to install a package again that you know has been updated.

---

### Post by evs on 2005-06-24
Still no luck.  Example: Firestarter: 1.0.1-1 shows in Synaptic, but 1.0.3-1 is available at [http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/](http://acm.cs.umn.edu/ubp/hoary-backports/universe/binary-i386/)
Hopefully I can get this working it's very frustrating.  Thanks for your help.  I'm going to try this very thing on my desktop later and see what happens (I've been having these troubles on my laptop).  I haven't used the desktop machine in a few days, but I know for a fact that I never had this problem before on that machine because I already had Mono 1.1.7 installed.

---

### Post by Kapre on 2005-06-24
Hiyall!

I think there is something wrong with the repos because I'm also experiencing some problems using my Synaptic Pkg Manager (I have a lot of error).

Are we up for maintenance today?

Kapre

---

### Post by Xian on 2005-06-24
[QUOTE=Kapre]I think there is something wrong with the repos because I'm also experiencing some problems using my Synaptic Pkg Manager (I have a lot of error).[/QUOTE]
That issue does not affect this topic.
evs showed an update session that finished properly.

---

### Post by jdong on 2005-06-24
[QUOTE=Xian]I do not have an answer at present.
Open a terminal and issue this command:
```
$ sudo apt-get clean
$ sudo apt-get update
```
Now try to install a package again that you know has been updated.[/QUOTE]

Try **apt-cache policy mono** and post the results.

Try an **apt-get dist-upgrade**, and see if that'll bring you up-to-date.

Note that when Synaptic/APT gives you the Not Authenticated warning, you tell it to continue installing.

---

### Post by Xian on 2005-06-24
I don't know why, but we had a member [POST](http://www.ubuntuforums.org/showthread.php?p=221099#post221099) in another thread similar to this that using the following mirror for backports fixed their issue. I never could understand it but I'll offer it since there have been no new ideas presented.

```
deb http://acm.cs.umn.edu/ubp/ hoary-backports main universe multiverse restricted
```

---

### Post by evs on 2005-06-24
[QUOTE=jdong]Try **apt-cache policy mono** and post the results.

Try an **apt-get dist-upgrade**, and see if that'll bring you up-to-date.

Note that when Synaptic/APT gives you the Not Authenticated warning, you tell it to continue installing.[/QUOTE]

```
root@Acer:~# apt-cache policy mono
mono:
  Installed: 1.1.7-0ubuntu4~5.04ubp1
  Candidate: 1.1.7-0ubuntu4~5.04ubp1
  Version table:
 *** 1.1.7-0ubuntu4~5.04ubp1 0
        500 http://acm.cs.umn.edu hoary-backports/universe Packages
        100 /var/lib/dpkg/status
     1.0.5-1 0
       1000 http://us.archive.ubuntu.com hoary/universe Packages
root@Acer:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` 

I also tried **apt-cache policy firestarter** to see what the output would be, since I had already manually downloaded the .deb's and updated mono with dpkg -i:
```
root@Acer:~# apt-cache policy firestarter
firestarter:
  Installed: 1.0.1-1ubuntu2
  Candidate: 1.0.1-1ubuntu2
  Version table:
     1.0.3-1.1~5.04ubp1 0
        500 http://acm.cs.umn.edu hoary-backports/universe Packages
 *** 1.0.1-1ubuntu2 0
       1000 http://us.archive.ubuntu.com hoary/universe Packages
        100 /var/lib/dpkg/status
``` 

Does that shed anymore light on this?  Thanks.

---

### Post by evs on 2005-06-24
[QUOTE=Xian]I don't know why, but we had a member [POST](http://www.ubuntuforums.org/showthread.php?p=221099#post221099) in another thread similar to this that using the following mirror for backports fixed their issue. I never could understand it but I'll offer it since there have been no new ideas presented.

```
deb http://acm.cs.umn.edu/ubp/ hoary-backports main universe multiverse restricted
```[/QUOTE]

Thanks, it was worth a shot, but I actually tried that very thing a few hours ago, and nothing changed.  Still no luck  ](*,) .  That post was similar, but his problem was that they actually showed up as ready to be updated in Synaptic.  Mine shows that I actually have the latest version installed according to Synaptic/Apt, but I can physically see that there are newer versions available in the backports repositories.

---

### Post by jdong on 2005-06-24
Aha, you must've pinned official Ubuntu repos with priority 1000, overriding backports. Edit /etc/apt/perferences.

---

### Post by evs on 2005-06-24
[QUOTE=jdong]Aha, you must've pinned official Ubuntu repos with priority 1000, overriding backports. Edit /etc/apt/perferences.[/QUOTE]
 
I've never actually touched /etc/apt/preferences, so I don't know what to edit.  Here is my current file:

```
Package: *
Pin: release a=hoary, v=5.04
Pin-Priority: 1000

Package: *
Pin: release a=hoary-security, v=5.04
Pin-Priority: 1000

Package: *
Pin: release a=hoary-updates, v=5.04
Pin-Priority: 1000
``` 

What needs to be changed?  Thanks for your help.

---

### Post by jdong on 2005-06-24
[QUOTE=evs]I've never actually touched /etc/apt/preferences, so I don't know what to edit.  Here is my current file:

```
Package: *
Pin: release a=hoary, v=5.04
Pin-Priority: 1000

Package: *
Pin: release a=hoary-security, v=5.04
Pin-Priority: 1000

Package: *
Pin: release a=hoary-updates, v=5.04
Pin-Priority: 1000
``` 

What needs to be changed?  Thanks for your help.[/QUOTE]

Remove everything :)

---

### Post by Xian on 2005-06-24
[QUOTE=jdong]Remove everything :)[/QUOTE]
If this is the default setting, as must be the case since evs didn't modify this file, then why isn't everyone having these same issues?

---

### Post by evs on 2005-06-24
Well, that did it.  Here come 39 upgraded packages now.  Thanks a lot for all your help guys.  I definitely appreciate it.

---

### Post by jdong on 2005-06-24
[QUOTE=Xian]If this is the default setting, as must be the case since evs didn't modify this file, then why isn't everyone having these same issues?[/QUOTE]


Sometimes it's a Synaptic thing... maybe playing around with Force Versions too much would cause it.

---

### Post by Xian on 2005-06-24
[QUOTE=jdong]Sometimes it's a Synaptic thing... maybe playing around with Force Versions too much would cause it.[/QUOTE]
So then it's possible the situation would just reoccur?
Perhaps a recommended preferences config would be in order.

To this line of thought, if the following was added to the apt preferences (assuming the acm.cs.umn.edu backport repo is used) would it then prevent evs (or anyone else for that matter) from having to deal with this situation again?

```
Package: *
Pin: origin acm.cs.umn.edu
Pin-Priority: 1000
```

---

