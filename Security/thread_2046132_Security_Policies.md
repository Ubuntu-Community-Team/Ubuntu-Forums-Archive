---
title: "Security Policies"
date: 2012-08-22
forum: Security
---

### Post by Loki57701 on 2012-08-22
I'm trying to setup some security policies on Ubuntu server 12.04.

I've successfully implemented all but the following:

-Failed login attempts: 5
-Lockout time: 30min
-Deny login if no home dir present


The 'solutions' I found on google haven't work.


_Deny login if home directory isn’t present_

Open /etc/login.defs

Change the following:

```
DEFAULT_HOME yes
```

To:

```
DEFAULT_HOME no
```

_Set account lockout policy:_

Add the following line **TO THE TOP** of /etc/pam.d/common-auth 
(order of rules matters).

```
auth required pam_tally.so per_user magic_root onerr=fail
```

_Set the number of allowed attempts to 5, and the lockout time to 30min_

```
faillog –m 3 -l 1800
```


After making the above changes I am still able to attempt a login after 5 failed tries, as well as login using the correct password after those tries - no wait. 

I'm also still able to login if no home directory is present.

Can anyone help me out with this?

---

### Post by SeijiSensei on 2012-08-22
Do you really want just to restrict logins if there is no home directory, or do you want to create users that cannot log in at all?  If the latter, just change their default shells to /bin/false in /etc/passwd.

---

### Post by Loki57701 on 2012-08-22
The security policy I have to comply with says:

"Termination of user login upon a missing home directory must be set."

---

### Post by SeijiSensei on 2012-08-22
> **Loki57701 said:**
> The security policy I have to comply with says:

"Termination of user login upon a missing home directory must be set."

Then set the shells for all users without a home directory to /bin/false.  That will terminate their logins.  Give it a try.

---

### Post by Loki57701 on 2012-08-22
This is intended to be another layer of security. Setting system and non-root accounts to /bin/false is one thing, but I need to deny access if the home dir isn't present for any potential user.

---

### Post by lisati on 2012-08-22
One possibility would be to require users to register and have some kind of verification, possibly with an email containing a link that must be clicked before a home folder is created and registration is complete.

Limiting a user's access to their own home folder, if it exists, can depend on the your choice of software for gaining access.

---

### Post by Loki57701 on 2012-08-23
Im not trying to limit a user to their home folder. I'm simply trying to deny them access if it doesnt exist.

---

### Post by CharlesA on 2012-08-23
I am assuming you mean logging in via SSH?

Why not just set the AllowedUsers setting to whoever you want to have the ability to login.

---

