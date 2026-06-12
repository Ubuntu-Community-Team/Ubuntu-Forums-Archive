---
title: "samba problems"
date: 2007-03-17
forum: Server Platforms
---

### Post by Mrwasab1 on 2007-03-17
hi guys,
I have 2 machines, 1 windows and 1 ubuntu 6.10
they both connect over a router. the windows pc is wireless and this one is wired. i have followed the guide found here [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+howto](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+howto)

and it all went a bit further than what it did before.

I have followed it down to a T, and when i type in \\penguin101 in the run box in windows, it only shows me printers and faxes on the ubuntu machine...nothing else. so the share directories arent showing up.

below is my config, please let me know what im doing wrong.
thanks

Edit: oh and i guess one more thing, i know how to brows files from windows to ubuntu, but how do i do it the other way around?

 
```
[global]

    ; General server settings

    netbios name = penguin101

    server string =

    workgroup = MSHOME

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



[MyFiles]

    path = /home/samba

    browseable = yes

    read only = no

    guest ok = no

    create mask = 0644

    directory mask = 0755

    force user = mrwasabi

    force group = mrwasabi

```

---

### Post by elst on 2007-03-17
Try putting the share name in the run box: \\penguin101\MyFiles. IIRC, the browse lists for each Windows system are updated every 15 minutes, and it's not absolutely guaranteed that a share will be picked up on the first pass.

On Ubuntu, go to Places > Network Servers. There will be a pause as it scans. Then click on the "Windows Network" icon.

---

### Post by Mrwasab1 on 2007-03-17
Well ive tried entering \\penguin101\myfiles in the run box, it just keeps telling me that the path could not be found

i went to places and network servers. i can see my windows machine there. When i click on it, it asks me for a password. The HOWTO said to just press enter if you didn't have a password set up in windows (which i don't) but when i do that the box disappears and comes back again asking me for the password

---

### Post by hortimech on 2007-03-18
Have you set mrwasabi as a user on the samba server? if not then do , then set up the password with "smbpasswd -a mrwasabi" enter your password, then enter it again. You should then be able to browse to the share from your windows box, you will probably have to add "encrypt passwords = yes" to your smb.conf.
I believe that by denying guest access you need passwords!

---

### Post by elst on 2007-03-18
> **Mrwasab1 said:**
> Well ive tried entering \\penguin101\myfiles in the run box, it just keeps telling me that the path could not be found

Try putting the IP address instead of the NETBIOS name. If that works then the problem is with name resolution.

WRT to accessing a Windows system, you'll probably still need to specify a username even if you don't have a password on the account.

---

