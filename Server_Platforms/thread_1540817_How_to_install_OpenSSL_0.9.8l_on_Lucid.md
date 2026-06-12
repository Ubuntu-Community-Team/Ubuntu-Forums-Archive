---
title: "How to install OpenSSL 0.9.8l on Lucid"
date: 2010-07-28
forum: Server Platforms
---

### Post by Greg B on 2010-07-28
I'd like to upgrade libssl to 0.9.8l version on my Lucid-based server, because of CVE-2009-3555 - they say that 0.9.8l disables SSL renegotiation, fixing the security issue. But there is no 0.9.8l in Ubuntu repositories - only 0.9.8k-7 is available. Can anybody help me, how can I upgrade this library? BTW. it is really strange why such significant security fix is not available in Ubuntu repositories... any clue why it is not available?

---

### Post by cdenley on 2010-07-28
Ubuntu rarely releases an a newer version of a package for a version of ubuntu which is already released. Security patches are backported. The patch you mention was added to lucid in version 0.9.8k-6. However, it was disabled in 0.9.8k-7ubuntu1. I believe this was because some software relies on re-negotiation, and the patch broke it. Apache as of 2.2.14-2, as well as possibly other server software which uses SSL but doesn't rely on re-negotiation, disables re-negotiation to eliminate the vulnerability.

---

### Post by Greg B on 2010-07-28
But it means, that if I downgrade to k-6, renegotiation should be disabled, right?

---

### Post by Greg B on 2010-07-28
Unfortunately, k-6 version is no longer available in repositories :(

---

### Post by cdenley on 2010-07-28
> **Greg B said:**
> But it means, that if I downgrade to k-6, renegotiation should be disabled, right?

Hypothetically, if you managed to find outdated packages and downgrade without breaking dependencies, then yes renegotiation would be disabled for anything using openssl, including the software which requires it. However, you would lose other security patches which have been added since then.

What software which uses openssl are you concerned about?

---

### Post by Greg B on 2010-07-28
I run Tomcat server, which handles HTTPs using APR/OpenSSL. When I open the page served by this server in Opera 10.60, there is a warning "this page doesn't support secure SSL renegotiation, admin should upgrade the server" or something like this. 
According to Tomcat docs, everything is setup correctly, so the only suspicious part is libssl version - if it was in 0.9.8l than perhaps the warning would not be there. 
(there is not other public server running on this system, so I guess renegotation could be safely turned off - but of course I can be wrong about it)

---

### Post by cdenley on 2010-07-28
What version of tomcat are you using? Is it from the repos? I believe versions >=5.5.29 or >=6.0.21 should disallow renegotiation by default.

[http://tomcat.apache.org/security-5.html](http://tomcat.apache.org/security-5.html)
[http://tomcat.apache.org/security-6.html](http://tomcat.apache.org/security-6.html)

---

### Post by Greg B on 2010-07-29
Yes, it is Tomcat from repos, 6.0.24. That's why I say that according to Tomcat docs, everything looks ok, but Opera still claims the server is not protected. The only missing point is OpenSSL library version, based on this description of APR vulnerabilities: [http://tomcat.apache.org/security-native.html](http://tomcat.apache.org/security-native.html).
On the other hand, I don't know what's the Opera's algorithm of deciding on server security - maybe it is buggy somehow? Perhaps I should ask on Opera forums.
Anywawy, they say in all docs that OpenSSL 0.9.8m fixes the problem without disabling renegotation. Do you know when this version will be available in Ubuntu repos?

---

### Post by Bachstelze on 2010-07-29
> **Greg B said:**
> 
Anywawy, they say in all docs that OpenSSL 0.9.8m fixes the problem without disabling renegotation. Do you know when this version will be available in Ubuntu repos?

Maverick will apparently have 0.9.8o.  And yes, Opera is obviously being stupid, as usual.

---

### Post by Greg B on 2010-07-29
Ah ok, thanks for help :)

---

