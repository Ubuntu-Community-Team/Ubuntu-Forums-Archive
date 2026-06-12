---
title: "mount.nfs4 failed:No such file or directory"
date: 2012-01-25
forum: Server Platforms
---

### Post by dpouliot on 2012-01-25
showmount -e 192.168.1.1
yields:

Export list for 192.168.1.1:
/srv/nfs4/foo *
/srv/nfs4/foo2     *

yet:
sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.1.1:/srv/nfs4/foo /var/foo/

yields:
mount.nfs4: mounting 192.168.1.1:/srv/nfs4/foo failed, reason given by server:
  No such file or directory

I'm stuck. Any help is greatly appreciated!

---

### Post by SeijiSensei on 2012-01-26
Does root own the NFS share on the server?  Is /var/foo owned by root?  If so, you need no_root_squash among the export options; the default is root_squash.  See "man exports" for details.

---

### Post by nanog on 2012-03-10
If you are running lucid and just updated to the 38 or 39 kernel, nfs broke and seems to not want to mount nfsv4 shares unless you explicitly state the version (e.g. in fstab). since i have been upgrading to precise i no longer have this problem.

this is a lucid kernel problem since my dozen nfs mounts only broke after a lucid kernel upgrade and started functioning normally after upgrade to precise.

i noticed that the 40 kernel in proposed has some nfs fixes (probably from upstream).

---

