---
title: "HTTP local repository and GPG problem"
date: 2009-08-19
forum: Security
---

### Post by fapo on 2009-08-19
Hi all. I have a local HTTP Apache server (into a NSLU2 embedded device) that for years always made my Ubuntu computers upgraded thanks to debmirror.
Monthly Cron updates the local repository via a script with a debmirror command. It downloads the main,restricted,multiverse,universe,backports,security repositories (Jaunty is ~27 GB for i386).
My machines are connected firstly with the NSLU2 address and after with a web mirror. I never take care about GPG signs, but now my most upgraded machine seems to always open the Update Manager. It always fails in upgrade (but the system have already downloaded and installed the packages shown) because of the GPG sign verify (that return NODATA1 NODATA2).

My question is: do you know a way to entrust a (local) mirror without need to create a gpg pair keys, or how can I deactivate the GPG signs checking?

Thanks in advance and sorry for my English.
fapo

---

### Post by shaggy999 on 2009-08-19
How are you running debmirror? Here's my debmirror command:

```

debmirror --passive \
          --progress \
          --verbose \
          --nosource \
          --method=$METHOD \
          --host=$HOST \
          --root=$ROOT \
          --dist=$DIST_ALL \
          --section=$SECTION \
          --arch=$ARCH \
          --ignore-release-gpg \
          --getcontents \
          $MIRROR_DIR/$DIST/canonical | tee $LOG

```

The contents of the variables should be of no consequence, but anyway as you see I use the --ignore-release-gpg option in my command. If you don't use it maybe adding it will help?

---

### Post by fapo on 2009-08-19
> **shaggy999 said:**
> How are you running debmirror? Here's my debmirror command:

```

debmirror --passive \
          --progress \
          --verbose \
          --nosource \
          --method=$METHOD \
          --host=$HOST \
          --root=$ROOT \
          --dist=$DIST_ALL \
          --section=$SECTION \
          --arch=$ARCH \
          --ignore-release-gpg \
          --getcontents \
          $MIRROR_DIR/$DIST/canonical | tee $LOG

```

The contents of the variables should be of no consequence, but anyway as you see I use the --ignore-release-gpg option in my command. If you don't use it maybe adding it will help?

Mine is very similiar and already has the --ignore-release-gpg . I don't have --getcontents , I can try to add it but... :confused:

I tried to uncheck all the packages from the Update Manager window and seems to be no more in a loop; if I reopen it manually the packages appears all selected.

This is one of my scripts:
```

HOST="na.mirror.garr.it"
ROOT="ubuntu"
DIST="jaunty"
debmirror --nosource -m --host=$HOST --root=$ROOT --method=ftp --progress --dist=$DIST --section=main,restricted,multiverse,universe --arch=$ARCH ubuntu/ --ignore-release-gpg && date > end.txt

```

Thanks for reply :P

---

### Post by shaggy999 on 2009-08-20
Is it possible that there's something wrong with the server you're syncing from? Perhaps try selecting another server or set one of your systems to a regular ubuntu mirror and see if that changes anything?

---

### Post by fapo on 2009-08-24
> **shaggy999 said:**
> Is it possible that there's something wrong with the server you're syncing from? Perhaps try selecting another server or set one of your systems to a regular ubuntu mirror and see if that changes anything?

It could be for me too, the message is:

W: GPG Error: [http://192.168.10.252](http://192.168.10.252) jaunty Release: Following signs was not valid: NODATA 1 NODATA 2

I done a "sudo apt-get install git-core" and after the successful installation (downloading via local) the Update Manager is woke up and asked for verify new updates. Now there are packages into "updates" category that really need to upgrade (like the kernel-2.6.28.15), so I agreed that could be for a not up to date web mirror. I try to change mirror into the sources.list and upgrade my local.

For the moment thanks :popcorn:

---

