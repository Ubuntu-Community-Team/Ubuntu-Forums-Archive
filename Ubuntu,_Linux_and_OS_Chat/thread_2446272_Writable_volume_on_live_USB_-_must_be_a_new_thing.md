---
title: "Writable volume on live USB - must be a new thing?"
date: 2020-06-27
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2020-06-27
Quite some time ago Ubuntu's Startup Disk Creator quit working properly for creating newer live USB's of newer versions of Ubuntu in older installed Ubuntu operating systems. If you've been around for several years (or longer) you'll remember this. Something I hadn't noticed until now is the existence of a "Writable" volume which mounts separately when the drive is inserted in an installed system:

[ATTACH=CONFIG]286329[/ATTACH]

I think they did away with casper-rw so what's up? Could other user-selected files be saved to that volume as well?

---

### Post by sudodus on 2020-06-27
Hi kansasnoob,

Yes, this is new. They have replaced 'casper-rw' with 'writable' as the default name, but for partitions, you can still use 'casper-rw' as label, although they prefer 'writable'.

Also, which may seem strange, a cloned live drive is no longer read-only, but it creates an ext4 partition with the label 'writable' behind the cloned part of the drive *automatically*. This partition is used to store log files and possible crash dumps. I think the intention is to make it easier to debug problems during installation (and otherwise during live sessions).

It is possible to turn off this with the boot option 'nopersistent'.

It is possible to use this 'writable' partition for persistence with the boot option 'persistent', and get a persistent live drive.

See these links,

[How is it easier to make a persistent live drive with Ubuntu 19.10?](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10)

[How can I get a live-only drive with Ubuntu 19.10 and newer versions?](https://askubuntu.com/questions/1189020/how-can-i-get-a-live-only-drive-with-ubuntu-19-10-and-newer-versions)

and the bug report #1863672 [The 'new' persistent live method starting in 19.10 no longer works](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672)

---

### Post by kansasnoob on 2020-06-27
Very informative. Many thanks. Now that I have less and less time to play I find all kinds of changes that catch me by surprise :)

In that particular case I'd used that drive to perform several installations and then it got tossed on my desk without labeling it. So when needed again I had to sort which drive had which OS on it. That's when I noticed the Writable volume. No doubt I could plow through the copied logs and find information about each of those installations.

I seldom use Ubuntu as a live repair OS anymore. When I do need to use Ubuntu live I almost always grab the latest LTS daily build - which should NOT be used for installations because proposed updates are enabled AFAIK. But they're great for temporary usage.

---

### Post by sudodus on 2020-06-27
With today's big and fast USB 3 pendrives and fairly cheap SSDs, you can have a persistent live drive with a big partition for persistence and even do

```

sudo apt update && sudo apt full-upgrade

```

Such a drive is a nice experience. In Windows I can recommend [Rufus](https://rufus.ie), and in Ubuntu of course my own [mkusb](https://help.ubuntu.com/community/mkusb) for that purpose.

Another nice system for portable drives in an [installed Ubuntu system that can boot both in UEFI and BIOS mode](https://ubuntuforums.org/showthread.php?t=1958073&page=49&p=13968438#post13968438).

---

### Post by kansasnoob on 2020-06-27
Yep, left that out - I do have an external SSD that boots either UEFI or MSDOS systems. It's a dream for repairing most 64 bit Linux systems or copying files from pretty much any OS. There are exceptions - like needing a live drive with a specific kernel - but they're few and far between.

---

### Post by C.S.Cameron on 2020-06-27
It is simple to turn the "writable" partition on a modern Live USB into a NTFS partition that will share data on Windows and Linux computers.

[https://askubuntu.com/questions/1198035/add-ntfs-data-partition-to-startup-disk-creator-usb-install/1198037#1198037](https://askubuntu.com/questions/1198035/add-ntfs-data-partition-to-startup-disk-creator-usb-install/1198037#1198037)

---

### Post by mastablasta on 2020-06-29
> **sudodus said:**
> 

Yes, this is new. 

is this only for ubuntu startup disk creator or in general for USB "makers"

---

### Post by sudodus on 2020-06-29
> **mastablasta said:**
> is this only for ubuntu startup disk creator or in general for USB "makers"

- The Ubuntu Startup Disk Creator is a cloning tool, and the result will be exactly the same with all cloning tools/methods.

- There are also extracting tools, for example Rufus (in its standard mode), Unetbootin and mkusb-dus (when making a persistent live drive). Extracting tools do various things when creating the USB boot drive, and in some cases, they can create persistent live drives.
. Rufus and mkusb-plug use this new feature of Ubuntu.
. mkusb-dus uses an old feature/method to use a partition for persistence.
. If I understand correctly, Unetbootin is still creating files for persistence (limited to 4 GiB in a FAT32 partition).

[hr][/hr]
- The label 'writable' is new, and I think used only by Ubuntu and the Ubuntu family flavours.

- Ubuntu creates this partition for persistence automatically, if there is unallocated drive space, so a cloned USB drive can be used as a persistent live drive, if you add the boot option persistent manually at boot.

- This easy way to use partition for persistence described here works in Debian too, but I don't think Debian will create the partition for you if there is unallocated drive space. *You* have to add the partition.

- Similar automatic methods are used by several Linux distros. Some of them provide suitable boot menus, so that you not only get logging, but also a full persistent live system in a fully automatic way. OpenSUSE and Knoppix did it years ago, this year there are several other linux distros that do it too. Unfortunately Ubuntu has not yet taken full advantage of the feature, so you have to add 'persistent' to the linux line in the menuentry for persistence to work.

---

