---
title: "apt-get dependency problems"
date: 2013-08-23
forum: Server Platforms
---

### Post by Brian_Murray on 2013-08-23
Hey everyone, I love the Linux cli and shell scripting... but I swear when it comes to dependency issues I just about want to rip my hair out. I've got an old desktop running Ubuntu Server 12.04.2 LTS and I just recently started getting the following errors when trying to perform my usual "apt-get update" / "apt-get upgrade".  The server is just your typical LAMP server with nothing special going on and has run flawlessly for a while now prior to this.  If anyone has any insight on how to troubleshoot this mess I'd greatly appreciate it.  I've searched but only found the likely causes to be low disk space and a CPU that doesn't support PAE, but both of those gave better error messages than what I'm seeing.  Additionally I'm absolutely not out of disk space on any partition.

It seems like linux-headers-generic-pae is too far ahead at version 3.2.0.52.62 because linux-generic-pae depends on linux-headers-generic-pae version 3.2.0.51.61.... but I really don't know for sure. Not to mention, why would the package manager allow the versions to get out of sync?  I just would like to get it working again. :-)

```

root@web:/# apt-get clean
root@web:/# apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
<snip'd to keep the thread from being long, only default sources configured>
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Reading package lists... Done
root@web:/# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.51.61) but 3.2.0.52.62 is installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-51-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
root@web:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-43-generic-pae linux-headers-3.2.0-38-generic-pae linux-headers-3.2.0-41-generic-pae linux-headers-3.2.0-36-generic-pae linux-headers-3.2.0-40 linux-headers-3.2.0-41
  linux-headers-3.2.0-36 linux-headers-3.2.0-37 linux-headers-3.2.0-43 linux-headers-3.2.0-38 linux-headers-3.2.0-44 linux-headers-3.2.0-39 linux-headers-3.2.0-45 linux-headers-3.2.0-44-generic-pae
  linux-headers-3.2.0-39-generic-pae linux-headers-3.2.0-37-generic-pae linux-headers-3.2.0-45-generic-pae linux-headers-3.2.0-40-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
Need to get 4,074 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic-pae i386 3.2.0.52.62 [1,730 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-generic-pae i386 3.2.0.52.62 [2,344 B]
Fetched 4,074 B in 0s (32.4 kB/s)
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-51-generic-pae; however:
  Package linux-image-3.2.0-51-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.51.61); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.51.61); however:
  Version of linux-headers-generic-pae on system is 3.2.0.52.62.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```

root@web:/# df -k
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdc1      191777404  7230496 174805136   4% /
udev              505332        4    505328   1% /dev
tmpfs             205056      312    204744   1% /run
none                5120        0      5120   0% /run/lock
none              512640        0    512640   0% /run/shm
/dev/sda1      240364216 76161136 151993204  34% /homeserver
```

---

### Post by bapoumba on 2013-08-24
I've added code tags to your post.

Have you at some point used a ppa or another repo ?

The packages I've checked are at the version you need in the precise repos :
[http://packages.ubuntu.com/search?keywords=linux-headers-generic-pae&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=linux-headers-generic-pae&searchon=names&suite=precise&section=all)
[http://packages.ubuntu.com/search?keywords=linux-generic-pae&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=linux-generic-pae&searchon=names&suite=precise&section=all)
[http://packages.ubuntu.com/search?keywords=linux-image-3.2.0-51-generic-pae&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=linux-image-3.2.0-51-generic-pae&searchon=names&suite=precise&section=all)

Could you please post your sources.list ?

---

### Post by koenn on 2013-08-24
you seem to have some incomplete install actions :  ```

2 upgraded,  [ ... ].
2 not fully installed or removed.
 
```
if those "not fully installed or removed" are versions of  the kernel image and headers packages, that might be the reason you get that weird mismatch between kernel and headers 

you could probably find out what's happening there with ```
 dpkg -l |more 
``` and look for packages that don't have a [FONT=Courier New]'ii'[/FONT] 

Your fix will then probably consist of manually removing and reinstalling one or more of the offending packages (ie. apt-get install i.s.o upgrade), but since this is your kernel it might be tricky, so let's see of dpkg tells us something first.

---

### Post by Brian_Murray on 2013-08-25
Thank you very much for the replies (and for adding the code tags).  Below is the output as requested:

I don't believe I've ever pointed it at any other repos or anything like that.  I just did a basic 12.04 LTS install from ISO and used apt-get update / upgrade since.


Output of sources.list:

```


root@web:/etc/apt# cat sources.list
#


# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (201208                                                17.3)]/ precise main restricted


#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (2012081                                                7.3)]/ precise main restricted


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
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted unive                                                rse multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted u                                                niverse multiverse


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
root@web:/etc/apt#



```



Below are the packages that aren't marked "ii":

```


iU  linux-generic-pae                  3.2.0.51.61                         Complete Generic Linux kernel
iU  linux-image-generic-pae            3.2.0.51.61                         Generic Linux kernel image
rc  mdadm                              3.2.5-1ubuntu0.2                    tool to administer Linux MD arrays (software RAID)





