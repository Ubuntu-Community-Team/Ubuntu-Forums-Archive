---
title: "dpkg: dependency problems"
date: 2014-04-10
forum: Server Platforms
---

### Post by LHammonds on 2014-04-10
I'm stuck trying to resolve package issues.  Any advice on how to resolve this would be appreciated.

I have a server that seems to have not had enough free space in /usr (although it had a gig free) when doing kernel updates.

Nagios told me there was a Broken Package so I logged in to see what the problem was.  I increased the /usr volume to have an additional gigabyte free and shows 44% in use out of 3GB.

Now, when I do "sudo apt-get -f install" I get the following message:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-45-generic linux-image-3.5.0-43-generic
  linux-image-3.5.0-46-generic linux-headers-3.5.0-43-generic
  linux-headers-3.5.0-46-generic linux-image-3.5.0-44-generic
  linux-headers-3.5.0-44-generic linux-headers-3.5.0-43 linux-headers-3.5.0-44
  linux-headers-3.5.0-45 linux-headers-3.5.0-46 linux-image-3.5.0-45-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-generic-lts-quantal
The following packages will be upgraded:
  linux-headers-generic-lts-quantal
1 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,330 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?

```
I answer yes and then I get this:
```

dpkg: dependency problems prevent configuration of linux-headers-generic-lts-quantal:
 linux-headers-generic-lts-quantal depends on linux-headers-3.5.0-47-generic; however:
  Package linux-headers-3.5.0-47-generic is not installed.
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-headers-generic-lts-quantal; however:
  Package linux-headers-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried the following:
```

# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-47-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

I then tried the following commands:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get -f install

```
I still get the same message.

I try to remove linux-headers-generic-lts-quantal and get the following:

```

# sudo apt-get remove linux-headers-generic-lts-quantal
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-lts-quantal : Depends: linux-headers-generic-lts-quantal but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I then try the following:

```

# sudo apt-get remove linux-generic-lts-quantal
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-47-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I then try:

```

# sudo apt-get remove linux-headers-3.5.0-47-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-3.5.0-47-generic is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-47-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Now I try to install linux-headers-3.5.0-47-generic
```

# sudo apt-get install linux-headers-3.5.0-47-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.5.0-47-generic : Depends: linux-headers-3.5.0-47 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Now I try to install linux-headers-3.5.0-47
```

# sudo apt-get install linux-headers-3.5.0-47
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-47-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Now I seem to be stuck in an infinite loop. :)

Here is some other info about the server which is running in a virtual environment on top of ESXi 4.1.0:

```

uname -a
Linux srv-mysql 3.5.0-48-generic #72~precise1-Ubuntu SMP Tue Mar 11 20:09:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

ls /boot/vm* -l
-rw------- 1 root root 5190624 Oct 24 10:16 /boot/vmlinuz-3.5.0-43-generic
-rw------- 1 root root 5191232 Nov 13 10:36 /boot/vmlinuz-3.5.0-44-generic
-rw------- 1 root root 5190112 Dec  4 10:39 /boot/vmlinuz-3.5.0-45-generic
-rw------- 1 root root 5191168 Jan  9 18:17 /boot/vmlinuz-3.5.0-46-generic
-rw------- 1 root root 5192320 Feb 19 16:24 /boot/vmlinuz-3.5.0-47-generic
-rw------- 1 root root 5189952 Mar 11 15:30 /boot/vmlinuz-3.5.0-48-generic

```

```

df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root    1.9G  1.1G  737M  59% /
udev                    237M  4.0K  237M   1% /dev
tmpfs                    50M  420K   49M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    246M     0  246M   0% /run/shm
/dev/sda1               268M  151M  103M  60% /boot
/dev/mapper/LVG-home    183M  5.6M  168M   4% /home
/dev/mapper/LVG-tmp     461M   11M  427M   3% /tmp
/dev/mapper/LVG-usr     3.0G  1.3G  1.6G  44% /usr
/dev/mapper/LVG-var     1.9G  435M  1.4G  25% /var
/dev/mapper/LVG-srv     183M  5.6M  168M   4% /srv
/dev/mapper/LVG-opt     993M  773M  178M  82% /opt
/dev/mapper/LVG-bak     2.0G  1.1G  790M  59% /bak

