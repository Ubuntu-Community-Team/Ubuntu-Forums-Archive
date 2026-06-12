---
title: "root user and security"
date: 2012-12-31
forum: Security
---

### Post by phamhung on 2012-12-31
Hello,

Firstly, thanks for great distro. I just installed Ubuntu on a VPS and it runs fast. Quite impressed. 

Saying that, I am very new with Ubuntu. So, here is the first question about security in Ubuntu.

I know the root account is disabled by default. Any action will need to do through sudo. However, it seems less secure than Redhat-based machine? For example
- in Ubuntu: I access ssh through user-ubuntu, then do any action with sudo and password of user-ubuntu.
- in Redhat: I access ssh through user-redhat. But I will need to know root password too for processing any root-related actions. That means if I lost password of user-redhat, my machine is still "more secured" than Ubuntu machine, because user-redhat cannot do root-level actions.

Please correct me if I am wrong.
Thanks

---

### Post by deadflowr on 2012-12-31
user-redhat can still run as root if it is part of the sudo/admin group.
The problem with running as root, is that typically you run root open ended, where as running as sudo is limited per instance.
Running open ended is like opening the door to your house and keeping it open. Running sudo is like opening the door and then when you've finished closing it and locking it.
To look at an example of open ended root users look no further than earlier versions of windows, where users normally set up one account, an administrator, and ran it as such, in essence a root user. This action is one main reason so many had their machines compromised. Later version of Windows have tried to change that, thankfully, albeit not highly successfully.

---

### Post by phamhung on 2012-12-31
Thanks for explanation. 

However, with user-redhat, I don't need to put it to sudo group. Here is the real example

[user-redhat@testbox ~]$ ls /root
ls: /root: Permission denied
[user-redhat@testbox ~]$ sudo ls /root

We trust you have received the usual lecture from the local System Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for user-redhat: 
user-redhat is not in the sudoers file.  This incident will be reported.
[user-redhat@testbox ~]$ 

As the result, even I accessed under user-redhat and entered password of user-redhat, I still cannot do root-related action. 

But with Ubuntu, due to user-ubuntu is belonged to sudo group, I can do root-level actions. Will it end up with less-secured environment?

---

### Post by samiux on 2012-12-31
> **phamhung said:**
> Thanks for explanation. 

However, with user-redhat, I don't need to put it to sudo group. Here is the real example

[user-redhat@testbox ~]$ ls /root
ls: /root: Permission denied
[user-redhat@testbox ~]$ sudo ls /root

We trust you have received the usual lecture from the local System Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for user-redhat: 
user-redhat is not in the sudoers file.  This incident will be reported.
[user-redhat@testbox ~]$ 

As the result, even I accessed under user-redhat and entered password of user-redhat, I still cannot do root-related action. 

But with Ubuntu, due to user-ubuntu is belonged to sudo group, I can do root-level actions. Will it end up with less-secured environment?

First of all, "sudo" is designed for administration purpose more than security purpose, I think.  With "sudo" accounts setup, SysAdmin is not required to release his very important root password to others.  He just have to set the permission of the users only.  And he can set the different level of permission too.

In the view of security, "sudo" and "root" are similar.  The sudoer with the root privilege and root account can do the same work, they are same.

Finally, only the first Ubuntu user account has the root privilege sudoer (uid 1000).  The following users (uid 1001+) are not unless you give them the privilege.

Therefore, in my own opinion, you must treat the root account and the first Ubuntu account as the same level.

P.S. root account means the Linux system without sudoer setup

Samiux

---

### Post by deadflowr on 2012-12-31
As I said before when you run as root, you are in root for the durasion, so if you get to root and stay there indefintely you're system will be wide-open.
sudo can be limited:

[http://aplawrence.com/Basics/sudo.html]("http://aplawrence.com/Basics/sudo.html")

By default, sudo in Ubuntu has 15 minutes(or as least did in the past) before it times out.
But that can be changed using visudo and entering the line:

```
timestamp_timeout=(whatever time you want)
```
to the defaults line.
In these regards sudo is more malleable than root, as security can be severely tightened.

---

### Post by phamhung on 2012-12-31
> **samiux said:**
> Therefore, in my own opinion, you must treat the root account and the first Ubuntu account as the same level.

That's what I feel. Thanks for expressing.
So, with Redhat-based machine, we are protected in two layers, meanwhile in Ubuntu only one, right? Is there anyway to improve security in this ssh access?

---

### Post by samiux on 2012-12-31
> **phamhung said:**
> That's what I feel. Thanks for expressing.
So, with Redhat-based machine, we are protected in two layers, meanwhile in Ubuntu only one, right? Is there anyway to improve security in this ssh access?

As I said before, root account and first Ubuntu account (with root privilege) are the same.  You can say that the first Ubuntu account is the root account.

For SSH access, there are many ways to make it more secure, such as login with key only, fail2ban, disable the root access, and etc.

Samiux

---

### Post by phamhung on 2012-12-31
> **deadflowr said:**
> By default, sudo in Ubuntu has 15 minutes(or as least did in the past) before it times out

I got the time idea. However, once user can get in the machine, 15 minutes or 2 minutes, it doesn't matter. He can also change that settings too.

---

### Post by haqking on 2012-12-31
> **samiux said:**
> As I said before, root account and first Ubuntu account (with root privilege) are the same.  You can say that the first Ubuntu account is the root account.



not quite.  Root is UID 0, first user account is UID 1000.  Hvaing the same privelege does not make them the same account.

> He can also change that settings too.

Course they can, if you dont trust the user then dont put them in sudo group ;-)

