---
title: "sudo not asking for admin password"
date: 2012-03-29
forum: Security
---

### Post by CptanPanic on 2012-03-29
I have a new installation of 11.10.  I have an admin user, and a standard user that doesn't have password.  If I log in as standard user, when I use sudo from command line, it asks for that users password, which doesn't work because that user has no password, and isn't admin.  If I log in as admin user, it asks for admins password.  How do I make sudo always ask for admin password?
Thanks,
CP

---

### Post by Ms. Daisy on 2012-03-30
I'm not sure I understand what you're trying to accomplish.  What's the purpose of the standard user account for you?  From Ubuntu's perspective, the standard user account would be so that you can have a user with limited rights.

You could add the standard user to the sudo group, and then you would assign him his own password.  I suppose you could give him the same password as your admin account, but what would be the point of the standard account then?

You can also su from one user account to another account but someone with more experience would have to guide you on that.

You can read more about Ubuntu user accounts here
[https://help.ubuntu.com/11.10/ubuntu-help/user-admin-explain.html](https://help.ubuntu.com/11.10/ubuntu-help/user-admin-explain.html)
[https://help.ubuntu.com/11.10/ubuntu-help/user-admin-change.html](https://help.ubuntu.com/11.10/ubuntu-help/user-admin-change.html)

---

### Post by darkod on 2012-03-30
I also don't understand what do you want to accomplish.

As far as I know, sudo doesn't ask you for admin password. It's role is to ask for the same user password again, only it will elevate the user to a higher level to do admin tasks. This could work only if the user is part of the sudoers group.

So, if you want your "standard" user to have permission to do admin tasks, simply configure a password for it, and with sudo and entering the password a second time it can do admin tasks.

If you don't want it to have admin permissions, leave it outside the sudoers and it can't do admin tasks. Then you will need to do them with another user.

---

### Post by dfreer on 2012-03-31
> **CptanPanic said:**
> I have a new installation of 11.10.  I have an admin user, and a standard user that doesn't have password.  If I log in as standard user, when I use sudo from command line, it asks for that users password, which doesn't work because that user has no password, and isn't admin.  If I log in as admin user, it asks for admins password.  How do I make sudo always ask for admin password?
Thanks,
CP

It sounds like the OP is trying to create the following enviroment: Have a user with limited rights be able to login with no password. Then, when the user needs to be able to perform administrative functions, the user can temporarily login as root (or at least a user with higher permissions such as the ability to use sudo).

The solution in this case is to have the user with no password use **su** to login as the other user with higher permissions. If the higher permissions user is root, then that is all. But if not, then once the user is logged in they will need to use **sudo** to perform administrative functions.

In short, OP needs to know the difference between su and sudo I believe. I may be wrong.

---

### Post by dres on 2012-03-31
I am having the opposite problem. I can't install updates available in Ubuntu 11.10 because it ask's for a root password. I type in the password I created when I first installed Ubuntu 11.10 and nothing (Your authentication request was unsuccesful). Please HELP!!!

---

### Post by DarthLord on 2012-03-31
> **dres said:**
> I am having the opposite problem. I can't install updates available in Ubuntu 11.10 because it ask's for a root password. I type in the password I created when I first installed Ubuntu 11.10 and nothing (Your authentication request was unsuccesful). Please HELP!!!

hi

---