```

Thanks again!

---

### Post by bapoumba on 2013-08-25
In your sources.list, there is some weird formatting on both backports lines. Is it also in the sources.list file or only in the copy/pasted block on the forums ?

If you have it in your sources.list, please correct the formatting and do the update/upgrade again.
You might even want to run a dist-upgrade that will better check dependencies :
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Edit: please also wait for koenn's input.

---

### Post by koenn on 2013-08-25
> **Brian_Murray said:**
> 
Below are the packages that aren't marked "ii":

```

iU  linux-generic-pae                  3.2.0.51.61                         Complete Generic Linux kernel
iU  linux-image-generic-pae            3.2.0.51.61                         Generic Linux kernel image
rc  mdadm                              3.2.5-1ubuntu0.2                    tool to administer Linux MD arrays (software RAID)

```


we'll ignore the mdadm because that's not an issue here

you have 2 kernel packages that are marked to be installed (first 'i') but are not (second 'i' = 'installed' but you have 'U' )

you probably want to remove those, assuming that your current kernel is already 3.2.0.52
you should check that first : ```
 uname -r 
```
if that checks out, your linux-headers package is the correct version and no longer part of the problem.

you might also want to look through that list of installed software to see what kernels are installed :  ```
dpkg -l linux*
```


if there is indeed something wrong with your sources list, as Bapoumba points out, you will want to fix that first, but only run 'apt-get update' afterwards, not upgrade. You want the list of available packages to be correct and up to date, but you don't want to install anything yet


also, how important is this server, and do you have backups ?

---

### Post by Brian_Murray on 2013-08-31
Thanks for all the feedback.  The sources.list file is formatted correctly, I'm not sure why it got messed up on the copy / paste and I get no errors when doing an apt-get update.  Given that everything seems installed correctly except an older version of the kernel, is there anyway of just manually editing the package manager database to tell it that everything is OK and at 3.2.0-52-generic-pae already?  My concern is how do I go about uninstalling the "old" version of the kernel, since clearly that's not what's actually currently installed.



The server is backed up, not insanely important, and due for a hardware refresh anyway.  If it makes more sense to just blow it all away and start fresh I can do that, but I'm hesitant to install Ubuntu server again if package issues are going to be an on going issue.  The last time I reinstalled the OS it was due to package issues after a failed distro upgrade... in short packages and I just don't seem to get along very well. ;)  I guess I'm just wondering that if I have to start fresh if I would be better off with a RHEL based CentOS since it's using a different package management system?  Are package issues common on Ubuntu servers that get the "apt-get update / apt-get ugprade" commands once or twice a month?  Am I doing something wrong there?  I do love the simplicity, speed, and minimalist nature of Ubuntu server over most of the other options.

Again, thanks for all the feedback.


Current dpkg -l |grep linux* output:

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                       Version                    Description
+++-==========================-==========================-====================================================================
un  linux-doc-3.2.0            <none>                     (no description available)
ii  linux-firmware             1.79.6                     Firmware for Linux kernel drivers
iU  linux-generic-pae          3.2.0.51.61                Complete Generic Linux kernel
un  linux-headers              <none>                     (no description available)
un  linux-headers-3            <none>                     (no description available)
un  linux-headers-3.0          <none>                     (no description available)
ii  linux-headers-3.2.0-36     3.2.0-36.57                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-gen 3.2.0-36.57                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37     3.2.0-37.58                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-gen 3.2.0-37.58                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38     3.2.0-38.61                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-gen 3.2.0-38.61                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39     3.2.0-39.62                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-gen 3.2.0-39.62                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40     3.2.0-40.64                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-gen 3.2.0-40.64                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41     3.2.0-41.66                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-gen 3.2.0-41.66                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-43     3.2.0-43.68                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-gen 3.2.0-43.68                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44     3.2.0-44.69                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-gen 3.2.0-44.69                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-45     3.2.0-45.70                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-gen 3.2.0-45.70                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48     3.2.0-48.74                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-gen 3.2.0-48.74                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51     3.2.0-51.77                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-gen 3.2.0-51.77                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52     3.2.0-52.78                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-gen 3.2.0-52.78                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic-pae  3.2.0.52.62                Generic Linux kernel headers
un  linux-image                <none>                     (no description available)
un  linux-image-3.0            <none>                     (no description available)
ii  linux-image-3.2.0-29-gener 3.2.0-29.46                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-gener 3.2.0-31.50                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-gener 3.2.0-32.51                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-gener 3.2.0-33.52                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-gener 3.2.0-34.53                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-gener 3.2.0-35.55                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-gener 3.2.0-36.57                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-gener 3.2.0-37.58                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-gener 3.2.0-38.61                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-gener 3.2.0-39.62                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-gener 3.2.0-40.64                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-gener 3.2.0-41.66                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-gener 3.2.0-43.68                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-gener 3.2.0-44.69                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-45-gener 3.2.0-45.70                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-gener 3.2.0-48.74                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
in  linux-image-3.2.0-51-gener <none>                     (no description available)
ii  linux-image-3.2.0-52-gener 3.2.0-52.78                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic-pae    3.2.0.51.61                Generic Linux kernel image
un  linux-initramfs-tool       <none>                     (no description available)
un  linux-kernel-headers       <none>                     (no description available)
un  linux-kernel-log-daemon    <none>                     (no description available)
ii  linux-libc-dev             3.2.0-51.77                Linux Kernel Headers for development
un  linux-restricted-common    <none>                     (no description available)
un  linux-source-3.2.0         <none>                     (no description available)
un  linux-tools                <none>                     (no description available)
un  linux32                    <none>                     (no description available)



```

