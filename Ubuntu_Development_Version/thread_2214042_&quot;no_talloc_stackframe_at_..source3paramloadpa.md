---
title: "&quot;no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory&quot;"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by sanderj on 2014-03-30
Trusty Tahr, fully updated (2014-03-30)

With any sudo-command where the su password is needed (so: in a new terminal tab or after x minutes), I get:

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
```

When I Google that, there is one set of bug reports, related to Samba. :confused:

Tips?

Examples:

```
sander@flappie:~$ sudo whoami
[sudo] password for sander: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
root
sander@flappie:~$
```

```
sander@flappie:~$ sudo uptime
[sudo] password for sander: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
 10:34:44 up 46 min,  6 users,  load average: 0,24, 0,52, 0,39
sander@flappie:~$
```

```
sander@flappie:~$ sudo ls bl*
[sudo] password for sander: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
blabla	blablabla.planner  blabla.c  blabla.c~	blabla.par
sander@flappie:~$
```

---

### Post by bapoumba on 2014-03-30
```
bapoumba_lxde@SonyBlue:~$ whoami
bapoumba_lxde
bapoumba_lxde@SonyBlue:~$ sudo whoami
[sudo] password for bapoumba_lxde: 
root
bapoumba_lxde@SonyBlue:~$ apt-cache policy samba
samba:
  Installed: (none)
  Candidate: 2:4.1.3+dfsg-2ubuntu4
  Version table:
     2:4.1.3+dfsg-2ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

```
Do you have samba installed ?

---

### Post by sanderj on 2014-03-30
Yes, I have Samba installed and running.

```
sander@flappie:~$ apt-cache policy samba
samba:
  Installed: 2:4.1.3+dfsg-2ubuntu4
  Candidate: 2:4.1.3+dfsg-2ubuntu4
  Version table:
 *** 2:4.1.3+dfsg-2ubuntu4 0
        500 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
sander@flappie:~$
```

So it is samba related? :(

---

### Post by bapoumba on 2014-03-30
Looks like..
I have removed a duplicate post of the one just above mine.
I did get to the same bug reports you found, but did not find a workaround or a fix in any of them. I'll have a closer look.

---

### Post by deadflowr on 2014-03-30
> **bapoumba said:**
> Looks like..
I have removed a duplicate post of the one just above mine.

I wondered why my posting was blocked, timing, huh?
(I seeming posted at the same time as the mod action)

That said, my post was asking if this was a fresh install or an upgrade from saucy?
I had this problem from an upgrade, and seemed to have marked that bug as affecting me.
(I don't remember doing so, and thought it was for sudo)
Don't know if it fixed, since that install is gone now.

Haven't seen it with a fresh install, though.

---

### Post by bapoumba on 2014-03-30
> **deadflowr said:**
> I wondered why my posting was blocked, timing, huh?
(I seeming posted at the same time as the mod action)


Sometimes pages take a long time to load. If you open the same thread in another tab, you may see your post has already gone through..

---

### Post by sanderj on 2014-03-30
I removed samba & smbclient, did a reboot, but the error message is still there.

Based on [https://bugzilla.samba.org/show_bug.cgi?id=10420](https://bugzilla.samba.org/show_bug.cgi?id=10420), I removed "pam_smbpass.so" from /etc/pam.d/common-password, did a reboot, but the error message is still there.

FWIW: my 14.04 is an upgraded 13.10.

EDIT: I also removed samba-common-bin and smbc, but still get the same error message with sudo. So I would say samba is now not installed anymore, but I still get the error message.

---

### Post by sanderj on 2014-03-30
Ah, seems to be gone after 

```
sudo apt-get remove libpam-smbpass

```

Based on [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186) (and it's dupe [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680))

EDIT: 

FYI: "the libpam-smbpass package will sync system users and passwords with the Samba user database."

---

### Post by icephreaq on 2014-04-20
> **sanderj said:**
> Ah, seems to be gone after 

```
sudo apt-get remove libpam-smbpass

```

Based on [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186) (and it's dupe [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1274680))

EDIT: 

FYI: "the libpam-smbpass package will sync system users and passwords with the Samba user database."

You can also fix this issue while keeping libpam-smbpass installed by running [COLOR=#333333][FONT=Ubuntu Mono]"pam-auth-update" and remove "SMB password synchronization".  Got that solution from [/FONT][/COLOR][Thomas (reusch)]("https://launchpad.net/~reusch") on [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186)

---

