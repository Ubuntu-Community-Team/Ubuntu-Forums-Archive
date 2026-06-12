---
title: "How safe are password managers?"
date: 2010-01-26
forum: Security
---

### Post by BlakeM on 2010-01-26
It's not really a specific Ubuntu issue but seeing as I was looking at KeePassX on Ubuntu I thought it would be ok to post here.

My concern with using a password manager like KeePassX is you're putting all your eggs in one basket.  If someone compromises your master password than they have access to a lot of login details.

Would it be very unwise to allow SSH access to the machine that is storing the password manager database? (Assume SSH is properly configured allowing only pub/private key authentication, no root login and the private key is passphrase protected).

If it were you, would you trust your bank details and other critical information stored on a computer (with or without allowing remote access)? Even if it was encrypted by a password manager?

---

### Post by mcgeek on 2010-01-26
I use KeePassX and have all of my bank details stored in it. If you don't like having the DB on your hard drive then put it on a thumb drive.

For me, an ageing dyslectic, KeePassX is a life saver. I only have to remember one password. I use the password generator to generate proper passwords, unique for every account.

---

### Post by njiii on 2010-01-27
can your password manager guard against TEMPEST attacks? None of them do, so they FAIL. They also FAIL against many other attacks including but not limited to thermal, keyboard, powerline, and other attacks. Use your brain instead, even though "the mind has no firewall"

---

### Post by BlakeM on 2010-01-27
Thanks for the reply :). Do you have port 22/SSH open to the world?  Or are you behind a hardware router with no ports open?

I wouldn't have any problem running KeePassX if I was behind a router with all ports closed, but my intention is to allow SSH to the box with the keepassx DB on it.

Storing the DB on a pen drive sounds like a good idea. I didn't realise you could do that with KeePassX.  However, if someone gained root access to your system (without your knowledge) would it make much difference if the DB was stored on the HDD or a separate pendrive? Eventually you're going to connect the pendrive to the computer and enter the master password.

---

### Post by cariboo on 2010-01-27
If you use a public/private key with ssh instead of a password you will be much more secure. Weak passwords are one of the main reason a system can be cracked. Have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for info on setting up keys.

---

### Post by bluelamp999 on 2010-01-27
Personally, I wouldn't use one.

It's that I just don't trust them. 

This isn't based on personal experience, merely a hunch.

---

### Post by FuturePilot on 2010-01-27
> **njiii said:**
> can your password manager guard against TEMPEST attacks? None of them do, so they FAIL. They also FAIL against many other attacks including but not limited to thermal, keyboard, powerline, and other attacks. Use your brain instead, even though "the mind has no firewall"
If someone used any one of those kind of attacks to get your passwords, whether you were using a password manager or not would be irrelevant. So no, they don't FAIL.

> **bluelamp999 said:**
> Personally, I wouldn't use one.

It's that I just don't trust them. 

This isn't based on personal experience, merely a hunch.

There's an old saying: "don't judge a book by its cover". ;)

---

### Post by BlakeM on 2010-01-27
> **cariboo907 said:**
> If you use a public/private key with ssh instead of a password you will be much more secure. Weak passwords are one of the main reason a system can be cracked. Have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for info on setting up keys.

I already have keys set up :), spent a lot of time reading up on SSH.  Seems to be the mantra on these forums: "if you want remote access use SSH with public/private keys".  For good reason.  Also have fail2ban and loving it.

I suppose it comes down to how much trust you place in SSH and your ability to correctly configure it.

Has anyone using a password manager like KeePassX with SSH access to the box had their master password compromised (i.e. noticed money going out of their bank account or similar?)

---

### Post by Soul-Sing on 2010-01-27
> **cariboo907 said:**
> If you use a public/private key with ssh instead of a password you will be much more secure. Weak passwords are one of the main reason a system can be cracked. Have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for info on setting up keys.

Could you explain how to set up, and to secure, revelation/KeePassX (two passwordmanager)with ssh keys on a desktop environment?
- i did have a look at the wiki
- i made a public/private key
- whats next?

---

