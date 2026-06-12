---
title: "forward mail from one server to the main server"
date: 2008-06-15
forum: Server Platforms
---

### Post by dmm1983 on 2008-06-15
Need to know how to forward roots mail to another server
anybody know how

i'm using hardy
postfix

Help will be appericated
Thank

---

### Post by windependence on 2008-06-16
Add "root: username_to_forward_to" line to your '/etc/aliases' file.

You will have to run /usr/bin/newaliases to restart the service.

-Tim

---

### Post by dmm1983 on 2008-06-18
still may have problem see if resolved itself
my mail forwards it to be the root user on the mail server that its suppose to go to.
But my mail doesn't forward to how to fix and i did it the same way as explained in reply

---

### Post by dmm1983 on 2008-06-19
finally solved
by using internet and smarthost option

---

### Post by hyper_ch on 2008-06-19
if you use procmail for local filtering you could directly forward root mails to another server...

---

