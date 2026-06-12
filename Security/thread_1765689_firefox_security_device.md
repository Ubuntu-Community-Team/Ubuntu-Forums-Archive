---
title: "firefox security device"
date: 2011-05-23
forum: Security
---

### Post by fieldyweb on 2011-05-23
I'm hoping someone will want to get thier teeth into this, if not, if i find an answer, as always i will update this post.

Within Firefox 3.6 (and older versions) It is possible to load a security device such as a token Edit -> Preferences -> Advanced -> Encryption -> Security Devices

This allows you to load a smartcard or token and use this as the authentication device for websites and services such as Citrix.

I understand i can be done using the GUI, and i also know that the results of the action seem to be held in secmod.db however can anyone point me in a way of doing this from either bash or perl?

I have potentially 1000 users who may or may not need this done, and need a way of doing it from a command line script remotely...

---

### Post by emiller12345 on 2011-05-23
A 5 second Google search (New PKCS Module firefox cli) yielded info on a tool called "modutil"
 [http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html](http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html)

it looks like it might be loadable by
```

sudo apt-get install libnss3-tools

```

I don't know if it works for what you need it to do or not

---

### Post by fieldyweb on 2011-05-23
Ok, yes, i did see that page, and i might have read it wrong, so i'll take the "5 seconds on google" hot for now, i'll try this in the morning with a DoD CAC and see if it imports it.

---

