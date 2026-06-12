---
title: "Recovering permissions - unable to ssh, sudo"
date: 2007-12-11
forum: Server Platforms
---

### Post by JeremyLaurenson on 2007-12-11
Hi all,

I messed up my stsrem by being in the wrong directory when i did a chmod -R 777 *

Thought I was in /data but I was in /

As a result, I am unable to sudo (wrong perms on that file), unable to chmod sudo and unable to ssh into the system.

In addition, I am not sure I can find the info to 'fix' all the issues I may have just caused.

How can I reset the permissions I need to get my system healthy?

TIA
J

---

### Post by jingo811 on 2007-12-11
Sorry don't have any practical solutions for you.  But this is a tip for the future in case you're trying to do the same thing again.
```
$ pwd
```
Print Working Directory.

---

### Post by JeremyLaurenson on 2007-12-11
Oh yes, no doubt a hefty amount of stupidity was involved.

---

### Post by jingo811 on 2007-12-11
I'm no server expert but I'm thinking that you need to chmod all sub-sub-sub-directories back to what they were manually.  Which will be like headache.

---

### Post by JeremyLaurenson on 2007-12-11
The issue is that because of the all-access security I am locked out (as a security feature) from most of the system. I can no longer sudo to root, so I essentially cant change anything - by the looks of it.

---

### Post by craigp84 on 2007-12-11
Hi,

All should not be lost here! - The fix is time consuming as you can probably imagine. First things last and all that... to get root access -

Try booting to single user (recovery mode) then for quickness, set a root password - you can lock the account later.

Do a "reboot" and come up into multi user as normal.

If this fails, you're looking at booting off the ubuntu install cd, mounting the partitions from disk and resetting the perms on that sudoers file.

Anyways, once you can get the root access back through one of the above approaches (you will!), you need to reset all the other perms to default. I think the fastest way to do this is issuing (as root) - 

```
dpkg-reconfigure --all
```

This will take a long time, and ask you a lot of questions. If you're unsure, go with the defaults. I'd encourage you not to tweak too much. You can always change your mind later - just take a note of the package name you weren't sure about and you can dpkg-reconfigure <package-name> later.



Hope this helps,

-c

---

### Post by linuxisfree on 2007-12-11
> **JeremyLaurenson said:**
> Oh yes, no doubt a hefty amount of stupidity was involved.

Don't be too hard on yourself... That IS, after all, how we must learn (SOMETIMES):)

---

### Post by HermanAB on 2007-12-11
Hmm, the only way to fix a mess like that is to re-install.  Don't worry, you'll nevevr make that mistake again.  Guess how I know...
;)

Cheers,

H.

---

### Post by JeremyLaurenson on 2007-12-11
An issue I am having is that the root account can not log in. I have set the password, but when typing   root    as the username, I get the Incorrect login  message... How do I reenable this?

---

### Post by g2g591 on 2007-12-11
just do it in recovery mode, (if i remember from last night when i pretty much got hosed when i tried to upgrade to hardy and fix errors, the /etc/sudoers should be 440)

---

### Post by JeremyLaurenson on 2007-12-11
Heres the schtick to get sudo back runing:
 1... Boot into  recovery mode.
 2... cd /usr/bin
 3... chmod 4111 sudo    (perms on sudo were reset in the initial chmod)
 4... chmod 0440 /etc/sudoers    (perms on sudo were reset in the initial chmod)

---

### Post by JeremyLaurenson on 2007-12-31
Hey, a clean install did the trick ;-)

---

