---
title: "Ubuntu 14.04 samba 4.1.6: Errors after upgrading"
date: 2014-05-19
forum: Server Platforms
---

### Post by kjertil on 2014-05-19
Hello, i upgraded my ubuntu server from ( i think it was) 13.04 to 14.04 and i had webmin + samba working.
Now, i get tons of errors. i don't use the webmin interface at the moment, rather just trying to find out how to save this mess.
Let's forget for a moment that webmin doesn't seem to work with samba 4 at all.

When ssh-ing and sudo-ing in to the server i get this (official bug it seems) :
```

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Failed to open /var/lib/samba/private/secrets.tdb
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_new_rid: failed to open /var/lib/samba/private/passdb.tdb!
```

Instead of trying to find out what is wrong, perhaps the easiest is to revert to samba 3 ? Or even just reinstall Ubuntu 12.04...
It amazes me that it can be so fragile that you need to feel sceptic every time there is a package update notification...
I hope some one has any thought about this!

---

### Post by mörgæs on 2014-05-19
> **kjertil said:**
> 
Instead of trying to find out what is wrong, perhaps the easiest is to revert to samba 3 ? Or even just reinstall Ubuntu 12.04...

If you decide to reinstall it's better to go for 14.04. What you saw could be the upgrade process failing, not necessarily 14.04 nor Samba.


> **kjertil said:**
> 
It amazes me that it can be so fragile that you need to feel sceptic every time there is a package update notification...
I hope some one has any thought about this!

Updates are normally safe. The problem is upgrading.

---

### Post by Morbius1 on 2014-05-19
Not a big fan of upgrades but this is a known bug:
> no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
They're workin' on it: [https://bugs.launchpad.net/ubuntu/trusty/+source/samba/+bug/1257186](https://bugs.launchpad.net/ubuntu/trusty/+source/samba/+bug/1257186)

Get rid of the following package and the memory leak error will _[COLOR=#0000cd]likely[/COLOR]_ go away:
```
sudo apt-get remove libpam-smbpass
```
It's a silly package any way since it forces at every reboot the samba password to match the user's local login password.

---

### Post by kjertil on 2014-05-19
Thanks for your replies so far. 
I removed libpam-smbpass and got rid of the "no talloc.." thing. Obviously this problem arised after a upgrade to 14.04, the question is if there is a way to get it working again. 

I've reinstalled Samba 4, ditched the old smb.conf file and are now trying to get it working again starting from the default Samba 4 smb.conf file. I'm still not sure if there are more things preventing it from working. 
Not sure what to do now since this server is live and hot with users beeing slightly upset at the moment :)

---

### Post by kjertil on 2014-05-19
Update:
I apt-get purged samba, re-installed and now i get from testparm:

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
[...]
Loaded services file OK.
ERROR: cache directory /var/cache/samba does not exist

...and of course there are no cache directory for samba. Where is the directive to look for this cache directory!? 

smbstatus gives this info:

/var/run/samba/locking.tdb not initialised
This is normal if an SMB client has never connected to your server.

Time is running out, i think at this point i'll either have to reinstall 13.10 or take a look at the win2008 server price offers...

---

### Post by kjertil on 2014-05-19
Update 2:
Spamming my own thread here...

So i did (after many different try outs):
```
sudo apt-get autoremove samba samba-common
```

and then
```
sudo apt-get install samba samba-common
sudo apt-get install system-config-samba cifs-utils
```

At least for now, i can testparm and smbstatus with no errors! Will try and manually restore shares now...

---

### Post by Morbius1 on 2014-05-19
It does appear you may have some weird hybrid of samba3 and samba4 going on.

You stated you purged samba. Did you mean the samba package itself? /var/cache/samba doesn't come from samba it comes from samba-common.

You might want to make sure there are no samba3 packages and make sure only samba4 packages are present.

If 13.10 worked for you then you could go back to it or you can install 14.04. Not sure why you upgraded a production server but either way you might want to install it in a VBox guest first to test things out before you deploy it.

---

### Post by kjertil on 2014-05-19
Morbius1, 
you might be correct since i did a upgrade to 14.04 and had previously installed most things via Webmin. I'm doing my best to clear everything out but i mean, how far must ones wisdom stretch in order to be able to uninstall Samba? I'm not sure how to find Samba 3 related files and safely remove them only?
Also, i think it's not fair to say that when the system itself promotes an upgrade, the production server has to be cloned and tested in a virtual enviroment in order to see if it [an upgrade] works?
Btw, i'm not sure you read my post #6? 
Before i had to leave work, i was still not able to log in to a test share with smbclient. Will try again tomorrow!

---

### Post by kjertil on 2014-05-20
Update 3:
Still not able to get Samba 4.1.6 to work.
Seems there is an Samba 4.1.7 that might fix these strange bugs, but i haven't been able to compile it to try it out...
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1273447](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1273447)

