---
title: "users and groups"
date: 2009-01-14
forum: Security
---

### Post by nikhilneela on 2009-01-14
Hi everyone!!!!I recently migrated to ubuntu from windows...and i find thousands of advantages with ubuntu....thanks for ubuntu developers and thanks to all those who are helping me how to tackle problems in ubuntu.....i really mean it.
            now i would like to know how can i create users and groups in ubuntu and give them stringent permissions.....please help me out....and thanks in advance

---

### Post by albinootje on 2009-01-14
> **nikhilneela said:**
> Hi everyone!!!!I recently migrated to ubuntu from windows...and i find thousands of advantages with ubuntu....thanks for ubuntu developers and thanks to all those who are helping me how to tackle problems in ubuntu.....i really mean it.

Welcome to Ubuntu :)
> 
            now i would like to know how can i create users and groups in ubuntu and give them stringent permissions.....please help me out....and thanks in advance

Check -> System -> Administration -> Users and Groups

See also :
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://help.ubuntu.com](http://help.ubuntu.com)
[http://wiki.ubuntu.com](http://wiki.ubuntu.com)

---

### Post by bodhi.zazen on 2009-01-15
See also :

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by lensman3 on 2009-01-15
The previous reference is good, but also become familiar with:

vigr - edit the group file
vipw - edit the password file
groups - show what groups a user belongs to
chown -
chgrp -
chmod -
sg - run command in another group
newgrp - change to a new group (like su)

---

### Post by pdtpatrick on 2009-01-17
hmm i gotta say i didnt know about the vipw vigr and sg .. nice lensman3 ... thanks :)

---

### Post by albinootje on 2009-01-17
> **pdtpatrick said:**
> hmm i gotta say i didnt know about the vipw vigr and sg .. nice lensman3 ... thanks :)

+1 Thanks lensman3.

However, I find 
```

vipw -s   (for the shadow file)
vipw -g   (for the group file)

```
easier to remember, esp. since I use those since years.

---

