---
title: "Samba4 not visible in Windows Discovery Network"
date: 2018-02-22
forum: Server Platforms
---

### Post by msv1500 on 2018-02-22
[COLOR=#242729][FONT=Arial]Please help me with configuration of Samba 4 (Version 4.3.11-Ubuntu, Ubuntu 16.04.3 LTS) and windows workgroup. My problem: samba server (blue computer icon) doens't appear in Microsoft Windows Discovery Network. I can connect to samba server via \\SAMBASRV, I can write to samba's shares and I can attache samba's shares to windows machine via network drive. Of course, samba and windows machines have the same group name. I enabled samba as WINS server and manually wrote samba's IP-address on each windows machine. Of course, I enabled NetBIOS over TCP option. I use only workgroup, without domain and all windows machines in network are Win7 (HB, Prof). I tried to execute smbtree command and I returned correct info from samba's shares and windows machines. Also I cheched /var/cache/samba/browse.dat file and it had correct records of network members with local disks and shares. I disabled firewall on ununtu (ufw) and windows machines - no changes.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My Samba4 configuration (testparm result):

[/FONT][/COLOR]```

# Global parameters
    [global]
    dos charset = CP850
    unix charset = UTF-8
    workgroup = MYGROUP
    realm =
    netbios name = SAMBASRV
    netbios aliases =
    netbios scope =
    server string = %h server (Sambasrv, Samba, Ubuntu)
    interfaces = enp3s0 lo
    bind interfaces only = Yes
    config backend = file
    server role = standalone server
    security = USER
    auth methods =
    encrypt passwords = data
    client schannel = Auto
    server schannel = Auto
    allow trusted domains = Yes
    map to guest = Bad User
    null passwords = No
    old password allowed period = 60
    obey pam restrictions = Yes
    password server = *
    smb passwd file = /etc/samba/smbpasswd
    private dir = /var/lib/samba/private
    passdb backend = tdbsam
    algorithmic rid base = 1000
    root directory =
    guest account = nobody
    enable privileges = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd chat debug = No
    passwd chat timeout = 2
    check password script =
    username map =
    username level = 0
    unix password sync = No
    restrict anonymous = 0
    lanman auth = No
    ntlm auth = Yes
    raw NTLMv2 auth = No
    client NTLMv2 auth = Yes
    client lanman auth = No
    client plaintext auth = No
    client use spnego principal = No
    preload modules =
    dedicated keytab file =
    kerberos method = default
    map untrusted to domain = No
    log level = 2
    syslog = 1
    syslog only = No
    log file = /var/log/samba/log.%m
    logging =
    max log size = 0
    debug timestamp = Yes
    timestamp logs = Yes
    debug prefix timestamp = No
    debug hires timestamp = Yes
    debug pid = No
    debug uid = No
    debug class = No
    enable core files = Yes
    smb ports = 445 139
    large readwrite = Yes
    server max protocol = SMB3
    max protocol = SMB3
    protocol = SMB3
    server min protocol = LANMAN1
    min protocol = LANMAN1
    client max protocol = default
    client min protocol = CORE
    unicode = Yes
    min receivefile size = 0
    read raw = Yes
    write raw = Yes
    disable netbios = No
    reset on zero vc = No
    log writeable files on exit = No
    defer sharing violations = Yes
    nt pipe support = Yes
    nt status support = Yes
    smbd profiling level = off
    max mux = 50
    max xmit = 16644
    name resolve order = bcast hosts lmhosts wins
    max ttl = 259200
    max wins ttl = 518400
    min wins ttl = 21600
    time server = No
    unix extensions = Yes
    use spnego = Yes
    client signing = default
    server signing = default
    client use spnego = Yes
    client ldap sasl wrapping = sign
    ldap server require strong auth = Yes
    enable asu support = No
    svcctl list =
    cldap port = 389
    dgram port = 138
    nbt port = 137
    krb5 port = 88
    kpasswd port = 464
    web port = 901
    rpc big endian = No
    deadtime = 0
    getwd cache = Yes
    keepalive = 300
    change notify = Yes
    kernel change notify = Yes
    lpq cache time = 30
    max smbd processes = 0
    max disk size = 0
    max open files = 16384
    socket options = TCP_NODELAY
    use mmap = Yes
    hostname lookups = No
    name cache timeout = 660
    ctdbd socket =
    cluster addresses =
    clustering = No
    ctdb timeout = 0
    ctdb locktime warn threshold = 0
    smb2 max read = 8388608
    smb2 max write = 8388608
    smb2 max trans = 8388608
    smb2 max credits = 8192
    load printers = No
    printcap cache time = 0
    printcap name = /dev/null
    cups server =
    cups encrypt = No
    cups connection timeout = 30
    iprint server =
    disable spoolss = Yes
    addport command =
    enumports command =
    addprinter command =
    deleteprinter command =
    show add printer wizard = Yes
    os2 driver map =
    mangling method = hash2
    mangle prefix = 1
    max stat cache size = 256
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
    username map cache time = 0
    logon script =
    logon path = \\%N\%U\profile
    logon drive =
    logon home = \\%N\%U
    domain logons = No
    init logon delayed hosts =
    init logon delay = 100
    os level = 255
    lm announce = Auto
    lm interval = 60
    preferred master = Yes
    local master = Yes
    domain master = Yes
    browse list = Yes
    enhanced browsing = Yes
    dns proxy = No
    wins proxy = No
    wins server =
    wins support = Yes
    wins hook =
    smb2 leases = No
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
    ldap ssl = start tls
    ldap ssl ads = No
    ldap deref = auto
    ldap follow referral = Auto
    ldap timeout = 15
    ldap connection timeout = 2
    ldap page size = 1024
    ldap user suffix =
    ldap debug level = 0
    ldap debug threshold = 10
    eventlog list =
    add share command =
    change share command =
    delete share command =
    config file =
    preload =
    auto services =
    lock directory = /var/run/samba
    state directory = /var/lib/samba
    cache directory = /var/cache/samba
    pid directory = /var/run/samba
    ntp signd socket directory = /var/lib/samba/ntp_signd
    utmp directory =
    wtmp directory =
    utmp = No
    default service =
    default =
    message command =
    get quota command =
    set quota command =
    remote announce =
    remote browse sync =
    nbt client socket address = 0.0.0.0
    socket address = 0.0.0.0
    nmbd bind explicit broadcast = Yes
    homedir map = auto.home
    afs username map =
    afs token lifetime = 604800
    log nt token command =
    NIS homedir = No
    registry shares = No
    usershare allow guests = No
    usershare max shares = 100
    usershare owner only = Yes
    usershare path = /var/lib/samba/usershares
    usershare prefix allow list =
    usershare prefix deny list =
    usershare template share =
    allow insecure wide links = No
    async smb echo handler = No
    panic action = /usr/share/samba/panic-action %d
    perfcount module =
    host msdfs = Yes
    passdb expand explicit = No
    idmap backend = tdb
    idmap cache time = 604800
    idmap negative cache time = 120
    idmap uid =
    idmap gid =
    template homedir = /home/%D/%U
    template shell = /bin/false
    winbind separator = \
    winbind cache time = 300
    winbind reconnect delay = 30
    winbind request timeout = 60
    winbind max clients = 200
    winbind enum users = No
    winbind enum groups = No
    winbind use default domain = No
    winbind trusted domains only = No
    winbind nested groups = Yes
    winbind expand groups = 0
    winbind nss info = template
    winbind refresh tickets = No
    winbind offline logon = No
    winbind normalize names = No
    winbind rpc only = No
    create krb5 conf = Yes
    ncalrpc dir = /var/run/samba/ncalrpc
    winbind max domain connections = 1
    winbindd socket directory = /var/run/samba/winbindd
    winbindd privileged socket directory = /var/lib/samba/winbindd_privileged
    winbind sealed pipes = Yes
    neutralize nt4 emulation = No
    reject md5 servers = No
    require strong key = Yes
    allow dns updates = secure only
    dns forwarder =
    dns update command = /usr/sbin/samba_dnsupdate
    nsupdate command = /usr/bin/nsupdate -g
    rndc command = /usr/sbin/rndc
    multicast dns register = Yes
    samba kcc command = /usr/sbin/samba_kcc
    server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbindd, ntp_signd, kcc, dnsupdate, dns
    dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver
    spn update command = /usr/sbin/samba_spnupdate
    share backend = classic
    allow nt4 crypto = No
    reject md5 clients = No
    tls enabled = Yes
    tls keyfile = tls/key.pem
    tls certfile = tls/cert.pem
    tls cafile = tls/ca.pem
    tls crlfile =
    tls dh params file =
    tls priority = NORMAL:-VERS-SSL3.0
    tls verify peer = as_strict_as_possible
    client ipc max protocol = default
    client ipc min protocol = default
    client ipc signing = default
    allow dcerpc auth level connect = No
    idmap config * : backend = tdb
    comment =
    path =
    username =
    invalid users =
    valid users =
    admin users =
    read list =
    write list =
    force user =
    force group =
    group =
    read only = Yes
    spotlight = No
    acl check permissions = Yes
    acl group control = No
    acl map full control = Yes
    acl allow execute always = No
    create mask = 0744
    force create mode = 0000
    directory mask = 0755
    directory mode = 0755
    force directory mode = 0000
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
    smb encrypt = default
    durable handles = Yes
    block size = 1024
    directory name cache size = 100
    max connections = 0
    min print space = 0
    strict allocate = No
    strict rename = No
    strict sync = No
    sync always = No
    use sendfile = No
    write cache size = 0
    max reported print jobs = 0
    max print jobs = 1000
    printable = No
    print notify backchannel = No
    printing = bsd
    cups options =
    print command = lpr -r -P'%p' %s
    lpq command = lpq -P'%p'
    lprm command = lprm -P'%p' %j
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
    store dos attributes = No
    dmapi support = No
    browseable = Yes
    access based share enum = No
    blocking locks = Yes
    csc policy = manual
    fake oplocks = No
    kernel oplocks = No
    kernel share modes = Yes
    locking = Yes
    oplocks = Yes
    level2 oplocks = Yes
    oplock contention limit = 2
    posix locking = Yes
    strict locking = Auto
    dfree cache time = 0
    dfree command =
    include =
    preexec =
    exec =
    preexec close = No
    postexec =
    root preexec =
    root preexec close = No
    root postexec =
    available = Yes
    volume =
    fstype = NTFS
    wide links = No
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
    msdfs shuffle referrals = No
    ntvfs handler = unixuid, default




    [MYSHARE]
    path = /samba/shares/MYSHARE
    valid users = @mygrp
    force group = mygrp
    group = mygrp
    read only = No
    create mask = 0770
    directory mask = 0770
    directory mode = 0770
    hide special files = Yes
    hide files = /~*/
    vfs objects = recycle
    recycle:versions = Yes
    recycle:excludedir = /tmp|/temp|/cache
    recycle:exclude = *.tmp, *.temp, *.o, *.obj, ~$*, *.~??, *.trace, *.TMP, *.TEMP, *.O, *.OBJ, *.TRACE
    recycle:maxsize = 0
    recycle:mode = KEEP_DIRECTORIES|VERSIONS|TOUCH
    recycle:repository = /samba/shares/MYSHARE/RECBIN/%U

```[COLOR=#242729][FONT=Arial]

I don't have any ideas about my problem. Please let me know where is my mistake?[/FONT][/COLOR]

---

### Post by Morbius1 on 2018-02-22
You realize no one will help you with that right? It looks like what happens when someone uses gadmin-samba. 

Anyhoo, I would like to point out the only thing that is obvious to me:

I took what you said was the output of testparm, saved it to a file in my home directory ( smb.txt ), and ran testparm on it:
> tester@vub-16041:~$ testparm -s smb.txt
Load smb config files from smb.txt
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
[COLOR=#0000cd]**set_variable_helper(data): value is not boolean!**[/COLOR]
Error loading services.
Took a bit but in your post is this listing:
> encrypt passwords = data
It should either be yes or no. I suspect you wanted yes.
After fixing that in smb.txt and running testparm again you get the typical output after gadmin-samba is used:
> tester@vub-16041:~$ testparm -s smb.txt
Load smb config files from smb.txt
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "null passwords" option is deprecated
WARNING: The "enable privileges" option is deprecated
WARNING: The "client use spnego principal" option is deprecated
WARNING: The "syslog" option is deprecated
WARNING: The "syslog only" option is deprecated
WARNING: The "use spnego" option is deprecated
WARNING: The "dgram port" option is deprecated
WARNING: The "nbt port" option is deprecated
WARNING: The "nbt client socket address" option is deprecated
WARNING: The "socket address" option is deprecated
WARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
WARNING: The "username" option is deprecated
WARNING: The "acl check permissions" option is deprecated
WARNING: The "only user" option is deprecated
Can't find include file 
Processing section "[MYSHARE]"
Loaded services file OK.
ERROR: the 'winbind separator' parameter must be a single character.

---

### Post by msv1500 on 2018-02-22
Thank you for your response.

> **Morbius1 said:**
> [COLOR=#000000]*encrypt passwords = data*[/COLOR]
[COLOR=#000000]It should either be yes or no. I suspect you wanted yes.[/COLOR]
You are absolutely right. This value is "yes" in current output of testparm -v. I exported config again and checked it (only this position was wrong).

---

### Post by msv1500 on 2018-02-22
I run testparm /etc/samba/smb.conf and discovered, that output didn't have 'netbios name' parameter. 
I changed netbios name to other value and 'netbios name' string appeared in testparm /etc/samba/smb.conf output. When netbios name is equal hostname value - it didn't appeared in output. Current output of testparm /etc/samba/smb.conf

testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog only" option is deprecated
Processing section "[MYSHARE]"
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
        workgroup = MYGROUP
netbios name = newname
        server string = %h server (Newname, Samba, Ubuntu)
        server role = standalone server
        security = USER
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        log file = /var/log/samba/log.%m
        max log size = 0
        name resolve order = bcast hosts lmhosts wins
        load printers = No
        printcap cache time = 0
        printcap name = /dev/null
        disable spoolss = Yes
        os level = 255
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        printing = bsd

---

### Post by Morbius1 on 2018-02-22
> I run testparm /etc/samba/smb.conf and discovered, that output didn't have 'netbios name' parameter. 

It wouldn't. 

Run testparm this way:
```
testparm -sv /dev/null | grep "netbios name"
```
[COLOR=#0000cd]*You are running testparm against an empty file so the only thing you will get are the default settings of samba. *[/COLOR]

What you will see is that the "netbios name" is automatically set to your hostname. Samba does this by itself.

If you run testparm without specifying the file name it automatically tests /etc/samba/smb.conf and without the "v" operator only tests smb.conf itself. smb.conf is not the samba configuration file. It represents a set of additions or overrides to the default settings of samba. When you run testparm it shows you the result your smb.conf has on those defaults.

If you set the netbios name to your hostname in smb.conf it has no affect ( therefore no output ) since the default is already set to that. Change it to something else and testparm shows you it listed.

---

