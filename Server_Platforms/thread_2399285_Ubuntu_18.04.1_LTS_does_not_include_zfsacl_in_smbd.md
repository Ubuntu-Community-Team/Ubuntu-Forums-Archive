---
title: "Ubuntu 18.04.1 LTS does not include zfsacl in smbd?"
date: 2018-08-23
forum: Server Platforms
---

### Post by Scrumps on 2018-08-23
Hello,

From what I have read, zfsacl should be a compatible and supported module with Samba 4.7+. Ubuntu 18.04.1 supports Samba 4.7.6 out of the box, and the zfsacl module is a part of this as described by the [documentation]("https://www.samba.org/samba/docs/4.7/man-html/vfs_zfsacl.8.html"). If I enable zfsacl as a vfs option on any share like so:

```
[storage]    path = "/mnt/zfs_pool/storage"
    printable = no
    veto files = /.snapshot/.windows/.mac/.zfs/
    writeable = yes
    browseable = yes
    access based share enum = no
    recycle:repository = .recycle/%U
    recycle:keeptree = yes
    recycle:versions = yes
    recycle:touch = yes
    recycle:directory_mode = 0777
    recycle:subdir_mode = 0700
    vfs objects = streams_xattr recycle zfsacl
    hide dot files = no
    guest ok = no
    nfs4:mode = special
    nfs4:acedup = merge
    nfs4:chown = yes



```

I end up not being able to connect to the share and receive this message:

```
$ tail -f /var/log/samba/log.smbd[2018/08/23 17:33:08.065547,  0] ../source3/smbd/service.c:623(make_connection_snum)
  vfs_init failed for service storage
[2018/08/23 17:33:08.065887,  0] ../lib/util/modules.c:49(load_module)
  Error loading module '/usr/lib/x86_64-linux-gnu/samba/vfs/zfsacl.so': /usr/lib/x86_64-linux-gnu/samba/vfs/zfsacl.so: cannot open shared object file: No such file or directory
[2018/08/23 17:33:08.065899,  0] ../source3/smbd/vfs.c:184(vfs_init_custom)
  error probing vfs module 'zfsacl': NT_STATUS_UNSUCCESSFUL
[2018/08/23 17:33:08.065905,  0] ../source3/smbd/vfs.c:379(smbd_vfs_init)
  smbd_vfs_init: vfs_init_custom failed for zfsacl
[2018/08/23 17:33:08.065911,  0] ../source3/smbd/service.c:623(make_connection_snum)
  vfs_init failed for service storage

```

So I need to ask, am I going insane? Is zfsacl not a VFS in Samba on Ubuntu 18.04.X, and if so why not? Is there any way to obtain this module through "official means"? Am I required to build this by source? I have been having a hard time finding any information on Ubuntu 18.04 and the vfs_zfsacl so maybe this is why. I do see the vfs_fruit module in "/usr/lib/x86_64-linux-gnu/samba/vfs/". 
I have the following samba packages installed:
```
 sudo dpkg -l | grep sambaii  python-samba                          2:4.7.6+dfsg~ubuntu-0ubuntu2.2    amd64        Python bindings for Samba
ii  samba                                 2:4.7.6+dfsg~ubuntu-0ubuntu2.2    amd64        SMB/CIFS file, print, and login server for Unix
ii  samba-common                          2:4.7.6+dfsg~ubuntu-0ubuntu2.2    all          common files used by both the Samba server and client
ii  samba-common-bin                      2:4.7.6+dfsg~ubuntu-0ubuntu2.2    amd64        Samba common files used by both the server and the client
ii  samba-dev                             2:4.7.6+dfsg~ubuntu-0ubuntu2.2    amd64        tools for extending Samba
ii  samba-dsdb-modules                    2:4.7.6+dfsg~ubuntu-0ubuntu2.2    amd64        Samba Directory Services Database
ii  samba-libs:amd64                      2:4.7.6+dfsg~ubuntu-0ubuntu2.2    amd64        Samba core libraries
ii  samba-vfs-modules                     2:4.7.6+dfsg~ubuntu-0ubuntu2.2    amd64        Samba Virtual FileSystem plugins

```

In terms of smbd with build options:

```
--with Options:   WITH_ADS
   WITH_AUTOMOUNT
   WITH_AVAHI_SUPPORT
   WITH_DNS_UPDATES
   WITH_PAM
   WITH_PAM_MODULES
   WITH_PTHREADPOOL
   WITH_QUOTAS
   WITH_SENDFILE
   WITH_SYSLOG
   WITH_WINBIND
~$ sudo smbd -b | grep -i zfs
~$ sudo smbd -b | grep -i vfs
   HAVE_SYS_STATVFS_H
   HAVE_SYS_VFS_H
   HAVE_STATVFS
   HAVE_STATVFS_F_FLAG
   STAT_STATVFS
   static_decl_vfs
   static_init_vfs
   vfs_acl_tdb_init
   vfs_acl_xattr_init
   vfs_aio_fork_init
   vfs_aio_pthread_init
   vfs_audit_init
   vfs_btrfs_init
   vfs_cap_init
   vfs_catia_init
   vfs_ceph_init
   vfs_commit_init
   vfs_crossrename_init
   vfs_default_quota_init
   vfs_dfs_samba4_init
   vfs_dirsort_init
   vfs_expand_msdfs_init
   vfs_extd_audit_init
   vfs_fake_perms_init
   vfs_fileid_init
   vfs_fruit_init
   vfs_full_audit_init
   vfs_linux_xfs_sgid_init
   vfs_media_harmony_init
   vfs_netatalk_init
   vfs_offline_init
   vfs_posix_eadb_init
   vfs_preopen_init
   vfs_readahead_init
   vfs_readonly_init
   vfs_recycle_init
   vfs_shadow_copy2_init
   vfs_shadow_copy_init
   vfs_shell_snap_init
   vfs_snapper_init
   vfs_streams_depot_init
   vfs_streams_xattr_init
   vfs_syncops_init
   vfs_time_audit_init
   vfs_unityed_media_init
   vfs_worm_init
   vfs_xattr_tdb_init
   vfs_default vfs_posixacl auth_domain auth_builtin auth_sam auth_winbind pdb_smbpasswd pdb_tdbsam auth_unix nss_info_template idmap_tdb idmap_passdb idmap_nss pdb_samba_dsdb pdb_ldapsam




```

So I guess the other question, is why is SMB not being compiled with ACL support? Apparently by default, it is supposed to be according to abartlet in #samba on freenode.

---

### Post by Scrumps on 2018-08-24
After chatting on IRC, bug report filed:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1788776](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1788776)

Seems like this is an issue with the package, as --with-acl-support is supposed to be a default build option on Samba (and someone or something is disabling it) and zfsacl is obviously missing from the samba-vfs-modules package.

---

