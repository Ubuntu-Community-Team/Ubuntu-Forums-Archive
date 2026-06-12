---
title: "Re-importing a GPG key"
date: 2005-07-26
forum: Server Platforms
---

### Post by TravisNewman on 2005-07-26
Here's the deal. At some point in time I reinstalled Hoary and I didn't back up my .gnupg folder or anything. I have a public key that I've uploaded to a keyserver. My question, how do I re-import it into GPG so I can use it like I would have had I just made them?

---

### Post by TravisNewman on 2005-07-26
The problem here is that I don't have the private key, only the public key. Anyone?

---

### Post by Brian Puccio on 2005-07-27
You'd need the private key, you can't generate a private key from the public one. If you could, anyone (becuase your public key is on a public key server) could create a new private key and sign emails (and other files) as though they were you.

Secondly, this is why most GPG Howto's reccomend generating a revocation at the same time as key generation:

> 3.7 Generating a revocation certificate

This is an optional step.

The generation and storage of a revocation certificate will allow you to revoke your public key even in the event that you loose access to your private key due to compromise, seizure, forgotten passphrase, or media failure. If you want to have the ability to revoke your public key when you do not have access to your private key, you should generate a revocation certificate and store it a secure and safe place. You should also print out a copy of your revocation certificate so that it can be entered and used in the event of the failure of the media it is stored on.

If you revocation certificate is compromised, the individual who compromises your revocation certificate will be able to circulate the certificate thereby disabling your key. However, the individual will not be able to compromise your secret key through his access to your revocation certificate. Therefor, they will not be able to generate fake signatures, decrypt messages encrypted with your keypair, or otherwise misrepresent themselves as the owner of your keypair. Since the only negative outcome possible from the compromise of a revocation certificate is the disabling of your keypair, it is a generally safe and good thing to do. 

[http://cryptnet.net/fdp/crypto/gpg-party.html#ss3.7](http://cryptnet.net/fdp/crypto/gpg-party.html#ss3.7)

See also:

> Generation and management of your keys, specifically your private key, is your responsibility. If your private key is lost you will be unable to sign or decrypt emails. If your private key is compromised or stolen other people may be able to masquerade as you.

[http://www.bath.ac.uk/bucs/supporters/email/mulberry-gpg.html#gettingstarted](http://www.bath.ac.uk/bucs/supporters/email/mulberry-gpg.html#gettingstarted)

As well as:

[http://wiki.openskills.org/OpenSkills/OpenPGP+Key+Backup](http://wiki.openskills.org/OpenSkills/OpenPGP+Key+Backup)
[http://lists.yukidoke.org/pipermail/debian-nyc-soc/2004-November/000011.html](http://lists.yukidoke.org/pipermail/debian-nyc-soc/2004-November/000011.html)

---

### Post by beeldings on 2005-08-02
I had to re-install Hoary a few days ago, and I lost my secret keys and my revocation certificate. Does anyone know if/how I can revoke my key even though I lost my revocation certificate and secret key? I memorized my passphrase, if that helps matters.

---

### Post by Brian Puccio on 2005-08-03
[QUOTE=beeldings]I had to re-install Hoary a few days ago, and I lost my secret keys and my revocation certificate. Does anyone know if/how I can revoke my key even though I lost my revocation certificate and secret key? I memorized my passphrase, if that helps matters.[/QUOTE]
 Not unless you've memorized the revocation as well.  Sorry!

---

### Post by beeldings on 2005-08-04
[QUOTE=Brian Puccio]Not unless you've memorized the revocation as well.  Sorry![/QUOTE]

No biggie. I did what I thought was the best thing to do and closed the e-mail account associated with that PGP key. It really would not have bothered me so much that I lost my private key and certificate had I set an expiration date on my keys. I did not, so they will remain in the system for a very long time.

---

### Post by Brian Puccio on 2005-08-04
[QUOTE=beeldings]No biggie. I did what I thought was the best thing to do and closed the e-mail account associated with that PGP key. It really would not have bothered me so much that I lost my private key and certificate had I set an expiration date on my keys. I did not, so they will remain in the system for a very long time.[/QUOTE]
 And by very long time, that means forever.

Eh, I wouldn't fret over it, there's nothing you can do, you're not the first and you won't be the last.  Live and learn.

---

