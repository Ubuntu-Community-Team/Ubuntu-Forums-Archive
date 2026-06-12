---
title: "Is Tor/Privoxy setup the same in Jaunty?"
date: 2009-08-06
forum: Security
---

### Post by zer010 on 2009-08-06
I have read the setup posts for Tor/Privoxy, but they are for older versions of Ubuntu.  I have followed them to the letter, and have had problems with it working.  Just wanted to know if setup or config is any different with Jaunty, or newer kernels.  If I create a new User account to use Tor/Priv, and it doesn't work (or I don't want it anymore), will deleteing the "test" User account also get rid of Tor/Priv? If not how would I remove Tor/Priv? Any help would greatly be appreciated! :)

---

### Post by cdenley on 2009-08-06
> **zer010 said:**
> I have read the setup posts for Tor/Privoxy, but they are for older versions of Ubuntu.  I have followed them to the letter, and have had problems with it working.  Just wanted to know if setup or config is any different with Jaunty, or newer kernels.  If I create a new User account to use Tor/Priv, and it doesn't work (or I don't want it anymore), will deleteing the "test" User account also get rid of Tor/Priv? If not how would I remove Tor/Priv? Any help would greatly be appreciated! :)

Packages are not installed on a per-user basis, they are global. If you want to remove them, you must do so with a package manager as root.
```

sudo apt-get remove tor privoxy

```

I believe the most current version now uses socks5, whereas guides for the older version probably told you to configure a socks4a proxy. Also, tor used to be in the repos, but isn't any longer, I believe because it wasn't maintained well.

---

### Post by zer010 on 2009-08-08
Thanks! I'll take the SOCKS 5 into consideration. Thanks for the removal code.

---

