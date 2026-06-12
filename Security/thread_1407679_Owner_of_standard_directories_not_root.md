---
title: "Owner of standard directories not root??"
date: 2010-02-15
forum: Security
---

### Post by cornware-cjp on 2010-02-15
I noticed that when I do "ls -l /", most directories are owned by my standard user account, and *not* by the root account. This seems to be unsafe to me, **so my question is:** is it supposed to be this way, or is something wrong with my system?

The history of my system: I recently upgraded from Ubuntu 9.04 to 9.10. I've upgraded the system before; the original install was probably Ubuntu 8.04.

Anyway, I thought it would be smart to manually chown those things to root. I tried to be careful not to change any entry that is not supposed to be owned by root, but apparently I still changed a bit too much. I now have the following problems:
[LIST]
[*]sudo complains it needs to be setuid root, and refuses to work. That sounds reasonable, but I can not remember changing any permission bits.
[*]The GNOME terminal refuses to start. Konsole still works though, and logging in on the text mode terminals also works.
[/LIST]
I'm thinking about using a live CD to repair all the damage I've done. Any idea what could be wrong with the GNOME terminal program?

---

### Post by The Cog on 2010-02-15
Here is mine, which I believe to be normal:
```
drwxr-xr-x   2 root root  4096 2010-01-29 19:01 bin
drwxr-xr-x   3 root root  4096 2010-02-06 14:30 boot
lrwxrwxrwx   1 root root    11 2009-11-06 22:35 cdrom -> media/cdrom
drwxr-xr-x  15 root root  4000 2010-02-15 18:31 dev
drwxr-xr-x 143 root root 81920 2010-02-15 18:54 etc
drwxr-xr-x   5 root root  4096 2009-11-01 15:53 home
lrwxrwxrwx   1 root root    37 2010-02-06 14:30 initrd.img -> boot/initrd.img-2.6.31-19-generic-pae
lrwxrwxrwx   1 root root    37 2010-01-08 18:59 initrd.img.old -> boot/initrd.img-2.6.31-17-generic-pae
drwxr-xr-x  18 root root  4096 2010-01-29 19:01 lib
drwxr-xr-x   4 root root  4096 2010-02-08 20:40 media
drwxr-xr-x   4 root root    32 2010-01-30 18:42 mnt
drwxr-xr-x   9 root root  4096 2010-02-06 20:04 opt
dr-xr-xr-x 151 root root     0 2010-02-15 18:30 proc
drwx------  19 root root  4096 2010-02-10 23:52 root
drwxr-xr-x   2 root root  4096 2010-01-29 19:01 sbin
drwxr-xr-x   2 root root     1 2009-10-20 00:05 selinux
drwxr-xr-x   3 root root     8 2009-11-29 17:24 srv
drwxr-xr-x  12 root root     0 2010-02-15 18:30 sys
drwxrwxrwt  15 root root  4096 2010-02-15 19:44 tmp
drwxr-xr-x  12 root root    96 2009-11-07 00:22 usr
drwxr-xr-x  15 root root  4096 2009-10-28 21:02 var
lrwxrwxrwx   1 root root    34 2010-02-06 14:30 vmlinuz -> boot/vmlinuz-2.6.31-19-generic-pae
lrwxrwxrwx   1 root root    34 2010-01-08 18:59 vmlinuz.old -> boot/vmlinuz-2.6.31-17-generic-pae

```
So I suspect that something is amiss (and unsafe) with yours. I can't guess why it should be that way.

---

### Post by bodhi.zazen on 2010-02-15
> **cornware-cjp said:**
> I noticed that when I do "ls -l /", most directories are owned by my standard user account, and *not* by the root account. This seems to be unsafe to me, **so my question is:** is it supposed to be this way, or is something wrong with my system?

The history of my system: I recently upgraded from Ubuntu 9.04 to 9.10. I've upgraded the system before; the original install was probably Ubuntu 8.04.

Anyway, I thought it would be smart to manually chown those things to root. I tried to be careful not to change any entry that is not supposed to be owned by root, but apparently I still changed a bit too much. I now have the following problems:
[LIST]
[*]sudo complains it needs to be setuid root, and refuses to work. That sounds reasonable, but I can not remember changing any permission bits.
[*]The GNOME terminal refuses to start. Konsole still works though, and logging in on the text mode terminals also works.
[/LIST]
I'm thinking about using a live CD to repair all the damage I've done. Any idea what could be wrong with the GNOME terminal program?

My guess would be you typed 

chown -R you:you /

or that you changed your permissions accidentally.

Restoring all the ownership and permissions manually is difficult at best and often takes more time then backing up your data and performing a fresh install.

---

### Post by cornware-cjp on 2010-02-15
> **bodhi.zazen said:**
> 
chown -R you:you /

or that you changed your permissions accidentally.

Maybe, but I don't remember doing anything like that.

> **bodhi.zazen said:**
> 
Restoring all the ownership and permissions manually is difficult at best and often takes more time then backing up your data and performing a fresh install.

Is there really no easy way to do this? Can't the APT software check whether permissions are the same as they should be in a fresh install?

After my first first repair attempt (chmod -R root /bin /usr /etc .....), and a fix with a live CD, I now have a working system, gnome-terminal is working again and sudo is working again. Only gdm reports some errors about ICE-authority and something else. Something tells me there are more hidden errors under the hood.

I have another system with 9.10 installed (Xubuntu in that case). Is there a way to get a listing of all non-root files? Maybe ls -lR and then grepping for everything without 'root' in it?

---

### Post by cornware-cjp on 2010-02-15
I think I mostly repaired the damage. Based on my (working) laptop, I've restored most ownerships, and most SetUID permissions on my (broken) desktop PC.

Now gdm doesn't complain about ICEauthority anymore, the system is able again to reboot and sound started working again.

One final issue (hopefully): before logging in, gdm complains that /usr/lib/libgconf-2-4/gconf-sanity-check-2 returns error status 256. I ran it manually, but it returned no information. Then I found [this page]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215"), so I looked into .xsession-errors. Unfortunately, I can not find any useful information there. See attachment.

---

### Post by The Cog on 2010-02-15
I wouldn't feel comfortable running on a system where the ownerships had been messed up like that. You never know what wrinkles are left. Even if you don't reinstall before then, I would advise a clean re-install when you come to upgrade to Lucid.

---

### Post by cornware-cjp on 2010-02-15
I seem to have eliminated the gdm problem with "sudo dpkg-reconfigure gdm".

AFAICS, everything is up and running again. Any remaining issue is probably minor. Besides, they are mostly my own fault, and they are not security issues anymore. I won't disturb you with them anymore, at least not in this thread. :p With a bit of luck, any remaining errors will be eliminated sooner or later with updates or upgrades.

---

### Post by cornware-cjp on 2010-02-15
> **The Cog said:**
> I wouldn't feel comfortable running on a system where the ownerships had been messed up like that. You never know what wrinkles are left. Even if you don't reinstall before then, I would advise a clean re-install when you come to upgrade to Lucid.

In the current situation, I expect any remaining error to cause a lack of permissions, not to give too many permissions. So I expect it to be secure, but possibly not fully functioning.

I'll consider your clean install advise. I think I'll do that either when I run into another big problem, or on the next upgrade (whichever comes first).

---

