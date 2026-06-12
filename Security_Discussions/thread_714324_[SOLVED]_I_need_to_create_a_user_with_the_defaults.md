---
title: "[SOLVED] I need to create a user with the defaults permissions that came with ubuntu"
date: 2008-03-03
forum: Security Discussions
---

### Post by Derviansoul on 2008-03-03
Hello

Recently when i installed the ati drivers when i restarted i couldn't use my user e17 wouldn't let me use it, i created a new user then my i didn't had any permissions sudo didn't work and i couldn't install anything!!
I had to login and enable the root account, that i'm using now!! can anyone tell how do i create a user that had all the same groups and permissions that the default user that comes with ubuntu has? so i can put the root account off again!
i'm using e17 and i haven't got any gnome or kde installed so i will have to do everything in the command line!!
If anyone could tell which groups the defaults user belongs to, would be great!!

---

### Post by kaens on 2008-03-03
The default user belongs to the same groups as the root user during a recovery boot, minus the "root" group.

Those should be (I think):
```

adm uucp dialout cdrom floppy audio dip video plugdev scanner fuse lpadmin admin netdev powerdev

```

You should be able to do:
```

usermod -a -G adm,uucp,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,fuse,lpadmin,admin,netdev,powerdev USERNAME
```

where USERNAME is the user you need to add the groups to.

---

### Post by Derviansoul on 2008-03-04
solved thanks!!

---

