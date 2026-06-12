---
title: "Does this change anything vis-a-vis Whole Disk Encryption?"
date: 2008-02-22
forum: Security Discussions
---

### Post by euler_fan on 2008-02-22
I have been reading Scheier's newsletter and found this article talking about a [new]("http://www.schneier.com/blog/archives/2008/02/cold_boot_attac.html") [attack]("http://www.freedom-to-tinker.com/?p=1257") which can be used to circumvent whole disk encryption.

Does this change anything from a practical point of view or will we all simply need  to be a little more careful about the physical security of our machines?

---

### Post by kiloecho7 on 2008-02-23
It will sure keep me from leaving my laptop in hibernate when I leave home for a long time . . . but on a different level, the following deterrents will probably become a little more main stream from now on.
1. Bios makers permanently setting their chips to scramble the ram on every shut down.
2. Cable locks that not only prevent someone from running off with your computer but that also prevent the RAM compartment from being opened when in the locked position.
3. OTFE software that wipes the key over a few times after un-mounting the encrypted volume.

Anyways, it was stated quite wisely a while ago, that "If a bad guy has unrestricted physical access to your computer, it's not your computer anymore."  (Microsoft's Immutable Laws of Computer Security, Law #3)

---

### Post by michaelzap on 2008-02-23
I would expect that #3 will be implemented in encryption software packages soon, as I imagine it would be the easiest way to resolve this (I'm still amazed that RAM has some permanence after the power is off...).

---

### Post by NiN on 2008-02-23
This doesn't change anything. It has been well known (at least at universities) that RAM does hold information for some time.

Therefore a standby mode like suspend to ram has always been dangerous.

Suspend to disk has many attack vectors, because many passwords are stored to unencrypted swap (therfore every swap partition should use dmcrypt with random passwords to make them unrecoverable).

This has been suggested for some time now, but this news may bring new attention to this form of attack. (heared something similar last year at a conference)

But still, an attacker with full physical access may also simply attatch a firewire device to read out the memory. (so always load the firewire module, otherwise it is bios controlled)

[edit]
Typos

---

### Post by bismark on 2008-02-26
My question is how would this affect a setup down with SmartCards such as this one? [https://help.ubuntu.com/community/EncryptedFilesystemHowto4](https://help.ubuntu.com/community/EncryptedFilesystemHowto4)

If the attacker didn't have the smartcard would they still be able to access this system after retrieving the systems memory?

---

### Post by solitaire on 2008-02-26
As ALL key's are held in memory (even smart keys) then having encryption running all the time on your comp is idiotic!! 

you should only use it when it's required (Encrypted drives are only useful if everything you are doing is illegal in the country you are in, or if the data is so sensitive that you require encryption then why the hell have you got it outside the company building!!)....

It only changes things if the Police Kick down your door and your comp is on.

Otherwise after 20 mins in room temp the info in the memory is next to useless..

Also if you keep Laptops on Hibernate / Standby then you deserve all you get :D lol!! A few mins of wait is better than a few hours in the Cells waiting for the police to dump your memory and nosey they way through your personal info..

---

### Post by bismark on 2008-02-26
> **solitaire said:**
> As ALL key's are held in memory (even smart keys) then having encryption running all the time on your comp is idiotic!! 

you should only use it when it's required (Encrypted drives are only useful if everything you are doing is illegal in the country you are in, or if the data is so sensitive that you require encryption then why the hell have you got it outside the company building!!)....

 
Hmmm nice assumption that all people who use encryption are criminals or doing something illegal.  

I have\use it for two reasons, 1) my data is my data legal or otherwise, not someone else's,  2) my clients data is their data and they would very much like any confidential information that I have to stay that way, confidential. Since I travel a lot, using a desktop is not an option.


Now the way I understood the smartcard setup to work was that it had to be present for any decryption to take place.  If it was removed then the system can not access anymore then what was in memory.  My assumption here is probably wrong, if it is, is there a way to setup disk encryption to work this way.

---

### Post by solitaire on 2008-02-26
think that's more your assumption

Amnesty international used Encryption all the time due to it's involvement in nations which limit civil liberties!

That's way i said "illegal in the country you are in" rather than "Doing Illegal things"

Small but major difference :D:D

But i get where you were coming from..

---