```

---

### Post by bapoumba on 2014-04-10
Does not seem you are running out of space anywhere, but  I see some Quantal and some Precise references, I'd be more inclined to some mixed repositories. What do you have in your sources.list & are you using ppas or third party repos ?
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

---

### Post by LHammonds on 2014-04-10
Should be default.  I don't recall messing with 3rd-party.

```

cat /etc/apt/sources.list

#

# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main

```

There is nothing in /etc/apt/sources.list.d/

EDIT: I should also note that when doing updates, I do the following:

```

aptitude update
aptitude safe-upgrade

```

You don't see the space issues because I already expanded the opt volume and opt file system by 1 GB.  I didn't save the initial error message talking about space issues since I thought increasing the space would have solved the problem and it was too late to scroll up to see the text by the time I was wanting to post here.  Was mainly explaining a potential cause to the situation.

LHammonds

---

### Post by bapoumba on 2014-04-11
OK thanks, looks fine to me. What I do not understand then is where is your quantal kernel coming from. Two ideas I cannot double check for now : you have the backports enabled and are using the us- repos. Please try using the main repos first (and run an update/upgrade) then comment out the backports if this does not work.

---

### Post by LHammonds on 2014-04-11
> **bapoumba said:**
> you have the backports enabled and are  using the us- repos. Please try using the main repos first (and run an  update/upgrade) then comment out the backports if this does not  work.
Eh, what are the "main" repos?  What is the address?

----------------------------------

I have several 12.04 servers so checked all of them.  They all defaulted to the US locations (probably because I'm in the US...hehehe).

I picked a random server and check what version it was on.

```

# uname -a
Linux srv-mediawiki 3.5.0-47-generic #71~precise1-Ubuntu SMP Wed Feb 19 22:02:52 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

r# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:        12.04
Codename:       precise

```

I then checked what images were in /boot.

```

# ls -l /boot/vmlin*
-rw------- 1 root root 5191168 Jan  9 18:17 /boot/vmlinuz-3.5.0-46-generic
-rw------- 1 root root 5192320 Feb 19 16:24 /boot/vmlinuz-3.5.0-47-generic

```

I then wanted to see what the safe-upgrade message would show:

```

# aptitude safe-upgrade
Resolving dependencies...
The following NEW packages will be installed:
  linux-headers-3.5.0-48{a} linux-headers-3.5.0-48-generic{a}
  linux-image-3.5.0-48-generic{a}
The following packages will be upgraded:
  linux-generic-lts-quantal linux-headers-generic-lts-quantal
  linux-image-generic-lts-quantal
3 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 53.9 MB of archives. After unpacking 228 MB will be used.
Do you want to continue? [Y/n/?] n

```

Ah ha! There is the 1st sign of quantal.  I am wondering if it has something to do with aptitude so I try using the most basic command next.

```

# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic-lts-quantal linux-image-generic-lts-quantal
The following packages will be upgraded:
  linux-generic-lts-quantal
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,744 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? n

```

So why is Precise 12.04 using Quantal 12.10?

From my understanding, 12.04 is Kernel 3.2.0 and 12.10 is Kernel 3.5.0.  Are the kernels updated due to security updates?

LHammonds

---

### Post by LHammonds on 2014-04-14
I cannot get this resolved but since 14.04 LTS is only a few days away, I'll just re-build a new 14.04 server and move my data over to it.

EDIT: The space issue happened to yet another server but correcting the space issue on that server and running the fix command didn't produce the same situation...it actually fixed the problem.  But regardless, this is the initial out-of-space message that I missed 1st time round in case anyone else is interested and has this issue:

```

# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.5.0-44-generic linux-headers-3.5.0-44-generic
  linux-headers-3.5.0-44
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.5.0-48-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-48-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/968 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

