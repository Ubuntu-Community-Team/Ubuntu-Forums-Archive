---
title: "Revoking a Lost OpenPGP Key From Ubuntu Servers"
date: 2013-02-17
forum: Security
---

### Post by gerowen on 2013-02-17
So back in 2011 I generated an OpenPGP key to use for encrypting files/emails and digitally signing things.

The computer I used to generate that key is long gone (I used it for target practice because it kept overheating), and I'm not quite sure how I would go about revoking that old key, so I generated a new one on this computer to start using and have sync'd it with the Ubuntu servers as well.  However, I've noticed my old one is still there.  I was wondering if anybody could help me out.

My new key, and the one I want to remain on the server has the following information:
Key ID: BAFDBD15

The old key, and the one I want to be removed from the server, has the following information:
Key ID: 257503EF

I've updated my Launchpad account to use the new key as well, but I want to make sure that anybody who sends me an e-mail uses the correct key to encrypt things.

---

### Post by bodhi.zazen on 2013-02-18
You can not remove the old key, you can only revoke it

[http://www.gnupg.org/faq/GnuPG-FAQ.html#how-to-send-a-revocation-to-the-keyservers](http://www.gnupg.org/faq/GnuPG-FAQ.html#how-to-send-a-revocation-to-the-keyservers)

---

### Post by sudodus on 2013-02-18
This link might also help you to revoke it or at least to add some information, so that people might understand, that it does not work any more.

[[COLOR="Red"]http://www.pgp.net/pgpnet/pgp-faq/pgp-faq-key-revocation.html[/COLOR]]("http://www.pgp.net/pgpnet/pgp-faq/pgp-faq-key-revocation.html")

---

### Post by offgridguy on 2013-02-18
I see i am a little late, but there is also info in this thread on creating and revoking  the
PGP Key.

[http://ubuntuforums.org/showthread.php?t=1146081](http://ubuntuforums.org/showthread.php?t=1146081)

---

