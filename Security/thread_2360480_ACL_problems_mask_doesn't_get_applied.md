---
title: "ACL problems: mask doesn't get applied"
date: 2017-05-05
forum: Security
---

### Post by lars-daniel on 2017-05-05
Hi there.

I've got problems with ACL. User "root" has created /tmp/test.txt and is copying it to a shared folder /opt/shared. The files in this directory should be writeable by all users in group "shared", but it doesn't work. Using "cp /tmp/test.txt /opt/shared/", the ACL mask doesn't get applied: the group has no right to write, only the owner (aka ROOT) has. Anyone with an idea?

That's my setup:
```
sudo addgroup         shared
sudo adduser root     shared
sudo adduser larsdaniel shared
sg shared


share='/opt/shared'
sudo mkdir         "${share}"
sudo chgrp shared  "${share}"
sudo chmod g+rwsx  "${share}"
sudo chmod o-rwx   "${share}"
sudo setfacl -d -m u::rwx,g::rwx,o::--- "${share}"
```

---