After answering yes:
```

(Reading database ... 146551 files and directories currently installed.)
Unpacking linux-headers-3.5.0-48-generic (from .../linux-headers-3.5.0-48-generic_3.5.0-48.72~precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-48-generic_3.5.0-48.72~precise1_amd64.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.5.0-48-generic/include/linux/capi.h': No space left on device
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.5.0-48-generic_3.5.0-48.72~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And checking the file system space:
```
# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  1.9G  595M  1.2G  34% /
udev                  237M  4.0K  237M   1% /dev
tmpfs                  50M  288K   49M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  246M     0  246M   0% /run/shm
/dev/mapper/LVG-opt   497M   11M  464M   3% /opt
/dev/mapper/LVG-bak   461M   11M  427M   3% /bak
/dev/sda1             268M   78M  176M  31% /boot
/dev/mapper/LVG-home  183M  5.6M  168M   4% /home
/dev/mapper/LVG-tmp   461M   11M  427M   3% /tmp
**/dev/mapper/LVG-usr   1.9G  1.2G  [COLOR=#ff0000]595M[/COLOR]  67% /usr**
/dev/mapper/LVG-var   1.9G  546M  1.3G  31% /var
/dev/mapper/LVG-srv   183M  5.6M  168M   4% /srv
```
Of which, the /usr needs another gigabyte free in order to operate.

I do "**vgdisplay**" and see that I have 5 GB available (unallocated), then I do "**lvscan**" to see that /dev/LVG/usr is 3 GB and I "could" expand the file system but I like to have extra space for emergencies so I expand the volume an extra gigabyte (**sudo lvextend -L4G /dev/LVG/usr**) then expand the file system (**sudo resize2fs /dev/LVG/usr 3G**)

This is the point where it had the problems documented earlier in this thread but on this particular server, it resolved the situation and didn't fall into the cyclic problem.

```

# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.5.0-44-generic linux-headers-3.5.0-44-generic
  linux-headers-3.5.0-44
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.5.0-48-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-48-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/968 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 146551 files and directories currently installed.)
Unpacking linux-headers-3.5.0-48-generic (from .../linux-headers-3.5.0-48-generic_3.5.0-48.72~precise1_amd64.deb) ...
Setting up linux-headers-3.5.0-48-generic (3.5.0-48.72~precise1) ...
Setting up linux-headers-generic-lts-quantal (3.5.0.48.54) ...
Setting up linux-generic-lts-quantal (3.5.0.48.54) ...

```

---

### Post by bapoumba on 2014-04-14
> **LHammonds said:**
> I cannot get this resolved but since 14.04 LTS is only a few days away, I'll just re-build a new 14.04 server and move my data over to it.

I am very sorry, I had a long WE and a few things got overseen here on UF. Please accept my apologies.
The main repositories are here (a pic is better than 100 words): [https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)
If you want to do it by editing your sources.list file (as this is a server with may be no GUI), juste remove the **us.** in the repo url, then ```
sudo apt-get update
sudo apt-get upgrade
```

If you run a clean 14.04 install, that should do it. If you upgrade, the issue may remain, as we have not pinpointed its origin.

---

### Post by koenn on 2014-04-14
I don't know where the quantal kernel packages come from either.
Other than that, the upgrade that failed because of the "no space left" error obviouslly  left some packages half installedn which triggert that error cascade.

You can probably work out a solution based on either
1-  force the installation of a kernel package (i.e. ignore missing dependencies, fix them afterwards) 
2- force de-installation/removel of the troublesome kernels (and don't reboot until you're quite sure you have a bootable kernel, i.e. after a succesful run of update-grub)

you 'd do this with dpkg  directly , not through apt or aptitude.

Both approaches are quite risky in that you may end up with an unbootable or non-functional  system  (the first approache more so, imo), which is worse than what you have now,  so if starting from scratch is not too big a deal, that would be the safe route.


similar issue  : [http://ubuntuforums.org/showthread.php?t=2169901](http://ubuntuforums.org/showthread.php?t=2169901)

---

### Post by LHammonds on 2014-04-14
> **bapoumba said:**
> I am very sorry, I had a long WE and a few things got overseen here on UF. Please accept my apologies.
Thanks, but no apologies are necessary.  If this were catastrophic, I'd just restore backups of the partitions using fsarchive or create a new 12.04 server and move over the data or create a 12.04 server and restore the partitions I backup to an offsite location. :)

Was just trying to get a solution out there because if I run into it, I'd figure others might as well.

> **koenn said:**
> You can probably work out a solution based on either
1-  force the installation of a kernel package (i.e. ignore missing dependencies, fix them afterwards) 
2- force de-installation/removel of the troublesome kernels (and don't reboot until you're quite sure you have a bootable kernel, i.e. after a succesful run of update-grub)

Thanks for the tips.

I'm going to stick with my plan to go 14.04 and just move over the data.  I was going to do this for the upgrade to 14.04 anyway (don't like doing in-place upgrades for major releases).  I like to update and have my own personal library of documentation of how to install the current server from scratch especially if that is the version I'm running. :)

But until then, if I find a solution that isn't too risky and works, I'll post back here with the results.

Thanks,
LHammonds

---

### Post by bapoumba on 2014-04-15
Re the Quantal kernels : would you have used some third party repos for some application that would have brought it along in an awkward way ? Or some leftover from an upgrade ? It should not be there unless something went wrong on either your repos or the us repos. But in the latter case, you would not be alone in this situation (I have not checked). I tend to think it is a local configuration or a succession of small unnoticed events.

---

### Post by ian-weisser on 2014-04-15
When looking at "No space left on device" errors,
in addition to **df** for looking at space,
remember to also check **df -i** for looking at inodes.
Check both.

mapper and multiple kernels both use a lot of inodes, and there a *lot* of threads in this forum where "No space left" referred to inodes instead of disk space.

---

### Post by LHammonds on 2014-04-15
I don't mess with repo stuff.  What is set is set by default.

This particular server is running MySQL and I have documented every step of its setup in my signature.  Shouldn't be anything quirky going on that I know of.

Maybe the Quantal kernel got there because of my [upgrade script]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=193#p326") which is designed to just get security updates using the following command:

```

