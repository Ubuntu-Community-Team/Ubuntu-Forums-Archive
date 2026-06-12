---
title: "Advanced GnuPG Concepts - Advanced Key Generation"
date: 2008-02-04
forum: Tutorials
---

### Post by kevdog on 2008-02-04
**Note to Moderator or Any User -- Current Writeup is Incomplete -- Attempt to Complete Very Soon!  Please notify me if thread is moved.

**[SIZE="5"]GnuPG Background Study -- Essential Knowledge in order to Utilize GnuPG Correctly[/SIZE]**

**[SIZE="4"]Introduction[/SIZE]**

GnuPG provides two important security measures to its end users-- [SIZE="2"]**Data Encryption**[/SIZE] and [SIZE="2"]**Data Authentication**[/SIZE].  Although linked, these two functions are fundamentally different and important for the end-users of GnuPG to understand.  

[SIZE="2"]**Data Encryption**[/SIZE] allows for data to be sent in an encrypted format that is extremely difficult for anyone but the data recipient to decode.  Once encoded, it is extremely difficult for anyone, including the sender of the encrypted data, to decode the encrypted data. 
[SIZE="2"]
**Data Authentication**[/SIZE] allows the recipient of the data, to be sure that the data received was not altered or changed in any way once it left the hands of the sender.  Without this important authentication measure, it would be theoretically possible for encrypted data to be intercepted during its transport to the end recipient, data either removed or inserted, the data re-encrypted and sent to the end recipient without any knowledge on the part of the end-recipient that the received data was different than the data originally sent. The process of providing for **Data Authentication** within GnuPG is known as **Digital Signing**. 

In order to make use of GnuPG's Encryption and Digital Signing capabilities, a set of keypairs needs to be created and distributed.  Each keypair contains a encryption and digital signing key.  Furthermore, the function of each keypair is different and unique.  One keypair is used to digitally encrypt and sign outgoing data -- this is known as the public keypair*. The other keypair is used to digitally decrypt and verify the signature of the received data -- this keypair is known as the private keypair**.  Because each keypair functions in a unique way (either signing/encrypting or verifying/decrypting), GnuPG provides for **key-based asymmetric cryptography**.

*The Public Keypair in many internet publications is known simply as the Public Key.  Please be aware however that the "Public Key" is actually a combination of at least one public digital signing key and one public encryption key.

**The Private Keypair in many internet publications is known simply as the Private Key.  Please be aware that the "Private Key" is actually a combination of at least one private digital signing key and one private digital signing key. 

In practical terms, two users who want to utilize GnuPG cryptography, must create and distribute their public keys while keeping their private keys secret.  User A would create public and private keypairs, distributing the public keypair to User B.  User B on the other hand would create his own set of public and private keypairs, and distribute his public keypair to User A.  If User A wanted to send User B a digitally encrypted and signed message, User A would encrypt the message with User B's public encryption key, but sign the message with his own (User A's) private signing key.  Upon arrival of the message, User B would his own (User  B's) private encryption key to decrypt the message, while utilizing User A's public signing key to verify the signature of the letter and authenticate that the letter was not changed or altered after being digitally signed.

**Summary**
GnuPG
1) Provides for **Data Encryption** and **Data Authentication**
2) Requires each user to create a Public and Private KeyPair.  The Public Keypair must be distributed a priori to other users wanting to send data.  The Private KeyPair must be kept private by the data recipient.
3) Each Keypair contains at least one signing key and one encryption key.  The signing key and encryption key differ, as do the public/private signing key and public/private encryption keys.  All keys are unique.
4) The Public Keypair is generated (or can be regenerated) from the Private Keypair, hence the security of GnuPG hinges on confidentiality of the Private Keypair.  The Private Keypair must be kept private.

**[SIZE="4"]Advanced Concepts[/SIZE]**

**[SIZE="3"]Data Encryption[/SIZE]**
Thinking of GnuPG's data encryption in a broad overview - a user's public encryption key is used to encrypt the data, whereas the user's private encryption key is used to decrypt the data.  Although many users think that GnuPG's data encryption scheme is purely asymmetric, it uses both asymmetric and symmetric methods -- otherwise employing a hybrid encryption method.  Unlike asymmetric encryption that uses one key to lock the data, and another key to unlock the data, symmetric encryption utilizes the same key or password.  A file that is password protected, is utilizing a symmetric security method, in that it is the same password to unlock or lock the file.

