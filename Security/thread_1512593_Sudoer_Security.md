---
title: "Sudoer Security"
date: 2010-06-18
forum: Security
---

### Post by crazybrokenmike on 2010-06-18
Just looking for opinions as far as using the sudoer script for escalated privileges. Since by default anyone added to the admin group has sudo access wouldn't that provide someone who has access to the box more of a chance of gaining root access vs just have a single root account without admin's being able to sudo up? To clarify, once you have the password to someone in the admin group, you don't have to know a "root" password to sudo, just the password to the account you have already gained access to. Granted, the sudoers file are set for root access only but being as /etc/group can be read by most users and a simple grep command on the file can tell you who is in the admin group. Besides the obvious of having a strong password policy on your system, I would think this opens up a particular security threat as having more than one way to gain root access through a normal user. If I am missing something let me know. THanks!

---

### Post by Bachstelze on 2010-06-18
Of course, if you have full sudo access, you should give your account just as much security as you would give the root account if you had one. I fail to see your point there.

---

### Post by aysiu on 2010-06-18
Yes, once you have the password of someone in the *admin* group, you essentially have root.

Same thing as once you have the password of root on a non-Ubuntu Linux system.

What's your point exactly?

If the people in the *admin* account can't secure their passwords, they shouldn't be in the *admin* group. The nice thing about this model is that you can easily revoke that privilege by removing them from the group. If you have a root account you give certain users the root password to, you have to then inform all the other users as to the new root password and then change the root password.

---

### Post by Rubi1200 on 2010-06-18
[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

[http://tldp.org/HOWTO/Security-HOWTO/local-security.html](http://tldp.org/HOWTO/Security-HOWTO/local-security.html)

---

### Post by bodhi.zazen on 2010-06-18
> **crazybrokenmike said:**
> Just looking for opinions as far as using the sudoer script for escalated privileges. Since by default anyone added to the admin group has sudo access wouldn't that provide someone who has access to the box more of a chance of gaining root access vs just have a single root account without admin's being able to sudo up? To clarify, once you have the password to someone in the admin group, you don't have to know a "root" password to sudo, just the password to the account you have already gained access to. Granted, the sudoers file are set for root access only but being as /etc/group can be read by most users and a simple grep command on the file can tell you who is in the admin group. Besides the obvious of having a strong password policy on your system, I would think this opens up a particular security threat as having more than one way to gain root access through a normal user. If I am missing something let me know. THanks!

sudo access is no more or less secure then su. If a cracker has access to an account that has either sudo or su privileges to escalate to root, root access is not far behind, does not matter if sudo or su is used to gain (root) access.

If you have 10 users with full access via sudo and 10 users with full access via su - , what is the difference ?

The major advantage of sudo is that you can give much more flexibility then su, ie finer grains of control. su is all or none.

with sudo , however, you can give access to a limited set of commands.

See :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

To even have a chance of limiting a crackers access one has to use tools such as apparmor or selinux to confine root.

For example:

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/sect-Security-Enhanced_Linux-Targeted_Policy-Confined_and_Unconfined_Users.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/sect-Security-Enhanced_Linux-Targeted_Policy-Confined_and_Unconfined_Users.html)

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/chap-Security-Enhanced_Linux-Confining_Users.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security-Enhanced_Linux/chap-Security-Enhanced_Linux-Confining_Users.html)

So a user in the staff group has limited access to root via sudo and selinux. Even if a staff member runs sudo su -s (or similar) s/he is still confined by selinux.

You can configure the same behavior with apparmor or other tools.

---

### Post by crazybrokenmike on 2010-06-18
I guess my concern is that since with other distro I have used when you su - you still have to have the root password where as when you use sudo it only requires that you use the password from the account you are sudoing from. And since it seems that Ubuntu defaults everyone in the admin group as sudoers it creates a bigger foot print to work with if you wanted to gain root access to a computer. I suppose the real question I am trying to ask is if anyone has had problems with this? I have not had much experience sudo as I have always used distro's with the traditional su - command.

---

