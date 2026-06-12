---
title: "is aes encryption enough for sftp"
date: 2009-01-08
forum: Security
---

### Post by Superdude_123 on 2009-01-08
On a OpenSSH linux server, is AES encryption enough or should I change it to something better? How easy is it for a 3rd party to crack the encryption and figure out the transmitted data?

---

### Post by hyper_ch on 2009-01-09
it depends on you... do you use a 4 letter password? Do you use a 10 letter password? do you use a 20 letter password?
Do you mix capital and small letters? Number?
Is the password a real "word" or a modified word like "word11" or maybe "w03d"?

---

### Post by jpkotta on 2009-01-09
I wasn't aware that AES had any major flaws.  AFAIK it's the best general purpose block cipher around.

It is far more likely that the weak link is somewhere other than AES.  Like policy or users.

---

### Post by kevdog on 2009-01-09
I'm going to generally answer this since I don't know the exact ciphers that are available within sftp.  AES (Advanced Encryption Standard) actually represents a variant of the Rajindel encryption algorith.  NIST (National Institutes of Standards and Technology - USA) held an encryption competition to name a AES successor to DES (the old AES)in 2006. Nine finalists were chosen:
CAST-256, CRYPTON, DEAL, DFC, E2, FROG, HPC, LOKI97, MAGENTA, MARS, RC6, Rijndael, SAFER+, Serpent, and Twofish

Rijndael won the competition and hence became the AES on May 26, 2002.  The AES modification of the Rijndael ciphers is a block cipher of 128 bits and uses a symmetric encryption method, with a key size of either 128, 192, or 256 bits.  Theoretically AES256 should be the "most secure" since it takes more processing round of the key schedule to generate the key as compared to 128, however the process is slower.  

Depending on your needs speed may be more important than absolute cipher strength.  For example -- ssh, sftp - you may elect for AES128 for speed, whereas with email and GPG encryption with AES, you would probably elect for AES256 since only a finite piece of data is being transmitted on one occasion.

Hopefully that explanation may have helped.  I don't know if sftp offers the AES variants of 128,192,256.  No known break of AES has been published (no matter what the key size is chosen) to the best of my knowledge.  I believe if a credible break and had performed, this information would spread like wildfire since use of AES is within all encryption products (ssh, TrueCrypt, GPG, PGP, others (password keepers) -- you name it -- AES is always contained)

---

### Post by adamlau on 2009-01-09
Some say that AES was chosen due to the fact that the NSA had discovered a backdoor to the cipher and thus held the keys to its decryption method. Only the NSA knows for certain. Even so, I trust AES enough for my needs (though I prefer Twofish for certain applications). And just as hyper_ch hinted to, the key to any cipher is the strength of its passphrase. .

---

### Post by scorp123 on 2009-01-09
> **adamlau said:**
> Some say that AES was chosen due to the fact that the NSA had discovered a backdoor to the cipher and thus held the keys to its decryption method.  The source code of OpenSSH is public. If there were any backdoors it would have been spotted by now.

Also, AES is based on the Rijndael (see here: [http://en.wikipedia.org/wiki/Rijndael](http://en.wikipedia.org/wiki/Rijndael) ) algorithm which was developed by two Belgians: Joan Daemen and Vincent Rijmen. Belgians are known for chocolate and over 300+ kinds of beer ... but not for colaborating with the NSA (which is an US agency).

This whole "NSA has a backdoor" thing is therfore rubbish, sorry to say so.

---

### Post by adamlau on 2009-01-09
Rubbish, open source, conspiracy theory, or otherwise, the idea exists. It is up to the paranoia of the end user to determine how to best securify their systems. Again, I use AES for most of what I need encryption for :) .

---

### Post by hyper_ch on 2009-01-09
there is [N]o [S]uch [A]gency!

---

### Post by kevdog on 2009-01-09
Although the overhead would be high -- too bad you couldn't dual encrypt things -- run through something like AES then Serpent of Twofish for example.  That would probably be overkill.

Yes password strength is the weak link in the chain, not the actual cipher algorithm.  If you want to be ultraparanoid about picking a password -- pick a very complex password or passphrase, and then run this through something like the whirlpool hash, and use the resultant as the password for the aes encryption process.  Yes its yet another step, it might provide security through obscurity, however if you by that argument, so does picking a long password provide for security by obscurity.

Hyper_ch
Can I get some private support?

---

### Post by scorp123 on 2009-01-09
> **hyper_ch said:**
> there is [N]o [S]uch [A]gency! We're talking about AES and Rijndael, Belgium and their 300+ brands of beer ... shouldn't it therefore be:  **N**o **S**uch **A**le .... ? :)

---

### Post by jpkotta on 2009-01-09
> **scorp123 said:**
> The source code of OpenSSH is public. If there were any backdoors it would have been spotted by now.


I think he was refering to a weakness in the cipher, not the implementation.  There were all sorts of rumors about NSA compromising DES, and it turned out that they did tweak it -- to make it stronger.  We don't know what the NSA knows; they could certainly have an exploit for AES.  But there are *a lot* of people who don't work at the NSA, are very smart, have analyzed AES in depth, concluded that it has no weaknesses, and published their results for others to check.  Almost certainly the conspiracy theories are rubbish.

---

### Post by Dr Small on 2009-01-09
> **jpkotta said:**
> Almost certainly the conspiracy theories are rubbish.

But it's better to check and analyze, as you said has been done, than to blindly believe and accept that the cipher is flawless when it could have a backdoor in it.

Some men were made to invent things, some to raise awareness about specific things, and others to check, verify or debunk the awareness of others. (Not specifically saying that the awareness raisers are wrong, but that it adds to the second outlook of things, and raises questions.)

---

### Post by brian_p on 2009-01-10
> **scorp123 said:**
> We're talking about AES and Rijndael, Belgium and their 300+ brands of beer ... shouldn't it therefore be:  **N**o **S**uch **A**le .... ? :)

Only if the beverage is without hops.

---

