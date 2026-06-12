---
title: "OpenSSL Patched?"
date: 2007-07-10
forum: Server Platforms
---

### Post by rubedog on 2007-07-10
Hello all,

I'm pretty new to the Linux world and I'm trying to figure something out.

**BACKGROUND:**
I have a Dell Poweredge 2650 that I installed Ubuntu Edgy Eft on.  Once installed I did and apt-get install for Apache2 and also for libapache-mod-ssl (this is what I needed for mod_ssl).  What I think I've learned since doing this is that mod_ssl uses OpenSSL and so OpenSSL was installed along with everything else.

When I started apache2, I would look at the error.log file and find this line:
Apache/2.0.55 (Ubuntu) mod_ssl/2.0.55 **OpenSSL/0.9.8b** configured

After a security scan from my security people to allow access to this server, they came back and said that OpenSSL 0.9.8c and older had several vulnerabilities and that they wouldn't allow access to my server until OpenSSL was updated to 0.9.8d or 0.9.8e.

I eventually did an apt-get dist-upgrade to upgrade from Edgy to Feisty.  By doing so, I also upgraded Apache, mod_ssl, and OpenSSL.  However, my OpenSSL is still too old.  Here's what error.log shows now:
Apache/2.2.3 (Ubuntu) mod_ssl/2.2.3 **OpenSSL/0.9.8c** configured

I recently spoke with someone who knows Linux better than I do and he said that Ubuntu may have patched the vulnerabililties in 0.9.8c and that I may not need to actually upgrade to 0.9.8d or 0.9.8e.

**QUESTION:** 
Does anyone know if Ubuntu patched OpenSSL 0.9.8c for security vulnerabilities.  

**EXTRA INFO:**
Here's the list of vulnerabilities my security people came up with:

CVE:
   CVE-2006-3738 ([http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-3738](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-3738))
   - Buffer overflow in the SSL_get_shared_ciphers function in
   OpenSSL 0.9.7 before 0.9.7l, 0.9.8 before 0.9.8d, and earlier
   versions has unspecified impact and remote attack vectors involving
   a long list of ciphers.

   CVE-2006-2937 ([http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-2937](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-2937))
   - OpenSSL 0.9.7 before 0.9.7l and 0.9.8 before 0.9.8d allows
   remote attackers to cause a denial of service (infinite loop
   and memory consumption) via malformed ASN.1 structures that
   trigger an improperly handled error condition.

   CVE-2006-2940 ([http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-2940](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-2940))
   - OpenSSL 0.9.7 before 0.9.7l, 0.9.8 before 0.9.8d, and earlier
   versions allows attackers to cause a denial of service (CPU
   consumption) via parasitic public keys with large (1) "public
   exponent" or (2) "public modulus" values in X.509 certificates
   that require extra time to process when using RSA signature
   verification.

   CVE-2006-4343 ([http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4343](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-4343))
   - The get_server_hello function in the SSLv2 client code in
   OpenSSL 0.9.7 before 0.9.7l, 0.9.8 before 0.9.8d, and earlier
   versions allows remote servers to cause a denial of service
   (client crash) via unknown vectors that trigger a null pointer
   dereference.

Thanks for all your help!

---

### Post by cdenley on 2007-07-10
[http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_0.9.8c-4build1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_0.9.8c-4build1/changelog)
> 
openssl (0.9.8c-2) unstable; urgency=high

  * Fix security vulnerabilities (CVE-2006-2937, CVE-2006-2940,
    CVE-2006-3738, CVE-2006-4343).  Urgency set to high.

 -- Kurt Roeckx <kurt@roeckx.be>  Wed, 27 Sep 2006 21:24:55 +0000


---

### Post by rubedog on 2007-07-10
Thank you so much!!!!!

---

### Post by craigp84 on 2007-07-10
Yeah fixed in edgy too - [http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_0.9.8b-2ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_0.9.8b-2ubuntu2/changelog)

```
openssl (0.9.8b-2ubuntu2) edgy; urgency=low

  * SECURITY UPDATE: Remote arbitrary code execution, remote DoS.
  * crypto/asn1/tasn_dec.c, asn1_d2i_ex_primitive(): Initialize 'ret' to avoid
    an infinite loop in some circumstances. [CVE-2006-2937]
  * ssl/ssl_lib.c, SSL_get_shared_ciphers(): Fix len comparison to correctly
    handle invalid long cipher list strings. [CVE-2006-3738]
  * ssl/s2_clnt.c, get_server_hello(): Check for NULL session certificate to
    avoid client crash with malicious server responses. [CVE-2006-4343]
  * Certain types of public key could take disproportionate amounts of time to
    process. Apply patch from Bodo Moeller to impose limits to public key type
    values (similar to Mozilla's libnss). Fixes CPU usage/memory DoS. [CVE-2006-2940]
  * Updated patch in previous package version to fix a few corner-case
    regressions. (This reverts the changes to rsa_eay.c/rsa.h/rsa_err.c, which
    were determined to not be necessary).

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 27 Sep 2006 12:16:12 +0200
```

-c

---

