---
title: "Samba 4.1.23 Logon Scripts"
date: 2016-11-25
forum: Server Platforms
---

### Post by mircea.troaca on 2016-11-25
Hello,


I used Ubuntu in order to create a domain controller. It works very good, I configured properly Samba and Kerberos, I can join other PCs using Windows to my ubuntu domain controller, everything works perfectly. The only problem is that I don't really get it how I am supposed to set the logon scripts for windows to run on these PCs with Windows. I tried to add .bat files to /usr/local/samba/var/locks/sysvol/domain.controller.name.com/scripts, but got no succes..
I have found something on the Internet saying that i should add the following lines to smb.conf.. This is my actual smb.conf

```

# Global parameters

[global]
        workgroup = MIRCEA-DOMAIN
        realm = mircea.xxx.xxx.com
        netbios name = DC2
        server role = active directory domain controller
        dns forwarder = xxx.xxx.xxx.xxx
        add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody %u
        logon home =
        logon path = /usr/local/samba/profiles/%U
        logon script = start.bat


[netlogon]
        comment = Network Logon Service
        path = /usr/local/samba/lib/netlogon
        admin users = root
        guest ok = Yes
        browseable = No
#       logon script = start.bat


[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No


[users]
        directory_mode: parameter = 0700
        read only = no
        path = /Users
        csc policy = documents


[Profiles]
        comment = User Profiles
        path = /usr/local/samba/profiles
        readonly = No
        profile acls = Yes

```

Usually I struggle myself in searching on internet.. but this time I got no success.. Seems like people don't really tend to use a linux server as domain controller for windows.. Thank you in advice!

EDIT:
The "start.bat" script is located in /usr/local/samba/lib/netlogon and the script changes the computer time and date to 00:00:00 / 01.01.2006.. I tried to log in to a windows machine with a fresh-created account to check if the script is working, but unsuccessfully.. I just want the script to run on every account everytime they log in.. I tried to open manually the script and it's working properly, the date changes..

---

### Post by volkswagner on 2016-11-26
I'm no expert, but I'm curious if you can make it work by using RSAT
and adding the file name to logon field like below?

[IMG]https://www.petri.com/images/logon_script_dsa_2.gif[/IMG]

---

### Post by mircea.troaca on 2016-11-26
I can't believe, that works like a charm!! Thank you, mate. (it is perfect because right now I can work at the scripts and see their behaviour)

But still, the problem persist because the I am not intending to do that for every single account from my domain. Does anybody have an idea how I am supposed to do that for everyone, maybe via terminal? Thank you in advice!

---

