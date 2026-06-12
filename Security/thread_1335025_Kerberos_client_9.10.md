---
title: "Kerberos client 9.10"
date: 2009-11-23
forum: Security
---

### Post by bartin on 2009-11-23
Hi 
After upgrading to 9.10. I'm having problems using kerberos against a Microsoft AD. Authentication works fine, if the password is valid. If I enter a wrong password the kerberos client tries 4 times in rapid succession with the wrong password. 
It seems like the client is not honouring KRB5KDC_ERR_PREAUTH_FAILED.
Now I'm just wondering if this is a feature or a bug? I don't know enough about kerberos to know if this behaviour is by design.

/Bjoern

PS Relevant pkg information:
ii  krb5-clients         1.7dfsg~beta3-1  
ii  krb5-config         1.23 
ii  krb5-doc             1.7dfsg~beta3-1
ii  krb5-user            1.7dfsg~beta3-1
ii  libgssapi-krb5-2  1.7dfsg~beta3-1
ii  libkrb5-3            1.7dfsg~beta3-1
ii  libkrb5support0  1.7dfsg~beta3-1
ii  libpam-krb5       3.15-1

---

### Post by Lars Noodén on 2009-11-25
Microsoft has a broken implementation of kerberos, which does not play nice with others.  

[http://brianlivingston.com/windowmanager/archive/articles/op/xml/00/05/29/000529oplivingston.xml.html](http://brianlivingston.com/windowmanager/archive/articles/op/xml/00/05/29/000529oplivingston.xml.html)

Your client is fine.

---

### Post by bartin on 2009-11-27
I'm pretty sure that, that's not the problem I'm experiencing. This is the first time I've seen this kind of behaviour on a Linux host. I've SLES and FreeBSD working fine against the same AD.

/Bjoern

BTW It was working fine with 9.04

---

