---
title: "different users and home directories"
date: 2009-12-30
forum: Server Platforms
---

### Post by aljachimiak on 2009-12-30
Trying to have different users from my Vista machine keep their documents in their own directory under "/home" 

Each user has a directory that I have confirmed through using "ls" in "/home". 

I have used Webmin to make the unix users also listed as samba users.

here is my smb.conf:

> # Date: 2009/12/28 11:57:09

[global]
    realm = JUBUNTU.NET
    netbios name = # MACHINE DNS NAME
    server string = JUBUNTU
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *New*password* %n\n *Retype*new*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*
    unix password sync = Yes
    log file = /var/log/samba/%m.log
    max log size = 0
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    add user script = /usr/sbin/useradd -g 300 -d /dev/null -c "%U" -s /bin/false -M %u
    add machine script = /usr/sbin/adduser -n -g machines -c Machine -d /var/lib/nobody -s /bin/false %u
    logon path = \\%N\profiles\%u
    logon drive = H:
    domain logons = Yes
    os level = 64
    preferred master = Yes
    domain master = Yes
    wins server = 127.0.0.1
    wins support = Yes
    ldap ssl = no

[netlogon]
    path = /var/netlogon

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[MEDIA DRIVE]
    comment = drive for pictures, music, and movies
    path = /digitalmedia
    force user = root
    read only = No

[ARCHIVE]
    comment = files from old computers
    path = /archive
    force user = root
    read only = No
    guest ok = Yes
    map hidden = Yes
    map system = Yes
    delete readonly = Yes

[BACKUP]
    comment = an active backup of the HOME partition
    path = /backup
    force user = root
    read only = No

[profiles]
    comment = Network Profiles Share
    path = /srv/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    hide files = /desktop.ini/outlook*.Ink/*Briefcase*/
    store dos attributes = Yes

[homes]
    valid users = %S
    read only = No
writable = yesMy probelm specifically is this:  when I login as a different user (as my wife or daughter)  in VISTA I am always directed to the my personal directory, rather than that of my wife or daughter.  

When I try to access the UBUNTU server shares from my  VISTA machine I am prompted for a user name and password.  Even though I have set up profiles for wife, daughter, and me; I can only access the home share when I enter my username and password.  

FYI - I have enacted the root password, although I don't totaly understand what it means.  I figured it would make accessing shares easier - which it has for the other shares that I have that I have added the "force user = root" line on. 

Also - I think there are some lines left over from my failed attempt at roaming profiles...but that is a topic for a different thread...

What adjustments should I make to access the other home directories of other users?

Thanks

---

