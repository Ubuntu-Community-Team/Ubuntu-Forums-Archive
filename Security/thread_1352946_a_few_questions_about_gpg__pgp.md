---
title: "a few questions about gpg | pgp"
date: 2009-12-12
forum: Security
---

### Post by Andreas1 on 2009-12-12
hi,

i just used seahorse to generate a pgp key. while i understand the basic concept of asymmetric cryptography (thanks to [Little Brother]("http://craphound.com/littlebrother/")), i still have a few practical questions:
```
andreas@aspire:~$ gpg --list-public-keys 
/home/andreas/.gnupg/pubring.gpg
--------------------------------
pub   1024D/2CF803F4 2009-12-12
uid                  **** **** <****.****@****.com>
sub   2048g/272DB220 2009-12-12

andreas@aspire:~$ gpg --list-secret-keys 
/home/andreas/.gnupg/secring.gpg
--------------------------------
sec   1024D/2CF803F4 2009-12-12
uid                  **** **** <****.****@****.com>
ssb   2048g/272DB220 2009-12-12


```
what is my private key and what is my public key in this example? what are sub keys?

is anything in ~/.gnupg stored in plaintext, or is it encrypted by my passphrase, and if so, is it safe to back up that folder somewhere else? (i tend to make symbolic links from my home folder to /media/data/... so i can share selected user settings between different systems). if that is not safe, how do i back up my own private and public key?

why can people who don't have my public key read emails i signed? is the public key sent along?
*EDIT: just found the answer to this one: what's being encrypted is not the actual message but a checksum of the message.*

is there a reason against using the same key for several mail accounts that all belong to me?

if i upload my key to a server, does that mean my friends will automatically retrieve it if they use some pgp tool?

---

### Post by rookcifer on 2009-12-12
> **Andreas1 said:**
> what is my private key and what is my public key in this example? what are sub keys?

Public key is the top one (pub).  The other one is the private key (or subkey).

> is anything in ~/.gnupg stored in plaintext, or is it encrypted by my passphrase, and if so, is it safe to back up that folder somewhere else? (i tend to make symbolic links from my home folder to /media/data/... so i can share selected user settings between different systems). if that is not safe, how do i back up my own private and public key?

The private key should be encrypted (the private key is the one that needs to be, well, private).  And yes, you can, and definitely should, back that .gnupg folder up somewhere safe.

> is there a reason against using the same key for several mail accounts that all belong to me?

Not really.  People might be a bit more hesitant to sign your key.  However, no one should sign a key unless they have seen the person face to face anyway.

> if i upload my key to a server, does that mean my friends will automatically retrieve it if they use some pgp tool?

When you upload the key to one server, it is passed around to the other servers automatically.  So if someone is using Gnupg or PGP, they should automatically be able to import the key.

---

### Post by tubbygweilo on 2009-12-12
> i just used seahorse to generate a pgp key
Andreas1, I trust that you have also created a revocation certificate for each and every key you have just created? If so then keep it safe as you never know when it will be needed. As the keys I use do not change all that often I copy my .gnupg folder to a dvd (more than one copy) and after making sure that the dvd contains everything it should (including all revocation certificates) I then encrypt the dvd using truecrypt. This gives me safe and secure key storage on the off chance that my file system or machine can no longer function as required.

---

### Post by Andreas1 on 2010-02-06
> **tubbygweilo said:**
> Andreas1, I trust that you have also created a revocation certificate for each and every key you have just created? If so then keep it safe as you never know when it will be needed. As the keys I use do not change all that often I copy my .gnupg folder to a dvd (more than one copy) and after making sure that the dvd contains everything it should (including all revocation certificates) I then encrypt the dvd using truecrypt. This gives me safe and secure key storage on the off chance that my file system or machine can no longer function as required.

sorry to bring this up so much later, but no, i haven't. I thought i'd go by the gui (seahorse), because i was insecure ("the gui won't let me do it wrong"). there is no option to generate a revocation certificate in seahorse, but there is a "Revoke" button (right click key > properties > details > subkeys). Does this mean it's ok? If not, how can such a security problem exist in an application that is part of the default install without anyone taking note?

---

### Post by Andreas1 on 2010-02-06
> **rookcifer said:**
> Public key is the top one (pub).  The other one is the private key (or subkey).

i still don't get it. which one do you mean? i see 4 keys: pub, sub, sec, ssb. or are those the same ones again? if so, the helpfile states that dsa keys are only used for signing and elgamal keys are only used for encrypting. so, since my public key is dsa (the 1024bit one), how would someone else be able to encrypt a message for me?

---

### Post by tubbygweilo on 2010-02-06
Andreas1, As I use my keys mainly to sign and encrypt emails I manage them via Openpgp in Mozilla Thunderbird when used with the Enigmail extension from the repos, this gui allows me to do all that I need. 

The information required to create a revocation certificate can be seen in section 3 of the Gunpg [How To]("http://dewinter.com/gnupg_howto/english/GPGMiniHowto-3.html") using a couple of command line commands. The revocation certificate should be crated and held safely and securely against the time when it is required for use. 

