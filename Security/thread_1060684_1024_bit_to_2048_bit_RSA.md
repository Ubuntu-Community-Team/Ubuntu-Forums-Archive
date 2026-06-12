---
title: "1024 bit to 2048 bit RSA"
date: 2009-02-05
forum: Security
---

### Post by bosworthy on 2009-02-05
Hi,

I've sent the following email, and I did check out some of his links, but since I don't understand the intricacies of the documents, I'll post here and ask for someone to shed some light:

I wrote:

Subject: RE: Entrust SSL Certificates - Error Message Regarding Invalid Certificate

Hi Chris,

I’ll admit I don’t understand the key complexity issues involved in encryption nor if the following is related.  Reading below, _for my info_, does the move from 1024 bit to 2048 bit RSA by 2010 means that RSA 1024 bit encryptions are estimated to be breakable by the most powerful super computers in 2010, thus the need for transition to 2048 bits?  

Thus, does this imply that by 2010, it means that AES 128 and 258 are considered unbreakable?  This assumes the implementation of code is sound.

Does this then mean that even with super secure random long passwords, let’s say 24+ characters, AES 128, 256 encryption can currently be broken if it’s ran on some of the world’s fastest super computer that has thousands of processors?  I vaguely recall that it takes time to compute prime numbers, or something involving prime numbers, or that there are no known efficient algorithms for factoring arbitrary integers, thus the more bits the more secure.

Thanks,


-------------

Chris's response:

I’m not an expert in cryptography, so I’d suggest that you take a look at NIST Special Publication 800-57:
[http://csrc.nist.gov/publications/nistpubs/800-57/sp800-57-Part1-revised2_Mar08-2007.pdf](http://csrc.nist.gov/publications/nistpubs/800-57/sp800-57-Part1-revised2_Mar08-2007.pdf)
[http://csrc.nist.gov/publications/nistpubs/800-57/SP800-57-Part2.pdf](http://csrc.nist.gov/publications/nistpubs/800-57/SP800-57-Part2.pdf)
[http://csrc.nist.gov/publications/drafts/800-57-part3/Draft_SP800-57-Part3_Recommendationforkeymanagement.pdf](http://csrc.nist.gov/publications/drafts/800-57-part3/Draft_SP800-57-Part3_Recommendationforkeymanagement.pdf)

AES encryption is considered sufficient for anything up to classified information:
[http://en.wikipedia.org/wiki/Advanced_Encryption_Standard](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

---

### Post by e1mer on 2009-02-05
I am not sure about your question.

The dates you mentioned are guesses based on brute force
attacks and Moores law, a remarkable observation that has 
held up well against all reason. 
(Moores law cant go past a certain point because
the vacuum tubes can only be made so small!)

No cryptographic method is un-crackable.
The computational difficulty compared to the value of the
data is what makes the difference.  

At the end of the day, xkcd says it best here: 
 [http://xkcd.com/538/](http://xkcd.com/538/)

IMHO, the important thing is to say things like:
"I like Yellow Cake." "Every bomb is A Dirty Bomb."

Then put a block of text to keep the computers busy:
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.2.6 (GNU/Linux)

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
A8ipkmmYutZesAI9sNV2RJU=
=37Eq
-----END PGP MESSAGE-----

---

### Post by movieman on 2009-02-05
> **bosworthy said:**
> Does this then mean that even with super secure random long passwords, let’s say 24+ characters, AES 128, 256 encryption can currently be broken if it’s ran on some of the world’s fastest super computer that has thousands of processors?

Depends on how 'super long' your password is: a 24-character alphanumeric password is only about 128 bits of randomness, and about half that if it's actual English text.

Assuming a secure password, AES-128 could, perhaps, be broken by a super-powerful quantum computer far beyond anything known to exist. AES-256 would last a while even if you build an enormous computer that used every atom in the known universe.

If I remember correctly, the difficulty of breaking a 512-bit RSA key is roughly equivalent to a 56-bit DES key, and a quantum computer can do a brute force search in about the square root of the time taken by a conventional computer; so a 128-bit key for a quantum computer is about as difficult as a 64-bit key for a conventional computer.

---

### Post by bosworthy on 2009-02-14
> **movieman said:**
> 

If I remember correctly, the difficulty of breaking a 512-bit RSA key is roughly equivalent to a 56-bit DES key, and a quantum computer can do a brute force search in about the square root of the time taken by a conventional computer; so a 128-bit key for a quantum computer is about as difficult as a 64-bit key for a conventional computer.


Wasn't DES broken a long while back?

---

### Post by movieman on 2009-02-14
> **bosworthy said:**
> Wasn't DES broken a long while back?

Yes. Which is why you should never use DES or a 512-bit RSA key for anything you want to keep secure.

That was just to give some idea of how the security of an RSA key compares to conventional cryptography; you need at least 10x as many bits to get the same security level.

Personally I use at least 2048-bit keys for SSH because I don't see any good reason not to.

---

### Post by Chayak on 2009-02-14
I think this comic sums up the argument of key strength in a nutshell.  Just because it's so many bits doesn't mean the implementation is at that full strength.  Software crypto is also weaker in the sense of memory key vulnerabilities.  If someone really wants your data there are ways to get it.

There is a different in key strengths when comparing a stream cipher such as RSA and a block cipher such as AES.  A stream cipher takes a stream of bits and encrypts them on the fly, why it's great for web traffic.  AES is a block cipher therefore a 128 or 256 bit key is considered fairly secure.

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

### Post by movieman on 2009-02-15
> **Chayak said:**
> I think this comic sums up the argument of key strength in a nutshell.

Only to the naive. Crackers are far more likely to attack your system remotely than turn up on your doorstep with a baseball bat.

---

### Post by tubbygweilo on 2009-02-15
Or even pay to get access to keys because some form of encryption may be just too hard to crack or take too long so that the information is no longer of any value.

It is reported that NSA are offering '[billions]("http://www.theregister.co.uk/2009/02/12/nsa_offers_billions_for_skype_pwnage/")' for Skype eavesdrop solution but then what do I know?

---

