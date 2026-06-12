---
title: "PGP Support?"
date: 2010-01-01
forum: Security
---

### Post by Tamalin on 2010-01-01
I want to send a PGP encrypted file to a friend who (unfortunately) probably doesn't even have any idea what PGP is.  He runs Windows XP.  I know I can encrypt and decrypt PGP files easily and freely on Ubuntu, but I have no idea about how to handle PGP in XP...  I tried downloading a PGP file in an XP virtual machine to find out, and Windows was pretty much unable to identify the file type.  What kind of software on Windows (that is completely free and trustworthy) would be able to decrypt my PGP files?
Thanks!

---

### Post by __p1n__ on 2010-01-01
Tell your friend to dl/install gnupg.  Your friend will need to generate a key-pair and send you the public key.  Add that latter to your keyring and encrypt the file(s) with it.  Your friend can run gpg from a CMD box in windows and decrypt the file.

---

### Post by Tamalin on 2010-01-01
Ok, Thanks...  I gonna have to tell him how to use a command prompt though...  Quite disappointing...  I wish he'd quit XP, this would be so much easier.

---

### Post by rookcifer on 2010-01-01
PGP is proprietary.  GnuPG is the FLOSS version of it, and can be used on 'doze or Linux.  GnuPG should be fully compatible with those using PGP on Windows.  So, just tell your friend to either use PGP (probably easier) or help him install GnuPG.  It will probably be easier just to tell him to use the free version of PGP.

---

### Post by michaelzap on 2010-01-01
> **rookcifer said:**
> PGP is proprietary.  GnuPG is the FLOSS version of it, and can be used on 'doze or Linux.  GnuPG should be fully compatible with those using PGP on Windows.  So, just tell your friend to either use PGP (probably easier) or help him install GnuPG.  It will probably be easier just to tell him to use the free version of PGP.

