---
title: "Can't login when I upload my smb.conf file..."
date: 2009-02-09
forum: Server Platforms
---

### Post by ayyjayy on 2009-02-09
Hello there,

I have seen this problem posted elsewhere in these forums, but the fix posted doesn't exactly work for me. I have a Dell SC1420 running ubuntu 8.10 server. I have LAMP, OpenSSH, and Samba installed from the menu choices. I have upgraded the system and installed SWAT and Webmin. When I use webmin (or any other way) to put my smb.conf file in place, and I restart the Samba service, I can't login locally to the machine or into SWAT, but I can log in to webmin and put the default smb.conf file back and it all works fine. I have tried the solution that has been posted elswhere using the commands:
```
sudo mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.old
sudo rm /var/lib/samba/secrets.tdb
sudo dpkg --purge libpam-smbpass
```

If I leave it like that it works but when I reinstall libpam-smbpass it stops working. I will put my smb.conf file below for your perusal:

[global]
	dos charset = CP850
        unix charset = UTF-8
        display charset = LOCALE
        workgroup = ABC_FRED
        realm = AURORA.ABC.NB.CA
        netbios name = AURORA
        netbios aliases = 
        netbios scope = 
        server string = %h server (Samba %v)
        interfaces = eth0
        bind interfaces only = No
        security = USER
        auth methods = 
        encrypt passwords = Yes
        update encrypted = No
        client schannel = Auto
        server schannel = Auto
        allow trusted domains = Yes
        hosts equiv = 
        min password length = 5
        map to guest = Never
        null passwords = No
        obey pam restrictions = Yes
        password server = *
        smb password file = /etc/samba/smbpasswd
        private dir = /etc/samba
        passdb backend = tdbsam, guest
        algorithmic rid base = 1000
        root directory = 
        guest account = nobody
        enable privileges = No
        pam password change = No
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
        passwd chat debug = No
        passwd chat timeout = 2
        check password script = 
        username map = /etc/samba/smbusers
        password level = 0
        username level = 0
        unix password sync = No
        restrict anonymous = 0
        lanman auth = Yes
        ntlm auth = Yes
        client NTLMv2 auth = No
        client lanman auth = Yes
        client plaintext auth = Yes
        preload modules =
        use kerberos keytab = No
        log level = 0
        syslog = 0
        syslog only = No
        log file = /var/log/samba/log.%m
        max log size = 1000
        debug timestamp = Yes
        debug hires timestamp = No
        debug pid = No
        debug uid = No
        smb ports = 445 139
        large readwrite = Yes
        max protocol = NT1
        min protocol = CORE
        read bmpx = No
        read raw = Yes
        write raw = Yes
        disable netbios = No
        acl compatibility = 
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
        change notify timeout = 60
        deadtime = 0
        getwd cache = Yes
        keepalive = 300
        kernel change notify = Yes
        lpq cache time = 30
        max smbd processes = 0
        paranoid server security = Yes
        max disk size = 0
        max open files = 10000
        socket options = TCP_NODELAY
        use nmap = Yes
        hostname lookups = No
        name cache timeout = 660
        load printers = No
        printcap cache time = 0
        printcap name =
        cups server = 
        disable spoolss = No
        enumports command = 
        addprinter command = 
        deleteprinter command = 
        show add printer wizard = Yes
        os2 driver map = 
        mangling method = hash2
        mangle prefix = 1
        stat cache = Yes
        machine password timeout = 604800
        add user script = /usr/sbin/useradd -m '%u'
        delete user script = /usr/sbin/userdel -r '%u'
        add group script = /usr/sbin/groupadd '%g'
        delete group script = /usr/sbin/groupdel '%g'
        add user to group script = /usr/sbin/usermod -G '%g' '%u'
        delete user from group script =
        set primary group script =
        add machine script = /usr/sbin/useradd -g machines -s /bin/false -d /var/lib/nobody '%u'
        shutdown script = /var/lib/samba/scripts/shutdown.sh
        abort shutdown script = /sbin/shutdown -c
        logon script = scripts\%G.bat
        logon path = \\%L\profiles\%U
        logon drive = U:
        logon home = \\%N\%U
        domain logons = Yes
        os level = 20
        lm announce = Auto
        lm interval = 60
        preferred master = Auto
        local master = Yes
        domain master = Auto
        browse list = Yes
        enhanced browsing = Yes
        dns proxy = No
        wins proxy = No
        wins server =
        wins support = No
        wins hook =
        wins partners =
        kernel oplocks = Yes
        lock spin count = 3
        lock spin time = 10
        oplock break wait time = 0
        ldap admin dn =
        ldap delete dn = No
        ldap filter = (uid=%u)
        ldap group suffix =
        ldap idmap suffix =
        ldap machine suffix =
        ldap password sync = No
        ldap replication sleep = No
        ldap suffix =
        ldap ssl = No
        ldap timeout = 15
        ldap user suffix = 
        add share command =
        delete share command =
        config file =
        preload =
        lock directory =
        pid directory = /var/run/samba
        utmp directory =
        wtmp directory =
        utmp = No
        default service =
        message command =
        dfree command = 
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
        panic action = /usr/share/samba/panic-action %d
        host msdfs = No
        enable rid algorithm = Yes
        idmap backend = 
        idmap uid =
        idmap gid =
        template primary group = nobody
        template homedir = /home/%D/%U
        template shell = /bin/false
        winbind separator = \
        winbind cache time = 300
        winbind enable local accounts = No
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = No
        winbind trusted domains only = No
        winbind nested groups = No
        comment = 
        path = 
        username = 
        invalid users =
        valid users =
        admin users = root
        read list = 
        write list = 
        printer admin =
        force user = 
        force group = 
        read only = Yes
        create mask = 0744
        force create mask = 00
        security mask = 0777
        force security mode = 00
        directory mask = 0755
        force directory mode = 00
        force unknown acl user = No
        inherit permissions = No
        inherit acls = No
        guest only = No
        guest ok = No
        only user = No
        hosts allow =
        hosts deny =
        allocation roundup size = 1048576
        ea support = No
        nt acl support = Yes
        profile acls = No
        map acl inherit = No
        afs share = No
        block size = 1024
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
        default devmode = No
        force printername = No
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
        map system = No
        map hidden = No
        map archive = Yes
        mangled names = Yes
        mangled map =
        store dos attributes = No
        browseable = Yes
        blocking locks = Yes
        csc policy = manual
        fake oplocks = No
        locking = Yes
        oplocks = Yes
        level2 oplocks = Yes
        oplock contention limit = 2
        posix locking = Yes
        strict locking = Yes
        share modes = Yes
        copy = 
        include =
        preexec = 
        preexec close = No
        postexec =
        root preexed = 
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

