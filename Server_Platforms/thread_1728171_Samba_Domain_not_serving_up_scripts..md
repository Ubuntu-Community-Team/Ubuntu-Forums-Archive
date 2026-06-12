---
title: "Samba Domain not serving up scripts."
date: 2011-04-13
forum: Server Platforms
---

### Post by hey_pig on 2011-04-13
I seem to have an odd Samba domain controller issue. My samba domain controller will not serve up scripts upon login, and acts very slow when _not_ connected to the Internet. Also, network browsing from windows boxes shows no computers on the network once all this happens. Once the net connection comes back up, everything is fine. Anyone know why this may be happening?

Domain server: 
Ubuntu 10.04.2 LTS
Samba 3.4.7

Router:
Smoothwall Express 3.0-polar-i386 3.0 (update6). Router is set up as DHCP, and appears to be serving up normal IP's when the Internet connection goes down. I can ping the domain server at its normal IP when the connection goes down.


Heres my smb.conf:
```

[global]
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        socket options = TCP_NODELAY
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passdb backend = tdbsam
        dns proxy = no
        netbios name = dominium
        netbios aliases = Dominium
        server string = %h server (Samba, Ubuntu)
    username map = /etc/samba/smbusers
    name resolve order = wins bcast hosts
#       invalid users = root
        unix password sync = yes
        workgroup = OFFICE
        os level = 65
        syslog = 0
        security = user
        usershare allow guests = no
        panic action = /usr/share/samba/panic-action %d
        preferred master = yes
        max log size = 1000
        pam password change = yes
    add user script = /usr/sbin/useradd -m %u
        delete user script = /usr/sbin/userdel -r %u
        add group script = /usr/sbin/groupadd %g
        delete group script = /usr/sbin/groupdel %g
        add user to group script = /usr/sbin/usermod -G %g %u
        add machine script = /usr/sbin/useradd -s /bin/false -d /dev/null %u
        logon script = %G.bat
        logon path =
        logon drive = Z:
        domain logons = Yes
        preferred master = Yes
        wins support = Yes

[homes]
    comment = Home Directories
    valid users = %S
    read only = No
    browseable = No

#[printers]
#    comment = SMB Print Spool
#    path = /var/spool/samba
#    guest ok = Yes
#    printable = Yes
#    use client driver = Yes
#    default devmode = Yes
#    browseable = No

[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba
    guest ok = No
        browseable = No

```This only happens when our internet connection goes down. When its up, everything is works fine. Ive tried #samba #ubuntu-server #ubuntu on freenode, no one will even answer me. Any help would be greatly appreciated.

---

### Post by hey_pig on 2011-04-13
log from one of the users trying to log in:

[http://paste.ubuntu.com/593636/](http://paste.ubuntu.com/593636/)
and another:
[http://paste.ubuntu.com/593631/](http://paste.ubuntu.com/593631/)

---

### Post by root911911 on 2011-08-02
Hi there.

I am having the same problem? could any one tell me why samba is so slow when internet is not connected?

Thanks

---

