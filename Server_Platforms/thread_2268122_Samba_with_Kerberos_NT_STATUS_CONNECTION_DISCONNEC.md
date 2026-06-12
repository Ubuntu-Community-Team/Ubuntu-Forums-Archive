---
title: "Samba with Kerberos: NT_STATUS_CONNECTION_DISCONNECTED"
date: 2015-03-06
forum: Server Platforms
---

### Post by peridian on 2015-03-06
Hi,

I am trying to setup a standalone Samba share server, using Kerberos for password authentication and LDAP for user/group lookups.

I have already setup a working Kerberos 5/OpenLDAP server on a separate Ubuntu server.  The Samba server (Ubuntu server 14.04.2) has already been setup to successfully use the Kerberos/LDAP server using pam, nslcd and for ssh connections.  getent commands shows the users/groups from the LDAP server, and using those users with their Kerberos passwords works successfully.

Using smbclient, I'm certain the connection is established, but something goes wrong on the Samba server side that results in NT_STATUS_CONNECTION_DISCONNECTED.  Config and log outputs below.  Looking at a strace output from the smbd service on the server, just prior to process exiting, I can see one failed read to a file at '/usr/lib/x86_64-linux-gnu/../lib/plugin/krb5', and one successful read to the file at '/var/lib/samba/samba.keytab'

Given that last file, although it does not fail to access the file, it seems to abort almost immediately afterwards.  I think this has to do with my configuration of the smb.conf file, or my understanding of using Kerberos with Samba.  Given that the options stated Kerberos in the name, I assumed they were what I wanted, but a lot of articles refer to their use when in an AD domain, which I am not.

How do I configure smb.conf for a standalone server using Kerberos for authentication?

Regards,
Rob.

/etc/samba/smb.conf

```

[global]
        workgroup = REALM
        realm = REALM
        netbios name = HOSTNAME
        server string = Samba server
        server role = standalone         # Should be default, but explicitly stated to enforce.
        server services = smb            # Should be default, but explicitly stated to enforce.


        hosts allow = 10.
        dns proxy = no
        dns forwarder = 10.x.x.x


        interfaces = lo, em1
        bind interfaces only = yes


        syslog = 0
        log file = /var/log/samba/log.%m
        panic action = /usr/share/samba/panic-action %d


        kerberos method = dedicated keytab
        dedicated keytab file = /var/lib/samba/samba.keytab


        load printers = no
        cups options = raw


        socket options = TCP_NODELAY


        level2 oplocks = no
        oplocks = no

... shares defined below ...

```

smbclient debug:

```

user@hostname:/etc/samba$ sudo smbclient -d 10 -k -L //fqdn/
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 10
  tdb: 10
  printdrivers: 10
  lanman: 10
  smb: 10
  rpc_parse: 10
  rpc_srv: 10
  rpc_cli: 10
  passdb: 10
  sam: 10
  auth: 10
  winbind: 10
  vfs: 10
  idmap: 10
  quota: 10
  acls: 10
  locking: 10
  msdfs: 10
  dmapi: 10
  registry: 10
  scavenger: 10
  dns: 10
  ldb: 10
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = REALM
doing parameter realm = REALM
doing parameter netbios name = HOSTNAME
doing parameter server string = Local Laptop
doing parameter server role = standalone
doing parameter syslog = 0
doing parameter log file = /var/log/samba/log.%m
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter load printers = no
doing parameter cups options = raw
doing parameter socket options = TCP_NODELAY
doing parameter level2 oplocks = no
doing parameter oplocks = no
pm_process() returned Yes
lp_servicenumber: couldn't find homes
added interface eth0 ip=10.x.x.x bcast=10.x.x.x netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="HOSTNAME"
Client started (version 4.1.6-Ubuntu).
Opening cache file at /var/cache/samba/gencache.tdb
Opening cache file at /var/run/samba/gencache_notrans.tdb
sitename_fetch: No stored sitename for REALM
internal_resolve_name: looking up fqdn#20 (sitename (null))
Adding cache entry with key=[NBT/FQDN#20] and timeout=[Thu Jan  1 01:00:00 1970 BST] (-1425646371 seconds in the past)
no entry for fqdn#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name fqdn<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name fqdn<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name fqdn<0x20>
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 1 address for fqdn#20: 10.x.x.x
Adding cache entry with key=[NBT/FQDN#20] and timeout=[Fri Mar  6 13:03:51 2015 GMT] (660 seconds ahead)
internal_resolve_name: returning 1 addresses: 10.x.x.x:0 
Connecting to 10.x.x.x at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_REUSEPORT = 0
    SO_SNDBUF = 87040
    SO_RCVBUF = 372480
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0
 session request ok
protocol negotiation failed: NT_STATUS_CONNECTION_DISCONNECTED

```

/var/log/samba/log.10.x.x.x

