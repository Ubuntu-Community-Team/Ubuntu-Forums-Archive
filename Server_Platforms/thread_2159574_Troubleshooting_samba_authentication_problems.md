---
title: "Troubleshooting samba authentication problems"
date: 2013-07-03
forum: Server Platforms
---

### Post by RyanBiggs on 2013-07-03
Hello all,

I'm a fairly novice server administrator but have several Ubuntu 12.04.2 LTS x64-based samba servers set up at my work, which generally are performing very well. However, there's one share which won't allow non-guest access for some reason, and I'm having a heck of a time figuring out why.

In smb.conf, I have 

security = user

set, and the following share definition:

```
[accounting]
    comment = ATS Accounting File Server
    path = /srv/falcon/accounting
    browsable = yes
    create mask = 0755
    guest ok = no
    read only = no

```
I've added a couple of users by first creating unix accounts, then following the directions in this guide:

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

If I set

guest ok = yes

in smb.conf, then I can access the share just fine. However, with guest ok = no, I get the following error in Windows when trying to access the share after providing correct login credentials:

\\falcon\accounting is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

Just to be sure unix permissions aren't the problem, I temporarily have everything set wide open (0777) in the /srv/falcon/accounting directory and sub-directories. Things seem like they are set up just like another share (on a different server) which is working properly, so I can't figure out what's wrong. How can I troubleshoot further to figure out what the problem is?

Thanks!

---

### Post by Iowan on 2013-07-03
Moved to Server Platforms.

Are there other shares on this server that are working properly?
(Is problem limited to one share - or is this the only share?)

---

