---
title: "Login hours and Session timeouts."
date: 2008-02-17
forum: Security Discussions
---

### Post by Dandeloreon on 2008-02-17
Pretty much as the title says, i am looking in to how to properly configure login hour restrictions where a user is automatically logged off when their time is up. and then on top of that, to automatically log them off when they are inactive for about 30 minutes.

**edit:**

i did change Time.conf, however a few more changes will be needed to enforce the hours, and get the users to automatically log off when the time limit is reached... for example, i need limits to where users can't login from 9pm to 5am the next day from Monday to thursday... so far i know the change for the Time.conf, but i need to find out other changes, namely time.conf needs the following.
```

# Affected user can't login from 21:00 hours till 24:00 hours on Monday through Thursday.
login|gdm;*;AffectedUser;!MoTuWeTh2100-2400
# Affected user can't login from 00:00 hours till 05:00 hours on Tuesday through Friday.
login|gdm;*;AffectedUser;!TuWeThFr0000-0500

```

---

### Post by k_grdn on 2008-02-17
Hi,

Xinetd can provide such restrictions, run sshd under xinetd.

Regards,

k_grdn

---

### Post by Dandeloreon on 2008-02-17
Xinetd would have worked, if they where connecting from the internet, but they are physically using gdm to login and i want it to automatically sign them out after 30 minutes of inactivity.

---

