---
title: "Disallow users mounting NTFS volumes?"
date: 2010-11-13
forum: Security
---

### Post by gewone on 2010-11-13
Hi!

Easy one, probably. Just me not having the best expertise in fstab. Like this, say I have a system, I want only my sudoer account to show and automount NTFS partitions under 'Places' in Ubuntu. Simply, they shall not have access to mount it. Only my main sudoer user account shall take advantage on this show-and-possibly-automount feature of GNOME, but not anyone else. Do you guys follow? What's my best approach here?

[I]Ty in adv~
Regards~[/I]

---

### Post by Morbius1 on 2010-11-13
Well, you could create a line in fstab that looks something like this:

Let's assume the NTFS partition you want to mount is the Windows "C Disk":

```
/dev/sda1 /media/WinC ntfs defaults,uid=1000,umask=077 0 0
```The uid=1000 will make you the owner
The umask=077 will allow only the owner to access the mountpoint ( the "0" part ) and everyone else will have no access ( the "7" part ).

If you've never done anything like this before:

(1) Make a permanent home for the partiton to live in, for example:
```
sudo mkdir /media/WinC
```(2) FInd out how your system sees the partition, just to make sure it's really at /dev/sda1:
```
sudo blkid -c /dev/null
```You'll get an output that looks something like this:
> /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs"(3) Then add the line to /etc/fstab I used above as an example:
```
/dev/sda1 /media/WinC ntfs defaults,uid=1000,umask=077 0 0
```(4) Save fstab then run the following command to check for errors and add the new partition:
```
sudo mount -a
```

---

### Post by gewone on 2010-11-14
Thanks. Besides.
Now after further investigation, it seems only first Ubuntu user (1000) gets to mount system's NTFS volumes anyways. So, no issue really! :D

---

### Post by cariboo on 2010-11-14
If you give other users admin privileges, they can also mount the NTFS partition.

---

### Post by sisco311 on 2010-11-14
> **cariboo907 said:**
> If you give other users admin privileges, they can also mount the NTFS partition.

Yep, by default admin users are allowed to mount NTFS partitions without a password. 

One could write a polkit rule to allow other users or groups to mount the partitions with or without a password, but I think the OP prefers the default settings.

---

### Post by chatter on 2010-11-22
What happened here. I gave the following command:

gksudo blkid -d /dev/null


option "-c" did not work so upon reading the manual I figured it would be "-d" and this is what came up on the terminal

No ask_pass set, using default!
xauth: /tmp/libgksu-b6rkk6/.Xauthority
STARTUP_ID: gksudo/blkid '|dev|null'/7957-0-AzeemU_TIME26073215
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: blkid
cmd[9]: /dev/null
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
xauth: /tmp/libgksu-b6rkk6/.Xauthority
xauth_env: /var/run/gdm/auth-for-azeem-3iQnDp/database
dir: /tmp/libgksu-b6rkk6



I am using Ubuntu 9.10. Any idea what just happened here. I just wanted to do as suggested by morbius1 in the 2nd post here:

> FInd out how your system sees the partition, just to make sure it's really at /dev/sda1:
     Code:
     sudo blkid -c /dev/null 
You'll get an output that looks something like this:
     Quote:
                                                 /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs"                      

---

### Post by sisco311 on 2010-11-22
> **chatter said:**
> What happened here. I gave the following command:

gksudo blkid -d /dev/null




Welcome to the forums!

blkid is CLI application, so you should use sudo instead of gksudo:
```
sudo blkid -c /dev/null
```

---

