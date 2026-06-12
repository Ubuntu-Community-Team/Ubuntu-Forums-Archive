---
title: "ldap+samba seems to be up &amp; running. No logging from windows possible"
date: 2011-05-17
forum: Server Platforms
---

### Post by asaak on 2011-05-17
Hi everybody!

I followed the howto memoria.pdf in [http://www.riunet.upv.es/handle/10251/10027](http://www.riunet.upv.es/handle/10251/10027) which seems pretty good for my purpose. 

Everything seemed to go find and I got the same results as in the howto. 

However, when I try to connect form windows to my ubuntu server, it seems to find the domain but then on the user/password logging it says " error trying to connect to "yourdomain". access denied"

I am kind of desperate because I've tried a lot of different things.
I could attach you some conf files if you want to know more in detail.

This is my smb.conf file


```

[global]

#Domain name
workgroup=dibrapel

#Server name as seen by windows PCs
netbios name = samba-dibrapel

#Be a PDC

domain logons = yes
domain master = yes
#Be a Wins Server
wins support = true

obey pam restrictions = yes
dns proxy = No
os level = 35
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
pam password change = yes

#Allows users on WinXP PCs to change their passwords when they press Ctrl-Alt-Del
unix password sync = no
ldap passwd sync = yes

#Printing from PCs will go via CUPS
load printers = yes
printing = cups
printcap name = cups

#Use LDAP for Samba users accounts and groups
passdb backend = ldapsam:ldap://localhost

#This must match init.ldif...
ldap suffix = dc=dibrapel,dc=local
#The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
#This is done by running 'sudo smbpasswd -w'...
ldap admin dn = cn=admin,dc=dibrapel,dc=local

#4 Ous that samba uses when creating user accounts, computer accounts, etc
ldap user suffix = ou=Users
ldap group suffix = ou=Groups
ldap idmap suffix = ou=ldmap

#Samba and LDAP server are on the same server in this example
ldap ssl = no

#Scripts for samba to use if it creates users,groups,etc.

add user script = /usr/sbin/smbldap-useradd -m '%u'
delete user script = /usr/sbin/smbldap-userdel %u
add group script = /usr/sbin/smbldap-groupadd -p '%g'
delete user script = /usr/sbin/smbldap-groupdel '%g' 
add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g' 
delete user from group script = /usr/sbin/smbldap -x '%u' '%g'
set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

#Script that Samba users when a PC joint a domain
add machine script = /usr/sbin/smbldap-useradd -w '%u'

#Values used when a new user is created
logon drive =
logon home =
logon path =
logon script = allusers.bat

#This is required for windows XP clients...
server signing = auto
server schannel = auto

[homes]

comment = Home Directories
valid users = %S
read only = no
browseable = no

[netlogon]

comment = Network Logon Service
path = /var/lib/samba/netlogon
admin users = root
guest ok = yes
browseable = no
logon script = allusers.bat

[Profiles]

comment = Roaming profile share
path = /var/lib/samba/profiles
read only = no
profile acls = yes
browseable = no

[printers]

comment = All Printers
path = /var/spool/samba
use client driver = yes
create mask = 0600
guest ok = yes
printable = yes
browseable = no
public = yes
writable = yes
admin users = root
write list = root

[print$]

comment = Printer Driver Share
path = /var/lib/samba/printers
write list = root
create mask = 0664
directory mask = 0775
admin users = root

[shared]

writeable = yes
path = /var/lib/samba/shared
public = yes
browseable = yes

[archive]

path = /exports/archive
browseable = yes
create mask = 755
directory mask = 755
read only = no


```

and this is an example user I want to be able to log to the domain:


```

toni@Servidor:~$ sudo smbldap-usershow prova
dn: uid=prova,ou=Users,dc=dibrapel,dc=local
objectClass: sambaSamAccount,posixAccount,inetOrgPerson,organizationalPerson,person
sambaHomeDrive: U:
sambaDomainName: dibrapel
sambaAcctFlags: [XU         ]
displayName: prova
sambaPrimaryGroupSID: S-1-5-21-2293197003-1186991814-1703358567-513
sambaSID: S-1-5-21-2293197003-1186991814-1703358567-512
homeDirectory: /home/prova
loginShell: /bin/bash
uid: prova
cn: prova prova
uidNumber: 10000
gidNumber: 548
sn: prova
givenName: prova
sambaNTPassword: 9CADAFF03AE475011E5EA6E4B7C4E597
sambaPwdLastSet: 1305628881
userPassword: {SSHA}toMwrQlqy5yTzLzHz64yYfzC44uEyYsD

```


Any ideas? please help me because I feel I am really closed to the end but I must be doing something wrong...

Thank you very much!

---

### Post by asaak on 2011-05-17
any suggestion?? please, I really need it.

Thanks!

---

### Post by brettg on 2011-05-17
Try this guide;

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

---

### Post by asaak on 2011-05-18
I followed a tutorial exactly like this one but still when I try to log from a win xp computer I get " access denied"....Apparently winxp sees the domain but when logging with user/passwd it says "access denied.."

Any ideas please?

---

### Post by brettg on 2011-05-18
You followed a tutorial exactly like . . . which one?

I assure you that I tried a tonne that gave me "access denied" errors.

The one I linked to is the only one that worked.

Check the comments;

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

---

### Post by asaak on 2011-05-18
First of all thank you for your help! I did follow the tutorial you suggested and it worked.

I was able to set-up the domain in a win xp machine and in a win 7. During the set up, I chose the option "don't import users of the domain...then I restarted and the option of the domain was available. " I press ctr+alt+supr and I try to log with a user of that domain. However, when I press enter to log in I get "System can't start session in this moment because the domain <domain> is not avialable ".

If I log in as a local user, it appears that I am joined to the domain but I can't log in with a user of the domain.

Any ideas?

Thanks again!

---

### Post by asaak on 2011-05-18
BTW I checked the comments and I found people with the same problem I am having yet they haven't had any solution.

---

