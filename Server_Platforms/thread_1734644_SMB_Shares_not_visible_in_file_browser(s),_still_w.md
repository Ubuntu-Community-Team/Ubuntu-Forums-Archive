---
title: "SMB Shares not visible in file browser(s), still work"
date: 2011-04-20
forum: Server Platforms
---

### Post by Vectorferret on 2011-04-20
I set up an Ubuntu server install yesterday. I have used Ubuntu desktop for quite some time and have no issue with command line. I have everything working, except SMB shares. The share still works if I enter it's path manually (//server/share) but even shares I want to be viewable by browsing are not. (Attempted to browse in Nautilus, Windows and Mac file managers.) Server is running 10.10 (AMD64).

Dump of smb.conf (generated with SWAT, which also works otherwise) follows. Solution with either SWAT or editing the file manually is fine.
```
# Samba config file created using SWAT
# from UNKNOWN (192.168.0.100)
# Date: 2011/04/20 14:24:19

[global]
    dos charset = CP850
    unix charset = UTF-8
    display charset = LOCALE
    workgroup = WORKGROUP
    realm = 
    netbios name = LAGAVULIN
    netbios aliases = 
    netbios scope = 
    server string = %h server (Samba, Ubuntu)
    interfaces = 
    bind interfaces only = No
    security = USER
    auth methods = guest, sam
    encrypt passwords = Yes
    update encrypted = No
    client schannel = Auto
    server schannel = Auto
    allow trusted domains = Yes
    map to guest = Bad User
    null passwords = No
    obey pam restrictions = Yes
    password server = *
    smb passwd file = /etc/samba/smbpasswd
    private dir = /etc/samba
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
    password level = 0
    username level = 0
    unix password sync = Yes
    restrict anonymous = 0
    lanman auth = No
    ntlm auth = Yes
    client NTLMv2 auth = No
    client lanman auth = No
    client plaintext auth = No
    preload modules = 
    dedicated keytab file = 
    kerberos method = default
    map untrusted to domain = No
    log level = 0
    syslog = 0
    syslog only = No
    log file = /var/log/samba/log.%m
    max log size = 1000
    debug timestamp = Yes
    debug prefix timestamp = No
    debug hires timestamp = Yes
    debug pid = No
    debug uid = No
    debug class = No
    enable core files = Yes
    smb ports = 445 139
    large readwrite = Yes
    max protocol = NT1
    min protocol = CORE
    min receivefile size = 0
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
    unix extensions = Yes
    use spnego = Yes
    client signing = auto
    server signing = No
    client use spnego = Yes
    client ldap sasl wrapping = plain
    enable asu support = No
    svcctl list = 
    deadtime = 0
    getwd cache = Yes
    keepalive = 300
    lpq cache time = 30
    max smbd processes = 0
    paranoid server security = Yes
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
    load printers = Yes
    printcap cache time = 750
    printcap name = 
    cups server = 
    cups encrypt = No
    cups connection timeout = 30
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
    logon script = 
    logon path = \\%N\%U\profile
    logon drive = 
    logon home = \\%N\%U
    domain logons = No
    init logon delayed hosts = 
    init logon delay = 100
    os level = 20
    lm announce = Auto
    lm interval = 60
    preferred master = No
    local master = Yes
    domain master = Auto
    browse list = Yes
    enhanced browsing = Yes
    dns proxy = No
    wins proxy = No
    wins server = 
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
    preload = 
    lock directory = /var/run/samba
    state directory = /var/lib/samba
    cache directory = /var/cache/samba
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
    nmbd bind explicit broadcast = Yes
    homedir map = auto.home
    afs username map = 
    afs token lifetime = 604800
    log nt token command = 
    time offset = 0
    NIS homedir = No
    registry shares = No
    usershare allow guests = Yes
    usershare max shares = 100
    usershare owner only = Yes
    usershare path = /var/lib/samba/usershares
    usershare prefix allow list = 
    usershare prefix deny list = 
    usershare template share = 
    panic action = /usr/share/samba/panic-action %d
    perfcount module = 
    host msdfs = Yes
    passdb expand explicit = No
    idmap backend = tdb
    idmap alloc backend = 
    idmap cache time = 604800
    idmap negative cache time = 120
    idmap uid = 
    idmap gid = 
    template homedir = /home/%D/%U
    template shell = /bin/false
    winbind separator = \
    winbind cache time = 300
    winbind reconnect delay = 30
    winbind enum users = No
    winbind enum groups = No
    winbind use default domain = No
    winbind trusted domains only = No
    winbind nested groups = Yes
    winbind expand groups = 1
    winbind nss info = template
    winbind refresh tickets = No
    winbind offline logon = No
    winbind normalize names = No
    winbind rpc only = No
    create krb5 conf = Yes
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
    create mask = 0744
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
    smb encrypt = auto
    block size = 1024
    change notify = Yes
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
    cups options = 
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
    store dos attributes = No
    dmapi support = No
    browseable = Yes
    access based share enum = No
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

[homes]
    valid users = %S
    read only = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[public]
    path = /home/public
    read only = No
    guest ok = Yes

```

---

### Post by BertN45 on 2011-04-20
> **Vectorferret said:**
> I
[public]
    path = /home/public
    read only = No
    guest ok = Yes


In my system it looks like:

[Bert]
    comment = Bert's Music and Photos
    path = /media/HP_Data/Bert
    writeable = No
    browseable = yes
    guest ok = yes

for a read only browsable share accessible by everyone.

---

### Post by Morbius1 on 2011-04-20
Good Golly Miss Molly, you don't expect anyone to help you with that thing do you :wink:

If you're going to use something like SWAT you need to run testparm to see what it's done.

I ran the following command against your smb.conf: 
```
testparm -s
```testparm should end with an interpreted version of your smb.conf but for me it ended with this line:
> Error loading services.Services in samba-speak means shares.

Do you get the same error?

---

### Post by Vectorferret on 2011-04-20
No, I get no errors with testparm and the server works perfectly, except for being browseable (even though browsable is enabled). All I can find searching the forums and google for the issue is other threads that never ended with it working.

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[print$]"
Processing section "[printers]"
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        auth methods = guest, sam
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        valid users = %S
        read only = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[public]
        path = /home/public
        read only = No
        guest ok = Yes

```

EDIT - Problem no longer occurs. I have no idea what fixed it as I didn't do anything to smb. (I was configuring other things on the server and somehow made the services visible while doing it.)

---

