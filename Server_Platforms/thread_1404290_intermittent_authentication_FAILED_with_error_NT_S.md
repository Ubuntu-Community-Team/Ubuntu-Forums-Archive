---
title: "intermittent authentication: FAILED with error NT_STATUS_ACCESS_DENIED"
date: 2010-02-11
forum: Server Platforms
---

### Post by plut0 on 2010-02-11
OS: Ubuntu 8.04.3 LTS
Kernel: 2.6.24-23-server x86_64
Samba: 3.0.28a-1ubuntu4.9

We are having intermittent authentication issues with some windows clients connecting to our samba server.  Sometimes it works fine, sometimes it fails miserably and continually.  I'm not sure how to reproduce the issue everytime but it does happen every single day.  Looking for some help.


testparm -v:
```
[global]
    dos charset = CP850
    unix charset = UTF-8
    display charset = LOCALE
    workgroup = SOMEDOMAIN
    realm = SOMEDOMAIN.COM
    netbios name = SAMBASERVER
    netbios aliases = SMB
    netbios scope =
    server string = FileServer
    interfaces = eth0
    bind interfaces only = No
    security = ADS
    auth methods =
    encrypt passwords = Yes
    update encrypted = No
    client schannel = Auto
    server schannel = Auto
    allow trusted domains = Yes
    map to guest = Never
    null passwords = No
    obey pam restrictions = Yes
    password server = DC1, DC2, *
    smb passwd file = /etc/samba/smbpasswd
    private dir = /etc/samba
    passdb backend = smbpasswd
    algorithmic rid base = 1000
    root directory =
    guest account = nobody
    enable privileges = Yes
    pam password change = No
    passwd program =
    passwd chat = *new*password* %n\n *new*password* %n\n *changed*
    passwd chat debug = No
    passwd chat timeout = 2
    check password script =
    username map =
    password level = 0
    username level = 0
    unix password sync = No
    restrict anonymous = 1
    lanman auth = Yes
    ntlm auth = Yes
    client NTLMv2 auth = No
    client lanman auth = Yes
    client plaintext auth = Yes
    preload modules =
    use kerberos keytab = No
    log level = 0
    syslog = 1
    syslog only = No
    log file = /var/log/samba/%m.log
    max log size = 5000
    debug timestamp = Yes
    debug prefix timestamp = No
    debug hires timestamp = No
    debug pid = No
    debug uid = No
    enable core files = Yes
    smb ports = 445 139
    large readwrite = Yes
    max protocol = NT1
    min protocol = CORE
    read bmpx = No
    read raw = Yes
    write raw = Yes
    disable netbios = No
    reset on zero vc = No
    acl compatibility = auto
    defer sharing violations = Yes
    nt pipe support = Yes
    nt status support = Yes
    announce version = 4.9
    announce as = NT
    max mux = 50
    max xmit = 16644
    name resolve order = lmhosts wins host bcast
    max ttl = 259200
    max wins ttl = 518400
    min wins ttl = 21600
    time server = No
    unix extensions = No
    use spnego = Yes
    client signing = auto
    server signing = No
    client use spnego = Yes
    enable asu support = No
    svcctl list =
    deadtime = 0
    getwd cache = Yes
    keepalive = 300
    lpq cache time = 30
    max smbd processes = 0
    paranoid server security = Yes
    max disk size = 0
    max open files = 10000
    open files database hash size = 10007
    socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
    use mmap = Yes
    hostname lookups = No
    name cache timeout = 660
    load printers = Yes
    printcap cache time = 750
    printcap name = cups
    cups server =
    iprint server =
    disable spoolss = No
    addport command =
    enumports command =
    addprinter command =
    deleteprinter command =
    show add printer wizard = Yes
    os2 driver map =
    mangling method = hash2
    mangle prefix = 1
    max stat cache size = 1024
    stat cache = Yes
    machine password timeout = 604800
    add user script =
    rename user script =
    delete user script =
    add group script =
    delete group script =
    add user to group script =
    delete user from group script =
    set primary group script =
    add machine script =
    shutdown script =
    abort shutdown script =
    username map script =
    logon script =
    logon path = \\%N\%U\profile
    logon drive =
    logon home = \\%N\%U
    domain logons = No
    os level = 20
    lm announce = Auto
    lm interval = 60
    preferred master = No
    local master = No
    domain master = No
    browse list = Yes
    enhanced browsing = Yes
    dns proxy = Yes
    wins proxy = No
    wins server = a.b.c.d
    wins support = No
    wins hook =
    kernel oplocks = Yes
    lock spin time = 200
    oplock break wait time = 0
    ldap admin dn =
    ldap delete dn = No
    ldap group suffix =
    ldap idmap suffix =
    ldap machine suffix =
    ldap passwd sync = no
    ldap replication sleep = 1000
    ldap suffix =
    ldap ssl = no
    ldap timeout = 15
    ldap page size = 1024
    ldap user suffix =
    ldap debug level = 0
    ldap debug threshold = 10
    add share command =
    change share command =
    delete share command =
    eventlog list =
    config file =
    preload =
    lock directory =
    pid directory = /var/run/samba
    utmp directory =
    wtmp directory =
    utmp = No
    default service =
    message command =
    get quota command =
    set quota command =
    remote announce =
    remote browse sync =
    socket address = 0.0.0.0
    homedir map = auto.home
    afs username map =
    afs token lifetime = 604800
    log nt token command =
    time offset = 0
    NIS homedir = No
    usershare allow guests = No
    usershare max shares = 0
    usershare owner only = Yes
    usershare path = /var/lib/samba/usershares
    usershare prefix allow list =
    usershare prefix deny list =
    usershare template share =
    panic action =
    host msdfs = Yes
    passdb expand explicit = No
    idmap domains =
    idmap backend =
    idmap alloc backend =
    idmap cache time = 900
    idmap negative cache time = 120
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    template homedir = /samba/homes/%D+%U
    template shell = /bin/bash
    winbind separator = +
    winbind cache time = 300
    winbind enum users = No
    winbind enum groups = No
    winbind use default domain = No
    winbind trusted domains only = No
    winbind nested groups = Yes
    winbind nss info = template
    winbind refresh tickets = Yes
    winbind offline logon = No
    winbind normalize names = No
    comment =
    path =
    username =
    invalid users =
    valid users =
    admin users =
    read list =
    write list =
    printer admin =
    force user =
    force group =
    read only = Yes
    acl check permissions = Yes
    acl group control = No
    acl map full control = Yes
    create mask = 0740
    force create mode = 00
    security mask = 0777
    force security mode = 00
    directory mask = 0755
    force directory mode = 00
    directory security mask = 0777
    force directory security mode = 00
    force unknown acl user = No
    inherit permissions = No
    inherit acls = No
    inherit owner = No
    guest only = No
    administrative share = No
    guest ok = No
    only user = No
    hosts allow =
    hosts deny =
    allocation roundup size = 1048576
    aio read size = 0
    aio write size = 0
    aio write behind =
    ea support = No
    nt acl support = Yes
    profile acls = No
    map acl inherit = No
    afs share = No
    block size = 1024
    change notify = No
    directory name cache size = 100
    kernel change notify = Yes
    max connections = 0
    min print space = 0
    strict allocate = No
    strict sync = No
    sync always = No
    use sendfile = No
    write cache size = 0
    max reported print jobs = 0
    max print jobs = 1000
    printable = No
    printing = cups
    cups options = raw
    print command =
    lpq command = %p
    lprm command =
    lppause command =
    lpresume command =
    queuepause command =
    queueresume command =
    printer name =
    use client driver = No
    default devmode = Yes
    force printername = No
    printjob username = %U
    default case = lower
    case sensitive = Auto
    preserve case = Yes
    short preserve case = Yes
    mangling char = ~
    hide dot files = Yes
    hide special files = No
    hide unreadable = No
    hide unwriteable files = No
    delete veto files = No
    veto files =
    hide files =
    veto oplock files =
    map archive = Yes
    map hidden = No
    map system = No
    map readonly = yes
    mangled names = Yes
    mangled map =
    store dos attributes = No
    dmapi support = No
    browseable = Yes
    blocking locks = Yes
    csc policy = manual
    fake oplocks = No
    locking = Yes
    oplocks = Yes
    level2 oplocks = Yes
    oplock contention limit = 2
    posix locking = Yes
    strict locking = Auto
    share modes = Yes
    dfree cache time = 0
    dfree command =
    copy =
    include =
    preexec =
    preexec close = No
    postexec =
    root preexec =
    root preexec close = No
    root postexec =
    available = Yes
    volume =
    fstype = NTFS
    set directory = No
    wide links = Yes
    follow symlinks = Yes
    dont descend =
    magic script =
    magic output =
    delete readonly = No
    dos filemode = No
    dos filetimes = Yes
    dos filetime resolution = No
    fake directory create times = No
    vfs objects =
    msdfs root = No
    msdfs proxy =


[shared]
    comment = Shared Area
    path = /smb/shared
    read only = No
    create mask = 0770
    force security mode = 0700
    inherit acls = Yes
    hide unreadable = Yes
    vfs objects = audit, shadow_copy
```

