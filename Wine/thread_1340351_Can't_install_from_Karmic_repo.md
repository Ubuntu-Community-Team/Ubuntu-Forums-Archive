---
title: "Can't install from Karmic repo"
date: 2009-11-28
forum: Wine
---

### Post by dk75 on 2009-11-28
It looks like dependicies problem, like WINE depends on WINE1.2 but WINE1.2 is in conflict with WINE
```

root@kitsunes-zotac:/tmp# uname -a
Linux kitsunes-zotac 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

```
```

root@kitsunes-zotac:/tmp# cat /etc/apt/sources.list.d/ubuntu-wine-karmic.list
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main

```
```

root@kitsunes-zotac:/tmp# env LC_ALL=en_US.UTF8 apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

```
```

root@kitsunes-zotac:/tmp# env LC_ALL=en_US.UTF8 apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wine1.2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9,170kB of archives.
After this operation, 78.5MB of additional disk space will be used.
Selecting previously deselected package wine1.2.
(Reading database ... 157629 files and directories currently installed.)
Unpacking wine1.2 (from .../wine1.2_1.1.33-0ubuntu1~ppa1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up wine1.2 (1.1.33-0ubuntu1~ppa1) ...
start: Job failed to start
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```

root@kitsunes-zotac:/tmp# env LC_ALL=en_US.UTF8 apt-cache depends wine
wine
  Depends: wine1.2

```
```

root@kitsunes-zotac:/tmp# env LC_ALL=en_US.UTF8 apt-cache depends wine1.2
wine1.2
  Depends: procps
  Depends: binfmt-support
  Depends: ia32-libs
  Depends: lib32asound2
  Depends: libc6-i386
  Depends: lib32nss-mdns
  PreDepends: dpkg
  Suggests: xdg-utils
  Recommends: ttf-tahoma-replacement
  Recommends: ttf-symbol-replacement
  Recommends: ttf-liberation
  Recommends: winbind
  Recommends: wine1.2-gecko
  Recommends: ttf-mscorefonts-installer
  Conflicts: binfmt-support
  Conflicts: <libwine>
  Conflicts: <libwine-alsa>
  Conflicts: <libwine-arts>
  Conflicts: <libwine-capi>
  Conflicts: <libwine-cms>
  Conflicts: <libwine-esd>
  Conflicts: <libwine-gl>
  Conflicts: <libwine-gphoto2>
  Conflicts: <libwine-jack>
  Conflicts: <libwine-ldap>
  Conflicts: <libwine-nas>
  Conflicts: <libwine-print>
  Conflicts: <libwine-sane>
  Conflicts: <libwine-twain>
  Conflicts: wine
  Conflicts: <wine-doc>
  Conflicts: <wine-utils>
  Conflicts: <winesetuptk>
  Conflicts: <xwine>
  Replaces: <libwine-alsa>
  Replaces: <libwine-arts>
  Replaces: <libwine-capi>
  Replaces: <libwine-cms>
  Replaces: <libwine-esd>
  Replaces: <libwine-gl>
  Replaces: <libwine-gphoto2>
  Replaces: <libwine-jack>
  Replaces: <libwine-ldap>
  Replaces: <libwine-nas>
  Replaces: <libwine-print>
  Replaces: <libwine-sane>
  Replaces: <libwine-twain>
  Replaces: wine
  Replaces: <wine-doc>
  Replaces: <wine-utils>
  Replaces: <winesetuptk>
  Replaces: <xwine>

```

---

### Post by 8Kuula on 2009-11-28
$ sudo apt-get remove wine
$ sudo apt-get install wine1.2

---

### Post by dk75 on 2009-11-28
funny
did you thought that I didn't did that already few times?

```

root@kitsunes-zotac:~# env LC_ALL=en_US.UTF8 apt-get --purge remove wine wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages will be REMOVED:
  wine1.2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 78.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 158717 files and directories currently installed.)
Removing wine1.2 ...
Purging configuration files for wine1.2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@kitsunes-zotac:~# env LC_ALL=en_US.UTF8 apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wine1.2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9,170kB of archives.
After this operation, 78.5MB of additional disk space will be used.
Selecting previously deselected package wine1.2.
(Reading database ... 157629 files and directories currently installed.)
Unpacking wine1.2 (from .../wine1.2_1.1.33-0ubuntu1~ppa1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up wine1.2 (1.1.33-0ubuntu1~ppa1) ...
start: Job failed to start
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kitsunes-zotac:~# 

```

PS: I might have few "beans" but it is because usually I post at my national Ubuntu forum. But there is only one official WINE subforum at this main Ubuntu forum where I can post to actual developer not only to another Ubuntu user

---

### Post by 8Kuula on 2009-11-28
It's something to do with ubuntu-wine ppa repo, wine package from there marked with higer version number than one in ubuntu repos, or something.
I did remove wine and wine1.2 installs and installed only wine1.2 and it did clear for me.

> **dk75 said:**
> PS: I might have few "beans" but it is because usually I post at my national Ubuntu forum. But there is only one official WINE subforum at this main Ubuntu forum where I can post to actual developer not only to another Ubuntu user

Beans? I use vodka :]


Edit:
Bah, nvm, I don't know.

Edit2:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197) maybe #11 post gives some workground.

---

### Post by dk75 on 2009-11-29
ah, that's what I've needed.

It wasn post #11 in detail but all discussion in general.

It is old "/etc/sysctl.conf" configuration from Jaunty for most people and for me it was modyfication done for Scratchbox2 and ARMEL crosscompiler.

Faulty key is
```
vm.nmap_min_adr = XXXX
```
where "XXXX" is some number depend on configuration

After commenting it out wine1.2 installed without any problem

---

