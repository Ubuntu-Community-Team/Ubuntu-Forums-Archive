---
title: "Samba login trouble"
date: 2013-03-06
forum: Server Platforms
---

### Post by Johnyboy33 on 2013-03-06
Hey all,
   I've been chasing my issues with samba around all damn day left and right back and front. 

My shares will not mount or produce a password prompt for my windows boxes (Xp and 7) that I'm working to get setup.

Some quick background info:

All of the users have been created on the Ubuntu server as well as created and added to the smbusers file

SMB config dump

```

root@keystone:/etc/samba# testparm -v smb.conf
Load smb config files from smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[wall]"
Processing section "[john]"
Processing section "[tom]"
Processing section "[sam]"
Processing section "[trev]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        dos charset = CP850
        unix charset = UTF-8
        display charset = LOCALE
        workgroup = WORKGROUP
        realm =
        netbios name = KEYSTONE
        netbios aliases =
        netbios scope =
        server string = %h
        interfaces =
        bind interfaces only = No
        security = USER
        auth methods =
        encrypt passwords = No
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
        username map = /etc/samba/smbusers
        password level = 0
        username level = 0
        unix password sync = Yes
        restrict anonymous = 0
        lanman auth = No
        ntlm auth = Yes
        client NTLMv2 auth = Yes
        client lanman auth = No
        client plaintext auth = No
        client use spnego principal = No
        send spnego principal = No
        preload modules =
        dedicated keytab file =
        kerberos method = default
        map untrusted to domain = Yes
        log level = 2
        syslog = 0
        syslog only = No
        log file = /var/log/samba/log.%m
        max log size = 10000
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
        log writeable files on exit = No
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
        ctdb locktime warn threshold = 0
        smb2 max read = 65536
        smb2 max write = 65536
        smb2 max trans = 65536
        smb2 max credits = 8192
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
        username map cache time = 0
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
        allow insecure wide links = No
        async smb echo handler = No
        multicast dns register = Yes
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
        winbind max clients = 200
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
        ncalrpc dir = /var/ncalrpc
        winbind max domain connections = 1
        idmap config * : backend = tdb
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
        print notify backchannel = Yes
        print ok = No
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

[wall]
        comment = wall Home files
        path = /home/wallshare
        valid users = +wallshare
        admin users = john
        read only = No
        create mask = 0775
        directory mask = 0775
        inherit owner = Yes

[john]
        comment = homeshare
        path = /home/john
        valid users = john
        admin users = john
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes

[tom]
        comment = homeshare
        path = /home/tom
        valid users = john, tom
        admin users = john, tom
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes

[sam]
        comment = homeshare
        path = /home/sam
        valid users = john, sam
        admin users = john, sam
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes

[trev]
        comment = homeshare
        path = /home/trev
        valid users = john, trev
        admin users = john, trev
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes

```

Users added to the passdb.tdb correctly

```
key(12) = "USER_sam\00"
key(10) = "USER_john\00"
key(10) = "USER_trev\00"
key(12) = "USER_tom\00"
```

error message with the smbclient test

```
root@keystone:/var/lib/samba# smbclient -L keystone -Ujohn
Enter john's password:
Server requested LM password but 'client plaintext auth = no' or 'client ntlmv2 auth = yes'
session setup failed: SUCCESS - 0
```

Any tips/suggestions?

---

### Post by Johnyboy33 on 2013-03-07
Update:

I've been plodding along trying to get it to work and here is where I'm at:

My windows 7 box connects and authenticates when I use the IP address not the host name and HOSTNAMESAMBA\unixusername

Afterwords my windows 7 box will authenticate with the hostname and show all of the shares.

My windows xp box does not authenticate nor find the samba share via hostname or servername but does find it when I type in \\hostname\share However it does not authenticate for anything when I use the usernames and passwords for my 4 users.




```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[wall]"
Processing section "[john]"
Processing section "[tom]"
Processing section "[sam]"
Processing section "[trev]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        server string = %h
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        map untrusted to domain = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 10000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[wall]
        comment = wall Home files
        path = /home/wallshare
        valid users = +wallshare
        admin users = john
        read only = No
        create mask = 0775
        directory mask = 0775
        inherit owner = Yes
        guest ok = Yes

[john]
        comment = homeshare
        path = /home/john
        valid users = john
        admin users = john
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes

[tom]
        comment = homeshare
        path = /home/tom
        valid users = john, tom
        admin users = john, tom
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes

[sam]
        comment = homeshare
        path = /home/sam
        valid users = john, sam
        admin users = john, sam
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes

[trev]
        comment = homeshare
        path = /home/trev
        valid users = john, trev
        admin users = john, trev
        read only = No
        create mask = 0600
        directory mask = 0600
        inherit owner = Yes


```


Any help; I'm really ripping my hair out here.

---

