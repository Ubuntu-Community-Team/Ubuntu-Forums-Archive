---
title: "About adding postfix user to mail group"
date: 2008-06-10
forum: Server Platforms
---

### Post by satimis on 2008-06-10
Hi folks,


Ubuntu 6.06 server drake amd64



$ id postfix```

uid=107(postfix) gid=111(postfix) groups=111(postfix)

```


I need to add the postfix user to the mail group



Whether to run;

$ sudo groupadd mail -g 1001
$ useradd postfix -u 1001 -g 1001

Shall I use number 1001?  OR another number?


However on /etc/group I found following entries;

mail:x:8:dovecot
dovecot:x:113:


I don't have dovecot-* running on this server.  Can I remove them manually?  


Please advise.  TIA


B.R.
satimis

---

