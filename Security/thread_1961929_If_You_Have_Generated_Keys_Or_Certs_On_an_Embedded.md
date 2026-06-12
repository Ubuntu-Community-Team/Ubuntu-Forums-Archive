---
title: "If You Have Generated Keys Or Certs On an Embedded Device, Read This!"
date: 2012-04-20
forum: Security
---

### Post by rookcifer on 2012-04-20
Two different independent studies by two different groups of researchers revealed a major public-key compromise.  Both groups of researchers probed millions of SSL, SSH and PGP keys/certs on the Internet and found that as many as 1% (maybe more) are completely comrpromised.  The researchers were not only able to discover which ones were vulnerable, but they actually *broke them all* (i.e, they factored all the primes). This means if these researchers were bad guys and you were using one of these keys/certs, they could read all your encrypted mail and sniff your SSH traffic easily.  They could even set up a fake website with your SSL cert.  As they said in their reports, "if we can do this, we are certain that either criminals or government agencies have long ago done the same thing."

It turns out most of the bad keys and certs were of the RSA variety (symmetric ciphers like AES weren't affected, this only applies to public-key crypto).  The reason for this is the way RSA generates the key: It has to choose two different random primes during the generation process.  In contrast, DSA and Elgamal only use one.  What happened is the researchers discovered many thousands of keys which shared one common prime number.  This allowed them to identify the bad keys.  Statistically, even among millions of samples, this should not happen, yet they found many thousands of examples where it did.  Most of the keys were RSA 1024 bit, but some 2048 bit keys were compromised as well.

The first group of researchers sort of blamed RSA.  The second group (who did their research independently and with a different sample set) said not so fast.  It is more of a problem with how the keys are generated than with the algorithms themselves.  It turns out the reason for this disaster is that some machines out there on the internet are generating random numbers that aren't so random.  The second group of researchers identified most of the machines the bad certs/keys were on and said the vast majority of them were generated on routers or embedded devices.  They said most every major router/VPN manufacturer had bad keys in the sample.  Moreover, most of the bad keys appeared to be generated using the OpenSSL library.

So why are embedded devices so affected?  Because generating entropy on them is near impossible due to the lack of inputs.  This means that the entropy state is small and these routers will often start with the same seed or a very small number of seeds.  This is bad.  Very very bad for crypto.  It's really just as bad as using the day and time as a seed for a PRNG.

This news is sort of shocking due to the scope of how many keys were affected, but not really surprising either.  People in some circles have been warning for a long time that generating crypto keys on embedded devices is a very bad idea.  Device manufacturers are going to have to take a close look at how they can provide some means of entropy generation.

So, basically, if you have a router that you have generated, say, an SSH key on, it is probably a very good idea to go ahead and scrap that key.  If possible, generate the key-pair on a standalone desktop machine that utilizes /dev/random (I know GnuPG uses /dev/random to seed to CSPRNG).  Even though OpenSSL was used most often to generate the bad keys, it doesn't necessarily mean there's a flaw with it.  It probably just means more people use that library than the alternatives (though I hope the OpenSSL guys take a look at their code to see if there is anyway to improve the RSA prime generating process).


Ars Technia article which puts it all together: [http://arstechnica.com/business/news/2012/02/crypto-shocker-four-of-every-1000-public-keys-provide-no-security.ars](http://arstechnica.com/business/news/2012/02/crypto-shocker-four-of-every-1000-public-keys-provide-no-security.ars)

First study paper here (.PDF): [eprint.iacr.org/2012/064.pdf]("eprint.iacr.org/2012/064.pdf")

Second study overview here: [https://freedom-to-tinker.com/blog/nadiah/new-research-theres-no-need-panic-over-factorable-keys-just-mind-your-ps-and-qs/](https://freedom-to-tinker.com/blog/nadiah/new-research-theres-no-need-panic-over-factorable-keys-just-mind-your-ps-and-qs/)

---

### Post by matt_symes on 2012-04-20
Thanks for posting this. Most interesting indeed.

---

### Post by CharlesA on 2012-04-20
Thanks for posting. :)

I'm glad the key I use for my router at home is generated on a desktop machine and pushed over.

---

### Post by Johan Ryberg on 2012-04-20
It seems like users of ssh for example thinks they are invincible just because they use private/public keys and ignores to use a firewall and just let trusted ip/network to access the machines. 

  -- Johan Ryberg

---

### Post by CharlesA on 2012-04-20
> **Johan Ryberg said:**
> It seems like users of ssh for example thinks they are invincible just because they use private/public keys and ignores to use a firewall and just let trusted ip/network to access the machines. 

  -- Johan Ryberg
That sounds like a bit of a generalization. Using keys might add another layer of security, but it is still a good idea to lock down and firewall any service you have exposed to the internet.

---

### Post by Johan Ryberg on 2012-04-20
> **CharlesA said:**
> That sounds like a bit of a generalization. Using keys might add another layer of security, but it is still a good idea to lock down and firewall any service you have exposed to the internet.
Yes, exactly but as far as I have seen way to many users lets 0.0.0.0/0 access 22/tcp without any further thoughts and thinks that their private/public keys are good enough.

---

### Post by rookcifer on 2012-04-21
> **Johan Ryberg said:**
> It seems like users of ssh for example thinks they are invincible just because they use private/public keys and ignores to use a firewall and just let trusted ip/network to access the machines. 

  -- Johan Ryberg

That's not really the issue here.  This has to do with the keys themselves being broken from the start because they were generated with insufficient entropy.  Hiding bad keys is not the solution. That's merely security through obscurity.  Indeed the whole point of public-keys is to *share* them with third parties.  In most cases this is necessary like with SSL certificates.

The solution is to make sure the key is strong at the start, and to do that you should *not* trust your embedded device to generate them.  You should generate them with a desktop machine that utilizes /dev/random (or a hardware TRNG) and then push them to the embedded device.

The problem, again, is that cryptographically secure random number generation is hard.  It's one of the hardest problems in cryptography.  No matter how well designed your ciphers are, with weak random numbers, the whole system falls apart and is easily broken.  Finding practical means of generating strong and unpredictable numbers is tough in many circumstances.  This study shows that with the current generation of embedded devices, it is almost impossible.

The solution is for the hardware makers to design hardware TRNG's that are in every device.  With current technology this should not be all that hard to do (though care needs to be taken in the design).  Via has TRNG's in some of their processors and has for years.  Intel [has said]("http://spectrum.ieee.org/computing/hardware/behind-intels-new-randomnumber-generator/0") they are going to put a TRNG on all upcoming Ivy Bridge processors (a good read if you're interested in their design).  I am hoping AMD does the same thing at some point.  But, these are mostly desktop processors and desktops are not really the problem right now.  Embedded device makers need to find similar solutions.

---

