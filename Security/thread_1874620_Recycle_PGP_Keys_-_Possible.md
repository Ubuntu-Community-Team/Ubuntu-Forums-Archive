---
title: "Recycle PGP Keys - Possible?"
date: 2011-11-03
forum: Security
---

### Post by badinoff on 2011-11-03
I am a newly converted Ubuntu user, coming off of Windows. Ubuntu has PGP encryption as a standard feature, so I have been playing around with it.

I barely have any knowledge of how encryption works so my question below may be stupid, but I could not find any threads discussing it.

I created a set of PGP keys (private and public) on my physical machine, but I would like to be able to use the same set on other (virtual) machines. 

I am curious if my private key can be copied from one machine to another in order for me to be able to use the same one and not create separate ones for each computer.

---

### Post by haqking on 2011-11-03
> **badinoff said:**
> I am a newly converted Ubuntu user, coming off of Windows. Ubuntu has PGP encryption as a standard feature, so I have been playing around with it.

I barely have any knowledge of how encryption works so my question below may be stupid, but I could not find any threads discussing it.

I created a set of PGP keys (private and public) on my physical machine, but I would like to be able to use the same set on other (virtual) machines. 

I am curious if my private key can be copied from one machine to another in order for me to be able to use the same one and not create separate ones for each computer.

depending on the tool you are using (probably seahorse) then choose to export key.

Export it to location of choice and then use import.

---

### Post by badinoff on 2012-04-02
> **haqking said:**
> depending on the tool you are using (probably seahorse) then choose to export key.

Export it to location of choice and then use import.

Thanks for responding! 

I am indeed able to export an .asc file, which only contains the public key. So when I import that file on a different machine (using Gpg4win), I can only use it to decrypt. I am curious if there is a way to export the private key, so that I can use it to encrypt on any machine. Hope this makes sense.

---

### Post by kevdog on 2012-04-02
Couple of things I would suggest -- I'm not sure the name of the program that generated your pgp keys, however I'm wondering if your program is capable of handling gpg keys.  gpg is the open source equivalent of pgp and both adhere to the opengpg standard.  I know for a fact gpg4win and other windows type programs (ie enigmail) handle gpg keys and gpg keys are cross-compatible across many platforms.  I also know for a fact its possible to export copies of gpg private and public keys and import them into keyrings on different computers to use.  One of the tenants of security however is to try to limit the number of copies of private keys.  Ideally there should be only one copy of your private gpg/pgp keys -- if everyone had a copy, it wouldn't be so secure.  Copying the same key to multiple computers increases your risk, however if you've evaluated your own personal situation and found this risk to be negligible, then it can definitely be done.

---

### Post by haqking on 2012-04-03
> **badinoff said:**
> Thanks for responding! 

I am indeed able to export an .asc file, which only contains the public key. So when I import that file on a different machine (using Gpg4win), I can only use it to decrypt. I am curious if there is a way to export the private key, so that I can use it to encrypt on any machine. Hope this makes sense.

actually technically speaking (mathematically speaking) either the public or private key can encrypt or decrypt the other (it is a misconception that only one can do a certain job)

And in your example you have it round wrong way as the private key is what would conventionally be used to decrypt as the public key is used to encrypt conventionally speaking (although that sounds like im contradicting myself im not if you read it carefully ;-)

but if data was encrypted with the public/private then the other would decrypt/encrypt it.

However it would seem there is an issue with seahorse not sure if it is a bug or it purposely differentiates the 2, anyways  as far as i can remember you can export the public key to a .asc file or export both to a tar file but not both to a .asc file or private to .asc

Cheers

---

### Post by ottosykora on 2012-04-03
in passwords and encryption keys

go to own keys, right clcik on the *key pair* , properties, details tab, 
down right side 'export whole key'


this will produce .asc file with complete key pair, unless: you did deliberately mark the private key as non exportable at some time during the creation.

---

### Post by rookcifer on 2012-04-16
The simplest solution to do what you want is to navigate to /home/username and then find the directory named ".gnupg".  Copy the entire directory and then paste it into your virtual machine at the same location.  At that point, GnuPG should work just the same on the virtual machine as it does on your physical machine.

In fact, it is a good idea to backup that entire directory somewhere (like a CD or backup drive) so you will always have it.  Just be sure your private key is protected by a good strong password, and it will be secure.

---

