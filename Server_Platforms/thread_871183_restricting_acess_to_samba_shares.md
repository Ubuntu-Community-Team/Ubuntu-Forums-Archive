---
title: "restricting acess to samba shares?"
date: 2008-07-26
forum: Server Platforms
---

### Post by Comandos on 2008-07-26
Hi,
I have 3 mapped shares on my samba server. The problem is that I'm trying to set up premisions so each user can only see his own share, but instead every user can see all shares. How would I set up permissions correctly?

---

### Post by Comandos on 2008-07-26
Here's my config file:

[global]
    ; General server settings
    netbios name = family-desktop
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    invalid users = root bin daemon adm sync shutdown \


    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /home/samba/
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

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

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[eyal]
    path = /home/samba/eyal
    browseable = yes
    read only = no
    read list = eyal
    write list = eyal
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user =
    force group =

[gal]
    path = /home/samba/gal
    browseable = yes
    read only = yes
    guest ok = no
    writeable = no
    write list = gal
    read list = gal
    valid users = gal
    create mask = 0644
    directory mask = 0755
    force user =
    force group =

[ehud]
    path = /home/samba/ehud
    browseable = yes
    read only = yes
    guest ok = no
    writeable = no
    write list = ebartfeld
    read list = ebartfeld
    valid users = ebartfeld
    create mask = 0644
    directory mask = 0755
    force user =
    force group =

---

### Post by bab1 on 2008-07-27
Use the [homes] section for that.  This is not restricted to the /home/***user*** directory.  I use [homes] at /smb/home.  Only the logged in user can see this (their) directory.  You set the permissions as any Linux directory.  The Samba docs are the best source for further info.

---

