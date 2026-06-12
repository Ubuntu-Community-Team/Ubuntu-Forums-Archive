---
title: "Virtual Box error"
date: 2010-11-16
forum: Virtualisation
---

### Post by BSOD64 on 2010-11-16
I'v installed VirtualBox OSE from the Ubuntu software center

I setup an ubuntu vm to test it and when I tried it out it said:

```

Kernel driver not installed (rc=-1908)

please install virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

```

---

### Post by CharlesA on 2010-11-16
Run this:

```
sudo apt-get install virtualbox-ose-dkms
```

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by BSOD64 on 2010-11-16
after I execute the first it says its already installed.

and after execute the second it says: "command not found" :confused:

---

### Post by CharlesA on 2010-11-16
Try this then:

```
sudo modprobe vboxdrv
```

---

### Post by BSOD64 on 2010-11-18
no luck.

---

### Post by CharlesA on 2010-11-18
Purge it and then reinstall.

```
sudo apt-get purge virtualbox-ose
```

```
sudo apt-get install virtualbox-ose
```

---

### Post by jpl888 on 2010-11-18
There is no /etc/init.d/vboxdrv in the OSE version in Ubuntu.

Could you try reinstalling the dkms bit again?

```
sudo apt-get --reinstall install virtualbox-ose-dkms
```

---

### Post by CharlesA on 2010-11-18
> **jpl888 said:**
> There is no /etc/init.d/vboxdrv in the OSE version in Ubuntu.[/CODE]

Didn't know that. Thanks. :)

---

### Post by BSOD64 on 2010-11-19
I can't reinstall the packages right now because the internet is not working.

