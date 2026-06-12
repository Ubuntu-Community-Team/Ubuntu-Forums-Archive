---
title: "Password and Keys Security Issue?"
date: 2012-03-18
forum: Security
---

### Post by spikoley on 2012-03-18
In 11.10, when you go to Passwords and Keys the default setting allows you to access passwords.  

I would think by default you should be prompted for your password when opening Passwords and Keys.  If I let a friend on my computer they could go straight to Passwords and Keys to access my passwords.

This seems like a security risk to me.  Am I right or am I missing something?

---

### Post by Ms. Daisy on 2012-03-18
You could let your friend use a "guest" account instead of your account.  I believe it's limited and wouldn't be able to see the passwords & keys (but you should check to be certain).

---

### Post by spikoley on 2012-03-18
Using the Guest account is an option to avoid this issue, but that is not my point.

This is a security risk!  Anybody stepping away from their computer for a minute is vulnerable.  Somebody can access your passwords in under a minute!  You should be prompted for your password first.

This is a serious security risk unless I am missing something.

---

### Post by Ms. Daisy on 2012-03-18
This discussion has actually come up several times.  See this thread for details

[http://ubuntuforums.org/showthread.php?t=1931670](http://ubuntuforums.org/showthread.php?t=1931670)

But the crux of the matter is physical access is root access.

---

### Post by haqking on 2012-03-18
> **spikoley said:**
> Using the Guest account is an option to avoid this issue, but that is not my point.

This is a security risk!  Anybody stepping away from their computer for a minute is vulnerable.  Somebody can access your passwords in under a minute!  You should be prompted for your password first.

This is a serious security risk unless I am missing something.

the security issue is you letting someone use your account or not securing your machine when away from it.

Physical access is root access

This is all security basics and common sense


Cheers

---

### Post by spikoley on 2012-03-18
> **Ms. Daisy said:**
> This discussion has actually come up several times.  See this thread for details

[http://ubuntuforums.org/showthread.php?t=1931670](http://ubuntuforums.org/showthread.php?t=1931670)

But the crux of the matter is physical access is root access.

That is a different issue.  I would agree with you if this issue was the same as the one in the link.

> **haqking said:**
> the security issue is you letting someone use your account or not securing your machine when away from it.

Physical access is root access

This is all security basics and common sense


Cheers

Then why even have sudo?  That line of think is an argument against sudo.  This is a sudo issue.

Do you think having a lock on User Accounts is a bad idea?  Currently when you go into User Accounts it requires a password to unlock it.  This issue is exactly the same.  My argument is Passwords and Keys should be treated the same as User Accounts when it comes to security.

---

### Post by Ms. Daisy on 2012-03-18
If it's a serious security risk then you have the option to:  1) log out,  2) hibernate/suspend and require a password to resume. 3) Let a friend use guest and he won't have access to password files.

When you're logged into your machine and you simply walk away leaving it running, I don't understand how you could secure the entire system- not just the password file.

---

### Post by spikoley on 2012-03-18
> **Ms. Daisy said:**
> If it's a serious security risk then you have the option to:  1) log out,  2) hibernate/suspend and require a password to resume. 3) Let a friend use guest and he won't have access to password files.

When you're logged into your machine and you simply walk away leaving it running, I don't understand how you could secure the entire system- not just the password file.

Then why have a lock on User Accounts?  It makes no sense to have a lock on User Accounts and not Passwords and Keys.  Shouldn't Ubuntu at least be consistent on how it treats similar applications?

---

### Post by haqking on 2012-03-18
> **spikoley said:**
> Then why have a lock on User Accounts?  It makes no sense to have a lock on User Accounts and not Passwords and Keys.  Shouldn't Ubuntu at least be consistent on how it treats similar applications?

it is not Ubuntu's application.

it is seahorse/GNU privacy guard

and if you give your car keys to your friend and they crash your car is it then the car manufacturers fault that the car was allowed to be driven by the person with the keys ? or yours for giving the keys to someone ?

Physical access is root access.

Do you want a password prompt for every action ? or are you happy to allow your friend to access your documents, spreadsheets, emails but just not your passwords ? after all why do they need your passwords ? you have given them access to everything anyways ;-)

Peace

---

### Post by spikoley on 2012-03-18
So why have sudo or a lock on any application?  I've always thought it was there for security.

---

### Post by winh8r on 2012-03-18
If I may quote haqking from another thread he posted in:

> System security is not a product
System security is not a state.

System security is a process and ongoing and the responsibility of the User/Admin.

The minute you, as the user or the admin allows **anyone** unsupervised physical access to your machine, it is effectively compromised.

It does not matter what measures are in place in terms of software, passwords,keyrings. All it takes is a live cd, and your data is instantly accessible.

The sudo command is primarily about restricting permissions to carry out various tasks and actions whilst running the system. It is not in itself a robust security measure against anyone other than the uninitiated user.

Security is in the hands of the user/owner at all times and how they choose to deal with that responsibility is what determines the integrity of the data held on the machine (s)

---

### Post by Ms. Daisy on 2012-03-18
To put what winh8r & haqking said another way:

The purpose of sudo is so that you don't have to run as root. When you give your sudo password you temporarily elevate your permissions to allow whatever action you choose. When you use sudo, you have to knowingly allow  processes/programs that could potentially harm your computer. Nothing can just run without your knowledge or without you specifically allowing it.  Sudo is there for security in that way. Read the official documentation:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Physical security of your computer is a different beast, and sudo has nothing to do with physical security.  When you walk away from your computer and leave it running, yeah, someone can sit down and peek at your passwords.  But they could also copy your data onto a flash drive.  Then they could rm -rf your drive completely erasing everything. You don't need sudo privileges to do that.  So in my mind, worrying about the password & keys file is kind of like worrying about a leaking faucet on the Titanic.

---

