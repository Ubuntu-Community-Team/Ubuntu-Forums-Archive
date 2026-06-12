---
title: "Samba 4.4.4 domain member, writable impossible"
date: 2017-01-02
forum: Server Platforms
---

### Post by someuser000 on 2017-01-02
Hello,
i'm trying to get samba working for everyone from my domain.
I successfully joined the domain with "net rpc join -S 'DOMAIN' -U username%pw" and tried "net rpc rights grant 'DOMAIN\Domain Users' -U....".
/opt/test is 777 
testparm gives me no erros, nothing special logged and i can indeed browse the share from windows 7/10 and with "smbclient //fileserver/share1 -U Tester" (Tester is a domain account).
I can read everything from this share but not write :(

```
#smbclient //fileserver/share1 -U TesterEnter Tester's password:
Domain=[DOMAIN] OS=[Windows 6.1] Server=[Samba 4.4.4]
smb: \> mkdir teeest
NT_STATUS_ACCESS_DENIED making remote directory \teeest
smb: \> ls
  .                                   D        0  Mon Jan  2 16:04:32 2017
  ..                                  D        0  Mon Jan  2 15:40:35 2017
  ll.txt                              A        0  Mon Jan  2 16:04:30 2017


                52403200 blocks of size 1024. 40043060 blocks available
smb: \>



```
```

[global]


        workgroup = DOMAIN
        realm = DOMAIN.LOCAL
        netbios name = SERVERNAME
        netbios aliases = SERVERNAME.DOMAIN.local SERVERNAME
        server string = Fileserver
        security = ADS
        dns forwarder = 192.168.2.100
        encrypt passwords = yes
        wins support = yes
        winbind nss info = rfc2307
        winbind trusted domains only = no
        winbind use default domain = yes
        winbind enum users  = yes
        winbind enum groups = yes
        winbind cache time = 10
        client use spnego = yes
        client ntlmv2 auth = yes
        restrict anonymous = 2
        domain master = no
        local master = no
        preferred master = no
        os level = 0


        vfs objects = acl_xattr
        map acl inherit = Yes
        store dos attributes = Yes


        domain logons = No
        wins support = Yes
        local master = No
        domain master = No
        preferred master = No


        load printers = no
        printing = bsd
        printcap name = /dev/null
        disable spoolss = yes


[share1]
        comment = share
        path = /opt/test


#  create mask = 0777
#  directory mask = 0777


writeable = yes
public = yes
guest ok = yes
browsable = yes
usershare allow guests = yes
map to guest = bad user
```

---

### Post by cariboo on 2017-01-02
Server question moved to server platforms.

---

### Post by darkod on 2017-01-02
What about the linux permissions of /opt/test? Samba rights are one part of the setup, users also need correct folder/file permissions.

Post the permissions of /opt/test and I bet they allow only read to all users. They probably allow write only to root.

---

### Post by someuser000 on 2017-01-06
see attachment

(test is now anonymous)

tried even chown nobody:user and nobody:nobody -R /opt/anonymous with guest account = nobody in smb.conf



the strange thing is that everything is working as expected when i use "smbd -i" without any errors/warnings


[root@xxxxx]# getfacl /opt/anonymous
getfacl: Entferne führende '/' von absoluten Pfadnamen
# file: opt/anonymous
# owner: nobody
# group: users
user::rwx
group::rwx
other::rwx

---

