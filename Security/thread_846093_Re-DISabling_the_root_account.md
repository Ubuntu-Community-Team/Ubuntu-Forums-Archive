---
title: "Re-DISabling the root account"
date: 2008-07-01
forum: Security
---

### Post by meganox on 2008-07-01
I [read]("https://help.ubuntu.com/community/RootSudo") that the proper way to disable a root account that has been enabled is

# sudo passwd -l root

however this locks the account but does not remove the password, and breaks install scripts that add users and create directories in restricted ares (such as apt-get install hobbit).

# sudo passwd -u root
# sudo passwd -d root

enables the account then deletes the password, preventing logins.  Hobbit installed with no errors once this was done.

I believe the root account should be unlocked and with no password: sudo passwd -l root does not achieve this (locking works by creating an invalid password).

Is my security back to the way it was before I enabled the root account?

Why did I do such a stupid and unnecessary thing in the first place?  (You don't have to answer this one ;))

---

### Post by cdenley on 2008-07-01
I remember seeing that, too. I think the proper way should be
```

sudo usermod -p ! root

```
The -l option inserts a "!" before the password hash so the result of any crypt function can't match it. This is so it can be re-enabled, keeping the original password. However, it also sets the account to expired, which is probably what was causing your problems. The -d option just clears the password entirely. **This allows you to login to the terminal as root without providing a password!** I think the way ubuntu is configured by default is with root's password hash set to "!" with the account not expired. The command above should accomplish this.

---

### Post by Wickedone on 2008-09-19
Is there any command that can be used to verify that root is disabled?  

I disabled root using ```
sudo passwd -l root
``` which resulted in cron jobs failing.  Thus I ended up on this thread and re-enabled the root user and followed cdenely advice about ```
sudo usermod -p ! root
``` so where does that leave the root account?  

Console logins seem disabled, but I have no way of verifying it across every possible way to login.  

I would prefer cron jobs not running as root.

---

### Post by cdenley on 2008-09-20
> **Wickedone said:**
> Is there any command that can be used to verify that root is disabled?  

I disabled root using ```
sudo passwd -l root
``` which resulted in cron jobs failing.  Thus I ended up on this thread and re-enabled the root user and followed cdenely advice about ```
sudo usermod -p ! root
``` so where does that leave the root account?  

Console logins seem disabled, but I have no way of verifying it across every possible way to login.  

I would prefer cron jobs not running as root.

```

sudo getent shadow root|cut -d : -f 2

```
This command will print the password hash for your root password. If it starts with "!", then there is no way for a user to authenticate since that isn't a valid hash. The regular way of disabling a user actually marks a user as disabled without touching their password hash, but this causes the problems you were experiencing. Another method adds a ! before the existing password hash, so it can be unlocked without the password being set. The way ubuntu comes is to have ! as the entire password hash. This is what the command I gave accomplishes. There is no password that they will be able to login with, but sudo will work fine since besides the hash, there is nothing unusual about the root account.

---

### Post by bodhi.zazen on 2008-09-20
There are 3 issues here :

1. How shadow handles passwords and locking accounts.

[indent]See cdenley's post and man passwd[/indent]

2. Ubuntu patches sudo to allow locking the root account.

3. Most important, there is a bug in sudo / locking accounts. The bug was reported against Debian and thus also affects Ubuntu.

I do not have the original link to the dibian bug report, but I did find this :

[https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755)

---

### Post by Wickedone on 2008-09-20
> **cdenley said:**
> ```

sudo getent shadow root|cut -d : -f 2

```


Would this command be useful in determining if root has been enabled?  (IE the reason I disabled root was I was not certain if it had been enabled and didn't know a way to check to see if root was enabled.)

If it is would it be useful to check this if one suspects a system might have been compromised?

---

### Post by cdenley on 2008-09-20
> **Wickedone said:**
> Would this command be useful in determining if root has been enabled?  (IE the reason I disabled root was I was not certain if it had been enabled and didn't know a way to check to see if root was enabled.)

If it is would it be useful to check this if one suspects a system might have been compromised?

I suppose. As I said, that output is the accounts password hash. If the hash begins with a "!", then there is no way to authenticate as that user. If the hash does not begin with a "!", then it probably is a valid hash, and someone can authenticate as that user. If the user has a valid hash, that doesn't necessarily mean they haven't been disabled, though. If the hash is empty, then the user doesn't have to enter a password (huge security problem). Is it just me, or do I keep repeating this?

Yes, it can be used to determine if the account has been enabled (output isn't "!").

Yes, I suppose if someone suspected their system was compromised, they could check the output of that command. An attacker can't change the hash unless they already have root, but changing the password may give the attacker easier access in the future.

---

### Post by tarun.winlin on 2008-09-21
I have been using that workaround for some time now & that works fine.

---

### Post by Wickedone on 2008-09-21
> **cdenley said:**
> Is it just me, or do I keep repeating this?

Sorry, didn't really mean for you to repeat yourself.  Just wanted to confirm that I understood you and that what I intend to use the command for is valid.

Thanks for your help.

---

