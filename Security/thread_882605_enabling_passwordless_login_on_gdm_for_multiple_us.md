---
title: "enabling passwordless login on gdm for multiple users, using PAM settings"
date: 2008-08-07
forum: Security
---

### Post by sameerds on 2008-08-07
I have a PC at home with two users on it. We are not concerned about physical access to the system, so we would like to have a login that does not prompt for passwords. Searched around for such a setup, but didn't find anything satisfactory.

A common method is to reset the password in /etc/passwd, and then configure PAM and gdm to allow null passwords. But if the user has sudo privileges, then sudo does not prompt for a password as well, which kinda defeats the purpose of sudo. Basically, I want to disable passwords only in gdm, and not in the system itself.

I searched in the PAM documentation a bit and came up with the pam_succeed_if module. So I added a line for that module in /etc/pam.d/gdm, just before the line that includes common-auth

```
auth    sufficient       pam_succeed_if.so user ingroup users
@include common-auth
```

This seems to work. Both the users are members of the group "users". We can now login without having to type anything at the prompt, with a suitable theme for gdmgreeter. But I just want to make sure this is a good idea, and accomplishes only what I intended. For example, I don't know if this setup for gdm in PAM somehow interacts with anything else.

One thing I noticed, is that for one of the two users, the logout button on the desktop behaves wierdly now. If that user logs in and clicks on the logout button without doing anything else, it does not respond. If the user then performs any other action like clicking a launcher or opening a document, the logout screen comes up, as if it had been waiting for some condition to occur!

---

### Post by vlovich on 2008-08-07
Sorry - misread the post.  It seems you're doing it correctly.

[http://ubuntuforums.org/showthread.php?t=123116](http://ubuntuforums.org/showthread.php?t=123116)

Even better step-by-step explanation
[http://www.dm.ufscar.br/~sadao/freeware/linux/postinst-710.txt](http://www.dm.ufscar.br/~sadao/freeware/linux/postinst-710.txt)

---