### Post by RyanBiggs on 2013-07-03
Hi [COLOR=#000000]Iowan,

Thanks for the move; I wasn't sure the best place to post this question.

There is one other share on the server (actually the main share provided by this box), but it's by design open:
[/COLOR]
```
[projects]
    comment = ATS General File Server
    path = /srv/falcon/projects
    browsable = yes
    create mask = 0755
    guest ok = yes
    read only = no

```

It works very well, but of course authentication issues don't come into play!

---

### Post by Iowan on 2013-07-03
You may not have the desire to experiment - otherwise, I'd ask if [projects] loses access with **guest ok = no**. I'm also curious if you can log into the server as one of the users you created.

---

### Post by RyanBiggs on 2013-07-03
> [COLOR=#000000]You may not have the desire to experiment - otherwise, I'd ask if [projects] loses access with [/COLOR]**guest ok = no.**

I tried that and was unable to access the share even after providing credentials, just as with the accounting share.

> **I'm also curious if you can log into the server as one of the users you created.**

Yes I can, but there is a clue that appears on login:

```
Could not chdir to home directory /home/rbiggs: No such file or directory
/usr/bin/xauth:  error in locking authority file /home/rbiggs/.Xauthority
```

I haven't pondered yet the implications of this... I used sudo useradd to create the user accounts; did I miss something?

---

### Post by capscrew on 2013-07-04
> **RyanBiggs said:**
> I tried that and was unable to access the share even after providing credentials, just as with the accounting share.



Yes I can, but there is a clue that appears on login:

```
Could not chdir to home directory /home/rbiggs: No such file or directory
/usr/bin/xauth:  error in locking authority file /home/rbiggs/.Xauthority
```

I haven't pondered yet the implications of this... I used sudo useradd to create the user accounts; did I miss something?

Did you add the appropriate samba users with smbpasswd -a <user>?  Besides the Linux user you need to have the Samba users in the Samba database.

You can see who has been added with this```
sudo pdbedit -L
```This lists the contents of the Samba user database.

---

### Post by RyanBiggs on 2013-07-05
> [COLOR=#000000]Did you add the appropriate samba users with smbpasswd -a <user>? Besides the Linux user you need to have the Samba users in the Samba database.[/COLOR]

Yes sure did, here's the output of [COLOR=#000000][FONT=Ubuntu Mono]pdbedit -L:[/FONT][/COLOR]

```
nobody:65534:nobody
falcon:1000:Falcon
rbiggs:1002:
kari:1001:
```

rbiggs and kari are the two users I added. I also added a samba user for the "admin" account, falcon.

---

### Post by redmk2 on 2013-07-05
> **RyanBiggs said:**
> Yes sure did, here's the output of [COLOR=#000000][FONT=Ubuntu Mono]pdbedit -L:[/FONT][/COLOR]

```
nobody:65534:nobody
falcon:1000:Falcon
rbiggs:1002:
kari:1001:
```

rbiggs and kari are the two users I added. I also added a samba user for the "admin" account, falcon.

From the Ubuntu terminal post the output of this (login with a user when asked)```
smbtree -d3
```

---

### Post by RyanBiggs on 2013-07-05
Hi [COLOR=#000000]redmk2,[/COLOR]

The output of [COLOR=#000000][FONT=Ubuntu Mono]smbtree -d3 that seems to pertain to the server in question shows:[/FONT][/COLOR]

```
        \\FALCON                        falcon server (Samba, Ubuntu)
Connecting to host=FALCON
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_wins: Attempting wins lookup for name FALCON<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name FALCON<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\FALCON\IPC$                   IPC Service (falcon server (Samba, Ubuntu))
                \\FALCON\accounting             ATS Accounting File Server
                \\FALCON\projects               ATS General File Server
                \\FALCON\print$                 Printer Drivers

```

The following is the complete output, some of which is obviously from other shares, servers, and workstations:

```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::21f:d0ff:fe99:c809%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter falcon's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ATS<0x1d>
Got a positive name query response from 192.168.0.3 ( 192.168.0.3 )
Connecting to host=192.168.0.3
Connecting to 192.168.0.3 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.3 ( 192.168.0.3 )
Got a positive name query response from 192.168.0.7 ( 192.168.0.7 )
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
Connecting to host=192.168.0.129
Connecting to 192.168.0.129 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
Connecting to host=192.168.0.129
Connecting to 192.168.0.129 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\TESTOPS-PC
Connecting to host=TESTOPS-PC
resolve_lmhosts: Attempting lmhosts lookup for name TESTOPS-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TESTOPS-PC<0x20>
resolve_wins: Attempting wins lookup for name TESTOPS-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TESTOPS-PC<0x20>
Connecting to 192.168.0.110 at port 445
Connecting to 192.168.0.110 at port 139
Error connecting to 192.168.0.110 (Success)
cli_start_connection: failed to connect to TESTOPS-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
        \\OTTER
Connecting to host=OTTER
resolve_lmhosts: Attempting lmhosts lookup for name OTTER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name OTTER<0x20>
resolve_wins: Attempting wins lookup for name OTTER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name OTTER<0x20>
resolve_hosts: getaddrinfo failed for name OTTER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name OTTER<0x20>
Got a positive name query response from 192.168.0.55 ( 192.168.0.55 )
Connecting to 192.168.0.55 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\OEM-RHSYHZ66QEP
Connecting to host=OEM-RHSYHZ66QEP
resolve_lmhosts: Attempting lmhosts lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_wins: Attempting wins lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_hosts: getaddrinfo failed for name OEM-RHSYHZ66QEP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name OEM-RHSYHZ66QEP<0x20>
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
Connecting to 192.168.0.129 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\LANCASTER
Connecting to host=LANCASTER
resolve_lmhosts: Attempting lmhosts lookup for name LANCASTER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LANCASTER<0x20>
resolve_wins: Attempting wins lookup for name LANCASTER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LANCASTER<0x20>
Connecting to 192.168.0.123 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
ATSMFG
resolve_lmhosts: Attempting lmhosts lookup for name ATSMFG<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ATSMFG<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ATSMFG<0x1d>
Got a positive name query response from 192.168.0.7 ( 192.168.0.7 )
Connecting to host=192.168.0.7
Connecting to 192.168.0.7 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\MFG                           mfg server (Samba, Ubuntu)
Connecting to host=MFG
resolve_lmhosts: Attempting lmhosts lookup for name MFG<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MFG<0x20>
resolve_wins: Attempting wins lookup for name MFG<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MFG<0x20>
Connecting to 192.168.0.7 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\MFG\print$            Printer Drivers
                \\MFG\authority         ATS Manufacturing Authority Data
                \\MFG\engineering       ATS Manufacturing Engineering Data
                \\MFG\IPC$              IPC Service (mfg server (Samba, Ubuntu))
ATS
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ATS<0x1d>
Got a positive name query response from 192.168.0.3 ( 192.168.0.3 )
Connecting to host=192.168.0.3
Connecting to 192.168.0.3 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\VF8                           MS-DOS Peer Server
Connecting to host=VF8
resolve_lmhosts: Attempting lmhosts lookup for name VF8<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name VF8<0x20>
resolve_wins: Attempting wins lookup for name VF8<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name VF8<0x20>
resolve_hosts: getaddrinfo failed for name VF8 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name VF8<0x20>
Got a positive name query response from 192.168.0.18 ( 192.168.0.18 )
Connecting to 192.168.0.18 at port 445
Connecting to 192.168.0.18 at port 139
Server requested plaintext password but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED
        \\STARLIFTER                    TeraByte File Server -- Secondary
Connecting to host=STARLIFTER
resolve_lmhosts: Attempting lmhosts lookup for name STARLIFTER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name STARLIFTER<0x20>
resolve_wins: Attempting wins lookup for name STARLIFTER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name STARLIFTER<0x20>
Connecting to 192.168.0.12 at port 445
Connecting to 192.168.0.12 at port 139
                \\STARLIFTER\ADMIN$             IPC Service (TeraByte File Server -- Secondary)
                \\STARLIFTER\IPC$               IPC Service (TeraByte File Server -- Secondary)
                \\STARLIFTER\projects           ATS Eagle Project Server Backup - New 2013
                \\STARLIFTER\SVN_Backup         Backup for Project Subversion Server
                \\STARLIFTER\Code               Old DOS Programs And Application Share
                \\STARLIFTER\info               TeraStation utilities
        \\PROJECT                       G-Code Server
Connecting to host=PROJECT
resolve_lmhosts: Attempting lmhosts lookup for name PROJECT<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PROJECT<0x20>
resolve_wins: Attempting wins lookup for name PROJECT<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PROJECT<0x20>
Connecting to 192.168.0.2 at port 445
Connecting to 192.168.0.2 at port 139
cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
                \\PROJECT\ADMIN$                IPC Service (G-Code Server)
                \\PROJECT\IPC$                  IPC Service (G-Code Server)
                \\PROJECT\CODE                  For CNC Machine Code
        \\PEACEMAKER                    Workstation
Connecting to host=PEACEMAKER
resolve_lmhosts: Attempting lmhosts lookup for name PEACEMAKER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PEACEMAKER<0x20>
resolve_wins: Attempting wins lookup for name PEACEMAKER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PEACEMAKER<0x20>
Connecting to 192.168.0.125 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\HERCULES                      hercules
Connecting to host=HERCULES
resolve_lmhosts: Attempting lmhosts lookup for name HERCULES<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name HERCULES<0x20>
resolve_wins: Attempting wins lookup for name HERCULES<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name HERCULES<0x20>
Connecting to 192.168.0.114 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\GALAXY                        Tera-Byte File Server -- Primary
Connecting to host=GALAXY
resolve_lmhosts: Attempting lmhosts lookup for name GALAXY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name GALAXY<0x20>
resolve_wins: Attempting wins lookup for name GALAXY<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name GALAXY<0x20>
resolve_hosts: getaddrinfo failed for name GALAXY [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name GALAXY<0x20>
Got a positive name query response from 192.168.0.11 ( 192.168.0.11 )
Connecting to 192.168.0.11 at port 445
Connecting to 192.168.0.11 at port 139
                \\GALAXY\ADMIN$                 IPC Service (Tera-Byte File Server -- Primary)
                \\GALAXY\IPC$                   IPC Service (Tera-Byte File Server -- Primary)
                \\GALAXY\Music                  Share Your Music CDs With Your Buds
                \\GALAXY\Download               Files Downloaded Once - Used Many Times
                \\GALAXY\Code                   Old DOS Programs And Application Share
                \\GALAXY\Document               Read-Only Document Share
                \\GALAXY\projects               Company Wide Project Share
                \\GALAXY\info                   TeraStation utilities
        \\FALCON                        falcon server (Samba, Ubuntu)
Connecting to host=FALCON
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_wins: Attempting wins lookup for name FALCON<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name FALCON<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\FALCON\IPC$                   IPC Service (falcon server (Samba, Ubuntu))
                \\FALCON\accounting             ATS Accounting File Server
                \\FALCON\projects               ATS General File Server
                \\FALCON\print$                 Printer Drivers
        \\CAM2
Connecting to host=CAM2
resolve_lmhosts: Attempting lmhosts lookup for name CAM2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CAM2<0x20>
resolve_wins: Attempting wins lookup for name CAM2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CAM2<0x20>
resolve_hosts: getaddrinfo failed for name CAM2 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CAM2<0x20>
Got a positive name query response from 192.168.0.35 ( 192.168.0.35 )
Connecting to 192.168.0.35 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\BRNDD1EFA
Connecting to host=BRNDD1EFA
resolve_lmhosts: Attempting lmhosts lookup for name BRNDD1EFA<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BRNDD1EFA<0x20>
resolve_wins: Attempting wins lookup for name BRNDD1EFA<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BRNDD1EFA<0x20>
Connecting to 192.168.0.116 at port 445
Connecting to 192.168.0.116 at port 139
Error connecting to 192.168.0.116 (Connection refused)
cli_start_connection: failed to connect to BRNDD1EFA<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED



```

---

### Post by redmk2 on 2013-07-05
> **RyanBiggs said:**
> Hi [COLOR=#000000]redmk2,[/COLOR]

The output of [COLOR=#000000][FONT=Ubuntu Mono]smbtree -d3 that seems to pertain to the server in question shows:[/FONT][/COLOR]

```
        \\FALCON                        falcon server (Samba, Ubuntu)
Connecting to host=FALCON
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_wins: Attempting wins lookup for name FALCON<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name FALCON<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\FALCON\IPC$                   IPC Service (falcon server (Samba, Ubuntu))
                \\FALCON\accounting             ATS Accounting File Server
                \\FALCON\projects               ATS General File Server
                \\FALCON\print$                 Printer Drivers

```


You must be using the command from the computer named FALCON.  This shows a problem networking problem right off the bat.  The IP address 127.0.1.1 is only seen by the local host.  So this machine is misconfigured.  Hopefully you have a wired Ethernet card and a fixed IP address for that NIC.  Post the output of this:```
ifconfig |grep inet
```
> 

The following is the complete output, some of which is obviously from other shares, servers, and workstations:

```
lp_load_ex: refreshing parametersInitialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::21f:d0ff:fe99:c809%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter falcon's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ATS<0x1d>
Got a positive name query response from 192.168.0.3 ( 192.168.0.3 )
Connecting to host=192.168.0.3
Connecting to 192.168.0.3 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.3 ( 192.168.0.3 )
Got a positive name query response from 192.168.0.7 ( 192.168.0.7 )
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
Connecting to host=192.168.0.129
Connecting to 192.168.0.129 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
Connecting to host=192.168.0.129
Connecting to 192.168.0.129 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\TESTOPS-PC
Connecting to host=TESTOPS-PC
resolve_lmhosts: Attempting lmhosts lookup for name TESTOPS-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TESTOPS-PC<0x20>
resolve_wins: Attempting wins lookup for name TESTOPS-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TESTOPS-PC<0x20>
Connecting to 192.168.0.110 at port 445
Connecting to 192.168.0.110 at port 139
Error connecting to 192.168.0.110 (Success)
cli_start_connection: failed to connect to TESTOPS-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
        \\OTTER
Connecting to host=OTTER
resolve_lmhosts: Attempting lmhosts lookup for name OTTER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name OTTER<0x20>
resolve_wins: Attempting wins lookup for name OTTER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name OTTER<0x20>
resolve_hosts: getaddrinfo failed for name OTTER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name OTTER<0x20>
Got a positive name query response from 192.168.0.55 ( 192.168.0.55 )
Connecting to 192.168.0.55 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\OEM-RHSYHZ66QEP
Connecting to host=OEM-RHSYHZ66QEP
resolve_lmhosts: Attempting lmhosts lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_wins: Attempting wins lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name OEM-RHSYHZ66QEP<0x20>
resolve_hosts: getaddrinfo failed for name OEM-RHSYHZ66QEP [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name OEM-RHSYHZ66QEP<0x20>
Got a positive name query response from 192.168.0.129 ( 192.168.0.129 )
Connecting to 192.168.0.129 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\LANCASTER
Connecting to host=LANCASTER
resolve_lmhosts: Attempting lmhosts lookup for name LANCASTER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LANCASTER<0x20>
resolve_wins: Attempting wins lookup for name LANCASTER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LANCASTER<0x20>
Connecting to 192.168.0.123 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
ATSMFG
resolve_lmhosts: Attempting lmhosts lookup for name ATSMFG<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ATSMFG<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ATSMFG<0x1d>
Got a positive name query response from 192.168.0.7 ( 192.168.0.7 )
Connecting to host=192.168.0.7
Connecting to 192.168.0.7 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\MFG                           mfg server (Samba, Ubuntu)
Connecting to host=MFG
resolve_lmhosts: Attempting lmhosts lookup for name MFG<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MFG<0x20>
resolve_wins: Attempting wins lookup for name MFG<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MFG<0x20>
Connecting to 192.168.0.7 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\MFG\print$            Printer Drivers
                \\MFG\authority         ATS Manufacturing Authority Data
                \\MFG\engineering       ATS Manufacturing Engineering Data
                \\MFG\IPC$              IPC Service (mfg server (Samba, Ubuntu))
ATS
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name ATS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name ATS<0x1d>
Got a positive name query response from 192.168.0.3 ( 192.168.0.3 )
Connecting to host=192.168.0.3
Connecting to 192.168.0.3 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\VF8                           MS-DOS Peer Server
Connecting to host=VF8
resolve_lmhosts: Attempting lmhosts lookup for name VF8<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name VF8<0x20>
resolve_wins: Attempting wins lookup for name VF8<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name VF8<0x20>
resolve_hosts: getaddrinfo failed for name VF8 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name VF8<0x20>
Got a positive name query response from 192.168.0.18 ( 192.168.0.18 )
Connecting to 192.168.0.18 at port 445
Connecting to 192.168.0.18 at port 139
Server requested plaintext password but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED
        \\STARLIFTER                    TeraByte File Server -- Secondary
Connecting to host=STARLIFTER
resolve_lmhosts: Attempting lmhosts lookup for name STARLIFTER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name STARLIFTER<0x20>
resolve_wins: Attempting wins lookup for name STARLIFTER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name STARLIFTER<0x20>
Connecting to 192.168.0.12 at port 445
Connecting to 192.168.0.12 at port 139
                \\STARLIFTER\ADMIN$             IPC Service (TeraByte File Server -- Secondary)
                \\STARLIFTER\IPC$               IPC Service (TeraByte File Server -- Secondary)
                \\STARLIFTER\projects           ATS Eagle Project Server Backup - New 2013
                \\STARLIFTER\SVN_Backup         Backup for Project Subversion Server
                \\STARLIFTER\Code               Old DOS Programs And Application Share
                \\STARLIFTER\info               TeraStation utilities
        \\PROJECT                       G-Code Server
Connecting to host=PROJECT
resolve_lmhosts: Attempting lmhosts lookup for name PROJECT<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PROJECT<0x20>
resolve_wins: Attempting wins lookup for name PROJECT<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PROJECT<0x20>
Connecting to 192.168.0.2 at port 445
Connecting to 192.168.0.2 at port 139
cli_session_setup: NT1 session setup failed: NT_STATUS_LOGON_FAILURE
                \\PROJECT\ADMIN$                IPC Service (G-Code Server)
                \\PROJECT\IPC$                  IPC Service (G-Code Server)
                \\PROJECT\CODE                  For CNC Machine Code
        \\PEACEMAKER                    Workstation
Connecting to host=PEACEMAKER
resolve_lmhosts: Attempting lmhosts lookup for name PEACEMAKER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PEACEMAKER<0x20>
resolve_wins: Attempting wins lookup for name PEACEMAKER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PEACEMAKER<0x20>
Connecting to 192.168.0.125 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\HERCULES                      hercules
Connecting to host=HERCULES
resolve_lmhosts: Attempting lmhosts lookup for name HERCULES<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name HERCULES<0x20>
resolve_wins: Attempting wins lookup for name HERCULES<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name HERCULES<0x20>
Connecting to 192.168.0.114 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\GALAXY                        Tera-Byte File Server -- Primary
Connecting to host=GALAXY
resolve_lmhosts: Attempting lmhosts lookup for name GALAXY<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name GALAXY<0x20>
resolve_wins: Attempting wins lookup for name GALAXY<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name GALAXY<0x20>
resolve_hosts: getaddrinfo failed for name GALAXY [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name GALAXY<0x20>
Got a positive name query response from 192.168.0.11 ( 192.168.0.11 )
Connecting to 192.168.0.11 at port 445
Connecting to 192.168.0.11 at port 139
                \\GALAXY\ADMIN$                 IPC Service (Tera-Byte File Server -- Primary)
                \\GALAXY\IPC$                   IPC Service (Tera-Byte File Server -- Primary)
                \\GALAXY\Music                  Share Your Music CDs With Your Buds
                \\GALAXY\Download               Files Downloaded Once - Used Many Times
                \\GALAXY\Code                   Old DOS Programs And Application Share
                \\GALAXY\Document               Read-Only Document Share
                \\GALAXY\projects               Company Wide Project Share
                \\GALAXY\info                   TeraStation utilities
        \\FALCON                        falcon server (Samba, Ubuntu)
Connecting to host=FALCON
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_wins: Attempting wins lookup for name FALCON<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name FALCON<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\FALCON\IPC$                   IPC Service (falcon server (Samba, Ubuntu))
                \\FALCON\accounting             ATS Accounting File Server
                \\FALCON\projects               ATS General File Server
                \\FALCON\print$                 Printer Drivers
        \\CAM2
Connecting to host=CAM2
resolve_lmhosts: Attempting lmhosts lookup for name CAM2<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CAM2<0x20>
resolve_wins: Attempting wins lookup for name CAM2<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CAM2<0x20>
resolve_hosts: getaddrinfo failed for name CAM2 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CAM2<0x20>
Got a positive name query response from 192.168.0.35 ( 192.168.0.35 )
Connecting to 192.168.0.35 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
        \\BRNDD1EFA
Connecting to host=BRNDD1EFA
resolve_lmhosts: Attempting lmhosts lookup for name BRNDD1EFA<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BRNDD1EFA<0x20>
resolve_wins: Attempting wins lookup for name BRNDD1EFA<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BRNDD1EFA<0x20>
Connecting to 192.168.0.116 at port 445
Connecting to 192.168.0.116 at port 139
Error connecting to 192.168.0.116 (Connection refused)
cli_start_connection: failed to connect to BRNDD1EFA<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED



```

There are plenty of computers and lots of errors such as ```

cli_start_connection: failed to connect to TESTOPS-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

resolve_hosts: getaddrinfo failed for name OEM-RHSYHZ66QEP [Name or service not known]

resolve_hosts: getaddrinfo failed for name VF8 [Name or service not known]

Server requested plaintext password but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED

resolve_hosts: getaddrinfo failed for name GALAXY [Name or service not known]

Error connecting to 192.168.0.116 (Connection refused)
cli_start_connection: failed to connect to BRNDD1EFA<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED


```
The command smbtree lists ALL of the CIFS servers on the LAN (both Linux and Windows) What you see is all the errors from all the machines.

I think that the best way to handle all of this is to establish one successful Samba server.  How many of these are Windows machines and how many are Linux?  Do you control all of these (administrator)?  Falcon may be the easiest one to fix once I know that the address is fixed and it is in the IP network of 192.168.0.0 /24.

---

### Post by RyanBiggs on 2013-07-05
The output of [COLOR=#000000][FONT=Ubuntu Mono]ifconfig |grep inet [/FONT][/COLOR]on Falcon is the following:

```
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe99:c809/64 Scope:Link
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host



```

If I run smbtree from a different computer than falcon, the falcon section is:

```
\\FALCON                        falcon server (Samba, Ubuntu)Connecting to host=FALCON
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name FALCON<0x20>
resolve_wins: Attempting wins lookup for name FALCON<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name FALCON<0x20>
Connecting to 192.168.0.3 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\FALCON\IPC$                   IPC Service (falcon server (Samba, Ubuntu))
                \\FALCON\accounting             ATS Accounting File Server
                \\FALCON\projects               ATS General File Server
                \\FALCON\print$                 Printer Drivers



```


There are indeed many other computers on the network, but only a few are intended to be operational Samba servers and many others are windows laptops (TESTOPS-PC) and other "junk". VF8 is a CNC mill that apparently has some sort of samba server running. [COLOR=#000000][FONT=Ubuntu Mono]BRNDD1EFA [/FONT][/COLOR]is a printer. MFG is an operational Ubuntu Samba server (with user authorization enabled) which works great. The "open" share on falcon is operational and works great. Practically speaking, I'm the "administrator" of all this junk.

---

### Post by redmk2 on 2013-07-05
> **RyanBiggs said:**
> There are indeed many other computers on the network, but only a few are intended to be operational Samba servers and many others are windows laptops (TESTOPS-PC) and other "junk". VF8 is a CNC mill that apparently has some sort of samba server running. [COLOR=#000000][FONT=Ubuntu Mono]BRNDD1EFA [/FONT][/COLOR]is a printer. MFG is an operational Ubuntu Samba server (with user authorization enabled) which works great. The "open" share on falcon is operational and works great. Practically speaking, I'm the "administrator" of all this junk.

I see the IP address now.   It's 192.168.0.3.

Any host that is sharing directories (a share) is a Samba server.  It doesn't matter what hardware it is using.  This includes the printer which is most likely sharing only printer drivers.

I'm curious so let's make another of those big 'ol long replies.  Post the output of ```
cat /etc/samba/smb.con

```

I wonder if you need to explicitly allow users using: valid user = falcon, <other names>  or: valid user @<a common user group>.  I just noticed that you have not done that when you removed the: guest only = yes   -- I'm a bit confused with all the postings -- am I correct in my thought here?

---

### Post by RyanBiggs on 2013-07-05
> [COLOR=#000000]Any host that is sharing directories (a share) is a Samba server. It doesn't matter what hardware it is using. This includes the printer which is most likely sharing only printer drivers.[/COLOR]

Sure, I follow you there...

I did try adding a "valid users" entry in smb.conf, as you can see in the following. Still no joy connecting to the guest ok = no ("accounting") share with that user (rbiggs):

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ATS


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
   max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user


# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam


   obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user


########## Domains ###########


# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the
# SAMR RPC pipe.
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.
; add group script = /usr/sbin/addgroup --force-badname %g


########## Printing ##########


# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes


# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap


# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY


# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &


# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes


# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
[projects]
    comment = ATS General File Server
    path = /srv/falcon/projects
    browsable = yes
    create mask = 0755
    guest ok = yes
    read only = no


[accounting]
    comment = ATS Accounting File Server
    path = /srv/falcon/accounting
    browsable = yes
    create mask = 0755
    guest ok = no
    read only = no
    valid users = rbiggs

```

---

### Post by redmk2 on 2013-07-05
Did you restart the smbd daemon?

```
sudo service smbd restart 
```

---

### Post by RyanBiggs on 2013-07-05
> [COLOR=#000000]Did you restart the smbd daemon?[/COLOR]

Yes, but I usually do so with

```
sudo restart smbd
sudo restart nmbd
```

I did try

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo service smbd restart[/FONT][/COLOR]
```

just to be sure. Not sure if there's any difference in practice...

---

### Post by redmk2 on 2013-07-06
There is no difference.  Either way seems to work.

I have a feeling that the file system permissions are going to be the culprit.  I don't see anything wrong with the smb.conf file.  I wuld check the permissions along the entire path from / to /srv/falcon/<the directory>.  The user should have execute permission along the entire directory path in some way as either the user or a member of the group or at least the others execute bit should be set.  Note this is only on the directories in the path.  The files permissions are another thing entirely.

---

### Post by RyanBiggs on 2013-07-06
> [COLOR=#000000] I wuld check the permissions along the entire path from / to /srv/falcon/<the directory>. The user should have execute permission along the entire directory path in some way as either the user or a member of the group or at least the others execute bit should be set.[/COLOR]

That was my thought early on as well, but the execute permissions were all set -- just to be extra sure, I set the directory permissions wide open (0777) from srv on down just to be sure (yeah I know, bad idea lol). Still no dice.

Pretty mysterious. Is there a way to see more detail about what is going wrong in the authentication process? The Samba logs I looked at didn't seem to indicate much. I also might think about connecting from another Ubuntu box instead of Windows but need to look into how best to do that. mount -t cifs, or is there a better way to test?

---

### Post by RyanBiggs on 2013-07-06
**OOPS --**now this is a "sorry to waste your time" moment -- I was trying with two different Windows computers, neither of which could get into the share. Somewhere along the way, I must have fixed the problem (unix permissions perhaps?), but those two computers still won't log in though they ask for credentials on each attempt. But I went and tried some completely different Windows computers, and they work!

It's another question why the Windows PCs don't see the share as-is, but I bet they will after a reboot. I should have known Windows was more likely the problem than Linux!

Thanks for all the help redmk2, and sorry again to have you on a wild goose chase!

---

### Post by redmk2 on 2013-07-07
> **RyanBiggs said:**
> **OOPS --**now this is a "sorry to waste your time" moment -- I was trying with two different Windows computers, neither of which could get into the share. Somewhere along the way, I must have fixed the problem (unix permissions perhaps?), but those two computers still won't log in though they ask for credentials on each attempt. But I went and tried some completely different Windows computers, and they work!

It's another question why the Windows PCs don't see the share as-is, but I bet they will after a reboot. I should have known Windows was more likely the problem than Linux!

Thanks for all the help redmk2, and sorry again to have you on a wild goose chase!

Doh!  I don't know how many times I've been caught like you.  I try and remember that if I'm dealing with Windows that the first thing you do is reboot the dang thing!  :D  At least you finally resolved the issue.

---

