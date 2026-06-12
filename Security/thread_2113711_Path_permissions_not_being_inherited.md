---
title: "Path permissions not being inherited"
date: 2013-02-08
forum: Security
---

### Post by oygle on 2013-02-08
Have noticed a lot of paths with permissions of 775.

So, I went to a path that was 755, added a new sub path, and it was made permissions of 775.

There does not seem to be a permissions inheritance in place ??

---

### Post by schragge on 2013-02-08
The permissions normally don't get inherited from the parent (set-group-ID and set-user-ID being exceptions on directories). Look what the output of 'umask' is. That would define the default permissions for newly created files and directories.

---

### Post by oygle on 2013-02-08
Okay thanks, here is the output of umask ..

```

$ **umask**
0002

```

Does that look right ?

EDIT: It seems that the default permissions changed in 12.04, see [this post]("http://ubuntuforums.org/showpost.php?p=11880906&postcount=7")

How do I change the default permissions ?

---

### Post by oygle on 2013-02-09
Considering the informative post by "Morbius1" [here]("http://ubuntuforums.org/showpost.php?p=12181259&postcount=19"), a snippet ..

> 
_On Linux Filesystems_

At the moment of birth every file has permissions of 666 and every directory has permissions of 777. A system wide umask is created to modify these permissions immediately after birth and it's currently set at 002. So when you create a new file it's permissions are:

666
002 <-- minus the umask
==
664

And every new directory has permissions of:

777
002 <-- minus the umask
==
775


and the "umask" value I have is 0002.

Now it all makes sense, because my files are defaulting to 664, and paths are defaulting to 775

[This change]("http://www.mail-archive.com/ubuntu-devel-announce@lists.ubuntu.com/msg00628.html") was made in *Ubuntu some time ago.

How do I change the umask to a value of 0022 , so that I get ..

Files  644
Folders  755

Oygle

---

### Post by schragge on 2013-02-09
Well, if you want to change the default only for one user then put *umask 022* into *~/.bash_profile*, *~/.bashrc* or some other shell start-up file for that user.

For changing the system-wide default, put a short script that contains```
umask 022
``` into the directory */etc/profile.d*. Name it, say *umask.sh*. This way, it'll override the umask set either in */etc/profile* or in */etc/login.defs*, but won't interfere with other things in those files.

Sure, you're free to directly change the default setting in */etc/login.defs* instead, but I guess then this file won't get updated automatically with the rest of the system.

---

