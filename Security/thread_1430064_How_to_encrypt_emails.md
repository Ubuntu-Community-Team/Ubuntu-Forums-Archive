---
title: "How to encrypt emails?"
date: 2010-03-14
forum: Security
---

### Post by dogdo on 2010-03-14
Hi

Im using gmail with https always turned on but what programs can i use to easily encrypt emails? Is pretty good privacy easy to use?

---

### Post by ndefontenay on 2010-03-14
Hi.

You can indeed PGP but it's a 2 way process.

PGP works on the principle of a public and private key. When you create your PGP encryption, you will be given a set of 2 keys. 

One will be kept on your computer for you. It's your private key. The private key can only decrypt data sent to you with your public key.

The other one, you guessed it is the public key. It's sent to anyone whom you want to send you encrypted messages. They will somehow associate your contact information with your public key (it's done in a variety of ways) and as soon as they send you an email, it would use your own personal public key.

On the internet, it's all gibberish encrypted data and as soon as you get the email on your computer your private key decrypt the mail for you.

What that means is that everybody you deal with will have to get a copy of your public key and you will have to ask anybody you deal with to create their set of keys as well if privacy is an issue.

It's so painful that it's generally used for specific corporate communication channel with say sensitive customer information. The cost of loosing information has to be worth the pain basically.

---

### Post by ndefontenay on 2010-03-14
To be complete on the subject. If encryption is a pain, you can always sign your emails with a PGP signature. it will authenticate as really being sent by you. 

A careful person receiving an email from you could eventually click on it and verify whatever information is associated with it. This is not encryption but it ensures that the right person is behind the message.

---

### Post by richs-lxh on 2010-03-14
Enigmail has a nice Thunderbird plugin (if that's what you use) as well as a handy howto guide:
[http://enigmail.mozdev.org/documentation/quickstart.php](http://enigmail.mozdev.org/documentation/quickstart.php)

It'll even generate a new key pair for you:
[http://enigmail.mozdev.org/documentation/quickstart-ch2.php#id2533239](http://enigmail.mozdev.org/documentation/quickstart-ch2.php#id2533239)

And here's the Ubuntu gpg guide:
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
And it's Enigmail guide:
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Thunderbird](https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Thunderbird)

---

### Post by km0r3 on 2010-03-15
> **ndefontenay said:**
> Hi.

You can indeed PGP but it's a 2 way process.

PGP works on the principle of a public and private key. When you create your PGP encryption, you will be given a set of 2 keys. 

One will be kept on your computer for you. It's your private key. The private key can only decrypt data sent to you with your public key.

The other one, you guessed it is the public key. It's sent to anyone whom you want to send you encrypted messages. They will somehow associate your contact information with your public key (it's done in a variety of ways) and as soon as they send you an email, it would use your own personal public key.

On the internet, it's all gibberish encrypted data and as soon as you get the email on your computer your private key decrypt the mail for you.

What that means is that everybody you deal with will have to get a copy of your public key and you will have to ask anybody you deal with to create their set of keys as well if privacy is an issue.

It's so painful that it's generally used for specific corporate communication channel with say sensitive customer information. The cost of loosing information has to be worth the pain basically.

+1 for good explanation.

I'm using PGP now for some time and it was hard for me to understand in the beginning, but there's nothing better at the moment I'd say and despite that [good]("http://www.bretschneidernet.de/tips/secmua.html") e-mail clients support PGP anyway.

---

### Post by lalawawa on 2010-04-06
I have ubuntu 9.10.  I have thunderbird 2.0.0.24 which is the version that synaptic package manager gave me.  I have used the synaptic package manager to install enigmail, I just did "find / 2>/dev/null -iname '*.xpi' and found there is no file anywhere on my hard disk with the suffix ".xpi".  So how do I install enigmail into my thunderbird?

---

### Post by FuturePilot on 2010-04-06
> **lalawawa said:**
> I have ubuntu 9.10.  I have thunderbird 2.0.0.24 which is the version that synaptic package manager gave me.  I have used the synaptic package manager to install enigmail, I just did "find / 2>/dev/null -iname '*.xpi' and found there is no file anywhere on my hard disk with the suffix ".xpi".  So how do I install enigmail into my thunderbird?

Start up Thunderbird. It should be there.

---

### Post by tubbygweilo on 2010-04-07
Thunderbird + Enigmail works for me and what is more it works well, as hinted at in previous posts the hard part is convincing others be they friends or work based contacts to move to encryption and / or signing of emails. Key management can be seen by some as a pain so make sure you keep backups of secret and public keys along with revocation certificates in a safe place (I keep mine safe from prying eyes by placing in a truecrypt encrypted container) and replaciting copies on several dvds for safe storage.

---

### Post by lalawawa on 2010-04-08
Hi, I quit thunderbird and started it again and yes pgp was available.  I was able to decrypt an encrypted message my friend sent to me.  I was not, however, able to encrypt messages either to myself or to my friend.  In both cases, I got an error, something about not being able to find the key, though in both cases I had selected the key off a menu.

---

### Post by EJeanmaire on 2010-04-08
Google is your friend... You might want to try this out for Gmail PGP: [http://www.technovisionary.com/howto-secure-gmail-pgp-encrypt/](http://www.technovisionary.com/howto-secure-gmail-pgp-encrypt/)

---

### Post by lalawawa on 2010-04-08
I'm not using gmail, I'm using thunderbird.

I compose my message.  I click "OpenPGP" on the message browser and select "encrypt message".  I click "send".  It lists all the keys I've imported, with the one for the appropriate recipient ticked.  I click "OK".  It says

nullINV_RECP 0 0x414E26F5

gpg command line and output:
/usr/bin/gpg --charset utf8 --batch --no-tty --status-fd 2 --comment 'Using GnuPG with Mozilla - [http://enigmail.mozdev.org](http://enigmail.mozdev.org)' -a -t -e --trust-model always --encrypt-to 0x414E26F5 -r 0x81C0636FD5ADAFCS -u 0x414E26F5
gpg: 0x414E26F5: skipped: public key not found
gpg: [stdin]: encryption failed: public key not found

---

### Post by René André Poeltl on 2011-04-25
have you tried [http://www.safermail.biz]("http://www.safermail.biz?") javascript AES 256 on the client.

---

