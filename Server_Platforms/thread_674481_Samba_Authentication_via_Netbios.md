---
title: "Samba Authentication via Netbios"
date: 2008-01-21
forum: Server Platforms
---

### Post by tek55 on 2008-01-21
Hi,

This is my first post, and I'm new to Linux.

I have been scouring the internet to find a way to integrate Vista with Samba, I'm running Ubuntu 7.10 Desktop with server modules installed to share files.

This is a test server that I put together so I can implement it quicker at my workplace.

This site was extremely beneficial to me ([http://www.cody-snider.com/linux/howto-setup-samba-peer-to-peer-with-windows.html](http://www.cody-snider.com/linux/howto-setup-samba-peer-to-peer-with-windows.html))
Prior to finding it, I could NOT get my Vista setup to work with my Samba server even after changing the registry hacks.

I removed a "force user = _______" line from the smb.conf file because I'd LIKE to have each computer that logs in have access to their directory with symbolic links in it to the actual shares, and I wasn't sure if I had to force a certain user to login or not, but I have different levels of groups and I don't know how to make this happen.

My question is this:

Can anybody help me configure my smb.conf file so that users who log in (preferrably by netbios identification) see only their home directory?

Attached is my smb.conf file.


[global]
    ; General server settings
    netbios name = TCRSERVER
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_$
    interfaces = lo, eth0
    bind interfaces only = true

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
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
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

[MyFiles]
    path = /data
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
;    force user = tcr
;    force group = tcr


Thanks!

---

### Post by cdenley on 2008-01-22
I'm not sure what you mean by "netbios identification". If you want to have a share for each computer, I think you can do something like this

```

[netbios]
path = /var/lib/samba/netbios/%m
valid users = %U
create mode = 0660
directory mode = 0775

```

That should create a share for each netbios name. A directory with same name as the netbios name will have to exist in /var/lib/samba/netbios, and the user will have to have unix permissions to access it. If you want to remove other shares, just comment them out. If you want them available, but not visible, set browseable=no.

---

