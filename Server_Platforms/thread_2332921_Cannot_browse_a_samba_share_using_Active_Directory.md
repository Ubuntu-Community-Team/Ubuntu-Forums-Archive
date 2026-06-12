---
title: "Cannot browse a samba share using Active Directory user account"
date: 2016-08-05
forum: Server Platforms
---

### Post by Sean_Montgomery on 2016-08-05
I've been struggling for some time now trying to browse a samba share using my Windows Active Directory Domain user account. The scenario is:

Windows 2012 Active Directory Domain Controller
Domain is currently only running at Windows Server 2003 functional level
Fresh install of Ubuntu 16.04 LTS
Fresh install of Samba - Version 4.3.9-Ubuntu "apt-get install ntp krb5-user samba cifs-utils smbclient winbind"

I've successfully joined the Ubuntu server to my AD domain and and can successfully see the Ubuntu server in the computers OU in AD, it also has a DNS record in the domain. wbinfo -u also successfully shows all of my active directory users and wbinfo -g also shows the AD groups. When i try to browse either the samba share from my windows machine it prompts with "access is denied". This is the first time i've tried to setup samba joined to a domain and passthru authentication can anybody help?

```
krb5.conf is as follows:
[libdefaults]
  ticket_lifetime = 24h
  default_realm = TESTDOMAIN.CO.UK
  forwardable = true


[realms]
        TESTDOMAIN.CO.UK = {
                kdc = TESTDC
                admin_server = TESTDC
        }

[domain_realm]
  .testdomain.co.uk = TESTDOMAIN.CO.UK
  testdomain.co.uk = TESTDOMAIN.CO.UK

[kdc]
  profile = /etc/krb5kdc/kdc.conf

[appdefaults]
  pam = {
    debug = false
    ticket_lifetime = 36000
    renew_lifetime = 36000
    forwardable = true
    krb4_convert = false
  }

[logging]
  kdc = FILE:/var/log/krb5kdc.log
  admin_server = FILE:/var/log/kadmin.log
  default = FILE:/var/log/krb5lib.log

---------------------------------------

/etc/nsswitch.conf is as follows


passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind
gshadow:        files

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

-----------------------------
smb.conf is as follows


[global]
    # No .tld
    workgroup = TESTDOMAIN.CO.UK
    # Active Directory System
    security = ads
    # With .tld
    realm = TESTDOMAIN.CO.UK
    # Just a member server
    domain master = no
    local master = no
    preferred master = no
    # Disable printing error log messages when CUPS is not installed.
    printcap name = /etc/printcap
    load printers = no
    # Works both in samba 3.2 and 3.6.        
    idmap backend = tdb
    idmap uid = 10000-99999
    idmap gid = 10000-99999
    # no .tld
    idmap config TESTDOMAIN:backend = rid
    idmap config TESTDOMAIN:range = 10000-9999
    winbind enum users = yes
    winbind enum groups = yes
    # This way users log in with username instead of [email]username@testdomain.co.uk[/email]
    winbind use default domain = yes
    # Inherit groups in groups
    winbind nested groups = yes
    winbind refresh tickets = yes
    winbind offline logon = true
    # Becomes /home/example/username
    template homedir = /home/%D/%U
    # No shell access
    template shell = /bin/false
    client use spnego = yes
    client ntlmv2 auth = yes
    encrypt passwords = yes
    restrict anonymous = 2
    log file = /var/log/samba/samba.log
    log level = 2

[Windows]
    comment = Windows Share
    path = /usr/windows
    valid users = "@TESTDOMAIN.CO.UK\Domain Users"
    force group = "domain users"
    writable = yes
    read only = no
    force create mode = 0660
    create mask = 0777
    directory mask = 0777
    force directory mode = 0770
    access based share enum = yes
    hide unreadable = yes

```

Please help i'm all out of ideas and i really need this to works :( 

Thank you

---

### Post by wildmanne39 on 2016-08-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

*Thread moved to **Server Platforms**.*

---

### Post by volkswagner on 2016-08-05
"Access denied" seems to me it's authenticating but the user does not have permission to access the share.

Can you post output of the following:

```
ls -al usr/windows
```

```
getfacl usr/windows
```

```
wbinfo -i <real domain username here>
```

```
wbinfo -i "domain users"
```

```
wbinfo -i "domain admins"
```

Have you tried accessing the share with domain\administrator account?

I believe you should change position of your first quation:

```
valid users = "@TESTDOMAIN.CO.UK\Domain Users"
```

