---
title: "Administrator vs. Standard User"
date: 2012-11-29
forum: Security
---

### Post by optimumpro on 2012-11-29
Hello all.  I have a question. Please forgive if this has already been answered:

Is it possible on Ubuntu 12.10 to set accounts the way it is done in Windows, i.e. to have a standard user account where if there is an administrative task to be performed I would have a prompt for administrator's password? That is how I had it in Windows. In other words, I created a separate Administrative account and used my standard account for every day activities. However, when I needed to perform an administrative task, instead of signing out of my standard account, I would simply have a windows prompt to enter my administrative credentials. Thanks in advance.

---

### Post by snowpine on 2012-11-29
This page will answer all your questions: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Specifically, the first user you create (when you install) and all users in the 'sudo' group are considered 'administrators' and have the ability to use 'sudo' for administrative tasks. So if you want to have a non-administrative user, make a new user account and don't put it in the 'sudo' group, then that user won't be able to make any system-wide changes.

Hope that helps, welcome to the forums!

---

### Post by Morbius1 on 2012-11-29
It's unfortunate that Linux has started using the term "Admisistrator" as one class of users becasue it's not the same thing as "Administrator" in Windows. The "Administrator" in Windows is almost like root in Linux and as such you are cautioned not to run as either.

The Administrator in Linux is what snowpine just posted and fulfils this requirement exactly:
> ... to have a standard user account where if there is an administrative task  to be performed I would have a prompt for administrator's password?An Administrator in Linux acts just like a regular user until you need to have elevated privileges - at that point you will be prompted for the sudo password.

A regular user in Linux has no sudo password so he is limited in what he can do. If you are the only user you want to be an administrator.

---

### Post by optimumpro on 2012-11-29
Thanks for your replies. I understand that standard users don't have sudo password. Now, regarding the root account: if it is disabled, could a remote attacker enable it and take over the system? If that's the case, would it make sense to enable the root account and protect it with a strong password?

---

### Post by snowpine on 2012-11-29
> **optimumpro said:**
> Thanks for your replies. I understand that standard users don't have sudo password. Now, regarding the root account: if it is disabled, could a remote attacker enable it and take over the system? If that's the case, would it make sense to enable the root account and protect it with a strong password?

If you have a root password (most Linux distros) then a remote attacker knows the username (root) and only has to guess the password.

If the root account is locked (Ubuntu) then a remote attacker has to simultaneously guess BOTH your username and password. It is exponentially more secure. :)

---

### Post by newbie-user on 2012-11-29
The only way for someone to enable the root account is if they have access to an existing account that can use sudo. Furthermore, a remote hacker would need some sort of entry point to even try to access the system. If you have any services running, such as ssh, which allow remote access, this might be possible. So, yes, it would be a good idea to have a strong root password. In the case of ssh, you might also want to disable password login and require ssh keys.

---

### Post by spynappels on 2012-11-30
> **newbie-user said:**
> So, yes, it would be a good idea to have a strong root password. 

This is not strictly correct in the context of Ubuntu. Not having the root account enabled (as in no password set) is more secure than a strong password for the root account and the account enabled. By default, it is impossible to log in as root on a standard Ubuntu install, and this adds a layer of security for inexperienced users. Only enable the account with a password if you are absolutely sure you can keep the system secure, otherwise leave as is.

> **newbie-user said:**
> In the case of ssh, you might also want to disable password login and require ssh keys.

This is always good advice.

---