### Post by aysiu on 2010-06-18
> **crazybrokenmike said:**
> I guess my concern is that since with other distro I have used when you su - you still have to have the root password where as when you use sudo it only requires that you use the password from the account you are sudoing from. And since it seems that Ubuntu defaults everyone in the admin group as sudoers it creates a bigger foot print to work with if you wanted to gain root access to a computer. I suppose the real question I am trying to ask is if anyone has had problems with this? I have not had much experience sudo as I have always used distro's with the traditional su - command.
I'm still not seeing the issue.

Is the idea that a user password could be a weak one and the root password could be a stronger one? If a user who knows and uses the root password has her account compromised, the root password will shortly be compromised as well.

If you're really that worried, use strong passwords for all accounts. And if there are certain people you don't trust with being in the *admin* group, don't put them in that group. With *sudo* you can easily allow them only one or two privileges instead of system-wide privileges.

---

### Post by bodhi.zazen on 2010-06-18
> **crazybrokenmike said:**
> I guess my concern is that since with other distro I have used when you su - you still have to have the root password where as when you use sudo it only requires that you use the password from the account you are sudoing from. And since it seems that Ubuntu defaults everyone in the admin group as sudoers it creates a bigger foot print to work with if you wanted to gain root access to a computer. I suppose the real question I am trying to ask is if anyone has had problems with this? I have not had much experience sudo as I have always used distro's with the traditional su - command.

Only the first user is in the admin group by default, from there you would need to specify that any user(s) you add are in then admin group.

The arguement that only one password is needed with sudo (vs two for su) is counterbalanced by with with sudo the root account is locked.

So to "crack" an Ubuntu machine you need to know a user name + password.

To crack a distro that uses su, we already know the user name (root) now all we need is a password.

su vs sudo , is one more secure or better then another, I have not seen anything more then opinions (sometimes strong ones) on this subject.

Use whichever method you prefer, but do not fool yourself into believing sudo is more or less secure then su.

---

### Post by crazybrokenmike on 2010-06-18
Ok, thanks for the input. :-)

---

### Post by cariboo on 2010-06-18
I think you are misunderstanding something here, only the user you create when installing is in the admin group, you have to purposely add the rest of the users to the admin group manually.

---

### Post by rookcifer on 2010-06-18
I personally do not use sudo on my single user box.  I take my user out of the sudoers file, then unlock the root account and assign it a different password.  This way, as the OP is suggesting, if the user account is compromised, the attacker doesn't get root *de facto.*  

Many people say if a user account is compromised then it automatically means root isn't far behind.  But this, IMO, is incorrect.  After all, that's the whole point of having privilege separation in the first place.  If it was as ineffective as they suggest, we may as well not have limited users at all.  We all may as well run our boxes as root.

Sudo was created as a way for an administrator of a large network to delegate certain root tasks to trusted people without having to give them the all powerful root password.  The needed commands are put into the sudoers file and any command not listed for a particular user cannot be executed.  Moreover, any user not in the wheel group (Ubuntu calls it the admin group) cannot escalate privileges at all.  Sudo is basically akin to "capabilities" except instead of being for daemons, it is for user accounts.  It was not intended to be a substitute for root.

---

### Post by Bachstelze on 2010-06-18
> **rookcifer said:**
> I personally do not use sudo on my single user box.  I take my user out of the sudoers file, then unlock the root account and assign it a different password.  This way, as the OP is suggesting, if the user account is compromised, the attacker doesn't get root *de facto.*

However, the more you use your root account, the more likely it is to get compromised. You just move the problem, you don't suppress it.

> **rookcifer said:**
> It was not intended to be a substitute for root.

By that logic, computers weren't intended to display images, just text. But someone, some day, thought it would be cool to use them for displaying images too, and it works pretty well. Same for sudo, it's called evolution and innovation.

*EDIT:* By the way, albeit commented out by default, a default sudo installation will give a line to allow root access to all users in the wheel group, just like Ubuntu does. Why would the sudo devs put it if "it's not intended"?

---

### Post by bodhi.zazen on 2010-06-18
> **rookcifer said:**
> I personally do not use sudo on my single user box.  I take my user out of the sudoers file, then unlock the root account and assign it a different password.  This way, as the OP is suggesting, if the user account is compromised, the attacker doesn't get root *de facto.*  

