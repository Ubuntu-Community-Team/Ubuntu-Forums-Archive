---
title: "Change root password (Some questions)"
date: 2011-07-10
forum: Security
---

### Post by pato wlmc on 2011-07-10
Ok, so I've been using Ubuntu for like a year now, but being sincere it has never been my Main OS, and there have been periods of time where I've stopped using Linux.

Now I'm really getting into it and I have some questions regarding the root user.

Whenever I want root privileges I just type sudo and enter my User password.

I wanna know if there's a way to change this, in a way that My User password is: "ABC" and the password needed to have root privileges is: "ABC123" (or whatever else, i think you have the idea)

Thanks in advance

NOTE: I have no problem using the terminal, I actually prefer it to any GUI, it just seems easier to me =D

---

### Post by karlson on 2011-07-10
As far as I know there is no way to have a separate password from what you default user password is.  The question is why would you want to be in the admin group to be able to become root and have a weak password?

---

### Post by cariboo on 2011-07-11
About the only way I can think of doing what you want, it to have two separate users, one with limited privileges, and an admin user. You can then use **]su** to switch users to the user with admin privileges. You could also do the same thing by enabling the root account.

Of course if you enable the root account, you should also be aware of the damage you can do to the system by mistake, if you don't log out of the root account as soona s you finish doing what you were doing.

---

### Post by bodhi.zazen on 2011-07-11
> **pato wlmc said:**
> Ok, so I've been using Ubuntu for like a year now, but being sincere it has never been my Main OS, and there have been periods of time where I've stopped using Linux.

Now I'm really getting into it and I have some questions regarding the root user.

Whenever I want root privileges I just type sudo and enter my User password.

I wanna know if there's a way to change this, in a way that My User password is: "ABC" and the password needed to have root privileges is: "ABC123" (or whatever else, i think you have the idea)

Thanks in advance

NOTE: I have no problem using the terminal, I actually prefer it to any GUI, it just seems easier to me =D

Yes, read the man pages for sudo and sudoers 

[http://www.gratisoft.us/sudo/man/1.8.1/sudo.man.html](http://www.gratisoft.us/sudo/man/1.8.1/sudo.man.html)

[http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

