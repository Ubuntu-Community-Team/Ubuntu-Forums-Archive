---
title: "Is it substantially safer to use a non-administrator account?"
date: 2015-02-21
forum: Security
---

### Post by pfthizzz on 2015-02-21
For a desktop installation, is it substantially safer to use a non-admin account?

When you first install the OS, the account you create will be an administrator by default. Installing apps, making certain system changes, etc, will prompt you for the password to that account. 
Even though this is not the Root account, is this admin account perhaps still too privileged for everyday use? 
Is this admin account, even without password prompted-changes, capable of doing more than a non-admin account?

Thanks

---

### Post by bab1 on 2015-02-21
> **pfthizzz said:**
> For a desktop installation, is it substantially safer to use a non-admin account?

When you first install the OS, the account you create will be an administrator by default. Installing apps, making certain system changes, etc, will prompt you for the password to that account. 
Even though this is not the Root account, is this admin account perhaps still too privileged for everyday use? 
Is this admin account, even without password prompted-changes, capable of doing more than a non-admin account?

Thanks
No, no and no.

That first account is has only one difference between itself and a regular user account.  It is a member of the sudoers group.  That allows the user to have the user account root to act in the users behalf.  When you are installing applications you are invoking sudo and asking root to do the installation.

Only root can administrate the system.  No sudo rights means you can't administrate the system via the root account.

You can read about sudo here: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ian-weisser on 2015-02-21
+1 bab1 is right. 

> **pfthizzz said:**
> Is this admin account, even without password prompted-changes, capable of doing more than a non-admin account?
No. Not one bit more.

---

### Post by maglin2 on 2015-02-23
> **ian-weisser said:**
> +1 bab1 is right. 


No. Not one bit more.

This hasn't quite been my experience with ubuntu 14.04 (Unity).

For example, I can mount the dual booted windows OS partition without being asked for password when logged into the primary account, but if I am logged into a standard account I am asked for the primary account password.

I can install some (but not all) software updates without being asked for password when logged into the primary account, but if I am logged into a standard account I am asked for the primary account password.

---

### Post by deadflowr on 2015-02-23
> I can install some (but not all) software updates without being asked for password when logged into the primary account, but if I am logged into a standard account I am asked for the primary account password.
That's the design of the system.
Those updates you can install without a password prompt are updates to existing packages, and not new packages.
The system admin is already logged in, so no need to prompt for a password, in that case.
If logged in as a non-admin, it'll need to know that an admin approved those updates.
Makes sense to me...

---

### Post by bab1 on 2015-02-23
> For example, I can mount the dual booted windows OS partition without being asked for password when logged into the primary account
This also can be happen due to a configuration setting.  The default is: only root can mount partitions.  See ```
man mount
```

The pertinent section starts with this```
 The non-superuser mounts.
              Normally,  only the superuser can mount filesystems.  However, when fstab con&#8208;
              tains the user option on a line, anybody can mount the corresponding system.


```

---

### Post by maglin2 on 2015-02-23
I wasn't complaining or reporting a bug! 

I was just pointing out that with Unity default configuration there are things that the primary (admin) user can do without password that a standard user can't.

That wasn't the flavour of the responses the OP was getting to his question:

'Is this admin account, even without password prompted-changes, capable of doing more than a non-admin account?'

---

### Post by bab1 on 2015-02-23
Yes, but only via sudo.  Which means root does the work and the admin user must as that account to do so.  Sudo = Switch User and DO.  You are switching to the root user for just that command.

---

