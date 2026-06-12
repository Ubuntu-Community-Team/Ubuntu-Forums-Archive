---
title: "Automatically add a samba and a unix user"
date: 2012-09-27
forum: Server Platforms
---

### Post by fweng322 on 2012-09-27
Hi list,


I once had a server running samba 3.5.10.  It was a member of a windows domain.  And when a domain user connected to it, it would automatically create a samba user and a unix user.

Now I reinstalled a server using kubuntu 12.04, running samba 3.6.3.  The new server joined the domain successfully too, but now I need to create a samba user first so that a domain user can connect to it, and then a unix user will be created later.

I've googled a lot and read samba 3.5 howto, but failed to find a solution.  The following are my testparm output:


# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[public]"
Loaded services file OK.
WARNING: The setting 'security=ads' should NOT be combined with the 'password server' parameter.
(by default Samba will discover the correct DC to contact automatically).
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
        workgroup = CORP
        realm = XX.CORP
        server string = %h
        interfaces = 127.0.0.0/8, eth1
        bind interfaces only = Yes
        security = ADS
        map to guest = Bad User
        obey pam restrictions = Yes
        password server = XX.CORP
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        max protocol = SMB2
        add user script = /usr/sbin/useradd -s /bin/false -g users '%u'
        delete user script = /usr/sbin/userdel -r %s
        dns proxy = No
        usershare max shares = 0
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[homes]
        comment = Home Directories
        read only = No
        browseable = No

[public]
        comment = Public directories for RD
        path = /opt/samba
        write list = @users, franklin, root
        read only = No
        force create mode = 0664
        force directory mode = 02775
        guest ok = Yes


Any help will be highly appreciated.


Thanks,
Franklin

---

