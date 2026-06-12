---
title: "Ubuntu for a classroom lab"
date: 2019-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by sporanox2 on 2019-07-15
I wish to migrate one of my classrooms from Windows to Linux.  Right now the windows computers are running deep freeze so that when they reboot they are back to a fresh image and any changes made by students are gone.  Is there any thing comparable to Deep Freeze or settings that can achieve this goal in Linux?

---

### Post by wildmanne39 on 2019-07-15
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by #&amp;thj^% on 2019-07-15
By default Ubuntu and most other Unices deny regular users (students, guests) write access to system files. Only an administrator with the proper authorisation (username and key) can install software, change system settings, or delete partitions.

Regular users can, by default, only write in their home directory and the system's temporary directory. A common way to handle one-time guest sessions is to put their home directory inside the temp directory, and the temp directory in main memory.
I understand that might not be enough so, "fsprotect" is a set of scripts that protect existing filesystems. fsprotect is excellent for public computers like those in libraries, internet cafés, etc.

Using aufs they pack a tmpfs filesystem forcing changes to be written to the tmpfs filesystem.

The root filesystem is protected by an initramfs script. Other filesystems are protected by an init script. All protected filesystems become read-only ensuring their immutability even on power-offs.

To install fsprotect in all currently supported versions of Ubuntu open the terminal and type:
```

sudo apt install fsprotect
```

**The benefits of using fsprotect are:**
[list]
    [*]Filesystems are protected and no change is ever written to the disk.
    [*]Protected filesystems are mounted read-only. This means that they aren't damaged when the computer is turned off improperly.
    [*]It is very easy to use.
    [*]In some cases it makes the filesystem access faster.

[B]The drawbacks of using fsprotect are:
[/B]
    [*]Filesystem changes cannot be more than a predefined limit in bytes (set by you).
    [*]Since tmpfs is heavily used, you need to have adequate swap space.[/list]
That's about all I can tell you about it.

---

### Post by mastablasta on 2019-07-16
deep freeze = kiosk mode - there should be some options for that. 
for example:
[https://tutorials.ubuntu.com/tutorial/secure-ubuntu-kiosk](https://tutorials.ubuntu.com/tutorial/secure-ubuntu-kiosk)
[https://www.omgubuntu.co.uk/2014/07/create-ubuntu-kiosk](https://www.omgubuntu.co.uk/2014/07/create-ubuntu-kiosk)

---

### Post by TheFu on 2019-07-16
I've never used fsprotect, but I have setup classroom accounts on Unix servers.  We tended NOT to do this for individual desktops, since our students provided their own and in most corporate environments, they would be working on servers inside data centers in a different building or halfway around the world.  Connections to the servers would be via ssh and the accounts would be used by multiple classes, so we would delete them the day after the finals finished for the semester, not at each logoff.  We did setup quotas to prevent too much storage abuse which forced students to maintain a clean account. 

Unless the students are specifically learning Unix administration, they do not need admin rights.  Don't give them admin or sudo and it would be best not to allow physical access, since with a USB flash drive and physical access, they can completely pwn any Linux system.

If you want to just start fresh with a new account at every boot, you could script adding and removing userids as needed with a script.  Just have the delete-user script also remove the HOME directory.  You could have this script run every hour or once a day or at whatever time/interval you need.  It can be selective on the userids handled or just wipe all created in a specific name-pattern or using a specific HOME directory mount.  adduser (or is it useradd?) can create users with HOME directories. deluser (or is it userdel?) will delete users and their HOME directories.  If you need/want specific files to be pre-created in each user's HOME, then useradd (or is it adduser?) has the ability to use a skeleton to copy.

For any Unix admin, using the useradd/userdel + skeleton methods would be fairly easy and less than an hour of effort.  Think it would be more like 10 minutes if they were already familiar. Nothing extra needed.

I would block any mounting of storage on the systems and  still have quotas setup.

---

### Post by C.S.Cameron on 2019-07-16
You can add a Guest User using lightdm.
It will reset after every use but can be modified by the admin.
See:
[https://askubuntu.com/questions/1120448/disable-persistence-on-hdd-install-public-pc/1120537#1120537](https://askubuntu.com/questions/1120448/disable-persistence-on-hdd-install-public-pc/1120537#1120537)

---

### Post by cruzer001 on 2019-07-16
Simple and effective; +1 C.S.Cameron

---

### Post by SeijiSensei on 2019-07-16
Another option is to have "dumb" terminals and shared servers. Take a look at the [Linux Terminal Server Project]("http://ltsp.org/").

---