If you know how to fix it please help.
[http://ubuntuforums.org/showthread.php?t=1623686](http://ubuntuforums.org/showthread.php?t=1623686)

never mind that's solved!:D

---

### Post by BSOD64 on 2010-11-21
this is what I get:(
```

me@me-laptop:~$ sudo apt-get --reinstall install virtualbox-ose-dkms
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of virtualbox-ose-dkms is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by CharlesA on 2010-11-21
Did you already purge virtualbox?

---

### Post by jpl888 on 2010-11-21
Sounds like you have a connectivity problem. Can you confirm you can ping an external ip and also what the server addresses are in /etc/apt/sources.list

---

### Post by BSOD64 on 2010-11-21
I tried these commands and nothing happens.:(

```

me@me-laptop:~$ sudo apt-get purge virtualbox-ose
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-opengl libqtcore4 libqt4-network libqtgui4 libmng1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-ose* virtualbox-ose-qt*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 44.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 180374 files and directories currently installed.)
Removing virtualbox-ose-qt ...
Purging configuration files for virtualbox-ose-qt ...
Removing virtualbox-ose ...
Purging configuration files for virtualbox-ose ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
me@me-laptop:~$ sudo apt-get install virtualbox-ose
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-ose-qt
Suggested packages:
  virtualbox-guest-additions
The following NEW packages will be installed:
  virtualbox-ose virtualbox-ose-qt
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.9MB of archives.
After this operation, 44.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package virtualbox-ose.
(Reading database ... 180192 files and directories currently installed.)
Unpacking virtualbox-ose (from .../virtualbox-ose_3.1.6-dfsg-2ubuntu2_i386.deb) ...
Selecting previously deselected package virtualbox-ose-qt.
Unpacking virtualbox-ose-qt (from .../virtualbox-ose-qt_3.1.6-dfsg-2ubuntu2_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up virtualbox-ose (3.1.6-dfsg-2ubuntu2) ...

Processing triggers for python-central ...
Setting up virtualbox-ose-qt (3.1.6-dfsg-2ubuntu2) ...

me@me-laptop:~$ sudo apt-get --reinstall install virtualbox-ose-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of virtualbox-ose-dkms is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

by the way I am posting this from this computer.

---

### Post by jpl888 on 2010-11-22
> **BSOD64 said:**
> this is what I get:(
```

me@me-laptop:~$ sudo apt-get --reinstall install virtualbox-ose-dkms
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of virtualbox-ose-dkms is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The modules won't load until virtualbox-ose-dkms is installed properly. You have some sort of connectivity issue. Probably DNS related considering you managed to get the network working in your other post. What DNS servers have you got set? Can you ping [www.google.ie](www.google.ie)?

---

### Post by BSOD64 on 2010-11-22
I can browse the Internet fine.:confused:

---

### Post by jpl888 on 2010-11-22
> Reinstallation of virtualbox-ose-dkms is not possible, it cannot be downloaded.

From your earlier post. For some reason it could not download the package. If internet is working fine then you need to check which server you are downloading from either in "software sources" or in /etc/apt/sources.list

If it can't download the package and there is a problem with the modules not being installed correctly then VirtualBox will not work.

---

### Post by BSOD64 on 2010-11-23
so your saying there is no thing I can do to fix it?:icon_frown:

---

### Post by jpl888 on 2010-11-23
No I'm saying to fix the problem we need to find out why it can't download the package.

Since you are telling me that the internet is working I am assuming the server names in /etc/apt/sources.list are wrong.

Perhaps you could post the contents of that file so we can check it?

---

### Post by BSOD64 on 2010-11-24
Here is my /etc/apt/sources.list file.;)

```

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

---

### Post by jpl888 on 2010-11-24
Your sources.list looks fine. Can you ping us.archive.ubuntu.com ?

If you run apt-get update does it complete without errors?

---

### Post by BSOD64 on 2010-11-24
It looks like I don't get any errors.:confused:

```

Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid Release 
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done

```

---

### Post by CharlesA on 2010-11-24
You never answered if you purged virtualbox or not.

---

### Post by jpl888 on 2010-11-24
Do

```
sudo apt-get upgrade
```

and then:-

```
sudo apt-get --reinstall install virtualbox-ose-dkms
```

Let us know if there are any errors.

---

### Post by BSOD64 on 2010-11-24
I just purged virtualbox and did the other stuff you said.

```

**BSOD64@BSOD64-laptop:~$ sudo apt-get purge virtualbox-ose**
[sudo] password for BSOD64: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-opengl libqtcore4 libqt4-network libqtgui4 libmng1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-ose* virtualbox-ose-qt*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 44.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 201888 files and directories currently installed.)
Removing virtualbox-ose-qt ...
Purging configuration files for virtualbox-ose-qt ...
Removing virtualbox-ose ...
Purging configuration files for virtualbox-ose ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
**BSOD64@BSOD64-laptop:~$ sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**BSOD64@BSOD64-laptop:~$ sudo apt-get --reinstall install virtualbox-ose-dkms**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of virtualbox-ose-dkms is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  libqt4-opengl libqtcore4 libqt4-network libqtgui4 libmng1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

then I reinstalled it.

---

### Post by jpl888 on 2010-11-24
Again same error

```
Reinstallation of virtualbox-ose-dkms is not possible, it cannot be downloaded.
```

Perhaps we should try clearing the apt cache.

---

### Post by jpl888 on 2010-11-24
```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
```

And try it again.

---

### Post by andymorton on 2010-11-24
> **BSOD64 said:**
> I'v installed VirtualBox OSE from the Ubuntu software center

I setup an ubuntu vm to test it and when I tried it out it said:

```

Kernel driver not installed (rc=-1908)

please install virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

```


I was having this same problem a while ago (I think when 10.10 was in the beta stage. I submitted a bug report on launchpad but was told that it couldn't be replicated. I'll have a look now to see if anything else has been posted about it

andy

---

### Post by andymorton on 2010-11-24
> **andymorton said:**
> I was having this same problem a while ago (I think when 10.10 was in the beta stage. I submitted a bug report on launchpad but was told that it couldn't be replicated. I'll have a look now to see if anything else has been posted about it

andy

Here's a link to the bug report. (Still 'unassigned')

[https://bugs.launchpad.net/ubuntu/+bug/645340](https://bugs.launchpad.net/ubuntu/+bug/645340)

---

### Post by jpl888 on 2010-11-24
Thanks for your input. However, the problem the OP seems to be having at the moment is that his system won't download virtualbox-ose-dkms so that he can reinstall it.

There may well be a bug beyond that, difficult to tell unless he can successfully reinstall it.

I would also suggest downloading the file manually in /var/cache/apt/archives.

i.e.

```
cd /var/cache/apt/archives
sudo wget http://ie.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-dkms_3.1.6-dfsg-2ubuntu2_all.deb
```

And try the reinstall again.

---

### Post by BSOD64 on 2010-11-24
I downloaded the package and tried to run it but the installer said: Error: A later version is already installed.:(

---

### Post by jpl888 on 2010-11-25
Can you do ```
dpkg -l |grep virtualbox
``` and post the output here?

It's probably that you are using Maverick which has a newer version.

---

### Post by BSOD64 on 2010-11-26
I did what you said and this is what happed.

```

BSOD64@BSOD64-laptop:~$ dpkg -l |grep virtualbox
ii  virtualbox-ose                       3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - base binaries
ii  virtualbox-ose-dkms                  3.2.10-dfsg-1                                   x86 virtualization solution - kernel module 
ii  virtualbox-ose-qt                    3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - Qt based user 

```

---

### Post by CharlesA on 2010-11-26
You've got a newer version of virtualbox-ose-dkms then the rest, that's probably why it's giving you problems.

---

### Post by jpl888 on 2010-11-26
> **BSOD64 said:**
> I did what you said and this is what happed.

```

BSOD64@BSOD64-laptop:~$ dpkg -l |grep virtualbox
ii  virtualbox-ose                       3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - base binaries
ii  virtualbox-ose-dkms                  3.2.10-dfsg-1                                   x86 virtualization solution - kernel module 
ii  virtualbox-ose-qt                    3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - Qt based user 

```

There in lies the problem.

The version of virtualbox-ose-dkms you have installed doesn't match the version of virtualbox-ose or virtualbox-ose-qt. I'm not surprised it doesn't work. I don't know how you managed that. I bet you couldn't do it again if you tried!

Anyway I think the best way forward is to purge virtualbox-ose-dkms and install the one I got you to download the other day.

```
sudo apt-get purge virtualbox-ose-dkms
```

Hope that sorts it out for you.

---

### Post by BSOD64 on 2010-11-27
I still get the same error!

---

### Post by agent8131 on 2010-11-27
Update: It occurs to me that you should do this first to try and isloate how the problem occurred:

```
apt-cache policy virtualbox-ose-dkms

```

On the assumption that you installed a deb file with dpkg or something like that then the following should resolve your problem permanently:

Mixing versions of packages is always a recipe for problems.  Try this:

```
sudo apt-get install virtualbox-ose-dkms=3.1.6-dfsg-2ubuntu2

```

---

### Post by BSOD64 on 2010-12-01
That didn't work either.:sad:

---

### Post by CharlesA on 2010-12-01
> **BSOD64 said:**
> That didn't work either.:sad:
Are you trying to run Virtualbox inside Virtualbox by chance?

You weren't too clear about it in the OP.

---

### Post by BSOD64 on 2010-12-02
No, all I'm trying to do is run virtualbox in Ubuntu.

By the way what do I do if nobody replies to a thread I post.

---

### Post by CharlesA on 2010-12-03
You can post in a thread after 24-hours to bump it to page one, any more frequent then that is frowned upon.

---

### Post by BSOD64 on 2010-12-06
Is there any way I can fix my error?

---

### Post by BSOD64 on 2010-12-13
please help if you can.:(

---

### Post by CharlesA on 2010-12-13
Run this and post the output please:

```
dpkg -l |grep virtualbox
```

If uninstalling it didn't work, that'll tell us what is still installed.

---

### Post by BSOD64 on 2010-12-14
```

BSOD64@BSOD64-laptop:~$ dpkg -l |grep virtualbox
ii  virtualbox-ose                       3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - base binaries
ii  virtualbox-ose-dkms                  3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - kernel module 
rc  virtualbox-ose-qt                    3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - Qt based user

```
here it is

---

### Post by CharlesA on 2010-12-14
Can you remove everything with apt-get?

```
sudo apt-get purge virtualbox-ose-qt virtualbox-ose-dkms virtualbox-ose
```

---

