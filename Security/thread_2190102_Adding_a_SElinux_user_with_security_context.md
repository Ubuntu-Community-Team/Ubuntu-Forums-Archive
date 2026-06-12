---
title: "Adding a SElinux user with security context"
date: 2013-11-25
forum: Security
---

### Post by almikul on 2013-11-25
Short description of what I am trying to do: I need to add security context to an existing user or add a new SElinux user in Ubuntu 12.04 LTS. Is it possible? 

On the remote network, I have "context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023" added to my user, but on my local Ubuntu, I have not. I am not even sure I fully understand how these SElinux permissions work, but I need to mount a SElinux partition on my local Ubuntu and have the same access as I have on the that network. 

Your input would be highly appreciated.

---

### Post by bab1 on 2013-11-26
> **almikul said:**
> Short description of what I am trying to do: I need to add security context to an existing user or add a new SElinux user in Ubuntu 12.04 LTS. Is it possible? 

On the remote network, I have "context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023" added to my user, but on my local Ubuntu, I have not. I am not even sure I fully understand how these SElinux permissions work, but I need to mount a SElinux partition on my local Ubuntu and have the same access as I have on the that network. 

Your input would be highly appreciated.
There is no SELinux needed on the local Ubuntu machine for you to mount a remote NFS export or Samba share.  I assume you will be using EXT as the file system.  The normal ownership and permissions should be all you have to worry about.

---

