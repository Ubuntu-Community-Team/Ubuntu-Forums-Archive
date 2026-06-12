---
title: "Problem with sharing for guest with samba as domain controller"
date: 2014-11-25
forum: Server Platforms
---

### Post by gilgarcia-c on 2014-11-25
Hi Everyone :D

I was tried almost everything on my mind and, to make my ubuntu samba server as active directory domain controller works correctly. (I need some workstations with Win7 to be part of a domain controller for specific services that i have to implement)

I'm using Bind9 as dns backend for samba, I can add new worksatation to my server without problems, but I'm stuck with the sharing folder for guest users.

I hope someone can help me with this, my original domain provision was the next: 

>  samba-tool domain provision --realm=gdom.local --domain=GDOM --server-role=dc --dns-backend=BIND9_DLZ --adminpass="MyPasswordExample" --use-rfc2307 --use-xattrs=yes

And my smb.conf are:

    ```
# Global parameters
    [global]
    
        server string = %h server (Samba, Ubuntu)
        workgroup = GDOM
        realm = gdom.local
        netbios name = GGARCIA
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
        idmap_ldb:use rfc2307 = yes
    
        usershare allow guests = yes
        security = user
        map to guest = Bad User
        guest account = nobody
        guest ok = yes
    
    [netlogon]
        path = /var/lib/samba/sysvol/gdom.local/scripts
        read only = No
        guest ok = yes
    
    [sysvol]
        path = /var/lib/samba/sysvol
        read only = No
        guest ok = yes
    
    
    # Shares
    [gilberto files]
        comment = Gil Files
        path = /shared/files/gilberto
        browseable = yes
        read only = no
        valid users = gilberto
    [public files]
        comment = Public Files
        path = /shared/files/public
        browseable = yes
        read only = no
        guest ok = yes
```

The server are always asking for a valid credentials when we try to access it with something simple like 

> \\\ipaddress\

from any windows machine and from any macosX with 

> smb://ipaddress

when we select log as guest, the Mac OSX reject and ask for a valid credentials again

What i should do? what i miss on my config file.

Thank you in advance and best regards.


Ps1: I was tried with samba from ubuntu repos and with samba compiled from [www.samba.org]("http://www.samba.org")
Ps2: my main language are Spanish, please don't blame my writing hehehehe :P

---

