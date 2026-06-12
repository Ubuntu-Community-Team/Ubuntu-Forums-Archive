---
title: "How to send PGP Encrypted E-Mail through Thunderbird?"
date: 2008-12-01
forum: Security
---

### Post by Replayfb on 2008-12-01
hey all,

im very new to Linux and Ubuntu. So im trying to discover all... but i have stucked in this. Is there anyone to help me how to send PGP Encrypted Email through Thunderbird or any other email program?? i have created a PGP Password, for a gmail account. and when im trying to send it by Evolution Mail as PGP Encrypted, i got always errors. I dont know what to do...

---

### Post by hyper_ch on 2008-12-01
posting the error would be helpful.

---

### Post by tubbygweilo on 2008-12-01
The encryption / decryption and key management is managed by the Enigmail extension and is detailed by this help document [http://enigmail.mozdev.org/home/index.php](http://enigmail.mozdev.org/home/index.php). From what I can remember being a Mozilla ThunderBird user I had to install the Enigmail Application alongside ThunderBird via the Synaptic Package Manager.

---

### Post by kevdog on 2008-12-01
Just for the record and clarity

Is it PGP or GPG?  The two are different.

---

### Post by Replayfb on 2008-12-01
so, here is the error that i get, as an attachment...

---

### Post by kevdog on 2008-12-01
For the record your error is in regards to GnuPG -- and not PGP.  

Second, it states it can't find the public key of the recipient.  

If at the command line or within Thunderbird, there should be a way to list the keys on your keyring.  

At the command line it would be:
gpg --list-keys

You should see a list of keys with one key listed with the exact same email address as the sender which you are trying to correspond with.

---

### Post by Replayfb on 2008-12-02
well, the thing is, i use the default email program that ubuntu provides. Evolution Email. And when i click on Security -> PGP Encrypt and then try to send, i got this error. I created a key already in Passwords And Encrypting Keys. and when i write in terminal what u wrote to me, i got the list that i created one for the email i used. But i dont know how to use this key to encrypt the outgoing email. That`s my problem. thanks..

---

