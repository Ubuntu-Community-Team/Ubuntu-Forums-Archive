---
title: "How do I get nfs-server to run in an LXC Unprivileged Container?"
date: 2016-05-12
forum: Virtualisation
---

### Post by Light Speed on 2016-05-12
For the life of me I cannot get the nfsd mount working:

Run as root in the container:
```
# service nfs-kernel-server restart * Stopping NFS kernel daemon                                                                                [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                          [ OK ] 
mount: permission denied
 * Exporting directories for NFS kernel daemon...                                                            [ OK ] 
 * Starting NFS kernel daemon                                                                                       rpc.nfsd: Unable to access /proc/fs/nfsd errno 2 (No such file or directory).
Please try, as root, 'mount -t nfsd nfsd /proc/fs/nfsd' and then restart rpc.nfsd to correct the problem
                                                                                                             [fail]
# mount -t nfsd nfsd /proc/fs/nfsd
mount: permission denied
```

In dmesg:
```
[1297233.302723] audit: type=1400 audit(1463013825.147:135): apparmor="DENIED" operation="mount" info="failed flags match" error=-13 profile="lxc-container-default" name="/proc/fs/nfsd/" pid=5018 comm="mount" fstype="nfsd" srcname="nfsd" flags="rw"[1297233.302897] audit: type=1400 audit(1463013825.147:136): apparmor="DENIED" operation="mount" info="failed flags match" error=-13 profile="lxc-container-default" name="/proc/fs/nfsd/" pid=5018 comm="mount" fstype="nfsd" srcname="nfsd" flags="ro"
[1297233.316298] audit: type=1400 audit(1463013825.159:137): apparmor="DENIED" operation="mount" info="failed flags match" error=-13 profile="lxc-container-default" name="/proc/fs/nfsd/" pid=5030 comm="mount" fstype="nfsd" srcname="nfsd" flags="rw"
[1297233.316361] audit: type=1400 audit(1463013825.159:138): apparmor="DENIED" operation="mount" info="failed flags match" error=-13 profile="lxc-container-default" name="/proc/fs/nfsd/" pid=5030 comm="mount" fstype="nfsd" srcname="nfsd" flags="ro"
```

My /etc/apparmor.d/lxc/lxc-default file:
```
# Do not load this file.  Rather, load /etc/apparmor.d/lxc-containers, which# will source all profiles under /etc/apparmor.d/lxc


profile lxc-container-default flags=(attach_disconnected,mediate_deleted) {
  #include <abstractions/lxc/container-base>


  # the container may never be allowed to mount devpts.  If it does, it
  # will remount the host's devpts.  We could allow it to do it with
  # the newinstance option (but, right now, we don't).
  deny mount fstype=devpts,
  mount fstype=rpc_pipefs,
  mount fstype=nfs,
  mount fstype=nfsd,
  mount options=(rw, bind, ro),
}
```

Any pointers?

---

