---
title: "Unexpected Partition Mounting"
date: 2016-02-17
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2016-02-17
I'm a noob at all this, but a recent update to xenial has freaked me out.

My upgrade path is to rsync an existing release into a new partition and then do a dist-upgrade in the new partition.   As new releases are made wash, rinse, repeat and life goes on.   I've done this starting with trusty, then to vivid and now xenial (I didn't like U or W).   All of these partitions are on an SSD with data (sdb5) and backups (sdc5) on separate HDs.   I update the current release daily.

Something came down the pipe as an update on 15th or 16th Feb (my time, AWST) that now results in all SSD partitions loading on boot.   After some initial messing around trying to amend fstab and/or partition settings with the Disks program I gave up in frustration and loaded my backup copy of xenial (from 10th Feb) into  sda7 (the original xenial partition) and  sda8 (new creation).   I've left sda7 alone but have done a daily upgrade in sda8 to show what happens.

From the sda7 partition (not updated), gnome-disk-utility looks like this:
[ATTACH=CONFIG]267337[/ATTACH]

From the sda8 partition (updated), gnome-disk-utility looks like this:
[ATTACH=CONFIG]267338[/ATTACH]

and now all partitions are mounted under /media/wayne/   There was no "/media/wayne" before this problem (yeah, I'm wayne).

All UUIDs are unique and there's nothing real fancy in fstab.   All the fstab files look like this with the exception that the first two lines change to reflect the current partition.```

# / was on /dev/sda7 during installation
UUID=ac70df9f-b728-4ebb-b293-3a9b422d31b2 /               ext4    errors=remount-ro 0       1
# /media/data was on /dev/sdb5 during installation
UUID=5947bfa4-0c9f-4281-8d30-ab675e8e0b25 /media/data     ext4    defaults        0       2
# /media/backup was on /dev/sdc5 during installation
UUID=1122a345-8be0-495b-8359-80b7f7b1175a /media/backup     ext4    defaults        0       2 
```

I have no clue where to start with this issue.   Any/all advice would be appreciated.

---

### Post by Chazall1 on 2016-02-18
I am having the same issue. All my ssd partitios are mounting when I open my file manager. I right click on any mounted icon on my desktop, or in my file managers, nautilus or nemo. When I right click, choose eject, I get the following,Cannot eject drive in use: Device /dev/sdc9 is mounted. sdc9 is my /drive for ubuntu gnome. I also get the same issue when I am on Ubuntu mate 16.04. My / partition on mate is on /dev/sdc1. I do not have this issue with Ubuntu Gnome 15.10.

---

### Post by PJs Ronin on 2016-02-18
@ Chazall1.   I have no clue, but with about the 12th reload of the partition from my archives and then updated, this issue has gone away.   I'll leave this open for a couple of days to see if anyone comes up with a solution for you before marking it closed.[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=139200")

---

### Post by Chazall1 on 2016-02-20
My mounting issue occurs each time if coming from a screen timeout, log out and back in all my ssd partitions mount. I will keep an eye on it. Thanks

---

### Post by PJs Ronin on 2016-02-22
I think I have determined "what" was happening to my system, but not necessarily "why".

I read a recent post that in part mentioned using "sudo apt update/upgrade" instead of my customary "sudo apt-get update/upgrade".   I tried the apt syntax and liked the format so I edited my aliases (thanks Cavsfan) to "alias ud='sudo apt update && sudo apt upgrade && sudo apt clean'".   Everything seemed to execute well, except that all partitions were mounted, and hence this thread.   Not being able to resolve this issue I overwrote my xenial partition with an Fsarchive file I knew worked well.   Hindsight shows that when I did this my old .bashrc file using aliases with "apt-get" instead of "apt" was brought over so when I did a standard "ud" to update/upgrade my partition, it was "apt-get" and not "apt" that executed.   My partition was thus stable and familiar.

However, I would occasionally do a manual update/upgrade in terminal using "apt" instead of "apt-get" and on reboot my install had turned to worms and all partitions were being mounted.   My assumption that apt and apt-get had the same result was in error.

As a final test (and with a newly imported xenial backup) I performed a 'sudo apt update' then a 'sudo apt-get update' (no idea why, clutching at straws).    Here's what I get:
```
sudo apt update
Fetched 14.8 MB in 55s (264 kB/s)                                                                                                                 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
181 packages can be upgraded. Run 'apt list --upgradable' to see them.
``` And if I run 'sudo apt upgrade' it would happily update the 181 packages.   I aborted.

On the apt-get side I get this:```
sudo apt-get upgrade
0 to upgrade, 0 to newly install, 0 to remove and 181 not to upgrade.
wayne@xenial:~$ 
```

I've read the man entries for apt and apt-get as they pertain to 'upgrade' and I don't see any significant difference.   Nonetheless, I'm staying away from 'apt'.   I'll mark this thread as solved.

---

### Post by Chazall1 on 2016-02-26
I am staying with apt-get and have not used apt. I just want to find out why all my SSD drives are getting auto mounted. It is getting annoying and should not be happening at all. I have no errors in logs and I would like to salve this issue.

---

### Post by Chazall1 on 2016-02-27
I have the same issue with all my SSD partitions mounting, I choose to eject and same outcome. This issue is not solved!

Thanks

---

### Post by Chazall1 on 2016-03-03
Anyone looking into this issue. I have not been able to stop it from happening.

Thanks

---