*EDIT*
I'm able to access a test share with the guest ok = yes directive so hopefully not too far from solving this.

---

### Post by kjertil on 2014-05-20
Update 4: 
I can't for my life understand what is going on. I'm adding directive log level = 10 to smb.conf but it's not it showing up with testparm? 
*EDIT*
Found this... Of course testparm doesn't show it: [http://unix.stackexchange.com/questions/129384/unable-to-modify-log-level-is-samba](http://unix.stackexchange.com/questions/129384/unable-to-modify-log-level-is-samba)

So, just got to dig through this (excerpts):

```

pdb_getsampwrid (TDB): error looking up RID 513 by key RID_00000201

 Can't find a unix id for an unmapped group

 LEGACY: mapping failed for sid S-1-5-21-1804163848-409296064-3285502590-513

pdb_getsampwrid (TDB): error looking up RID 513 by key RID_00000201

Can't find a unix id for an unmapped group

Failed to fetch domain sid for WORKGROUP

Can't find a unix id for an unmapped group

Could not convert SID S-1-5-11 to gid, ignoring it

NT error packet at ../source3/smbd/sesssetup.c(377) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE

receive_smb_raw_talloc failed for client ipv4 https://www.netiq.com/support/kb/doc.php?id=7012104

Server exit (failed to receive smb request)
```

debconf-show samba-common:
  ```
samba-common/title:
  samba-common/workgroup: WORKGROUP
  samba-common/encrypt_passwords: true
  samba-common/do_debconf: true
  samba-common/dhcp: false
```


smbpasswd -r localhost -U samba-user:

