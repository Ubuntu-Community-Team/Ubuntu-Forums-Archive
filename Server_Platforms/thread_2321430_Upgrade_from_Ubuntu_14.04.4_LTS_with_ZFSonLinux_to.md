---
title: "Upgrade from Ubuntu 14.04.4 LTS with ZFSonLinux to 16.04"
date: 2016-04-22
forum: Server Platforms
---

### Post by stan4 on 2016-04-22
I have an Ubuntu server installed on ext3/4 with ZFS mounted pool (user storage). As the ZFS built into 16.04 I'm wondering if it's safe to upgrade from 14.04 to 16.04 in my case and if anyone using ZFSonLinux has done it yet. Should I uninstall zfsonlinux before upgrading?

---

### Post by nerdtron on 2016-04-23
If this is a production server I'd say don't upgrade. If it's working now on 14.04 then don't do in-place upgrade directly to 16.04. Upgrades like this can introduce problems which can be hard to fix and you can't rollback immediately if something goes wrong.  If you really want to upgrade to 16.04 to use the native ZFS, then better to do a fresh install and then setup ZFS and migrate your data. It's a lot of work but at least it's a safer way.  

PS. I haven't tested the performance of ZFS on 16.04 yet.

---

### Post by darkod on 2016-04-23
A real migration of the data is not even needed probably. If the OS is on a separate disk (as it usually should be), you can simply export the zpools, do a clean install of 16.04, and import the zpools.

Of course, whether you choose to do a clean install will depend also on other services you might have configured on the server and how easy it is to configure them again on a new installation. But the zpools are very resilient and should survive the reinstall perfectly. And of course, don't do it without a good backup of the data.

About a year or two ago I was doing some testing between FreeNAS and ubuntu with ubuntu-zfs package. But the test was with smaller VBox VMs with small disks and only small amount of test data. The principle should be true for a prod system too... I did the ubuntu install, create small zpool on separate disks, put some small data there. Then I formatted the OS disk and installed FreeNAS, without even exporting the zpools first (I wanted to simulate a sudden crash where you had no time to export the pools). FreeNAS was able to pick them up perfectly, and the data structure was there. Even the quotas for the zfs datasets were kept if I remember correctly. Then I did it again, formatting the OS disk and putting ubuntu back. It was also able to pick up the zpool and import it without problems.

So despite that FreeNAS is based on BSD and ubuntu on debian linux, the zpool survived this ping-pong between OSs perfectly. Note that this was only a small zpool with little data and no special settings. Maybe on a larger scale it wouldn't have worked so smoothly. But I was happy with that test...

---

### Post by stan4 on 2016-04-24
Guys, if that were a production system I wouldn't have asked, I would have rolled out 14.04 LTS in a VM, set it up with ZFS, made snapshot for easy restore and experimented with the upgrade. Anyways, now that I've had time to play with this upgrade scenario, I can share my experience.

Starting with the 14.04 LTS with ubuntu-zfs installed, I have:
1. Stopped everything accessing ZFS pool
2. Exported ZFS pool
3. apt-get remove ubuntu-zfs
4. do-release-upgrade -d (to get to 16.04 before 16.04.1 is available)
5. after reboot into 16.04 I realized I needed to to apt remove spl-dkms

So at this point the ZFS pool would not automount, but would mount manually and I've spent some time troubleshooting it. What helped was:
1. aptitude remove zfs-doc (it also removed all the traces of trusty-zfs)
2. apt install zfsutils-linux 

So I think the proper steps for painless upgrade from 14.04 LTS to 16.04 LTS if you're using non-system ZFS pool are:
1. Stop everything accessing ZFS pool
2. Export ZFS pool
3. apt-get remove ubuntu-zfs zfs-doc spl-dkms
4. apt-get autoremove
5. do-release-upgrade -d 
6. apt install zfsutils-linux
7. (if it wouldn't happen automagically) import your ZFS pool

---

### Post by fermulator on 2017-04-14
> **stan4 said:**
> Guys, if that were a production system I wouldn't have asked, I would have rolled out 14.04 LTS in a VM, set it up with ZFS, made snapshot for easy restore and experimented with the upgrade. Anyways, now that I've had time to play with this upgrade scenario, I can share my experience.

Starting with the 14.04 LTS with ubuntu-zfs installed, I have:
1. Stopped everything accessing ZFS pool
2. Exported ZFS pool
3. apt-get remove ubuntu-zfs
4. do-release-upgrade -d (to get to 16.04 before 16.04.1 is available)
5. after reboot into 16.04 I realized I needed to to apt remove spl-dkms

So at this point the ZFS pool would not automount, but would mount manually and I've spent some time troubleshooting it. What helped was:
1. aptitude remove zfs-doc (it also removed all the traces of trusty-zfs)
2. apt install zfsutils-linux 

So I think the proper steps for painless upgrade from 14.04 LTS to 16.04 LTS if you're using non-system ZFS pool are:
1. Stop everything accessing ZFS pool
2. Export ZFS pool
3. apt-get remove ubuntu-zfs zfs-doc spl-dkms
4. apt-get autoremove
5. do-release-upgrade -d 
6. apt install zfsutils-linux
7. (if it wouldn't happen automagically) import your ZFS pool

WARNING
 - if you were keeping up with the latest package updates from this PPA [https://launchpad.net/~zfs-native](https://launchpad.net/~zfs-native), then in performing these steps you are likely to have DOWNGRADED your zfsonlinux version by a few minor releases. While this SHOULD NOT affect data integrity of your pools, there are a few bug fixes which will be missing, and if you're running a bleeding edge latest kernel you may inadvertently lose support for zfsonlinux.
 - suggest reading: [http://zfsonlinux.org/](http://zfsonlinux.org/) release notes for more information

PS:
 - I've contacted the owner of that PPA to see if I can assist with building zfsonlinux latest packages on Xenial and contributing there so that the PPA works for Ubuntu xenial as well.

---