### Post by Dangertux on 2012-04-16
Haqking i am not saying you are wrong but I am rather confused about what you said.

With pgp if you encrypt to the public key. The private key will decrypt it. However if you encrypt to the private key anyone who holds the public key can then decrypt it.

Is this understanding correct or am i missing something?

---

### Post by haqking on 2012-04-16
> **Dangertux said:**
> Haqking i am not saying you are wrong but I am rather confused about what you said.

With pgp if you encrypt to the public key. The private key will decrypt it. However if you encrypt to the private key anyone who holds the public key can then decrypt it.

Is this understanding correct or am i missing something?

yeah my wording was terrible ;-)

I was trying to say that though we use the terms public and private and often it is assumed that only the private can decrypt.

I was saying mathematically it works both ways.

I was more being pedantic than helpful ;)

---

### Post by ottosykora on 2012-04-18
>actually technically speaking (mathematically speaking) either the public or private key can encrypt or decrypt the other (it is a misconception that only one can do a certain job)<

correct, but practically not so simple as the software used to do it, pgp or gpg will prevent you doing that as it will detect both keys in keyrings.
It will need quite some work to get the private key alone to be inside the public key ring, but yes it is possible with quite some manual work.



>anyways as far as i can remember you can export the public key to a .asc file or export both to a tar file but not both to a .asc file or private to .asc<

one can export public key or key pair (both public and private) to .asc, this is just the ascii format of the binary form, but it can be also exported in other formats. But the asc is default as it is convenient for handling and storing etc. In case of public key, it is also fine for transmission via e-mail, as it does not need to be ascii coded and therefore mutilation on transport is less likely.

---

### Post by donsy on 2012-04-20
As a somewhat related issue what would be the harm in storing the complete key on a public medium such as Google Docs, provided that the private key is protected by a very strong passphrase?

---

### Post by rookcifer on 2012-04-20
> **donsy said:**
> As a somewhat related issue what would be the harm in storing the complete key on a public medium such as Google Docs, provided that the private key is protected by a very strong passphrase?

Absolutely nothing wrong with that.

---

### Post by ottosykora on 2012-04-21
> **donsy said:**
> As a somewhat related issue what would be the harm in storing the complete key on a public medium such as Google Docs, provided that the private key is protected by a very strong passphrase?

if the passphrase is strong , well it will be rather difficult to use the key pair, but I was always told that if someone has your complete keypair and not the passphrase, he is just about half the way from successful attack then not having the private key.

Therefore you will get instruction in all sorts of pgp and gpg readmes to hide your private key as much as possible and make sure no one can get hold of it.

In fact, when I know or have to assume that my private key might have leaked somewhere out of my control, I revoke the key and create a new one.

How important the protection of the private key is, you can estimate from the effort done with the digital signing systems introduced in many countries now.
The private key is completely hidden inside a usb media and this is done that way that the key is complete non exportable and can not be accessed or otherwise copied out of the media and only a utility running inside the media can use the key. So now passphrase is needed, but if key would be available, attacks are apparently known to reconstruct passphrase from enough cryptdata or do simply without it.

I just remember that one of those attacks, the 'czech attack' was dealing with stealing private key without passphrase, but I think this applied to certain quality of keys only.


----
from pgp manual:

>Never give your secret key to anyone else.  For the same reason, don't
make key pairs for your friends.  Everyone should make their own key
pair.  Always keep physical control of your secret key, and don't risk
exposing it by storing it on a remote timesharing computer.  Keep it
on your own personal computer.<

---

### Post by rookcifer on 2012-04-21
> **ottosykora said:**
> if the passphrase is strong , well it will be rather difficult to use the key pair, but I was always told that if someone has your complete keypair and not the passphrase, he is just about half the way from successful attack then not having the private key.

All GPG private keys are encrypted symmetrically using a 128 bit cipher.  I actually have GPG set to encrypt my private key with AES-256.  Good luck to anyone getting that.

Since the private-key is itself encrypted, there's nothing wrong with storing it on a remote machine, *as long* as you use a very strong passphrase.

---

### Post by ottosykora on 2012-04-22
> **rookcifer said:**
> All GPG private keys are encrypted symmetrically using a 128 bit cipher.  I actually have GPG set to encrypt my private key with AES-256.  Good luck to anyone getting that.

Since the private-key is itself encrypted, there's nothing wrong with storing it on a remote machine, *as long* as you use a very strong passphrase.

