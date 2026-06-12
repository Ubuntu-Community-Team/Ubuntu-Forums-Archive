---
title: "[IDEA] Disk Manager by default"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by Bou on 2007-10-23
I rescued this thread from the [Gutsy idea pool]("http://ubuntuforums.org/showthread.php?t=429281&highlight=%5BIDEA%5D"), and opened a [specification for it]("https://wiki.ubuntu.com/DiskManagerByDefault"):

== Summary ==

Include a disk management utility in default Ubuntu installs.

== Release Note ==

There have been complaints that Ubuntu lacks a disk configuration utility, which forces newbies to manually edit fstab if they want to use a drive that was not present when they installed the system. Manually editing the file is difficult and frustrating to them, and not an ideal way to handle the issue on the long run.

An application exists by the name of Disk Manager, which keeps tracks and notifies of newly added units, and for extremely easy (automagical) configuration. That is the kind of stuff we want in Ubuntu.

-Disk Manager notifies about new drives:

[http://flomertens.free.fr/disk-manager/images/notify.png](http://flomertens.free.fr/disk-manager/images/notify.png)

-Disk Manager allows the user to mount or unmount drives without any hassle, even by providing a simple name for them:

[http://flomertens.free.fr/disk-manager/images/add.png](http://flomertens.free.fr/disk-manager/images/add.png)

-Disk Manager allows to easily enable NTFS writing support:

[http://flomertens.free.fr/disk-manager/images/main_general.png](http://flomertens.free.fr/disk-manager/images/main_general.png)

-Disk Manager allows to keep track of mounted / unmounted partitions and free space on them:

[http://flomertens.free.fr/disk-manager/images/main_advance.png](http://flomertens.free.fr/disk-manager/images/main_advance.png)

== Rationale ==

Ubuntu strives to be the easiest to use Linux distro. Several steps have been taken to make the user experience natural. Installing Disk Manager by default would make adding and removing hard disk units natural. Just another field where Ubuntu would stand out in simplicity.

== Use Cases ==

-David has been using Ubuntu for a short time, but he has already filled his hard drive. He buys a second one and, when he reboots, gets a notification telling him that a new HD has been found. He clicks the notification area icon and gets his new drive up and working in seconds and just with a few clicks. He doesn't know what fstab is, he will never need to worry about that.


If there are any forum ambassadors reading this, could you guys tell me if I followed the right procedure? Thanks in advance.

---

### Post by Turgon on 2007-10-23
1+

Ubuntu really needs this to be user friendly enough for new users. Installing and mounting a hard drive is just too difficult.

It would also be nice to see some encryption, raid and lvm support for this!

---

### Post by autocrosser on 2007-10-23
Bou & I are both talking about this one---please also look at this post:

[http://ubuntuforums.org/showthread.php?t=580757](http://ubuntuforums.org/showthread.php?t=580757)

We need to make one post our of all this...

I have contacted the Disk Manager dev & will contact the Gnome Gparted devs---I feel very strongly that the two apps would & should be blended into one app that (with the addition of raid creation) be a one stop for disk work.....somewhat like OSX's Disk Utility.


My E to DM's dev:

Hello-- 

On Ubuntu forums, Bou & I have both been talking about your software...I  would like to know if you are open to expanding Disk Manager to using  Gparted code to include partitioning work? I will contact Gnome Gparted  development & put the same question to them--I envision a blend of Disk  Manager & Gparted into one app similar to OSX's Disk Utility--The only  thing that would be missing would be easy raid creation...... 


Thank You for your time. 
Dean Loros 
autocrosser @ ubuntu forums

---

### Post by oponek on 2008-02-02
I think that it should be done in post-Hardy release.

---

