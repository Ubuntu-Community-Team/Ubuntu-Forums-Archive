---
title: "Repo Down, Have a Copy Local"
date: 2012-08-09
forum: Server Platforms
---

### Post by cardy_c on 2012-08-09
Hi, I am trying to install vBilling with a script but it's giving me the error;

Initialized empty Git repository in /vBilling/.git/
github.com[0: 207.97.227.239]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)

So I assume the repo is unavailable, but I have a copy of the repo downloaded how can I alter the script to look local for what it needs?

VBILLING_REPO=git://github.com/digitallinx/vBilling.git
#TEMPDIR=$(/bin/mktemp -d)
TEMPDIR=$(/tmp/tmp)
FS_GIT_REPO=git://git.freeswitch.org/freeswitch.git
FS_INSTALL_PATH=/home/vBilling/freeswitch
FS_BASE_PATH=/usr/local/src/
FS_USER=freeswitch
VBILLING_DB=vBilling
VBILLING_DB_USER=vBilling
CURRENT_PATH=$PWD
UPGRADE="0"

Cheers

---

### Post by rubylaser on 2012-08-10
The repository seems to work fine for me here.

```
Zack-Reeds-Mac-Pro ~ $ git clone git://github.com/digitallinx/vBilling.git
Cloning into 'vBilling'...
remote: Counting objects: 1919, done.
remote: Compressing objects: 100% (899/899), done.
remote: Total 1919 (delta 986), reused 1850 (delta 917)
Receiving objects: 100% (1919/1919), 10.61 MiB | 1.62 MiB/s, done.
Resolving deltas: 100% (986/986), done.

Zack-Reeds-Mac-Pro ~ $ git clone git://git.freeswitch.org/freeswitch.git
Cloning into 'freeswitch'...
remote: Counting objects: 190998, done.
remote: Compressing objects: 100% (38393/38393), done.
remote: Total 190998 (delta 147555), reused 189584 (delta 146167)
Receiving objects: 100% (190998/190998), 80.25 MiB | 1.97 MiB/s, done.
Resolving deltas: 100% (147555/147555), done.
Checking out files: 100% (11015/11015), done.

```

You'd just need to update the FS_GIT_REPO variable to point to the path on your system

---

