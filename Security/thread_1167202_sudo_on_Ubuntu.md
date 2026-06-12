---
title: "sudo on Ubuntu"
date: 2009-05-22
forum: Security
---

### Post by Mistoffeles on 2009-05-22
I am trying to understand how the Ubuntu method of securing root access is superior to simply disallowing remote root login and requiring a user to login unprivileged and then use sudo or su to become root, using root's password, not the user's password.

It would seem to me that if someone were to get the user's password on an Ubuntu system, they would then have full access to that person's sudo privileges, since they only have to use sudo and the user's password that they already have to gain access to root functions.

In my example, if the password for the user's unprivileged account were compromised, the attacker would be limited to the user's workspace and have no access to root privileges. Additionally, if they somehow got the root password, they could do nothing without a user account to log into, and that user would have to have privilege to run su or sudo in order to gain any benefit from having the user password. The only weakness is that if the root password and physical access to the local console were acquired, they would have total control.

---

### Post by Dr Small on 2009-05-22
Well, we can always assume that physical access is always one of the weakest links in our chain of security, because with physical access, someone could do whatever it takes to break in, or steal the system.

But yes, your thought pattern is correct with sudo. If the privileged user's account was cracked, they could also use this as a way to gain root access. Whereas, if the user was not privileged to use sudo, and root had it's own password, the attacker would have to:
[list]
1) Bruteforce root via SSH (redundant if you disallow root logins)
2) Crack a user account, and then bruteforce the root account.
[/list]

So yes, I see where you are coming from (and even use root accounts on my own systems, just for backup when sudo fails me), even though these forums do not recommend using the root account.

---

### Post by Mistoffeles on 2009-05-22
Thanks, that's what I figured.

So is the Ubuntu "way" basically due to the fact that it is being put forth as an "easy Linux" for new users, to give them a default level of security that an experienced admin, who can set up things like I described, would not need?

---

### Post by Chemical Imbalance on 2009-05-22
I prefer su -c over sudo.

Physical access= "pure pwnage" (unless you have it in a bank vault encapsulated in lead) ;)

---

### Post by cdenley on 2009-05-22
It is safer to have a user-selected username for a user with administrative privileges than an account universally named "root". Nearly all brute force attempts on linux systems use the "root" account. I've never seen anyone but me try to authenticate on one of my servers with my username.

Admin users have admin privileges, and should be protected and use a strong password. If you are concerned about security, you can always use a non-admin user, then su to your admin user for admin tasks (treat admin user like root). Of course, then the user would be forced to remember two passwords, which would be unacceptable for a typical user.

The ubuntu method also works better for environments where there are multiple admins. You shouldn't have multiple users using the same password. If one admin is fired from the project or something, you would have to reset the root password. If you forget, you might have some disgruntled former admin zeroing out your disks. In ubuntu, you just need to disable the user's account.

---

### Post by bodhi.zazen on 2009-05-22
> **Mistoffeles said:**
> I am trying to understand how the Ubuntu method of securing root access is superior to simply disallowing remote root login and requiring a user to login unprivileged and then use sudo or su to become root, using root's password, not the user's password.

It would seem to me that if someone were to get the user's password on an Ubuntu system, they would then have full access to that person's sudo privileges, since they only have to use sudo and the user's password that they already have to gain access to root functions.

In my example, if the password for the user's unprivileged account were compromised, the attacker would be limited to the user's workspace and have no access to root privileges. Additionally, if they somehow got the root password, they could do nothing without a user account to log into, and that user would have to have privilege to run su or sudo in order to gain any benefit from having the user password. The only weakness is that if the root password and physical access to the local console were acquired, they would have total control.

I am not sure what you are asking here.

First sudo is no more or less secure then su . sudo is, however, more versatile in that su gives root access in an all or none fashon (and can not be configured).

sudo, however, can be configured to operate in almost any way you wish, inclusing using a root password, see man sudoers.

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

Second, in terms of compromise, if a user account is compromised you are potentially in trouble and if this is the case I suggest you re-install. Compromised accounts can be problematic as there are ways to escalate to root privileges (this is what crackers do, :lolflag: ) and can cause issues without root access.

Third, if you want to restrict users and privileges you need to look at apparmor or selinux. Those kernel modules address your concerns about escalation of privileges (and not su / sudo).

Last, physical access == big trouble. IMO the only protection you have if a cracker has physical access is encryption. You can encrypt your installation with the alternate CD.

---

### Post by Mistoffeles on 2009-05-26
> **bodhi.zazen said:**
> Second, in terms of compromise, if a user account is compromised you are potentially in trouble and if this is the case I suggest you re-install. Compromised accounts can be problematic as there are ways to escalate to root privileges (this is what crackers do, :lolflag: ) and can cause issues without root access.

My point being, if I am an administrator and my account gets compromised, on a default Ubuntu install root is also compromised because anyone who gets into my account can simply 'sudo -i' and, using the same password they just used, have full root access.

---

### Post by cdenley on 2009-05-26
> **Mistoffeles said:**
> My point being, if I am an administrator and my account gets compromised, on a default Ubuntu install root is also compromised because anyone who gets into my account can simply 'sudo -i' and, using the same password they just used, have full root access.

If the admin account's password is compromised, then root is compromised. There are others ways to compromise an account than guessing the password.

---

### Post by bodhi.zazen on 2009-05-26
> **Mistoffeles said:**
> My point being, if I am an administrator and my account gets compromised, on a default Ubuntu install root is also compromised because anyone who gets into my account can simply 'sudo -i' and, using the same password they just used, have full root access.

As mentioned by [cdenley]("http://ubuntuforums.org/member.php?u=204457") , if I have access to an account on Fedora / Centos / Slackware etc , distros that use su, full root access is not far behind.

If you do not like the default behavior of sudo, configure it. read man sudoers and set sudo to use the target password rather then the user password. this will, of course, require you to set a root password.

My point is sudo has far more configuration options then su.

I do not think su is more or less secure then sudo.

If you wish to limit compromised accounts your best option is to look at apparmor or selinux.

---

