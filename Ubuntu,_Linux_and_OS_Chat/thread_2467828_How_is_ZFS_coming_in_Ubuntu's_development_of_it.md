---
title: "How is ZFS coming in Ubuntu's development of it?"
date: 2021-10-08
forum: Ubuntu, Linux and OS Chat
---

### Post by rlynwood on 2021-10-08
Can anyone tell me what the expected timeline is for Ubuntu's default inclusion of ZFS is?  I didn't find a decent answer in a 'net search.  Thanks.

---

### Post by Tadaen_Sylvermane on 2021-10-09
Not sure anyone can give a definitive answer. "When it's ready" seems to be the general answer for most open source projects. That being said it's highly anticipated, I'm sure they aren't dragging their feet so to speak.

You can do it manually right now if you wanted to. I've not tried it yet. This thread had me google it. I may pick up a couple cheap 120gb ssds just to mess with it.

[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html#step-1-prepare-the-install-environment](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html#step-1-prepare-the-install-environment)

---

### Post by rlynwood on 2021-10-09
First, re. the admonition, I'm chatting, not seeking technical support.  I don't have zfs & don't intend on installing/using it unless it comes with the OS.  I'm in Chat because I assume that's where I go to talk about Ubuntu's plans, which is what I'm doing.

Second, I appreciate everything you've said, Tadaen_Sylvermane, but like me, you're declaring ignorance.  I'm trying to learn if I can find out what the development timeline is and how they're coming.  If no one here knows such things, where do I go to learn this?  The Ubuntu site doesn't seem to have dev. info., and 'net searches yield nothing after late '19.  How do I learn this?

---

### Post by kurt18947 on 2021-10-10
Have you seen this?

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

ZFS seems a bit of overkill for desktop systems. There is BTRFS which is supposed to offer some of the benefits of ZFS and can be chosen on install. I'm no expert in these things.

---

### Post by tea for one on 2021-10-10
> **rlynwood said:**
>  The Ubuntu site doesn't seem to have dev. info., and 'net searches yield nothing after late '19.

Here is some more information from 2020.
[https://didrocks.fr/tags/zfs/](https://didrocks.fr/tags/zfs/)

---

### Post by deadflowr on 2021-10-10
You'd probably get a more thorough answer here: [https://discourse.ubuntu.com/]("https://discourse.ubuntu.com/")

As far as I know ZFS is already included. At least on the kernel side of things.
But it seems that only the Desktop installer has an option to set it up at installation time.
Not sure what the current status is for Server installers. In terms of if or when it will be an option during a standard normal (no need to pre-configure things) install.

Even if not all parts are included by default, all parts are within the Ubuntu repository ecosystem, so no need to install from outside sources.

---

### Post by rlynwood on 2021-10-10
Yes, Tadaen_Sylvermane, I think you're right.  I've just spent hours surveying the various forums, including the one that I think looks like the closest an outsider can get to the primary developer of an adaptive software called ZSys which apparently is supposed to make Ubuntu work with ZFS.  Apparently, ZFS's development is independent of any distro and it's up to the distros to adapt to it, as Ubuntu is doing with ZSys.  And I haven't found any way to even guess how they're coming.  They seem to be trying to complete and stablize ZSys for 20.04 and precious little later.  So I guess it'll be quite a while.  Thanks for your work and help.

Thanks, tea for one.  I just checked that link and don't find anything I should pursue, but appreciate the info.

Yes, kurt18947, I have now, both because of your link and my own searching.  You're right:  it seems to be gross overkill for an ordinary consumer.  It's designed for humongous enterprise use.  Still, Fedora has moved to btrfs, a similar system, and Ubuntu has chosen to proceed in the same direction but with ZFS rather than BTRFS.  My system is just a bit more complicated than a normal person's, so I'll use and appreciate some of that power then it's ready.  But it doesn't look like it'll be any time soon despite the devs' enthusiasm.

Thanks, deadflowr.  I've just spent quite a while there and found my way to the subforum that deals with Ubuntu's adaptation--it's called ZSys--to ZFS, but it's quite old.  They're still working on 20.04, as I said above (see my other comments).  And, yes, I know now that it's available for use, but I'm not a dev or experimenter; I'm waiting for it to be the default file system.

---

### Post by TheFu on 2021-10-10
btrfs article: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/) be very careful with that file system until understanding the limitations and failure modes.

Using ZFS for data-only, not the OS, is an easy choice for people inclined to use multiple disks and who want _advanced storage management_.  Many people - probably over 90% want "simple" storage. It is easier to understand.  That isn't what ZFS or BTRFS or LVM+EXT4 provide. They are complex, but provide some interesting capabilities in storage management.

The fact that a file system isn't pre-installed means very little. It is still in the ubuntu repos and just as available as any other program in those repos. I suppose that's a philosophical discussion similar to whether to include f2fs or exfat or fat32 or ntfs.  I have much need for f2fs, ZERO need for exfat and only a few systems need fat32 or ntfs, but 90% of my Linux systems have zero need for non-native linux file systems.  The Ubuntu pre-installed software list is already quite bloated.  Even for cloud deployments, the Ubuntu cloud image is 80MB whereas alphine Linux image is under 3MB.  That's almost 30x larger!

One size doesn't fit everyone. Lacking any proactive user request, I'm inclined to NOT install extra file systems.  OTOH, I didn't think the "minimal Ubuntu Install" should include a bloated web browser too. The packaging team expressed their thanks, removed a few packages on my list, but not firefox.  It is their distro, their choice.  If I want something else, I can fork the distro and do it that way or just script to remove the bloated stuff I don't want, which is what I've done.  I purge nano as my first command on any new Ubuntu. That would make many people unhappy, probably.

---

### Post by deadflowr on 2021-10-11
That's a big jump,
from *when will it be included* to *when will it be the default*.
Those are totally different things.
As far as I know there is no plan to make it the default file system.

---

### Post by DuckHook on 2021-10-12
Not sure that I understand the OP's question.

ZFS is baked into the kernel now. To my knowledge, it's been that way since at least Bionic. To run LXD properly, one should set up at least a ZFS partition, but it's better to give it a whole HDD/SSD.

So, I'm a bit lost on what OP means by "expected timeline for default inclusion", since it's already included.

Of course, to manage the file system, one needs to install one simple package: zfsutils-linux, but that is easily done.

As for it being overkill, not really. I use LXD to sandbox many apps. It's also amazingly useful for running older versions, different flavours, quick and dirty containment, and the usual assortment of suspects. Since ZFS is practically de rigueur for LXD, then, far from overkill, it becomes a necessity for me as a desktop user too.

---

### Post by TheFu on 2021-10-12
I think the OP wants ZFS as a boot device and pre-installed on all versions of Ubuntu, selected as the default file system so that choosing anything else takes extra work - A checkbox is all that LVM+ext4 needs and I vaguely remember ZFS being a 'beta' option in 20.04 for the OS.

I can also confirm that lxd **really**, really, really, wants to force us into using ZFS. They have valid reasons, but I really hate being forced into something I'm not prepared to use.  Sure, lxd has methods to use other storage types and file systems, but those are poorly documented and I wasn't able to get LVM working, so I ended up with 
container storage ---> ZFS ---> block file --> LV ---> VG --> PV --> LVM --> Partition --> HDD.
Not exactly thin. I'd actually setup thin provisioned LV just for LXD's use, so it was pretty maddening to have to give up and use 2 extra layers that I didn't want.

There are lots of things LXD forces onto a system.  For example, LXD is only shipped as a snap package, so to use lxd and stay patched with lxd, snapd and snap packages have to be allowed.  LXD containers are extremely useful and don't require learning an entire new way of dealing with OSes like Docker and other containers do.  With LXD, we can treat the container just like a VM OS.  Also, there are plenty of options for which OS to run in an lxd container. The Ubuntus for containers are not as bloated as some containers like CentOS (75MB vs 150MB), but they aren't as light as the most popular container base OS - alpine, which is less than 5MB.  

If you are comfortable with a shell and need a light server, say for an internal website or postfix/email server, then alpine has much to offer. Install and init lxd, then run:
```
$ time lxc launch images:alpine/3.14/cloud alpine-two
Creating alpine-two
Starting alpine-two                         

[COLOR="#FF0000"]real    0m8.481s[/COLOR]
user    0m0.061s
sys     0m0.035s

```
No sudo needed.  Takes about 10 seconds to download and init, then launch.
```
$ lxc list
+-------------+---------+----------------------+------+------------+-----------+
|    NAME     |  STATE  |         IPV4         | IPV6 |    TYPE    | SNAPSHOTS |
+-------------+---------+----------------------+------+------------+-----------+
| alpine-two  | RUNNING | 172.22.22.237 (eth0) |      | PERSISTENT | 0         |
+-------------+---------+----------------------+------+------------+-----------+
```
Connect to the container ... 
```
$ lxc exec alpine-two  -- ash
```
Go crazy. It is the root account, so be careful. It "feels" like a Linux server should, just missing bash, which can be installed with the alpine package manager. Beware, any installed packages add to the bloat.  After installation - from inside the VM, it is using 44MB for /.  apk is the package management system on Alpine.  [https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management](https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management)  Best of all, they don't install nano!  That warms the cockles of my heart.  Use vi.
```
# apk add bash bash-completion
```
And how much bloat?
```
# df -Th
Filesystem           Type            Size      Used Available Use% Mounted on
lxd/containers/alpine-two
                     zfs             9.6G     [COLOR="#FF0000"]46.9M[/COLOR]      9.5G   0% /
```

Maybe Ubuntu 20.04 in a container isn't so bad?  Here's the storage used from inside an email gateway running 20.04 Ubuntu lxd image:
```
$ df -Th
Filesystem           Type      Size  Used Avail Use% Mounted on
lxd/containers/spam1 zfs        11G  [COLOR="#FF0000"]1.5G[/COLOR]  9.6G  13% /

```
Here's from inside a little wallabag web-app server (that a LAMP webapp like Read-It-Later) also on 20.04:
$ df -Th
Filesystem              Type      Size  Used Avail Use% Mounted on
lxd/containers/wallabag zfs        11G  [COLOR="#FF0000"]976M[/COLOR]  9.6G  10% /

On a different system, here's a 20.04 server just for backups - the answers appear to be from the hostOS, not just the container. This system isn't using ZFS for  container storage. 
```
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdc1      ext4       20G   [COLOR="#FF0000"]13G[/COLOR]  5.9G  68% /
```
There's a way to have the container dump all sorts of current information to json or yaml so we can see the RAM, CPU, and disk used. ... 
```
name: [COLOR="#008000"]back-2004[/COLOR]
    disk: {}
    memory:
      usage: 1222651904
      usage_peak: 5017935872
      swap_usage: 0
      swap_usage_peak: 0
    cpu:
      usage: 661756367660
```
Appears it can't figure out the storage since I didn't use ZFS. Found it under /var/snap/lxd/common/lxd/storage-pools/lxd/containers
# du -sh [COLOR="#008000"]back-2004[/COLOR]
[COLOR="#FF0000"]1.8G [/COLOR]   [COLOR="#008000"]back-2004[/COLOR]
That just has ssh and rdiff-backup stuff. Crazy, right?

---

### Post by DuckHook on 2021-10-12
This Alpine option is *AWESOME*!

I'm constantly learning cool stuff from you.

> **TheFu said:**
> I think the OP wants ZFS as a boot device and pre-installed on all versions of Ubuntu, selected as the default file system so that choosing anything else takes extra work - A checkbox is all that LVM+ext4 needs and I vaguely remember ZFS being a 'beta' option in 20.04 for the OS.
But, if memory serves, not on Focal. Granted, my memory is like a sieve these days, but I recall that it was now a regular selection at install (for the desktop anyways). That's why my HDD is set up entirely in ZFS on two laptops. That decision came with some unwanted fallout, but not relevant to the issue at hand. 

> I can also confirm that lxd **really**, really, really, wants to force us into using ZFS.
<snip>
Not exactly thin.
Anything but. Rather thick, I'd say. But for SOHO use, where fat, juicy installs aren't really a big deal, it's not an impediment. For uber-gurus running hundreds of container instances and wishing to eek the last smidgeon of efficiency out of each container, I understand the frustration.
> There are lots of things LXD forces onto a system.  For example, LXD is only shipped as a snap package, so to use lxd and stay patched with lxd, snapd and snap packages have to be allowed.
True enough. I've made my peace with snap—or at least called a truce with it. Even Firefox will henceforth be shipped only as a snap (Chromium has only been available that way for some time), so one has to come to terms with it and move on. But I do hear you.
> …Crazy, right?
What is there about the black art of computing that isn't crazy? :lolflag:
Stay safe, stay crazy.

DH

---

### Post by lammert-nijhof on 2021-10-12
I use ZFS since 2017 and it is a great file management system, that is a perfect fit for desktops too. ZFS is very reliable! I have used it on a HP dc5850 (Phenom II X4 B97; 8GB DDR2) and since 2019 with a Ryzen 3 2200G and 16GB DDR4. I installed Ubuntu 21.04 on ZFS and that works flawlessly. I use it mostly for the standard work and my hobby is virtual machines and since 2010 I use Virtualbox. The performance of OpenZFs and Virtualbox is good, I boot Ubuntu VMs in ~10 seconds and Windows 11 VM in ~30 seconds from a nvme-SSD. By default all storage and all caches are lz4 compressed by OpenZFS in Ubuntu. My compression ratio is ~2.0, which means that the system only needs half the IO Operations to boot an OS or to load a program. With respect to memory usage, on my system I limit the L1ARC memory cache to 4GB.

OpenZFS is a mature file system in contradiction to btrfs that is still finishing the more complex features. OpenZFS is also used on many other systems like FreeBSD; Proxmox; TrueNAS and more. I use a FreeBSD (Pentium 4 HT; 2GB DDR and 4 HDDs 2 IDE and 2 SATA) as my backup server. For incremental backups ZFS only sends the changed 128K records lz4 compressed! OpenZFS is superior for maintaining, snap-shotting and backing up your data.

However I'm less happy with the Ubuntu add-on for operating system snapshots, I  normally purge that function/package (zsys) directly. It is only used to create too many automatic snapshots with useless names. For 21.10 I had another look at it,  but I had a problem with it on Xubuntu 21.10 trying to revert to and  boot from a manual snapshot created with zsys. For all file systems (ext4; btrfs or openzfs) I would backup the home directory and the other user directories, so you can re-install the OS from scratch if needed.

---

### Post by DuckHook on 2021-10-13
> **DuckHook said:**
> …my HDD is set up entirely in ZFS on two laptops. That decision came with some unwanted fallout, but not relevant to the issue at hand.
> **lammert-nijhof said:**
> However I'm less happy with the Ubuntu add-on for operating system snapshots, I  normally purge that function/package (zsys) directly. It is only used to create too many automatic snapshots with useless names. For 21.10 I had another look at it,  but I had a problem with it on Xubuntu 21.10 trying to revert to and  boot from a manual snapshot created with zsys. For all file systems (ext4; btrfs or openzfs) I would backup the home directory and the other user directories, so you can re-install the OS from scratch if needed.
This was the "unwanted fallout" I mentioned. Glad you posted in detail. It may be relevant to the OP after all.

@OP

You can now choose to have the Ubuntu desktop install process automatically format your HDD/SSD as ZFS at time of initial install. However, as lammert-nijhof points out, this will also set it up to take snapshots of your system on an automated basis. This will quickly exhaust your free disk space and, at least for me, led to frustratingly obscure breakages that it took some time to correct. I had to do much the same as lammert-nijhof did, and disabled this function, but through obscure settings rather than by purging the zsys package. In future, I may use lammert-nijhof's nuke option because it is much simpler and easier to implement.

---

### Post by grahammechanical on 2021-10-13
I have a single machine running Ubuntu desktop. I have no experience with ZFS and a little experimental experience of btrfs some years ago. With btrfs an additional option is put into the Friendly Recovery menu. It was called apt-snapshots ... Revert to old snapshot and reboot. Does using ZFS put such an option into the Friendly Recovery menu?

Regards

---

### Post by lammert-nijhof on 2021-10-14
The function to revert to an old snapshot is present not in OpenZFS but in the Ubuntu add-on around zsys. Like I said, I found it did not work with manual created snapshots. I wrote a bug-report and a patch has already been issued, but not yet distributed. As far as I understood the cause was a mis-merge of source, that introduced an old version of initramfs. Today Ubuntu 21.10 will be released, I hope with that patch, since the bug has been classified as "critical". 

I have now two options using Ubuntu on OpenZFS.
- Purge zsys and work without the revert and reboot from a snapshot or
- switch off the automatic snapshots by:

systemctl --user stop zsys-user-savestate.timer 
systemctl --user disable zsys-user-savestate.timer 
sudo mv /etc/apt/apt.conf.d/90_zsys_system_autosnapshot /etc/apt/apt.conf.d/90_zsys_system_autosnapshot_disabled

and then I use the following command to create my manual snapshots (-s stands for the whole system directory structure including /home):

zsysctl save <snapshot name> -s

Note that OpenZFS itself is a rock solid professional file system. The problem is around the handling of manual system snapshots introduced by Ubuntu on top of OpenZFS. The whole situation has been complicated by the introduction of UEFI boot and its corresponding UEFI partition in the FAT format (Thanks Microsoft). That initramfs probably mishandles the FAT partition and always regenerates the last version of initrd, so you have a mismatch during the snapshot boot between the selected and last Linux versions.

I will try it out that patch during one of the next days.

---

### Post by TheFu on 2021-10-14
Snapshots are great!  Snapshots retained too long are a blight on a system.

I can see a use to have 2 weeks of snapshots retained by almost everyone - it wouldn't be tied to any specific number, just the time on a calendar. Of course, it would depend on how full the disk is and how good the admin is at making backups to other storage.

For lurkers ... I fear that normal people will confuse "snapshot" with "backup", a term that gets abused by so many backup tools.  Backups and snapshots aren't the same things.  Snapshots feed into backups and can make getting a good backup easier and cleaner, but until the bits of moved off the source storage to different storage, hopefully 500 miles away, it isn't really a "backup."  Using terms in a technically accurate way is very important.  Don't get me started about "full stack" developers that only know 1 language and very little about administration and security of systems.

---

### Post by lammert-nijhof on 2021-10-15
> **lammert-nijhof said:**
> The function to revert to an old snapshot is present not in OpenZFS but in the Ubuntu add-on around zsys. Like I said, I found it did not work with manual created snapshots. I wrote a bug-report and a patch has already been issued, but not yet distributed. As far as I understood the cause was a mis-merge of source, that introduced an old version of initramfs. Today Ubuntu 21.10 will be released, I hope with that patch, since the bug has been classified as "critical". 

I will try it out that patch during one of the next days.

Today the maintainer asked me to test that patch after, it has been made available in the "proposed" libraries. The problem seems to be solved, no more problems during the boot! The revert/rollback to a snapshot via the grub boot menu works fine. You can use Ubuntu again very soon with the snapshots, as soon as they move the modified software from proposed to the official version of Ubuntu 21.10. I will test it somewhat more with the coming Ubuntu updates, now I did test it with some files in my home folder. I will keep working with it and I installed it also on my Host OS. Normally I move early say November to the development edition of 22.04 and I will keep trying it in a VM, because I will depend on it. 

I keep you informed of the progress.

---

### Post by lammert-nijhof on 2021-10-15
Personally I don't like automated snapshots, the names are often useless and soon they clutter up your system. I use scripts to make manual snapshots and so I have the freedom to use my own rules for snapshot names and I can decide myself, which ones I want to keep or destroy.

---

### Post by DuckHook on 2021-10-15
> **lammert-nijhof said:**
> Personally I don't like automated snapshots, the names are often useless and soon they clutter up your system. I use scripts to make manual snapshots and so I have the freedom to use my own rules for snapshot names and I can decide myself, which ones I want to keep or destroy.
I'm glad that you are forging the path ahead for us (and I greatly appreciate it!). Your description of the problem is precisely why I disable this "feature": it was more painful than the "problem" it was meant to cure. One day I just found my HDD completely full. The traditional *df* showed lots of room. At that time, I did not know that *df* is not ZFS-aware and will return with incorrect readings. It took the better part of a day and ridiculous amounts of web-search-fu to understand the obscure processes going on behind the scenes. I had to use ZFS utilities to delete the accumulated shapshots, then disabled the service altogether. Like you, I want to control the whole snapshot process and not have the system blindly snapshot every time I do an update/upgrade.

Moreover, since I upgrade on a regular basis, the snapshots add up quickly. The old zsys process did not delete older snapshots to make way for newer ones and was not smart enough to free up disk space for non&#8209;snapshot storage needs. Perhaps it was early days and the worst bugs have been worked out, but it soured me on the whole concept.

I will await the results of your experimentation with anticipation.

---

### Post by Flimm on 2021-10-16
Since it's easy to miss, I wanted to point out that there is a known issue with ZFS in Ubuntu 21.10 which causes filesystem corruption. So don't install or upgrade to Ubuntu 21.10 if you're using ZFS.

See [the release notes]("https://discourse.ubuntu.com/t/impish-indri-release-notes/21951") (search for "ZFS").

---

### Post by zebra2 on 2021-10-16
Just a FYI but 21.10 had ZFS updates yesterday Oct 15th along with its release.  There was no Impish  21.10 until it was released.

---

### Post by DuckHook on 2021-10-16
> **Flimm said:**
> Since it's easy to miss, I wanted to point out that there is a known issue with ZFS in Ubuntu 21.10 which causes filesystem corruption. So don't install or upgrade to Ubuntu 21.10 if you're using ZFS.

See [the release notes]("https://discourse.ubuntu.com/t/impish-indri-release-notes/21951") (search for "ZFS").
Thank you for this timely and *very* relevant warning. I had actually considered upgrading one of my primary partitions to Impish because it solves the issue of support for my spanking new video card. I will now wait for the LTS (just announced to be called "Jammy Jellyfish") and live with my current GPU workaround.

So grateful for your warning. I have a large number of lxd containers running on zfs and would have been in tears had they all been corrupted.

---

### Post by lammert-nijhof on 2021-10-16
DON"T PANIC, but to be absolutely sure, postpone the upgrade to 21.10 with some weeks. I did already upgrade on the 13th of October not a Friday fortunately :( 

Well the error seems to be present in all releases and not only in 21.10. The first bug report is from January about "zfs-dkms 0.8.4-1ubuntu16", which means Ubuntu 20.04 or 20.10 in the time of ZFS on Linux (ZoL), thus before OpenZFS.
 I have updated to 21.10 this week from 21.04, but reading the 9 months long list of comments on the bug report, Ubuntu 21.04 had the same type of problem. Reading those bug report's comments I often see: encryption and manual updates of  ZFS from Github.  I have the impression, that combinations of kernel  releases and ZFS releases were used, that were not used and tested in  Ubuntu. In the comments often you see the people trying out different versions of  zfs-dkms, some work with that kernel and others not. Of course all those combinations should work, but sticking to  official Ubuntu releases is far more secure :) 

I detected no issues with ZFS not in 21.04 nor in 21.10, only once I had one scrub error on my laptop, corrected automatically by OpenZFS 2.0.2 (Ubuntu 21.04). Today I did run my weekly backup again and then all changes to all 3 datapools are send to my 2 backups and there was no error reported. To be absolutely sure, tonight I will run "zpool scrub" again for all my 3 datapools and that takes hours. Fortunately in case of issues I have 12 weeks of snapshots on my backup :)

