---
title: "Problem changing password for local users"
date: 2010-05-07
forum: Server Platforms
---

### Post by LebLinux on 2010-05-07
Dears,

I am on ubuntu server and its joined to an W3k Domain thru winbind/samba. However everything works fine and Windows and Local users can login to the machine without any problem. However when I wanted to create a local user X and change his password I couldn't. It created the local user X but I could not change the password. Here are the outputs:

Pam configs:

Common-account:
account sufficient pam_winbind.so
account required pam_unix.so
----------------------------------------------
Common-auth:
auth sufficient pam_winbind.so krb5_auth krb5_ccache_type=FILE
auth sufficient pam_unix.so nullock_secure use_first_pass
auth required pam_deny.so
--------------------------------------------------
Common-password:
password [success=1 default=ignore] pam_unix.so obscure use_authtok try_first_pass sha512
----------------------------------------------------
Common-session:
session required pam_unix.so
session required pam_mkhomedir.so skel=/etc/skel/ umask=0066
session sufficient pam_winbind.so
-----------------------------------------------------

The output from /var/log/auth.log when I try to change the password for local username saad.
local means the username on the machine itself.

Passwd[1779]: PAM bad jump in stack
May 6 17:29:59 ubuntu-linux sudo: pam_unix(sudo:auth): unrecognized option [nullock_secure]
May 6 17:29:59 ubuntu-linux sudo: pam_unix(sudo:auth): auth could not identify password for [saad]
---------------------------------------------------------
Output of the NSSWITH.conf

passwd: compat winbind
group: compat winbind
shadow: compat winbind

hosts: files dns
networks: files dns

protocols: db files
services: db files
ethers: db files
rpc: db files

netgroup: nis
-------------------------------------------------
Output of Smb.conf

[GLOBAL]
workgroup = Domain
netbios name = Hostname
realm = Full Domain name
password server = Domain server name
enable privileges = Yes
allow trusted domains = Yes
time server = Yes
obey pam restrictions = yes
winbind refresh tickets = yes
client ntlmv2 auth = yes
winbind use default domain = yes
security = ADS
encrypt passwords = yes
passdb backend = tdbsam
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = no

map to guest = bad user

idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash
winbind enum groups = yes
winbind enum users = yes
usershare allow guests = yes
================================================== =======

main problem is:

passwd saad
Changing password for saad.
(current) UNIX password:
passwd: Permission denied
passwd: password unchanged
saad@ubuntu-server:~$
----------OR--------------
root@ubuntu-server:~# passwd saad
passwd: Permission denied
passwd: password unchanged
root@ubuntu-server:~#
---------------------------------
cat /etc/passwd
saad:1002:1002:,,,:/home/saad:/bin/bash

--------------------------------

I can login fine without any problem.
====================================

Regards,
Saad


Solved the problem by commenting

Common-password:
password [success=1 default=ignore] pam_unix.so obscure use_authtok try_first_pass sha512

and Uncommenting:
password required pam_unix.so nullok obscure min=4 max=50 md5
====================================

---