```

[2015/03/06 13:21:41.321854,  0] ../lib/util/fault.c:72(fault_report)
  ===============================================================
[2015/03/06 13:21:41.323551,  0] ../lib/util/fault.c:73(fault_report)
  INTERNAL ERROR: Signal 11 in pid 1457 (4.1.6-Ubuntu)
  Please read the Trouble-Shooting section of the Samba HOWTO
[2015/03/06 13:21:41.323578,  0] ../lib/util/fault.c:75(fault_report)
  ===============================================================
[2015/03/06 13:21:41.323596,  0] ../source3/lib/util.c:785(smb_panic_s3)
  PANIC (pid 1457): internal error
[2015/03/06 13:21:41.329629,  0] ../source3/lib/util.c:896(log_stack_trace)
  BACKTRACE: 33 stack frames:
   #0 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(log_stack_trace+0x1a) [0x7fd9bd1d7f3a]
   #1 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(smb_panic_s3+0x20) [0x7fd9bd1d8010]
   #2 /usr/lib/x86_64-linux-gnu/libsamba-util.so.0(smb_panic+0x2f) [0x7fd9be700c6f]
   #3 /usr/lib/x86_64-linux-gnu/libsamba-util.so.0(+0x1ae86) [0x7fd9be700e86]
   #4 /lib/x86_64-linux-gnu/libpthread.so.0(+0x10340) [0x7fd9be928340]
   #5 /usr/lib/x86_64-linux-gnu(+0x5e023) [0x7fd9b31ad023]
   #6 /usr/lib/x86_64-linux-gnu(krb5_storage_free+0xf) [0x7fd9b31ab44f]
   #7 /usr/lib/x86_64-linux-gnu(+0x42465) [0x7fd9b3191465]
   #8 /usr/lib/x86_64-linux-gnu/samba/libgse.so.0(gse_krb5_get_server_keytab+0x27f) [0x7fd9b8486d8f]
   #9 /usr/lib/x86_64-linux-gnu/samba/libgse.so.0(+0xa7ca) [0x7fd9b84887ca]
   #10 /usr/lib/x86_64-linux-gnu/libgensec.so.0(gensec_start_mech+0x71) [0x7fd9b82672b1]
   #11 /usr/lib/x86_64-linux-gnu/libgensec.so.0(gensec_start_mech_by_ops+0xc) [0x7fd9b82673cc]
   #12 /usr/lib/x86_64-linux-gnu/libgensec.so.0(+0x83da) [0x7fd9b82643da]
   #13 /usr/lib/x86_64-linux-gnu/libgensec.so.0(+0x8ab6) [0x7fd9b8264ab6]
   #14 /usr/lib/x86_64-linux-gnu/libgensec.so.0(+0x98b2) [0x7fd9b82658b2]
   #15 /usr/lib/x86_64-linux-gnu/libgensec.so.0(gensec_update+0xa) [0x7fd9b826608a]
   #16 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(negprot_spnego+0x92) [0x7fd9be298452]
   #17 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0xbd98c) [0x7fd9be29898c]
   #18 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(reply_negprot+0x489) [0x7fd9be2990f9]
   #19 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0x112e11) [0x7fd9be2ede11]
   #20 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0x113edf) [0x7fd9be2eeedf]
   #21 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(+0x1144b0) [0x7fd9be2ef4b0]
   #22 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(run_events_poll+0x16c) [0x7fd9bd1ee0ac]
   #23 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(+0x37300) [0x7fd9bd1ee300]
   #24 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x8d) [0x7fd9bbbc65ed]
   #25 /usr/lib/x86_64-linux-gnu/samba/libsmbd_base.so.0(smbd_process+0x9ca) [0x7fd9be2f05ca]
   #26 smbd(+0x9fa4) [0x7fd9bed64fa4]
   #27 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(run_events_poll+0x16c) [0x7fd9bd1ee0ac]
   #28 /usr/lib/x86_64-linux-gnu/libsmbconf.so.0(+0x37300) [0x7fd9bd1ee300]
   #29 /usr/lib/x86_64-linux-gnu/libtevent.so.0(_tevent_loop_once+0x8d) [0x7fd9bbbc65ed]
   #30 smbd(main+0x13eb) [0x7fd9bed61b8b]
   #31 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7fd9bb81fec5]
   #32 smbd(+0x6f1d) [0x7fd9bed61f1d]
[2015/03/06 13:21:41.329899,  0] ../source3/lib/util.c:797(smb_panic_s3)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 1457]
[2015/03/06 13:21:41.332535,  0] ../source3/lib/util.c:805(smb_panic_s3)
  smb_panic(): action returned status 0
[2015/03/06 13:21:41.332590,  0] ../source3/lib/dumpcore.c:317(dump_core)
  dumping core in /var/log/samba/cores/smbd

```

/var/log/samba/log.%m

```

[2015/03/06 13:02:55.363632,  0] ../source4/smbd/server.c:370(binary_smbd_main)
  samba version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/03/06 13:02:56.009635,  0] ../source4/smbd/server.c:492(binary_smbd_main)
  samba: using 'standard' process model
samba: setproctitle not initialized, please either call setproctitle_init() or link against libbsd-ctor.
[2015/03/06 13:02:56.010786,  0] ../source4/smbd/service_stream.c:346(stream_setup_socket)
  Failed to listen on 127.0.0.1:445 - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED

```

/var/log/samba/smbd.log

```

[2015/03/06 13:02:55,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2015/03/06 13:02:55.402409,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2015/03/06 13:02:55.504690,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/03/06 13:02:55.504871,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2015/03/06 13:15:56.617529,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/03/06 13:15:56.617746,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL

```

---

### Post by peridian on 2015-03-06
Nevermind, I'm blind.

I finally noticed that the /var/lib/samba/samba.keytab file only had an entry for host/fqdn, and that the /etc/krb5.keytab had both host/fqdn and the cifs/fqdn entry.

Once I regenerated the keytab files so that krb5.keytab had the host/fqdn and the samba.keytab had the cifs/fqdn entry, everything started working.

Regards,
Rob.

---

### Post by aromo2 on 2015-03-06
Have you joined the Samba server to the LDAP domain?
```
net ads join -U DomAdminUsr
```
Even if you get errors after that, try a
```
net ads testjoin
```
If it says it's ok, you should be able to get a list of domain users by running:
```
wbinfo -u
```

Remember to start winbind and nmd services before doing all this.

---

