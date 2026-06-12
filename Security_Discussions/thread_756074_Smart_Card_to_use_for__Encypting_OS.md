---
title: "Smart Card to use for  Encypting OS"
date: 2008-04-15
forum: Security Discussions
---

### Post by e-dard on 2008-04-15
Hey all,

I am a little confused with some encyption stuff.

I have a smartcard (open gpg one) and a smart card reader on my desktop & laptop.  What I wish to do is encrypt both desktop and laptop, such that the encryption key on the smartcard is used for decrypting the partitions.

I wish to encrypt the / partition so that it must be decrypted to boot into ubuntu.

Basically, I am wondering how this is going to work because normally when fully encrypting the OS  (using dm-crypt or something) the keys are stored on the drive and a password is entered to retrieve them.  However, can ubuntu read a smart card at boot time?

Can anyone point me in the right direction?  I have seen a lot of the encryption howtos but none on how to use a key on a smart card at boot time.

I want:

\ encrypted
\home encrypted
\swap encrypted

on both machines, using the key on my card.

thanks!

e-dard

---

### Post by hyper_ch on 2008-04-16
Hmmm, if the smartcard can be read directly at bootup (like a usb flash drive) then you could store a key in there and use it for bootup... however I'd advice you to still have a password (as backup login)...

And you'd also need to create another partition for the /boot folder.

---

### Post by e-dard on 2008-04-16
Hey, thanks for the comments.

The thing is, if I encrypt my drive with my public key, then only my private key (on my smart card) will be able to decrypt my drive.

So having a pasword as a backup means that my private key would have to be duplicated on my drive somewhere, which defeats the point of only having a single private key on the card.

However, since the keys generated on the card are subkeys of my master key (which is kept on a usb stick hidden away somewhere) were I to lose the card, new subkeys could be made from the master key, which would still decrypt the drive.  At least that's what I understand from reading a bit.

I am not sure if my computer can boot from the smartcard reader.  What I am thinking is I need linux set such that it loads the drivers and associated software to read the smartcard, then uses the key to decrypt the drive.  Of course, keys cannot be read from the card without entering the pin, which travels with the card.

So, anyone know anything about using smartcards to provide keys for decryption at boot time??

thanks,

e-dard

---

### Post by hyper_ch on 2008-04-16
> **e-dard said:**
> So having a pasword as a backup means that my private key would have to be duplicated on my drive somewhere, which defeats the point of only having a single private key on the card.
With dm_crypt/luks you can authorize yourself either by a single key file or by a password... and you can setup those both at the same time... I think you can have up to 10 passwords or keyfiles for unlocking the drive.

So if anything should happen to the key (card gets defect, accidentally deleted, ....) you can still unlock the drive with the password.

---

### Post by e-dard on 2008-04-16
Hey,

that sounds to me like dm_crypt/LUKS uses some random key pair to encrypt the drive, and to get at the decrypting key you enter a password OR use an authorisation key.

I have room on my card for an authorisation key (for using with ssh etc).  Maybe this is a solution if I can't do it using my ecryption key.  Although, this method is less secure, since someone only needs to steal the laptop to begin having a go at the password to get at the key.  If the drive is encrypted using the encryption key on the smart card, they would need to steal the laptop and card to even begin getting anywhere...

Edd

---

### Post by hyper_ch on 2008-04-16
I'm not getting what you mean...

With luks/dm_crypt you can unlock the partition by entering either your password or submit your keyfile..

It is somewhat beyond my comprehension why a password should be less secure than a keyfile...

---

### Post by e-dard on 2008-04-16
Hey, 

Ok, well I presume that in this case dm_crypt is using a passphrase to encrypt the drive.  Thus you only need to enter it to decrypt.  Of course you can also set up an authentication key, which serves as your password if you have it.  This is not insecure, but it means that you only need the laptop to begin having a go at guessing the password.

