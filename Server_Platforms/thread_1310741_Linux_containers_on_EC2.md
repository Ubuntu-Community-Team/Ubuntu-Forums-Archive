---
title: "Linux containers on EC2?"
date: 2009-11-02
forum: Server Platforms
---

### Post by mateiz on 2009-11-02
Hi,

I'm getting errors when I try to use Linux Containers (lxc) on the new Karmic EC2 images from Canonical. A typical session looks like this:

```
root@domU-12-31-39-09-E1-A2:~# lxc-create -n foo
root@domU-12-31-39-09-E1-A2:~# mkdir /cgroup
root@domU-12-31-39-09-E1-A2:~# mount -t cgroup cgroup /cgroup
root@domU-12-31-39-09-E1-A2:~# lxc-execute -n foo /bin/echo hello
lxc-execute: failed to clone(0x2c020000): Invalid argument
lxc-execute: Invalid argument - failed to fork into a new namespace
lxc-execute: failed to spawn '/usr/lib/lxc/lxc-init'
```

(Note that before running this stuff, I did apt-get update and apt-get install lxc to install the LXC userspace tools.)

The same set of commands works on Ubuntu Server on my laptop. The commands fail on EC2 in both 32-bit and 64-bit instances.

Is this happening because the EC2 kernel is configured with slightly different options than the server one? If so, will new kernels be available in the future? EC2 doesn't allow users to build their own kernel, so I need to wait for Canonical to release one.

Thanks for your help - I was very excited to see LXC in Ubuntu 9.10, and I hope to be able to use it on EC2.

---

