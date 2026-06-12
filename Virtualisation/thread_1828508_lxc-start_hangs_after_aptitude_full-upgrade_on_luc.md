---
title: "lxc-start hangs after aptitude full-upgrade on lucid guest"
date: 2011-08-19
forum: Virtualisation
---

### Post by bj0 on 2011-08-19
I just setup an LXC container using the lucid template, and it runs fine.

If I modify the /etc/apt/sources.list to include security updates:
```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main universe multiverse

```
then do an aptitude update && aptitude full-upgrade, it downloads and installs updates.  When I stop and re-start the container, however, the lxc-start command just hangs with no output.

Can the guest not be updated?  What about security bugs?

B

---

