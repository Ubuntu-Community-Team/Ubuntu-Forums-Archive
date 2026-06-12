---
title: "Ubuntu 12.04, Active Directory Integration, Kerberos won't resolve service principals"
date: 2013-08-25
forum: Server Platforms
---

### Post by michael41 on 2013-08-25
Dear Ubuntu community, 

after having checked the whole internet literally, I hope that I might get help here. 

I am trying to accomplish integration of ubuntu 12.04 servers into a Windows 2012 active directory with nfs and single sign on. 

setup:
[LIST]
[*]srv02 Windows server
[*]srv03 Ubuntu file server
[*]srv04 Ubuntu application server
[/LIST]

**What I have done so far:**
[LIST=1]
[*]Set up Windows Server 2012 (srv02) Active Directory with DNS, and NTP.
[*]Extended AD with identity management for UNIX and set UNIX attributes for my users and groups.
[*]Installed two Ubuntu 12.04 servers (srv03 and srv04) and set them up to use MIT kerberos and sssd (with gssapi) to be able to authenticate AD users.
[*]Used the package msktutil to add my ubuntu servers to active directory.
[*]Set up Samba and NFS on srv03 and NFS client on srv04.
[/LIST]

**What works:**
-srv03 and srv04 can both see all my users and groups with unix attributes.
-users can login on both servers and use samba shares from srv03.
-srv03 and srv04 can get kerberos tickets for every user (eg. kinit [EMAIL="Administrator@LETTRICH.LOCAL"]Administrator@LETTRICH.LOCAL[/EMAIL] works)
-srv03 and srv04 can get kerberos tickets for their host name ( kinit -k srv03$@LETTRICH.LOCAL works)

**What does not work:**
-mounting an NFS share on srv04 hosted on srv03.
-getting a kerberos ticket for service principals.

Configuration Files:
krb5.conf (identical on srv03/srv04)
```

cat /etc/krb5.conf 
[libdefaults]
    default_realm = LETTRICH.LOCAL


# The following krb5.conf variables are only for MIT Kerberos.
    krb4_config = /etc/krb.conf
    krb4_realms = /etc/krb.realms
    kdc_timesync = 1
    ccache_type = 4
    forwardable = true
    proxiable = true


    default_tgs_enctypes = AES256-CTS-HMAC-SHA1-96 AES128-CTS-HMAC-SHA1-96 RC4-HMAC
        default_tkt_enctypes = AES256-CTS-HMAC-SHA1-96 AES128-CTS-HMAC-SHA1-96 RC4-HMAC
        permitted_enctypes = AES256-CTS-HMAC-SHA1-96 AES128-CTS-HMAC-SHA1-96 RC4-HMAC

[realms]
    LETTRICH.LOCAL = {
        kdc = srv02.lettrich.local:88
        default_domain = lettrich.local    
    }


[domain_realm]
    .lettrich.local = LETTRICH.LOCAL
    lettrich.local = LETTRICH.LOCAL
    .local = LETTRICH.LOCAL
    local = LETTRICH.LOCAL




[login]
    krb4_convert = true
    krb4_get_tickets = false




```

krb5.keytab on srv03, analog for srv04.

```

sudo klist -ke
Keytab name: FILE:/etc/krb5.keytab
KVNO Principal
---- --------------------------------------------------------------------------
  10 srv03$@LETTRICH.LOCAL (arcfour-hmac) 
  10 srv03$@LETTRICH.LOCAL (aes128-cts-hmac-sha1-96) 
  10 srv03$@LETTRICH.LOCAL (aes256-cts-hmac-sha1-96) 
  10 nfs/srv03.lettrich.local@LETTRICH.LOCAL (arcfour-hmac) 
  10 nfs/srv03.lettrich.local@LETTRICH.LOCAL (aes128-cts-hmac-sha1-96) 
  10 nfs/srv03.lettrich.local@LETTRICH.LOCAL (aes256-cts-hmac-sha1-96) 
  10 host/srv03.lettrich.local@LETTRICH.LOCAL (arcfour-hmac) 
  10 host/srv03.lettrich.local@LETTRICH.LOCAL (aes128-cts-hmac-sha1-96) 
  10 host/srv03.lettrich.local@LETTRICH.LOCAL (aes256-cts-hmac-sha1-96) 

```

