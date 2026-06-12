---
title: "Securing Sudo"
date: 2010-03-31
forum: Security
---

### Post by lorddarkflare on 2010-03-31
I have been doing some research and have come to the conclusion that my nascent server should get a much needed boost to security.

To this end, I have started for ways to handle some of the user privileges and am planning to use the following configurations:

-Admin and sub-admins get limited ability to do certain changes based on the tasks that they most often perform through sudo

-No single user can Sudo up to all of root privileges, not even the main admin

-Sudo times out in 2 minutes instead of 5

-Only the admin has the root password and only he(I) can gain complete root access and that is only through Su, and only when his limited Sudo privileges do not cut it

-**Sudo requires a password other than login. So users effectively have 2 passwords, one to login to their account, and a different one when they want to gain Sudo. This second password would be different for each user, and different from the root password as well.**

Now, of all of those, my biggest issue is the last one.** Is it at all possible to setup a password specifically for gaining Sudo?**

I only started learning this stuff last week, so go easy on me :smile:.

---

### Post by cdenley on 2010-03-31
> **lorddarkflare said:**
> 
Now, of all of those, my biggest issue is the last one.** Is it at all possible to setup a password specifically for gaining Sudo?**

I don't think so. sudo will only prompt for the user's password, the root password, or the password of the user they user running the command as.
```

man sudoers

```

Also, I would suggest not setting a root password. It would be better to only allow a single user or group to have full sudo privileges.

---

### Post by bodhi.zazen on 2010-03-31
> **lorddarkflare said:**
> I have been doing some research and have come to the conclusion that my nascent server should get a much needed boost to security.

To this end, I have started for ways to handle some of the user privileges and am planning to use the following configurations:

-Admin and sub-admins get limited ability to do certain changes based on the tasks that they most often perform through sudo

-No single user can Sudo up to all of root privileges, not even the main admin

-Sudo times out in 2 minutes instead of 5

-Only the admin has the root password and only he(I) can gain complete root access and that is only through Su, and only when his limited Sudo privileges do not cut it

-**Sudo requires a password other than login. So users effectively have 2 passwords, one to login to their account, and a different one when they want to gain Sudo. This second password would be different for each user, and different from the root password as well.**

Now, of all of those, my biggest issue is the last one.** Is it at all possible to setup a password specifically for gaining Sudo?**

I only started learning this stuff last week, so go easy on me :smile:.

Well, this is the advantage of sudo over su , controlled access to root. su is , as you know, all or none.

Honestly, I would just configure sudo and not worry all *that* much about passwords. Enforce strong login passwords and you will be fine.

I would put your energy into learning to use apparmor or selinux (or similar).

For example : [http://www.engardelinux.org/](http://www.engardelinux.org/)

You can log into engarde as root and selinux will confine you.

---

### Post by lorddarkflare on 2010-03-31
The problem I have with sudo is that in Ubuntu, the minute the account with full privileges logs in, it might as well be root because it is only one simple log-in password away from that.

But still, I like the restriction of rights for other users.

Perhaps I may have to right this rule in myself, or maybe it *IS *in sudoers and I just have to dig.

---

### Post by bodhi.zazen on 2010-03-31
> **lorddarkflare said:**
> The problem I have with sudo is that in Ubuntu, the minute the account with full privileges logs in, it might as well be root because it is only one simple log-in password away from that.

But still, I like the restriction of rights for other users.

Perhaps I may have to right this rule in myself, or maybe it *IS *in sudoers and I just have to dig.

You can configure sudoers to use the target PW, in this case root, rather then the user password.

I understand what you are saying, but if the admin account is compromised, root access is not far too behind, no matter how many passwords you use.

Again, this is where you might want to look at apparmor or selinuix.

---

### Post by cdenley on 2010-03-31
> **lorddarkflare said:**
> The problem I have with sudo is that in Ubuntu, the minute the account with full privileges logs in, it might as well be root because it is only one simple log-in password away from that.

It is a good compromise between usability and security. If you're more concerned about security, then use an unprivileged user, and treat your admin user as root. You can switch to your admin user when you need to escalate privileges.

---

### Post by _GoRDoN_ on 2010-04-01
If you use ssh to control the server then you can get this 2 password system quite easily. Just use keys with passphrases to login and actual password with sudo.

---

