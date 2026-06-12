---
title: "NFS server ignoring no_root_squash on exports"
date: 2013-01-11
forum: Server Platforms
---

### Post by MakOwner on 2013-01-11
Not sure exactly when this happened, I just noticed this when copying files between servers with NFS exports.  This has been up and working as expected for a while prior to this.

My export file looks like this on a 12.04 LTS server on 3.2.0-35-generic 64 bit kernel


The server has an interface on a single subnet and is essentially read only to everyone but root, as the permissions are set on the folders and directories to a single ID and group for all files.  In the past, if I copied data between servers using root, ID and group were maintained on the files - the same group and ID exist on all of these servers with same UID and GID.  In the last couple of days when I copy files, permissions are set to the anon ID and group as if root_squash was active on the export.  The files get copied but the process pauses at each file bceasue permissions are checked and fail.

Anyone have any idea what change I have missed that came in via updates over the last few weeks?  Last time I remember doing this and not having this issue was over a month ago...



```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/media/md1	*(rw,sync,no_root_squash)


```

I found it - just (another) brain fart on my part with permissions.



And the correct answer appears -- yet another bug:  [http://lists.debian.org/debian-user/2008/08/msg01966.html](http://lists.debian.org/debian-user/2008/08/msg01966.html)

---