```
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
pm_process() returned Yes
lp_servicenumber: couldn't find homes
Netbios name list:-
my_netbios_names[0]="SERVER"
Attempting to register passdb backend smbpasswd
Successfully added passdb backend 'smbpasswd'
Attempting to register passdb backend tdbsam
Successfully added passdb backend 'tdbsam'
Attempting to register passdb backend wbc_sam
Successfully added passdb backend 'wbc_sam'
Attempting to register passdb backend samba_dsdb
Successfully added passdb backend 'samba_dsdb'
Attempting to register passdb backend samba4
Successfully added passdb backend 'samba4'
Attempting to register passdb backend ldapsam
Successfully added passdb backend 'ldapsam'
Attempting to register passdb backend NDS_ldapsam
Successfully added passdb backend 'NDS_ldapsam'
Attempting to register passdb backend IPA_ldapsam
Successfully added passdb backend 'IPA_ldapsam'
Attempting to find a passdb backend to match tdbsam (tdbsam)
Found pdb backend tdbsam
pdb backend tdbsam has a valid init
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Old SMB password:
New SMB password:
Retype new SMB password:
Opening cache file at /var/cache/samba/gencache.tdb
Opening cache file at /var/run/samba/gencache_notrans.tdb
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up localhost#20 (sitename (null))
Adding cache entry with key=[NBT/LOCALHOST#20] and timeout=[Thu Jan  1 01:00:00 AM 1970 CET] (-1400592178 seconds in the past)
no entry for localhost#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name localhost<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name localhost<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name localhost<0x20>
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 1 address for localhost#20: 127.0.0.1
Adding cache entry with key=[NBT/LOCALHOST#20] and timeout=[Tue May 20 03:33:58 PM 2014 CEST] (660 seconds ahead)
internal_resolve_name: returning 1 addresses: 127.0.0.1:0 
Connecting to 127.0.0.1 at port 445
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
    SO_SNDBUF = 2626560
    SO_RCVBUF = 1061808
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
    TCP_DEFER_ACCEPT = 0
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
     negotiate: struct NEGOTIATE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmNegotiate (1)
        NegotiateFlags           : 0x60088215 (1611170325)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               0: NTLMSSP_NEGOTIATE_TARGET_INFO
               0: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
        DomainNameLen            : 0x0009 (9)
        DomainNameMaxLen         : 0x0009 (9)
        DomainName               : *
            DomainName               : 'WORKGROUP'
        WorkstationLen           : 0x0006 (6)
        WorkstationMaxLen        : 0x0006 (6)
        Workstation              : *
            Workstation              : 'SERVER'
     challenge: struct CHALLENGE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmChallenge (0x2)
        TargetNameLen            : 0x000c (12)
        TargetNameMaxLen         : 0x000c (12)
        TargetName               : *
            TargetName               : 'SERVER'
        NegotiateFlags           : 0x608a8215 (1619690005)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               1: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               1: NTLMSSP_NEGOTIATE_TARGET_INFO
               0: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
        ServerChallenge          : 1be0d946da0d55f2
        Reserved                 : 0000000000000000
        TargetInfoLen            : 0x0038 (56)
        TargetNameInfoMaxLen     : 0x0038 (56)
        TargetInfo               : *
            TargetInfo: struct AV_PAIR_LIST
                count                    : 0x00000005 (5)
                pair: ARRAY(5)
                    pair: struct AV_PAIR
                        AvId                     : MsvAvNbDomainName (0x2)
                        AvLen                    : 0x000c (12)
                        Value                    : union ntlmssp_AvValue(case 0x2)
                        AvNbDomainName           : 'SERVER'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvNbComputerName (0x1)
                        AvLen                    : 0x000c (12)
                        Value                    : union ntlmssp_AvValue(case 0x1)
                        AvNbComputerName         : 'SERVER'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvDnsDomainName (0x4)
                        AvLen                    : 0x0000 (0)
                        Value                    : union ntlmssp_AvValue(case 0x4)
                        AvDnsDomainName          : ''
                    pair: struct AV_PAIR
                        AvId                     : MsvAvDnsComputerName (0x3)
                        AvLen                    : 0x000c (12)
                        Value                    : union ntlmssp_AvValue(case 0x3)
                        AvDnsComputerName        : 'server'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvEOL (0x0)
                        AvLen                    : 0x0000 (0)
                        Value                    : union ntlmssp_AvValue(case 0x0)
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
     authenticate: struct AUTHENTICATE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmAuthenticate (3)
        LmChallengeResponseLen   : 0x0018 (24)
        LmChallengeResponseMaxLen: 0x0018 (24)
        LmChallengeResponse      : *
            LmChallengeResponse      : union ntlmssp_LM_RESPONSE(case 24)
            v1: struct LM_RESPONSE
                Response                 : 89fa6affa00f007d4bc9e3705c934bfd8253df8f1a2cca89
        NtChallengeResponseLen   : 0x0064 (100)
        NtChallengeResponseMaxLen: 0x0064 (100)
        NtChallengeResponse      : *
            NtChallengeResponse      : union ntlmssp_NTLM_RESPONSE(case 100)
            v2: struct NTLMv2_RESPONSE
                Response                 : b3af2d5562a61ae90e2459e4394970df
                Challenge: struct NTLMv2_CLIENT_CHALLENGE
                    RespType                 : 0x01 (1)
                    HiRespType               : 0x01 (1)
                    Reserved1                : 0x0000 (0)
                    Reserved2                : 0x00000000 (0)
                    TimeStamp                : Tue May 20 03:22:58 PM 2014 CEST
                    ChallengeFromClient      : 0d7a401ca34dd7e5
                    Reserved3                : 0x00000000 (0)
                    AvPairs: struct AV_PAIR_LIST
                        count                    : 0x00000005 (5)
                        pair: ARRAY(5)
                            pair: struct AV_PAIR
                                AvId                     : MsvAvNbDomainName (0x2)
                                AvLen                    : 0x000c (12)
                                Value                    : union ntlmssp_AvValue(case 0x2)
                                AvNbDomainName           : 'SERVER'
                            pair: struct AV_PAIR
                                AvId                     : MsvAvNbComputerName (0x1)
                                AvLen                    : 0x000c (12)
                                Value                    : union ntlmssp_AvValue(case 0x1)
                                AvNbComputerName         : 'SERVER'
                            pair: struct AV_PAIR
                                AvId                     : MsvAvDnsDomainName (0x4)
                                AvLen                    : 0x0000 (0)
                                Value                    : union ntlmssp_AvValue(case 0x4)
                                AvDnsDomainName          : ''
                            pair: struct AV_PAIR
                                AvId                     : MsvAvDnsComputerName (0x3)
                                AvLen                    : 0x000c (12)
                                Value                    : union ntlmssp_AvValue(case 0x3)
                                AvDnsComputerName        : 'server'
                            pair: struct AV_PAIR
                                AvId                     : MsvAvEOL (0x0)
                                AvLen                    : 0x0000 (0)
                                Value                    : union ntlmssp_AvValue(case 0x0)
        DomainNameLen            : 0x0000 (0)
        DomainNameMaxLen         : 0x0000 (0)
        DomainName               : *
            DomainName               : ''
        UserNameLen              : 0x0010 (16)
        UserNameMaxLen           : 0x0010 (16)
        UserName                 : *
            UserName                 : 'samba-user'
        WorkstationLen           : 0x000c (12)
        WorkstationMaxLen        : 0x000c (12)
        Workstation              : *
            Workstation              : 'SERVER'
        EncryptedRandomSessionKeyLen: 0x0010 (16)
        EncryptedRandomSessionKeyMaxLen: 0x0010 (16)
        EncryptedRandomSessionKey: *
            EncryptedRandomSessionKey: DATA_BLOB length=16
[0000] CE 19 0D 15 7C 29 D2 15   BA CF 80 45 1B C2 35 E1   ....|).. ...E..5.
        NegotiateFlags           : 0x60088215 (1611170325)
               1: NTLMSSP_NEGOTIATE_UNICODE
               0: NTLMSSP_NEGOTIATE_OEM    
               1: NTLMSSP_REQUEST_TARGET   
               1: NTLMSSP_NEGOTIATE_SIGN   
               0: NTLMSSP_NEGOTIATE_SEAL   
               0: NTLMSSP_NEGOTIATE_DATAGRAM
               0: NTLMSSP_NEGOTIATE_LM_KEY 
               0: NTLMSSP_NEGOTIATE_NETWARE
               1: NTLMSSP_NEGOTIATE_NTLM   
               0: NTLMSSP_NEGOTIATE_NT_ONLY
               0: NTLMSSP_ANONYMOUS        
               0: NTLMSSP_NEGOTIATE_OEM_DOMAIN_SUPPLIED
               0: NTLMSSP_NEGOTIATE_OEM_WORKSTATION_SUPPLIED
               0: NTLMSSP_NEGOTIATE_THIS_IS_LOCAL_CALL
               1: NTLMSSP_NEGOTIATE_ALWAYS_SIGN
               0: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               0: NTLMSSP_NEGOTIATE_TARGET_INFO
               0: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
Could not connect to machine localhost: NT_STATUS_LOGON_FAILURE
```

