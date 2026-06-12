---
title: "Extreme Samba Weirdness"
date: 2009-03-04
forum: Server Platforms
---

### Post by shadowfirebird on 2009-03-04
I've got something *very* strange going on here.  Let me show you what happens when I try to connect to my new samba server:

```
andy@Blake:~$ smbclient //10.0.0.5/filing 
Password: 
Server not using user level security and no password supplied.
Server requested plaintext password but 'client use plaintext auth' is disabled
tree connect failed: SUCCESS - 0
andy@Blake:~$
```

Here's the output of testparm on the server.  You can see that smbclient is lying.

```
andy@cally:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[filing]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = FIREBIRD
        server string = %h server (Samba, Ubuntu)
        passdb backend = smbpasswd:/etc/samba/smbpasswd
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        hosts allow = 10.0.0..

[filing]
        path = /filing
        read only = No
andy@cally:~$
```


In fact I would like a more complex samba configuration than that, but for the past eight hours or so I've been whittling bits off of it in the hope I could make *something* work.  No luck.  (By the way: it doesn't work from Windows, either.)

At this point, I'm prepared to believe in man-in-the-middle attacks, mysterious second smb.conf files, or flying saucers...  

Anyone got any ideas, at all?

---

### Post by koenn on 2009-03-04
try testparm -v for all settings, including defaults not in smb.conf

you might need to set 'security'
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2552069](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2552069)

I don't think it's a flying saucers case; it could be gremlins or cosmic rays, or you're using a version of samba that was written on a Monday.

---

### Post by dannyboy79 on 2009-03-04
I strongly suggest reading the man pages for smb.conf. it helped me get my network up and running flawlessly.

```
man smb.conf
```

here's my smb.conf if you'd like to check it out:
[http://pastebin.com/f5cf9c451](http://pastebin.com/f5cf9c451)

---

### Post by shadowfirebird on 2009-03-04
Thanks for the suggestions, folks.  

I'd not realised that testparm had that -v option, ta.  It does confirm that securiry = user and encrypt passwords = yes.  (I'll put the whole output at the end of this post.)

You're right, it's probably not aliens.  Maybe a white car went past while I was installing Samba or something.


"man" is my favourite command, actually.  If a day goes past with out my running it at least six times, then ... that's a weird day.


By the way -- I've got this problem duplicated on 8.04 and 8.10 now.

Here's the testparm -v output, in case that helps anyone:
```
[global]
        dos charset = CP850
        unix charset = UTF-8
        display charset = LOCALE
        workgroup = FIREBIRD
        realm =
        netbios name = CALLY
        netbios aliases =
        netbios scope =
        server string = %h server (Samba, Ubuntu)
        interfaces =
        bind interfaces only = No
        config backend = file
        security = USER
        auth methods =
        encrypt passwords = Yes
        update encrypted = No
        client schannel = Auto
        server schannel = Auto
        allow trusted domains = Yes
        map to guest = Never
        null passwords = No
        obey pam restrictions = No
        password server = *
        smb passwd file = /etc/samba/smbpasswd
        private dir = /etc/samba
        passdb backend = smbpasswd:/etc/samba/smbpasswd
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
        restrict anonymous = 0
        lanman auth = No
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
        debug prefix timestamp = No
        debug hires timestamp = No
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
        max open files = 10000
        socket options = tcp_nodelay
        use mmap = Yes
        hostname lookups = No
        name cache timeout = 660
        ctdbd socket =
        cluster addresses =
        clustering = No
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
        ldap ssl =
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
        registry shares = No
        usershare allow guests = No
        usershare max shares = 100
        usershare owner only = Yes
        usershare path = /var/lib/samba/usershares
        usershare prefix allow list =
        usershare prefix deny list =
        usershare template share =
        panic action = /usr/share/samba/panic-action %d
        host msdfs = Yes
        passdb expand explicit = No
        idmap domains =
        idmap backend =
        idmap alloc backend =
        idmap cache time = 900
        idmap negative cache time = 120
        idmap uid =
        idmap gid =
        template homedir = /home/%D/%U
        template shell = /bin/false
        winbind separator = \
        winbind cache time = 300
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
        hosts allow = 10.0.0..
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

[filing]
        path = /filing
        read only = No
```

---

### Post by shadowfirebird on 2009-03-05
Update: I replaced my smb.conf with the one dannyboy posted a link to, above, and I got the same error when I tried to connect to it!

(Obviously I had to replace the settings for the directory being shared, and the IP address, but I left everything else as it was.)

I'm really starting to think that my server just isn't seeing the same smb.conf as I am...

---

### Post by koenn on 2009-03-05
did you create samba user accounts ?

---

### Post by shadowfirebird on 2009-03-07
I have indeed set up user accounts using smbpasswd -a. (Since in fact I want to have a PDC setup, I've set up machine accounts too.)


Update: I've since got samba sort of working by running gadmin-samba.  It said it couldn't work with my smb.conf and asked me if it could start over.  Does anyone think there might have been something subtly wrong with the syntax, something that samba picked up but testparm didn't?  Control characters, for instance?


gadmin-samba wasn't really something I found usable before, but it seems to have improved greatly.  (I still don't have a PDC configuration working, but that's another story.)  So in the sense that I would recommend anyone having samba problems to try it, I guess this is a solved problem.  I'll mark it as such once people have had a chance to comment on the control characters idea.  Ta, everyone.

---

### Post by ks01 on 2012-08-16
I have had the same issue setting up my second file server.

The fix was copying the smb.conf from the existing server to the new server and edited it with the new server info.  Rebooted and it worked.  
That fixed the problem.  


I ran a diff on the files and there appears that there are some issues with the default file.  
I have attached the diff output.  working file on the left, original file on the right.

---

### Post by cariboo on 2012-08-16
@ks01, you may not have noticed, but the last reply in this thread was in 2009, thread closed, as things have changed quite a bit since then.

---

