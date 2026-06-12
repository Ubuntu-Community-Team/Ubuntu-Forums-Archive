---
title: "lxc-start: No such file or directory - failed to exec /sbin/init"
date: 2012-10-27
forum: Virtualisation
---

### Post by KenSharp on 2012-10-27
I cannot figure out what is wrong with this, and I have to give up and ask for help.

I have (**tried** to) setup a linux container with network access where I wish to install a windows executable under Wine. Unfortunately I can't even get it to init.

```
lxc.utsname = gomez-5
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = lxcbr0
lxc.network.ipv4 = 10.0.3.5/24
lxc.rootfs = /var/lib/lxc/gomez-5/rootfs
lxc.mount.entry = proc  /var/lib/lxc/gomez-5/rootfs/proc        proc    nodev,nosuid,noexec     0       0
lxc.mount.entry = /sbin /var/lib/lxc/gomez-5/rootfs/sbin        none    ro,bind                 0       0
lxc.tty = 1
```I have created the relevant proc and sbin directories in $ROOTFS but

> lxc-start -n gomez-5 -o /tmp/log -l DEBUG
lxc-start: No such file or directory - failed to exec /sbin/init
lxc-start: invalid sequence number 1. expected 2
lxc-start: failed to spawn 'gomez-5I cannot figure out why it cannot see /sbin/init, given that the bind mount is successful according to the log.

Can someone PLEASE help me here? I've wasted hours on what should be an extremely easy container to set up. I've Googled everywhere but the only articles I find suggest I am doing everything correctly.

Bind mounts work fine with chroot but I would prefer to avoid a totally separate file system if possible.

TIA

---

