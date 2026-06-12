---
title: "admin managing"
date: 2013-02-03
forum: Security
---

### Post by ciscoboy on 2013-02-03
I'm not sure if I'm in the right spot for this but here we go...
I was wondering if hypothetically you would have 2 accounts with admin clearance and both with different passwords. Hypothetically, could both accounts do stuff like installing programs 

Thanks

ciscoboy

---

### Post by Cheesemill on 2013-02-03
Yes.

Any account that belongs in the administrator group has full access and control over the OS.

---

### Post by cariboo on 2013-02-03
In current versions, they also have to be a member of the sudo group.

---

### Post by bodhi.zazen on 2013-02-05
> **ciscoboy said:**
> I'm not sure if I'm in the right spot for this but here we go...
I was wondering if hypothetically you would have 2 accounts with admin clearance and both with different passwords. Hypothetically, could both accounts do stuff like installing programs 

Thanks

ciscoboy

Actually you can configure the behavior by configuring sudo.

If you add both users to the sudo group they will have full privileges.

See man sudoers if you wish to change what users can do:

[http://www.sudo.ws/sudoers.man.html](http://www.sudo.ws/sudoers.man.html)

---

