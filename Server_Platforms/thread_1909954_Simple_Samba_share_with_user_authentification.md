---
title: "Simple Samba share with user authentification"
date: 2012-01-16
forum: Server Platforms
---

### Post by harpert on 2012-01-16
I was trying to set up a Samba server on my UBUNTU 10.4 and thought to have been successful.
However I have noticed that the share is available not only for the intended users but to everybody on the LAN.

Can anybody give an advice what line to /delete/add/alter to get the intended behaviour!?!?!

Tanks in advance 
Harpert

Here my smb.conf (created wit SWAT)
# Samba config file created using SWAT

[global]
    workgroup = MY_WORKGROUP
    server string = Samba file and print server
    interfaces = 127.0.0.1/8, 192.168.10.0/24
    bind interfaces only = Yes
    update encrypted = Yes
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    guest account = smbguest
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    password level = 6
    username level = 6
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 994
    name resolve order = wins lmhosts bcast
    client signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    load printers = No
    printcap name = cups
    machine password timeout = 120
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    delete user script = /usr/sbin/userdel '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    logon script = %G.bat
    logon path = \\%L\profiles\%u
    logon drive = m:
    logon home = \\%L\homes\%u
    os level = 33
    local master = No
    domain master = No
    dns proxy = No
    remote announce = 192.168.10.255
    remote browse sync = 192.168.10.255
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind separator = @
    winbind cache time = 360
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind nested groups = No
    winbind nss info = no
    hosts allow = 127., 192.168.10.
    cups options = raw
    follow symlinks = No

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    browseable = No
    browsable = No
    locking = No
    strict locking = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No
    locking = No
    strict locking = No

[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = lprm -P'%p' %j
    use client driver = Yes

[HP-LJ-1300]
    comment = HP-Laserjet 1300
    path = /tmp
    create mask = 0700
    guest ok = Yes
    printable = Yes
    printer name = HP-LJ-1300

[2T-NTFS-1]
    comment = Our Files (auf 2TiB-Part1)
    path = /media/2T-NTFS
    valid users = me, her
    read list = me, her
    write list = me, her
    read only = No
    locking = No
    strict locking = No

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    browseable = No
    browsable = No
    locking = No
    strict locking = No

---

