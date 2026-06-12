---
title: "LXC - Ubuntu Guest Dist Upgrade Fails - Help"
date: 2015-11-16
forum: Virtualisation
---

### Post by redger on 2015-11-16
I have a Ubuntu 14.04LTS host running a variety of LXC containers. These are all unprivileged containers, created following Stephane Grabers instructions [https://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/]("https://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/")

I originally created Utopic and Trusty containers. Now Utopic is eol I want to upgrade these LXC guests

the dist-upgrade seems to work ... BUT  when the container subsequently starts there are a host of issues which prevent it from starting
```
lxc_container: conf.c: mk_devtmpfs: 1320 Permission denied - Unable to create /dev/.lxc for autodev
lxc_container: utils.c: safe_mount: 1434 No such file or directory - Mount of '/sys/firmware/efi/efivars' onto '/usr/lib/x86_64-linux-gnu/lxc/sys/firmware/efi/efivars' failed
Failed to insert module 'autofs4'
Failed to mount cgroup at /sys/fs/cgroup/systemd: Permission denied
systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
Detected virtualization lxc.
Detected architecture x86-64.

Welcome to Ubuntu 15.04!

Set hostname to <utopic_browse_normal_backup_151115>.
/etc/mtab is not a symlink or not pointing to /proc/self/mounts. This is not supported anymore. Please make sure to replace this file by a symlink to avoid incorrect or misleading mount(8) output.
Failed to install release agent, ignoring: No such file or directory
Failed to create root cgroup hierarchy: No such file or directory
Failed to allocate manager object: No such file or directory
[!!!!!!] Failed to allocate manager object, freezing.
```

I've tried a few different approaches, including
[http://ubuntuforums.org/showthread.php?t=1863056]("http://ubuntuforums.org/showthread.php?t=1863056")
and just resolving the problems one by one (mostly creating directories and links as required). The best I've been able to do is to bring the container to the point where it boots, but doesn't initialise the network correctly, for which i need to execute the following steps manually
```
# ------ Correct for  network error arising from upgrade Utopic to Vivid
mkdir /run/network
mkdir /run/resolvconf
mkdir /run/resolvconf/interface

ifup eth0
# ----------- End --------- #
```

does anyone have advice on how to successfully upgrade the distribution version for an LXC guest ?

---

