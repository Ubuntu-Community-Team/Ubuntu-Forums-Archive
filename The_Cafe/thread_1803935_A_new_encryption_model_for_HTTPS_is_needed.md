---
title: "A new encryption model for HTTPS is needed"
date: 2011-07-14
forum: The Cafe
---

### Post by TimeSpacial on 2011-07-14
Who thinks certificates need to be dropped with the HTTPS model?

When I SSH to another box, no 3rd party certificate is used.. so encryption can be achieved without them.

This would be good because it would mean encryption can be achieved without having to pay money to the CA crooks.

Who agrees?

---

### Post by ve4cib on 2011-07-14
The certificates -- as I understand them -- are to ensure that the public key of the server has not been compromised.

You'll note that when you SSH into a server for the first time it asks you to confirm the RSA fingerprint of the server.  This is to ensure that you are not subject to man-in-the-middle attacks.

The HTTPS certificates serve basically the same purpose; they're a way of confirming that the server's key really does belong to the server, and not some malicious third-party.

Certificates are not essential, but some mechanism of ensuring the validity of the public keys being presented to you is.  If you can come up with a sane, cost-effective, easy-to-implement alternative to CA certificates I'm all ears.  But simply saying "Certificates should be scrapped!" without presenting a viable alternative is nonsense.

---

### Post by Bachstelze on 2011-07-14
What you describe can already be achieved with self-signed certificates.  As ve4cib pointed out, when you connect to a machine via SSH for the first time, it asks you to confirm the fingerprint of the server: you are supposed to ask the server owner what the fingerprint is, and compare it to the one you get, to ensure that you are indeed talking to the correct server.  Likewise, when you connect to a website via HTTPS for the first time and the website uses a self-signed certificate, you will be asked to confirm that the certificate's fingerprint match the expected one.

It is true, however, that the CA model is deeply flawed.  Security researchers have known this for ages, and the recent Comodo fiasco made it more or less mainstream.  Those interested can read [this paper](http://citpsite.s3.amazonaws.com/publications/Roosa_Schultze_CA_Trust_Model.pdf) for an overview about how the moel is flawed.

---

### Post by wizard10000 on 2011-07-14
> **ve4cib said:**
> The certificates -- as I understand them -- are to ensure that the public key of the server has not been compromised.

This.  I can't add much other than to say certificates aren't part of an encryption model, they're part of an authentication model - that's the reason encryption can be achieved without them  ;)

The certificate verifies that the server's private key and public key match.  You can self-sign a webserver without having to give a CA any money at all - but if the requirement is for you to be able to prove you are who you say your are then you're gonna have to cough up the money to a trusted CA.

---

