---
title: "Recover Encrypted Home Partition"
date: 2010-04-26
forum: Security
---

### Post by PerfectReign on 2010-04-26
While setting up my laptop on a new hard drive (a bad mobo caused writes which pretty much rendered teh old hdd unusable) I was asked if I wanted to encrypt my home partition.

I've been wanting this for several years - even going as far as trying to get a copy of CheckPoint. That's waht my organization uses on all Wintendo laptops and is required.

In any case, I said "yes" and am happily using my laptop with an encrypted home partition. I'm assuming based on this - [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/) - that it is using EncryptFS as the scheme.

My question - if I were to misplace my laptop, how easy would it be for a forensics team to retrieve my data. Let's assume I have a fairly strong passphrase, such as BisZumBitterenEnd3.  ([http://en.wikipedia.org/wiki/Bis_zum_bitteren_Ende_%E2%80%93_Die_Toten_Hosen_Live](http://en.wikipedia.org/wiki/Bis_zum_bitteren_Ende_%E2%80%93_Die_Toten_Hosen_Live)!)

---

### Post by limey_rick on 2010-04-27
I imagine that if someone was determined to crack a hard drive, they could do it, but its a question of how long this takes. A 256 should take long enough so that if the key is cracked, the information is not actually useful.

See here for more info: [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by wilee-nilee on 2010-04-27
So tell us why a forensics team would want to know whats on your HD.

---

### Post by P4man on 2010-04-27
limey_rick linked to a page with some nice analogies. I liked this one:

> To understand how secure 128 bit keys are, you may read this analogy by Jon Callas:

&#8220;Imagine a computer that is the size of a grain of sand that can test keys against some encrypted data. Also imagine that it can test a key in the amount of time it takes light to cross it. Then consider a cluster of these computers, so many that if you covered the earth with them, they would cover the whole planet to the height of 1 meter. The cluster of computers would crack a 128-bit key on average in 1,000 years.&#8221; 

Basically a brute force attack is out of the question, even for the NSA and even if computer speed keeps increasing at exponential rates for the next 25 years.

If ever a weakness in the algorithm is detected, or quantum computing becomes a realistic option,  this might change, but then it will not just be your PC at "risk". BTW, the example of the password you gave isnt all that secure, as it *could* be tried in a dictionary attack (adding one number for each). Dont use words or phrases that you get hits on with google :) Well, theoretically speaking that is :)

---

### Post by PerfectReign on 2010-04-27
thank you all, for your answers. I figured as much.

I had written a brute force process in C a few years back, just to check how long it would take to crack an MD5 hash of my then common forum password, all1gat0r.  A P-IV, running SUSE 9.3 took three weeks to brute-force the password.



As for why I asked, it is simple. The laptop is a work laptop, which contains some sensitive data. No SSN's or credit card information but other stuff that my management doesn't want "out there" in the event I lose the laptop.

I had a Fraud Awareness & Prevention seminar at work yesterday, which started me thinking about this.

---

### Post by rookcifer on 2010-04-27
> **PerfectReign said:**
> My question - if I were to misplace my laptop, how easy would it be for a forensics team to retrieve my data. Let's assume I have a fairly strong passphrase, such as BisZumBitterenEnd3.  ([http://en.wikipedia.org/wiki/Bis_zum_bitteren_Ende_%E2%80%93_Die_Toten_Hosen_Live](http://en.wikipedia.org/wiki/Bis_zum_bitteren_Ende_%E2%80%93_Die_Toten_Hosen_Live)!)

It would be impossible for them to recover your data.  If they used every computer on earth to brute force your key, the sun would burn out before they would succeed.

---