PGP 8 works well on XP and is available for free:
[http://www.pgpi.org/products/pgp/versions/freeware/winxp/8.0/](http://www.pgpi.org/products/pgp/versions/freeware/winxp/8.0/)

You're lucky he doesn't have Vista, since PGP 8 doesn't run on Vista.

---

### Post by Bobulous on 2010-01-02
Just remember that you need to meet in person to exchange public keys. It's the only way to be sure that you're getting the keys from each other, and not from some shadowy interceptor sat on your connection.

(Okay, I know there's little chance of that, but if you're gonna do security, you should do it properly.)

The funniest thing I heard about encryption in recent months was when a security consultant was feeling pleased with himself because he'd arranged to encrypt a file before it was transmitted by email. I had a bad feeling, so I asked him: "you're not gonna send the password by email too, are you?" He thought for a moment and then said, "Uhm, I'm not now, no." It hadn't occurred to him until then that if the encrypted file was intercepted, the password sent by email would be acquired exactly the same way.

---

### Post by JackRock on 2010-01-02
> **Bobulous said:**
> The funniest thing I heard about encryption in recent months was when a security consultant was feeling pleased with himself because he'd arranged to encrypt a file before it was transmitted by email. I had a bad feeling, so I asked him: "you're not gonna send the password by email too, are you?" He thought for a moment and then said, "Uhm, I'm not now, no." It hadn't occurred to him until then that if the encrypted file was intercepted, the password sent by email would be acquired exactly the same way.

*facepalm*

---

### Post by kevdog on 2010-01-02
GnuPG has a couple of good frontends --

FireGPG is a firefox extension

WinPT is a good frontend for windows as well.

---

### Post by rookcifer on 2010-01-03
> **Bobulous said:**
> Just remember that you need to meet in person to exchange public keys. It's the only way to be sure that you're getting the keys from each other, and not from some shadowy interceptor sat on your connection.

Why would two people need to meet in order to share public keys?  Public keys, by their nature, are public.  I can put my public key out there and anyone who has it can send me encrypted mail.  If they get a public key from someone pretending to be me, I simply will not be able to decrypt their e-mail and can let them know they are using the wrong key.

I think you are confusing encryption keys with public *signing* keys.  Indeed, if one wants to have a "key signing party" it should be done in person.  Key signing is really only useful for building a web of trust, but is not necessary for merely sending encrypted messages.  Naturally, it is not a good idea to sign keys and give them ultimate trust unless you have met with the person and they have provided a picture ID.

---

### Post by Bobulous on 2010-01-03
Well, so long as you perfectly recognise the person's voice, you could just email the public keys to each other and then read out over the phone the hash of each key, to confirm that the keys haven't been tampered with on the journey.

But you do need to make sure you can completely trust that the key belongs to the person you think it belongs to, otherwise you're assuming that you're not already being monitored. And if you're that confident, then you don't need encryption anyway.

I used to be part of Thawte's Web Of Trust (which has sadly been wrapped up now due to the cost to Thawte to maintain it). To have your name attached to email certificates you had to have your identity asserted by existing members, and they'd have to meet you in person, see your passport (and take a photocopy of it) and confirm that you were who you said you were. Meeting in person was the only way to be sure.

---

### Post by BkkBonanza on 2010-01-03
You should do some test exchanges of messages first so you can test that you each have the correct keys for each other. Sign and encrypt the messages and if you get the correct messages back then you can be sure you're ready to go with real data.

If you plan to send the file by email then you can install and use Enigmail quite easily on Linux or Windows for Thunderbird. I don't think it works with Outlook but I'm sure I heard there is an equivalent to Enigmail that is compatible and easy to install.

---

### Post by Sarmacid on 2010-01-04
I exchanged keys with a friend a couple of years ago and she was using Windows too. There was a program called PortableGPG, it was nice and easy to work with.

---

### Post by nanotube on 2010-01-04
> **rookcifer said:**
> Why would two people need to meet in order to share public keys?  Public keys, by their nature, are public.  I can put my public key out there and anyone who has it can send me encrypted mail.  If they get a public key from someone pretending to be me, I simply will not be able to decrypt their e-mail and can let them know they are using the wrong key.


you will not be able to decrypt their email - but the person who was pretending to be you, and whose public key they used to encrypt, /will/ be able to decrypt their email. epic fail. since the whole point of encryption is to prevent third parties from reading the content, and since the person pretending to be you is just such a third party... you get the point.

so, while you don't have to meet in person, you should at least verify the key hash by phone (assuming you can recognize the person by voice).

---

### Post by rookcifer on 2010-01-04
> **nanotube said:**
> you will not be able to decrypt their email - but the person who was pretending to be you, and whose public key they used to encrypt, /will/ be able to decrypt their email. epic fail. since the whole point of encryption is to prevent third parties from reading the content, and since the person pretending to be you is just such a third party... you get the point.

That scenario is unlikely.  If someone wants to contact me, they can get my key from any server.  The only way our conversations would be compromised is if they snatch the wrong key, which would be unlikely, especially if they know my e-mail addy and can match it to a name. 

I suppose it all depends on how confidential the conversation needs to be.  If it's national security, then yes, one would want to meet in person to verify the keys before any e-mail exchange took place.  If it's just some random person wanting to e-mail another random person, simply snatching the keys off a server should suffice.  Again, this is saying nothing about signing keys -- key signings always need to be done in person since they are used for webs of trust.

> so, while you don't have to meet in person, you should at least verify the key hash by phone (assuming you can recognize the person by voice).

That is fine if one knows the person beforehand, but if one knows the person, usually key verification isn't necessary.  It really depends on how person A came across person B to begin with.  Usually it's from visiting their website or coming across them in a forum (such as this).  In that case, snatching the correct key should be straight forward.

---

### Post by nanotube on 2010-01-04
> **rookcifer said:**
> That scenario is unlikely.  If someone wants to contact me, they can get my key from any server.  The only way our conversations would be compromised is if they snatch the wrong key, which would be unlikely, especially if they know my e-mail addy and can match it to a name. 


well, of course it's unlikely. but you're the first one to have posited the existence of someone pretending to be you. presumably, if there's someone actively pretending to be you and distributing a fake gpg key, that someone is specifically interested in communication you might receive, etc, etc. was just going along with your scenario. :)

in 'real life' just grabbing a key off a server is quite acceptable to me, so i think we're basically agreeing with each other.

---

