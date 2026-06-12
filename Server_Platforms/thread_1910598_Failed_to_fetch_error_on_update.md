---
title: "Failed to fetch error on update"
date: 2012-01-17
forum: Server Platforms
---

### Post by dinonet on 2012-01-17
Hi, I tried updating today and I got a bunch of errors like this

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_binary-i386_Packages - open (22: Invalid argument)

Could this be temporary or does anyone else have this issue? My sources file looks like this

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe

Any help would be greatly appreciated.

Thanks!

---

### Post by jerrrys on 2012-01-19
try

sudo rm /var/lib/apt/lists/* -vf 

sudo apt-get update

---

### Post by dinonet on 2012-01-19
> **jerrrys said:**
> try

sudo rm /var/lib/apt/lists/* -vf 

sudo apt-get update

Thanks. I tried it and I get a bunch of these. I didn't paste them all but just to give you an idea.


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_source_Sources - open (30: Read-only file system) [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-i386_Packages - open (30: Read-only file system) [IP: 91.189.92.181 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_binary-i386_Packages - open (30: Read-only file system) [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_source_Sources - open (30: Read-only file system) [IP: 91.189.92.183 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_source_Sources - open (30: Read-only file system) [IP: 91.189.92.184 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_Packages - open (30: Read-only file system) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_source_Sources - open (30: Read-only file system) [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_binary-i386_Packages - open (30: Read-only file system) [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_source_Sources - open (30: Read-only file system) [IP: 91.189.92.169 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock

---

### Post by jerrrys on 2012-01-19
sudo -i

apt-get clean

cd /var/lib/apt

mv lists lists.old

mkdir -p lists/partial

apt-get clean

apt-get update

This will rename your "list" folder to "list.old" for backup purposes and then rebuild.

---

### Post by dinonet on 2012-01-20
> **jerrrys said:**
> sudo -i

apt-get clean

cd /var/lib/apt

mv lists lists.old

mkdir -p lists/partial

apt-get clean

apt-get update

This will rename your "list" folder to "list.old" for backup purposes and then rebuild.

Thanks! Is what gets saved to this lists folder that messed things up?

---

### Post by jerrrys on 2012-01-20
Congratulations 

If you did an error free "apt-get update" then yes, the "list.old" folder is corrupted and can be deleted.  List.old served its purpose as a backup (the original) in-case something went wrong.

---

