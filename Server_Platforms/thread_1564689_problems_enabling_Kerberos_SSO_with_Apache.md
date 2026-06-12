---
title: "problems enabling Kerberos SSO with Apache"
date: 2010-08-30
forum: Server Platforms
---

### Post by tr333 on 2010-08-30
I successfully used likewise-open5 on Lucid to connect an Ubuntu-Server machine to an AD domain.

I followed the instructions at [http://likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#apachesso](http://likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#apachesso) for setting up Kerberos SSO with Apache on Ubuntu 10.04.  When I try to access the protected page using Internet Explorer, it gives me a 500 Internal Server Error and apache error log says:
> gss_acquire_cred() failed: Unspecified GSS failure.  Minor code may provide more information (Key table entry not found)

Running “sudo klist -kt /etc/apache2/http.ktb” returns:
```
Keytab name: WRFILE:/etc/apache2/http.ktb
KVNO Timestamp         Principal
---- ----------------- --------------------------------------------------------
   3 01/01/70 10:00:00 HTTP/myserver.mydomain.com@MYDOMAIN.COM
```

Can anyone explain whats gone wrong?

---

### Post by tyman00 on 2011-09-21
Sorry to resurrect such an old thread. I am curious if you were able to solve this issue and how you did it?

I'm running into the exact same issue you described and I'm at my wits end trying to solve it.

---

### Post by tr333 on 2011-10-28
I finally got this working.  I gave up on LikewiseOpen and used CentrifyDC instead.  No fiddling required.  Appeared to work OOB after connecting to the AD domain.  I'll post a sample apache config when I can find it.

---

### Post by tyman00 on 2011-11-03
I gave up on Kerberos SSO and went with the Winbind option for Apache/NTLM SSO

---

### Post by tr333 on 2011-11-06
Apache conf:
```
<Directory /var/www/kerberos/>
AuthType Kerberos
AuthName "Kerberos Auth"
KrbServiceName http
require valid-user
</Directory>

```

This should "just work" OOB if you connect to AD via CentrifyDC.

---

