---
title: "Security warning for Thunderbird 3.0 users"
date: 2010-01-08
forum: Security
---

### Post by BkkBonanza on 2010-01-08
I just wanted to post this here so that TB 3 users are aware.

Thunderbird 3 has some changes in how the master password is handled and how it relates to the security device / certificate store. In the previous version these were two separate passwords and now they are combined into one single password severely increasing the vulnerability.

To make matters worse the method for removing the master password has been posted in public on the GetSatisfaction Thundebird support forums to help people who have lost their master password. 

This of course means that anyone with login access, or any user who has auto-login enabled without password, is able to clear the master password in Thunderbird 3. This makes the master password a convenience device rather than a security feature and anyone who intends to prevent access to their email accounts should not depend on this to prevent access.

Even worse, if the master password is now reset by some user then they also have access to security device / certificates in Thunderbird 3 because some genius decided along the way that combining the passwords was a good idea. A user can backup any certificate from the store and use it for impersonation, once the master password is reset.

I don't know if there's a way to fix this yet but when I tested Thunderbird 3 a few weeks back I discovered this and removed it form my system and reverted back to version 2. I added information to a bug report already reported and complained about it on the support forum. So far no one appears to be taking this issue up and dealing with it. On the support forum they are ignoring the severity of the problem.

I would recommend not using Thunderbird 3 if you value the security of your email and/or certificates.

---

### Post by CharlesA on 2010-01-08
Yikes! Thanks for the info!

---

### Post by FuturePilot on 2010-01-08
Physical access = you're screwed anyway. ;)

---

### Post by witeshark17 on 2010-01-09
> **FuturePilot said:**
> Physical access = you're screwed anyway. ;) This is my first reaction; if my e-mail client is securely logged out, my whole system is as well. That is, the system is logged completely off. :popcorn:

---

### Post by BkkBonanza on 2010-01-09
Ya, except the TB certificate store is supposedly encrypted. So having physical access without a password for it should make it mostly safe. Having a simple bypass for that password just makes things far easier. 

And who said anything about physical access. With this problem anyone who can get in via VNC (a common issue now) has access to your desktop and can reset the TB password and get your certificates and access your email accounts (and change your passwords on them if they wanted).

This is far more relevant then just Physical access = Screwed. We all know that. It doesn't mean using passwords or any other level of security should be skipped. There is no doubt users out there who think they are safe using a master password on TB 3.

And I've heard of at least one corporate user who treats certificates as though they enable highly secure email communication.

---