Note that "zpool scrub" reads all directories and all files and compares the stored checksums (fletcher 4) of the files and directories with the re-calculated checksums after the read. The last time my system did it, has been on Sunday morning the 10th of October at 0:00 and no errors were detected. Ubuntu starts it by default the 2nd Sunday of the month and you can check the results by "zpool status". So I'm absolutely sure on the 10th of October everything was fine; no hw errors; no file system corruption and no bitrot.

UPDATE SUNDAY: I did run scrub for all my datapools and there are no problems, the filesystems are fine.

---

### Post by kevdog on 2021-11-24
So I'm just trying to get a feel how ZFS is managed from the Ubuntu side.  I currently use some Arch systems with zfs-dkms.  I'm currently using a product known as znapzend [https://github.com/oetiker/znapzend](https://github.com/oetiker/znapzend) that auto manages creation/deletion of snapshots and sending to remote server. I'm aware there are other options for snapshot management such as sanoid/syncoid [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid). I'm not aware of any of these solutions making it possible to boot to snapshot or clone automatically.

How does Ubuntu's snapshot management tool differ?  Does it not delete old snapshots?  Does it have option to boot to old/most recent snapshot/clone automatically?  

ZFS is pretty reliable until it isnt -- meaning the problems I've mostly encountered during zfs are during kernel upgrades when a utility such as zfs-dkms is broken, or the initramd isn't generated properly.  With arch, ZFS isn't in the mainline kernel so it needs to be added during kernel upgrade via dkms (or use a kernel specifically precompiled with zfs modules).  Although I've never used zfs within Ubuntu, I'm guessing?? Ubuntu uses a similar approach since this post mentions zfs-dkms.  

When updating kernels, I'm wondering if Ubuntu users using ZFS have seen some systems failing to boot because of a bad initramfs generation.  What did you do to recover? or does this not really happen?  One of the tools I need to use to recover a broken system (virtual or actual system), is an arch-chroot allowing me to boot via USB/CD-ROM iso (acutal or virtual), and mount the corrupted filesystem via chroot, and then reinstall a new kernel, a newer or older zfs-dkms package, or regenerate the initramfs.  I'm aware debian has a similar debian-chroot (although I've never used it), but does Ubuntu have a similar utility (or do you just use debian's tool or something else?).  I can't imagine not having a chroot ability to rescue a broken kernel upgrade.

---

