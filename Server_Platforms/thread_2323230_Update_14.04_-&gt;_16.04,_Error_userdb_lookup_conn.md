---
title: "Update 14.04 -&gt; 16.04, Error: userdb lookup: connect(/var/run/dovecot/auth-userdb)"
date: 2016-05-03
forum: Server Platforms
---

### Post by christian99 on 2016-05-03
Hello,

i update my mail-server form 14.04 to 16.04 and now i got the following error message:

```
May 4 00:54:42 server dovecot: lda(mail@christian-burmeister.de): Error: userdb lookup: connect(/var/run/dovecot/auth-userdb) failed: Permission denied (euid=5000(vmail) egid=5000(vmail) UNIX perms appear ok (ACL/MAC wrong?), dir owned by 0:0 mode=0755)
May 4 00:54:42 server dovecot: lda: Fatal: Internal error occurred. Refer to server log for more information.
```

```
May 4 00:21:20 server kernel: [ 332.985999] audit: type=1400 audit(1462314080.436:239): apparmor="ALLOWED" operation="connect" info="Failed name lookup - disconnected path" error=-13 profile="/usr/lib/dovecot/dovecot-lda" name="run/dovecot/auth-userdb" pid=5352 comm="deliver" requested_mask="wr" denied_mask="wr" fsuid=5000 ouid=5000
```

The File "/var/run/dovecot/auth-userdb" ist accessible for user vmail.

```
root@server:/etc/dovecot# ls -aln /var/run/dovecot/auth-userdb
srw-rw---- 1 5000 5000 0 May  4 00:36 /var/run/dovecot/auth-userdb

root@server:/etc/dovecot# ls -al /var/run/dovecot/auth-userdb
srw-rw---- 1 vmail vmail 0 May  4 00:36 /var/run/dovecot/auth-userdb


```

And the settings in "10-master.conf"  are correct

```
root@server:/etc/dovecot# cat /etc/dovecot/conf.d/10-master.conf 
....
  unix_listener auth-userdb {
    mode = 0660
    user = vmail
    group = vmail
  }
....

```

Can anyone explain me why I get the error message?

---

### Post by christian99 on 2016-05-04
I solved the problem.


/etc/apparmor.d/usr.lib.dovecot.dovecot-lda

add the line "/var/run/dovecot/* rw"

---

