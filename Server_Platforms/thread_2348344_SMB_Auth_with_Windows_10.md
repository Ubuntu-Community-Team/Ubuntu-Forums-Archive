---
title: "SMB Auth with Windows 10"
date: 2017-01-02
forum: Server Platforms
---

### Post by travis7 on 2017-01-02
Hello,

Before I get into my post I'll list some relevant details,

smbd version : 4.4.5-Ubuntu
Ubuntu Server version : 16.10

smb.conf

```

   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\                                                                                                                                                             n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = no
[media]
        path = /mnt/nas/media
        valid users = travis
        writable = yes
        browsable = yes
        read only = no
        guest ok = no
        public = no
        create mask = 0777
        directory mask = 0775
[sysadmin]
        path = /mnt/nas/sysadmin
        valid users = travis
        writable = yes
        browsable = yes
        read only = no
        guest ok = no
        public = no
        create mask = 0770
        directory mask = 0775
        force group = nasdata
[documents]
        path = /mnt/nas/documents
        valid users = travis
        writable = yes
        browsable = yes
        read only = no
        guest ok = no
        public = no
        create mask = 0770
        directory mask = 0775
        force group = nasdata
[wwwdata]
        path = /mnt/nas/wwwdata
        valid users = travis
        writable = yes
        browsable = yes
        read only = no
        guest ok = no
        public = no
        create mask = 0770
        directory mask = 0775
        force group = wwwdata
[backups]
        path = /mnt/nas/backups
        valid users = travis
        writable = yes
        browsable = yes
        read only = no
        guest ok = no
        public = no
        create mask = 0770
        directory mask = 0775
[servers]
        path = /mnt/nas/servers
        valid users = travis
        writable = yes
        browsable = yes
        read only = no
        guest ok = no
        public = no
        create mask = 0775
        directory mask = 0775

```

Now for what's happening. It seems that if I disable SMB 2 & 3 on my Windows 10 box, that I can authenticate and connect to my samba shares just fine. However, in Windows 10 with SMB 3 enabled, every authentication attempt fails. I have read statements such as:

> [COLOR=#242729][FONT=Arial]Windows 10 will try to negotiate SMB3_11, which Samba4 doesn't yet support[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]except in the current 4.3 release candidate. I suspect for now disabling[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]SMB2/3 on the Windows 10 client is your best, if not ideal, option.[/FONT][/COLOR]

Which I have also heard isn't entirely correct as Windows 10 should have auto-negotiate capabilities, and should auto-negotiate back down to SMB 3. However, if this is the case then why do samba authentication requests only work with SMB 3 and 2 forcefully disabled? 

Commands used to disable SMB 3 and 2 within Windows 10:

```

[COLOR=#000000][FONT=&amp]sc.exe config lanmanworkstation depend= bowser/mrxsmb10/nsi [/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]sc.exe config mrxsmb20 start= disabled[/FONT][/COLOR]

```

---

### Post by volkswagner on 2017-01-03
Please post file permissions:
```
ls -al /mnt/nas/media
```

Did you create a Linux user Travis and a samba user Travis? Is your Windows 10 user name Travis and using same password as Linux/samba user?

---

### Post by travis7 on 2017-01-03
> **volkswagner said:**
> Please post file permissions:
```
ls -al /mnt/nas/media
```

Did you create a Linux user Travis and a samba user Travis? Is your Windows 10 user name Travis and using same password as Linux/samba user?[URL="http://screencast.com/t/3M2elSbLj"]

http://screencast.com/t/3M2elSbLj[/URL]
[URL="http://screencast.com/t/ExRLsIrL"]
http://screencast.com/t/ExRLsIrL[/URL]

[http://screencast.com/t/xYcKuFW1](http://screencast.com/t/xYcKuFW1)

The user travis exists only on the linux box. I setup a samba password with *smbpasswd*. The linux user travis, and samba user travis, both have the same password. The Windows 10 username is travi (note the missing s).

---

### Post by volkswagner on 2017-01-04
What error message do you get when trying to access the share?

Is Windows 10 client part of WORKGROUP? Have you tried entering the username as workgroup\travis?

I would try creating a user on Win10 named travis. You can get unexpected results when username does not match.

What happens if you comment out the "valid users = travis"?

Please post code response using code tags not image links.

---

### Post by travis7 on 2017-01-04
> **volkswagner said:**
> What error message do you get when trying to access the share?

Is Windows 10 client part of WORKGROUP? Have you tried entering the username as workgroup\travis?

I would try creating a user on Win10 named travis. You can get unexpected results when username does not match.

What happens if you comment out the "valid users = travis"?

Please post code response using code tags not image links.
 
Last night I redid my entire VM install of my Samba server.

For no apparent reason, everything works fine now. 

```

ServerName ShareName UserName        Credential              Dialect NumOpens
nas        documents OFFICE-PC\travi MicrosoftAccount\travis 3.1.1   1

```

---

