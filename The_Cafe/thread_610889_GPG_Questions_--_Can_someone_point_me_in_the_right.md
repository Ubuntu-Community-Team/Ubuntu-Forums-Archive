---
title: "GPG Questions -- Can someone point me in the right direction??"
date: 2007-11-12
forum: The Cafe
---

### Post by kevdog on 2007-11-12
Currently using gpg for signing/encrypting.  I currently have a sha-1 1096 length signing key with a elgamal 4096 encryption key.  Do you know if I can change or add a rsa signing key??

What about the inclusion of dsa2??  I know I can specifiy --enable-dsa2 on the command line, however if I do this does this require me to generate two new keys?

I dont have any public keys on a key server so I dont have to worry about revocation.  I just distribute the public key to a select handful of individuals.


Any link or nudge in the right direction would be great!!

---

### Post by henriquemaia on 2007-11-26
I bump this thread because I also wanted some information on this issue.

---

### Post by Zdravko on 2007-11-26
What's a GPG key?

---

### Post by kevdog on 2007-11-26
GPG for encrypted email --- GnuPG??

Anyone know the best cipher to use for encryption?

---

### Post by Zdravko on 2007-11-26
> **kevdog said:**
> GPG for encrypted email --- GnuPG??

Anyone know the best cipher to use for encryption?
I still don't understand. What it's use?

---

### Post by p_quarles on 2007-11-26
> **Zdravko said:**
> I still don't understand. What it's use?
[http://en.wikipedia.org/wiki/Gpg](http://en.wikipedia.org/wiki/Gpg)

---

### Post by FuturePilot on 2007-11-26
> **Zdravko said:**
> I still don't understand. What it's use?

To encrypt emails so that only the recipient can read it providing that they have your key. You can also encrypt files with it as well.

Edit:
> **p_quarles said:**
> [http://en.wikipedia.org/wiki/Gpg](http://en.wikipedia.org/wiki/Gpg)

Better explanation ;)

---

### Post by Zdravko on 2007-11-26
> **p_quarles said:**
> [http://en.wikipedia.org/wiki/Gpg](http://en.wikipedia.org/wiki/Gpg)

I read this and still don't understand what it is :(

---

### Post by Zdravko on 2007-11-26
> **FuturePilot said:**
> To encrypt emails so that only the recipient can read it providing that they have your key. You can also encrypt files with it as well.

Edit:


Better explanation ;)
How does the recipient know the key?

---

### Post by tribaal on 2007-11-26
The public keys are shared on public keyservers.

So if I want to send you encrypted mail, I'll search for your email address on a keyserver, get the corresponding public key, encrypt my email with it and send it.
Then you will decrypt it using your private key. And only the private key that matches the public key I encrypted it with can decrypt it.

Hope this helps. You should open a new thread if it doesn't, though, and let people here get back on topic ;)

- Trib'

---

### Post by kevdog on 2007-11-26
I posted a thread a ways back and less than 10% of the ubuntu responders do not use gpg or any type of email encryption.  I was shocked.  Anyway I find it very useful on a limited basis, and have since converted by brother to use gpg -- he is really into it now, although he was very skeptical at first.  He uses WinPT from his windows box, and MAC users can also use gpg -- so its truly cross-platform compatible.  

I wish everyone would use gpg.

---

### Post by ice60 on 2007-11-26
you can just generate a new key, then when you go to sign something you'll be asked which key you want to use. i'm almost certain that's correct, but maybe you should try it on a livecd first if it's really important for you.

i think you just run this and follow the instructions, run as a user, not root. -
```
gpg --gen-key
```

---

### Post by ice60 on 2007-11-26
here are some links i've got. maybe they will help??
[http://www.gentoo.org/doc/en/gnupg-user.xml](http://www.gentoo.org/doc/en/gnupg-user.xml)
[http://www.dewinter.com/gnupg_howto/](http://www.dewinter.com/gnupg_howto/)
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

and i remembered a whole podcast about it, i think it was this one - (lol it must be because the links above look the same as on that page!)
[http://www.linuxreality.com/podcast/episode-47-openpgp/](http://www.linuxreality.com/podcast/episode-47-openpgp/)

---

### Post by kevdog on 2007-11-26
For gpg, to generate keys, you would be better served creating a 4096 bit RSA signing key and 4096 ElGamal encryption key.  The default I believe is a 1024 DSA signing key and 1024 ElGamal encryption key.  I could generate a tutorial how to generate the keys if anyone was interested.

---

### Post by Zdravko on 2007-11-27
> **kevdog said:**
> For gpg, to generate keys, you would be better served creating a 4096 bit RSA signing key and 4096 ElGamal encryption key.  The default I believe is a 1024 DSA signing key and 1024 ElGamal encryption key.  I could generate a tutorial how to generate the keys if anyone was interested.
I am interested!

---

### Post by kevdog on 2007-11-27
I'll see what I can make in the next day or two.  Its fairly straightforward now that I figured out how to do it, but its slightly more complex than the one line setup

ssh genkey

---

### Post by ice60 on 2007-11-27
> **Zdravko said:**
> I am interested!the links i gave tell you everything you need to know about generating keys. i'm sure any cryptography expert will tell you the defaults are fine to use!

---

### Post by kevdog on 2007-11-27
Probably, but DSA has been broken -- DSA uses the SHA-1 hash, and this hash has been broken, however probably not in any meaningful way:
[http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html](http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html)

Cryptography experts fear that once a one part of a hash shows a weakness, there are likely others.  Because of this many recommend moving away from utilization of the SHA-1 hash.  RIPEMD160 is another fix 160 bit hash that may be utilized with DSA -- to my knowledge this hash has not been broken.

Supposedly fix bit hashes (I think that is the correct term) are not as efficient as newer modern algorithms.  With newer hashes available its advised to use these -- such as SHA512.  This hash in conjuction with RSA rather than DSA.  I dont think SHA512 can be used with DSA.

Ask your friend if what I am saying is correct, however Ive done a lot of extensive googling on this subject lately, and have come to this conclusion.  

DSA/RSA and the use of hash functions of course is only in reference to the signature key.  Encryption uses ciphers, not hashes.  

GPG actually employs a hybrid encryption scheme.  A session key is generated randomly for each message.  This session key employs a certain symmetric cipher to encrypt the contents of the letter.  The session key is then encrypted with the recipients public key -- (El Gamal is the algorithm used for this encryption).  Note that the contents of the letter are symmetrically encrypted -- where as the session key is asymmetrically encrypted.  The encrypted session key along the the symmetrically encrypted letter are sent together to the recipient.  The recipient uses the private key to decrypt the session key and then the session key decrypts the message.  

For symmetric encryption, gpg/pgp can utilize the following ciphers:
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH

You might want to verify this information but one post I found stated gnupg uses blowfish as the default cipher, whereas opengpg (gpg2) uses 3DES and PGP uses CAST5 as the default.  Of course by passing flags on the command line or by alterations in the gpg.conf file, something other algorithm other than the default cipher can be utilized.  I currently use TWOFISH -- BLOWFISH/TWOFISH ciphers were created from the same author.  I haven't found any information of people's opinions of the "strongest" cipher, however I do not believe any cipher up to this point has been compromised.

---

### Post by kevdog on 2007-11-27
Here is another link you might want to take a look at:
[http://www.pthree.org/2007/01/22/time-for-higher-security-in-digital-email-signatures/](http://www.pthree.org/2007/01/22/time-for-higher-security-in-digital-email-signatures/)
[http://www.e-ignite.co.uk/html/key_types.html#RSA](http://www.e-ignite.co.uk/html/key_types.html#RSA)

---

