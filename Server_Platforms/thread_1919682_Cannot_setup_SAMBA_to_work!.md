---
title: "Cannot setup SAMBA to work!"
date: 2012-02-03
forum: Server Platforms
---

### Post by MakroSiroki on 2012-02-03
Hello!

I am getting desperated, since I cannot setup SAMBA as PDC and join Windows 7 machine into domain. Can someone explain me, why? Here is error (after command  **clear && net rpc join -d10 -S PDC -U root**:> [2012/02/03 14:58:12,  5] lib/debug.c:405(debug_dump_status)
  INFO: Current debug levels:
    all: True/10
    tdb: False/0
    printdrivers: False/0
    lanman: False/0
    smb: False/0
    rpc_parse: False/0
    rpc_srv: False/0
    rpc_cli: False/0
    passdb: False/0
    sam: False/0
    auth: False/0
    winbind: False/0
    vfs: False/0
    idmap: False/0
    quota: False/0
    acls: False/0
    locking: False/0
    msdfs: False/0
    dmapi: False/0
    registry: False/0
[2012/02/03 14:58:12,  3] param/loadparm.c:9169(lp_load_ex)
  lp_load_ex: refreshing parameters
[2012/02/03 14:58:12,  3] param/loadparm.c:4939(init_globals)
  Initialising global parameters
[2012/02/03 14:58:12,  2] param/loadparm.c:4798(max_open_files)
  rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
[2012/02/03 14:58:12.980251,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2012/02/03 14:58:12.980270,  3] param/loadparm.c:7853(do_section)
  Processing section "[global]"
  doing parameter protocol = NT1
  doing parameter domain master = yes
  doing parameter winbind trusted domains only = yes
  doing parameter winbind use default domain = yes
  doing parameter wins support = true
  doing parameter netbios name = KILIMANJARO
[2012/02/03 14:58:12.980343,  4] param/loadparm.c:7215(handle_netbios_name)
  handle_netbios_name: set global_myname to: KILIMANJARO
  doing parameter server string = Zenit MS Real Samba PDC
  doing parameter writable = no
  doing parameter path = /var/spool/samba
  doing parameter workgroup = MOUNTAINS
  doing parameter os level = 33
  doing parameter winbind enum groups = no
  doing parameter security = domain
  doing parameter preferred master = yes
  doing parameter domain logons = yes
  doing parameter password server = KILIMANJARO
[2012/02/03 14:58:12.980425,  4] param/loadparm.c:9204(lp_load_ex)
  pm_process() returned Yes
[2012/02/03 14:58:12.980435,  7] param/loadparm.c:9410(lp_servicenumber)
  lp_servicenumber: couldn't find homes
[2012/02/03 14:58:12.980444,  1] param/loadparm.c:8387(set_server_role)
  Server's Role (logon server) NOT ADVISED with domain-level security
[2012/02/03 14:58:12.980451, 10] param/loadparm.c:8414(set_server_role)
  set_server_role: role = ROLE_DOMAIN_BDC
[2012/02/03 14:58:12.980463,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS-2LE
[2012/02/03 14:58:12.980471,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS-2LE
[2012/02/03 14:58:12.980478,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-16LE
[2012/02/03 14:58:12.980487,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-16LE
[2012/02/03 14:58:12.980494,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS-2BE
[2012/02/03 14:58:12.980501,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS-2BE
[2012/02/03 14:58:12.980508,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-16BE
[2012/02/03 14:58:12.980515,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-16BE
[2012/02/03 14:58:12.980521,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF8
[2012/02/03 14:58:12.980528,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF8
[2012/02/03 14:58:12.980535,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-8
[2012/02/03 14:58:12.980541,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-8
[2012/02/03 14:58:12.980548,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset ASCII
[2012/02/03 14:58:12.980556,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset ASCII
[2012/02/03 14:58:12.980562,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset 646
[2012/02/03 14:58:12.980570,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset 646
[2012/02/03 14:58:12.980577,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset ISO-8859-1
[2012/02/03 14:58:12.980589,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset ISO-8859-1
[2012/02/03 14:58:12.980596,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS2-HEX
[2012/02/03 14:58:12.980604,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS2-HEX
[2012/02/03 14:58:12.980621,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980795,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980822,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980835,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980850,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980862,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980874,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980891,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980905,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980917,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980943,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.980983,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.981006,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.981031,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/03 14:58:12.981063,  5] lib/util.c:276(init_names)
  Netbios name list:-
  my_netbios_names[0]="KILIMANJARO"
[2012/02/03 14:58:12.981221,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=fe80::219:66ff:feef:2559%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
[2012/02/03 14:58:12.981309,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=192.168.100.101 bcast=192.168.100.255 netmask=255.255.255.0
lp_load_ex: refreshing parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter protocol = NT1
doing parameter domain master = yes
doing parameter winbind trusted domains only = yes
doing parameter winbind use default domain = yes
doing parameter wins support = true
doing parameter netbios name = KILIMANJARO
handle_netbios_name: set global_myname to: KILIMANJARO
doing parameter server string = Zenit MS Real Samba PDC
doing parameter writable = no
doing parameter path = /var/spool/samba
doing parameter workgroup = MOUNTAINS
doing parameter os level = 33
doing parameter winbind enum groups = no
doing parameter security = domain
doing parameter preferred master = yes
doing parameter domain logons = yes
doing parameter password server = KILIMANJARO
pm_process() returned Yes
lp_servicenumber: couldn't find homes
Server's Role (logon server) NOT ADVISED with domain-level security
set_server_role: role = ROLE_DOMAIN_BDC
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Netbios name list:-
my_netbios_names[0]="KILIMANJARO"
added interface eth0 ip=fe80::219:66ff:feef:2559%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.100.101 bcast=192.168.100.255 netmask=255.255.255.0
Opening cache file at /var/run/samba/gencache.tdb
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
Cache entry with key = AD_SITENAME/DOMAIN/ couldn't be found 
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up PDC#20 (sitename (null))
Cache entry with key = NBT/PDC#20 couldn't be found 
no entry for PDC#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name PDC<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name PDC<0x20>
Cache entry with key = WINS_SRV_DEAD/127.0.0.1,0.0.0.0 couldn't be found 
wins_srv_is_dead: 127.0.0.1 is alive
resolve_wins: using WINS server 127.0.0.1 and tag '*'
bind succeeded on port 0
Sending a packet of len 50 to (127.0.0.1) on port 137
read_udp_v4_socket: ip 127.0.0.1 port 35072 read: 56
parse_nmb: packet id = 11724
Received a packet of len 56 from (127.0.0.1) port 137
nmb packet from 127.0.0.1(137) header: id=11724 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=3 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=PDC<20> rr_type=10 rr_class=1 ttl=0
Negative name query response, rcode 0x03: The name requested does not exist.
resolve_hosts: Attempting host lookup for name PDC<0x20>
resolve_hosts: getaddrinfo failed for name PDC [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name PDC<0x20>
bind succeeded on port 0
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 126976
    SO_RCVBUF = 126976
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.100.255) on port 137
Sending a packet of len 50 to (192.168.100.255) on port 137
Sending a packet of len 50 to (192.168.100.255) on port 137
Unable to resolve server name
lang_tdb_init: /usr/share/samba/en_US:en.msg: No such file or directory
Unable to find a suitable server for domain MOUNTAINS
failed to make ipc connection: NT_STATUS_UNSUCCESSFUL
Cache entry with key = AD_SITENAME/DOMAIN/ couldn't be found 
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up PDC#20 (sitename (null))
Cache entry with key = NBT/PDC#20 couldn't be found 
no entry for PDC#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name PDC<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name PDC<0x20>
Cache entry with key = WINS_SRV_DEAD/127.0.0.1,0.0.0.0 couldn't be found 
wins_srv_is_dead: 127.0.0.1 is alive
resolve_wins: using WINS server 127.0.0.1 and tag '*'
bind succeeded on port 0
Sending a packet of len 50 to (127.0.0.1) on port 137
read_udp_v4_socket: ip 127.0.0.1 port 35072 read: 56
parse_nmb: packet id = 23382
Received a packet of len 56 from (127.0.0.1) port 137
nmb packet from 127.0.0.1(137) header: id=23382 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=3 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=PDC<20> rr_type=10 rr_class=1 ttl=0
Negative name query response, rcode 0x03: The name requested does not exist.
resolve_hosts: Attempting host lookup for name PDC<0x20>
resolve_hosts: getaddrinfo failed for name PDC [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name PDC<0x20>
bind succeeded on port 0
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 126976
    SO_RCVBUF = 126976
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.100.255) on port 137
Sending a packet of len 50 to (192.168.100.255) on port 137
Sending a packet of len 50 to (192.168.100.255) on port 137
Unable to resolve server name
Unable to find a suitable server for domain MOUNTAINS
return code = 1
tdb(/var/run/samba/gencache.tdb): tdb_transaction_start: cannot start a transaction on a read-only or internal db
Could not start transaction on gencache.tdb: Invalid parameter

---

### Post by luvshines on 2012-02-04
Have you tried it with PDC's IP address instead of the hostname

---

### Post by MakroSiroki on 2012-02-04
> **luvshines said:**
> Have you tried it with PDC's IP address instead of the hostnameNope, where do I put ip instead of hostname, in /etc/samba/smb.conf?

Here is my current smb.conf:```
[global]
    protocol = NT1
    socket options = TCP_NODELAY
    domain master = yes
    winbind trusted domains only = yes
    winbind use default domain = yes
    wins support = true
    netbios name = KILIMANJARO
    server string = Zenit MS Real Samba PDC
    writable = no
    password server = KILIMANJARO
    path = /var/spool/samba
    workgroup = MOUNTAINS
    os level = 33
    winbind enum groups = no
    security = domain
    preferred master = yes
    domain logons = yes

[domains]
    logon path             = \\%N\%U\profile
    logon drive            = H:
    logon home             = \\%N\%U
    logon script            = logon.cmd
    add machine script        = sudo /usr/sbin/useradd -N -g machines -c Machine -d /var/lib/samba -s /bin/false %u

[netlogon]
    comment                = "Zenit MS Real Samba PDC Logon Scripts and other profile data"
    path                = /etc/samba/netlogon
    guest ok            = no
    read only            = yes
    share modes            = no

[homes]
    comment                = "Home directory for U%"
    writable            = yes
    browseable             = no
    read only             = no
    create mask             = 0700
    directory mask             = 0700
    valid users             = %S

[share]
    comment                = "Zenit MS Real Samba File Server Share"
    path                = /srv/samba/share
    guest ok            = no
    read only            = no
    create mask            = 0777

[printers]
    browsable            = yes
    guest ok            = no
    printable            = yes
    available            = yes

[MP280]
    printer = Canon_MP280_series
    comment = Canon Pixma MP280
    printable = yes

[e120]
    printer = Lexmark_Lexmark_E120
    comment = Lexmark E120
    printable = yes
```

---

### Post by luvshines on 2012-02-04
In the smb.conf file, you have mentioned KILIMANJARO as 'password server'
Is the server reachable by this name ? Can you ping it by this name ?

If yes, then try  'KILIMANJARO' in the -S field of 'net rpc' command you are hitting
Else try replacing both fields by IP address

---

### Post by MakroSiroki on 2012-02-04
> **luvshines said:**
> In the smb.conf file, you have mentioned KILIMANJARO as 'password server'
Is the server reachable by this name ? Can you ping it by this name ?

If yes, then try  'KILIMANJARO' in the -S field of 'net rpc' command you are hitting
Else try replacing both fields by IP addressYes, I can ping server KILIMANJARO:> Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\markofr>ping KILIMANJARO

Pinging KILIMANJARO [192.168.100.101] with 32 bytes of data:
Reply from 192.168.100.101: bytes=32 time=1ms TTL=64
Reply from 192.168.100.101: bytes=32 time<1ms TTL=64
Reply from 192.168.100.101: bytes=32 time<1ms TTL=64
Reply from 192.168.100.101: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.100.101:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 1ms, Average = 0ms

C:\Users\markofr>

---

### Post by luvshines on 2012-02-04
Ok

Try net rpc command with 'sudo' or root user (if not already doing it) and -S 'KILIMANJARO'

---

### Post by MakroSiroki on 2012-02-04
> **luvshines said:**
> Ok

Try net rpc command with 'sudo' or root user (if not already doing it) and -S 'KILIMANJARO'I've run following command:```
clear && sudo net rpc join -d10 -S 192.168.100.101 -U root
```I've changed -S paramater value from KILIMANJARO to KILIMANJARO's IP (192.168.100.101) and now I get  following errors, which are included in attached file!

---

### Post by luvshines on 2012-02-05
> **MakroSiroki said:**
> I've run following command:```
clear && sudo net rpc join -d10 -S 192.168.100.101 -U root
```I've changed -S paramater value from KILIMANJARO to KILIMANJARO's IP (192.168.100.101) and now I get  following errors, which are included in attached file!

Ah! 'no such user' error

Did you add 'root' user to Samba on the SAMBA PDC ?> 'smbpasswd -a root'

---

### Post by MakroSiroki on 2012-02-05
> **luvshines said:**
> Ah! 'no such user' error

Did you add 'root' user to Samba on the SAMBA PDC ?Yes, I have, I've also enabled debug level 10 and now that is what I get once I try to add root to PDC (I think user root had been added ok):> installer@kilimanjaro:~$ sudo smbpasswd -aD10 root
Netbios name list:-
my_netbios_names[0]="KILIMANJARO"
Attempting to register passdb backend ldapsam
Successfully added passdb backend 'ldapsam'
Attempting to register passdb backend ldapsam_compat
Successfully added passdb backend 'ldapsam_compat'
Attempting to register passdb backend NDS_ldapsam
Successfully added passdb backend 'NDS_ldapsam'
Attempting to register passdb backend NDS_ldapsam_compat
Successfully added passdb backend 'NDS_ldapsam_compat'
Attempting to register passdb backend smbpasswd
Successfully added passdb backend 'smbpasswd'
Attempting to register passdb backend tdbsam
Successfully added passdb backend 'tdbsam'
Attempting to register passdb backend wbc_sam
Successfully added passdb backend 'wbc_sam'
Attempting to find a passdb backend to match smbpasswd (smbpasswd)
Found pdb backend smbpasswd
pdb backend smbpasswd has a valid init
New SMB password:
Retype new SMB password:
getsampwnam (smbpasswd): search by name: root
startsmbfilepwent_internal: opening file /etc/samba/smbpasswd
getsmbfilepwent: LM password for user root invalidated
getsmbfilepwent: returning passwd entry for user root, uid 0
endsmbfilepwent_internal: closed password file.
getsampwnam (smbpasswd): found by name: root
Finding user root
Trying _Get_Pwnam(), username as lowercase is root
Get_Pwnam_internals did find user [root]!
pdb_set_username: setting username root, was
pdb_set_full_name: setting full name root, was
pdb_set_domain: setting domain MOUNTAINS, was
Home server: kilimanjaro
pdb_set_profile_path: setting profile path \\kilimanjaro\root\profile, was
Home server: kilimanjaro
pdb_set_homedir: setting home dir \\kilimanjaro\root, was
pdb_set_dir_drive: setting dir drive , was NULL
pdb_set_logon_script: setting logon script , was
pdb_set_user_sid: setting user sid S-1-5-21-1876437633-3346474330-1414540629-1000
pdb_set_user_sid_from_rid:
        setting user sid S-1-5-21-1876437633-3346474330-1414540629-1000 from rid 1000
account_policy_get: name: maximum password age, val: -1
Opening cache file at /var/run/samba/gencache.tdb
Opening cache file at /var/run/samba/gencache_notrans.tdb
Cache entry with key = IDMAP/GID2SID/0 couldn't be found
gid_to_sid: winbind failed to find a sid for gid 0
LEGACY: gid 0 -> sid S-1-5-21-1876437633-3346474330-1414540629-512
account_policy_get: name: password history, val: 0
pdb_set_username: setting username root, was
pdb_set_domain: setting domain MOUNTAINS, was
pdb_set_nt_username: setting nt username , was
pdb_set_full_name: setting full name root, was
Home server: kilimanjaro
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
pdb_set_homedir: setting home dir \\kilimanjaro\root, was
pdb_set_dir_drive: setting dir drive , was NULL
pdb_set_logon_script: setting logon script , was
Home server: kilimanjaro
pdb_set_profile_path: setting profile path \\kilimanjaro\root\profile, was
pdb_set_workstations: setting workstations , was
account_policy_get: name: password history, val: 0
pdb_set_user_sid: setting user sid S-1-5-21-1876437633-3346474330-1414540629-1000
pdb_set_user_sid_from_rid:
        setting user sid S-1-5-21-1876437633-3346474330-1414540629-1000 from rid 1000
Cache entry with key = IDMAP/SID2GID/S-1-5-21-1876437633-3346474330-1414540629-512 couldn't be found
winbind failed to find a gid for sid S-1-5-21-1876437633-3346474330-1414540629-512
lookup_global_sam_rid: looking up RID 512.
smbpasswd_getsampwrid: search by sid: S-1-5-21-1876437633-3346474330-1414540629-512
startsmbfilepwent_internal: opening file /etc/samba/smbpasswd
getsmbfilepwent: LM password for user root invalidated
getsmbfilepwent: returning passwd entry for user root, uid 0
getsmbfilepwent: end of file reached.
endsmbfilepwent_internal: closed password file.
LEGACY: sid S-1-5-21-1876437633-3346474330-1414540629-512 -> gid 0
pdb_set_group_sid: setting group sid S-1-5-21-1876437633-3346474330-1414540629-512
account_policy_get: name: password history, val: 0
mod_smbfilepwd_entry: opening file /etc/samba/smbpasswd
mod_smbfilepwd_entry: entry exists for user rootAnd when I try to join the domain with existing SAMBA's root acount, I get error as seen in attachment .png screenshot.

---

### Post by MakroSiroki on 2012-02-07
I've managed to join SMABA PDC box into it's DOMAIN:```
installer@kilimanjaro:~$ sudo net rpc join -d10 -S KILIMANJARO -U root 2>log.txt
Enter root's password:
Joined domain MOUNTAINS.
installer@kilimanjaro:~$
```Here is the log:> [2012/02/07 11:55:32,  5] lib/debug.c:405(debug_dump_status)
  INFO: Current debug levels:
    all: True/10
    tdb: False/0
    printdrivers: False/0
    lanman: False/0
    smb: False/0
    rpc_parse: False/0
    rpc_srv: False/0
    rpc_cli: False/0
    passdb: False/0
    sam: False/0
    auth: False/0
    winbind: False/0
    vfs: False/0
    idmap: False/0
    quota: False/0
    acls: False/0
    locking: False/0
    msdfs: False/0
    dmapi: False/0
    registry: False/0
[2012/02/07 11:55:32,  3] param/loadparm.c:9169(lp_load_ex)
  lp_load_ex: refreshing parameters
[2012/02/07 11:55:32,  3] param/loadparm.c:4939(init_globals)
  Initialising global parameters
[2012/02/07 11:55:32,  2] param/loadparm.c:4798(max_open_files)
  rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
[2012/02/07 11:55:32.284602,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2012/02/07 11:55:32.284621,  3] param/loadparm.c:7853(do_section)
  Processing section "[global]"
  doing parameter logon drive = H:
  doing parameter domain master = yes
  doing parameter winbind trusted domains only = yes
  doing parameter winbind use default domain = yes
  doing parameter logon home = \\%N\%U
  doing parameter passdb backend = smbpasswd
  doing parameter wins support = true
  doing parameter netbios name = KILIMANJARO
[2012/02/07 11:55:32.284705,  4] param/loadparm.c:7215(handle_netbios_name)
  handle_netbios_name: set global_myname to: KILIMANJARO
  doing parameter server string = Zenit MS Real Samba PDC
  doing parameter writable = no
  doing parameter logon script = logon.cmd
  doing parameter password server = KILIMANJARO
  doing parameter winbind enum users = no
  doing parameter path = /var/spool/samba
  doing parameter workgroup = MOUNTAINS
  doing parameter logon path = \\%N\%U\profile
  doing parameter winbind enum groups = no
  doing parameter os level = 33
  doing parameter security = user
  doing parameter preferred master = yes
  doing parameter add machine script = sudo /usr/sbin/useradd -N -g machines -c Machine -d /var/lib/samba -s /bin/false %u
  doing parameter domain logons = yes
[2012/02/07 11:55:32.284817,  4] param/loadparm.c:9204(lp_load_ex)
  pm_process() returned Yes
[2012/02/07 11:55:32.284827,  7] param/loadparm.c:9410(lp_servicenumber)
  lp_servicenumber: couldn't find homes
[2012/02/07 11:55:32.284835, 10] param/loadparm.c:8414(set_server_role)
  set_server_role: role = ROLE_DOMAIN_PDC
[2012/02/07 11:55:32.284847,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS-2LE
[2012/02/07 11:55:32.284855,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS-2LE
[2012/02/07 11:55:32.284862,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-16LE
[2012/02/07 11:55:32.284871,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-16LE
[2012/02/07 11:55:32.284878,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS-2BE
[2012/02/07 11:55:32.284885,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS-2BE
[2012/02/07 11:55:32.284891,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-16BE
[2012/02/07 11:55:32.284898,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-16BE
[2012/02/07 11:55:32.284905,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF8
[2012/02/07 11:55:32.284912,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF8
[2012/02/07 11:55:32.284918,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-8
[2012/02/07 11:55:32.284925,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-8
[2012/02/07 11:55:32.284932,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset ASCII
[2012/02/07 11:55:32.284940,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset ASCII
[2012/02/07 11:55:32.284946,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset 646
[2012/02/07 11:55:32.284959,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset 646
[2012/02/07 11:55:32.284966,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset ISO-8859-1
[2012/02/07 11:55:32.284973,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset ISO-8859-1
[2012/02/07 11:55:32.284980,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS2-HEX
[2012/02/07 11:55:32.284992,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS2-HEX
[2012/02/07 11:55:32.285010,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285180,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285206,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285219,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285234,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285246,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285257,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285274,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285287,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285298,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285324,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285363,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285387,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285411,  5] lib/charcnv.c:98(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2012/02/07 11:55:32.285442,  5] lib/util.c:276(init_names)
  Netbios name list:-
  my_netbios_names[0]="KILIMANJARO"
[2012/02/07 11:55:32.285592,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=fe80::219:66ff:feef:2559%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
[2012/02/07 11:55:32.285674,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=192.168.100.101 bcast=192.168.100.255 netmask=255.255.255.0
lp_load_ex: refreshing parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter logon drive = H:
doing parameter domain master = yes
doing parameter winbind trusted domains only = yes
doing parameter winbind use default domain = yes
doing parameter logon home = \\%N\%U
doing parameter passdb backend = smbpasswd
doing parameter wins support = true
doing parameter netbios name = KILIMANJARO
handle_netbios_name: set global_myname to: KILIMANJARO
doing parameter server string = Zenit MS Real Samba PDC
doing parameter writable = no
doing parameter logon script = logon.cmd
doing parameter password server = KILIMANJARO
doing parameter winbind enum users = no
doing parameter path = /var/spool/samba
doing parameter workgroup = MOUNTAINS
doing parameter logon path = \\%N\%U\profile
doing parameter winbind enum groups = no
doing parameter os level = 33
doing parameter security = user
doing parameter preferred master = yes
doing parameter add machine script = sudo /usr/sbin/useradd -N -g machines -c Machine -d /var/lib/samba -s /bin/false %u
doing parameter domain logons = yes
pm_process() returned Yes
lp_servicenumber: couldn't find homes
set_server_role: role = ROLE_DOMAIN_PDC
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Netbios name list:-
my_netbios_names[0]="KILIMANJARO"
added interface eth0 ip=fe80::219:66ff:feef:2559%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.100.101 bcast=192.168.100.255 netmask=255.255.255.0
Opening cache file at /var/run/samba/gencache.tdb
Opening cache file at /var/run/samba/gencache_notrans.tdb
Cache entry with key = AD_SITENAME/DOMAIN/ couldn't be found 
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up KILIMANJARO#20 (sitename (null))
Returning valid cache entry: key = NBT/KILIMANJARO#20, value = 192.168.100.101:0, timeout = Tue Feb  7 12:05:05 2012
name KILIMANJARO#20 found.
Connecting to host=KILIMANJARO
Running timed event "tevent_req_timedout" 0x7fbf96ce0410
Connecting to 192.168.100.101 at port 445
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
    SO_SNDBUF = 50868
    SO_RCVBUF = 87744
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
cli_init_creds: user  domain 
saf_store: domain = [MOUNTAINS], server = [KILIMANJARO], expire = [1328613032]
Adding cache entry with key = SAF/DOMAIN/MOUNTAINS and timeout = Tue Feb  7 12:10:32 2012
 (900 seconds ahead)
Bind RPC Pipe: host KILIMANJARO auth_type 0, auth_level 1
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000001
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345778
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 89 ab 
        0030 version: 00000000
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=72, this_data=72, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 00000001
rpc_api_pipe: got frag len of 68 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 68 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 00000001
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000d
        001a str: \PIPE\lsarpc.
    000027 smb_io_rpc_results 
        0028 num_results: 01
        002c result     : 0000
        002e reason     : 0000
    000030 smb_io_rpc_iface 
        000030 smb_io_uuid uuid
            0030 data   : 8a885d04
            0034 data   : 1ceb
            0036 data   : 11c9
            0038 data   : 9f e8 
            003a data   : 08 00 2b 10 48 60 
        0040 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_noauth: opened pipe \lsarpc to machine KILIMANJARO and bound anonymously.
     lsa_OpenPolicy: struct lsa_OpenPolicy
        in: struct lsa_OpenPolicy
            system_name              : *
                system_name              : 0x005c (92)
            attr                     : *
                attr: struct lsa_ObjectAttribute
                    len                      : 0x00000018 (24)
                    root_dir                 : NULL
                    object_name              : NULL
                    attributes               : 0x00000000 (0)
                    sec_desc                 : NULL
                    sec_qos                  : NULL
            access_mask              : 0x02000000 (33554432)
                   0: LSA_POLICY_VIEW_LOCAL_INFORMATION
                   0: LSA_POLICY_VIEW_AUDIT_INFORMATION
                   0: LSA_POLICY_GET_PRIVATE_INFORMATION
                   0: LSA_POLICY_TRUST_ADMIN   
                   0: LSA_POLICY_CREATE_ACCOUNT
                   0: LSA_POLICY_CREATE_SECRET 
                   0: LSA_POLICY_CREATE_PRIVILEGE
                   0: LSA_POLICY_SET_DEFAULT_QUOTA_LIMITS
                   0: LSA_POLICY_SET_AUDIT_REQUIREMENTS
                   0: LSA_POLICY_AUDIT_LOG_ADMIN
                   0: LSA_POLICY_SERVER_ADMIN  
                   0: LSA_POLICY_LOOKUP_NAMES  
                   0: LSA_POLICY_NOTIFICATION  
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 003c
    000a auth_len  : 0000
    000c call_id   : 00000002
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000024
    0014 context_id: 0000
    0016 opnum     : 0006
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=60, this_data=60, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 00000002
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     lsa_OpenPolicy: struct lsa_OpenPolicy
        out: struct lsa_OpenPolicy
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000001-0000-0000-314f-240328340000
            result                   : NT_STATUS_OK
     lsa_QueryInfoPolicy: struct lsa_QueryInfoPolicy
        in: struct lsa_QueryInfoPolicy
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000001-0000-0000-314f-240328340000
            level                    : LSA_POLICY_INFO_ACCOUNT_DOMAIN (5)
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 002e
    000a auth_len  : 0000
    000c call_id   : 00000003
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000016
    0014 context_id: 0000
    0016 opnum     : 0007
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=46, this_data=46, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 006c
    000a auth_len  : 0000
    000c call_id   : 00000003
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000054
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 108, data_len 84, ss_len 0
rpc_api_pipe: got frag len of 108 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 168 bytes.
     lsa_QueryInfoPolicy: struct lsa_QueryInfoPolicy
        out: struct lsa_QueryInfoPolicy
            info                     : *
                info                     : *
                    info                     : union lsa_PolicyInformation(case 5)
                    account_domain: struct lsa_DomainInfo
                        name: struct lsa_StringLarge
                            length                   : 0x0012 (18)
                            size                     : 0x0014 (20)
                            string                   : *
                                string                   : 'MOUNTAINS'
                        sid                      : *
                            sid                      : S-1-5-21-1876437633-3346474330-1414540629
            result                   : NT_STATUS_OK
     lsa_Close: struct lsa_Close
        in: struct lsa_Close
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000001-0000-0000-314f-240328340000
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 002c
    000a auth_len  : 0000
    000c call_id   : 00000004
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000014
    0014 context_id: 0000
    0016 opnum     : 0000
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=44, this_data=44, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 00000004
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     lsa_Close: struct lsa_Close
        out: struct lsa_Close
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000000-0000-0000-0000-000000000000
            result                   : NT_STATUS_OK
rpc_pipe_destructor: closed \lsarpc
Bind RPC Pipe: host KILIMANJARO auth_type 0, auth_level 1
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000005
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345678
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 cf fb 
        0030 version: 00000001
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=72, this_data=72, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000005
rpc_api_pipe: got frag len of 72 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 72 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000005
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000f
        001a str: \PIPE\netlogon.
    000029 smb_io_rpc_results 
        002c num_results: 01
        0030 result     : 0000
        0032 reason     : 0000
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_noauth: opened pipe \netlogon to machine KILIMANJARO and bound anonymously.
Locking key 534543524554532F5349
Allocated locked data 0x0x7fbf96ce11f0
Unlocking key 534543524554532F5349
rpc command function failed! (NT_STATUS_NOT_SUPPORTED)
rpc_pipe_destructor: closed \netlogon
write_socket(5,39)
write_socket(5,39) wrote 39
got smb length of 35
size=35
smb_com=0x71
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51203
smb_tid=1
smb_pid=13351
smb_uid=100
smb_mid=13
smt_wct=0
smb_bcc=0
Cache entry with key = AD_SITENAME/DOMAIN/ couldn't be found 
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up KILIMANJARO#20 (sitename (null))
Returning valid cache entry: key = NBT/KILIMANJARO#20, value = 192.168.100.101:0, timeout = Tue Feb  7 12:05:05 2012
name KILIMANJARO#20 found.
Connecting to host=KILIMANJARO
Running timed event "tevent_req_timedout" 0x7fbf96ce07b0
Connecting to 192.168.100.101 at port 445
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
    SO_SNDBUF = 50868
    SO_RCVBUF = 87744
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
     &negotiate: struct NEGOTIATE_MESSAGE
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
            DomainName               : 'MOUNTAINS'
        WorkstationLen           : 0x000b (11)
        WorkstationMaxLen        : 0x000b (11)
        Workstation              : *
            Workstation              : 'KILIMANJARO'
write_socket(5,172)
write_socket(5,172) wrote 172
got smb length of 348
size=348
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51203
smb_tid=0
smb_pid=13351
smb_uid=100
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  249 (0xF9)
smb_bcc=305
[0000] A1 81 F6 30 81 F3 A0 03   0A 01 01 A1 0C 06 0A 2B   ...0.... .......+
[0010] 06 01 04 01 82 37 02 02   0A A2 81 DD 04 81 DA 4E   .....7.. .......N
[0020] 54 4C 4D 53 53 50 00 02   00 00 00 12 00 12 00 30   TLMSSP.. .......0
[0030] 00 00 00 15 82 89 60 23   97 F9 87 FA 01 AA 8C 00   ......`# ........
[0040] 00 00 00 00 00 00 00 98   00 98 00 42 00 00 00 4D   ........ ...B...M
[0050] 00 4F 00 55 00 4E 00 54   00 41 00 49 00 4E 00 53   .O.U.N.T .A.I.N.S
[0060] 00 02 00 12 00 4D 00 4F   00 55 00 4E 00 54 00 41   .....M.O .U.N.T.A
[0070] 00 49 00 4E 00 53 00 01   00 16 00 4B 00 49 00 4C   .I.N.S.. ...K.I.L
[0080] 00 49 00 4D 00 41 00 4E   00 4A 00 41 00 52 00 4F   .I.M.A.N .J.A.R.O
[0090] 00 04 00 22 00 7A 00 65   00 6E 00 69 00 74 00 2D   ...".z.e .n.i.t.-
[00A0] 00 6D 00 73 00 2D 00 72   00 65 00 61 00 6C 00 2E   .m.s.-.r .e.a.l..
[00B0] 00 63 00 6F 00 6D 00 03   00 3A 00 6B 00 69 00 6C   .c.o.m.. .:.k.i.l
[00C0] 00 69 00 6D 00 61 00 6E   00 6A 00 61 00 72 00 6F   .i.m.a.n .j.a.r.o
[00D0] 00 2E 00 7A 00 65 00 6E   00 69 00 74 00 2D 00 6D   ...z.e.n .i.t.-.m
[00E0] 00 73 00 2D 00 72 00 65   00 61 00 6C 00 2E 00 63   .s.-.r.e .a.l...c
[00F0] 00 6F 00 6D 00 00 00 00   00 55 00 6E 00 69 00 78   .o.m.... .U.n.i.x
[0100] 00 00 00 53 00 61 00 6D   00 62 00 61 00 20 00 33   ...S.a.m .b.a. .3
[0110] 00 2E 00 35 00 2E 00 31   00 31 00 00 00 4D 00 4F   ...5...1 .1...M.O
[0120] 00 55 00 4E 00 54 00 41   00 49 00 4E 00 53 00 00   .U.N.T.A .I.N.S..
[0130] 00                                                . 
size=348
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51203
smb_tid=0
smb_pid=13351
smb_uid=100
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  249 (0xF9)
smb_bcc=305
[0000] A1 81 F6 30 81 F3 A0 03   0A 01 01 A1 0C 06 0A 2B   ...0.... .......+
[0010] 06 01 04 01 82 37 02 02   0A A2 81 DD 04 81 DA 4E   .....7.. .......N
[0020] 54 4C 4D 53 53 50 00 02   00 00 00 12 00 12 00 30   TLMSSP.. .......0
[0030] 00 00 00 15 82 89 60 23   97 F9 87 FA 01 AA 8C 00   ......`# ........
[0040] 00 00 00 00 00 00 00 98   00 98 00 42 00 00 00 4D   ........ ...B...M
[0050] 00 4F 00 55 00 4E 00 54   00 41 00 49 00 4E 00 53   .O.U.N.T .A.I.N.S
[0060] 00 02 00 12 00 4D 00 4F   00 55 00 4E 00 54 00 41   .....M.O .U.N.T.A
[0070] 00 49 00 4E 00 53 00 01   00 16 00 4B 00 49 00 4C   .I.N.S.. ...K.I.L
[0080] 00 49 00 4D 00 41 00 4E   00 4A 00 41 00 52 00 4F   .I.M.A.N .J.A.R.O
[0090] 00 04 00 22 00 7A 00 65   00 6E 00 69 00 74 00 2D   ...".z.e .n.i.t.-
[00A0] 00 6D 00 73 00 2D 00 72   00 65 00 61 00 6C 00 2E   .m.s.-.r .e.a.l..
[00B0] 00 63 00 6F 00 6D 00 03   00 3A 00 6B 00 69 00 6C   .c.o.m.. .:.k.i.l
[00C0] 00 69 00 6D 00 61 00 6E   00 6A 00 61 00 72 00 6F   .i.m.a.n .j.a.r.o
[00D0] 00 2E 00 7A 00 65 00 6E   00 69 00 74 00 2D 00 6D   ...z.e.n .i.t.-.m
[00E0] 00 73 00 2D 00 72 00 65   00 61 00 6C 00 2E 00 63   .s.-.r.e .a.l...c
[00F0] 00 6F 00 6D 00 00 00 00   00 55 00 6E 00 69 00 78   .o.m.... .U.n.i.x
[0100] 00 00 00 53 00 61 00 6D   00 62 00 61 00 20 00 33   ...S.a.m .b.a. .3
[0110] 00 2E 00 35 00 2E 00 31   00 31 00 00 00 4D 00 4F   ...5...1 .1...M.O
[0120] 00 55 00 4E 00 54 00 41   00 49 00 4E 00 53 00 00   .U.N.T.A .I.N.S..
[0130] 00                                                . 
     &challenge: struct CHALLENGE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmChallenge (0x2)
        TargetNameLen            : 0x0012 (18)
        TargetNameMaxLen         : 0x0012 (18)
        TargetName               : *
            TargetName               : 'MOUNTAINS'
        NegotiateFlags           : 0x60898215 (1619624469)
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
               1: NTLMSSP_TARGET_TYPE_DOMAIN
               0: NTLMSSP_TARGET_TYPE_SERVER
               0: NTLMSSP_TARGET_TYPE_SHARE
               1: NTLMSSP_NEGOTIATE_EXTENDED_SESSIONSECURITY
               0: NTLMSSP_NEGOTIATE_IDENTIFY
               0: NTLMSSP_REQUEST_NON_NT_SESSION_KEY
               1: NTLMSSP_NEGOTIATE_TARGET_INFO
               0: NTLMSSP_NEGOTIATE_VERSION
               1: NTLMSSP_NEGOTIATE_128    
               1: NTLMSSP_NEGOTIATE_KEY_EXCH
               0: NTLMSSP_NEGOTIATE_56     
        ServerChallenge          : 2397f987fa01aa8c
        Reserved                 : 0000000000000000
        TargetInfoLen            : 0x0098 (152)
        TargetNameInfoMaxLen     : 0x0098 (152)
        TargetInfo               : *
            TargetInfo: struct AV_PAIR_LIST
                count                    : 0x00000005 (5)
                pair: ARRAY(5)
                    pair: struct AV_PAIR
                        AvId                     : MsvAvNbDomainName (0x2)
                        AvLen                    : 0x0012 (18)
                        Value                    : union ntlmssp_AvValue(case 0x2)
                        AvNbDomainName           : 'MOUNTAINS'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvNbComputerName (0x1)
                        AvLen                    : 0x0016 (22)
                        Value                    : union ntlmssp_AvValue(case 0x1)
                        AvNbComputerName         : 'KILIMANJARO'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvDnsDomainName (0x4)
                        AvLen                    : 0x0022 (34)
                        Value                    : union ntlmssp_AvValue(case 0x4)
                        AvDnsDomainName          : 'zenit-ms-real.com'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvDnsComputerName (0x3)
                        AvLen                    : 0x003a (58)
                        Value                    : union ntlmssp_AvValue(case 0x3)
                        AvDnsComputerName        : 'kilimanjaro.zenit-ms-real.com'
                    pair: struct AV_PAIR
                        AvId                     : MsvAvEOL (0x0)
                        AvLen                    : 0x0000 (0)
                        Value                    : union ntlmssp_AvValue(case 0x0)
Got challenge flags:
Got NTLMSSP neg_flags=0x60898215
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
NTLMSSP challenge set by NTLM2
challenge is: 
[0000] E3 9C AF AB 19 A0 34 8B                            ......4. 
     &authenticate: struct AUTHENTICATE_MESSAGE
        Signature                : 'NTLMSSP'
        MessageType              : NtLmAuthenticate (3)
        LmChallengeResponseLen   : 0x0018 (24)
        LmChallengeResponseMaxLen: 0x0018 (24)
        LmChallengeResponse      : *
            LmChallengeResponse      : union ntlmssp_LM_RESPONSE(case 24)
            v1: struct LM_RESPONSE
                Response                 : ef83da6d0541d81300000000000000000000000000000000
        NtChallengeResponseLen   : 0x0018 (24)
        NtChallengeResponseMaxLen: 0x0018 (24)
        NtChallengeResponse      : *
            NtChallengeResponse      : union ntlmssp_NTLM_RESPONSE(case 24)
            v1: struct NTLM_RESPONSE
                Response                 : 73dcaf8658c35d0463e5fc089558fa451371129d047466f8
        DomainNameLen            : 0x0012 (18)
        DomainNameMaxLen         : 0x0012 (18)
        DomainName               : *
            DomainName               : 'MOUNTAINS'
        UserNameLen              : 0x0008 (8)
        UserNameMaxLen           : 0x0008 (8)
        UserName                 : *
            UserName                 : 'root'
        WorkstationLen           : 0x0016 (22)
        WorkstationMaxLen        : 0x0016 (22)
        Workstation              : *
            Workstation              : 'KILIMANJARO'
        EncryptedRandomSessionKeyLen: 0x0010 (16)
        EncryptedRandomSessionKeyMaxLen: 0x0010 (16)
        EncryptedRandomSessionKey: *
            EncryptedRandomSessionKey: DATA_BLOB length=16
[0000] 82 92 07 47 D6 4A AE 80   14 75 7D 28 A6 74 87 4E   ...G.J.. .u}(.t.N
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
write_socket(5,274)
write_socket(5,274) wrote 274
got smb length of 108
size=108
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51203
smb_tid=0
smb_pid=13351
smb_uid=100
smb_mid=3
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    9 (0x9)
smb_bcc=65
[0000] A1 07 30 05 A0 03 0A 01   00 55 00 6E 00 69 00 78   ..0..... .U.n.i.x
[0010] 00 00 00 53 00 61 00 6D   00 62 00 61 00 20 00 33   ...S.a.m .b.a. .3
[0020] 00 2E 00 35 00 2E 00 31   00 31 00 00 00 4D 00 4F   ...5...1 .1...M.O
[0030] 00 55 00 4E 00 54 00 41   00 49 00 4E 00 53 00 00   .U.N.T.A .I.N.S..
[0040] 00                                                . 
size=108
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51203
smb_tid=0
smb_pid=13351
smb_uid=100
smb_mid=3
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    9 (0x9)
smb_bcc=65
[0000] A1 07 30 05 A0 03 0A 01   00 55 00 6E 00 69 00 78   ..0..... .U.n.i.x
[0010] 00 00 00 53 00 61 00 6D   00 62 00 61 00 20 00 33   ...S.a.m .b.a. .3
[0020] 00 2E 00 35 00 2E 00 31   00 31 00 00 00 4D 00 4F   ...5...1 .1...M.O
[0030] 00 55 00 4E 00 54 00 41   00 49 00 4E 00 53 00 00   .U.N.T.A .I.N.S..
[0040] 00                                                . 
cli_init_creds: user root domain MOUNTAINS
saf_store: domain = [MOUNTAINS], server = [KILIMANJARO], expire = [1328613034]
Adding cache entry with key = SAF/DOMAIN/MOUNTAINS and timeout = Tue Feb  7 12:10:34 2012
 (900 seconds ahead)
Bind RPC Pipe: host KILIMANJARO auth_type 0, auth_level 1
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000006
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345778
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 89 ab 
        0030 version: 00000000
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=72, this_data=72, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 00000006
rpc_api_pipe: got frag len of 68 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 68 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 00000006
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000d
        001a str: \PIPE\lsarpc.
    000027 smb_io_rpc_results 
        0028 num_results: 01
        002c result     : 0000
        002e reason     : 0000
    000030 smb_io_rpc_iface 
        000030 smb_io_uuid uuid
            0030 data   : 8a885d04
            0034 data   : 1ceb
            0036 data   : 11c9
            0038 data   : 9f e8 
            003a data   : 08 00 2b 10 48 60 
        0040 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_noauth: opened pipe \lsarpc to machine KILIMANJARO and bound anonymously.
     lsa_OpenPolicy: struct lsa_OpenPolicy
        in: struct lsa_OpenPolicy
            system_name              : *
                system_name              : 0x005c (92)
            attr                     : *
                attr: struct lsa_ObjectAttribute
                    len                      : 0x00000018 (24)
                    root_dir                 : NULL
                    object_name              : NULL
                    attributes               : 0x00000000 (0)
                    sec_desc                 : NULL
                    sec_qos                  : *
                        sec_qos: struct lsa_QosInfo
                            len                      : 0x0000000c (12)
                            impersonation_level      : 0x0002 (2)
                            context_mode             : 0x01 (1)
                            effective_only           : 0x00 (0)
            access_mask              : 0x02000000 (33554432)
                   0: LSA_POLICY_VIEW_LOCAL_INFORMATION
                   0: LSA_POLICY_VIEW_AUDIT_INFORMATION
                   0: LSA_POLICY_GET_PRIVATE_INFORMATION
                   0: LSA_POLICY_TRUST_ADMIN   
                   0: LSA_POLICY_CREATE_ACCOUNT
                   0: LSA_POLICY_CREATE_SECRET 
                   0: LSA_POLICY_CREATE_PRIVILEGE
                   0: LSA_POLICY_SET_DEFAULT_QUOTA_LIMITS
                   0: LSA_POLICY_SET_AUDIT_REQUIREMENTS
                   0: LSA_POLICY_AUDIT_LOG_ADMIN
                   0: LSA_POLICY_SERVER_ADMIN  
                   0: LSA_POLICY_LOOKUP_NAMES  
                   0: LSA_POLICY_NOTIFICATION  
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 00000007
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 0000002c
    0014 context_id: 0000
    0016 opnum     : 0006
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=68, this_data=68, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 00000007
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     lsa_OpenPolicy: struct lsa_OpenPolicy
        out: struct lsa_OpenPolicy
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000001-0000-0000-314f-260329340000
            result                   : NT_STATUS_OK
     lsa_QueryInfoPolicy: struct lsa_QueryInfoPolicy
        in: struct lsa_QueryInfoPolicy
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000001-0000-0000-314f-260329340000
            level                    : LSA_POLICY_INFO_ACCOUNT_DOMAIN (5)
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 002e
    000a auth_len  : 0000
    000c call_id   : 00000008
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000016
    0014 context_id: 0000
    0016 opnum     : 0007
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=46, this_data=46, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 006c
    000a auth_len  : 0000
    000c call_id   : 00000008
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000054
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 108, data_len 84, ss_len 0
rpc_api_pipe: got frag len of 108 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 168 bytes.
     lsa_QueryInfoPolicy: struct lsa_QueryInfoPolicy
        out: struct lsa_QueryInfoPolicy
            info                     : *
                info                     : *
                    info                     : union lsa_PolicyInformation(case 5)
                    account_domain: struct lsa_DomainInfo
                        name: struct lsa_StringLarge
                            length                   : 0x0012 (18)
                            size                     : 0x0014 (20)
                            string                   : *
                                string                   : 'MOUNTAINS'
                        sid                      : *
                            sid                      : S-1-5-21-1876437633-3346474330-1414540629
            result                   : NT_STATUS_OK
     lsa_Close: struct lsa_Close
        in: struct lsa_Close
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000001-0000-0000-314f-260329340000
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 002c
    000a auth_len  : 0000
    000c call_id   : 00000009
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000014
    0014 context_id: 0000
    0016 opnum     : 0000
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=44, this_data=44, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 00000009
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     lsa_Close: struct lsa_Close
        out: struct lsa_Close
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000000-0000-0000-0000-000000000000
            result                   : NT_STATUS_OK
rpc_pipe_destructor: closed \lsarpc
Bind RPC Pipe: host KILIMANJARO auth_type 0, auth_level 1
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 0000000a
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345778
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 89 ac 
        0030 version: 00000001
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=72, this_data=72, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 0000000a
rpc_api_pipe: got frag len of 68 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 68 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 0000000a
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000b
        001a str: \PIPE\samr.
    000025 smb_io_rpc_results 
        0028 num_results: 01
        002c result     : 0000
        002e reason     : 0000
    000030 smb_io_rpc_iface 
        000030 smb_io_uuid uuid
            0030 data   : 8a885d04
            0034 data   : 1ceb
            0036 data   : 11c9
            0038 data   : 9f e8 
            003a data   : 08 00 2b 10 48 60 
        0040 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_noauth: opened pipe \samr to machine KILIMANJARO and bound anonymously.
     samr_Connect2: struct samr_Connect2
        in: struct samr_Connect2
            system_name              : *
                system_name              : 'KILIMANJARO'
            access_mask              : 0x00000030 (48)
                   0: SAMR_ACCESS_CONNECT_TO_SERVER
                   0: SAMR_ACCESS_SHUTDOWN_SERVER
                   0: SAMR_ACCESS_INITIALIZE_SERVER
                   0: SAMR_ACCESS_CREATE_DOMAIN
                   1: SAMR_ACCESS_ENUM_DOMAINS 
                   1: SAMR_ACCESS_LOOKUP_DOMAIN
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0044
    000a auth_len  : 0000
    000c call_id   : 0000000b
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 0000002c
    0014 context_id: 0000
    0016 opnum     : 0039
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=68, this_data=68, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 0000000b
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     samr_Connect2: struct samr_Connect2
        out: struct samr_Connect2
            connect_handle           : *
                connect_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000002-0000-0000-314f-260329340000
            result                   : NT_STATUS_OK
     samr_OpenDomain: struct samr_OpenDomain
        in: struct samr_OpenDomain
            connect_handle           : *
                connect_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000002-0000-0000-314f-260329340000
            access_mask              : 0x00000211 (529)
                   1: SAMR_DOMAIN_ACCESS_LOOKUP_INFO_1
                   0: SAMR_DOMAIN_ACCESS_SET_INFO_1
                   0: SAMR_DOMAIN_ACCESS_LOOKUP_INFO_2
                   0: SAMR_DOMAIN_ACCESS_SET_INFO_2
                   1: SAMR_DOMAIN_ACCESS_CREATE_USER
                   0: SAMR_DOMAIN_ACCESS_CREATE_GROUP
                   0: SAMR_DOMAIN_ACCESS_CREATE_ALIAS
                   0: SAMR_DOMAIN_ACCESS_LOOKUP_ALIAS
                   0: SAMR_DOMAIN_ACCESS_ENUM_ACCOUNTS
                   1: SAMR_DOMAIN_ACCESS_OPEN_ACCOUNT
                   0: SAMR_DOMAIN_ACCESS_SET_INFO_3
            sid                      : *
                sid                      : S-1-5-21-1876437633-3346474330-1414540629
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 004c
    000a auth_len  : 0000
    000c call_id   : 0000000c
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000034
    0014 context_id: 0000
    0016 opnum     : 0007
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=76, this_data=76, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 0000000c
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     samr_OpenDomain: struct samr_OpenDomain
        out: struct samr_OpenDomain
            domain_handle            : *
                domain_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000003-0000-0000-314f-260329340000
            result                   : NT_STATUS_OK
Creating account with flags: -536543056
     samr_CreateUser2: struct samr_CreateUser2
        in: struct samr_CreateUser2
            domain_handle            : *
                domain_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000003-0000-0000-314f-260329340000
            account_name             : *
                account_name: struct lsa_String
                    length                   : 0x0018 (24)
                    size                     : 0x0018 (24)
                    string                   : *
                        string                   : 'kilimanjaro$'
            acct_flags               : 0x00000100 (256)
                   0: ACB_DISABLED             
                   0: ACB_HOMDIRREQ            
                   0: ACB_PWNOTREQ             
                   0: ACB_TEMPDUP              
                   0: ACB_NORMAL               
                   0: ACB_MNS                  
                   0: ACB_DOMTRUST             
                   0: ACB_WSTRUST              
                   1: ACB_SVRTRUST             
                   0: ACB_PWNOEXP              
                   0: ACB_AUTOLOCK             
                   0: ACB_ENC_TXT_PWD_ALLOWED  
                   0: ACB_SMARTCARD_REQUIRED   
                   0: ACB_TRUSTED_FOR_DELEGATION
                   0: ACB_NOT_DELEGATED        
                   0: ACB_USE_DES_KEY_ONLY     
                   0: ACB_DONT_REQUIRE_PREAUTH 
                   0: ACB_PW_EXPIRED           
                   0: ACB_NO_AUTH_DATA_REQD    
            access_mask              : 0xe00500b0 (3758424240)
                   0: SAMR_USER_ACCESS_GET_NAME_ETC
                   0: SAMR_USER_ACCESS_GET_LOCALE
                   0: SAMR_USER_ACCESS_SET_LOC_COM
                   0: SAMR_USER_ACCESS_GET_LOGONINFO
                   1: SAMR_USER_ACCESS_GET_ATTRIBUTES
                   1: SAMR_USER_ACCESS_SET_ATTRIBUTES
                   0: SAMR_USER_ACCESS_CHANGE_PASSWORD
                   1: SAMR_USER_ACCESS_SET_PASSWORD
                   0: SAMR_USER_ACCESS_GET_GROUPS
                   0: SAMR_USER_ACCESS_GET_GROUP_MEMBERSHIP
                   0: SAMR_USER_ACCESS_CHANGE_GROUP_MEMBERSHIP
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0060
    000a auth_len  : 0000
    000c call_id   : 0000000d
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000048
    0014 context_id: 0000
    0016 opnum     : 0032
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=96, this_data=96, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0038
    000a auth_len  : 0000
    000c call_id   : 0000000d
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000020
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 56, data_len 32, ss_len 0
rpc_api_pipe: got frag len of 56 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 64 bytes.
     samr_CreateUser2: struct samr_CreateUser2
        out: struct samr_CreateUser2
            user_handle              : *
                user_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000000-0000-0000-0000-000000000000
            access_granted           : *
                access_granted           : 0x00000000 (0)
            rid                      : *
                rid                      : 0x00000000 (0)
            result                   : NT_STATUS_USER_EXISTS
     samr_LookupNames: struct samr_LookupNames
        in: struct samr_LookupNames
            domain_handle            : *
                domain_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000003-0000-0000-314f-260329340000
            num_names                : 0x00000001 (1)
            names: ARRAY(1)
                names: struct lsa_String
                    length                   : 0x0018 (24)
                    size                     : 0x0018 (24)
                    string                   : *
                        string                   : 'kilimanjaro$'
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0068
    000a auth_len  : 0000
    000c call_id   : 0000000e
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000050
    0014 context_id: 0000
    0016 opnum     : 0011
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=104, this_data=104, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 003c
    000a auth_len  : 0000
    000c call_id   : 0000000e
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000024
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 60, data_len 36, ss_len 0
rpc_api_pipe: got frag len of 60 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 72 bytes.
     samr_LookupNames: struct samr_LookupNames
        out: struct samr_LookupNames
            rids                     : *
                rids: struct samr_Ids
                    count                    : 0x00000001 (1)
                    ids                      : *
                        ids: ARRAY(1)
                            ids                      : 0x0000520c (21004)
            types                    : *
                types: struct samr_Ids
                    count                    : 0x00000001 (1)
                    ids                      : *
                        ids: ARRAY(1)
                            ids                      : 0x00000001 (1)
            result                   : NT_STATUS_OK
     samr_OpenUser: struct samr_OpenUser
        in: struct samr_OpenUser
            domain_handle            : *
                domain_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000003-0000-0000-314f-260329340000
            access_mask              : 0x02000000 (33554432)
                   0: SAMR_USER_ACCESS_GET_NAME_ETC
                   0: SAMR_USER_ACCESS_GET_LOCALE
                   0: SAMR_USER_ACCESS_SET_LOC_COM
                   0: SAMR_USER_ACCESS_GET_LOGONINFO
                   0: SAMR_USER_ACCESS_GET_ATTRIBUTES
                   0: SAMR_USER_ACCESS_SET_ATTRIBUTES
                   0: SAMR_USER_ACCESS_CHANGE_PASSWORD
                   0: SAMR_USER_ACCESS_SET_PASSWORD
                   0: SAMR_USER_ACCESS_GET_GROUPS
                   0: SAMR_USER_ACCESS_GET_GROUP_MEMBERSHIP
                   0: SAMR_USER_ACCESS_CHANGE_GROUP_MEMBERSHIP
            rid                      : 0x0000520c (21004)
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0034
    000a auth_len  : 0000
    000c call_id   : 0000000f
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 0000001c
    0014 context_id: 0000
    0016 opnum     : 0022
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=52, this_data=52, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 0000000f
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     samr_OpenUser: struct samr_OpenUser
        out: struct samr_OpenUser
            user_handle              : *
                user_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000004-0000-0000-314f-260329340000
            result                   : NT_STATUS_OK
     samr_SetUserInfo2: struct samr_SetUserInfo2
        in: struct samr_SetUserInfo2
            user_handle              : *
                user_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000004-0000-0000-314f-260329340000
            level                    : UserInternal5Information (24)
            info                     : *
                info                     : union samr_UserInfo(case 24)
                info24: struct samr_UserInfo24
                    password: struct samr_CryptPassword
                        data                     : 01face220bdf9cd8724a6888388355dc889ad0e982551fe7a232a21084bacb9fb30434e70ad4a6ab999eca0df68e838409c4ee07a763a8e5c67bd8128273e24cfa3945118a1c8d8802b7fb41a1f4f3be02af9adc879903e7d92ad5734ddbc5bbb0da481afc9c59a45f660ff6e543da398f3adbd48f179a2210b5f4f17fe2f1ada9f7785b38665ba51da52090ad4fc11c98179f75d409989dec0e8ec4bd9fea3b34315e1ce2f27615980d024ed55a6de49dae8733bb9c12f005868040121d40a6f4d56dab67e4e3fea1616ec4730d8b9657b9a44e31e3eb3cfe7434a9b1fa86eb039f2e8fbc61a6642bf2855e5b03c022be08cdb23f6022e31625a983500aa28102aaa9830ef4d3f128c42e8d54bf20bba6527d55d35ab8aa0c7287d00eee156f8205f0bdfd0fd9f95c3582e6426b203f9819bf2ef198f44288698f1a3cd1cfb4c1a513c9b59d0fe7000156a2874c2344062bd693f058cf63ac8a717e90b5e51e69c69fd9c032d7a0d294a6cf70dcac62da2cb6f969831899fc846915adf329248ab5d753ece0d901f3eb776547ff6f1d4c63a29dc92bd41643170fa4287584079b39598b91a97c48d976659923ad560d4d10dc577cd8a546a562e658ebc750e2e0354b8cfaec935414cd939684d889a60a71086e485a6dc957a760b5c459dda1e12a9ce9b210 +>
482e5d7a98cce8bfa54caa5adac1954da1e039fe87bdb03747810d5c9c4e
                    password_expired         : 0x00 (0)
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0235
    000a auth_len  : 0000
    000c call_id   : 00000010
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 0000021d
    0014 context_id: 0000
    0016 opnum     : 003a
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=565, this_data=565, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 001c
    000a auth_len  : 0000
    000c call_id   : 00000010
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000004
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 28, data_len 4, ss_len 0
rpc_api_pipe: got frag len of 28 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 8 bytes.
     samr_SetUserInfo2: struct samr_SetUserInfo2
        out: struct samr_SetUserInfo2
            result                   : NT_STATUS_OK
     samr_SetUserInfo: struct samr_SetUserInfo
        in: struct samr_SetUserInfo
            user_handle              : *
                user_handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000004-0000-0000-314f-260329340000
            level                    : UserControlInformation (16)
            info                     : *
                info                     : union samr_UserInfo(case 16)
                info16: struct samr_UserInfo16
                    acct_flags               : 0x00000100 (256)
                           0: ACB_DISABLED             
                           0: ACB_HOMDIRREQ            
                           0: ACB_PWNOTREQ             
                           0: ACB_TEMPDUP              
                           0: ACB_NORMAL               
                           0: ACB_MNS                  
                           0: ACB_DOMTRUST             
                           0: ACB_WSTRUST              
                           1: ACB_SVRTRUST             
                           0: ACB_PWNOEXP              
                           0: ACB_AUTOLOCK             
                           0: ACB_ENC_TXT_PWD_ALLOWED  
                           0: ACB_SMARTCARD_REQUIRED   
                           0: ACB_TRUSTED_FOR_DELEGATION
                           0: ACB_NOT_DELEGATED        
                           0: ACB_USE_DES_KEY_ONLY     
                           0: ACB_DONT_REQUIRE_PREAUTH 
                           0: ACB_PW_EXPIRED           
                           0: ACB_NO_AUTH_DATA_REQD    
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0034
    000a auth_len  : 0000
    000c call_id   : 00000011
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 0000001c
    0014 context_id: 0000
    0016 opnum     : 0025
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=52, this_data=52, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 001c
    000a auth_len  : 0000
    000c call_id   : 00000011
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000004
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 28, data_len 4, ss_len 0
rpc_api_pipe: got frag len of 28 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 8 bytes.
     samr_SetUserInfo: struct samr_SetUserInfo
        out: struct samr_SetUserInfo
            result                   : NT_STATUS_OK
     samr_Close: struct samr_Close
        in: struct samr_Close
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000004-0000-0000-314f-260329340000
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 002c
    000a auth_len  : 0000
    000c call_id   : 00000012
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000014
    0014 context_id: 0000
    0016 opnum     : 0001
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=44, this_data=44, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0030
    000a auth_len  : 0000
    000c call_id   : 00000012
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000018
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 48, data_len 24, ss_len 0
rpc_api_pipe: got frag len of 48 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 48 bytes.
     samr_Close: struct samr_Close
        out: struct samr_Close
            handle                   : *
                handle: struct policy_handle
                    handle_type              : 0x00000000 (0)
                    uuid                     : 00000000-0000-0000-0000-000000000000
            result                   : NT_STATUS_OK
rpc_pipe_destructor: closed \samr
Bind RPC Pipe: host KILIMANJARO auth_type 0, auth_level 1
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000013
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345678
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 cf fb 
        0030 version: 00000001
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=72, this_data=72, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000013
rpc_api_pipe: got frag len of 72 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 72 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000013
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000f
        001a str: \PIPE\netlogon.
    000029 smb_io_rpc_results 
        002c num_results: 01
        0030 result     : 0000
        0032 reason     : 0000
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_noauth: opened pipe \netlogon to machine KILIMANJARO and bound anonymously.
     netr_ServerReqChallenge: struct netr_ServerReqChallenge
        in: struct netr_ServerReqChallenge
            server_name              : *
                server_name              : '\\KILIMANJARO'
            computer_name            : *
                computer_name            : 'KILIMANJARO'
            credentials              : *
                credentials: struct netr_Credential
                    data                     : 0469e9fce784f16e
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0070
    000a auth_len  : 0000
    000c call_id   : 00000014
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000058
    0014 context_id: 0000
    0016 opnum     : 0004
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=112, this_data=112, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0024
    000a auth_len  : 0000
    000c call_id   : 00000014
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 0000000c
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 36, data_len 12, ss_len 0
rpc_api_pipe: got frag len of 36 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 24 bytes.
     netr_ServerReqChallenge: struct netr_ServerReqChallenge
        out: struct netr_ServerReqChallenge
            return_credentials       : *
                return_credentials: struct netr_Credential
                    data                     : 1e20c3ae1209ec23
            result                   : NT_STATUS_OK
     netr_ServerAuthenticate2: struct netr_ServerAuthenticate2
        in: struct netr_ServerAuthenticate2
            server_name              : *
                server_name              : '\\KILIMANJARO'
            account_name             : *
                account_name             : 'KILIMANJARO$'
            secure_channel_type      : SEC_CHAN_BDC (6)
            computer_name            : *
                computer_name            : 'KILIMANJARO'
            credentials              : *
                credentials: struct netr_Credential
                    data                     : e78eac03503ba5d1
            negotiate_flags          : *
                negotiate_flags          : 0x600fffff (1611661311)
                       1: NETLOGON_NEG_ACCOUNT_LOCKOUT
                       1: NETLOGON_NEG_PERSISTENT_SAMREPL
                       1: NETLOGON_NEG_ARCFOUR     
                       1: NETLOGON_NEG_PROMOTION_COUNT
                       1: NETLOGON_NEG_CHANGELOG_BDC
                       1: NETLOGON_NEG_FULL_SYNC_REPL
                       1: NETLOGON_NEG_MULTIPLE_SIDS
                       1: NETLOGON_NEG_REDO        
                       1: NETLOGON_NEG_PASSWORD_CHANGE_REFUSAL
                       1: NETLOGON_NEG_SEND_PASSWORD_INFO_PDC
                       1: NETLOGON_NEG_GENERIC_PASSTHROUGH
                       1: NETLOGON_NEG_CONCURRENT_RPC
                       1: NETLOGON_NEG_AVOID_ACCOUNT_DB_REPL
                       1: NETLOGON_NEG_AVOID_SECURITYAUTH_DB_REPL
                       1: NETLOGON_NEG_STRONG_KEYS 
                       1: NETLOGON_NEG_TRANSITIVE_TRUSTS
                       1: NETLOGON_NEG_DNS_DOMAIN_TRUSTS
                       1: NETLOGON_NEG_PASSWORD_SET2
                       1: NETLOGON_NEG_GETDOMAININFO
                       1: NETLOGON_NEG_CROSS_FOREST_TRUSTS
                       0: NETLOGON_NEG_NEUTRALIZE_NT4_EMULATION
                       0: NETLOGON_NEG_RODC_PASSTHROUGH
                       0: NETLOGON_NEG_SUPPORTS_AES_SHA2
                       0: NETLOGON_NEG_SUPPORTS_AES
                       1: NETLOGON_NEG_AUTHENTICATED_RPC_LSASS
                       1: NETLOGON_NEG_AUTHENTICATED_RPC
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 009c
    000a auth_len  : 0000
    000c call_id   : 00000015
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000084
    0014 context_id: 0000
    0016 opnum     : 000f
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=156, this_data=156, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0028
    000a auth_len  : 0000
    000c call_id   : 00000015
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000010
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 40, data_len 16, ss_len 0
rpc_api_pipe: got frag len of 40 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 32 bytes.
     netr_ServerAuthenticate2: struct netr_ServerAuthenticate2
        out: struct netr_ServerAuthenticate2
            return_credentials       : *
                return_credentials: struct netr_Credential
                    data                     : 757b7dc81cc08542
            negotiate_flags          : *
                negotiate_flags          : 0x400241ff (1073889791)
                       1: NETLOGON_NEG_ACCOUNT_LOCKOUT
                       1: NETLOGON_NEG_PERSISTENT_SAMREPL
                       1: NETLOGON_NEG_ARCFOUR     
                       1: NETLOGON_NEG_PROMOTION_COUNT
                       1: NETLOGON_NEG_CHANGELOG_BDC
                       1: NETLOGON_NEG_FULL_SYNC_REPL
                       1: NETLOGON_NEG_MULTIPLE_SIDS
                       1: NETLOGON_NEG_REDO        
                       1: NETLOGON_NEG_PASSWORD_CHANGE_REFUSAL
                       0: NETLOGON_NEG_SEND_PASSWORD_INFO_PDC
                       0: NETLOGON_NEG_GENERIC_PASSTHROUGH
                       0: NETLOGON_NEG_CONCURRENT_RPC
                       0: NETLOGON_NEG_AVOID_ACCOUNT_DB_REPL
                       0: NETLOGON_NEG_AVOID_SECURITYAUTH_DB_REPL
                       1: NETLOGON_NEG_STRONG_KEYS 
                       0: NETLOGON_NEG_TRANSITIVE_TRUSTS
                       0: NETLOGON_NEG_DNS_DOMAIN_TRUSTS
                       1: NETLOGON_NEG_PASSWORD_SET2
                       0: NETLOGON_NEG_GETDOMAININFO
                       0: NETLOGON_NEG_CROSS_FOREST_TRUSTS
                       0: NETLOGON_NEG_NEUTRALIZE_NT4_EMULATION
                       0: NETLOGON_NEG_RODC_PASSTHROUGH
                       0: NETLOGON_NEG_SUPPORTS_AES_SHA2
                       0: NETLOGON_NEG_SUPPORTS_AES
                       0: NETLOGON_NEG_AUTHENTICATED_RPC_LSASS
                       1: NETLOGON_NEG_AUTHENTICATED_RPC
            result                   : NT_STATUS_OK
rpccli_netlogon_setup_creds: server KILIMANJARO credential chain established.
Bind RPC Pipe: host KILIMANJARO auth_type 2, auth_level 6
     &r: struct NL_AUTH_MESSAGE
        MessageType              : NL_NEGOTIATE_REQUEST (0x0)
        Flags                    : 0x00000003 (3)
               1: NL_FLAG_OEM_NETBIOS_DOMAIN_NAME
               1: NL_FLAG_OEM_NETBIOS_COMPUTER_NAME
               0: NL_FLAG_UTF8_DNS_DOMAIN_NAME
               0: NL_FLAG_UTF8_DNS_HOST_NAME
               0: NL_FLAG_UTF8_NETBIOS_COMPUTER_NAME
        oem_netbios_domain       : 'MOUNTAINS'
        oem_netbios_computer     : 'KILIMANJARO'
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 006e
    000a auth_len  : 001e
    000c call_id   : 00000016
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345678
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 cf fb 
        0030 version: 00000001
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
000048 smb_io_rpc_hdr_auth hdr_auth
    0048 auth_type    : 44
    0049 auth_level   : 06
    004a auth_pad_len : 00
    004b auth_reserved: 00
    004c auth_context_id: 00000001
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=110, this_data=110, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 005c
    000a auth_len  : 000c
    000c call_id   : 00000016
rpc_api_pipe: got frag len of 92 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 92 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 005c
    000a auth_len  : 000c
    000c call_id   : 00000016
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000f
        001a str: \PIPE\netlogon.
    000029 smb_io_rpc_results 
        002c num_results: 01
        0030 result     : 0000
        0032 reason     : 0000
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_schannel_with_key: opened pipe \netlogon to machine KILIMANJARO for domain MOUNTAINS and bound using schannel.
rpc_pipe_destructor: closed \netlogon
rpc_pipe_destructor: closed \netlogon
Locking key 534543524554532F5349
Allocated locked data 0x0x7fbf96cc0870
Unlocking key 534543524554532F5349
Locking key 534543524554532F4D41
Allocated locked data 0x0x7fbf96ce0bc0
Unlocking key 534543524554532F4D41
Locking key 534543524554532F4D41
Allocated locked data 0x0x7fbf96ce0bc0
Unlocking key 534543524554532F4D41
Locking key 534543524554532F4D41
Allocated locked data 0x0x7fbf96ce0cc0
Unlocking key 534543524554532F4D41
Locking key 534543524554532F4D41
Allocated locked data 0x0x7fbf96cc0b20
Unlocking key 534543524554532F4D41
Connecting to host=KILIMANJARO
Running timed event "tevent_req_timedout" 0x7fbf96cc0720
Connecting to 192.168.100.101 at port 445
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
    SO_SNDBUF = 50868
    SO_RCVBUF = 87744
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
cli_init_creds: user  domain 
saf_store: domain = [MOUNTAINS], server = [KILIMANJARO], expire = [1328613035]
Adding cache entry with key = SAF/DOMAIN/MOUNTAINS and timeout = Tue Feb  7 12:10:35 2012
 (900 seconds ahead)
Bind RPC Pipe: host KILIMANJARO auth_type 0, auth_level 1
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000017
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345678
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 cf fb 
        0030 version: 00000001
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=72, this_data=72, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000017
rpc_api_pipe: got frag len of 72 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 72 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0048
    000a auth_len  : 0000
    000c call_id   : 00000017
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000f
        001a str: \PIPE\netlogon.
    000029 smb_io_rpc_results 
        002c num_results: 01
        0030 result     : 0000
        0032 reason     : 0000
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_noauth: opened pipe \netlogon to machine KILIMANJARO and bound anonymously.
     netr_ServerReqChallenge: struct netr_ServerReqChallenge
        in: struct netr_ServerReqChallenge
            server_name              : *
                server_name              : '\\KILIMANJARO'
            computer_name            : *
                computer_name            : 'KILIMANJARO'
            credentials              : *
                credentials: struct netr_Credential
                    data                     : 71a1069cba5ef16d
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0070
    000a auth_len  : 0000
    000c call_id   : 00000018
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000058
    0014 context_id: 0000
    0016 opnum     : 0004
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=112, this_data=112, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0024
    000a auth_len  : 0000
    000c call_id   : 00000018
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 0000000c
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 36, data_len 12, ss_len 0
rpc_api_pipe: got frag len of 36 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 24 bytes.
     netr_ServerReqChallenge: struct netr_ServerReqChallenge
        out: struct netr_ServerReqChallenge
            return_credentials       : *
                return_credentials: struct netr_Credential
                    data                     : 1870b19a2b575dc0
            result                   : NT_STATUS_OK
     netr_ServerAuthenticate2: struct netr_ServerAuthenticate2
        in: struct netr_ServerAuthenticate2
            server_name              : *
                server_name              : '\\KILIMANJARO'
            account_name             : *
                account_name             : 'KILIMANJARO$'
            secure_channel_type      : SEC_CHAN_BDC (6)
            computer_name            : *
                computer_name            : 'KILIMANJARO'
            credentials              : *
                credentials: struct netr_Credential
                    data                     : 670ce2adb02a1d17
            negotiate_flags          : *
                negotiate_flags          : 0x600fffff (1611661311)
                       1: NETLOGON_NEG_ACCOUNT_LOCKOUT
                       1: NETLOGON_NEG_PERSISTENT_SAMREPL
                       1: NETLOGON_NEG_ARCFOUR     
                       1: NETLOGON_NEG_PROMOTION_COUNT
                       1: NETLOGON_NEG_CHANGELOG_BDC
                       1: NETLOGON_NEG_FULL_SYNC_REPL
                       1: NETLOGON_NEG_MULTIPLE_SIDS
                       1: NETLOGON_NEG_REDO        
                       1: NETLOGON_NEG_PASSWORD_CHANGE_REFUSAL
                       1: NETLOGON_NEG_SEND_PASSWORD_INFO_PDC
                       1: NETLOGON_NEG_GENERIC_PASSTHROUGH
                       1: NETLOGON_NEG_CONCURRENT_RPC
                       1: NETLOGON_NEG_AVOID_ACCOUNT_DB_REPL
                       1: NETLOGON_NEG_AVOID_SECURITYAUTH_DB_REPL
                       1: NETLOGON_NEG_STRONG_KEYS 
                       1: NETLOGON_NEG_TRANSITIVE_TRUSTS
                       1: NETLOGON_NEG_DNS_DOMAIN_TRUSTS
                       1: NETLOGON_NEG_PASSWORD_SET2
                       1: NETLOGON_NEG_GETDOMAININFO
                       1: NETLOGON_NEG_CROSS_FOREST_TRUSTS
                       0: NETLOGON_NEG_NEUTRALIZE_NT4_EMULATION
                       0: NETLOGON_NEG_RODC_PASSTHROUGH
                       0: NETLOGON_NEG_SUPPORTS_AES_SHA2
                       0: NETLOGON_NEG_SUPPORTS_AES
                       1: NETLOGON_NEG_AUTHENTICATED_RPC_LSASS
                       1: NETLOGON_NEG_AUTHENTICATED_RPC
000000 smb_io_rpc_hdr hdr    
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 00
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 009c
    000a auth_len  : 0000
    000c call_id   : 00000019
000010 smb_io_rpc_hdr_req hdr_req
    0010 alloc_hint: 00000084
    0014 context_id: 0000
    0016 opnum     : 000f
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=156, this_data=156, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 02
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 0028
    000a auth_len  : 0000
    000c call_id   : 00000019
000010 smb_io_rpc_hdr_resp rpc_hdr_resp
    0010 alloc_hint: 00000010
    0014 context_id: 0000
    0016 cancel_ct : 00
    0017 reserved  : 00
cli_pipe_validate_current_pdu: got pdu len 40, data_len 16, ss_len 0
rpc_api_pipe: got frag len of 40 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 32 bytes.
     netr_ServerAuthenticate2: struct netr_ServerAuthenticate2
        out: struct netr_ServerAuthenticate2
            return_credentials       : *
                return_credentials: struct netr_Credential
                    data                     : 06c67608088b075e
            negotiate_flags          : *
                negotiate_flags          : 0x400241ff (1073889791)
                       1: NETLOGON_NEG_ACCOUNT_LOCKOUT
                       1: NETLOGON_NEG_PERSISTENT_SAMREPL
                       1: NETLOGON_NEG_ARCFOUR     
                       1: NETLOGON_NEG_PROMOTION_COUNT
                       1: NETLOGON_NEG_CHANGELOG_BDC
                       1: NETLOGON_NEG_FULL_SYNC_REPL
                       1: NETLOGON_NEG_MULTIPLE_SIDS
                       1: NETLOGON_NEG_REDO        
                       1: NETLOGON_NEG_PASSWORD_CHANGE_REFUSAL
                       0: NETLOGON_NEG_SEND_PASSWORD_INFO_PDC
                       0: NETLOGON_NEG_GENERIC_PASSTHROUGH
                       0: NETLOGON_NEG_CONCURRENT_RPC
                       0: NETLOGON_NEG_AVOID_ACCOUNT_DB_REPL
                       0: NETLOGON_NEG_AVOID_SECURITYAUTH_DB_REPL
                       1: NETLOGON_NEG_STRONG_KEYS 
                       0: NETLOGON_NEG_TRANSITIVE_TRUSTS
                       0: NETLOGON_NEG_DNS_DOMAIN_TRUSTS
                       1: NETLOGON_NEG_PASSWORD_SET2
                       0: NETLOGON_NEG_GETDOMAININFO
                       0: NETLOGON_NEG_CROSS_FOREST_TRUSTS
                       0: NETLOGON_NEG_NEUTRALIZE_NT4_EMULATION
                       0: NETLOGON_NEG_RODC_PASSTHROUGH
                       0: NETLOGON_NEG_SUPPORTS_AES_SHA2
                       0: NETLOGON_NEG_SUPPORTS_AES
                       0: NETLOGON_NEG_AUTHENTICATED_RPC_LSASS
                       1: NETLOGON_NEG_AUTHENTICATED_RPC
            result                   : NT_STATUS_OK
rpccli_netlogon_setup_creds: server KILIMANJARO credential chain established.
Bind RPC Pipe: host KILIMANJARO auth_type 2, auth_level 6
     &r: struct NL_AUTH_MESSAGE
        MessageType              : NL_NEGOTIATE_REQUEST (0x0)
        Flags                    : 0x00000003 (3)
               1: NL_FLAG_OEM_NETBIOS_DOMAIN_NAME
               1: NL_FLAG_OEM_NETBIOS_COMPUTER_NAME
               0: NL_FLAG_UTF8_DNS_DOMAIN_NAME
               0: NL_FLAG_UTF8_DNS_HOST_NAME
               0: NL_FLAG_UTF8_NETBIOS_COMPUTER_NAME
        oem_netbios_domain       : 'MOUNTAINS'
        oem_netbios_computer     : 'KILIMANJARO'
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0b
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 006e
    000a auth_len  : 001e
    000c call_id   : 0000001a
000010 smb_io_rpc_hdr_rb 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 00000000
    0018 num_contexts: 01
    001c context_id  : 0000
    001e num_transfer_syntaxes: 01
    00001f smb_io_rpc_iface 
        000020 smb_io_uuid uuid
            0020 data   : 12345678
            0024 data   : 1234
            0026 data   : abcd
            0028 data   : ef 00 
            002a data   : 01 23 45 67 cf fb 
        0030 version: 00000001
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
000048 smb_io_rpc_hdr_auth hdr_auth
    0048 auth_type    : 44
    0049 auth_level   : 06
    004a auth_pad_len : 00
    004b auth_reserved: 00
    004c auth_context_id: 00000001
rpc_api_pipe: host KILIMANJARO
num_setup=2, max_setup=0, param_total=0, this_param=0, max_param=0, data_total=110, this_data=110, max_data=4280, param_offset=82, param_disp=0, data_disp=0
000000 smb_io_rpc_hdr rpc_hdr   
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 005c
    000a auth_len  : 000c
    000c call_id   : 0000001a
rpc_api_pipe: got frag len of 92 at offset 0: NT_STATUS_OK
rpc_api_pipe: host KILIMANJARO returned 92 bytes.
000000 smb_io_rpc_hdr hdr
    0000 major     : 05
    0001 minor     : 00
    0002 pkt_type  : 0c
    0003 flags     : 03
    0004 pack_type0: 10
    0005 pack_type1: 00
    0006 pack_type2: 00
    0007 pack_type3: 00
    0008 frag_len  : 005c
    000a auth_len  : 000c
    000c call_id   : 0000001a
000010 smb_io_rpc_hdr_ba 
    000010 smb_io_rpc_hdr_bba 
        0010 max_tsize: 10b8
        0012 max_rsize: 10b8
        0014 assoc_gid: 000053f0
    000018 smb_io_rpc_addr_str 
        0018 len: 000f
        001a str: \PIPE\netlogon.
    000029 smb_io_rpc_results 
        002c num_results: 01
        0030 result     : 0000
        0032 reason     : 0000
    000034 smb_io_rpc_iface 
        000034 smb_io_uuid uuid
            0034 data   : 8a885d04
            0038 data   : 1ceb
            003a data   : 11c9
            003c data   : 9f e8 
            003e data   : 08 00 2b 10 48 60 
        0044 version: 00000002
check_bind_response: accepted!
cli_rpc_pipe_open_schannel_with_key: opened pipe \netlogon to machine KILIMANJARO for domain MOUNTAINS and bound using schannel.
rpc_pipe_destructor: closed \netlogon
rpc_pipe_destructor: closed \netlogon
write_socket(10,39)
write_socket(10,39) wrote 39
got smb length of 35
size=35
smb_com=0x71
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51203
smb_tid=1
smb_pid=13351
smb_uid=100
smb_mid=12
smt_wct=0
smb_bcc=0
write_socket(5,39)
write_socket(5,39) wrote 39
got smb length of 35
size=35
smb_com=0x71
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51203
smb_tid=1
smb_pid=13351
smb_uid=100
smb_mid=30
smt_wct=0
smb_bcc=0
return code = 0But, when I try to join Windows 7 machine to Linux SAMBA PDC (I'tweaked wins 7 registry as instructed in [http://www.1stbyte.com/2009/05/31/join-windows-7-to-samba-pdc/](http://www.1stbyte.com/2009/05/31/join-windows-7-to-samba-pdc/)), I get following error, which shown in attached screenshot. Why am I getting this error?

---

### Post by MakroSiroki on 2012-02-19
What does excatly the error in image attachement mean?

---

### Post by MakroSiroki on 2012-03-03
Did not help, but I've managed to join windows 7 machine to SAMBA PDC !!! I had Windows 7 Service netlogon.exe setup as my account ran it, not Local Network Service, but now I cannot logon into domain with my username (I've added my username via smbuseradd), I get following error at Windows 7 login screen:
> The trust relationship between this workstation and the primary domain controller failed.
Offtopic: How do I take screenshot of Windows Logon Error, since PrtScreen does not work?

---