Here is the log from the client:
```
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17181 of length 270
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_spnego_negotiate(697)
  reply_spnego_negotiate: Got secblob of size 40
[2010/01/27 19:02:21, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0xa2088207
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17182 of length 292
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:21, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[] domain=[] workstation=[SERVER3] len1=1 len2=0
[2010/01/27 19:02:21, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user []\[]@[SERVER3] with the new password interface
[2010/01/27 19:02:21, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [SOMEDOMAIN]\[]@[SERVER3]
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] auth/auth.c:check_ntlm_password(270)
  check_ntlm_password: guest authentication for user [] succeeded
[2010/01/27 19:02:21, 3] passdb/lookup_sid.c:fetch_gid_from_cache(1107)
  fetch gid from cache 10747 -> S-1-5-32-544
[2010/01/27 19:02:21, 3] passdb/lookup_sid.c:fetch_gid_from_cache(1107)
  fetch gid from cache 10748 -> S-1-5-32-545
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-21-1548514525-1597833445-1171576397-501]
[2010/01/27 19:02:21, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2010/01/27 19:02:21, 3] lib/privileges.c:get_privileges(261)
  get_privileges: No privileges assigned to SID [S-1-5-32-546]
[2010/01/27 19:02:21, 3] libsmb/ntlmssp_sign.c:ntlmssp_sign_init(338)
  NTLMSSP Sign/Seal - Initialising with flags:
[2010/01/27 19:02:21, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0xa2088205
[2010/01/27 19:02:21, 3] smbd/password.c:register_vuid(304)
  User name: nobody    Real name: nobody
[2010/01/27 19:02:21, 3] smbd/password.c:register_vuid(325)
  UNIX uid 65534 is UNIX user nobody, and will be vuid 218
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17183 of length 76
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBtconX (pid 25287) conn 0x0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/service.c:make_connection_snum(815)
  Connect path is '/tmp' for service [IPC$]
[2010/01/27 19:02:21, 3] lib/util_seaccess.c:se_access_check(250)
[2010/01/27 19:02:21, 3] lib/util_seaccess.c:se_access_check(251)
  se_access_check: user sid is S-1-5-21-1548514525-1597833445-1171576397-501
  se_access_check: also S-1-1-0
  se_access_check: also S-1-5-2
  se_access_check: also S-1-5-32-546
[2010/01/27 19:02:21, 3] smbd/vfs.c:vfs_init_default(95)
  Initialising default vfs hooks
[2010/01/27 19:02:21, 3] smbd/vfs.c:vfs_init_custom(128)
  Initialising custom vfs hooks from [/[Default VFS]/]
[2010/01/27 19:02:21, 3] lib/util_seaccess.c:se_access_check(250)
[2010/01/27 19:02:21, 3] lib/util_seaccess.c:se_access_check(251)
  se_access_check: user sid is S-1-5-21-1548514525-1597833445-1171576397-501
  se_access_check: also S-1-1-0
  se_access_check: also S-1-5-2
  se_access_check: also S-1-5-32-546
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/service.c:make_connection_snum(1042)
  server3 (1.2.3.4) connect to service IPC$ initially as user nobody (uid=65534, gid=65534) (pid 25287)
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/reply.c:reply_tcon_and_X(574)
  tconX service=IPC$
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17184 of length 80
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6602) cmd=50 (SMBtrans2) NT_STATUS_NETWORK_ACCESS_DENIED
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17185 of length 98
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:21, 3] smbd/msdfs.c:get_referred_path(633)
  get_referred_path: |shared| in dfs path \sambaserver\shared is not a dfs root.
[2010/01/27 19:02:21, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6307) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17186 of length 270
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_spnego_negotiate(697)
  reply_spnego_negotiate: Got secblob of size 40
[2010/01/27 19:02:21, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0xa2088207
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17187 of length 376
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:21, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[someuser] domain=[SOMEDOMAIN] workstation=[SERVER3] len1=24 len2=24
[2010/01/27 19:02:21, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [SOMEDOMAIN]\[someuser]@[SERVER3] with the new password interface
[2010/01/27 19:02:21, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [SOMEDOMAIN]\[someuser]@[SERVER3]
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [someuser] -> [someuser] FAILED with error NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:21, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17188 of length 80
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6602) cmd=50 (SMBtrans2) NT_STATUS_NETWORK_ACCESS_DENIED
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17189 of length 98
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:21, 3] smbd/msdfs.c:get_referred_path(633)
  get_referred_path: |shared| in dfs path \sambaserver\shared is not a dfs root.
[2010/01/27 19:02:21, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6307) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
[2010/01/27 19:02:21, 3] smbd/process.c:process_smb(1083)
  Transaction 17190 of length 270
[2010/01/27 19:02:21, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:21, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:21, 3] smbd/sesssetup.c:reply_spnego_negotiate(697)
  reply_spnego_negotiate: Got secblob of size 40
[2010/01/27 19:02:21, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0xa2088207
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17191 of length 376
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:22, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[someuser] domain=[SOMEDOMAIN] workstation=[SERVER3] len1=24 len2=24
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [SOMEDOMAIN]\[someuser]@[SERVER3] with the new password interface
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [SOMEDOMAIN]\[someuser]@[SERVER3]
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [someuser] -> [someuser] FAILED with error NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17192 of length 80
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6602) cmd=50 (SMBtrans2) NT_STATUS_NETWORK_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17193 of length 98
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:22, 3] smbd/msdfs.c:get_referred_path(633)
  get_referred_path: |shared| in dfs path \sambaserver\shared is not a dfs root.
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6307) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17194 of length 270
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_spnego_negotiate(697)
  reply_spnego_negotiate: Got secblob of size 40
[2010/01/27 19:02:22, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0xa2088207
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17195 of length 376
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:22, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[someuser] domain=[SOMEDOMAIN] workstation=[SERVER3] len1=24 len2=24
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [SOMEDOMAIN]\[someuser]@[SERVER3] with the new password interface
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [SOMEDOMAIN]\[someuser]@[SERVER3]
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [someuser] -> [someuser] FAILED with error NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17196 of length 80
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6602) cmd=50 (SMBtrans2) NT_STATUS_NETWORK_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17197 of length 98
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:22, 3] smbd/msdfs.c:get_referred_path(633)
  get_referred_path: |shared| in dfs path \sambaserver\shared is not a dfs root.
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6307) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17198 of length 270
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_spnego_negotiate(697)
  reply_spnego_negotiate: Got secblob of size 40
[2010/01/27 19:02:22, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0xa2088207
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17199 of length 376
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:22, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[someuser] domain=[SOMEDOMAIN] workstation=[SERVER3] len1=24 len2=24
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [SOMEDOMAIN]\[someuser]@[SERVER3] with the new password interface
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [SOMEDOMAIN]\[someuser]@[SERVER3]
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [someuser] -> [someuser] FAILED with error NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17200 of length 80
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (65534, 65534) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6602) cmd=50 (SMBtrans2) NT_STATUS_NETWORK_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17201 of length 98
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBtrans2 (pid 25287) conn 0xbb3830
[2010/01/27 19:02:22, 3] smbd/msdfs.c:get_referred_path(633)
  get_referred_path: |shared| in dfs path \sambaserver\shared is not a dfs root.
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/trans2.c(6307) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17202 of length 270
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_spnego_negotiate(697)
  reply_spnego_negotiate: Got secblob of size 40
[2010/01/27 19:02:22, 3] libsmb/ntlmssp.c:debug_ntlmssp_flags(63)
  Got NTLMSSP neg_flags=0xa2088207
[2010/01/27 19:02:22, 3] smbd/process.c:process_smb(1083)
  Transaction 17203 of length 376
[2010/01/27 19:02:22, 3] smbd/process.c:switch_message(932)
  switch message SMBsesssetupX (pid 25287) conn 0x0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X(1253)
  wct=12 flg2=0xc807
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1038)
  Doing spnego session setup
[2010/01/27 19:02:22, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1069)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2010/01/27 19:02:22, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[someuser] domain=[SOMEDOMAIN] workstation=[SERVER3] len1=24 len2=24
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [SOMEDOMAIN]\[someuser]@[SERVER3] with the new password interface
[2010/01/27 19:02:22, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [SOMEDOMAIN]\[someuser]@[SERVER3]
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:push_sec_ctx(208)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/uid.c:push_conn_ctx(358)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/01/27 19:02:22, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/01/27 19:02:22, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [someuser] -> [someuser] FAILED with error NT_STATUS_ACCESS_DENIED
[2010/01/27 19:02:22, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_ACCESS_DENIED
```

---