[homes]
	comment = Home Directories
	read only = No
	create mask = 0700
	directory mask = 0700
	browseable = No

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon/
        admin users =
	guest ok = Yes
	share modes = No

[profiles]
	comment = Profile Share
	path = /home/profiles
        admin users =
	read only = No
	force security mode = 0700
	force directory security mode = 0700
	profile acls = Yes

[teachers$]
	comment = Teachers Shared Folder
	path = /home/teachers
	read only = No
	create mask = 0770
	directory mask = 0770

[shared]
	comment = Students Common Shared Folder
	path = /home/shared
	write list = [hidden]
	read only = No
	create mask = 0774
	directory mask = 0775

[homelinks$]
	comment = Links to Home Folders
	path = /home/homelinks
	valid users = [hidden]
        admin users =
	force user = root
	read only = No

[admin-share$]
	path = /home/admin-share
	valid users = [hidden]
	admin users = [hidden]
	write list = [hidden]
	read only = No
	force create mode = 0770
	force directory mode = 0770
	
[netadmin-share$]
	path = /home/netadmin-share
	valid users = [hidden]
        admin users =
	read only = No

[images]
	comment = Stored directory for OS image files
	path = /home/shared/images

[btprofiles$]
	path = /home/profiles
	valid users = [hidden]
	admin users = [hidden]
	read list = [hidden]
	write list = [hidden]
	force user = root
	force group = root
	read only = No
	hosts allow = 192.168.0.

[copier$]
	comment = copier shared
	path = /var/copier
	read only = No
	guest ok = Yes

I have hidden the user names to protect the innocent. I am using the basic setup that was here when I started here, it was on a debian 3.1 machine that got hosed 2 weeks ago.

Any help on this would be greatly appreciated.

---

### Post by capscrew on 2009-02-10
> **ayyjayy said:**
> Hello there,

... When I use webmin (or any other way) to put my smb.conf file in place, and I restart the Samba service, I can't login locally to the machine or into SWAT, but I can log in to webmin


I'm going to say that the libpam-smbpass enables the webmin features.  I have 2 Samba servers and neither use libpam-smbpass.
> 

 and put the default smb.conf file back and it all works fine. I have tried the solution that has been posted elswhere using the commands:
```
sudo mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.old
sudo rm /var/lib/samba/secrets.tdb
sudo dpkg --purge libpam-smbpass
```

If I leave it like that it works but when I reinstall libpam-smbpass it stops working.

Further proof that your symptoms are webmin induced via libpam-smbpass.  I see that the libpam-smbpass PAM module allows extended *name=value* pairs.  I don't know which in your smb.conf are Samba defaults and which are Webmin settings.

Cutting to the chase you can learn how to config and maintain Samba own its own from the command line or learn webmin.  I have seen very little on the inner workings of webmin and consider it a newbie helper program (middle ware if you will).  

My vote would be for you to learn Samba without using webmin.

If you are interested in libpam-smbpass, the info should be  located at:```
 /usr/share/doc/libpam-smbpass/
```

If you need an unmolested copy of the smb.conf file there should be a copy located at:```
/usr/share/samba/smb.conf
```

---

### Post by ayyjayy on 2009-02-10
I figured that is the way I would have to go. While webmin is fine for some things, sometimes you actually have to get down and dirty with the configuration. I am switching from Samba2 to Samba3 and didn't think that there would be that much of a difference. I have a few Samba and Ubuntu books on order, and have found a few scattered resources online as well. Thanks for the suggestions.

Adam

---