---

### Post by snowpine on 2012-12-31
> **phamhung said:**
> That's what I feel. Thanks for expressing.
So, with Redhat-based machine, we are protected in two layers, meanwhile in Ubuntu only one, right? Is there anyway to improve security in this ssh access?

If you tell an untrusted user the password to the root account OR to a sudo/admin user, then you have compromised your security. Best practice to set up a limited-privileges account for the untrusted user, whether you are using Redhat or Ubuntu. 

You have complete control and freedom to change the security settings on the Redhat machine to be identical to Ubuntu, or on the Ubuntu machine to be identical to Redhat. I suggest reading more about security topics here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

If you prefer to use Ubuntu with root password instead of sudo (like the Red Hat default) then simply read here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Professionals debate "root vs sudo" endlessly, there is no definitive answer. :)

---

### Post by samiux on 2012-12-31
> **phamhung said:**
> I got the time idea. However, once user can get in the machine, 15 minutes or 2 minutes, it doesn't matter. He can also change that settings too.

Agreed.  And the attacker already know how to escalate the privilege, so the time limit is not a big deal.

Samiux

---

### Post by phamhung on 2012-12-31
> **haqking said:**
> Course they can, if you dont trust the user then dont put them in sudo group ;-)

Well... I am not mentioning to the trust here. The case here is that somehow, I lost password of the first account, so my machine can be wiped out completely. Meanwhile it's harder in Redhat-based machine, due to root password.

> **snowpine said:**
> If you tell an untrusted user the password to the root account OR to a sudo/admin user, then you have compromised your security. Best practice to set up a limited-privileges account for the untrusted user, whether you are using Redhat or Ubuntu. 

You have complete control and freedom to change the security settings on the Redhat machine to be identical to Ubuntu, or on the Ubuntu machine to be identical to Redhat. I suggest reading more about security topics here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

If you prefer to use Ubuntu with root password instead of sudo (like the Red Hat default) then simply read here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Professionals debate "root vs sudo" endlessly, there is no definitive answer. :)

Again, as posted, I am very new with Ubuntu. So, I am just trying to learn and compare Redhat-based and Ubuntu-based machines :)

---

### Post by samiux on 2012-12-31
> **haqking said:**
> not quite.  Root is UID 0, first user account is UID 1000.  Hvaing the same privelege does not make them the same account.

Agreed.  root has uid 0 while first Ubuntu account has uid 1000.  They seem different.

However, in the view of attacker, they are the same when you can escalate the privilege of the first Ubuntu account, for example :

```
samiux@samiux:/home/samiux:~$sudo -sH
[sudo] password for samiux: 
root@samiux:/home/samiux#

root@samiux:/home/samiux#id
uid=0(root) gid=0(root) group=0(root)
```

Samiux

---

### Post by deadflowr on 2012-12-31
> **phamhung said:**
> I got the time idea. However, once user can get in the machine, 15 minutes or 2 minutes, it doesn't matter. He can also change that settings too.

Set the timeout to 0, and then you'll be prompted for a password every time.

---

### Post by haqking on 2012-12-31
> **phamhung said:**
> Well... I am not mentioning to the trust here. The case here is that somehow, I lost password of the first account, so my machine can be wiped out completely. Meanwhile it's harder in Redhat-based machine, due to root password.



  

Actually in some ways its a little safer.  If you have you lost your accounts password then reset it with root [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

In Redhat if you were doing things as root and lost your password then you would screw things up even more wouldnt you, you can still recover or reset it but often the methods are more long winded ;-)



Peace

---

### Post by samiux on 2012-12-31
> **deadflowr said:**
> Set the timeout to 0, and then you'll be prompted for a password every time.


Not agreed.  If the attacker already know how to escalate the privilege, the prompting for entering password every time is not a big deal.

Samiux

---

### Post by samiux on 2012-12-31
> **haqking said:**
> Actually in some ways its a little safer.  If you have you lost your accounts password then reset it with root [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

In Redhat if you were doing things as root and lost your password then you would screw things up even more wouldnt you, you can still recover or reset it but often the methods are more long winded ;-)



Peace

Linux system without sudoer setup can also boot into the single user mode to reset your root password.

Samiux

---

### Post by haqking on 2012-12-31
> **samiux said:**
> Linux system without sudoer setup can also boot into the single user mode to reset your root password.

Samiux

I know, i never said you couldnt

---

### Post by samiux on 2012-12-31
> **phamhung said:**
> Well... I am not mentioning to the trust here. The case here is that somehow, I lost password of the first account, so my machine can be wiped out completely. Meanwhile it's harder in Redhat-based machine, due to root password.

Not agreed.  As I said before, first Ubuntu account is same as root account.  You can treat they are same.  Linux system that with or without sudoer setup are in the same security situation when the password of the root privilege sudoer account and root account of a non-sudoer system is lost or leaked.

Therefore, strong password for root account and root privilege sudoer account is required and needed.

Samiux

---