GnuPG's hybrid encryption scheme works as follows. For every encrypted message sent, GnuPG generates a random session key.  The actual data content is symmetrically encrypted using a symmetric cipher utilizing the random session key as the password to the cipher.  The resultant is known as ciphertext.  The actual session key is then asymmetrically encrypted using the public encryption key.  Together the encrypted session key and the ciphertext is sent to the recipient.  The recipient would use the private encryption key to decrypt the session key, which then in turn would be used to symmetrically decrypt the ciphertext into text.

For any message sent, either the encrypted session key or the encrypted ciphertext represents potential points of vulnerability.  Because the session key is randomly generated each time, a break of the session key would at most compromise only one set of data.  On the other hand, vulnerability of the symmetric cipher would expose potentially many data sets if the same symmetric cipher was used each time.  

Because the use of a secure symmetric cipher is paramount, GnuPG is very conservative in its choice of ciphers. As of version 1.4.8 GnuPG currently offers 3DES, CAST5, BLOWFISH, AES, AES192, AES256, and TWOFISH as potential symmetric ciphers.  Proprietary ciphers such as IDEA as originally used in PGP can be added and compiled into the gpg source.  Other ciphers such as CAMELLIA128 and CAMELLIA256 -- ciphers recognized as the Japanese encryption standard as used by other countries in the Pacific Rim -- are considered "experimental' but may be added if GnuPG is compiled from source: [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=649466](http://ubuntuforums.org/showthread.php?t=649466)[/COLOR].

