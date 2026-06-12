---
title: "Please Help me (Ubuntu server 10.10). Cant add user"
date: 2018-03-13
forum: Server Platforms
---

### Post by novandika.rizki on 2018-03-13
Please help me about this:


```
root@PDS-PRD-STORAGE:~# adduser tes
Adding user `tes' ...
Adding new group `tes' (1017) ...
groupadd: cannot lock /etc/group; try again later.
adduser: `/usr/sbin/groupadd -g 1017 tes' returned error code 10. Exiting.
root@PDS-PRD-STORAGE:~# smbpasswd -a tes
New SMB password:
Retype new SMB password:
Failed to add entry for user tes.
root@PDS-PRD-STORAGE:~#
```

[ATTACH=CONFIG]278939[/ATTACH]

anyone?

---

### Post by lisati on 2018-03-13
*Thread moved to **Server Platforms**.*

Before we get to troubleshooting your problem, are you are aware that 10.10 is an old, unsupported version? I'd recommend upgrading, if possible, to a newer version of Ubuntu server.

---

### Post by novandika.rizki on 2018-03-13
> **lisati said:**
> *Thread moved to **Server Platforms**.*

Before we get to troubleshooting your problem, are you are aware that 10.10 is an old, unsupported version? I'd recommend upgrading, if possible, to a newer version of Ubuntu server.

Thanks. i'll  upgrade it later. but what about this case?

---

### Post by lisati on 2018-03-13
You are more likely to get useful support if you are using a more recent version of  Ubuntu.

Please post the output of:
```

ls /etc/ | grep "lock"

```

---

### Post by QIII on 2018-03-14
When you have sorted out this single issue, please do not ask other users to spend their volunteer time attempting to provide support for such an old release.

Thanks.

---

### Post by novandika.rizki on 2018-03-14
> **lisati said:**
> You are more likely to get useful support if you are using a more recent version of  Ubuntu.

Please post the output of:
```

ls /etc/ | grep "lock"

```

i use that code, but stil cannot work:confused::confused:?

---

### Post by lisati on 2018-03-14
What was the output from the command?
Is this the same computer that you mentioned in your [other thread]("https://ubuntuforums.org/showthread.php?t=2378444")?

---

### Post by novandika.rizki on 2018-03-14
> **lisati said:**
> What was the output from the command?
Is this the same computer that you mentioned in your [other thread]("https://ubuntuforums.org/showthread.php?t=2378444")?

Adding user `opr' ...
Adding new group `opr' (1017) ...
groupadd: cannot lock /etc/group; try again later.
adduser: `/usr/sbin/groupadd -g 1017 opr' returned error code 10. Exiting.

the same computer, but still cannot work?:(

---

### Post by lisati on 2018-03-14
If your disk is full or there are problems with your disk, then you are likely to run into problems adding new users. It would be a good idea to resolve those issues first.

My recommendation to upgrade to a newer version of Ubuntu stands.

Thread closed.

---

