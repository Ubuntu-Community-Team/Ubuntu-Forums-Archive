---
title: "What all tools should be install for the best zfs experience"
date: 2019-12-19
forum: Ubuntu Development Version
---

### Post by hpu3 on 2019-12-19
I  have a fair bit of experience with zfs already having been a long time user of openindian/hipster.  (An open source offshoot of solaris)

zfs is native to openindiana so  have used zfs/zpool a fair bit.

However, a search the focal fossa apt repo shows the basic zfsutils but also at least 2 tools that claim to do auto snapshots.
then a few other things: libzfs2linux claims to be openzfs library for linux... apparently not the same zfs as in zfsutils, l grubzfs-testsuite...  and a few more.

Goggle pages offering to explain how to install zfs on ubuntu only mention zfsutils.  Actually that is wrong too, several googled pages say to 
`apt-get install zfs' which, of course, does not exist on focal fossa default pkg repository.

Hard to tell just from `aptitude show' whats' what, so hoping someone who has been using zfs on focal fossa a while will coach me a little

---

### Post by leespa on 2020-01-23
Did you happen to find an answer to this?
I am looking to fire up a new server as well with ZFS on Linux. Been using ZFS on FreeBSD 9.x since 2013, but it is getting a little long in the tooth.

---

### Post by averyfreeman on 2020-01-31
Hi

Another Illumos user here (OmniOS in my case)

I set up Ubuntu 19.10 on my laptop bc of the installer's new ZFS option, really happy with it so far

I wrote some scripts for zfsnap, since the maintainer's package of zfsnap does not come with any default implementation. They're listed here:  [https://github.com/averyfreeman/zfsnap-scripts-ubuntu-19.10](https://github.com/averyfreeman/zfsnap-scripts-ubuntu-19.10)

They should work pretty well with any 19.10 or newer system and the default installer's dataset layout

Also, you'll probably miss beadm, but GRUB actually has a "history" section now with snapshots. 

I have to do more testing to find out the mechanism with which GRUB updates "history",  but I *believe* the way it is updated is through zfs-initramfs,and after taking snapshots if you run 'update-grub' it'll put snapshots in your GRUB "history" section.

---

