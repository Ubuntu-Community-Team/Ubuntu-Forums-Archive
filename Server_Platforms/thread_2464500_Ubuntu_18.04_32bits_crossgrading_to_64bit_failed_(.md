---
title: "Ubuntu 18.04 32bits crossgrading to 64bit failed (unusrpisingly) need suggestions"
date: 2021-07-03
forum: Server Platforms
---

### Post by lxme on 2021-07-03
Hello,
I have this (very) old ubuntu 18.04 home server running apache, a ERP software, torrent downloader an acting as a NFS/Samba fileserver.. this thing went through a lot: migration from 14.04 to 16.04 and lately 18.04. Crashed once (HDD failure), as well as a complete hardware change.
This new hardware is 64Bits compatible, and I really want to install new stuff, including virtualization, that requires 64Bit compatibility.

I like to tinker, I like challenge, so I tried crossgrading.. that challenge was way to high for me.
What other options do I have?

I would really try my best *not to reinstall everything*, aren't there a way to copy files and settings from my server directly to a running 18.04 64bit ubuntu installation and go from there ? or cloning onto a 64bit ubuntu?

All ideas are welcome

Thank you

---

### Post by CharlesA on 2021-07-03
I can't really think of a good way to do it tbh. You can get a list of the installed packages and install them on the new install, but that means you'll need to copy the configuration files/databases over manually and you might miss something.

Do you have a backup of this machine so you don't lose any data in case this fails?

EDIT: I'm assuming by crossgrading, you tried this method?
[https://askubuntu.com/questions/5018/is-it-possible-to-upgrade-from-a-32bit-to-a-64bit-installation](https://askubuntu.com/questions/5018/is-it-possible-to-upgrade-from-a-32bit-to-a-64bit-installation)

---

### Post by lxme on 2021-07-03
Yes indeed, I tried what's in your link, but also
this one [http://www.ewan.cc/?q=node/90](http://www.ewan.cc/?q=node/90)
That was my first attempt.. chroot a new 64bit based system and replace 32bit version of base system on my installation.

And this script, [https://github.com/pbkwee/distrorejuve](https://github.com/pbkwee/distrorejuve) abeit very alpha..
Both left me with 64 bit kernel and 64 bit systems, but broken apt and dependency hell I couldn't fix.

I also tried to run an ubuntu install CD to see if an upgrade could be done from the installer since it has been claimed to work.. well not with 18.10 DVD in my experience  :(

I have virtualized a clone of my server, that way I can test and try things on it without braking or loosing anything.

For now, I am stuck with 18.04 32bit ubuntu :(

---

### Post by scorp123 on 2021-07-03
> **lxme said:**
>  I would really try my best *not to reinstall everything*

But why??  It would be the quickest and cleanest way.

Just backup everything (e.g. to an external USB harddrive? They are big and cheap these days ...), especially all the config files inside **/etc**, your personal data inside **/home** ... reinstall and then restore those files back where appropriate. Voila, done. If anything is missing you can still get it from the backup.

---

### Post by CharlesA on 2021-07-03
> **lxme said:**
> 
I have virtualized a clone of my server, that way I can test and try things on it without braking or loosing anything.


That's good news at least.

If you haven't tried this yet.. it might work, but you still need to do a clean install of a supported 64-bit version of Ubuntu.

[https://www.cyberciti.biz/faq/how-to-list-all-installed-packages-debian-ubuntu/](https://www.cyberciti.biz/faq/how-to-list-all-installed-packages-debian-ubuntu/)

That also means you need to transfer the configuration files over manually. Where they are stored depends on the application though.

---

### Post by TheFu on 2021-07-03
You can't.  Don't bother. It will fail.

The solution is to backup 
[LIST]
[*]data
[*] all of /etc/
[*]system settings
[*]lists of manually installed packages
[*]home directories
[/LIST]
Those are all cross-platform - well, at least i32 vs i64 compatible.  Get 100% clean copies of those things. For example do not backup DBMS files while the DB is running.  Do a dump-to-text file for any DBMS data and be 100% certain you understand how to import the dump.  The database import commands aren't tied to 32-bit or 64-bit versions.

Do a fresh install, minimal server. Basically nothing but ssh.  Then put the data, selected system settings and home directories back into the directory structure where they came from the old install.  DO NOT RESTORE /etc/ blindly.  Only specific files - perhaps 10 - should be restored.  Use the old passwd and group files to ensure the restored data has the correct uid/gid numbers.  The underlying storage can be completely different. We can change from ext3 to ZFS or LVM+ext4 or whatever. That doesn't matter.  All that matters is for the directories to be in the correct location and the userid + groupid for each file and directory to be correct with the correct permissions.  That means a backup tool must be used - we can't just copy files and call that "a backup".   That only works for about 95% of file in a single userid's HOME.  Everywhere else, it fails, badly.  Really badly.

After all the data, userids, [[necessary]] settings have been restored, then it is time to feed the list of manually backed up packages back into APT.  Since the dependencies will have changed, we only want the manual package lists. Let APT figure out the dependences.  Also, don't use any PPAs this time.  Add those only as necessary. Most of the time, it isn't needed.

For more about restoring: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

I've done this process a few times. Most recently was a about a year ago in a 16.04 --> 20.04 desktop move.  NFS isn't any different that I can tell, so those config files can be copied over.  I don't have any web servers running on 20.04, but the change from 16.04 --> 18.04 was mostly painless.  My analytics engine did fail. Some day I'll correct that.  There are always a few tiny issues and on each system I've done upgrades on the issues were always different.  I have 1 system left to upgrade. It scares me and I've put it off a few months. ESM is working for it, for now.

Worst situation I had required 3 attempts to get everything handled, so if you have a spare HDD, now is the time to use it.  Be ready to try again and again.  The good news is that a fresh install is only 20 minutes. Putting most settings, data and user HOME's back is another 15 minutes. If there is any huge data areas - this is an NFS server - hopefully those are on storage that isn't tied to the OS storage. At least in different partitions.  There's a reason all the gurus say to split the OS from the HOMES from the data.  This is the time where what pays off immensely.  If it isn't split up already, NOW is the time to correct that.  35G for the OS. That should be overkill and easily last 5 yrs.

---

