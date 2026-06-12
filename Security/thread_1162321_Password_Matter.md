---
title: "Password Matter"
date: 2009-05-17
forum: Security
---

### Post by rishabh_destiny on 2009-05-17
I recently changed my pass from ABOUT ME menu from preferences. Now the problem is that, it sometimes recognizes my pass and sometimes not. Half of the time, it says password accepted and half of the time, pass incorrect. Although after entering the correct pass. What could be the issue?

I'm using ubuntu jaunty

---

### Post by Dr Small on 2009-05-17
Open a terminal, and type:
```
passwd
```

Enter your current password, and then enter your new password. This should change your password. Let us know if you have any more problems.

---

### Post by dec!&quot;` on 2009-05-21
I run Ubuntu 9.04 Jaunty and have the same problem. But, by now I already set 2 passwords and there must be a third one from my mate who was trying to help. Can I just set one without asking for the previous one?
Thanks!

---

### Post by cariboo on 2009-05-22
Start in recovery mode and at the menu choose drop to root prompt. At the prompt type:

```
passwd <username>
```

where username is your username.

---

