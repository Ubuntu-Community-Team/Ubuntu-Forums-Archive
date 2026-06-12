---
title: "root login problems"
date: 2009-05-04
forum: Security
---

### Post by TomB19 on 2009-05-04
On a system I upgraded to Jaunty last week, I can no longer set the user to root.  I know I've jumped in and out of root several times since the upgrade so I don't think this is upgrade related, but am not sure.

```
$ su -
Password:
su: Authentication failure
```

The thing is, I know the password is correct.  I have another root session open and I've changed the password to see what would happen and it still doesn't work.

```
$ sudo ls /
[sudo] password for TomB19:
sudo: pam_acct_mgmt: 7
Sorry, try again.
```

I've done some searching through the forums and the only thread I could find that seemed related suggested running "chmod +s /bin/su".  This did not help but the symptoms don't seem identical so it was a bit of a long shot.

Any idea where I might start looking?

Thanks!  :)

---

### Post by TomB19 on 2009-05-04
... so I updated my system.  The update process replaced a PM configuration and now it's working.  :lolflag:

---

