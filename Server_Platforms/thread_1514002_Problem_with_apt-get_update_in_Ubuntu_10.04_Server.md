---
title: "Problem with apt-get update in Ubuntu 10.04 Server"
date: 2010-06-20
forum: Server Platforms
---

### Post by Becks7 on 2010-06-20
Hello,
I have the following problem with the sources.list in Ubunto 10.04. When I set the command apt-get update in terminal I get:

```
Err http://us.archive.ubuntu.com lucid-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.45 80]
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://security.ubuntu.com karmic-security/restricted Sources
Ign http://de.archive.ubuntu.com karmic-updates/main Packages
Ign http://de.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://de.archive.ubuntu.com karmic-updates/main Sources
Ign http://de.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://de.archive.ubuntu.com karmic-updates/universe Packages
Ign http://de.archive.ubuntu.com karmic-updates/universe Sources
Ign http://de.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://de.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://de.archive.ubuntu.com karmic/main Packages
Ign http://de.archive.ubuntu.com karmic/restricted Packages
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Ign http://security.ubuntu.com karmic-security/multiverse Packages
Ign http://security.ubuntu.com karmic-security/multiverse Sources
Err http://security.ubuntu.com lucid-security/main Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/restricted Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/main Sources
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/restricted Sources
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/universe Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/universe Sources
  404  Not Found [IP: 91.189.92.167 80]
Ign http://de.archive.ubuntu.com karmic/main Sources
Ign http://de.archive.ubuntu.com karmic/restricted Sources
Ign http://de.archive.ubuntu.com karmic/universe Packages
Ign http://de.archive.ubuntu.com karmic/universe Sources
Ign http://de.archive.ubuntu.com karmic/multiverse Packages
Ign http://de.archive.ubuntu.com karmic/multiverse Sources
Ign http://de.archive.ubuntu.com karmic-updates/main Packages
Ign http://de.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://de.archive.ubuntu.com karmic-updates/main Sources
Ign http://de.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://de.archive.ubuntu.com karmic-updates/universe Packages
Ign http://de.archive.ubuntu.com karmic-updates/universe Sources
Ign http://de.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://de.archive.ubuntu.com karmic-updates/multiverse Sources
Err http://de.archive.ubuntu.com karmic/main Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic/restricted Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic/main Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic/restricted Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic/universe Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic/universe Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic/multiverse Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic/multiverse Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic-updates/main Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic-updates/restricted Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic-updates/main Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://security.ubuntu.com lucid-security/multiverse Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com lucid-security/multiverse Sources
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com karmic-security/main Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com karmic-security/main Sources
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com karmic-security/restricted Sources
  404  Not Found [IP: 91.189.92.167 80]
Err http://de.archive.ubuntu.com karmic-updates/restricted Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic-updates/universe Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic-updates/universe Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic-updates/multiverse Packages
  404  Not Found [IP: 141.30.13.31 80]
Err http://de.archive.ubuntu.com karmic-updates/multiverse Sources
  404  Not Found [IP: 141.30.13.31 80]
Err http://security.ubuntu.com karmic-security/universe Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com karmic-security/universe Sources
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com karmic-security/multiverse Packages
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com karmic-security/multiverse Sources
  404  Not Found [IP: 91.189.92.167 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz  404  Not Found [IP: 141.30.13.31 80]

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  404  Not Found [IP: 141.30.13.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

This is my sources.list:

```
# 
# deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted

# deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

# Zenoss rapository
# deb http://dev.zenoss.org/deb main stable # disabled on upgrade to lucid

```

I tried all options but will not work. 

Can someone help me.

Thanks

---

### Post by CharlesA on 2010-06-20
This is what I get when I run apt-get update:
```
Hit http://download.virtualbox.org lucid Release.gpg
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation                                                                                                                               -en_US
Hit http://download.virtualbox.org lucid Release
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Hit http://download.virtualbox.org lucid/non-free Packages
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_                                                                                                                               US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_                                                                                                                               US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en                                                                                                                               _US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_U                                                                                                                               S
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en                                                                                                                               _US
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
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

Judging from the Karmic repos, you did an upgrade from karmic to Lucid, right?

/etc/apt/sources.list:

```
charles@thor:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted

#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted
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
deb http://download.virtualbox.org/virtualbox/debian lucid non-free

```

Your sources.list looks almost identical.

---

### Post by Becks7 on 2010-06-20
I tried to download a file with the command wget, but give me the following error:

Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-06-20 18:08:28 ERROR 404: Not Found.

