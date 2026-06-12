---
title: "New Install of Jaunty won't recognize password"
date: 2009-05-30
forum: Security
---

### Post by RealGomer on 2009-05-30
I just installed Jaunty (9.04) on one PC. As is my habit, when I created the password, I wrote it down BEFORE hitting the enter key. Now, Jaunty claims it's an incorrect password. When I try to change it under About Me, the authentification waiting icon sits there for upwards an hour. Using Terminal returns an error message. Now what?

---

### Post by Rubicon_82 on 2009-05-30
You can reset your password by doing the following:

1) Reboot.  At the Grub menu, select Recovery Mode, and follow the prompts to get a root console.

2) Run the passwd command, specifically:
```

passwd <user>

```
where '<user>' is replaced with your normal login name.  This will allow you to change your password.

3) Reboot.  You should now be able to login normally with your new password.

For more information, see:
```

passwd --help
```
or
```

man passwd
```
and the Community documentation on the subject at [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

