---
title: "Boot repair says drive is mounted"
date: 2016-01-13
forum: Virtualisation
---

### Post by Mahewa on 2016-01-13
I don't know what caused this issue.  I downloaded some seemingly benign updates to a Xubuntu instance I run in VirtualBox, and now it won't boot:

[IMG]http://s9.postimg.org/tsh1o5u9r/boot_error.png[/IMG]

So I downloaded the boot recovery ISO and attached it to the machine, it seems to run fine, but then I get this message:

[IMG]http://s9.postimg.org/7674xor5r/boot_repair_error.png[/IMG]

This makes no sense to me, since when I check in GParted, it's not mounted:

[IMG]http://s9.postimg.org/lggp967i7/GParted_info.png[/IMG]

In case it's helpful, here's the Drive-repair information dump: [http://paste.ubuntu.com/14487560/](http://paste.ubuntu.com/14487560/)
Any help would be very, very much appreciated.

---

### Post by oldfred on 2016-01-13
You have grub installed to the partition(PBR) as well as MBR. You do not normally install grub to PBR, but it looks more like file corruption.

Have you tried running fsck on sda1?
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Do not know what difference vbox makes, if any??

---

### Post by Mahewa on 2016-01-13
Thanks for the advice.  I tried that command, and got the following:

[IMG]http://s15.postimg.org/krftkng4b/fsck.png[/IMG]

How should I proceed?

---

### Post by oldfred on 2016-01-13
I would first try the suggested option of no options.

And then perhaps try backup superblock.
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda1
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

