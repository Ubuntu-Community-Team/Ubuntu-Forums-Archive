---
title: "file permission problem"
date: 2009-12-05
forum: System76 Support
---

### Post by GradaL on 2009-12-05
Hi,

I am using 9.10. I changed the file permission of all filesystem to 755 and ownership to root for some stupid reason. The code was


sudo chown -R root /
sudo chmod -R 755 /


I didn't backup, and now, i need to reset the file permissions. Is there any short way to do this exept to fix all file one by one?

Thanks..

---

### Post by drewbenn on 2009-12-05
Well there's no automagic "undo" function, unfortunately.  At least for your home directory, you could do
```
sudo chown -R `whoami` ~
```
to make yourself the owner of all the files in your home directory.  As far as the rest of your filesystem, though... it might be easiest to back up all your files and do a fresh install of 9.10, to ensure things will work correctly (including from a security perspective).

---

### Post by jdb on 2009-12-05
> **GradaL said:**
> Hi,

I am using 9.10. I changed the file permission of all filesystem to 755 and ownership to root for some stupid reason. The code was


sudo chown -R root /
sudo chmod -R 755 /


I didn't backup, and now, i need to reset the file permissions. Is there any short way to do this exept to fix all file one by one?

Thanks..

There are a lot of things that won't work at all if they're not root so
be careful changing permissions outside of your home directory.
I think your home directory has to be 755 & owned by you for Ubuntu to let you log in.
If you change any files with a suid bit the suid bit will disappear.
There are only a few system files that have that, but a some important things won't work if those files don't have the suid bit set, ie. 4755 for owner suid bit.
Restoring might be the best fix.

BTW, to change the group at the same time as you change the owner
put a colon after the new owner like this

chown some_user: some_file

jdb

---

### Post by jdmelton on 2009-12-05
Ouch, this is going to hurt.

First, chown -R root will only change the user, not the group.
So, in /etc, you do not affect anything that I am aware of.
Ditto for /boot, /bin, /dev, /lib, /media, /mnt,... etcetera.
The major directories affected will be /home (yours and any other users) and /var.
The /var/log has several users.
It may be that logrotate will cure this for you, over time.
If your username is bob, then sudo chown -R bob /home/bob will fix the owner.

Second, the chmod -R 0755 will be harder to correct.
Most directories have 0755 anyway, but a lot of files should not have execute permissions.
The files in /lib normally have 0644 permissions.
Run find /lib -type f -exec chown 0644 {} \; as root to change the file permissions and not touch the directories.
You can test first with find /lib -type f
Note that /bin, /sbin, /usr/bin, and /usr/sbin already have 0755 file permissions.

Perhaps you can check another Ubuntu computer's permissions...

I have to agree with jdb. You are probably better off restoring or reinstalling.

---

### Post by Lee_Machine on 2009-12-06
I too have mistakenly done this in the past. Most recently I had  /home permission problems. So bad I couldn't graphically login 

Lucky this was on a test system that I was trying to harden to quite the extremes. 

As stated the best solution is a clean install.

---