---

### Post by bapoumba on 2013-08-31
I do not think any Linux distribution will do better/worse than another, maybe except debian stable that should be ultra stable but with less recent packages versions. You can check USN [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/) or subscribe to their mailing list to keep an eye on security updates.

---

### Post by koenn on 2013-09-03
the reason I asked about backups and how important this server is was not a hint to just start over, but rather: you're going to have to try and uninstall a kernel - you may and up with a server that is unbootable, so you need a fallback. Especially since I haven't done this before so I don't know what will happen.  (you've now been given fair warning :-) )

That also answers your other question : your problem is, imo, very rare. I've never seen it happen. No one else is joining this thread with "me too" or "I had the same or a similar problem, here's how I fixed it'


So here's what I think:

1-
uninstall the offending packages. Since the kernel versions are mentioned in the package names, you might simply try something like 
```
apt-get remove linux-image-3.2.0-51-generic-pae
```

apparently, apt or dpkg can uninstall specific versions of a package with an invocation like this
```
 apt-get remove linux-image-generic-pae=-3.2.0-51
```
i.e with ''=<version-number" appended to the package name

likewise with the headers packages
If apt-get doesn't work, look for the corresponding dpkg commands, and force them if necessary

At this point I'm not sure whether you should uninstall -51 to get rid of the 'iU' in your installed packages, or uninstall -52 to get it out of the way and allow -51 to fully install (and upgrade afterwards)
Both approaches might work


2- 
if you think you have at this point, you might want to run some apt-get invocations to make sure you have a bootable kernel. I'm thinking "apt-get install  --reinstall linux-image-generic-pae" and/or " apt-get install -f " (i.e. fix missing stuff)



3-  whatever you do, run update-grub before you reboot. You want to be pretty sure you have a bootable kernel installed before you even think about rebooting 

4- after reboot, do apt-get update. If no problems, do apt-get upgrade : run them separately so you don't attempt an upgrade with an incomplete packages list because this is bound to cause dependency issues.  If you get "packages held back", try apt-get dist-upgrade. Do some clean up (eg  'autoremove') afterwards

If you see anything scary during this procedure you can post it here so we can see how things are going. 


other option : in stead of trying to remove the 'iU' packages, try to get them completely installed (eg with dpkg -i  or see the man page for "force" options) so that your apt-get upgrade doesn't hang on them, then proceed with verifying that you have a working, bootable system, check what bootable kernels grub sees, clean up etc

good luck, and have fun.

---

### Post by Bashing-om on 2013-09-03
Brian_Murray; Hi !

If I may interject .
+1 to koenn's advise ! Let us reduce down to simpler terms and remove all those unneeded kernel versions. Remember to retain the current version you are running on and the one under it as a back up. Will be a tedious process - there are means to reduce the tedious - but due to the nature of the mixture of versions/pae-generic ... might be best to do this one entry at a time -VERY CAREFULLY,  watching for the possible errors generated. Might I also suggest that the option "apt-get purge" be used ... Now, when all the un-needed images have been removed, repeat the long process to remove the un-needed header files as well.
When this is done ... running "dpkg -l" command shows lots of "rc"s ; The state is rc, the package is removed, but the config files are not removed.
Now let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Little by little, I assure you, we will get the package manager lined out.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Brian_Murray on 2013-09-04
Cool, thanks guys.  I'll try and find some time to work on it here in the next couple days.  I really appreciate the help and I'll let you know what happens.

---

### Post by JnPson on 2013-09-04
I have had this problem for several weeks now and I couln't get any updates because of dependency problems.
```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-quantal : Depends: linux-image-3.5.0-36-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

It was so bad I was even thinking of doing a fresh install of Ubuntu Server 12.04.2. 

Today I was experimenting with Aptitude and looking at the different options so I logged on to my "troubled" server and typed
```

aptitude update && aptitude safe-upgrade

```
To my joy aptitude went pass the dependency problem and installed the missing updates. I believe I typed it twice to be safe. I tested a*pt-get update && apt-get dist-upgrade* but the problem was still there. *apt-get -f install* didn't help either. 

So I went throught the other options of aptitude and found *build-dep*, so I wrote
```
aptitude build-dep
```

Aptitude found the missing dependencies and asked if could remove it. It removed it without problems and after it finished I then ran *apt-get update && apt-get dist-upgrade* and it worked.
```
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 1514 kB in 3s (431 kB/s)                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@nas01:~# 

```
I haven't read the entire thread but I think this might help you too. 

Regards JnPson

---

