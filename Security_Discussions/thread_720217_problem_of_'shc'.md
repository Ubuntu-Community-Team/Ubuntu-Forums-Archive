---
title: "problem of 'shc'"
date: 2008-03-10
forum: Security Discussions
---

### Post by ccclay on 2008-03-10
I learn from internet that shc creates a stripped  binary  executable  version  of  the script specified with -f on the command line. The binary version will get a .x extension appended and will usually  be  a  bit  larger  in size than the original ascii code. Generated C source code is saved in a  file  with  the extension .x.c . In its simplest form "shc -f script" will produce "script.x" and "script.x.c"; the "script.x" is your executable and the "x.c" is the source code.

So I tried and have below result.

I make a script that will touch a file 123, the name of the script is named as test. Codes are :
#!/bin/sh
touch 123

Then I do this in terminal.
shc -f test

terminal responsed :
test.x.c:90:22: error: sys/stat.h: No such file or directory
test.x.c:91:23: error: sys/types.h: No such file or directory
test.x.c:93:19: error: errno.h: No such file or directory
test.x.c:94:19: error: stdio.h: No such file or directory
test.x.c:95:20: error: stdlib.h: No such file or directory
test.x.c:96:20: error: string.h: No such file or directory
test.x.c:97:18: error: time.h: No such file or directory
test.x.c:98:20: error: unistd.h: No such file or directory
test.x.c: In function 'key_with_file':
test.x.c:160: error: array type has incomplete element type
test.x.c:161: error: array type has incomplete element type
test.x.c:167: warning: incompatible implicit declaration of built-in function 'memset'
test.x.c: In function 'chkenv':
test.x.c:212: warning: incompatible implicit declaration of built-in function 'sprintf'
test.x.c:213: warning: assignment makes pointer from integer without a cast
test.x.c:217: warning: incompatible implicit declaration of built-in function 'strlen'
test.x.c:221: warning: incompatible implicit declaration of built-in function 'strdup'
test.x.c:224: warning: incompatible implicit declaration of built-in function 'sscanf'
test.x.c:236:24: error: sys/ptrace.h: No such file or directory
test.x.c:238:22: error: sys/wait.h: No such file or directory
test.x.c:239:19: error: fcntl.h: No such file or directory
test.x.c:240:20: error: signal.h: No such file or directory
test.x.c: In function 'untraceable':
test.x.c:259: warning: incompatible implicit declaration of built-in function 'sprintf'
test.x.c:262: error: 'O_RDWR' undeclared (first use in this function)
test.x.c:262: error: (Each undeclared identifier is reported only once
test.x.c:262: error: for each function it appears in.)
test.x.c:262: error: 'O_EXCL' undeclared (first use in this function)
test.x.c:263: error: 'errno' undeclared (first use in this function)
test.x.c:263: error: 'EBUSY' undeclared (first use in this function)
test.x.c:264: error: 'PTRACE_ATTACH' undeclared (first use in this function)
test.x.c:266: error: 'SIGCONT' undeclared (first use in this function)
test.x.c:269: error: 'SIGKILL' undeclared (first use in this function)
test.x.c:271: warning: incompatible implicit declaration of built-in function '_exit'
test.x.c:279: warning: incompatible implicit declaration of built-in function '_exit'
test.x.c: In function 'xsh':
test.x.c:292: error: 'time_t' undeclared (first use in this function)
test.x.c:292: error: expected expression before ')' token
test.x.c:293: error: expected expression before ')' token
test.x.c:308: warning: incompatible implicit declaration of built-in function 'calloc'
test.x.c:324: warning: incompatible implicit declaration of built-in function 'malloc'
test.x.c:327: warning: incompatible implicit declaration of built-in function 'memset'
test.x.c:328: warning: incompatible implicit declaration of built-in function 'memcpy'
test.x.c:334: warning: incompatible implicit declaration of built-in function 'malloc'
test.x.c:337: warning: incompatible implicit declaration of built-in function 'sprintf'
test.x.c: In function 'main':
test.x.c:371: warning: incompatible implicit declaration of built-in function 'fprintf'
test.x.c:371: error: 'stderr' undeclared (first use in this function)
test.x.c:372: error: 'errno' undeclared (first use in this function)
shc: Success

**I find that in my system there is a new file created as test.x.c**
However, there is[COLOR="Red"] no test.x[/COLOR] . Without it I cannot execute the file.

So, what is wrong ?

---

### Post by astrotech226 on 2008-03-10
You don't have all the header files and things to compile a program.  Do this and it should work:

```
sudo apt-get install build-essential
```

---

