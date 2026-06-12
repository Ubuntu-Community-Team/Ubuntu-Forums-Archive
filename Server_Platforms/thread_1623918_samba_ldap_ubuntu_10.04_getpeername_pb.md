---
title: "samba ldap ubuntu 10.04 getpeername pb"
date: 2010-11-17
forum: Server Platforms
---

### Post by fabien43 on 2010-11-17
Hello,   I have a problem after the installation of a coupled samba ldap on ubuntu 10.04.  (Ref: [samba tutorial]("http://translate.googleusercontent.com/translate_c?hl=fr&ie=UTF-8&sl=fr&tl=en&u=http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html&rurl=translate.google.fr&twu=1&usg=ALkJrhiJgB8YwvIzZrAKNTWxxleQ74PuUw") ).  After  following the tutorial, I find myself with this kind of error messages  (hostanme server: ubuntu, XP client hostname: original):
```

cat /var/log/samba/log.original
[2010/11/17 12:00:15,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2010/11/17 12:00:15,  0] smbd/process.c:62(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
```This happens when I try to connect with any user.  However, with the root user (part 
of the samba group administrators) have access to all the shares I 
defined but no other users. When I try with any user I get an error saying it can not find the resource on the network.   I took a look at the posts with this kind of error and make the smb.conf qques ds mods but nothing helped. 
  If anyone has an idea to progress .[LEFT]
[/LEFT]
Thank by advance

 [LEFT]
[/LEFT]
ps: the smbclient-L localhost on the server can easily see the shares. 
  smb.conf (all shares are not being, too heavy): 


> [global]
       # Domain name ..
       workgroup = mondomaine

       # Server name - as seen by Windows PCs ..
       netbios name = maquette
       # Be a PDC ..
       domain logons = Yes
       domain master = Yes
    local master = yes
    preferred master = yes
       # Be a WINS server ..
       wins support = true

    security = user
    time server = yes
    veto files = /lost+found/ .recycle/

       obey pam restrictions = Yes
       os level = 65
       log file = /var/log/samba/log.%m
       max log size = 1000
       syslog = 0
       panic action = /usr/share/samba/panic-action %d
       pam password change = Yes

       # DisAllows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
       unix password sync = no
       ldap passwd sync = no
interfaces = eth0
bind interfaces only = Yes
       # Printing from PCs will go via CUPS ..
       load printers = yes
       printing = cups
    printcap name = cups
    #use client driver = yes

       # Use LDAP for Samba user accounts and groups ..
       passdb backend = ldapsam:ldap://localhost

       # This must match init.ldif ..
       ldap suffix = dc=test,dc=fr
       # The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
       # This is done by running 'sudo smbpasswd -w'.
       ldap admin dn = cn=admin,dc=test,dc=fr

       # 4 OUs that Samba uses when creating user accounts, computer accounts, etc.
       # (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)
       ldap machine suffix = ou=Computers
       ldap user suffix = ou=Users
       ldap group suffix = ou=Groups
       ldap idmap suffix = ou=Idmap
       # Samba and LDAP server are on the same server in this example.
       ldap ssl = no

       # Scripts for Samba to use if it creates users, groups, etc.
       add user script = /usr/sbin/smbldap-useradd -m '%u'
       delete user script = /usr/sbin/smbldap-userdel %u
       add group script = /usr/sbin/smbldap-groupadd -p '%g'
       delete group script = /usr/sbin/smbldap-groupdel '%g'
       add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
       delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
       set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

       # Script that Samba users when a PC joins the domain ..
       # (when changing 'Computer Properties' on the PC)
       add machine script = /usr/sbin/smbldap-useradd -w '%u'

       # Values used when a new user is created ..
       # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
    logon drive = Z:
       logon home = \\maquette\%U
       logon path = \\maquette\profiles\%U
       logon script = logon.bat


       # This is required for Windows XP client ..
       server signing = auto
       server schannel = Auto

    # veto files
    #veto files = /*tmp*/*recycle*/*Temporary*/*Temp*/*.tmp/*RECYCLER*/*Recycle*/
    # log connexion et deconnexions
    hide files = /desktop.ini/Desktop.ini/ntuser.ini/NTUSER.*/
    root preexec = /bin/bash -c 'echo "[%T] %u connexion de %m (%I) sur %S" >> /var/log/samba/connexion.log'
    root postexec = /bin/bash -c 'echo "[%T] %u deconnexion sur %S" >> /var/log/samba/connexion.log'



[printers]
    comment = Partage imprimantes
    path = /data/samba/spool
    printable = yes
    browseable = yes
    guest ok = no
    cups options = "raw"
[print$]
        comment = Printer Drivers
        path = /data/samba/drivers
        browseable = yes
        guest ok = no
        read only = yes
        write list = root

[homes]
       comment = Repertoire Personnel
    path = /data/samba/home/%u
       valid users = %S
    guest ok = no
    writeable = yes
    create mode = 0700
    directory mode = 2700
       read only = No
       browseable = No

[netlogon]
       comment = Network Logon
       path = /data/samba/netlogon
       guest ok = no
       browseable = No

[Profiles]
       comment = Profils
       path = /data/samba/profiles
    guest ok = no
    writeable = yes
    create mode = 0700
       browseable = No

[tmp]
    comment = Repertoire fichiers temporaires
    path = /data/samba/tmp
    browseable = yes
    writeable = yes

[general]
       comment = rep general
       path = /data/samba/general
       browseable = yes

       writeable = yes

---

