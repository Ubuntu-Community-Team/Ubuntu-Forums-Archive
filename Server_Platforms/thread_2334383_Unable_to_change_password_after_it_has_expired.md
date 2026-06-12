---
title: "Unable to change password after it has expired"
date: 2016-08-19
forum: Server Platforms
---

### Post by Eloge_Bapfunya on 2016-08-19
Hi all,
I have an issue with my server which has only one user account enabled. Its password expired and the root account is disable from login. I tried to boot in recovery mode, get in root maintenance prompt and type the command:
```
passwd username
passwd: Authentication token manipulation error
passwd: password unchanged

```The system doesn't even give me possibility to type new password.
I unmount and remount the partition as read/write with this command:
```
mount -o remount,rw /
```
but it still get same error message.
Do I have to change something before trying to change the password.
Thank you in advance for your help.

EB.

---

### Post by howefield on 2016-08-19
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by DigiAngel on 2016-08-20
Have you made any changes to the user with chage or mucked with your /etc/login.defs?

---

