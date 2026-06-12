---
title: "Forged CA certificate in Firefox 3.6"
date: 2010-03-25
forum: Security
---

### Post by bluelamp999 on 2010-03-25
Having read how a private company is providing governments (and probably criminals) with a box that can listen in on SSL traffic by the use of forged CA certificates - [http://www.wired.com/threatlevel/2010/03/packet-forensics/](http://www.wired.com/threatlevel/2010/03/packet-forensics/) 

It turns out there's already a forged certificate in Firefox 3.6.

Go to Edit>Preferences>Advanced>Encryption>View Certificates and look for 'Equifax Secure Inc.' - You should see a proof-of-concept rogue certificate called 'MD5 Collisions Inc.' and a link to phreedom.org which explains the method used to generate it.

That little lock doesn't necessarily mean that you're safe...

---

### Post by cdenley on 2010-03-25
The fact that SSL relies on the trusted CA's only issuing certificates to the actual owner of the domain is nothing new. I wonder if the purpose of the devices are specifically for fake certificates issued by a CA, or probably more likely that the product was intended to be used with self-signed certificates.

The forged certificate in firefox is unrelated. I'm pretty sure the reason why it is in firefox is because it is untrusted by default. Firefox ensures that the CA certicate cannot be used since it has been compromised.

---

### Post by rookcifer on 2010-03-25
As [Matt Blaze says]("http://www.crypto.com/blog"), the whole CA model is broken.  The whole system needs to be scraped and redesigned.

This is why I prefer GPG.  That way I can only sign keys where I have met the person who owns the key.  Of course, GPG doesn't do much good for http encrption.

---

### Post by OpSecShellshock on 2010-03-26
Well no, surely there's nothing wrong with the same private organization registering the most popular TLDs, maintaining more than one of the tiny number of root name servers in the world, *and* acting as a major CA. Separation of duties and wide distribution of potential failure points is for the little people, dudes.

---

### Post by galfly on 2010-08-10
This is exactly why we shouldn't let the CA cartels handle web of trust.

Of course there are other alternatives: Use monkeysphere!

```


aptitude install monkeysphere

```

---

