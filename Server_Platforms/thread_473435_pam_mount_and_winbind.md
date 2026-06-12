---
title: "pam_mount and winbind"
date: 2007-06-14
forum: Server Platforms
---

### Post by heno77 on 2007-06-14
Hi, I am using fiesty fawn and am trying to use both pam_mount and winbind.

First I set up winbind without using pam_mount, which was successful.

_common-auth:_
auth	sufficient	pam_winbind.so
auth	required	pam_unix.so	nullok_secure	use_first_pass

_common-session:_
session	required	pam_unix.so
session	required	pam_mkhomedir.so umask=0022 skel=/etc/skel
session	optional	pam_foreground.so


I added pam_mount by changing the files

_common-auth:_
auth	require		pam_mount.so
auth	sufficient	pam_winbind.so	use_first_pass
auth	required	pam_unix.so	nullok_secure	use_first_pass

_common-session:_
session	required	pam_unix.so
session	required	pam_mkhomedir.so umask=0022 skel=/etc/skel
session	optional	pam_foreground.so
session	optional	pam_mount.so

With these changes password was denied.

_My /var/log/auth_
Jun 14 08:33:22 computer sshd[6224]: PAM pam_parse: expecting return value; [...require]
Jun 14 08:33:22 computer sshd[6224]: PAM pam_parse: expecting return value; [...require]
Jun 14 08:33:27 computer pam_winbind[6224]: user 'username' granted access
Jun 14 08:33:27 computer sshd[6224]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost  user=username
Jun 14 08:33:29 computer sshd[6224]: Failed password for username from 127.0.0.1 port 44453 ssh2
Jun 14 08:33:31 computer sshd[6224]: Connection closed by 127.0.0.1

Any idea what I have missed?

Thanks in advance!

---

### Post by teamanx on 2007-06-14
I have pam_mount and winbind working OK. Here is my config:


# /etc/pam.d/common-session - session-related modules common to all services

session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
session required pam_unix.so 
session optional pam_foreground.so 
session optional pam_mount.so 



# /etc/pam.d/common-auth - authentication settings common to all services

auth required pam_mount.so 
auth sufficient pam_unix.so use_first_pass nullok_secure
auth required pam_group.so use_first_pass
auth sufficient pam_winbind.so use_first_pass
auth required pam_deny.so

---

### Post by heno77 on 2007-06-15
Thanks teamanx! After changing my common-auth it works :)

A nice site for others, who like me. is working with pam for the first time.

[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html)

---

