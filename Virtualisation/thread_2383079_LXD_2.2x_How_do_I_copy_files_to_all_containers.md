---
title: "LXD 2.2x: How do I copy files to all containers"
date: 2018-01-20
forum: Virtualisation
---

### Post by etphonehome2 on 2018-01-20
My LXD host is using ZFS as the back end storage.
My LXD host has some files, eg., /etc/*****, and I want to copy these files to all containers prior to starting the containers.  How would I go about this?
My LXD host has some user files, and I want to copy these files to all containers prior to starting the containers.  How would I go about this, assuming I want it to go to /home/ubuntu/subdir/....?

How would I go about appending a file from LXD host to a container?

---

### Post by etphonehome2 on 2018-01-20
I found the answer to some of my questions:

[TABLE="width: 500"]
[TR]
[TD][LEFT][COLOR=#222222][FONT=Verdana]display the help[/FONT][/COLOR][/LEFT]
[/TD]
[TD]**lxc file ?****&#8203;**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][LEFT][COLOR=#222222][FONT=Verdana]push a pattern of files[/FONT][/COLOR][/LEFT]
[/TD]
[TD]**lxc file push -p /tmp/test* lxd001/tmp/newdir/**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][LEFT][COLOR=#222222][FONT=Verdana]push multiple files[/FONT][/COLOR][/LEFT]
[/TD]
[TD][COLOR=#222222][LEFT][COLOR=#222222][FONT=Verdana][FONT=Verdana]**lxc file push -p /tmp/test* /etc/host* lxd001/tmp/newdir/**[/FONT][/FONT][/COLOR][/LEFT]
[/COLOR][/TD]
[TD][/TD]
[/TR]
[/TABLE]


[COLOR=#222222][FONT=Verdana]I could not find a way to push to all containers, the only way is to script it.
[/FONT][/COLOR]
[LEFT][COLOR=#222222][FONT=Verdana]There is no way to append files, the only way is to script it.

[/FONT][/COLOR][/LEFT]

---

### Post by simosx on 2018-01-22
I think the most elegant way is to use **cloud-init**, as shown in the tutorial at
[https://blog.simos.info/how-to-preconfigure-lxd-containers-with-cloud-init/](https://blog.simos.info/how-to-preconfigure-lxd-containers-with-cloud-init/)

You edit an LXD profile with the cloud-init instructions that will copy the files and make other changes. 

The alternative that you are suggesting when the containers are not running, is to edit the container files directly.
Those container files are in /var/lib/lxd/containers/... (or /var/snap/lxd/common/lxd/containers/ if you use LXD as a snap).

---

