---
title: "rootkit scan results"
date: 2007-11-07
forum: Server Platforms
---

### Post by darkeale on 2007-11-07
hi ive just ran chkrootkit and this has appeared in the results

Checking `lkm'... You have 1 process hidden for readdir command
You have 1 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

and after running rkhunter this warning came up

Performing file properties checks

/usr/bin/ldd [ Warning ]



is this anything to worry about?

thanks, alex

---

### Post by pedja_portugalac on 2007-11-07
I think there is nothing to worry about cause this script came as official update for glibc. We were talking about this event yesterday on this forum so you can see lil bit. Name of the theme was something like ldd (GNU libc) 2.6.1

---

### Post by gerrymoth on 2007-11-20
I'm getting the following when running rkhunter, but didn't have this last week?

> [19:56:56] /usr/bin/ldd                                      [ Warning ]
[19:56:56] Warning: The file properties have changed:
[19:56:56]          File: /usr/bin/ldd
[19:56:56]          Current inode: 460403    Stored inode: 459431
[19:56:56]          Current file modification time: 1193274171
[19:56:56]          Stored file modification time : 1191200505
[19:56:56] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.

---

### Post by netlogic on 2007-11-21
rkhunter tends to go off on an alarm over stupid things. you should try chkrootkit. 
rkhunter works good on certain distros, but on ubuntu, there are many false alarms.

---

### Post by whoboo on 2007-11-22
I got this identical result regarding LKM Trojan.
Is it real or not ?
I can't find any previous discussion of this.

---

