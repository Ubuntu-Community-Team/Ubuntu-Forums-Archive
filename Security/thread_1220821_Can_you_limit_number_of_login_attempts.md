---
title: "Can you limit number of login attempts"
date: 2009-07-23
forum: Security
---

### Post by dave66 on 2009-07-23
Hi,

I have found that through "Login Window preferences" on Ubuntu 8.04 UNR I can set a login in retry delay which is fine, but I can't find any method to lock an account after a number of unsuccessful login attempts.

A customer we are supplying with Netbooks with 8.04 LTS (UNR) has had a Security risk consultant evaluate the security we have set on the netbooks and his only real gripe is that somebody could try continously to crack the password - ironic thing his he specified the password format, guess he's no so confident it's secure!

Does anyone know a way to limit the number of login attempts?

Thanks

---

### Post by dragos2 on 2009-07-23
> **dave66 said:**
> Hi,

I have found that through "Login Window preferences" on Ubuntu 8.04 UNR I can set a login in retry delay which is fine, but I can't find any method to lock an account after a number of unsuccessful login attempts.

A customer we are supplying with Netbooks with 8.04 LTS (UNR) has had a Security risk consultant evaluate the security we have set on the netbooks and his only real gripe is that somebody could try continously to crack the password - ironic thing his he specified the password format, guess he's no so confident it's secure!

Does anyone know a way to limit the number of login attempts?

Thanks

Fast :You need to define a burst rate using iptables for port 22.
Easy: ufw limit 22 on ubuntu 8.10+
Serious: install some scripts designed to take care of this.

---

### Post by dave66 on 2009-07-23
Dragos,

Do you suggestions apply to local logins as well as remote logins? I'm really (at present) only concerned with the user sitting in front of the computer and not remote logins.

Thanks

---

### Post by dragos2 on 2009-07-23
> **dave66 said:**
> Dragos,

Do you suggestions apply to local logins as well as remote logins? I'm really (at present) only concerned with the user sitting in front of the computer and not remote logins.

Thanks

Hmm, then you should try pam, but I can't help you much.

Drop a line if you get it to work.

---

### Post by sisco311 on 2009-07-23
add something like:
```
#  Lock user account after 10 failed attempts
auth required pam_tally.so onerr=fail per_user deny=9 file=/var/log/faillog

```

or

```
# use this to lockout accounts for 10 minutes after 3 failed attempts
auth            required        pam_tally.so deny=2 unlock_time=600 onerr=succeed file=/var/log/faillog

```

to the /etc/pam.d/login file.

for more info, read the man page:
```
man pam_tally
```

---

### Post by reed026 on 2009-07-27
would it be possible that for say 3 incorrect password tries it would wipe the system clean ? :):popcorn:

---

### Post by bodhi.zazen on 2009-07-27
> **reed026 said:**
> would it be possible that for say 3 incorrect password tries it would wipe the system clean ? :):popcorn:
You would have to script it and keep in mind, such wipes take time.

I suggest you skip all this and encrypt your installation.

---

### Post by Harry83 on 2009-07-27
> **dave66 said:**
> Hi,

I have found that through "Login Window preferences" on Ubuntu 8.04 UNR I can set a login in retry delay which is fine, but I can't find any method to lock an account after a number of unsuccessful login attempts.

A customer we are supplying with Netbooks with 8.04 LTS (UNR) has had a Security risk consultant evaluate the security we have set on the netbooks and his only real gripe is that somebody could try continously to crack the password - ironic thing his he specified the password format, guess he's no so confident it's secure!

Does anyone know a way to limit the number of login attempts?

Thanks


It depends on the site mate.

Regards

Harry

---

### Post by dave66 on 2009-08-05
> **Harry83 said:**
> It depends on the site mate.

Regards

Harry

Harry,

I think we are talking at crossed purposes, I'm talking about a local login to the PC and not an FTP or other network login.

David

---

