---
title: "is this the best way to secure data?"
date: 2008-01-14
forum: Server Platforms
---

### Post by PetePete on 2008-01-14
i was thinking, if I had some kinda top secret documents that I wanted no one to have access to would this be the optimal solution?..


create a truecrypt volume (file)
mount it..
use virtualbox or similar to create a hard disk within the truecrypt volume
run puppy linux or other lightweight distro and install to virtualbox hdd.

when finished unmount the truecrypt volume..

I was thinking this way it is more secure as all the data is encrypted and its not even possible to view the goings on of the OS.

whats people's thoughts on this? 
The only flaw I could see would be that virtualbox would use the physical memory of your actual computer and put data on there which may be able to be recovered with specialist software (is this even possible, once pc switched off?!)

---

### Post by rivalarrival on 2008-01-14
If someone were REALLY interested in these documents, it would be pretty obvious where you had put them. In theory, the larger the dataset, the easier it is to break the encryption, and your dataset now contains not only the documents but also the operating system and various software. If the attacker knows (or can guess) what the cleartext data is on some part of the encrypted drive (such as the linux kernel?) he can work out a decryption algorithm from this data.

If we're assuming that someone is interested in and has posession of the data, it's just a matter of throwing computing power at it before your encryption fails. All of your eggs are in one basket: if someone breaks your truecrypt encryption, you are compromised. Is this data worth the resources necessary to break it?



As an alternative, I'd recommend something like IronKey ([https://www.ironkey.com/](https://www.ironkey.com/))

This is a secure USB key that "self destructs" if you forget your password or try to bypass its security. Unlike a hard disk, you cannot read the encrypted data directly off the drive and break it at your leisure. Someone would have to physically disassemble the drive (which is metal encased and filled with epoxy) and read the data directly off the chips. It is likely that any attempt to gain physical access would destroy or damage the chips and the data on them. 

Here's the real question: is this data worth the effort for an adversary to extract? Are we talking about dirty pictures or nuclear launch codes? :)

---

### Post by PetePete on 2008-01-14
nuclear blue prints actually :P

I see what you mean by knowing  a plain text value, maybe this is even more secure...

truecrypt volume------virtual hdd ---- truecrypt volume (inside virtualbox disk) --- hidden truecrypt volume ---- files...

then you've got plausible deniability and 2 layers of encryption with the second layer not being weakened from know plain text and also being hidden.

would be ridiculously inconvenient though!

i like the iron key thing, if i had data I was worried about that would seem like a good investment.

---

### Post by Dr Small on 2008-01-14
I know you are wanting to make a truecrypt mount, but the way I encrypt things, is with my public PGP password, and no body can decrypt it.
It works good for just encrypting files / folders or whatnot.

Dr Small

---

### Post by HermanAB on 2008-01-14
The problem with a security system is always on the periphery.  To make the whole system secure, you have to ensure that there are no plain text copies of the file somewhere else.  No print-outs, no paper copies lying around. This is very difficult.

If you are really paranoid, then you also have to think about emissions from the computer, the wires and the screen.  Someone can be in the office next door and monitor everything you are doing wirelessly with a special receiver.  Someone can be across the road or even kilometers away and listen to everything you say by bouncing a laser off the window.  Someone can turn your cell or desk phone on remotely and listen to everything happening around you.

It is only in the Holiwood movies that a PI has to plant a bug in an office.  In real life, the bugs are everywhere already, the cops just need to turn them on.

Cheers,

Herman

---

### Post by kvonb on 2008-01-14
-

---

### Post by PetePete on 2008-01-14
hahahha brilliant post by kvonb!

---