Many people say if a user account is compromised then it automatically means root isn't far behind.  But this, IMO, is incorrect.  After all, that's the whole point of having privilege separation in the first place.  If it was as ineffective as they suggest, we may as well not have limited users at all.  We all may as well run our boxes as root.

Sudo was created as a way for an administrator of a large network to delegate certain root tasks to trusted people without having to give them the all powerful root password.  The needed commands are put into the sudoers file and any command not listed for a particular user cannot be executed.  Moreover, any user not in the wheel group (Ubuntu calls it the admin group) cannot escalate privileges at all.  Sudo is basically akin to "capabilities" except instead of being for daemons, it is for user accounts.  It was not intended to be a substitute for root.

It seems as if you understand su / sudo quite well and have thus decided on how you wish to sys admin your boxen.

The only point I would disagree with is that not all limited accounts are created equally.

I consider any account that has access to full root powers, either by sudo or su, to be a root account.

Privilege escalation is a broad term and in general applies to services running as non-root users (such as www-data for apache) or user accounts not in the admin group (sudo) or accounts that never access root via su.

I would caution you, if someone has access to log into an account you access root via su, root access is not far behind. The ways of doing this are almost too numerous to count. The only way to prevent root access from such an account is to disable the ability to access root.

Again, the account you use to access root is not the same as an account that never accesses root, either via su or sudo.

---

### Post by rookcifer on 2010-06-18
> **Bachstelze said:**
> However, the more you use your root account, the more likely it is to get compromised. You just move the problem, you don't suppress it.

That argument only works if the user runs his box from the root account 24/7.  The root account should only be used for installation of packages or routine maintenance, etc.  If that's all it's used for, I think running the box day to day from a non-sudo user account is safer.  If the password of the user account gets compromised, it wont do the attacker much good, whereas if the user account is in the sudoers file, it will give the attacker root.


> By that logic, computers weren't intended to display images, just text. But someone, some day, thought it would be cool to use them for displaying images too, and it works pretty well. Same for sudo, it's called evolution and innovation.

But the sudoers file was not intended to be an evolution away from the root account.  There's a difference in intentionally innovating something for one purpose and someone else taking an innovation and using it for a purpose it was not intended for.

All in all, I don't think sudo vs. root makes much difference in the real world since Linux systems tend to be pretty secure regardless.  But, it is an interesting debate.

---

### Post by crazybrokenmike on 2010-06-18
> **cariboo907 said:**
> I think you are misunderstanding something here, only the user you create when installing is in the admin group, you have to purposely add the rest of the users to the admin group manually.


I understand that. The whole point in case was on a larger scale network where perhaps you have a server(s) running Ubuntu(or any sudo based distro) in a small to medium size business and have different admins that have access sudo. This would mean that there are multiple admins which means that there is no longer one account that has some or all root escalation abilities. And since there is multiple accounts that also means more risk. I am not familiar with sudo and since have learned that it is more flexible then all or nothing. However, I still believe when it comes to hardening a system that the more surface area such as user accounts that can get escalated privileges the more chances for being compromised. Do you see what I am trying to say? I was simply trying to get some opinions following that train of thought. And usually in the enterprise world there is more than one admin account to manage server, network, san environments.

---

### Post by sisco311 on 2010-06-18
> **crazybrokenmike said:**
> I am not familiar with sudo

If you are not familiar with sudo, su, pkexec, chsh, passwd, gpasswd, ping and other setuid/setgid applications and/or with the unix/linux file permissions and ownership then why don't you learn how they work?

---

### Post by Bachstelze on 2010-06-19
> **sisco311 said:**
> If you are not familiar with sudo, su, pkexec, chsh, passwd, gpasswd, ping and other setuid/setgid applications and/or with the unix/linux file permissions and ownership then why don't you learn how they work?

Pedantic much? But we already knew that...

---

### Post by sf-it-services on 2010-06-19
I think the best thing about sudo is the fact that its 'su' 'do' its a one time command executed by the super-user or root this is not exactly the same as being logged in as the super-user although it has the same effect, and the sudo prefix does allow the user to be aware that what he is doing is a privileged command.

---