3DES is the default cipher as specified in the OpenGPG standard.  It is computationally slow, however has no known security breaches since its implementation.  AES - otherwise known as the Advanced Encryption Standard - employs a variant of the Rijndael -- pronounced "rain-doll" -- algorithm.  The Rijndael algorithm was chosen as the AES by the National Institues of Standards and Technology (NIST) on Nov 26, 2001 after a 5 year standardization process ([http://en.wikipedia.org/wiki/Advanced_Encryption_Standard](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard)).  AES is the official cipher recognised by the United States government.  GnuPG (as opposed to the OpenGPG standard) defines the AES256 cipher as the default cipher. 

The cipher employed during the symmetric encryption process may be selected, changed, or modified at any time.  This may be accomplished through either modification of the encryption keys or by editing of the gpg.conf file.  This process will be expanded upon below.  In comparison however, the algorithm used for the asymmetric session key encryption is chosen at the time of key generation, and may not later be altered.  The process of Encryption Key Generation will also be expanded upon below.  

**Summary**
1. GnuPG employs a hybrid encryption scheme.
2. The randomly generated session key is asymmetrically encrypted, whereas the message text is symmetrically encrypted creating ciphertext.
3. The encrypted session key and ciphertext are the two parts of an encrypted correspondence.
4. The cipher used to symmetrically encrypt text to ciphertext may be changed or modified.
5. AES256 is the default GnuPG cipher - as of GnuPG version 1.48
5. The algorithm or cipher used to encrypt the session key may not be altered and is only specified at the time of encryption key generation.

**[SIZE="3"]Digital Signing[/SIZE]**

Digital Signing is a method to ensure data authenticity.  Messages in which the signature can be verified, represent data that unaltered during transport.  Note that digital signing does not guarantee that the data during the transport route was not intercepted and read, it simply guarantees that nothing was subtracted or added to the data during transport.  Again it guarantees that the message or data received was unaltered during transport.

Data authenticity is guaranteed by the use of cryptographic hash algorithms.  For those unfamiliar with cryptographic hash functions, a cryptographic hash function is:

> cryptographic hash: A mathematical function that maps values from a large (or even very large) domain into a smaller range, and is (a) one-way in that it is computationally infeasible to find any input which maps to any pre-specified output; and (b) collision-free in that it is computationally infeasible to find any two distinct inputs which map to the same output. [After X9.31]
- From [COLOR="Red"][http://www.atis.org/tg2k/_cryptographic_hash.html](http://www.atis.org/tg2k/_cryptographic_hash.html)[/COLOR]

Hash functions in general can be considered ONE-WAY conversion algorithms.  Hash functions in general take a large set of data as input, and output a much smaller set of data representing the data's fingerprint.  It is impossible to take the fingerprint and reproduce the original data set.  Hash functions are commonly used in other areas other than cryptography.  Take for example the distribution of the ubuntu iso image. [COLOR="Red"][https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)[/COLOR]  A user for example would download their selected version of the ubuntu iso image.  Once the download of the iso image was complete, one could verify that the iso image was authentic -- ensuring that the downloaded iso file had not been corrupted during the downloading process(pieces either added or missing) -- by calculating the md5sum of the downloaded iso file. The  md5sum program uses the md5 cryptographic hash to calculate the iso file's hash or digital signature.  If the calculated value matches the value reported on the ubuntu website, then one can be guaranteed that the downloaded iso image is authentic.

In addition to providing a one-way transformation, cryptographic hashes are theoretically unique.  This means that no two sets of input should produce the same output, or no two sets of input data should produce the same digital fingerprint or hash value.  Practically however this is not the case.  Take for example the SHA-1 hash.  In theory it would take 2^80 operations to find two input values that would map to the same hash product.  When two inputs are found to produce the same hash, a "collision" is stated to have occurred.  Although it is impossible to create any cryptographic hash function that does not produce collisions, proper cryptographic hash functions are designed so that it would take even the fastest of computers years (if not longer) to produce a collision.

As of version 1.48, GnuPG offers the following cryptographic hashes - MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224.  Although different hashes may be used, only one hash can be used for any one message or data set, to produce the digital signature.  Currently SHA1 is the default cipher, although this is likely to change in the future given the recently discovered vulnerabilities of the SHA1 hash: [http://www.schneier.com/blog/archives/2005/02/sha1_broken.html](http://www.schneier.com/blog/archives/2005/02/sha1_broken.html).  Similar to the NIST competition that named the Rijndael algorithm as the AES (American Encryption Standard) in 2001, NIST is holding another competition to define a new American Secure Hash Standard: [http://csrc.nist.gov/groups/ST/hash/index.html](http://csrc.nist.gov/groups/ST/hash/index.html).  Entries to this competition will no longer be accepted beyond Q3 2008.  The actual date when the winner will be announced is currently unknown.   


**[SIZE="2"]How Digital Hashes Work within GnuPG[/SIZE]**
Hashes or Data Signatures are used in conjunction with Public and Private signing keys in order to provide data authentication.  The sender of the data or message first calculates the hash value of the data or message being sent.  This hash value is then asymmetrically encrypted with the recipient's Public Signing Key and resultant sent as a footer contained in the original message. A digitally signed message would appear as follows  (Please note this message is employing the SHA512 hash):

```

-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

This letter is digitally signed
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.8
Comment: [http://firegpg.tuxfamily.org](http://firegpg.tuxfamily.org)

iQIcBAEBCgAGBQJHrnaiAAoJEOU4qDEbiBDF9woQAJb9yWxjr+s44R7ziUgUlwsc
3fBm94WgWXiYQOrbNx378SaPRLaEgYmJNYLeKINmnlLzpqoqcYtCN6NIiDFtrkOw
7nkahaAWSky6/QxO8z382WhkFb8a0NGnli0Emyfpb0KMpGL7yFbecoQS0J47iwJC
euUrfTxJ2Jj5yf620/76eWrMhoI0t2HvA5h34V2khq6/Df9ShEaGRfvfg4TaszDP
4P7yl/9CbVhJpBEt8OMEPzUnR4NiJa6NLNbiZcPXxN9kGm0Qa/r+7rKGnPLIYgd+
Nni4cD2KDz8+4QAt9r7GRZ8ARzHEfdDcC1SLWllcYMjh4zqFF2Adj8D46C+O3DCk
tRhPLEdW4lmapkpeAlrY2hcyrDEgz+u9AzitN6CzPyGHg4q54WiGj9E3VZYhiuTB
9Ooo9wHgmoKxFSWikrkqECJDc21BavViudvFA80bGAACwbMswWvwugm8FvHosWYI
VkR2nrHCLMlEmdGrlE00gPapX26ykn4RSS1LEHdXQzBJN0dDPcJq+8HPZn1M6rLb
ycf81nAWw9fouavOy7RJS+7rnegJY4kAEd52QzUwo/bOi0iZ2JEfon40VK01daNo
JESKKI76hU2tT7R65B24rD/P3aPsGTgKb+Vu7vV9X/pSLJ3PRA3JiKbVVac6pE3q
/YgbgYAtT8HIk8oQNXx3
=gKxq
-----END PGP SIGNATURE-----

```

The recipient of the letter, calculates the hash or digital signature of the transmitted message (the portion of the letter not including the signature headers or footers).  Using the Private Signing Key, the encrypted hash is decoded.  _The Calculated Hash is then compared to the Decoded Hash_.  If the two signatures match, then the data signature is stated to be valid, and data the data considered to be authentic.  Please note that two process or algorithms are in use with digitally signed messages -- the cryptographic hash function to calculate the data fingerprint -- and an asymmetric encryption algorithm to encrypt the hash product, so the hash value is disguised during transport.  

**Summary**
1. A Cryptographic Hash is a one way algorithm to produce a data fingerprint.  The original data can not be recreated from the data fingerprint.
2. For each Cryptographic Hash function - no two sets of data should produce the same hash product.  When two sets of data produce the same hash product, a "collision" has occurred.  The occurrence of collisions must be extremely rare for a cryptographic hash function to be considered practically usable.
3. The most recent version of GnuPG -1.48-, utilizes the following hashes:  MD5, SHA-1, RIPEMD160, SHA-256, SHA-384, SHA-512, SHA-224.
4. The SHA-1 hash is the current default hash.
5. When sending an individual message signed with GnuPG, the cryptographic hash function produces a digital signature or hash product from the original message.  This digital signature is then encoded with the recipients Public Signing Key.  The recipient calculates the hash product of the received letter.  The recipient also decodes the encrypted digital signature sent with the message using the Private Signing Key.  If the Calculated Digital Hash/Signature matches the Encoded Digital Hash/Signature, the message is considered to be authentic.

**[SIZE="3"]Key Algorithms[/SIZE]**

The two principle parts of any asymmetric keypair are the:

- Key Type (Key Algorithm) and 
- Key Length 

As per the discussion above, the Signing Keypair is used to encrypt/decrypt the message hash, whereas the Encryption Keypair is used to encrypt/decrypt the message individual session key.

**[SIZE="2"]Public/Private Signing Keypair[/SIZE]**
Signing Keys employ either the DSA (Digital Signature Algorithm) or RSA (Rivest-Shamir-Adleman) algorithms to provide the asymmetric encryption/decryption of the message hash.  Information about DSA may be found here: [http://en.wikipedia.org/wiki/Digital_Signature_Algorithm](http://en.wikipedia.org/wiki/Digital_Signature_Algorithm) where as information about the RSA algorithm may be found here: [http://en.wikipedia.org/wiki/RSA](http://en.wikipedia.org/wiki/RSA).  The topic of which algorithm is best to use in GnuPG is highly controversial and will not be discussed here.  If the reader is interested, he may consult the GPG user archives for future discussion: [http://lists.gnupg.org/pipermail/gnupg-users/](http://lists.gnupg.org/pipermail/gnupg-users/) .  DSA is considered the default algorithm in GnuPG.  RSA was once a proprietary algorithm, however its patent expired on September 6, 2000, and its use is no longer restricted.  

Key Length is the primary measure of the cryptographic strength of the key.  **Many cryptographic experts are recommending a key length no shorter than 2048 bits**. RSA keys may be 1024, 2048, or 4096 bits in length.  DSA keys are typically 1024 bits in length, however 2048 and 3096 bit length keys may be created.  Please see immediate discussion below regarding the use of larger DSA keys and its implications in regards to signing hash algorithm.

If you are planning to use DSA signing keys, then the following discussion is particularly relevant to you: 

[COLOR="BLUE"][COLOR="black"]** Up to and including GnuPG version 1.48, DSA is the default signing algorithm. By default, all DSA signing keys are 1024 bits in length**[/COLOR].  In version 1.48, the GnuPG developers introduced the feature of DSA2 signing keys.  This feature allows signing keys to be created with 2048 or 3096 bit lengths. Although many may refer to DSA2 as a newer algorithm as compared to DSA, the same DSA algorithm is used, only that larger key lengths may be utilized -- all keys, no matter the length, are DSA keys.  [COLOR="black"]**The ability to create keys larger than 1024 bits in length is disabled by default, and DSA keys larger than 1024 bits are not compatible with older versions of GnuPG prior to 1.44.  In order to create larger length DSA signing keys, the user must manually edit the gpg.conf file - located in the ~/.gnupg directory - and enable the --enable-dsa2 switch**[/COLOR] (A sample gpg.conf file is given at the end of the tutorial).

Beyond providing extra cryptographic strength, larger DSA signing keys (>1024 bits), allow for the use of the SHA-256, SHA-384, SHA-512, and SHA-224 hashes.  The original Digital Signature Standard constrained the length of DSA keys to be a multiple of 64 between 512 and 1024 (inclusive).  With 1024 bit keys, users are constrained to 160 bit hash functions -- RIPEMD160 or SHA-1.  [COLOR="black"]**With 1024 bit length DSA keys, only the  SHA-1, or RIPEMD160 hash functions may be utilized**[/COLOR]. Given the recently discovered vulnerabilities with the SHA-1, it is recommended that a hash other than SHA-1 be utilized [http://www.schneier.com/blog/archives/2005/02/sha1_broken.html](http://www.schneier.com/blog/archives/2005/02/sha1_broken.html).  [COLOR="black"]**By using DSA keys > 1024 bits, not only is the cryptographic strength of the key improved, hashes such as SHA-256, SHA-384, SHA-512, and SHA-224, as well as RIPEMD160 and SHA-1 may be utilized.  Again it is recommended that users begin migrating away from the SHA-1 hash and towards longer hashes such as SHA-224 or SHA-256.**[/COLOR]
[/COLOR]

A further advanced explanation of the relationship between DSA keys and hash length is found in the FIPS-180-3 specification: [http://csrc.nist.gov/publications/PubsDrafts.html#FIPS-180--3](http://csrc.nist.gov/publications/PubsDrafts.html#FIPS-180--3)
L represents the DSA key bit size, N represents the corresponding resultant hash size:
      L = 1024, N = 160
      L = 2048, N = 224
      L = 3072, N = 256

This relationship shows that for any 1024 bit DSA key, a corresponding 160 bit hash will result.  For a 2048 bit key, a hash length of 224 bits will result.  For a 3072 bit key, a 256 hash will result. 

A practical example: if a DSA 2048 bit key is created, the following hashes that are 224 bits or higher are available for use within GnuPG: SHA-224, SHA-384, SHA-256, SHA-512.  As suggested by there name, the SHA-224 algorithm produces 224 bit signatures, SHA-384 produces 384 bit signatures, etc.  SHA-1 or RIPEMD-160 could not be used since the resultant signatures (both 160 bits) are less than the specified 224 bit length.  Although internally SHA-224 will produce a 224 bit product, SHA-384 produces a 384 bit product, SHA-256 produces a 256 bit product, and SHA-512 produces a 512 bit product, in order to be compliant with the FIPS standard the result product will be truncated (using the leftmost bits) to always produce a 224 bit product.  With 3072 bit DSA signing keys, the SHA-256 or SHA-512 hash may be used but the resultant signature will always be truncated to be exactly 256 bits in length.  Because of this truncation, there is no practical advantage of using a SHA-256 hash vs a SHA-512 hash truncated to 256 bits.  The digital signatures are equally as strong.

The use of RSA signing keys are subject to no such hash restrictions.  No modification of the gpg.conf file is required to use larger key lengths with the RSA.  RSA Signing Keys may be 1024, 2048 or 4096 bits in length, and may utilize all available hash functions - SHA-512, SHA-384, SHA-256, SHA-224, SHA-1, RIPEMD160, and MD5.


**[SIZE="2"]Public/Private Encryption Keypair[/SIZE]**
Encryption keys are generated either using the ElGamal Algorithm or RSA (Rivest-Shamir-Adleman) Algorithm. Because the OpenGPG standard evolved directly from the PGP 5 standard and the RSA algorithm was patent encumbered prior to Sept 6, 2000, ElGamal is the default Encryption Key Algorithm.  The user however may specify whether to create ElGamal or RSA encryption keys during key generation.  This process will be discussed below. Using the chosen Encryption Key Algorithm, a public and private encryption keypair is generated.  Keys generated with the ElGamal or RSA algorithm are referred to as ElGamal or RSA Encryption Keys.  The key types (ElGamal, RSA) are not interchangeable.

The purpose of the Encryption public/private keypair is to encrypt/decrypt a randomly generated session key created with each new message.  The session key in turn acts as the password or key for a specified cipher algorithm which symmetrically encrypts/decrypts plain text to cipher text.  Session Key generation is modeled after the random number generator as described in Peter Gutmann's paper: "Software Generation of Practically Strong Random Numbers".  This is also described in Chapter 6: "Cryptographic Security Architecture", New York, 2004 - ISBN 0-387-95387-6.

Session key generation is handled by GnuPG.  It is not possible for a user on the fly to generate a random session key via and simply tell GnuPG to use this key for message encryption.  It is possible however to manually specify a session key to use during message decryption.  Although this concept may be seem strange at first glance, its utility is apparent when a higher authority may force revelation the contents of an encrypted message.  Rather than forfeiting the private key which would make decryption of every single message ever received possible, its possible to only turn over the session key of the message in question.  This session key could then be used to decrypt the contents of the message.  Since a unique session key is generated for every message sent, forfeiting possession of a single session key would only compromise the contents of one single message, rather than all the messages received by a particular user.


Discovering the messages session key as generated by default:


Using the manually specified session key to decrypt the message

---

### Post by seventhc on 2008-02-17
This looks good, thanks for pointing me in this direction. :)

---

### Post by Rocket2DMn on 2008-05-07
kevdog, I ran across a post you made [here]("http://ubuntuforums.org/showthread.php?t=759348") when I was searching for info on sharing a GPG key between computers, which I intend to do as soon as I finish this response.
You mentioned that this tutorial was incomplete (though it looks good to me), but I and many users would love for you to finish it.  I know that bodhi_zazen would certainly love to have this in his bookmarks, so I shall pass it on to him so it can be shared with others.  We've been discussing security at the Beginner's Team meetings and although this is a little advanced for beginners, it is a great resource for those looking to read up on security practices.

This little essay really is a gem, you really should finish it.

---

### Post by kevdog on 2008-05-07
There wasn't much response to the thread, so my motivation slowly died.  So far all I discussed were "background" concepts.  The second part of the guide was to be more practical, showing how to correctly make keys, how to identify the symmetric cipher and hash used in the keys, how to modify the preferred hash and cipher, and how to specify the order of hash and cipher used when creating keys.  I think this is important, particularly in terms of hash, since right now it seems people are migrating away from the SHA1 hash and toward SHA256 (or SHA512 although the two the way they are implemented within gpg are equivalent since the 512 bit hash is truncated to 256 bits).

---

### Post by bodhi.zazen on 2008-05-07
kevdog: Thank you for this post. With the influx of new users I am trying to raise the awareness of Linux security (IMO there are too many posts implying "install Ubuntu and forget about security" ).

I would like to add a link to this thread Here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

If you have time to add to this thread, it will be used. Another suggestion is to add it to the wiki. If you like, with your permission, I can help wiki this information.

---

### Post by Gourgi on 2008-11-04
i'm bumping this cause it just deserves it :lolflag:

this thread contains very interesting and informational stuff!!

@kevdog
I think major reason that this guide didn't attracted much of replies is because it is incomplete.
But surely this guide **DOES** draw attention! This thread has already 1,697 views despite is not completed yet.
Also have in mind that this is an advanced topic, targeting less audience from the ubuntu community.

But i strongly believe tha you should finish your guide and _definitely_  put it in the wiki.

Looking forward to completion :popcorn:

---

### Post by WelterPelter on 2009-01-12
I'd like to see this thread go forward. Please.

---

### Post by bravespear on 2009-01-22
I've added this thread to StumbleUpon.. should get a lot more views shortly.

And I agree, good info.  Please finish the post.

:KS

---

### Post by Kobalt on 2009-01-22
Very interesting reading, I hope to read further more soon. Thank you kevdog.

---

### Post by mgol on 2009-01-25
Excuse me, but... where is this example gpg.conf file? I don't see it at the end of the tutorial, as was mentioned...

---

### Post by kevdog on 2009-01-25
Tutorial is not completed yet -- hence the reason that its missing!!!

---

### Post by speedkreature on 2009-03-19
@kevdog: Thank you for this post.  I, like many others, appreciate the content of what you have written thus far.  You're a little ahead of your time.  By that, I mean you are posting content to a forum littered with users who are really just trying to get their *buntu installations behaving the way they want them.  The current state of personal security is such that it is an afterthought.  When everything else works and is understood, then they begin to explore "newer" concepts such as personal data security and integrity.  

Honestly, my knowledge of Linux is quite limited.  I'm only just beginning to venture beyond a beginner level of knowledge; I can now just barely administer my own systems on the command line with the help of the occasional how to--and I have this forum and members like you to thank for what I have accomplished.

I think that personal data security/integrity will become a very hot topic for the average user in the comming years and I have yet to find any resource as thorough as yours that is intelligible by the average user.  Every "complete" resource I've run across on this topic is either lacking in depth or is inundated with mathematical formulas that I would guess 70%+ of any OS's user base doesn't even know how to read.  There just aren't a lot of people who retain calculus beyond their initial exposure.  You have brought this topic to the masses in a way that we can understand--devoid of mathematical theory and obscure (to most of us) mathematical symbols.

It doesn't have to be kevdog that finishes this content, but it does need to be finished by someone.

*steps off of soap box*

---

### Post by Meson on 2009-03-30
I've always had trouble understanding how subkeys worked.  I once read that it's nice if a particular subkey gets compromised, the user can regenerate his subkeys without having to redistribute because everyone has the master key...

I'm sure there are some other benefits of having multiple signing and encryption keys grouped under the same master key.

Maybe you could elaborate on this topic.

Great article though.  You might consider some links for practical usage; Enigmail comes to mind.

---

### Post by kevdog on 2009-03-31
Ive seen subkeys used in the example if you are going to be using gpg from different computers.  A subkey could be generated for each computer of medium (ie USB stick).  The master key is never put at risk.  This is one of the topics I would like to cover, however when I was playing around with multiple subkeys, something wasnt working and I just lost time trying to figure things out between here and the gnupg mailing list.

I will probably never write on how to use Enigmail.  Ive used the product and its quite good, however I think there are multiple sites that explain how to use Enigmail effectively.  Additionally if you really want to capture the full power of gnupg, you frankly need to default to the command line for some features, since no enigmail gui function has been written.  For most everyday interaction with gnupg, Ive been using FireGPG since it integrates nicely with Gmail.

---

### Post by Meson on 2009-03-31
I didn't expect you to write about enigmail usage, I just thought it'd be helpful for people to see links to projects which make pgp (gnupg specifically) especially usefull.

---

### Post by colsandurz on 2009-04-06
I've found this thread to be very informative.  Thanks!

I would definitely appreciate a tutorial too, especially if you touched generating/using keys with SSH.  That's just my preference though.

Thanks again.

---

### Post by mirabilos on 2009-07-24
Here&#8217;s one, hope you have fun.

Important remark: always use
```
gpg --gen-key --expert
```
for key generation, then you can use
```
   (7) RSA (set your own capabilities)
```
and enable S+C+E+A capabilities (all four of them).

That way you won&#8217;t need the hassle that are subkeys.
Using batch mode, you can even generate longer RSA
keys, similar to what pgp-2.6.3ia allowed.

---

### Post by modafokaxx on 2010-02-14
KevDog, thanks for this really good, clear and precise explanation of GnuPG and PGP.

I'd been meaning to understand more of the nitty gritty of keys and encryption, and your explanation did just that.

I hope you find the motivation to tell us more about the subject, your explanations are great.

Really looking forward to a part 2!

Cheers!

---

### Post by Steve Kinney on 2010-08-19
I will add my thanks for "part one" of a very good tutorial.  I used to be well informed on this subject so I scanned the article pretty quickly, and it brought me up to date on several topics that have changed in important ways and/or emerged since I last paid real attention to the internals of PKI cryptosystems.  Most users will want to go directly to "part two", but the material you have up now is very useful to those of us who need to know how a security tool works before we can sanely trust it.

---

### Post by NertSkull on 2011-03-30
Thank you for the tutorial/information on GPG keys.

I've been slowly getting in to using keys for the past 8 months, and this really helped solidify and clarify some of the concepts I've been trying to pick up on.

I wish more people would get on board with using GPG keys.  

If you do write more on this, I would love to learn more about key servers.  How they work, how you find good ones, how you know one is still active, etc.

But, as it is, it was a great article to read.  Much appreciated!

---

### Post by ghat on 2012-09-06
Key archival...

Paperkey is the "best" archival method known to me..

Are there any better methods. 

Ideally I would like to have a business card size CD-RW or
DVD-RW or BD-RE... I can only find CD-R, and I bet none of these are archival quality... 

I believe even the smart card or USB key may not be safe as the data is stored electronically (electrons in floating gates), they may get erased over time or by water etc...

Ghat

---

