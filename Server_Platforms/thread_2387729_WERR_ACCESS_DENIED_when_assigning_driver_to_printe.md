---
title: "WERR_ACCESS_DENIED when assigning driver to printer [Samba]"
date: 2018-03-22
forum: Server Platforms
---

### Post by cradoumis on 2018-03-22
I have a fairly simple configuration following the following two guides
[https://www.tecmint.com/join-ubuntu-to-active-directory-domain-member-samba-winbind/](https://www.tecmint.com/join-ubuntu-to-active-directory-domain-member-samba-winbind/)
and
[https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Print_Server](https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Print_Server)

Everything turned out great for the first server (Site 1), but I am trying to replicate it on a fresh installation to a new server in another site (Site 2). I am able to join the machine to the domain, the DNS record and AD objects are created correctly, the Samba smb.conf file reflects the correct server name, the /etc/hosts and /etc/hostname reflect correctly. the /etc/network/interfaces are correct, all /etc/resolv.conf and DNS entries are all correct. I'm also getting all the correct info with 'net ads info'

I am able to share a printer, and I'm able to install the necessary print drivers (Just using the Windows Print Management), and yes I do have the SePrintOperatorPrivilege set for my domain account used to add the drivers. The Driver directory is set correctly, and is the same on both servers.

But, when I try to associate the driver to the printer with either the Windows Print Management, or with rpcclient, I get the following:
SetPrinter call failed!
result was WERR_ACCESS_DENIED

I have tried dropping the machine from the domain, re-adding, cloning the original server and changing the DNS / IP and hostnames in smb, changing the hostname, re-adding. There is nothing in logs or debugs that are showing the particular thing that is denied. I'm able to see my domain users / groups with either wbinfo -u / -g, or getent passwd/ group.

Even after cloning the original machine I still get the same error. Doesn't make any sense to me.

Here is part of my smb.conf file

[global]
        workgroup = DOMAIN
        realm = DOMAIN.COM
        netbios name = servername
        security = ADS
        template shell = /bin/bash
        dns forwarder = domaincontroller
        idmap config * : backend = tdb
        #idmap config *:range = 50000-1000000
        idmap config * : range = 16777216-33554431
        winbind use default domain = false
        winbind offline logon = false
        winbind nss info = rfc2307
        winbind enum users = yes
        winbind enum groups = yes
        hostname lookups = Yes
        vfs objects = acl_xattr
        map acl inherit = Yes
        store dos attributes = Yes
        map to guest = Bad User
        local master = No
        server string = Ubuntu Print Server


        # Fork processes
        #rpc_server:spoolss = external
        #rpc_daemon:spoolssd = fork


        # Windows x64 Print Driver
        spoolss: architecture = Windows x64


        # Logging
        log file = /var/log/samba/log.%m
        log level = 1 auth:1 winbind:1
        max log size = 50



[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = yes
        print ok = Yes
        browseable = yes
;       writable = yes
        guest ok = yes
        public = yes


[print$]
        comment = Printer Drivers
        path = /etc/samba/drivers
        read only = no
;       create mask = 0777
;       guest ok = yes
        browseable = yes
;       writeable = yes

This is identical to the original server with the exception of the dns forwarder, and the netbios name.

Any help on this would be extremely appreciated, i have been banging my head with this one for a few days. I even did straces and still can't find what is causing the access denied.

---

### Post by volkswagner on 2018-03-23
I don't see your printer backend directive, like:
```
printing = CUPS
```
Is CUPS your backend?


I'm surprised to see guest and public info in your printer share.
It's probably not related to your issue, but did you see this in
your linked samba documentation?
```
SMB (Server Message Block)-based printers: smb://username:password@domain/windows_print_server_host_name/printer_name
Note that forwarding a job to a print server running Windows Vista or newer, or Windows Server 2008 or newer requires authentication.
```

```

```

---

### Post by cradoumis on 2018-03-26
Sorry, the printing backend was not shown in the snippet i sent.

printing = lprng

This is nothing more than a Ghostscript printer that converts the print job to PDF.
Using rpcclient to set the print driver, I get access denied as well.

---

