---
title: "alternative backports mirror?"
date: 2006-01-25
forum: Ubuntu Backports
---

### Post by tyrus on 2006-01-25
Hi. I just moved from Libranet/straight Debian, and thought I'd give Ubuntu a try. Backports seems the place I gotta be to get the software I need, but after adding the servers to my repos list I get 404 and 111 errors everytime I try an apt-get update. I presume this is because of server overload (or perhaps they're down??) - in either case, is there a list of alternative mirrors somewhere???

Thanks!

Ty

---

### Post by tntc1978 on 2006-01-26
I get these errors when I try updating, seems related, but I have no clue as to why I get them!

[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz:) 404 Not Found

---

### Post by vaskark on 2006-01-26
Me too :(

---

### Post by ajgreeny on 2006-01-26
And me.  It started yesterday 25th Jan, before that all was well.  Have the servers gone down or are these backports no longer in existence?

---

### Post by hod139 on 2006-01-26
Down for me too.  Anyone know what's going on?

---

### Post by manicka on 2006-01-26
Try these 

#backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by hod139 on 2006-01-26
I should be more clear.  The backports still work:
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
```
but the breezy-extras
```
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted
```
do not work.  Are the breezy-extras gone or is the mirror just down for a while?

---

### Post by ice60 on 2006-01-26
[QUOTE=manicka]Try these 

#backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse[/QUOTE]
hi, i just realised that it was those which have been giving me alot of errors they work without the de. though like this [http://archive](http://archive)... why do some people get errors and not others when they use de. :confused:

my apt-get says it can't connect to the backports extras too :( i searched for backports extras and all the ones i found have the mirrormax.net address

---

### Post by davebgimp on 2006-01-26
It's looking like as of this time, all the repositories on mirrormax that are listed my sources list are down.

```
http://ubuntu-backports.mirrormax.net/dists/breezy-extras/Release.gpg: Temporary failure resolving 'ubuntu-backports.mirrormax.net'

W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```

---

### Post by davebgimp on 2006-01-26
Here we go...no more Mirrormax:
[http://www.ubuntuforums.org/showthread.php?t=121734](http://www.ubuntuforums.org/showthread.php?t=121734)

---

### Post by tyrus on 2006-01-27
The solution proposed in the above thread doesn't solve the issue of a missing mirror for extras. So, we still don't have a mirror for the extras archives.

wtf?

---

### Post by pulp on 2006-01-27
[http://ubuntuforums.org/showpost.php?p=548673&postcount=3](http://ubuntuforums.org/showpost.php?p=548673&postcount=3)

---

