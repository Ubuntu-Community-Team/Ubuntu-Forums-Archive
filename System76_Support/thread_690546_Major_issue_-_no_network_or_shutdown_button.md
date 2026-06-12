---
title: "Major issue - no network or shutdown button"
date: 2008-02-07
forum: System76 Support
---

### Post by steveneddy on 2008-02-07
[This issue]("http://ubuntuforums.org/showthread.php?t=594941") my shutdown button locks the laptop up with only mouse movement.

The Network Manager won't connect to any network and I am using network-config to connect to the wireless.

I can't set a user to see if another user profile would work correctly.

Any help appreciated.

Gutsy 64 bit - System76 Serval Performance Type 1

Core 2 Duo

I may have caused this issue by installing the hibernate package then deleting it a couple of days later.

EDIT:

Also my USB flash drive won't auto mount.

I can't even see it unless I do a lsusb, but it still won't open.

---

### Post by thomasaaron on 2008-02-07
Try re-installing the hibernate package.

To set another user, boot into recovery mode and then do this:

adduser steveneddy
adduser steveneddy admin

The first will give you a new user and let you set the password, etc.
The second will give you admin privs.

Then try to boot into gnome using the second user.
If the new user works OK, then copy your important files over and delete the first user.

If the new user doesn't work either, you have a seriously hosed system, and the time required to
figure out all of those issues is greater than the time necessary to just re-install.

---

### Post by steveneddy on 2008-02-07
Thanks for the prompt reply.

I'm trying this now.

I'm gonna add a new user first.

---

### Post by steveneddy on 2008-02-07
No luck How can I get the usb flash drive to mount so i can copy data before I reinstall?

---

### Post by thomasaaron on 2008-02-07
Go into recovery mode.

[HTML]tail -f /var/log/syslog   #After this command insert USB drive. Look for it's designation. Should be something like /dev/sda  or /dev/sdb. Write it down.[/HTML]

```
cd /media/flashDrive
```

```
mount /media/flashDrive /dev/sda1  #or /dev/sdb1, depending on step 2
```

```
#Now copy your home directory (or individual files) to your flash drive
cp -R /home/stevenEddy /media/flashDrive
```

```
#Then unmount
umount /dev/dsa1  #or /dev/sdb1, depending on step 2
```

Email me for restore instructions. There are some specific ones you should use.

---

### Post by steveneddy on 2008-02-08
It's fixed.

I was looking through the /home/.bash_history to see what I may have done wrong.

I remember reading a post that said to alter a line in the /etc/init.d/rc file

si I looked at it, changed it back to the way it was, rebooted and I see the wonderful goodness of my Network Manager and the shutdown button works.

If you open the  /etc/init.d/rc file, I do not recommend changing the label

CONCURRENCY=none

to 

CONCURRENCY=shell

It totally messed up GTK and Gnome and I almost had to reinstall.

Glad I looked in .bash_history to see what I was fiddling around with last weekend.

[B][COLOR="Red"]Note to self:

Don't fiddle and change your only production machine![/COLOR][/B]

---

### Post by asmiller-ke6seh on 2008-02-08
> **steveneddy said:**
> [B][COLOR="Red"]Note to self:

Don't fiddle and change your only production machine![/COLOR][/B]

Or... back up your system right before making any major changes so that you can always restore to where you were right before the change.

Glad it's fixed...

---

### Post by steveneddy on 2008-02-08
> **asmiller-ke6seh said:**
> Or... back up your system right before making any major changes so that you can always restore to where you were right before the change.

Glad it's fixed...

Yeah - my next issue is to figure out how to back up, when and what....

:popcorn:

---

### Post by thomasaaron on 2008-02-08
Applications > Add/Remove Software

Search for:
Simple Backup Config
and
Simple Backup Restore

For most people, backing up just your home directory (/home/username) is enough.

---

### Post by steveneddy on 2008-02-08
I feel so stoopid.....

](*,)

---