should be: (you don't want the @ inside quotes)
```
valid users = @"TESTDOMAIN.CO.UK\Domain Users"
```

---

### Post by Sean_Montgomery on 2016-08-07
First off thanks for coming back with a response, I've changed the smb.conf to be @"Domain Users" - sadly didn't solve my problem

```
root@mt0001lx:/# ls -al usr/windowstotal 8
drwxrwxrwx  2 root root 4096 Aug  4 13:35 .
drwxr-xr-x 11 root root 4096 Aug  4 13:35 ..



```


```
root@mt0001lx:/# getfacl usr/windows# file: usr/windows
# owner: root
# group: root
user::rwx
group::rwx
other::rwx



```


```
root@mt0001lx:/# wbinfo -i seanmseanm:*:10000:10004:Sean Montgomery (Hardware Dept):/home/TESTDOMAIN.CO.UK/seanm:/bin/false



```


```
root@mt0001lx:/# wbinfo -i "domain users"failed to call wbcGetpwnam: WBC_ERR_DOMAIN_NOT_FOUND
Could not get info for user domain users



```


```
root@mt0001lx:/# wbinfo -i "domain admins"failed to call wbcGetpwnam: WBC_ERR_DOMAIN_NOT_FOUND
Could not get info for user domain admins



```


I did try using the domain administrator account and this had the same response, access denied. From the commands you asked me to check it seems like possibly a group resolution problem?

I appreciate the help

Thank you

---

### Post by volkswagner on 2016-08-07
A couple more tests:

What happens when you try to chown a directory to a domain user account?
```
sudo mkdir /usr/windows/test
sudo chown seanm /usr/windows/test
```

Can you authenticate with smbclient?
```
smbclient -L TESTDOMAIN.CO.UK -U 'administrator'
smbclient //localhost/netlogon -U seanm
```

If all the above goes well, try creating a simple test share
```

[Test]
       path = /usr/windows/test
       read only = no
```

reload samba
```
smbcontrol all reload-config
```

Can seanm access the new share? How about if you add your user to the original share inside valid user list, like:
```
valid users = TESTDOMAIN.CO.UK\seanm, @"TESTDOMAIN.CO.UK\Domain Users"
```

---

### Post by Sean_Montgomery on 2016-08-08
Ok i've had a go

```
mtadminmt0001lx@mt0001lx:~$ sudo mkdir /usr/windows/test[sudo] password for mtadminmt0001lx:
mtadminmt0001lx@mt0001lx:~$ sudo chown seanm /usr/windows/test
chown: invalid user: ‘seanm’



```

```
mtadminmt0001lx@mt0001lx:~$ smbclient -L TESTDOMAIN.CO.UK -U 'administrator'WARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Enter administrator's password:
Domain=[TESTDOMAIN.CO.UK] OS=[Windows Server 2003 R2 3790 Service Pack 2] Server=[Windows Server 2003 R2 5.2]


        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        EPSON-WP        Printer   EPSON WP-4095
        labels          Printer   Label Printer
        ACULASER        Printer   Sales
        C$              Disk      Default share
        SALES5350       Printer   Sales Office Brother HL-5350
        PRNOFFICE2      Printer   Main Office MFC/Fax Inside the door
        Brother7050     Printer   Brother HL-7050
        PDrivers        Disk
        Software Dept Laser Printer   Back of Main Office 1270N
        CertEnroll      Disk      Certificate Services share
        IPC$            IPC       Remote IPC
        Main Office Laser Printer   Main Office 7050 Upstairs
        ADMIN$          Disk      Remote Admin
        PRN-MFC8880-ACC Printer   Brother MFC8880
        prnproc$        Disk
        QA dept Laser Printer Printer   QA Desk
        Hardware Dept MFC Printer   Hardware Deptment MFC Laser
        SYSVOL          Disk      Logon server share
        NETLOGON        Disk      Logon server share
        downloads       Disk


Connection to TESTDOMAIN.CO.UK failed (Error NT_STATUS_IO_TIMEOUT)
NetBIOS over TCP disabled -- no workgroup available






```

```
mtadminmt0001lx@mt0001lx:~$ smbclient //localhost/netlogon -U seanmWARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Enter seanm's password:
session setup failed: NT_STATUS_LOGON_FAILURE



```

Not sure what NT_STATUS_LOGON_FAILURE means?

I've added the basic test share


```
mtadminmt0001lx@mt0001lx:~$ smbcontrol all reload-configcould not init messaging context
mtadminmt0001lx@mt0001lx:~$ /etc/init.d/smbd restart
[....] Restarting smbd (via systemctl): smbd.service==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to restart 'smbd.service'.
Authenticating as: TESTDOMAIN Administrator,,, (mtadminmt0001lx)
Password:
==== AUTHENTICATION COMPLETE ===
. ok



```

I've tried browsing the test share and also get access denied.

I've also added the domain user aswell

```
[Windows]    comment = Windows Share
    path = /usr/windows
    valid users = TESTDOMAIN.CO.UK\seanm, @"TESTDOMAIN.CO.UK\Domain Users"
    force group = "domain users"
    writable = yes
    read only = no
    force create mode = 0660
    create mask = 0777
    directory mask = 0777
    force directory mode = 0770
    access based share enum = yes
    hide unreadable = yes



```

Still getting the same error message "Windows cannot access \\mt0001lx\windows", "You do not have permission to access \\mt0001lx\windows. Contact you network administrator to request access"

When you try and browse just the server \\mt0001lx, you get prompted to enter username and password, Access is denied.

---

### Post by darkod on 2016-08-08
Do you have the winbind package installed? I have seen lately some strange samba 4.3 behavior when you don't have winbind. I think there is a related bug and also related to that LOGON_FAILURE message.

No need to do any config, just install winbind and see if the LOGON message goes away.

You seem to have few different issues, so it will not solve them all, but you should get to a stage where there is no logon failure.

PS. I just saw in your first post that you do have winbind. So, it is not related to that.

The logon failure seems to say samba is not contacting the AD correctly. No? If it can't even authenticate the user properly you need to sort that first.

---

### Post by volkswagner on 2016-08-08
Your smb.conf needs to change workgroup, and possibly add the server's net bios name:

```
workgroup = TESTDOMAIN
netbios name = mt0001lx
```

Reload SAMBA, and retry smbclient commands.

If that doesn't work please post output of:
```
testparm -v
```

---

### Post by Sean_Montgomery on 2016-08-08
Interesting... so i've adjusted the smb.conf to have the netbios name of the server and changed WORKGROUP to be TESTDOMAIN rather than .co.uk, and the share are behaving differently...not correctly just differently. 

Now when i try to browse the server name \\mt0001lx, rather than access denied i get prompted with "The username or password is incorrect" and asked for the username and password again - I've tried both my username and the domain admin but neither work.

When you browse \\mt0001lx\windows it prompts for username and password, it doesn't say anything is incorrect it just prompts, if you enter my username seanm, it says "the specified network password is not correct" - and the same if you use the domain admin account. 

winbind is definitely installed 

I've tried the group commands again and get the same response.

```
mtadminmt0001lx@mt0001lx:~$ wbinfo -i "domain users"failed to call wbcGetpwnam: WBC_ERR_WINBIND_NOT_AVAILABLE
Could not get info for user domain users
mtadminmt0001lx@mt0001lx:~$ wbinfo -i "domain admins"
failed to call wbcGetpwnam: WBC_ERR_WINBIND_NOT_AVAILABLE
Could not get info for user domain admins
mtadminmt0001lx@mt0001lx:~$



```

testparm -v  shows the following

```
mtadminmt0001lx@mt0001lx:~$ testparm -vLoad smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Processing section "[Windows]"
Processing section "[TEST]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER


Press enter to see a dump of your service definitions


# Global parameters
[global]
        dos charset = CP850
        unix charset = UTF-8
        workgroup = TESTDOMAIN
        realm = TESTDOMAIN.CO.UK
        netbios name = MT0001LX
        netbios aliases =
        netbios scope =
        server string = Samba 4.3.9-Ubuntu
        interfaces =
        bind interfaces only = No
        config backend = file
        server role = auto
        security = ADS
        auth methods =
        encrypt passwords = Yes
        client schannel = Auto
        server schannel = Auto
        allow trusted domains = Yes
        map to guest = Never
        null passwords = No
        old password allowed period = 60
        obey pam restrictions = No
        password server = *
        smb passwd file = /etc/samba/smbpasswd
        private dir = /var/lib/samba/private
        passdb backend = tdbsam
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
        username level = 0
        unix password sync = No
        restrict anonymous = 2
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
        log file = /var/log/samba/samba.log
        logging =
        max log size = 5000
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
        name resolve order = lmhosts wins host bcast
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
        printcap cache time = 750
        printcap name = /etc/printcap
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
        local master = No
        domain master = No
        browse list = Yes
        enhanced browsing = Yes
        dns proxy = Yes
        wins proxy = No
        wins server =
        wins support = No
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
        panic action =
        perfcount module =
        host msdfs = Yes
        passdb expand explicit = No
        idmap backend = tdb
        idmap cache time = 604800
        idmap negative cache time = 120
        idmap uid = 10000-99999
        idmap gid = 10000-99999
        template homedir = /home/%D/%U
        template shell = /bin/false
        winbind separator = \
        winbind cache time = 300
        winbind reconnect delay = 30
        winbind request timeout = 60
        winbind max clients = 200
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        winbind trusted domains only = No
        winbind nested groups = Yes
        winbind expand groups = 0
        winbind nss info = template
        winbind refresh tickets = Yes
        winbind offline logon = Yes
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
        idmap config testdomain:range = 10000-19999999
        idmap config testdomain:backend = rid
        idmap config * : range = 10000-99999
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




[Windows]
        comment = Windows Share
        path = /usr/windows
        valid users = TESTDOMAIN.CO.UK\seanm "@TESTDOMAIN.CO.UK\Domain Users"
        force group = "domain users"
        group = "domain users"
        read only = No
        create mask = 0777
        force create mode = 0660
        directory mask = 0777
        directory mode = 0777
        force directory mode = 0770
        hide unreadable = Yes
        access based share enum = Yes




[TEST]
        path = /usr/windows/test
        read only = No
mtadminmt0001lx@mt0001lx:~$



```

---

### Post by volkswagner on 2016-08-08
What happens when you run the smblient commands? Are you prefixing username with domain (testdomain\seanm)?

---

### Post by Sean_Montgomery on 2016-08-08
Please see:
```
smbclient -L TESTDOMAIN.CO.UK -U 'administrator'

mtadminmt0001lx@mt0001lx:~$ smbclient //localhost/netlogon -U seanm
WARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Enter seanm's password:
session setup failed: NT_STATUS_NO_LOGON_SERVERS
mtadminmt0001lx@mt0001lx:~$ smbclient //localhost/netlogon -U TESTDOMAIN.CO.UK\seanm
WARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Enter TESTDOMAIN.CO.UKseanm's password:
session setup failed: NT_STATUS_NO_LOGON_SERVERS



```


and

```
mtadminmt0001lx@mt0001lx:~$ smbclient -L TESTDOMAIN.CO.UK -U 'administrator'WARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Enter administrator's password:
Domain=[TESTDOMAIN.CO.UK] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]


        Sharename       Type      Comment
        ---------       ----      -------
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        ADMIN$          Disk      Remote Admin
        SYSVOL          Disk      Logon server share
        NETLOGON        Disk      Logon server share
Domain=[TESTDOMAIN.CO.UK] OS=[Windows Server 2003 R2 3790 Service Pack 2] Server=[Windows Server 2003 R2 5.2]


        Server               Comment
        ---------            -------
 
        HWLAPTOP             HWLAPTOP
        MINIDUMP-1
        MINIDUMP-2
        TESTDC               Core DC / DNS / DHCP /  File server
        TEST-DC2
        SWDEVA
        SWDErDS              Work PC
 


        Workgroup            Master
        ---------            -------
        TESTDOMAIN            TEST2
        TESTDOMAIN.CO.UK      testMTNEW

```

I've tried prefixing the domain when browsing and not pre-fixing, either way it cannot browse?

Still confused

---

### Post by Sean_Montgomery on 2016-08-08
I know it's already specified in the krb5.conf but do you need to specify the logonserver in the smb.conf anyhow?

---

### Post by volkswagner on 2016-08-08
> **Sean_Montgomery said:**
> I know it's already specified in the krb5.conf but do you need to specify the logonserver in the smb.conf anyhow?

Actually samba will complain if you use security = ads and specify the password server.

Let's talk about your /etc/krb5.conf.

You have TESTDC as kdc and admin_server, is TESTDC the name of your active directory domain controller?

You are using an internet routable domain. Does it resolve to a LAN ip?

for /etc/krb5.conf you can try changing:

```
[realms]
        TESTDOMAIN.CO.UK = {
                kdc = TESTDC
                admin_server = TESTDC
        }
```

to

```
[realms]
        TESTDOMAIN.CO.UK = {
                kdc = ip_address_of_AD_DC
                admin_server = TESTDC.TESTDOMAIN.CO.UK
                kpasswd_server = ip_address_of_AD_DC
        }


TESTDOMAIN = {
                kdc = ip_address_of_AD_DC
                admin_server = TESTDC.TESTDOMAIN.CO.UK
                default_domain = TESTDOMAIN.CO.UK
        }



```

Does /etc/resolv.conf show your AD DC as DNS server? Does nslookup work for both testdc and testdc.testdomain.co.uk?

Reading latest errors, it seems SAMBA can't find your AD DC.

---

### Post by Sean_Montgomery on 2016-08-10
Its working!!! I had some missing packages and its working!!! 

```
apt-get install libnss-winbind libpam-winbind
```

I started to think that there must a reason why getent group didn't work, had a stab around on the internet and added the packages, worked straight away after a reboot!

Thank you all for your help!!! Especially Volkswagner[URL="https://ubuntuforums.org/member.php?u=288711"]
[/URL]

---

