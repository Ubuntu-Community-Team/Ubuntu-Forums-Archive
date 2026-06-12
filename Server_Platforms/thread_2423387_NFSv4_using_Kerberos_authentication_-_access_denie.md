---
title: "NFSv4 using Kerberos authentication - access denied by server while mounting"
date: 2019-07-22
forum: Server Platforms
---

### Post by djh87 on 2019-07-22
Hi all

I'm adding a couple of NFS servers to a mixed Windows/Ubuntu environment. Everybody is authenticating against Active Directory using realmd & SSSD.

Rather than just lock down by client name/IP I'm attempting to use Kerberos to secure the NFS connections.

I've been following this Ubuntu guide, [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo), with a bit of direction from RedHat [https://access.redhat.com/solutions/2677831](https://access.redhat.com/solutions/2677831) (may need subscription to access).

I'm now at the point where I've got my NFS shares visible and set up, and my client and server (both Ubuntu 18.04.02) kerberos authenticated, but when I try to mount the share with *sudo mount -t nfs -o sec=krb5 -vvv nfs-server:/exports /mnt/nfstest *I'm getting the below

```
**mount.nfs: timeout set for Mon Jul 22 17:14:55 2019**
**mount.nfs: trying text-based options 'sec=krb5,vers=4.2,addr=1.2.3.4,clientaddr=5.6.7.8'**
**mount.nfs: mount(2): Permission denied**
**mount.nfs: access denied by server while mounting nfs-server:/exports**

```
On the nfs-server there is no sign of the connection attempt in journalctl. 

If I omit the '*-o sec=krb5*' option in the mount command, then the nfs-server's journalctl shows that the connection authenticates, but I still get access denied.

Output of *s*udo *mount -t nfs -vvv nfs-server:/exports  /mnt/nfstest*

```
**mount.nfs: timeout set for Mon Jul 22 17:18:32 2019**
**mount.nfs: trying text-based options 'vers=4.2,addr=1.2.3.4,clientaddr=5.6.7.8'**
**mount.nfs: mount(2): Operation not permitted**
**mount.nfs: trying text-based options 'addr=1.2.3.4'**
**mount.nfs: prog 100003, trying vers=3, prot=6**
**mount.nfs: trying 1.2.3.4 prog 100003 vers 3 prot TCP port 2049**
**mount.nfs: prog 100005, trying vers=3, prot=17**
**mount.nfs: trying 1.2.3.4 prog 100005 vers 3 prot UDP port 3552**
**mount.nfs: mount(2): Permission denied**
[B]mount.nfs: access denied by server while mounting nfs-server:/exports
[/B]
```Output of journalctl (from nfs-server)

[B]rpc.mountd[2755]: authenticated mount request from 1.2.3.4:857 for /exports (/exports)

[/B]Using the same server and client, but omitting the kerberos security settings from the exports file, I can connect and write to NFS shares as expected.

```
**/exports *(rw,sec=krb5:krb5i:krb5p)**                   **#this one gives access denied errors, also tried with just the relevant subnet and with just the relevant IP/hostname**
**/mnt/testa *(rw,no_subtree_check)                     #this one works fine, but is insecure**

```

Adding kerberos security settings to the second directory causes identical behaviour to the /exports share above.

**Kerberos Settings**
Both have had nfs/hostname@domain.name records added with setspn on the active directory, then updated on the server and client with msktutil -u

Both have got nfs.keytab files containing **only** the nfs/ principal names, eg.

```
Keytab name: FILE:/etc/nfs.keytab
KVNO Principal
---- --------------------------------------------------------------------------
   3 nfs/nfs-server@DOMAIN.NAME
   3 nfs/nfs-server@DOMAIN.NAME
   3 nfs/nfs-server@DOMAIN.NAME



```

Both have the **krb5.conf** below

```
[logging]
        default = FILE:/var/log/krb5libs.log
        kdc = FILE:/var/log/krb5kdc.log
        admin_server = FILE:/var/log/kdadmind.log


[libdefaults]
        default_realm = DOMAIN.NAME
        dns_lookup_realm = false
        dns_lookup_kdc = false
        ticket_lifetime = 24h
        renew_lifetime = 7d
        forwardable = true
        rdns = false


[realms]
        DOMAIN.NAME = {
                kdc = kdc.domain.name
                admin_server = kdc.domain.name
        }


[domain_realm]
        .domain.name = DOMAIN.NAME
        domain.name = DOMAIN.NAME

```

