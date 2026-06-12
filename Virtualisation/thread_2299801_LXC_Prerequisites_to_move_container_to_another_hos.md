---
title: "LXC: Prerequisites to move container to another host"
date: 2015-10-21
forum: Virtualisation
---

### Post by bob151 on 2015-10-21
Hi LXC experts!

I have to move an Ubuntu container from its current Gentoo LXC host to a new CentOS LXC host.

Apart from resource questions (enough disk space, RAM, CPU, etc.), what are the prerequisites for this task, regarding the environment?
E.g.:
- Do the kernels have to be exactly the same?
- Does the LXC version has to be exactly the same?
- More things to consider...

In my case the specs of the participating machines are the following:

*Current LXC host:*

  ```
Gentoo: Linux 3.7.10-gentoo #1 SMP x86_64
```
  *New LXC host:*
  ```
CentOS 6.7: Linux 2.6.32-573.el6.x86_64 #1 SMP x86_64
```
  *Container, which has to be moved:*
  ```
root@computername:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
root@computername:~# uname -a
Linux computername.domain.tld 3.7.10-gentoo #1 SMP x86_64 GNU/Linux
```

Will that work?

Thanks in advance!

Kindest Regards,
Bob

---

