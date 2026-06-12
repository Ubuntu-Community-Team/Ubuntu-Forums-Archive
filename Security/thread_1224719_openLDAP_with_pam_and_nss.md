---
title: "openLDAP with pam and nss"
date: 2009-07-27
forum: Security
---

### Post by matthewboh on 2009-07-27
I've got openLDAP running and installed the pam and nss libraries so it would also control the Linux passwords.  I'm trying to sign onto my server using ssh - but once I enter my username and password, I get

```
WARNING: Your password has expired.
You must change your password now and login again!
Enter login(LDAP) password:
```

Now being a bad security person, I always use the exact same username / password combination and they don't work. 

If a use either nothing (just hit Enter) or if I put in the standard password I get

```
passwd: Authentication information cannot be recovered
passwd: password unchanged
Connection to ubuntu closed
```.

If I enter in some nonsensical string I get

```
LDAP Password incorrect: try again
Enter login(LDAP) password:

```

I tried to use the openLDAP listserv, but I was denied access - they said that it's not an openLDAP issue.  Would it be a pam / nss library issue?  Is there a listserve or forum for that?

However, that is the only root level user on the machine and I have TONS of stuff on it.  How do I fix? 

Thanks

---

