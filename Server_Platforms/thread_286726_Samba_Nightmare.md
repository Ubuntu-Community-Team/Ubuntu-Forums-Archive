---
title: "Samba Nightmare"
date: 2006-10-28
forum: Server Platforms
---

### Post by Jeeevs2001 on 2006-10-28
Hello, (again!) 

I am trying to add a new samba user and keep getting an error: 

NULL guest account!?!?
Failed to initialise SAM_ACCOUNT for user *****. Does this user exist in the UNIX password database ?
Failed to modify password entry for user ******

I have tried this through webmin and through ssh and can not seem to make it work. 

What am I missing? 

Thanks in advance 

Jeeves

---

### Post by Iowan on 2006-10-29
How are you trying to add the user, and...
> Does this user exist in the UNIX password database ?

---

### Post by Jeeevs2001 on 2006-10-30
Hi Iowan, 

I have tried two ways of adding the user, through Webmin and with the command line. 

With webmin I try to add the user to the general user list (Users and Groups) and tick the box to 'create the user in other modules' (or something like that) and it causes the above error, however it does create the user in the general users list. 

Its the same with the command line really, add the new user (useradd) then try to allocate a samba password (eg smbpasswd -a *****) and it just gives me the same error. But again, when looking in the 'users and groups' module in webmin the new user is listed. 

I assume that adding the user to this list (Users and Groups) is adding them to the UNIX password database? 

Any idea where the problem is?

Jeeves

---

### Post by unless on 2006-10-30
The first thing I'd check is whether the user was added to the Unix system. Let's say the username you added was bob. At the command line: 

```
grep bob /etc/passwd
```

If a line returns, the user has a local (system) account.

Then check to see if the user exists in the Samba database:

```
pdbedit -v -u bob
```

Does the user exist at both of these levels?  If so, have you actually tried to log in to the account? 

If you're still stuck, it may help debugging to post the output of pdbedit here (if pdbedit gave you any info).

---

