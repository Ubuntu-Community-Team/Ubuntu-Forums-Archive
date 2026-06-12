---
title: "Kerberized NFS: Permission Denied"
date: 2015-03-15
forum: Server Platforms
---

### Post by peridian on 2015-03-15
Hi,

I have two servers, both have the same central LDAP/Kerberos authentication setup, and this is working fine for all purposes so far (e.g. ssh).

I have tried to add a kerberized NFS mount on one of them, in order to perform system backups from the other.  However I seem to be getting access permission issues.  I have tried commenting out the hosts.deny line, but it makes no difference.  It does not appear that I am having trouble establishing a valid connection, it looks to me like the permissions on the exported file path.

Do I need to perform the mount as a user with permissions to that file path?  If so, how do I perform a mount as anything other than the root account on the client?

I was following the guides found [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo") and [here]("https://help.ubuntu.com/community/NFSv4Howto"), and I do not know what I have missed.  Any ideas?

Regards,
Rob.

Client output:

```

username@host:~$ sudo mount -t nfs4 -o sec=krb5 nfs-server:/share-path/ /mnt/tmp/
mount.nfs4: access denied by server while mounting nfs-server:/share-path/

```

Client klist:

```

username@host:~$ sudo klist -e -k /etc/krb5.keytab 
Keytab name: FILE:/etc/krb5.keytab
KVNO Principal
---- --------------------------------------------------------------------------
   3 host/nfs-client@REALM (aes256-cts-hmac-sha1-96) 
   4 nfs/nfs-client@REALM (aes256-cts-hmac-sha1-96) 

```

Server exportfs:

```

username@host:/$ sudo exportfs -v
/share-path
        10.0.0.0/8(rw,wdelay,root_squash,sec=sys,rw,root_squash,no_all_squash)
/share-path
        gss/krb5(rw,wdelay,root_squash,sec=sys,rw,root_squash,no_all_squash)

```

Server klist:

```

username@host:/$ sudo klist -e -k /etc/krb5.keytab 
Keytab name: FILE:/etc/krb5.keytab
KVNO Principal
---- --------------------------------------------------------------------------
   2 nfs/nfs-server@REALM (aes256-cts-hmac-sha1-96) 
   5 host/nfs-server@REALM (aes256-cts-hmac-sha1-96) 

```

/var/log/syslog (nothing in auth.log)

```

Mar 15 11:32:38 host rpc.mountd[3360]: auth_unix_ip: inbuf 'nfsd 10.x.x.x'
Mar 15 11:32:38 host rpc.mountd[3360]: auth_unix_ip: client 0x1877d00 '10.0.0.0/8'
Mar 15 11:32:38 host nslcd[1338]: [305def] <passwd="*"> request denied by validnames option

```

/etc/exports

```

/share-path 10.0.0.0/8(rw,root_squash,sync,subtree_check)
/share-path gss/krb5(rw,root_squash,sync,subtree_check)

```

/etc/hosts.deny

```

rpcbind mountd nfsd statd lockd rquotad : ALL

```


/etc/hosts.allow

```

rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1 127.0.1.1 10.0.0.0/8

```

/etc/default/nfs-kernel-server

```

# Number of servers to start up
RPCNFSDCOUNT=8


# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0


# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS="--manage-gids --debug all"


# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD="yes"


# Options for rpc.svcgssd.
RPCSVCGSSDOPTS="-vvv"


# Options for rpc.nfsd.
RPCNFSDOPTS=""

```

---

### Post by peridian on 2015-03-18
Figured it out in the end, it was a combination of:


[LIST]
[*]Firewalls; I had not specified a static port for the rpc daemon to run on in the file at /etc/default/nfs-kernel-server, and so my firewall rules did not include a path through to it.
[*]Client configuration; I had not specified to use RPC GSSD on the client side in /etc/default/nfs-common.
[/LIST]

Regards,
Rob.

---

