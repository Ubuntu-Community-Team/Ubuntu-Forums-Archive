---
title: "VMWare Workstation 6.0.2 install problem on Ubuntu 7.1.0"
date: 2007-11-20
forum: Virtualisation
---

### Post by jbradshw on 2007-11-20
I couldn't find any threads with this problem so I'm starting this new one.

Clean install of 7.1.0. I followed the instructions from this site:

[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

I got steps 1-3 working just fine. When I did step 4 it gives the following error: (minus the CC part as I did that part as a separate step after step 3)



root@Zyntax:/home/john/Desktop/vmware-distrib# sudo ./vmware-install.pl
Installing VMware Workstation.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

The path "/usr/lib/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 

Use of uninitialized value in split at ./vmware-install.pl line 4093.
Use of uninitialized value in subtraction (-) at ./vmware-install.pl line 4113.
Unable to get the access rights of source file "./lib".

Execution aborted.

root@Zyntax:/home/john/Desktop/vmware-distrib#




I checked and ./lib has full permissions for root. Anyone else getting this error? Like I said this is a clean install of 7.1.0 and as soon as that was done, I jumped into installing VMWare.

---

### Post by jbradshw on 2007-11-20
Nevermind - I got it fixed. For some reason ./lib didn't even exist!

---

### Post by Banacek on 2007-11-21
```
sudo apt-get install linux-headers-$2.6.22-14-generic build-essential gcc-3.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-.6.22-14-generic
```


In *System>Adminstration>Software Sources* I have all the sources checked. What am I missing? What else do I need?

---

### Post by Banacek on 2007-11-22
I goto *System>Administration>Synaptic Package Manager* and under *Development* I see *build-essential*. The one I need has "build-essential" in the name so maybe I need that package in order to get the first one? So I try to mark that one and I get this:


```
The following packages have unresolvable dependencies.
Make sure that all required repositories are added and
enabled in the preferences.



build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
```




I try to mark *g++* but I get
```
g++:
 Depends: g++-4.1 but it is not going to be installed
```



I try *g++-4.1* for
```
g++-4.1:
 Depends: libstdc++6-4.1-dev but it is not going to be installed
```



Next I look in *Libraries - Development* and try libstdc++6-4.1-dev.
```
libstdc++6-4.1-dev:
 Depends: g++-4.1 but it is not going to be installed
 Depends: libc6-dev but it is not going to be installed
```



So I try *libc6-dev*.
```
libc6-dev:
  Depends: libc6 (=2.6.1-1ubuntu9) but 2.6.1-1ubuntu10 is to be installed
```



I look under *Libraries* and see that *libc6* is installed but it's version 2.6.1-1ubuntu10 and version 2.6.1-1ubuntu9 is not available.

How can I get 9? Somebody help, please.

---

### Post by Banacek on 2007-11-23
```
su root
Password: 
aptitude install -f libc6=2.6.1-1ubuntu9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libc6-dev libc6-i686 
The following packages will be DOWNGRADED:
  libc6 
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 4183kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.6.1-1ubuntu10) but 2.6.1-1ubuntu9 is to be installed.
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.6.1-1ubuntu9 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6-dev [2.6.1-1ubuntu10 (gutsy-updates, now) -> 2.6.1-1ubuntu9 (gutsy, gutsy)]
libc6-i686 [2.6.1-1ubuntu10 (gutsy-updates, now) -> 2.6.1-1ubuntu9 (gutsy)]

Score is 110

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  libc6 libc6-dev libc6-i686 
0 packages upgraded, 0 newly installed, 3 downgraded, 0 to remove and 0 not upgraded.
Need to get 5331kB/8618kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press [Enter].

Get:1 http://us.archive.ubuntu.com gutsy/main libc6 2.6.1-1ubuntu9 [4183kB]
Get:2 http://us.archive.ubuntu.com gutsy/main libc6-i686 2.6.1-1ubuntu9 [1148kB]
Fetched 5331kB in 1m4s (82.7kB/s)       
dpkg - warning: downgrading libc6-dev from 2.6.1-1ubuntu10 to 2.6.1-1ubuntu9.
(Reading database ... 125377 files and directories currently installed.)
Preparing to replace libc6-dev 2.6.1-1ubuntu10 (using .../libc6-dev_2.6.1-1ubuntu9_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg - warning: downgrading libc6 from 2.6.1-1ubuntu10 to 2.6.1-1ubuntu9.
Preparing to replace libc6 2.6.1-1ubuntu10 (using .../libc6_2.6.1-1ubuntu9_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg - warning: downgrading libc6-i686 from 2.6.1-1ubuntu10 to 2.6.1-1ubuntu9.
(Reading database ... 125377 files and directories currently installed.)
Preparing to replace libc6-i686 2.6.1-1ubuntu10 (using .../libc6-i686_2.6.1-1ubuntu9_i386.deb) ...
Unpacking replacement libc6-i686 ...
Setting up libc6-dev (2.6.1-1ubuntu9) ...
Setting up libc6-i686 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
```

After that all the development packages installed. Yes, I did upgrade the downgraded packages back up to the newer versions afterwards.

---

### Post by dpj23 on 2007-11-25
I'm going to tell you I have done this install at least 5 different times and while all these posts offer great advice, the simplest install method I have found is this...

Log in as root...  graphical mode...

Browse to the vm and double chick on the vmware-install.pl file...

When prompted, select run in terminal and follow the prompts that it generates...

It will tell what to type and you just have to type the pathways for the install should take about 5 minutes. It works great and has proven to be reliable method of installing this software program....

---

### Post by gb64 on 2007-11-25
When you get messages such as 'not going to be installed', you might re-check your repository settings. In fact, the message even advices that. See it?
If you don't check all necessary repositories, an install might say a dependency is needed, but won't be installed - it cannot install a specific needed package if not in the chosen repository.

---

### Post by gb64 on 2007-11-25
Banacek -
I see you had noted you did check repos, but above is still good advice for others when they encounter that warning message.

---

### Post by Banacek on 2007-11-29
***dpj23***,


Well, opening a terminal window and doing *./vmware.install.pl* does about the same thing, essentially.

Yeah, the VMware installer works like a breeze, if you've already got the kernel development tools installed. VMware absolutely must have those in order to build the vmmon module specific to your kernel. Without the module correct for your kernel VMware cannot run. You must have already had some sort of development package installed that included being able to build for your kernel. 






***gb64 and dpj23***,


The problem was never really about the VMware installer itself. It always did what it was supposed to do. That was never the problem I was dealing with. The problem was that some of the dependencies for the repositories were wrong. I should never have had to take the steps that I did except that some dependencies had not been updated to point to the newer packages. The whole purpose of the machinations I had to take was to find a way to get around the fouled up dependencies.

Once I had dealt with Gusty's dependencies screwup, the VMware installer worked like a charm.

---

