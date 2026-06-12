---
title: "Root Certificates: Can someone explain?"
date: 2011-02-20
forum: Security
---

### Post by LepeKaname on 2011-02-20
Which are the default trusted root certificates in Java 1.4?

Someone could explain how can a 4096bit certificate be installed in Java 1.4? (as it seems to produce an error).

Thank you.

(Sorry for the misleading title, I was not able to re-edited it)

---

### Post by LepeKaname on 2011-02-20
In order to read which root certificates are supported in Java 1.4, I downloaded the source code and typed:

```
keytool -keystore ./jre/lib/security/cacerts -v -list
```

Now, my question is other... if I'm not able to import a 4096bit key, then how can I update cacerts in other way?

---

### Post by LepeKaname on 2011-02-21
For those interested, this is how it can be fixed:

[http://epp.ph.unimelb.edu.au/twiki/bin/view/EPPGrid/AusCAJava14](http://epp.ph.unimelb.edu.au/twiki/bin/view/EPPGrid/AusCAJava14)

):P

---

