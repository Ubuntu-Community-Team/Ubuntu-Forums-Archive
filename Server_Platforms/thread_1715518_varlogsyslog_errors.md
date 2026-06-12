---
title: "/var/log/syslog errors"
date: 2011-03-27
forum: Server Platforms
---

### Post by Z.K. on 2011-03-27
I am getting a bunch of errors in my /var/log/syslog like below only a lot more over and over.  It seems to be related to samba, but I am not sure exactly what it means.  I have also posted my smb.conf file.  

> 
[2011/03/26 22:28:36,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
Mar 26 22:28:36 server winbindd[1215]:   idmap_alloc module tdb already registered!
Mar 26 22:28:36 server winbindd[1215]: [2011/03/26 22:28:36,  0] winbindd/idmap.c:149(smb_register_idmap)
Mar 26 22:28:36 server winbindd[1215]:   Idmap module passdb already registered!
Mar 26 22:28:36 server winbindd[1215]: [2011/03/26 22:28:36,  0] winbindd/idmap.c:149(smb_register_idmap)
Mar 26 22:28:36 server winbindd[1215]:   Idmap module nss already registered!
Mar 26 22:28:36 server winbindd[1215]: [2011/03/26 22:28:36,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
Mar 26 22:28:36 server winbindd[1215]:   Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration


smb.conf
```

cat /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = Server
    server string = %h server (Samba, Ubuntu)
    workgroup = workgroup

    passdb backend = tdbsam
    security = user
    null passwords = true
    #username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes
    default = printers

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/


; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

;[printers]
;    path = /tmp
;    printable = yes
;    guest ok = yes
;    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/usbext/extdrive
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755


```

:confused:

---