Although I have not tried the revoke button in Seahorse I have the feeling that this may well crate and apply a revocation certificate on the fly and so revoke a key as soon as the button is clicked but I'm not sure.

Worth a read [GPGMiniHowto.]("http://dewinter.com/gnupg_howto/english/GPGMiniHowto.html")

---

### Post by Vined Adobo on 2010-02-12
My understanding of ubuntu 91.0 and the default version of seahorse which comes with it:

You can EXPORT an ascii version of your public key (make sure it's your PUBLIC key!) and include that in a signed document you send to the person who you desire an encrypted document from.  They will use the public key you send them and their secret key to encrypt the file they send you.  You will use your secret key and their public key (have them send you their public key) to decrypt the message.

To make this all easier, you can publish your key to a key server such as keyserver.ubuntu.com:11371 (seahorse should only publish your public key.)  When you receive an encrypted message, you can search the key server for the sender's public key so you can decrypt the message.  At least this is the way I understand it.  To  me, the documentation seems to be written for PhD's and I have great trouble understanding any of it.  I have sent signed and encrypted messages to and from other email accounts I have, and this seems to be the way it works.

Signed messages are sent in the clear, and anyone can read them.  The signature part of it is so you can go to a key server and ensure the sender really did send and sign that document.

In my version of ubuntu and seahorse, I can create, sign, and publish keys, but i can only delete a sub key and cannot revoke or truly expire a key.  If I revoke a key, nothing at all happens.  If I expire a key, I have to re-publish it, and then there are two identical keys on the key server.  One which never expires, and one which will expire.  The one which never expires doesn't expire.  The only way I have found to revoke a key is to open a terminal and use gpg to make a revocation certificate.  Type 'man gpg' (no quotes) in a terminal to find options.  After reading a little, it makes better sense than seahorse anyway.

Oh, the only way to export a PUBLIC key that works for me is to do it from gpg in terminal.   Seahorse doesn't seem to work well at all.

You can open two terminals at once.  One for man gpg, and one to type commands.  Slick.  Just copy from one terminal and paste to the other.

I wonder if there is a test keyserver... it would be nice to practice before you publish to an official keyserver.

Have I got all this right, or am I missing a BIG piece of the puzzle?

Dave

---

### Post by rookcifer on 2010-02-13
> **Vined Adobo said:**
> My understanding of ubuntu 91.0 and the default version of seahorse which comes with it:

You can EXPORT an ascii version of your public key (make sure it's your PUBLIC key!) and include that in a signed document you send to the person who you desire an encrypted document from.  They will use the public key you send them and their secret key to encrypt the file they send you.  You will use your secret key and their public key (have them send you their public key) to decrypt the message.

To make this all easier, you can publish your key to a key server such as keyserver.ubuntu.com:11371 (seahorse should only publish your public key.)  When you receive an encrypted message, you can search the key server for the sender's public key so you can decrypt the message.  At least this is the way I understand it.  To  me, the documentation seems to be written for PhD's and I have great trouble understanding any of it.  I have sent signed and encrypted messages to and from other email accounts I have, and this seems to be the way it works.

Signed messages are sent in the clear, and anyone can read them.  The signature part of it is so you can go to a key server and ensure the sender really did send and sign that document.

In my version of ubuntu and seahorse, I can create, sign, and publish keys, but i can only delete a sub key and cannot revoke or truly expire a key.  If I revoke a key, nothing at all happens.  If I expire a key, I have to re-publish it, and then there are two identical keys on the key server.  One which never expires, and one which will expire.  The one which never expires doesn't expire.  The only way I have found to revoke a key is to open a terminal and use gpg to make a revocation certificate.  Type 'man gpg' (no quotes) in a terminal to find options.  After reading a little, it makes better sense than seahorse anyway.

Oh, the only way to export a PUBLIC key that works for me is to do it from gpg in terminal.   Seahorse doesn't seem to work well at all.

You can open two terminals at once.  One for man gpg, and one to type commands.  Slick.  Just copy from one terminal and paste to the other.

I wonder if there is a test keyserver... it would be nice to practice before you publish to an official keyserver.

Have I got all this right, or am I missing a BIG piece of the puzzle?

Dave

I know how you feel.  It can be difficult to learn all of that stuff.  It gets especially confusing because the rules are different for different types of keys.  For instance, DSA keys are only for signing and ElGamal are only for encryption.  RSA can do both encryption and signing.

BTW, it is recommended that you begin phasing out DSA keys since they rely on the weak SHA-1 hash.  The default key generated in gpg 1.4.10 is going to be RSA-RSA.  RSA is recommended because it can utilize the stronger SHA2 (SHA224, 256, 384, 512).  So, it is probably best to begin creating 4096 bit RSA keys (one for singing and one for encryption).  These should last a number of years into the future (right now it is predicted that 4096 will be good for another 20 years).

---

