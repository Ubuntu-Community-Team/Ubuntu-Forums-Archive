---
title: "Samba config issues with winbindd"
date: 2007-01-12
forum: Server Platforms
---

### Post by BillGod on 2007-01-12
I have this posted in general but figured this would be a better place.

I am getting an error of

unable to initalize domain list (yes misspelling is built in

when trying to start winbindd. I have hunted around the net and a couple people have had this problem but none have an answer.

my windows 2003 server AD domain is MYDOMAIN.LOCAL. server address is 192.168.15.215 Ubuntu box is 192.168.15.102

My smb.conf looks like this.


[global]
workgroup = MYDOMAIN.LOCAL
realm = MYDOMAIN.LOCAL
server string = %h server (Samba, Ubuntu)
interfaces = 192.168.15.102
security = DOMAIN
auth methods = guest, sam, winbind
encrypt passwords = No
obey pam restrictions = Yes
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
printcap name = /etc/printcap
dns proxy = No
wins server = 192.168.15.215
panic action = /usr/share/samba/panic-action %d
invalid users = root
hosts allow = 192.168.15.
idmap uid = 10000-40000
idmap gid = 10000-40000
template homedir = /dev/null
template shell = /bin/false
; template primary group = "Domain Users"
winbind use default domain = yes
winbind enum users = yes
winbind enum groups = yes
winbind cache time = 300
# no is default
winbind nested groups = No

[printers]
comment = All Printers
path = /tmp
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

---

### Post by GrammatonCleric on 2007-02-09
Did you join your system to the domain? 

```
 smbpasswd -j <domain> -r <PDC> -U <NT administrator> 
```-GC

---

### Post by Brazen on 2007-02-09
have you installed kerberos:```
sudo apt-get &#8211;y install heimdal-clients libpam-krb5 
```
and joined a Windows domain:```
sudo net ads join -U Administrator@MYDOMAIN.LOCAL
```
and added the winbind entries to /etc/nsswitch.conf and /etc/pam.d/samba ?

---

### Post by localzuk on 2007-02-10
I would advise you to take a look at [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

This should explain how to do the entire process of adding your ubuntu box to a windows AD.

---