### Post by ccclay on 2008-03-11
thx astrotech226. I have done with "sudo apt-get install build-essential". However, I dont know why my ubuntu responsed with such result : it keeps on asking me to insert disk but I have already insert the disk. The same situation occurs when I install other package such as mailx in [http://ubuntuforums.org/showthread.php?p=4493068#post4493068](http://ubuntuforums.org/showthread.php?p=4493068#post4493068).

 I am looking for solution and be graceful if you may give me a hand. Thank you very much !!

 
~$ sudo apt-get install build-essential
[sudo] password for ccclay:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7934kB of archives.
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

---

### Post by astrotech226 on 2008-03-11
If you go into Synaptic, click Settings -> Repositories.  Simply uncheck the installable from cdrom.  You might also need to enable the other repositories.

---

### Post by ccclay on 2008-03-11
thx. After I unchecked the installable from cdrom, this is what I got :

> sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


So what to do now ? :confused:

---

### Post by astrotech226 on 2008-03-11
You might need to enable some of the other repositories in /etc/apt/sources.list first.

Also, have you updated the apt package list recently?  If not, do this and retry to install the build-essential.

```
sudo apt-get update
```

---

### Post by ccclay on 2008-03-11
Thx for your guide.

>> enable some of the other repositories in /etc/apt/sources.list first.
Below is my list, but I dont know how to enable, would you mind giving me some hints ? Thanks so much.

> # deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

# Line commented out by installer because it failed to verify:
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe


>> Also, have you updated the apt package list recently? If not, do this and retry to install the build-essential.
Actually I have done this yesterday : ~$ sudo apt-get update && sudo apt-get upgrade
And, I do this again after reading your message, this is what I got :

>  sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_HK                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                 
Get:2 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release.gpg [189B]
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Translation-en_HK
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Packages
Fetched 2B in 2s (1B/s)
Reading package lists... Done


So I install build-essential, but seems no luck.
> 
~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

---

### Post by astrotech226 on 2008-03-11
If you have Synaptic, it's easier to enable the repositories in there.  If not, uncomment the lines in /etc/apt/sources.list that say they were commented out because they could not be verified.  You probably didn't have an internet connection during the installation.  So take all the lines that look like this:

```
# Line commented out by installer because it failed to verify:
# deb http://hk.archive.ubuntu.com/ubuntu/ gutsy multiverse
```

And change to this:

```
deb http://hk.archive.ubuntu.com/ubuntu/ gutsy multiverse
```

Simply remove the "#" at the beginning of the lines.  I would also remove the lines explaining that the line was commented out because it failed to verify.

---

### Post by ccclay on 2008-03-12
oh yes, it works now !! :popcorn: thanks astrotech226 !! Also successfully run shc -f <file>, thank you !!

---

### Post by ccclay on 2008-03-12
But a new problem is found, and it is fatal : the file.x can only run in one ubuntu where the file.x is created, if run in other ubuntu it will be error and cannot run. I have installed 2 ubuntu in my PC, below is what I have tested with 2 files in 2 ubuntu installation. 

I created 2 files :  test_touch.x in old_Ubuntu and abc.x in New_Ubuntu

old_Ubuntu ( a CD version produced by Canonical Ltd, given by my friend ) 
**Here running test_touch.x is ok but abc.x is problem.**
 
~$ ./test_touch.x
~$ ./abc.x
./abc.x: b/&#65533;m
 

New_Ubuntu ( download from ubuntu website )
[COLOR="Red"]Here running abc.x is ok but test_touch.x is problem.[/COLOR]

~$ ./abc.x
~$ ./test_touch.x
./test_touch.x: &#65533;Aq0&#65533;&#65533;&#65533;&#65533;t&#65533;[&#65533;


Any suggestions ? Thanks a lot !!
If this problem is not solved then using shc is meaningless. Do you agree ?

---

### Post by astrotech226 on 2008-03-12
Try this on both machines and post the output.

```
ldd test_touch.x
ldd abc.x
```

I think you'll find that it's compiling the script against certain libraries and those are different versions on each Ubuntu install.  If you want to just copy the scripts between computers, they are going to need to be fairly similar in versions.

This is true with other executables in linux.  If you copied a really old version of anything out of /usr/bin from an old version of linux and tried to park it in /usr/bin on the new version, you will likely get glibc errors along with a list of other problems.

If you need this ability on an old and new version of Ubuntu, you might need to compile the script on each computer separately.

---

### Post by ccclay on 2008-03-13
Thx astrotech226. I found later by using an option as -r then can solve the problem. Anyway, I most appreciate your help which have been so detail and meeting my need. Thank you very much !! Would like to invite a long hair singer :guitar: to sing my thanks to you. :)

---

### Post by astrotech226 on 2008-03-13
Thank you!  I didn't know about the "-r" option.  Learning something new every day!

---

