---
title: "Samba4 not creating Log file"
date: 2015-06-07
forum: Server Platforms
---

### Post by andrew.coughlin@gmail.com on 2015-06-07
Has anyone seen it where in the smb.conf file you have specificed log file = /some/path/samba.log.%m and it doesn't seem to create that logfile?

[INDENT]# Global parameters
[global]
        netbios name = UNLINDC1SRV
        debug level = 3
        server role = active directory domain controller
        realm = mydomain.local
        write raw = no
        server string = SMB Server
        allow dns updates = nonsecure
        dns forwarder = 192.168.2.8
        workgroup = MYDOMAIN
        read raw = no

#  Server Information

[netlogon]
        path = /var/lib/samba/sysvol/mydomain.local/scripts
        read only = No
#       comment = Network Logon Service
#       writeable = yes
#       public = yes

[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

#  SMBLDAP Scripts
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        add machine script = /usr/sbin/smbldap-useradd -w '%u'
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        delete user script = /usr/sbin/smbldap-userdel %u
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

#Logging
        # Debug logging information
        log level = 2
        log file = /var/log/samba.log.%m
        max log size = 50
        debug timestamp = yes

#  Printing
        printing = cups
        printcap name = cups
        load printers = yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
# to allow user 'guest account' to print.
   guest ok = yes
   writable = no
   printable = yes
   create mode = 0700

[home]
         path = /home/samba/
         read only = No[/INDENT]


When I do a samba-tool testparm -v | grep log here is the output:[INDENT]root@:/var/log/samba# samba-tool testparm -v | grep log
Global parameter add user to group script found in service section!
Global parameter add user script found in service section!
Global parameter add machine script found in service section!
Global parameter add group script found in service section!
Global parameter delete group script found in service section!
Global parameter delete user script found in service section!
Global parameter delete user from group script found in service section!
Global parameter set primary group script found in service section!
Global parameter log level found in service section!
Global parameter log file found in service section!
Global parameter max log size found in service section!
Global parameter debug timestamp found in service section!
Global parameter printcap name found in service section!
Global parameter load printers found in service section!

        log level = 3
        syslog = 1
        syslog only = No
        log file =
        max log size = 0
        log writeable files on exit = No
        logon script =
        logon path =
        logon drive =
        logon home =
        domain logons = No
        init logon delayed hosts =
        init logon delay = 0
        eventlog list =
        log nt token command =
        winbind offline logon = No
        dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver
[netlogon][/INDENT]

Samba version 4.1.6-Ubuntu

---

### Post by volkswagner on 2015-06-07
Your smb.conf is malformed.

You should not have global parameters after share definitions.


The following should be moved up to the global section as you have it listed under [sysvol] share.
```
# SMBLDAP Scripts
add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
add user script = /usr/sbin/smbldap-useradd -m '%u'
add machine script = /usr/sbin/smbldap-useradd -w '%u'
add group script = /usr/sbin/smbldap-groupadd -p '%g'
delete group script = /usr/sbin/smbldap-groupdel '%g'
delete user script = /usr/sbin/smbldap-userdel %u
delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

#Logging
# Debug logging information
log level = 2
log file = /var/log/samba.log.%m
max log size = 50
debug timestamp = yes

# Printing
printing = cups
printcap name = cups
load printers = yes
```

As you can see from testparm output, error points to all similar to this:
```
[COLOR="#FF0000"]Global parameter[/COLOR] add user to group script [COLOR="#FF0000"]found in service section![/COLOR]
```

---

### Post by andrew.coughlin@gmail.com on 2015-06-08
Awesome! Thanks alot.... now this makes sense... guess I took this as a good thing that it was found in the service section.

---

