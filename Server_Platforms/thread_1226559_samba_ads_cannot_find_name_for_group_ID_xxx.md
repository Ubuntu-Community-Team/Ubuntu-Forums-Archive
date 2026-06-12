---
title: "samba ads cannot find name for group ID xxx"
date: 2009-07-29
forum: Server Platforms
---

### Post by TonyHardie on 2009-07-29
Hi i am using jaunty server, x64 (running samba 3.3.2)
I have gone through the various articles on setting up samba/winbind and joined the domain i currently have an issue where SOME (not all) users get messages like 
id: cannot find name for group ID 100073 and various other ID's.
since this is groups through AD it has nothing to do with /etc/groups permissions.
 
my troubleshooting has lead me to the following observations.
if i type groups <username> all the groupnames resolve for some users.
if i type groups <certain users> some of the groupnames resolve and some do not.
 
it's almost as if they belong to some wierd group that is non standard?
our domain structure is complicated where we have a parent forset (A) of which most users are in 2 organizations B and C which have mutual trusts with A (which is where the server is joined to).
 
so everything it working great accept for this last issue for not resolving all the groupIDs.
 
my samba config:
[global]
workgroup = YYYY
realm = XXX.XXX
server string = %h server (Samba, Ubuntu)
security = ADS
auth methods = winbind, quest, sam
map to guest = Bad User
obey pam restrictions = Yes
passdb backend = tdbsam
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes
restrict anonymous = 2
client NTLMv2 auth = Yes
use kerberos keytab = Yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
socket options = IPTOS_LOWDELAY SO_KEEPALIVE TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = No
dns proxy = No
usershare allow guests = Yes
panic action = /usr/share/samba/panic-action %d
idmap uid = 100001-300000
idmap gid = 100001-300000
template shell = /bin/bash
winbind cache time = 172800
winbind enum users = Yes
winbind enum groups = Yes
winbind refresh tickets = Yes
winbind offline logon = Yes
 
any ideas?

---