aptitude safe-upgrade --assume-yes --target-release `lsb_release -cs`-security

```

The only time I have ever added a 3rd-party repo was a Minecraft server in order to get Oracle Java installed and updated on a normal basis.

I edited /etc/apt/sources.list and removed "**us.**" from all entries on the MySQL server.  Then did "**aptitude update**" and then "**aptitude safe-upgrade**" and it worked without error!  Just as if there was nothing wrong.  Didn't even need to do the fix command.  Wow.

I was then able to do the "**apt-get remove linux-image-3.5.0-44-generic**" command without any errors and cleaned up all the old boot images (I always keep the latest two)

Being the curious sort, I then checked the Bugzilla server that was having the similar issue.  I verified that it still had the issue by trying to remove an old kernel and it spit out the error I expected.  I then did the "**aptitude update**" and "**aptitude safe-upgrade**" and was greeted with the familiar "quantal depends on quantal" error.  At this point, I then edited the sources.list file and removed "us.", ran "**aptitude update**" and "**aptitude safe-upgrade**" but it did not fix the issue.  The "**apt-get install -f**" also did not resolve the issue.

Still not sure what's going on but my plan of action will not change...still going to setup all new 14.04 servers and move over the data. :)

> **ian-weisser said:**
> When looking at "No space left on device" errors,
in addition to **df** for looking at space,
remember to also check **df -i** for looking at inodes.
Check both.

mapper and multiple kernels both use a lot of inodes, and there a *lot*  of threads in this forum where "No space left" referred to inodes  instead of disk space.
True but the issue was resolved by increasing the volume and file system.  The packages take up a lot of room in /usr during installation so it needs a lot of breathing room to operate.  When I create my 14.04 install documents, I will setup /usr to have 1GB more than I have in the past.

```

Filesystem           Inodes  IUsed  IFree IUse% Mounted on
/dev/mapper/LVG-root 121920  12369 109551   11% /
udev                  60471    514  59957    1% /dev
tmpfs                 62877    464  62413    1% /run
none                  62877      8  62869    1% /run/lock
none                  62877      1  62876    1% /run/shm
/dev/sda1            146016    236 145780    1% /boot
/dev/mapper/LVG-home  48192     18  48174    1% /home
/dev/mapper/LVG-tmp  121920     24 121896    1% /tmp
/dev/mapper/LVG-usr  195072 166503  28569   86% /usr
/dev/mapper/LVG-var  121920   3245 118675    3% /var
/dev/mapper/LVG-srv   48192     13  48179    1% /srv
/dev/mapper/LVG-opt  257024    886 256138    1% /opt
/dev/mapper/LVG-bak  520192    552 519640    1% /bak

```

LHammonds

---

