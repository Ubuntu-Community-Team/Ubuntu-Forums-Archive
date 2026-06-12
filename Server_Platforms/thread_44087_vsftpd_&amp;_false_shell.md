---
title: "vsftpd &amp; false shell"
date: 2005-06-24
forum: Server Platforms
---

### Post by [pl]ice on 2005-06-24
1)hi, i'm learing how to setup vsftpd, 
  for accounts i set them up with adduser, then edit /etc/passwd and change shell path ( i know i can do it with one line only with adduser)  for /bin/false
, so that a user won't be able to login through ssh etc. 
in vsftpd.con i put:  check_shell=no    
but this doesn't seem to work; still checks the file /etc/shells so i have added /bin/false to that shells list, and it works.
    is there another way for this to block user using my localhost (as he would have /bin/bash etc) ?  and by adding /bin/false would it affect something else?

2) for limiting user download, i can only see 2 commands from man. anon limit and localhost limit; for the localhost limit upload, would that apply to the users connecting externally, or 'localhost limit' refers to the /etc/passwd file?
thanks.

---

### Post by LordHunter317 on 2005-06-24
You can't use /bin/false as the fake shell as PAM will abort when it gets the return code.

Use /bin/true instead.  It should work and they won't be able to login via shell.

Never edit /etc/passwd directly too, btw.  One mistake will lock you out of your system.

---

