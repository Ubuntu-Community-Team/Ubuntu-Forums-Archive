---
title: "2 servers, 1 WinXp and not able to see 2nd server shared folder"
date: 2007-11-16
forum: Server Platforms
---

### Post by Alt69 on 2007-11-16
Hi , let me start by saying I am a newbie to Ubuntu and the Linux environment. Been playing with it, and have had lots of practice installing. :)

**Issue:** I can’t get my read/write access to the share file folder on my second server.

**Setup:**
-Two physical servers – both have the Desktop interface
- Windows XP
-Server-kbts:
  o Has been setup up as LAMP server
  o Everything installed on one drive (no-partition – this was my first attempt)
  o Only working on getting Samba working
  o I am able to connect from my WinXp to the shared folder
  o Server kbts can see Server kbts1 share folder, but can’t log in.

- Server-kbts1:
  oInstalled it as a Samba server
  oPartioned 
    - Filesyetm, /user and /home each on their own partition
    - Not able to see Server-kbts shared folder

**Description:**
I have followed the HOWTO: Setup Samba peer-to-peer with Windows to setup both servers.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer)

As mentioned earlier, I can connect to server-kbts with the WinsXP laptop. While I am very surprised at how long the file transfer between them takes, it is working. I can read, write and copy to the share folder.

**Server kbts smb.conf**

[global]
    ; General server settings
    netbios name = kbts
    server string =        
    workgroup = WORKGROUP
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

[Personal]
    path = /home/personal
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = windows1
    force group = windows1
    browsable = yes
    writable = yes

**Server kbts1 smb.conf**

[global]
    ; General server settings
    netbios name = kbts1
    server string =
    workgroup = WORKGROUP
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

[az]
    path = /home/az/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = az
    force group = az
    writeable = yes


From the WinsXp laptop, I can’t see the directory on kbts1.   

The goal is to create multiple private shares for a number of users, as well as global public directories.

Any thoughts, suggestion on what I am doing wrong?

thanks

---

### Post by HermanAB on 2007-11-17
Hmm, you have to run some manual tests to see what is going on.  See this document - it starts off talking about Mandriva - just skim over that part:
[http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

In your smb.conf, I suggest you change the create mask to 775 (The execute bit in Linux, is used for something else in Windows and should be set).

Also make sure that the user windows1 exists  on Linux and that the password is set with "smbpasswd -a windows1".

Cheers,

Herman

---

### Post by Alt69 on 2007-11-18
Hi, thanks for the additional info. I have tried the commands in the bebug section but still not there. 

I have decided to rebuild the accoutns and the dirrectory. So deleted the users and groups, created a new share, and also removed the 
  force user =
  force group =
parms.

I now have full access, but that isn't what I was striving for. I still need to have security in place to ensure only the appropriate people have access to the appropriate files.

Will try again redoing things from scratch. :(


cheers,

---

