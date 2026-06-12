---
title: "Confirmation required before editing sudoers"
date: 2012-05-24
forum: Security
---

### Post by satish_j on 2012-05-24
I need to enable shutdown and reboot from command _without the need of entering sudo password._
I know i have to edit /etc/sudoers file and add custom entry to it.
My UserID is already added to admin group.There is this entry for admin group(at the very end of file) already in sudoers file which allows ALL access to admin group.
So,my question is:if i enter following command AFTER the existing line for %admin
```

%admin ALL=NOPASSWD: /sbin/shutdown,/sbin/reboot

```
will it affect the original rule of %admin?
My requirement is very clear:sudo pwd to be entered for all sudo commands except shutdown and reboot..
Waiting for expert's inputs..

---

### Post by sikander3786 on 2012-05-24
My blog-mate wrote something on this at the very bottom of this post:

[http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html](http://www.tuxgarage.com/2011/09/shutdown-timer-tool-for-linux.html)

And yeah, it would only exclude the 'admin' group, or even if you want to, a specific user, from entering password for shutdown and reboot. Everything else should still need the 'sudo' password to be entered.

---

### Post by satish_j on 2012-05-24
thanks for the confirmation,will proceed with it today itself..

---

### Post by satish_j on 2012-05-31
found another way for achieving what i want.setting uid bit on /sbin/shutdown allows normal users to restart/shutdown from terminal without sudo password.
Only thing is:it will allow all users and not only the admin group.And that is acceptable at my end.

---

