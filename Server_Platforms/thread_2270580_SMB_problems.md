---
title: "SMB problems"
date: 2015-03-24
forum: Server Platforms
---

### Post by simon89 on 2015-03-24
I just got samba up and running on a fresh install of ubuntu and tried sharing a few folders for access on windows 8 machines on the network

I have 3 problems:

1. Although I can access the SMB share using \\192.168.1.50\Share, the machine/share does not show up in the windows 8 network locations list and the only way to access it is directly with the ip. How do I get the machine to show up in the network list on windows?

2. Once I get to the share (via ip), it does not prompt me for a password despite not having any saved credentials on the windows machine. I thought that by having valid users in the smb.conf it should force a login on the windows side to authenticate me as a user but apparently not. Is there something else I need to do in order to have users log in to be able to access shares? Some shares will eventually be restricted to certain users so this is essential to me

3. I ran testparm and it didn't complain about any problems with the conf file, but I noticed that the output it spits out is not the same as what I have in the conf file (its missing a few things). Is this related to the 2 problems above? Or is this normal?

Here is the contents of my smb.conf file:
```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
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


#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup


netbios name = NAS


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


	name resolve order = bcast host lmhosts wins


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


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
	server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam


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


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
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


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
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
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
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
;	guest ok = no
;	read only = yes
	create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


[Shared]
	path = /mnt/home/Shared
	writeable = yes
	browseable = yes
	valid users = sara, simon


[Simon]
path = /mnt/home/Simon
available = yes
valid users = simon
read only = no
browseable = yes
public = yes
writable = yes

```

and here is the output from testparm:
```

[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast, host, lmhosts, wins
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[Shared]
	path = /mnt/home/Shared
	valid users = sara, simon
	read only = No


[Simon]
	path = /mnt/home/Simon
	valid users = simon
	read only = No
	guest ok = Yes

```

any help is appreciated

---

### Post by volkswagner on 2015-03-24
Do other machines show in your Windows network locations? Perhaps you don't have network discovery on, or
your network is not listed as private?

If your windows username and password match that of your samba user, you will not be
prompted for a password. Is this true of your user login?

The command testparm does not output the netbios name. You can use verbose mode to see all settings, including the
defaults.

```
testparm -v
```

---

### Post by simon89 on 2015-03-24
> **volkswagner said:**
> Do other machines show in your Windows network locations? Perhaps you don't have network discovery on, or
your network is not listed as private?

If your windows username and password match that of your samba user, you will not be
prompted for a password. Is this true of your user login?

The command testparm does not output the netbios name. You can use verbose mode to see all settings, including the
defaults.

```
testparm -v
```

1. none of the windows machines on the network show the ubuntu machine in network locations, but they can all see each other which would imply that discovery is on. The only one that cannot be seen is the ubuntu, so I feel like theres a config issue on this side

2. the windows username thing seemed to be the issue. Its asking for login now. However, I keep getting "access denied" when trying to log in with my account from multiple machines, or logging in with another smb user while one is already connected - is there a way around this?

3. testparm -v still doesnt show everything. For example in smb.conf I have "browseable = yes", but testparm -v does not list that option in the output (same thing for a number of other options)

---

### Post by volkswagner on 2015-03-26
I'm not sure why it's not showing in network. Are the windows clients on workgroup = workgroup?
Also I'm not sure if it matters, but I always have netbios name match actual hostname.
I see one difference on your config, here is what I have:

```
name resolve order = lmhosts, wins, host, bcast
```

edit: How is the server getting ip address? DHCP or static? If it's static please post /etc/network/interfaces

Make sure you can log into samba locally using smbclient, or at least see the shares, verify password.
Login locally or via ssh to NAS.
List shares:
```
smbclient -L localhost -U <smbusername>
```
Connect to share, you can find help with smbclient [here]("http://www.tldp.org/HOWTO/SMB-HOWTO-8.html").
```
smbclient \\\\localhost\\share -U <smbusername>
```


It seems testparm does not display configs on shares if they're equal to defaults like "browseable = yes", but all
the global configs should show regardless if they are set to default.

---

### Post by simon89 on 2015-03-27
yep workgroup is correct, I can browse through the network and smb shares on ubuntu too

I have everything set on a static ip by editing /etc/network/interfaces and I just changed "iface eth0 inet static" and added:
address 192.168.1.50
gateway 192.168.1.1
netmask 255.255.255.0
dns-nameservers 192.168.1.1 8.8.8.8

Everything else was unchanged

---

### Post by volkswagner on 2015-03-27
I'm sorry, but I'm still not sure if password authentication is working.

You should add network and broadcast info to you network config then reboot.

```
        network 192.168.7.0
        broadcast 192.168.7.255
```

---

### Post by simon89 on 2015-03-28
pw auth works. I added the user to the smb password file. Visited \\192.168.1.50 and it asked for a user/password, entered the info and it let me in without a problem

I added network and broadcast to /etc/network/interfaces:

network 192.168.1.0
broadcast 192.168.1.255

But the share/computer is still not visible in windows network locations and can't browse through it without directly visiting the local ip

---

### Post by volkswagner on 2015-03-29
Can you post the output of:

```
testparm -v
```

Also from windows pc:

```
net view
```

and from Linux PC:
```
smbclient -L nas -U workgroup\\simon
```

---

### Post by SeijiSensei on 2015-03-29
Try explicitly defining the computer's "Netbios name" and "workgroup" in smb.conf:
```

[global]
     netbios name = gumby
     workgroup = MYNET

```
The name cannot exceed fifteen characters and should not include special characters.  The workgroup name should match that used by the Windows clients.

