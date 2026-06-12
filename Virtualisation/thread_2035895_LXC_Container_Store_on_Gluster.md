---
title: "LXC Container Store on Gluster"
date: 2012-07-31
forum: Virtualisation
---

### Post by joeyea3231 on 2012-07-31
Has anyone had any luck storing LXC rootfs directories on Gluster storage?  I have no issues starting a container if the rootfs directory resides on local storage.  When trying to start it when rootfs is on shared storage, it halts just before bringing up the console.  Here are the last few lines of the debug log:
```
      lxc-start 1343764349.171 DEBUG    lxc_conf - capabilities has been setup
      lxc-start 1343764349.171 NOTICE   lxc_conf - 'test1' is setup.
      lxc-start 1343764349.171 INFO     lxc_start - changed apparmor profile to lxc-container-default
      lxc-start 1343764349.171 NOTICE   lxc_start - exec'ing '/sbin/init'
      lxc-start 1343764349.182 NOTICE   lxc_start - '/sbin/init' started with pid '1971'
      lxc-start 1343764349.183 WARN     lxc_start - invalid pid for SIGCHLD
```Thinking it may be network configuration related, I've tried both bridging and macvlans but neither work.  Any ideas?

---

### Post by meepmeep on 2012-09-22
Hi joeyea3231

I just upgrade from 11.10 to 12.04, and, even if i'm not using glusterFS, I get the same message :

```
lxc_start - invalid pid for SIGCHLD

```
Did you find how to correct this ?

---

