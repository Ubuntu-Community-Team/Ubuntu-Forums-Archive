---
title: "suid files"
date: 2006-07-11
forum: Server Platforms
---

### Post by RShadow on 2006-07-11
Can anbody see any reason why any of the following would need the suid bit set? (in a server enviornment)

/bin/su
/bin/check-foreground-console
/usr/bin/arping
/usr/bin/traceroute6
/usr/bin/chfn
/usr/bin/chsh
/usr/bin/gpasswd
/usr/bin/mtr
/usr/bin/newgrp
/usr/bin/passwd
/usr/bin/sudo
/usr/bin/X
/usr/sbin/suexec
/lib/dhcp3-client/call-dhclient-script
/lib/uncompress.o
/usr/lib/eject/dmcrypt-get-device
/usr/lib/openssh/ssh-keysign
/usr/lib/courier/authlib/changepwd/authdaemon.passwd
/usr/lib/pt_chown
/usr/lib/apache2/suexec2

The only ones that make sense is 
/usr/sbin/sudo and /bin/su

---

### Post by LordHunter317 on 2006-07-11
Actually, the only thing I see on the list that could possibly not need to be suid is /lib/uncompress.o.  And I suspect it probably does need to be, though I can't give a reason immediately.

Look up the documentation for those programs and it should be obvious why they're SUID root.

---

### Post by lamego on 2006-07-11
There are some of them which are prety obvious, like /usr/bin/passwd.
When a user needs to change its own password the /etc/password and /etc/shadow files need to be changed, only root can change them so the command needs to be suid.

---

