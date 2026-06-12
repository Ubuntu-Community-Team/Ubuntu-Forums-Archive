---
title: "chroot from older GNU/Linux"
date: 2023-05-01
forum: Virtualisation
---

### Post by dchmelik on 2023-05-01
Lately I installed a couple Ubuntu variants on my PC because I administer them for users.  Personally I've always used the oldest GNU/Linux, so I want to chroot in.  When I do so, it says the following.

```
[FONT=monospace]groups: cannot find name for group ID 17
groups: cannot find name for group ID 215[/FONT]
```

I didn't see those in /etc/group, so what does this mean?  Other than this, the chroot seems to work well, including updates, apt, etc.  Do the error messages mean anything else needs to be configured for things to work right?  Of course, the OS I chroot from doesn't have systemd.

---

### Post by TheFu on 2023-05-01
TL;DR - don't worry about it unless those groups are needed inside the chroot environment.

More: 
Different installations have installed different packages.  Some of those installation processes create users and groups.  If the passwd and group files aren't consistent inside the chroot, then you'll see errors like that.  Did you copy over the passwd/group/shadow/gshadow files into the chroot (or include the /etc/) into it?  That would be the first place I looked.

chroot has a place (fixing boot issues), but for the last decade, most people use linux containers instead because they have more capabilities, more tools that make it easier to use, and provide more security thanks to cgroups and namespaces ... added to what chroot provides. I'm oversimplifying.

---

### Post by dchmelik on 2023-05-01
Thanks.

---

