---
title: "Secure social networks?"
date: 2012-10-08
forum: Security
---

### Post by Welly Wu on 2012-10-08
What are some good recommendations for a secure and preferably open source social media network?

I heard of Diaspora, but I want to know about other alternatives. I want to use encryption like GPG to control my data and I want to be able to select what I share with others across more popular social media networks like Facebook, Twitter, Google+, etc.

What are some recommendations and why?

---

### Post by KiwiNZ on 2012-10-08
The security of any Application is never certain, there are simply too many variables and of course the human factor.

---

### Post by Welly Wu on 2012-10-08
This is good to know, but did you try Diaspora or any other social networks that have better security?

I signed up for Diaspora. How do I configure GPG encryption?

Hmm, my Google searches are coming up too little useful information.

---

### Post by Elfy on 2012-10-08
*Thread moved to **Security Discussions**.*

This is not a chat topic - you are after support.

---

### Post by KiwiNZ on 2012-10-08
I am not a big user of Social Networks I even dislike IRC

---

### Post by Docaltmed on 2012-10-08
You can't have what you want, as security and social network participation are mutually incompatible.

---

### Post by mike acker on 2012-10-08
> **Docaltmed said:**
> You can't have what you want, as security and social network participation are mutually incompatible.

that would be correct: a social net is essentially a 1:many i.e. broadcast system

for private communication the first place to go is the Thungerbird e/mail client that comes with UBUNTU.  Enable the ENIGMAIL plug in.  with 12.04 LTS I found the needed GnuPG was pre-installed; earlier I had to load it.

bear in mind that in e/mail you can have e/mail lists -- so that you can send notes to your comrades as a group ... and GnuPG (like PGP) will allow you to encrypt your message to multiple recipients -- provided of course that you have their keys

I don't know if we have a Thunderbird/ENIGMAIL list here; both GnuPG and ENIGMAIL have email lists for support so I don't know if the Forum Administrators here will see setting up a topic for this as needed...

understanding the TRUST MODEL in Public Key Encryption -- takes some thinking,-- but is a critical need in our society today.*

It's one of my favorite topics.  My Public Key is on the KeyServer -- if anyone wants to play with ENIGMAIL
~~

Example: say you receive an Update from Adobe. the update uses Adobe Graphics and says "signature verified".

your immediate question should not be "cool", but rather : Signature verified by who and why do I trust that party to sign for software?

the answer is: you have to PERSONALLY verify the fingerprint on the Certificate Authority (CA) that is signing things for uou.... VeriSign -- MSFT -- etc

to do this you have to (1) generate your own personal key and assign it ultimate trust, and then (2) obtain a separate copy of any certificate you plan to trust as a CA and then verify the fingerprint on their certificate in your system - and then sign their certificate, authorizing it to sign for subordinate certificates on your system.  This builds your "TRUST MODEL".  

It may sound complex but we all need to go over it until we "get it" or at least know how to follow the process.

---

### Post by rookcifer on 2012-10-08
> **Docaltmed said:**
> You can't have what you want, as security and social network participation are mutually incompatible.

It depends.  Diaspora is designed in such a way that you can setup your own private social network (on your own server that you physically own) and only invite who you want (a private VPN if you will).  

Of course, I am not saying this is 100% hack-proof as the server hosting it might be cracked, etc.  But if everything is encrypted it might not do the attacker much good (I am not sure on Diaspora's encryption methods or if they even do at all).

It looks like a cool project.  If I cared for social networking, I might use it.

> I don't know if we have a Thunderbird/ENIGMAIL list here; both GnuPG and ENIGMAIL have email lists for support so I don't know if the Forum Administrators here will see setting up a topic for this as needed...

[Yahoo groups has PGPNet.]("http://tech.groups.yahoo.com/group/PGPNET/")  Free sign-up.  It's a mailing list where every message is encrypted.  You have to download everyone's key (about 40 or 50 members) then add the keys to your "per-recipient" rules in Enigmail.  From there you can have it encrypt to all keys on the list whenever you start a topic or respond to a topic.

---