nfs exports:

```

cat /etc/exports
/export               gss/krb5(rw,fsid=0,no_subtree_check,sync,insecure,crossmnt,anonuid=65534,anongid=65534)
/export/users           gss/krb5(rw,no_subtree_check,sync,insecure,nohide,anonuid=65534,anongid=65534)
/export/groups           gss/krb5(rw,no_subtree_check,sync,insecure,nohide,anonuid=65534,anongid=65534)
/export/share           gss/krb5(rw,no_subtree_check,sync,insecure,nohide,anonuid=65534,anongid=65534)
/export/backup           gss/krb5(rw,no_subtree_check,sync,insecure,nohide,anonuid=65534,anongid=65534)

```

both nfs server and client are told to use the gssapi.

mounting on srv04

```

sudo mount -t nfs4 -o sec=krb5 srv03:/export /mnt -vvv
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "srv03:/export"
mount: node:  "/mnt"
mount: types: "nfs4"
mount: opts:  "sec=krb5"
mount: external mount: argv[0] = "/sbin/mount.nfs4"
mount: external mount: argv[1] = "srv03:/export"
mount: external mount: argv[2] = "/mnt"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,sec=krb5"
mount.nfs4: timeout set for Sun Aug 25 18:44:58 2013
mount.nfs4: trying text-based options 'sec=krb5,addr=10.0.0.4,clientaddr=10.0.0.5'
mount.nfs4: mount(2): Permission denied
mount.nfs4: access denied by server while mounting srv03:/export

```

syslog on srv04 says:
```
Aug 25 18:42:58 srv04 rpc.gssd[754]: ERROR: No credentials found for connection to server srv03
```

trying to get a kerberos ticket for host or nfs
```

sudo kdestroy
sudo kinit -k
kinit: Client 'host/srv03.lettrich.local@LETTRICH.LOCAL' not found in Kerberos database while getting initial credentials

```

but 
```

sudo kinit -k 'srv03$'
sudo klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: srv03$@LETTRICH.LOCAL


Valid starting    Expires           Service principal
25/08/2013 20:18  26/08/2013 06:18  krbtgt/LETTRICH.LOCAL@LETTRICH.LOCAL
    renew until 26/08/2013 20:18

```
works for both srv03 and srv04 (names changed accordingly).

Active directory has both srv03 and srv04 listed as domain computers with correct service principal names.(names changed accordingly)
```
service principal name = nfs/srv03.lettrich.local; host/srv03.lettrich.local 
```

Where is my mistake? 

Will provide further information if needed. 

Thanks to all in advance who are willing to help.

---

### Post by koenn on 2013-08-25
I've never done anything like you describe so take this with a gain of salt :


Don't you need to map your service principals to AD user accounts ?

The only Kerberos I've done so far was setting up Kerberos SSO on an Apache web server, with user authentication against ms AD, and  the steps involved

1- running something like ```

ktpass /princ HTTP/testwiki.thedomain.be@REALM..BE /mapuser srv_wikitest   /pass 123XXX  
           /out D:\testwiki.keytab   /crypto all /ptype KRB5_NT_PRINCIPAL /mapop set

```
 on the domain controller  (command options : [http://technet.microsoft.com/en-us/library/cc753771.aspx](http://technet.microsoft.com/en-us/library/cc753771.aspx)   ; 'mapuser' and 'pass" refer to an AD user account )

2-  including the .keytab in the Apache configuration

the error "not found in Kerberos database while getting initial credentials" looks familiar to me and iirc correctly it disappeared when I got that keypass.exe and keytab thing figured out

maybe you need something similar for your host/... and nfs/... principals ?

---