If any one has any ideas where to start... ?

---

### Post by kjertil on 2014-05-22
Ok, i'm just throwing in another bump here...
I've just installed a fresh copy of Ubuntu 14.04 on a another drive, did a apt-get update and at boot time i see that samba has failed to start. Great.
ProFTPd has also been crashing latetly due to the log-rotate-restart-bug.Great.
Now i'm trying to update to the latest Webmin and get a HTTP not found message.Great.
Now, can ANYONE confirm a smooth non-problematic transition to 14.04 with the very common server role LAMP / SAMBA + Webmin combo?
I'm sitting here laughing hysterically as i'm typing this btw...

---

### Post by kjertil on 2014-06-05
LOL, not much action here.

So, i tried a fresh install of Ubuntu server 14.04 in Virtual box, installed Samba (which installs 4.1.6 by default) and samba-tool dbcheck outputs this:

```
ERROR(<type 'exceptions.ValueError'>): uncaught exception - unable to parse dn string
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/dbcheck.py", line 120, in run
    reset_well_known_acls=reset_well_known_acls)
  File "/usr/lib/python2.7/dist-packages/samba/dbchecker.py", line 69, in __init__
    self.infrastructure_dn = ldb.Dn(samdb, "CN=Infrastructure," + samdb.domain_dn()) 
```

samba-tool user list gives me:

```
Could not find machine account in secrets database: Failed to fetch machine account password from secrets.ldb: Could not find entry to match filter: '(&(flatname=WORKGROUP)(objectclass=primaryDomain))' base: 'cn=Primary Domains': No such object: (null) and failed to fetch SECRETS/MACHINE_PASSWORD/WORKGROUP from /var/lib/samba/private/secrets.tdb: NT_STATUS_CANT_ACCESS_DOMAIN_INFO
ERROR(ldb): uncaught exception - ldb_search: invalid basedn '(null)'
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/user.py", line 271, in run
    attrs=["samaccountname"]) 
```

---

### Post by vayu on 2014-07-27
[QUOTE=kjertil;13027608When ssh-ing and sudo-ing in to the server i get this (official bug it seems) :
```

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

```
[/QUOTE]

The below worked for me:
[http://ubuntuforums.org/showthread.php?t=2214042&p=12995103#post12995103]("http://ubuntuforums.org/showthread.php?t=2214042&p=12995103#post12995103")

"You can also fix this issue while keeping libpam-smbpass installed by running "pam-auth-update" and remove "SMB password synchronization". Got that solution from Thomas (reusch) on https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186"

---

