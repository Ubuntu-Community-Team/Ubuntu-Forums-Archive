---
title: "How much damage can a compromised user account cause?"
date: 2012-03-13
forum: Security
---

### Post by gudirun on 2012-03-13
Suppose I create a user account for a friend without entry in sudoers. And that account gets hacked.

What I can think off:
- they can use outgoing internet connections, I will held responsible for any DMCA and other abuse complaints
- they can read my /home folder if I do net set permissions not to do so
- they can create a huge system load until the system becomes unreliable
- they can try privilege escalation and compromise the whole system

Let's also suppose they are unable to do privilege escalation (which is sufficiently hard on a patched system for a Jon Doe script kiddy)...

What else? How much damage can a compromised user account cause?

What else should I do to lock down the user account of the guest?

---

### Post by wacky_sung on 2012-03-13
If you are million dollar man,lamers can steal your personal data and blackmailer you. Lkewise if you are commoners and who cares.:lolflag::lolflag::lolflag:

---

### Post by bodhi.zazen on 2012-03-13
For guests, use the guest account, it is confined by apparmor.

As far as intruders, depends on the skill and intent of the intruder. I would not so easily dismiss privilege escalation.

google search botnet.

---

### Post by 0011235813 on 2012-03-14
Well, they **could** do damage. It all depends I'm afraid. As far as I'm aware, a user cannot view or change the folders of an admin account, as for non-admin users, I'm not sure, I think an admin account could view a non-admin user... But I'm not sure.
The thing is, is how to get rid of a compromised admin account. How do you get rid of one? If system allows the admins to delete accounts, a compromised account could delete all your files! But if not, you won't be able to get rid of them. That's why it is good to use a separate root password in multi-user accounts, and not just the admin password.

---

### Post by bodhi.zazen on 2012-03-14
> **0011235813 said:**
> Well, they **could** do damage. It all depends I'm afraid. As far as I'm aware, a user cannot view or change the folders of an admin account, as for non-admin users, I'm not sure, I think an admin account could view a non-admin user... But I'm not sure.
The thing is, is how to get rid of a compromised admin account. How do you get rid of one?

It can be difficult to impossible. If you have the skills, and can identify what has been compromised you can recover, if not re-install and restore your data from a known good backup.

> If system allows the admins to delete accounts, a compromised account could delete all your files! But if not, you won't be able to get rid of them. That's why it is good to use a separate root password in multi-user accounts, and not just the admin password.

That last point is highly debatable. sudo has many advantages in a multiuser environment including better logging and finer grained control of root access. 

su (root password) is all or none. with sudo you can limit root access to only certain commands.

See : [http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

Even Fedora, one of the longest hold outs, is offering sudo.

---

### Post by youngunix on 2012-03-14
If it has nothing of value to the attacker, it'll be used as a zombie to perform certain tasks.

---

### Post by 0011235813 on 2012-03-14
> **bodhi.zazen said:**
> It can be difficult to impossible. If you have the skills, and can identify what has been compromised you can recover, if not re-install and restore your data from a known good backup.



That last point is highly debatable. sudo has many advantages in a multiuser environment including better logging and finer grained control of root access. 

su (root password) is all or none. with sudo you can limit root access to only certain commands.

See : [http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

Even Fedora, one of the longest hold outs, is offering sudo.
I think you mis-understood the post. I didn't say you should use root instead of sudo, I said **you should use a separate root password**, so when you type in 
```
sudo apt-get install <whatever> 
```
instead of typing your log on password, you type in the root password. If not an admin account, sudo wouldn't even be available.

---

### Post by bodhi.zazen on 2012-03-14
> **0011235813 said:**
> I think you mis-understood the post. I didn't say you should use root instead of sudo, I said **you should use a separate root password**, so when you type in 
```
sudo apt-get install <whatever> 
```
instead of typing your log on password, you type in the root password. If not an admin account, sudo wouldn't even be available.

It takes a little effort to do that, you have to first set a root password (which in itself can be considered a security risk), then configure sudo.

In addition, that adds little to security, if an account with root access is cracked, root access is not far behind, does not matter if you use sudo, su, or set a root password as you suggest. Many of the exploits to obtain root access work with all those methods (su, sudo, sudo with root pw).

You are also assuming that the intruder obtained a shell with a password. Most (many) exploits these days use other methods.

---

### Post by 0011235813 on 2012-03-14
> **bodhi.zazen said:**
> It takes a little effort to do that, you have to first set a root password (which in itself can be considered a security risk), then configure sudo.

In addition, that adds little to security, if an account with root access is cracked, root access is not far behind, does not matter if you use sudo, su, or set a root password as you suggest. Many of the exploits to obtain root access work with all those methods (su, sudo, sudo with root pw).

You are also assuming that the intruder obtained a shell with a password. Most (many) exploits these days use other methods.
The root password can be set at installation quite easily...

I'm not sure I get you. If the compromised account uses a password that has been compromised, actual damage to the root folders would still require the use of the uncompromised root password...

I don't understand- to alter root you need the root password, the compromised account's password isn't the root password, that's why I suggested separate root password in the first place. Also, if an admin account wanted to remove another admin account, the root password would be neccessary. Thus you can get rid of compromised accounts easily, and compromised accounts can't get rid of you!

---

### Post by bodhi.zazen on 2012-03-14
> **0011235813 said:**
> I don't understand- to alter root you need the root password, the compromised account's password isn't the root password, that's why I suggested separate root password in the first place. Also, if an admin account wanted to remove another admin account, the root password would be neccessary. Thus you can get rid of compromised accounts easily, and compromised accounts can't get rid of you!

That sort of makes limited sense if the comprise is due to a compromised password.

By definition, an admin account has root access, so your method in no way prevents and admin (someone with root access) from accessing another admin's account or system files.

Usually a compromise is not a password, it is "arbitrary code" or shell access.

See the reports here - [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

So, now our intruder has shell access. They can do tons of damage already, without privilege escalation.

They can then, if they so desire, try to leverage privilege escalation. They need a password, either the login (sudo), root (su), or with your method root (target_pw). So, either way, they are one password away from root access. As with shell access, many exploits (code injection) do not require determining the password. The ones that do gain the password work with all 3 (sudo, su, or target_pw).

Your problem is that you are assuming that the only exploit or method of privilege escalation is via password compromise, and, sadly that is simply not the case.

---

### Post by 0011235813 on 2012-03-15
> **bodhi.zazen said:**
> That sort of makes limited sense if the comprise is due to a compromised password.

By definition, an admin account has root access, so your method in no way prevents and admin (someone with root access) from accessing another admin's account or system files.

Usually a compromise is not a password, it is "arbitrary code" or shell access.

See the reports here - [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

So, now our intruder has shell access. They can do tons of damage already, without privilege escalation.

They can then, if they so desire, try to leverage privilege escalation. They need a password, either the login (sudo), root (su), or with your method root (target_pw). So, either way, they are one password away from root access. As with shell access, many exploits (code injection) do not require determining the password. The ones that do gain the password work with all 3 (sudo, su, or target_pw).

Your problem is that you are assuming that the only exploit or method of privilege escalation is via password compromise, and, sadly that is simply not the case.

Ah the last line cleared it up thanks.

---

### Post by bodhi.zazen on 2012-03-15
> **0011235813 said:**
> Ah the last line cleared it up thanks.

You are most welcome.

---