If however, you encrypt your drive using your public key (e.g. gpg keypair) then you can *only* decrypt the drive by supplying the corresponding private key.  Why is this more secure?  Well, if the key is on a smartcard then stealing/losing the laptop does not mean anything, since no matter what someone else does they are not going to be able to decrypt the drive, as they don't have the private key.  What if they get the private key (on the card)?  Well then you are in the same situation as described above, they have to get the password on the card.  However, if they enter it incorrectly three times, the card is locked until they guess the administrator password on the card.  Get that one wrong three times and the card destroys itself.

See how this way is more secure??

e-dard

---

### Post by hyper_ch on 2008-04-16
it still can be brute-forced... in the end, a private key is, IMHO, nothing more than a given sequence and for that it does not make any difference for entering a password or a normal keyfile...

The public/private key system as in PGP/GPG enables that OTHERS can encrypt data with your public key so that you may decrypt it with your private key...

That's the only difference but I still don't see why a private/public key would make it any more secure...

---

### Post by e-dard on 2008-04-16
Yeah,

I am starting to think I am looking at this wrong.  I think maybe the best thing would be to the authentication key on my smart card to authorise the computer to decrypt the partitions at boot.  

However, I think my point about the passwords still stands.  If you have a password on the machine you have infinite chances to brute force it.  If you have the authentication key on a smart card you only get three shots at guessing the password.

If you lose the card, you can make a new authentication subkey from your master key.

Will have to do some reading about how to do this all.

thanks,

e-dard

---

### Post by hyper_ch on 2008-04-16
well, the authentication key needs to be transferred to the computer somehow... it isn't restricted to your smart card... so it still can be brute-forced...

---

### Post by prlewis on 2008-04-18
Hi folks,

I see what you're after e-dard :-)

It seems to me that LUKS uses symmetric encryption (the same key is used both to encrypt and decrypt), whereas openPGP uses asymmetric encryption (you have a public and private key pair).

So, LUKS generates a key from random data during the setup, that key is stored somewhere, and then it's used to encrypt and decrypt the data on the fly. This means that you can't put it on your openPGP cryptocard AFAIK.

It might be possible to set up LUKS to use asymmetric encryption, in which case you could keep the actual decryption key off the computer (which is what you want I think), but I haven't seen any examples of that.

You're right that by simply having a password to unlock the LUKS key, which is stored on the drive, it is possible to brute-force it, though there are probably measures which can be applied to this, such as implementing a delay of a few seconds after a wrong password is entered. A ten second delay after every wrong attempt sure adds to the time it takes to brute-force something. But yes, in theory, you're right.

The more standard option is, as is suggested, to set up the smart-card as an authentication method to unlock the LUKS key (yes, using the authentication key on your card, I would imagine). You *could* then also disable the password entry for the LUKS key meaning that if you don't have the key on the card, the LUKS key can't be unlocked by password alone. But, you're then in trouble if you lose the card.

However, as you point out, you've got an openPGP master key stored offline somewhere, so I'd imagine that you could set that up as an additional authentication mechanism. I haven't tried this though, nor do I know if it would work.

This guy here appears to want to implement what you're talking about - storing the key itself on a smartcard: [http://blog.daniel-baumann.ch/](http://blog.daniel-baumann.ch/)

I did read somewhere on the web that it's possible to use another type of card (i.e. not the openPGP smartcard) to store your LUKS key, and you could also have a backup offline somewhere *of the same key*. This would achieve what you want, I think. Might track that down a bit further.

HTH,

Pete.

---

### Post by hyper_ch on 2008-04-18
I still fail to see where the LUKS/dm_crypt attempt is weaker?

In the end you need to provide some decryption key and that can be always be bruteforced...

And also the thoughts of the 10 seconds delay do not do anything... if you have access to the harddisk, you can copy the data and you just put it on a very, very, very huge number of computers that bruteforce it... even then, it will take a long time to brute-force LUKS/dm_crypt (if you have a stron password or strong key-file to it)

The assymetric approach does not contribute anything more to data security when you're the one who is encrypting and decrypting...

---

