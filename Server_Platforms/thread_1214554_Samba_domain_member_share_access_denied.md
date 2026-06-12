---
title: "Samba domain member: share access denied"
date: 2009-07-16
forum: Server Platforms
---

### Post by nutnut on 2009-07-16
Hi,

I have a Samba PDC working for the domain "VL". Now I wish to add a second server "serveur3", member to this domain.

Serveur3 has been bound to the domain, appears in browse lists and shares are visible.
Winbind seem ok because command like: wbinfo -u, getent passwd USERNAME, work just fine.

The problem is that any share I access gives a permission denied.

The share config is
[share3]
        comment = Server3 test
        writeable = yes
        path = /data/share3
        writeable = yes
        printable = no
        create mask = 0660
        directory mask = 0775
        valid users = VL\\test1, %S, @vluser
        write list = @vluser
         guest ok = yes

Under valid users one can see I've tried various forms to allow the user "test1" to gain access. test1 is also part of the vluser unix group.

One issue that strikes me that where as 'wbinfo -u' returns domain users on servuer3, the groups don't seem to be visible:
root@serveur3:/var/log/samba# wbinfo -g
BUILTIN\administrators
BUILTIN\users

in /etc/nsswitch.conf, its looks OK:
group:          compat winbind

Also "net groupmap list" does not shows only Builtin groups.

Any suggestions or tips please?

---

### Post by nutnut on 2009-07-17
wbinfo -g is now fine (no change made), but the groupmap is not yet visible, and access to the share is still denied.

wbinfo -g
BUILTIN\administrators
BUILTIN\users
VL\domain admins
VL\domain guests
VL\domain users

net --myworkgroup=VL groupmap list
Administrators (S-1-5-32-544) -> BUILTIN\administrators
Users (S-1-5-32-545) -> BUILTIN\users

The following is a log extract of key lines, I hope someone can help..
  check_ntlm_password:  Checking password for unmapped user [VL]\[test1]@[PC-06] with the new passw
ord interface
  check_ntlm_password:  authentication for user [test1] -> [test1] -> [VL\test1] succeeded
  fetch gid from cache 10002 -> S-1-5-32-545
  UNIX uid 10005 is UNIX user VL\test1, and will be vuid 101
  se_access_check: user sid is S-1-5-21-2635954911-775439175-2897430547-3004
  se_access_check: also S-1-5-21-2635954911-775439175-2897430547-513
 (513 is the group coresponding to Domain Users mapped to 'vluser')
   pc-06 (192.168.1.138) connect to service IPC$ initially as user VL\test1 (uid=10005, gid=10000) (
pid 10205)
  pc-06 (192.168.1.138) connect to service share3 initially as user VL\test1 (uid=10005, gid=10000)
 (pid 10205)
 error packet at smbd/process.c(992) cmd=50 (SMBtrans2) NT_STATUS_NETWORK_ACCESS_DENIED
  check_ntlm_password:  Checking password for unmapped user []\[]@[PC-06] with the new password int
erface
  error packet at smbd/process.c(992) cmd=50 (SMBtrans2) NT_STATUS_NETWORK_ACCESS_DENIED

---

### Post by nutnut on 2009-07-17
SOLVED: I got to the bottom of this. The problem was the user/group access on the unix level.

The files and directories must be assigned to groups and users in the domain format, for example:  

chgrp -R 'VL\domain users' .
chown 'VL\sean' README.txt

VL is the domain name.

My share definition is now very simple:
[share3]
        comment = Server3 test
        writeable = yes
        path = /data/share3
        writeable = yes
        printable = no
        create mask = 0660
        directory mask = 0775

I was unable to find a format that worked for the 'valid users' to I left that out. examples I tried were:
   valid users = @'VL\domain users'
   valid users = @VL\domain users
   valid users = @'VL\\domain users'

---

