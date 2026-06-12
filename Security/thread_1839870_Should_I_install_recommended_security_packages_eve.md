---
title: "Should I install recommended security packages even if these can't be authenticated?"
date: 2011-09-06
forum: Security
---

### Post by arroy_0209 on 2011-09-06
As per latest ubuntu (10.04LTS) recommendations for important security updates, I tried to install all such packages but during the process, I got warning from ubuntu itself, telling me that the list contains some packages which can't be authenticated. These may damage or cause other harm to my system. The list includes: foomatic-filters, dhcp3-client, -common, firefox gnome-support, -branding, libwbclient0, libwebkit-1.0-2, libxfont1, linux-libc-dev, smbclient, samba-common, xulrunner-1.9.2 etc. It is surprising that ubuntu is recommending "important" packages while being not-so-sure if these can be harmful to the user. Anyway should I ignore the warning and install all the packages or is there anything better to do?

---

### Post by 2F4U on 2011-09-06
May I ask what repositories you are using? To me the list of packages looks OK and I would go ahead and install them, but I am not the person in question here. There is always a potential risk in installing updated packages, since they may introduce new bugs. However, it is as risky to not update and live with known security holes, since these may be exploited by hackers.

---

### Post by arroy_0209 on 2011-09-06
I am not sure about the repository, indeed I am not choosing any, I am automatically being led to the location from where files are to be downloaded. For example, part of one URI was like this:
[http://in.archive.ubuntu.com/lucid-update/](http://in.archive.ubuntu.com/lucid-update/)......

---

### Post by CharlesA on 2011-09-06
Can you post the contents of /etc/apt/sources.list in code tags please.

---

### Post by arroy_0209 on 2011-09-07
Thanks for your attention. Here is the content you wanted:
```

#deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid universe
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

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
This seems very instructive. However I would like to know your opinion regarding the content first.

---

### Post by CharlesA on 2011-09-07
Hmm that looks fine. Try running this and post the output:

```
sudo apt-get update
```

I wouldn't install anything that isn't unauthenticated.

---

### Post by DZ* on 2011-09-07
perhaps one of suggestions from here will help:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)

---

### Post by arroy_0209 on 2011-09-07
Thanks. The result of sudo apt-get update is this:

```

Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN
Hit http://in.archive.ubuntu.com lucid Release.gpg
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN
Hit http://security.ubuntu.com lucid-security Release
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid-updates Release.gpg
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid Release 
Hit http://in.archive.ubuntu.com lucid-updates Release               
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://in.archive.ubuntu.com lucid/main Packages
Hit http://in.archive.ubuntu.com lucid/restricted Packages
Hit http://in.archive.ubuntu.com lucid/main Sources
Hit http://in.archive.ubuntu.com lucid/restricted Sources
Hit http://in.archive.ubuntu.com lucid/universe Packages
Hit http://in.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://in.archive.ubuntu.com lucid/multiverse Packages
Hit http://in.archive.ubuntu.com lucid/multiverse Sources
Hit http://in.archive.ubuntu.com lucid-updates/main Packages
Hit http://in.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://in.archive.ubuntu.com lucid-updates/main Sources
Hit http://in.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://in.archive.ubuntu.com lucid-updates/universe Packages
Hit http://in.archive.ubuntu.com lucid-updates/universe Sources
Hit http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done

```Can you please explain a bit what this implies?

---

### Post by CharlesA on 2011-09-07
Just updates the list of repos. Try reinstalling the updates in question:

```
sudo apt-get upgrade
```

---

### Post by arroy_0209 on 2011-09-07
I have reinstalled the updates as you have suggested. But how does this (reinstallation) help? What was wrong with the previous update?


(In case you need, this is part of the result afte I gave the command:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  checkbox checkbox-gtk firefox firefox-branding firefox-gnome-support libgtk-vnc-1.0-0 linux-headers-2.6.32-33
  linux-headers-2.6.32-33-generic linux-image-2.6.32-33-generic linux-libc-dev xulrunner-1.9.2
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 64.5MB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-33-generic 2.6.32-33.72 [31.5MB]
.....
Preconfiguring packages ...
(Reading database ... 164845 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-33-generic 2.6.32-33.71 (using .../linux-image-2.6.32-33-generic_2.6.32-33.72_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-33-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
....
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.

Setting up firefox-gnome-support (3.6.22+build2+nobinonly-0ubuntu0.10.04.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...


```)

---

### Post by CharlesA on 2011-09-07
Looks ok now. I'm not sure what causes the packages cannot be authenticated message but if you already reinstalled them, you should be fine.

If there was a problem now, the update and upgrade would have thrown errors, which there were none, so it should be good to go now.

---