---

### Post by simon89 on 2015-03-29
ok so I spun up a new server to continue testing this

I set a static ip with:
```
auto loiface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8
network 192.168.1.0
broadcast 192.168.1.255
```

I added a netbios name, and set up the smbpasswd and samba shares. This is the output of testparm -v:
```
[global]    dos charset = CP850
    unix charset = UTF-8
    workgroup = WORKGROUP
    realm = 
    netbios name = NASTEST
    netbios aliases = 
    netbios scope = 
    server string = %h server (Samba, Ubuntu)
    interfaces = 
    bind interfaces only = No
    server role = standalone server
    security = USER
    auth methods = 
    encrypt passwords = Yes
    client schannel = Auto
    server schannel = Auto
    allow trusted domains = Yes
    map to guest = Bad User
    null passwords = No
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
    unix password sync = Yes
    restrict anonymous = 0
    lanman auth = No
    ntlm auth = Yes
    client NTLMv2 auth = Yes
    client lanman auth = No
    client plaintext auth = No
    client use spnego principal = No
    preload modules = 
    dedicated keytab file = 
    kerberos method = default
    map untrusted to domain = No
    log level = 2
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
    smb ports = 445, 139
    large readwrite = Yes
    server max protocol = SMB3
    server min protocol = LANMAN1
    client max protocol = NT1
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
    max mux = 50
    max xmit = 16644
    name resolve order = lmhosts, wins, host, bcast
    max ttl = 259200
    max wins ttl = 518400
    min wins ttl = 21600
    time server = No
    unix extensions = Yes
    use spnego = Yes
    client signing = default
    server signing = default
    client use spnego = Yes
    client ldap sasl wrapping = plain
    enable asu support = No
    svcctl list = 
    cldap port = 0
    dgram port = 0
    nbt port = 0
    krb5 port = 0
    kpasswd port = 0
    web port = 0
    rpc big endian = No
    deadtime = 0
    getwd cache = Yes
    keepalive = 300
    lpq cache time = 30
    max smbd processes = 0
    max disk size = 0
    max open files = 16384
    socket options = TCP_NODELAY
    use mmap = Yes
    use ntdb = No
    hostname lookups = No
    name cache timeout = 660
    ctdbd socket = 
    cluster addresses = 
    clustering = No
    ctdb timeout = 0
    ctdb locktime warn threshold = 0
    smb2 max read = 1048576
    smb2 max write = 1048576
    smb2 max trans = 1048576
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
    ntp signd socket directory = 
    utmp directory = 
    wtmp directory = 
    utmp = No
    default service = 
    message command = 
    get quota command = 
    set quota command = 
    remote announce = 
    remote browse sync = 
    nbt client socket address = 0.0.0.0
    nmbd bind explicit broadcast = Yes
    homedir map = auto.home
    afs username map = 
    afs token lifetime = 604800
    log nt token command = 
    NIS homedir = No
    registry shares = No
    usershare allow guests = Yes
    usershare max shares = 100
    usershare owner only = Yes
    usershare path = /var/lib/samba/usershares
    usershare prefix allow list = 
    usershare prefix deny list = 
    usershare template share = 
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
    ncalrpc dir = /var/run/samba/ncalrpc
    winbind max domain connections = 1
    winbindd socket directory = 
    winbindd privileged socket directory = 
    winbind sealed pipes = No
    allow dns updates = disabled
    dns forwarder = 
    dns update command = 
    nsupdate command = 
    rndc command = 
    multicast dns register = Yes
    samba kcc command = 
    server services = 
    dcerpc endpoint servers = 
    spn update command = 
    share backend = 
    tls enabled = No
    tls keyfile = 
    tls certfile = 
    tls cafile = 
    tls crlfile = 
    tls dh params file = 
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
    read only = Yes
    acl check permissions = Yes
    acl group control = No
    acl map full control = Yes
    acl allow execute always = No
    create mask = 0744
    force create mode = 00
    directory mask = 0755
    force directory mode = 00
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
    ntvfs handler = 


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[simon]
    path = /mnt/storage
    valid users = simon
    read only = No
    guest ok = Yes
```

On my windows client, running net view I get:
```
System error 53 has occured.
The network path was not found
```

I have no linux clients, but on the linux server if I run 'smbclient -L localhost -U simon' I get:
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (nastest server (Samba, Ubuntu))
    simon           Disk      
    print$          Disk      Printer Drivers
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]


    Server               Comment
    ---------            -------
    KODIPI               OpenELEC
    NASTEST              nastest server (Samba, Ubuntu)


    Workgroup            Master
    ---------            -------
    WORKGROUP            KODIPI
```

kodipi is another linux machine (rpi) running on the network. It doesnt seem to see my windows machine though

---

### Post by volkswagner on 2015-03-29
For giggles, try changing the workgroup to something other than "WORKGROUP" as suggested by SeijiSensei.

I have noticed some interesting things during testing. If I have two workgroups (test and test2) each with samba servers, my 
windows machine wont see either group while belonging to "WORKGROUP". If I change Windows client to either
"TEST" or "TEST2" workgroups, the Windows Client can see servers in both groups.

I also have a SAMBA4 AD DC with two joined member servers. Windows machines can't browse any of these unless joined to the domain first.

Is your windows username the same as samba username? If not, you may want to add a share that allows guest, which may help
browsing via network neighborhood.

---

