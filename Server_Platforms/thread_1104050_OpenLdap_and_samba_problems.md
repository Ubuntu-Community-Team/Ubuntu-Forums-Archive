---
title: "OpenLdap and samba problems"
date: 2009-03-23
forum: Server Platforms
---

### Post by anelephant on 2009-03-23
Hi, I am having a problem setting up a openldap-samba server. I have used the ubuntu guide: [https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html) but when I try to add an xp machine it says that It can't find the machine on the server, and then prompts for a user. Then it can't find the user.

 I have tried to add the machine using ```
sudo smbldap-useradd -t 0 -w username

```

My smb.conf follows, thanks for any help you can give:
```

[global]
        workgroup = big.doom.net
        server string = doomdevice
        map to guest = Bad User
        passdb backend = ldapsam:ldap://localhost
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = wins bcast hosts
        add user script = /usr/sbin/smbldap-useradd -m "%u"
        delete user script = /usr/sbin/smbldap-userdel "%u"
        add group script = /usr/sbin/smbldap-groupadd -p "%g"
        delete group script = /usr/sbin/smbldap-groupdel "%g"
        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
        set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
        add machine script = sudo /usr/sbin/smbldap-useradd -t 0 -w "%u"
        logon script = logon.cmd
        logon drive = H:
        domain logons = Yes
        preferred master = Yes
        dns proxy = No
        wins support = Yes
        ldap admin dn = cn=admin,dc=big,dc=doom,dc=net
        ldap delete dn = Yes
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Users
        ldap machine suffix = ou=Computers
        ldap passwd sync = Yes
        ldap suffix = dc=big, dc=doom, dc=net
        ldap user suffix = ou=Users
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        security = user
        local master = yes
        domain master = yes
        preffered master = yes
        encrypt passwords = yes
        os level = 64

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /srv/samba/netlogon
        guest ok = Yes
        share modes = No

```

---

### Post by PoolSnoopy on 2009-05-05
I'm stuck at the same point. Despite minor issues with the howto like the misc.ldif <> samba.ldif error, samba and ldap seem to work together.
however adding a machine will result in a "user not found" error on the client side. more irritating is the fact that a machine account is actually created in ldap. I tried turning on logging as much as possible but can't find out what samba or the windows client is missing to successfully add a machine account.

---

### Post by lil_elvis2000 on 2009-05-13
I'm having exactly these problems! I'm on Ubuntu Jaunty server.

Below is my smb.conf:
```
[global]
	workgroup = CHAMDOM
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	passdb backend = ldapsam:ldap://localhost
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	log level = 2
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	load printers = No
	add user script = /usr/sbin/smbldap-useradd -a -m "%u"
	add group script = /usr/sbin/smbldap-groupadd -p "%g"
	delete group script = /usr/sbin/smbldap-groupdel "%g"
	add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
	delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
	set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
	add machine script = /usr/sbin/smbldap-useradd -t 0  -w "%u"
	logon drive = H:
	domain logons = Yes
	dns proxy = No
	wins server = 192.168.1.228
	ldap admin dn = cn=admin,dc=cham,dc=local
	ldap group suffix = ou=Groups
	ldap idmap suffix = ou=Idmap
	ldap machine suffix = ou=Machines
	ldap passwd sync = yes
	ldap suffix = dc=cham,dc=local
	ldap ssl = no
	ldap user suffix = ou=People
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap backend = ldap:ldap://localhost
	idmap uid = 5000-50000
	idmap gid = 5000-50000

[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	browseable = No

[netlogon]
	comment = Network Logon Service
	path = /home/samba/netlogon
	guest ok = Yes
	share modes = No

[Public]
	comment = Test area for files
	path = /mnt/lvm-pub
	force user = nobody
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes

```

I have the following in nsswitch.conf
```
passwd: files ldap
group: files ldap
shadow: files ldap

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup: nis

```

and I have performed the 
  net rpc rights grant Administrators SeMachineAccountPrivilege
  net rpc rights grant Administrators SeAddUserPrivilege

eventhough probably that wasn't needed.

When I use the XP Pro system dialog to add the machine to the domain I get the error "The User Name Could not be found".
But the entry in LDAP is made:

```
# cham04$, Machines, cham.local
dn: uid=cham04$,ou=Machines,dc=cham,dc=local
objectClass: top
objectClass: account
objectClass: posixAccount
cn: cham04$
uid: cham04$
uidNumber: 1020
gidNumber: 515
homeDirectory: /dev/null
loginShell: /bin/false
description: Computer
gecos: Computer

```

The logfile for samba is :
```
[2009/05/13 14:42:38,  2] passdb/pdb_ldap.c:init_group_from_ldap(2348)
  init_group_from_ldap: Entry found for group: 513
[2009/05/13 14:42:38,  2] passdb/pdb_ldap.c:init_group_from_ldap(2348)
  init_group_from_ldap: Entry found for group: 513
[2009/05/13 14:42:38,  2] rpc_server/srv_samr_nt.c:_samr_LookupDomain(3486)
  Returning domain sid for domain CHAMDOM -> S-1-5-21-768938858-4143042207-1543238485

```
No further messages.

I'm clueless as to what is missing. Obviously it is working for people.

---

### Post by lil_elvis2000 on 2009-05-13
Okay, I solved my problem...in the /etc/ldap.conf

I needed to add/modify these lines:

```
nss_base_passwd ou=People,dc=cham,dc=local?one
nss_base_passwd ou=Machines,dc=cham,dc=local?one
nss_base_shadow ou=People,dc=cham,dc=local?one
nss_base_group          ou=Groups,dc=cham,dc=local?one

```

Note nss_base_passwd is in twice. once for user password and again for machines.

Wheee!

---

### Post by frankacreano on 2009-08-11
Hi,

     I'd solved my problem modifying the folowing line at /etc/samba/smb.conf: add machine script = /usr/sbin/smbldap-useradd -w "%u" to  add machine script = /usr/sbin/smbldap-useradd -w %u

That's right, I just remove the quotes " ".

My machines logon in to the domain now.

Frank Douglas
Manaus - Amazonas - Brasil

---

### Post by rdratlos on 2011-07-22
> **lil_elvis2000 said:**
> I'm having exactly these problems! I'm on Ubuntu Jaunty server.

and I have performed the 
  net rpc rights grant Administrators SeMachineAccountPrivilege
  net rpc rights grant Administrators SeAddUserPrivilege

eventhough probably that wasn't needed.



I had the same problem when joining a Windows 7 machine to a Samba domain (<mydomain>). I tried to join by authenticating as a user that belongs to the built-in 'Administrators' group that has the follwoing privilegies:
```
BUILTIN\Administrators
SeMachineAccountPrivilege
SeTakeOwnershipPrivilege
SeBackupPrivilege
SeRestorePrivilege
SeRemoteShutdownPrivilege
SePrintOperatorPrivilege
SeAddUsersPrivilege
SeDiskOperatorPrivilege

```But it failed again with Samba error 'samr_CreateUser2 <user> can add this account:  False
After granting this user the required privileges, it worked fine:
> net rpc rights grant '<mydomain>\<user>' SeMachineAccountPrivilege
net rpc rights grant '<mydomain>\<user>' SeAddUsersPrivilegeIf it still fails, please take also bug [https://bugs.launchpad.net/bugs/814898](https://bugs.launchpad.net/bugs/814898) into account.

---

