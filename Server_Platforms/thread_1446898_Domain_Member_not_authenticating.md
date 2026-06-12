---
title: "Domain Member not authenticating???"
date: 2010-04-04
forum: Server Platforms
---

### Post by robertomason on 2010-04-04
I don't know if the problem is the way I create my shares on the Domain member, but here is the way I've configured my systems. My systems are home based, and though the topology may be all wrong, it's set up this way only for test purposes. I love to get things up and running.

I've already had a Domain Member running under Samba 3.02xx (Centos), but I'm having problems under Ubuntu and Samba 3.40

1. Server call Citadel is a VMware Server. I've got 3 virutal machines on this Server, 2 Ubunt 9.10 servers, and 1 Windows XP pro. One of my virtual servers is call Winserver, a Samba PDC server using TDBSAM as it's backend. Configured and working well. I have a share that I can access.
Here is samba.conf file, along with share. Winbind is not running here.
# Samba config file created using SWAT
# from UNKNOWN (0.0.0.0)
# Date: 2010/04/01 14:03:29

[global]
    workgroup = MEPHISTOPHELES
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    add user script = /usr/sbin/useradd -m %u
    delete user script = /usr/sbin/userdel -r %u
    add group script = /usr/sbin/groupadd -r %g
    delete group script = /usr/sbin/groupdel %g
    add user to group script = /usr/bin/gpasswd -a %u %g
    delete user from group script = /usr/sbin/userdel -r %u
    set primary group script = /usr/sbin/usermod -g '%g' '%u'
    add machine script = /usr/sbin/useradd -c Machine -d /var/lib/nobody -s /bin/false '%u'
    shutdown script = /sbin/shutdown
    abort shutdown script = /sbin/shutdown -c
    logon path = 
    domain logons = Yes
    dns proxy = No
    wins support = Yes
    preload = global printers print$
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    winbind enum users = Yes
    winbind enum groups = Yes
    winbind use default domain = Yes
    winbind rpc only = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Linux Doc]
    path = /usr/share/doc
    username = @"MEPHISTOPHELES\domain user",@"MEPHISTOPHELES\domain admin"
    read only = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No



2. Citadel is my domain member: Here is it's smb.conf file

# Samba config file created using SWAT
# from UNKNOWN (0.0.0.0)
# Date: 2010/04/01 14:07:09

[global]
    workgroup = MEPHISTOPHELES
    server string = %h server (Samba, Ubuntu)
    security = DOMAIN
    map to guest = Bad User
    obey pam restrictions = Yes
    password server = MEPHISTOPHELES.rmasonfamily.info
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins server = 192.168.1.5
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    winbind enum users = Yes
    winbind enum groups = Yes
    winbind rpc only = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[movie]
    writeable = yes
    admin users = MEPHISTOPHELES\roberto
    write list = MEPHISTOPHELES\roberto,@"MEPHISTOPHELES\domain admins"
    path = /storage/Movie
    force group = root
    force user = root
    valid users = MEPHISTOPHELES\roberto,@"MEPHISTOPHELES\domain admins"

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No
3. On Citadel, domain member
    a. getent passwd (works ok)[INDENT]            .
           .
           .
         pulse:116:124pulseAudio daemon,,,:/var/run/pulse:/bin/false
         gdm:117:126:Gnome Display Manager:/var/lib/gdm:/bin/false
         MEPHISTOPHELES\nobody:*:10000:10007:nobody:/home/MEPHISTOPHELES/nobody:/bin/false
        MEPHISTOPHELES\roberto:*:10001:10007:Roberto Mason,,,:/home/MEPHISTOPHELES/roberto:/bin/false
MEPHISTOPHELES\root:*:10002:10007:root:/home/MEPHISTOPHELES/root:/bin/false
[/INDENT]r
     b. getent group (work ok)[INDENT]            .
            .
            .
          pulse:124:
          pulse-access:125:
          gdm:126:
          MEPHISTOPHELES\print operators:10009:
          MEPHISTOPHELES\domain users:10010:
          MEPHISTOPHELES\system operators:10011:
          MEPHISTOPHELES\replicators:10012:
          MEPHISTOPHELES\domain guests:10013:
          MEPHISTOPHELES\backup operators:10014:
          MEPHISTOPHELES\domain admins:10006:MEPHISTOPHELES\roberto,MEPHISTOPHELES\root
          MEPHISTOPHELES\administrators:10015:

some editing was done here, since when I pasted, I got some smileys, I just simply removed them. the lines are missing some info, but I don't think they are relevant.

[/INDENT]c. I've already joined the domain with net rpc join -U root.

On my Windows XP, I'm a domain member, able to access my WinserverServer share "Linux Doc", but when I try to access my domain member, it keeps asking me to login.  I don't know what I'm doing wrong. I re pasting my share here for your convenience 

[movie]
    writeable = yes
    admin users = MEPHISTOPHELES\roberto
    write list = MEPHISTOPHELES\roberto,@"MEPHISTOPHELES\domain admins"
    path = /storage/Movie
    force group = root
    force user = root
    valid users = MEPHISTOPHELES\roberto,@"MEPHISTOPHELES\domain admins"

here are the ownership and right permissions to Movie directory

4 drwxr-xr-x  4 root root 4096 2010-03-30 21:44 Movie

just noticed something,

when I do a "wbinfo -a roberto%thepassword

I get the following:
root@citadel:~# wbinfo -a roberto%thepassword
plaintext password authentication failed
Could not authenticate user roberto%thepassword with plaintext password
challenge/response password authentication failed
error code was NT_STATUS_INVALID_PARAMETER (0xc000000d)
error messsage was: Invalid parameter
Could not authenticate user roberto with challenge/response

---

### Post by robertomason on 2010-04-05
Another thing I noticed, When I try to access the share and it asks me to logon, if I enter MEPHISTOPHELES\roberto and my password, it let me through. Hope it helps

---

### Post by alvilsb on 2010-04-28
Hey,
Just try adding the following line to your [GLOBAL] section of Samba:
map untrusted to domain = yes

And restart Samba afterwards.
This is a new "nice" feature in Samba 3.4.0.

---

