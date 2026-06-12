---
title: "Can't mount NFS share to unprivileged lxc container"
date: 2015-08-17
forum: Server Platforms
---

### Post by drogo1127 on 2015-08-17
I'm trying to mount nfs shares to an unprivileged ubuntu amd64 container, but keep getting access denied errors. I'm trying to do it from /etc/fstab within the container. I googled around a bit, and made some changes to apparmor (I usually use RedHat, so I'm used to selinux, apparmor is new to me);

  *mount fstype=nfs,*
* mount fstype=nfs4,*
[I]mount fstype=rpc_pipefs
[/I]
but that didn't resolve the issue. I decided to test on a privileged container and it's working fine. NFS shares mount fine. Both as root and as non-root with correct perms in fstab. 

So does anyone know if this an be done from within an unprivileged container? I was hoping to do everything unprivileged since that would be more secure, but I guess I could just do it as a regular user in a privileged container.

---

