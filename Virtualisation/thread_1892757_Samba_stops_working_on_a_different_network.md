---
title: "Samba stops working on a different network"
date: 2011-12-08
forum: Virtualisation
---

### Post by ratul.dasgupta on 2011-12-08
Hi,
I am absolutely new to Linux in general and this is my first post as well. So please excuse me if I am asking a stupid question! or if this is not the right forum!

I have Ubuntu 8.04 running on Virtualbox. The host OS is Windows Vista. I read a post on this forum on how to configure Samba(by Stormbringer) so that I can access files from Windows
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
The guide works like a charm when I am on the office network. 

However, when I am using my home network (or when I am not on any network), the network drive does not respond, gives me an error that the network path was not found.
I am however able to ping my virtual ubuntu 192.168.56.10


Any suggestions?If you need any other information, please let me know
Thanks in advance!!



Here's my smb.conf file

[global]
    ; General server settings
    netbios name = Ubuntu8-Virtual
    server string =
    workgroup = domainname.of.myoffice
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

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
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
   ; path = /var/lib/samba/printers
   ; browseable = yes
   ; guest ok = yes
   ; read only = yes
   ; write list = root
   ; create mask = 0664
   ; directory mask = 0775

[printers]
   ; path = /tmp
   ; printable = yes
   ; guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /srv/sambatest
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    force user = ubuntu
    force group = ubuntu

---

