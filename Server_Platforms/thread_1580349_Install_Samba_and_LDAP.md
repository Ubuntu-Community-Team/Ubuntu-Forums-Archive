---
title: "Install Samba and LDAP"
date: 2010-09-23
forum: Server Platforms
---

### Post by wizard210 on 2010-09-23
I am tickering around with 10.04 installing a samba + ldap. 

I have ldap installed and am installing samba.

I'm using the following smb.conf
```
[global]
        # Domain name ..
        workgroup = SAMBA
        # Server name - as seen by Windows PCs ..
        netbios name = EXAMPLE
        # Be a PDC ..
        domain logons = Yes
        domain master = Yes
        # Be a WINS server ..
        wins support = true

        obey pam restrictions = Yes
        dns proxy = No
        os level = 35
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        pam password change = Yes

        # Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
        unix password sync = no
        ldap passwd sync = yes

        # Printing from PCs will go via CUPS ..
        load printers = yes
        printing = cups
        printcap name = cups

        # Use LDAP for Samba user accounts and groups ..
        passdb backend = ldapsam:ldap://localhost

        # This must match init.ldif ..
        ldap suffix = dc=example,dc=com
        # The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
        # This is done by running 'sudo smbpasswd -w'.
        ldap admin dn = cn=admin,dc=example,dc=com

        # 4 OUs that Samba uses when creating user accounts, computer accounts, etc.
        # (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)
        ldap machine suffix = ou=Computers
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        # Samba and LDAP server are on the same server in this example.
        ldap ssl = no

        # Scripts for Samba to use if it creates users, groups, etc.
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        delete user script = /usr/sbin/smbldap-userdel %u
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

        # Script that Samba users when a PC joins the domain ..
        # (when changing 'Computer Properties' on the PC)
        add machine script = /usr/sbin/smbldap-useradd -w '%u'

        # Values used when a new user is created ..
        # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
    logon drive =
        logon home =
        logon path =
        logon script = allusers.bat


        # This is required for Windows XP client ..
        server signing = auto
        server schannel = Auto

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        admin users = root
        guest ok = Yes
        browseable = No
        logon script = allusers.bat

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /var/lib/samba/profiles
        read only = No
        profile acls = Yes
        browsable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        use client driver = Yes
        create mask = 0600
        guest ok = Yes
        printable = Yes
        browseable = No
        public = yes
        writable = yes
        admin users = root
        write list = root

[print$]
        comment = Printer Drivers Share
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        admin users = root

[shared]
        writeable = yes
        path = /var/lib/samba/shared
    public = yes
    browseable = yes


[archive]
        path = /exports/archive
        browseable = yes
        create mask = 755
        directory mask = 755
        read only = no

```in the terminal when I run this commad I receive the following

```
sudo smbclient -L localhost
Enter root's password: 
Anonymous login successful
Domain=[SAMBA] OS=[Unix] Server=[Samba 3.4.7]
tree connect failed: NT_STATUS_END_OF_FILE

```Google searches have failed to help me out. I'm totally stuck right now.

Can somonee help?:confused:

---

### Post by koenn on 2010-09-25
found one page that suggests this 'Failure of this test may mean that Samba isn't running on the server at all and may need to be started.'

Maybe restart samba ?

I notice you're running this against localhost. Might be worth checking if samba actually listens on localhost (or test from a different machine)

---

### Post by luvshines on 2010-09-29
What exactly are you trying to do ??

You want LDAP users should be allowed to connect to Samba shares with their passwords ??

Also, can you run and paste the output of same smbclient command with some debugging (-d 5 maybe)

---