this is unfortunately quite irrelevant, as it is not needed to decrypt the key:
[http://cryptome.org/pgp-email-flaw.htm](http://cryptome.org/pgp-email-flaw.htm)

however, most current pgp/gpg core programs were patched to some extend against that attack, some old versions will remain vulnerable to it unfortunately.

Simple expressed: the key could be modified as it is, rather then decrypted etc.

just get google search for 'pgp czech attack' and crowl in all those discussions threads etc.
AFAIK there was kind of patch issued 24h later for some versions to kind of complicate this attack however.
But you see, that encryption alone is not always automatically security.

---

### Post by rookcifer on 2012-04-22
> **ottosykora said:**
> this is unfortunately quite irrelevant, as it is not needed to decrypt the key:
[http://cryptome.org/pgp-email-flaw.htm](http://cryptome.org/pgp-email-flaw.htm)

That attack requires the attacker to have physical access to your machine.  Also this flaw was fixed many years ago (the article is from 2001) and only applied to *DSA signatures* (not encryption).  It in no way would allow an attacker who grabbed your encrypted private key off the web somewhere to be able to "decrypt" that key.  He would need physical access to your machine as you were performing encryption with your key.

Bottom line, if your key is stored somewhere offsite encrypted with AES, the attacker would have to find a flaw with AES, its implementation, or with your password in order to get your key.  Since your password is by far the weakest link, it should be very strong.

---

### Post by ottosykora on 2012-04-22
no , it has nothing to do with your machine directly, it is about simply accessing your machine and getting your private key and changing it and put it back possibly. No decryption takes place etc. It is simply that someone has the key file he can change the key file and use it for signing. This means not only some clersigning, but also signing of session keys on encrypted traffic etc. There is no passphrase  or decryption of traffic involved in fist place. The access to the lokal machine is mentioned just in the case that this is the only place you store your key.

If you store your key elsewhere, there is no problem to get it as it is. Modify it so it looks like the original, but it is not, and place it where the original was before.

That was the base of that attack. And this is therefore the reason, why private keys in the case of serious public key systems are so much protected physically. E.g definitely non exportable from any media, no way of backup or similar.
All my commercial key pairs are protected this way, the private key definitely not possible to get onto. Even the new digital signature systems for certifying documents or mails are using completely locked storage for the private key. If a software wants to use it, get signature for example, it has to send the data to the processor locked in similar protective environment as the key and it will create the sig and pass it to the application again.

The same does my banking card. Keypair created inside the card and only public key can be exported and signed and imported again. The issuer of the banking card knows well that private keys of the x.509 can still be manipulated so the original user does not find out immediately. As they are responsible to certain amount to the bank as what problems may come up, they choose the way of complete physical protection of the private key. And the liability here is just in the order of 100 000$.




So yes, there was a patch issued for some versions after 24h, but this patch is only to make it kind of more complex. To get rid of the problem, one would need to develop half of the asymetric crypto system new.

So while the particular so simple solution was closed by the patch, the problem is not solved for all ages.

---

### Post by rookcifer on 2012-04-22
> **ottosykora said:**
> no , it has nothing to do with your machine directly, it is about simply accessing your machine and getting your private key and changing it and put it back possibly. No decryption takes place etc. It is simply that someone has the key file he can change the key file and use it for signing. 

I read the paper.  It seems what happened is some ancillary file had a little bit of data leakage about the private key.  This file was not encrypted (as the private key itself was).  Therefore, if the attacker can alter that data, he can possibly forge signatures with your key after he watched you sign a document.

Either way, this attack requires physical access to the machine.  If the attacker found your key somewhere *else* like in the cloud encrypted, it would do him no good, even in this scenario.  He would still need access to this file on your machine.

> The same does my banking card. Keypair created inside the card and only public key can be exported and signed and imported again. The issuer of the banking card knows well that private keys of the x.509 can still be manipulated so the original user does not find out immediately. As they are responsible to certain amount to the bank as what problems may come up, they choose the way of complete physical protection of the private key. And the liability here is just in the order of 100 000$.

All of that is well and good, but I would prefer my private key to be protected by strong crypto and not a physical lock box.  Yes, smart cards are designed to be tamper-resistant, but I seriously doubt they would be as hard to break as a cipher itself.  Though for people who do not want to remember complex passwords, a smart-card is probably your best bet for securing the key (and much more convenient).  That I will admit.

---