I had an error in syslog - **nfsdcltrack[2865]: Failed to init database: -13** - but resolved with manually initialising the DB [https://kosheo.gitlab.io/silverbox-server/](https://kosheo.gitlab.io/silverbox-server/) 

The share folders are owned by the user initiating the mount on the client server, and set at 774.

UFW disabled for now while getting this set up.

Rpcinfo looks ok (I think!) from the client, looking at the server

```
  program vers proto   port  service    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100005    1   udp   3552  mountd
    100005    1   tcp   3552  mountd
    100005    2   udp   3552  mountd
    100005    2   tcp   3552  mountd
    100005    3   udp   3552  mountd
    100005    3   tcp   3552  mountd
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    3   tcp   2049
    100003    3   udp   2049  nfs
    100227    3   udp   2049
    100021    1   udp   3551  nlockmgr
    100021    3   udp   3551  nlockmgr
    100021    4   udp   3551  nlockmgr
    100021    1   tcp   3551  nlockmgr
    100021    3   tcp   3551  nlockmgr
    100021    4   tcp   3551  nlockmgr

```

I'm stuck for where to look next for troubleshooting - any suggestions are very welcome! 

Cheers

D


**UPDATE**

Bit more info from the client side of things.

With the config as above (specifically using the separate nfs.keytab file in /etc/default/nfs-common RPCGSSDARGS="-k /etc/nfs.keytab") the client errors as below in syslog

```
[B]
rpc.svcgssd[5211]: ERROR: GSS-API: error in gss_acquire_cred(): GSS_S_FAILURE (Unspecified GSS failure.  Minor code may provide more information) - No key table entry found matching nfs/@
rpc.svcgssd[5211]: unable to obtain root (machine) credentials
rpc.svcgssd[5211]: do you have a keytab entry for nfs/<your.host>@<YOUR.REALM> in /etc/krb5.keytab?
systemd[1]: rpc-svcgssd.service: Control process exited, code=exited status=1
systemd[1]: rpc-svcgssd.service: Failed with result 'exit-code'.[/B]

```

Removing that option (which presumably reverts rpc-svcgssd to using /etc/krb5.keytab) and restarting nfs-common and the rpc-svcgssd service presents the same 'access denied by server' message, and a different error in syslog

```

[B]systemd[1]: Failed to create compat systemd cgroup /system.slice/rpc-svcgssd.service: Read-only file systemsystemd[1]: Failed to attach 70502 to compat systemd cgroup /system.slice/rpc-svcgssd.service: No such file or directory
systemd[70502]: Failed to attach 70502 to compat systemd cgroup /system.slice/rpc-svcgssd.service: No such file or directory[/B]

```


Config files below


**(nfs-server) ****/etc/nfs-common **

```
NEED_STATD="no"


STATDOPTS="--port 3553 --outgoing-port 3554"


NEED_IDMAPD="yes"


NEED_GSSD="yes"


RPCGSSDARGS="-k /etc/nfs.keytab"

```


**(nfs-client) ****/etc/nfs-common**
```
STATDOPTS=


NEED_IDMAPD="yes"


NEED_GSSD="yes"


RPCGSSDARGS="-k /etc/nfs.keytab"

```

[B]/etc/default/nfs-kernel-server
[/B]

```
RPCNFSDCOUNT=8


RPCNFSDPRIORITY=0


RPCMOUNTDOPTS="--manage-gids --port 3552"


NEED_SVCGSSD="yes"


RPCSVCGSSDOPTS="-vvv -rrr"      #also tried with the -n option, and -p as both host/nfs-server@DOMAIN.NAME and nfs/nfs-server@DOMAIN.NAME



```[B]/etc/idmapd.conf
[/B]```
[General]


Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
Domain=domain.name


[Mapping]


Nobody-User = nobody
Nobody-Group = nogroup


[Translation]
Method = nsswitch

```

---

### Post by SeijiSensei on 2019-07-22
Just as a guess, the user you're trying to connect as does not have permissions to the /export directory.

---

### Post by djh87 on 2019-07-23
The user I'm connecting as owns the /export dir - user is admin, dir is admin:domain users - but thanks for the suggestion!

---

