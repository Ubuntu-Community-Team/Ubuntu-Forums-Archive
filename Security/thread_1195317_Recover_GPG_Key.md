---
title: "Recover GPG Key"
date: 2009-06-23
forum: Security
---

### Post by ace214 on 2009-06-23
Yes, I know I'm an idiot. Here's the problem:

I created a GPG key a while back ago to attempt some packaging. I formatted over it without backing it up. I don't have a revocation certificate.

Can I create a new private key with the public key since I still know the passphrase? I'm assuming not because of the randomization.

Is there anything I can do to revoke the key? It is published on keyservers.

Thanks for any help.

---

### Post by rookcifer on 2009-06-23
> **ace214 said:**
> Yes, I know I'm an idiot. Here's the problem:

I created a GPG key a while back ago to attempt some packaging. I formatted over it without backing it up. I don't have a revocation certificate.

Can I create a new private key with the public key since I still know the passphrase? I'm assuming not because of the randomization.

Is there anything I can do to revoke the key? It is published on keyservers.

Thanks for any help.

No, you will have to generate a new key.  And you can't remove a key from a key server -- once you upload it, it will always be there and will always be associated with the e-mail address you listed.

What I would do:

[LIST]
[*]Generate a new key
[*]Generate a revocation certificate.
[*]Copy the ~/.gnupg folder (and the revocation certificate) to a USB dongle or to a CD/DVD. 
[*]Put the back-up media away for storage (put it somewhere where it can't be lost, stolen or destroyed).
[/LIST]

This way if you ever format and reinstall an OS, you can just break out your USB or CD backup and copy the .gnupg folder to /home.  You will then have your key back.  I would also create a new e-mail address for this new key (to avoid confusion to those wanting to snatch your key from a key server).  

Lastly, never sign someone else's key unless you can verify their identity (best to meet them in person to verify their identity).

---

### Post by Lucian Solaris on 2009-06-24
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

Yea, as far as revocation you're sunk.  You must have the private key intact in order to sign a revocation certificate, and since you have neither the private key nor a pre-created revocation certificate, you're sunk.  Your e-mail address has nothing to do with the selection of prime numbers used in key generation.  You cannot re-create a private key by making another key with the same UID info (name, e-mail, comment).

Best case scenario you uploaded your key only to keyserver.pgp.com, as you could upload a new key with the same e-mail address and PGP's keyserver will replace the old key with the new key in its database.  You could try to help prove that your new key is your current key by downloading the key you uploaded to PGP's keyserver and uploading it to other servers, like pool.sks-keyservers.net .  The public key provided by PGP's keyserver contains a signature by PGP Global Directory, which only the most recent keys of a group that share the same e-mail address will have.  Your milage may vary.

ace214 is right, you probably should generate and sign a revocation certificate, then hide it.  DO NOT UPLOAD IT UNLESS YOU WISH TO REVOKE THE KEY THAT SIGNED IT!

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 - *.:{Hack.I.T Edition r0001}:.*

iJ4EAREKAAYFAkpCWzcACgkQ+7Rzy15t3vZu9AH9E3MsUjOqla09ZUdtmtrr1Mvr
vXHVSHSzRhgnflvo5FeqGZAwlX4l5mHmt628Xy/+SU+Q5mTrLswYw3uAf3uVmQH/
VEQ/rzFT3ybvh5zOu5eUV+gVOrTb5y4TLnxVu/o5UnVxbdNrkGH4Wx2jRXugWJYQ
uVbHyE+u9NKj51W8f475sA==
=D/Jg
-----END PGP SIGNATURE-----

> **ace214 said:**
> Yes, I know I'm an idiot. Here's the problem:

I created a GPG key a while back ago to attempt some packaging. I formatted over it without backing it up. I don't have a revocation certificate.

Can I create a new private key with the public key since I still know the passphrase? I'm assuming not because of the randomization.

Is there anything I can do to revoke the key? It is published on keyservers.

Thanks for any help.

---

### Post by Trebaruna on 2009-06-25
Perhaps this is unneeded but to clarify a bit: the passphrase has nothing to do with the actual key. The key is generated from a bunch of random data, and the passphrase is used to encrypt the key itself. This is also why it's perfectly possible to change your secret key's password without any problems: it doesn't affect the actual key.

---

