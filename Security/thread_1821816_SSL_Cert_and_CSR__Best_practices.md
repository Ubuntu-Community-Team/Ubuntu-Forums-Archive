---
title: "SSL Cert and CSR:  Best practices?"
date: 2011-08-09
forum: Security
---

### Post by sneakyimp on 2011-08-09
I'm about to create a CSR and was reading this page in the Ubuntu docs:
[https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html)

A couple of things:
* There's no date on the article.  The documentation needs DATES because this information gets out of date! Check MySQL docs, for instance -- they are organized by version.
* The instructions for generating a cert only specify 2048 bits.  I believe that's kind of out of date?  The verisign site has big red warnings saying you need 2048 if you want your cert to last past 2013 -- and that article is 4 years old!
* The instructions are confusing when discussing the passphrase.  We enter a passphrase only to remove it immediately.  We need some clarity here.  Why do this?

Can anyone help me to understand the current best practices for generating an HTTPS cert for apache and/or mail access?

---

### Post by dinu90 on 2011-08-10
Here's a good howto about certificate generation:
[http://www.akadia.com/services/ssh_test_certificate.html](http://www.akadia.com/services/ssh_test_certificate.html)

The 2048 bit encryption is the one preferred these days

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by sneakyimp on 2011-08-10
Thanks for your response. I've already created my key, a csr, and a self-signed cert.  I'm sort of wondering about some more specific issues that how to simply create it:
* Does the US Government impose any restrictions on the size of one's encryption key? I know that the US Government [restricts](http://www.bis.doc.gov/encryption/) the export of encryption technology, purportedly as a matter of national security. That document I linked is not particularly helpful.
* Hasn't DES been superceded by AES? I've seen a variety of links talking about threats to DES and that DES3 is a band aid of sorts.
* Is there any risk if some bad person obtains a copy of my certificate signing request? If so, what is the nature of this risk?

And one other question:
* Must I revoke an existing certificate for [www.mydomain.com](www.mydomain.com) before obtaining a new one?

---

### Post by MidSpeck on 2011-08-10
Answering just a few of your questions:

> **sneakyimp said:**
> * Hasn't DES been superceded by AES? I've seen a variety of links talking about threats to DES and that DES3 is a band aid of sorts.
Yes, I'd use AES over 3DES.  DES is only a 56 bit key, so avoid that for sure these days.

> **sneakyimp said:**
> * Is there any risk if some bad person obtains a copy of my certificate signing request? If so, what is the nature of this risk?
Not really.  The certificate signing request doesn't contain your private key, which is the part you need to keep protected.  Your CSR will have much of the same information as your public certificate itself.

> **sneakyimp said:**
> * Must I revoke an existing certificate for [www.mydomain.com](www.mydomain.com) before obtaining a new one?
No, you can have multiple certificates valid at the same time.  Revoking is generally used when someone steals your private key.

---

### Post by unspawn on 2011-08-11
> **sneakyimp said:**
> Must I revoke an existing certificate for [www.mydomain.com](www.mydomain.com) before obtaining a new one?
In your case, that is if we're talking about a certain thread elsewhere, the meaning of "must" changes significantly IMO: 0) if your private key was left on the system unprotected and you 1) can not determine if it could have been siphoned of said system and 2) given your intention to provide paying customers with a safe and trustworthy environment to conduct business in I would argue against not revoking that certificate.

---

### Post by NathanBrauer on 2011-09-20
> **sneakyimp said:**
> The documentation needs DATES because this information gets out of date! Check MySQL docs, for instance -- they are organized by version.

lol

You do realize that the link you posted shows:
[https://help.ubuntu.com/**_10.04_**/server...-security.html]("https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html")

---

### Post by sneakyimp on 2011-09-21
OK yes I see now that the version is in the URL (and also listed quite small at the top) but there is no *date* on the article and it only uses 1024-bit keys which makes me think it's out of date.

---

