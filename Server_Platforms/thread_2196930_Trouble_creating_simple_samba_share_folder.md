---
title: "Trouble creating simple samba share folder"
date: 2014-01-01
forum: Server Platforms
---

### Post by slgtheindividual on 2014-01-01
I've never used samba before or set up any kind of server or anything similar. I've had a look at several samba set up and how to files but I keep having trouble connecting. I'm trying to set up a folder on my ubuntu 13.10 under /home/slg/Shared which is accessible from my android tablet running AndSMB. I know this isn't the place for AndSMB help but I was hoping someone could look at my /etc/samba/smb.conf file just to check if it's set up ok? Thank you in advance. Here's my /etc/samba/smb.conf file:

```

[global]
    ; General server settings
    netbios name = Shared
    server string =
    workgroup = slg-Aspire-E1-571
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


[Shared]
    path = /home/slg/Shared
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = slg
    force group = slg

```


I have set the smb password for slg too.

---

### Post by Iowan on 2014-01-01
Moved to Server Platforms

---

### Post by Morbius1 on 2014-01-01
I don't know what compels people to deviate from the default smb.conf. 

Anywho, I know nothing about AndSMB but there is one thing and that's your workgroup name.

It normally doesn't mater what your workgroup name is or if it even matches anyone else's in the lan but it may be an issue if you have one as long as yours - it has to be 15 characters or less in length so change it to .. say ... 
```
workgroup = ASPIRE-E1-571
```
Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```
Then wait a good few minutes for things to settle down in the network.

Do you have a desktop on this machine ( Gnome, XFCE, ... ) or is it a headless server?

---

### Post by slgtheindividual on 2014-01-01
sorry for posting in the wrong place.

Ok I changed the workgroup name as suggested but still can't connect unfortunately. 
I'm just running normal desktop version of ubuntu 13.10. I really don't know anything about servers or anything, just what I've read from how to's for samba.

---

### Post by slgtheindividual on 2014-01-01
Ok well it seems I can connect from another windows laptop just not my android app so it's set up fine. thank you for your help

---

### Post by Morbius1 on 2014-01-01
Well I just did something interesting. I just installed Android into a VirtualBox VM and then installed AndSMB.

Created a connection:
[ATTACH=CONFIG]249090[/ATTACH]
Then connected to the Linux Samba server without issue with both upload and download support:
[ATTACH=CONFIG]249091[/ATTACH]

I can do it by ip address like above and also by netbios name. The only thing it can't do is recognize an mDNS qualified host name as in hostname.local. It appears there is no Avahi/Zeroconf support in Andoroid.

---

