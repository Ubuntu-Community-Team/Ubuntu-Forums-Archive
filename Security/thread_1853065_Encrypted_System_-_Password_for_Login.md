---
title: "Encrypted System - Password for Login"
date: 2011-10-01
forum: Security
---

### Post by Chrissd on 2011-10-01
Hi all,

I have a fully encrypted system (aside from boot, obviously) so I have to enter a password to get the system to boot. In addition to this, when Ubuntu boots, it asks for me my user password.

Since I'm the only user of this netbook, I'm thinking of setting the system to automatically log me in. Will this open me up to any other security problems?

I realise most of your guys out there understand computers much better than I do, so am seeking advice from the wise.

Thanks :)

---

### Post by iavor on 2011-10-01
Unless you use a weak password for your encrypted drive i dont think its a problem, however if its me i'll still use password for login, but im too paranoid.

---

### Post by Paddy Landau on 2011-10-01
You may get an irritating problem, in that when your system needs to access your keyring (e.g. to access your wireless passphrase), the system will ask for your password anyway.

Experience leads me to recommend that you don't use auto-login; however, it certainly cannot hurt to try -- provided that your computer is phsically secure from tampering. It's easy to turn it off again if you don't like it.

---

### Post by Chrissd on 2011-10-02
It sounds bad, but my system is working fine now, I think I'll leave it as I don't want to have to reset keyring passwords to a blank password just to stop me typing in my password more often.

Also, why be so paranoid as to encrypt my system only to remove a layer of security?

Thanks guys :)

---

### Post by Paddy Landau on 2011-10-02
> **Chrissd said:**
> Also, why be so paranoid as to encrypt my system only to remove a layer of security?
+1. The purpose of encryption is in case your laptop is stolen or otherwise physically compromised. With auto-login, you are right -- you might as well not encrypt.

---

