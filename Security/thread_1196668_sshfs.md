---
title: "sshfs"
date: 2009-06-25
forum: Security
---

### Post by WitchCraft on 2009-06-25
Hi, I setup sshfs to work over the network.

It works great, but I doubt that a password is the best security.

How can I set up a RSA/PGP key logins/authentication instead of a password?

What are recommended secure settings?

---

### Post by Trebaruna on 2009-06-25
Check out this page: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by WitchCraft on 2009-06-25
> **Trebaruna said:**
> Check out this page: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

And I've found out that the following:

RSA is less secure than DSA but authenticates faster.

DSA is faster in *signing*, but slower in *verifying*. 

A DSA key of the same strength as RSA (1024 bits) generates a smaller signature. 

An RSA 512 bit key has been cracked, but only a 280 DSA key. 

It doesn't matter because with ssh, only authentication is done using RSA or DSA algorithm, and then the "rest" is encoded using a (uh, was it block?) cipher like IDEA, DES, Blowfish, etc, etc after the authentication is done.

While ssh2 can use either DSA or RSA keys, ssh1 cannot. 
SSH2 will also not use patented cypers like IDEA.

---

### Post by Trebaruna on 2009-06-25
If you generate a 2048 bits RSA key (which is the default I believe) you're good. The key sizes do not matter terribly much in terms of performance here because the keys are only used to authenticate and then SSH will use a different encryption algorithm, anyway.

---

### Post by WitchCraft on 2009-06-25
> **Trebaruna said:**
> If you generate a 2048 bits RSA key (which is the default I believe) you're good. The key sizes do not matter terribly much in terms of performance here because the keys are only used to authenticate and then SSH will use a different encryption algorithm, anyway.

The topic has just dissolved, as RSA offers 4096 Bit, while DSA only offers 2048.

If they are about the same, I'm always going for the most Bits.

---

### Post by brian_p on 2009-06-25
> **WitchCraft said:**
> Hi, I setup sshfs to work over the network.

It works great, but I doubt that a password is the best security.

Anything in particular which occasioned this doubt?

> What are recommended secure settings?

Ones which cover the situations which ssh will be used in.

---

### Post by WitchCraft on 2009-06-25
> **brian_p said:**
> Anything in particular which occasioned this doubt?

The log of 8000 attemps to guess my password within the last 5 days.

---

### Post by brian_p on 2009-06-25
> **WitchCraft said:**
> The log of 8000 attemps to guess my password within the last 5 days.

About 140,000 probes here since last September. I wish them luck with their pathetic, futile attempts. Even if the automated scripts became cleverer Ubuntu's final distribution (Doomsday Dromedary) would be released before they got in here.

---

### Post by WitchCraft on 2009-06-26
> **brian_p said:**
> About 140,000 probes here since last September. I wish them luck with their pathetic, futile attempts. Even if the automated scripts became cleverer Ubuntu's final distribution (Doomsday Dromedary) would be released before they got in here.

Yep, but I don't want to rely on their scripts being stupid.
Just put in a 4096 key and replace it from time to time, and it's a certainty.

---

### Post by brian_p on 2009-06-26
> **WitchCraft said:**
> 

Yep, but I don't want to rely on their scripts being stupid.

No need to do that! The power of a 20 character password is sufficient.

> Just put in a 4096 key and replace it from time to time, and it's a certainty.

Why replace it periodically?

---

### Post by WitchCraft on 2009-06-27
> **brian_p said:**
> No need to do that! The power of a 20 character password is sufficient.


Probably, but I don't want to type in a 20 character password each time.

> **brian_p said:**
> 
Why replace it periodically?

Reason: paranoia.

---

### Post by brian_p on 2009-06-27
> **WitchCraft said:**
> 

Probably, but I don't want to type in a 20 character password each time.

You'd feel uncomfortable with a strong passphrase to protect a 4096 bit private key then.

> Reason: paranoia.

Knowledge and reason produce a more satisfactory outcome.

---

### Post by WitchCraft on 2009-10-26
> **brian_p said:**
> You'd feel uncomfortable with a strong passphrase to protect a 4096 bit private key then.


Exactly, the entering of the private key password already gets on my nerves. But I can't omit it, because I often use public transport, and it's probably only a question of time until I loose my laptop or until it gets stolen.

> **brian_p said:**
> 
Knowledge and reason produce a more satisfactory outcome.


That's true, but a bit paranoia here and there sometimes turns out to be right.

---