I think my problem is in my server but don't know where :S 

I'm not sure that my upgrade is finished done without errors. How I can solve it ?

---

### Post by CharlesA on 2010-06-20
There is definitely something going on with the server. Best thing to do would be to backup your stuff and do a clean install of 10.04. I always do clean installs between versions, since I don't really trust upgrades to not break anything.

---

### Post by gdonwallace on 2010-06-20
Your getting 404 errors, so it could be that the servers are down for some reason or any number of reason that would normally give a 404 error.

I would suggest trying your internet connection and trying to FTP into one of the repos and see if you can get in.

Also if you have made changes to your firewall, check that to make sure it is not interfering with your connection to the internet.

Anyway, its a 404 error; just like you get on web pages sometimes.  The servers may have reached capacity, or something changed on their side.  Its hard to say.  Just keep trying.

---

### Post by Becks7 on 2010-06-20
Installed fresh copy of Ubuntu Server 10.04 64bit - the same think. Can't Install anything with apt-get install :(

Can anyone help ?

---

### Post by Vegan on 2010-06-20
I just checked with webmin on my server and there is no problem that I saw.

I ran....

sudo apt-get update
sudo apt-get upgrade

nothing to update

This is because I updated yesterday

---

### Post by Becks7 on 2010-06-20
@localhost:/$ wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb)
--2010-06-20 23:55:45--  [http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-06-20 23:55:45 ERROR 404: Not Found.

This is when I try to download webmin to the server

---

### Post by sjinks on 2010-06-20
I would suggest to try different mirrors.

---

### Post by Becks7 on 2010-06-20
Won't work :(

---

### Post by sjinks on 2010-06-20
Then I would suppose you have DNS problems, e.g., your ISP's DNS reports incorrect IP address for some servers.

What is the output of

dig -t A security.ubuntu.com

?

---

### Post by Becks7 on 2010-06-20
becks@localhost:/proftpd-1.3.3$ dig -t A security.ubuntu.com

; <<>> DiG 9.7.0-P1 <<>> -t A security.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24755
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 3, ADDITIONAL: 0

;; QUESTION SECTION:
;security.ubuntu.com.           IN      A

;; ANSWER SECTION:
security.ubuntu.com.    600     IN      A       91.189.88.37
security.ubuntu.com.    600     IN      A       91.189.92.167

;; AUTHORITY SECTION:
ubuntu.com.             140502  IN      NS      ns1.canonical.com.
ubuntu.com.             140502  IN      NS      ns3.canonical.com.
ubuntu.com.             140502  IN      NS      ns2.canonical.com.

;; Query time: 51 msec
;; SERVER: 78.90.248.7#53(78.90.248.7)
;; WHEN: Mon Jun 21 00:19:30 2010
;; MSG SIZE  rcvd: 133

---

### Post by madneon on 2010-06-20
Maybe you are behind some web-proxy and your configuration is wrong?
What internet connection do you have? What is your network configuration - */etc/network/interfaces*,
*/etc/resolv.conf* ?

What does *route*, *ifconfig* says?

---

### Post by Becks7 on 2010-06-20
# The loopback network interface
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
~

I'm using PPPoE


becks@localhost:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:9e:32:e6
          inet6 addr: fe80::2e0:4cff:fe9e:32e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11521881 (11.5 MB)  TX bytes:2315906 (2.3 MB)
          Interrupt:19 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2368 (2.3 KB)  TX bytes:2368 (2.3 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:78.90.252.60  P-t-P:78.90.248.30  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:13741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:11049319 (11.0 MB)  TX bytes:2038498 (2.0 MB)


Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
78.90.248.30    *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0


nameserver 78.90.248.7
nameserver 78.90.248.1
nameserver 78.90.248.6
nameserver 78.90.248.8

---

### Post by Becks7 on 2010-06-20
any idea ?

---

### Post by CharlesA on 2010-06-20
I get the same results when I use dig.

I don't know what is different with your machine. It sounds like it is not communicating properly or something.

---

### Post by Aperion on 2010-07-10
not sure if this was resolved or not. I Was getting 404 errors on update as well. I went into software sources and changed from us servers to main servers and it was solved.

---

### Post by ma2k1 on 2010-10-27
Just happened to me on Ubuntu 8.04.3 LTS 64 Server trying to install mtop.
**404 Not Found [IP: 91.189.92.167 80]**
Next I run
sudo -s
apt-get update 
and on successive retry *apt-get install mtop* work!

---

