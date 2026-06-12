---
title: "Setting encryption beyond a Samsung SSD FDE"
date: 2016-02-10
forum: Security
---

### Post by PsychedelicWonders on 2016-02-10
So I have a Samsung 850 Pro that has FDE and I am able to set a "User" ATA password via my Asrock mobo UEFI/bios

It is known that hardware encryption is better than software because it doesn't use any resources and is generally known to be very secure without any backdoors.

But - there is always the chance that the Samsung "Master Password" has back door ability - so would it also be best to set some encryption up through Ubuntu?

I know you can encrypt the entire drive through Ubuntu's initial setup via software - but is this needed if I'm doing hardware FDE?

And you can also encrypt your home folder on top of all of that - is this really needed if FDE is in place and also Ubuntu's software encryption abilities of the SSD itself?

All encryption is done through the Ubuntu program LUKS correct?

---

### Post by sandyd on 2016-02-11
Depends.

If you set the entire drive to be encrypted, it will be LUKS.
Encryption of the home folder is done through eCryptfs.

Side Note:
LUKS does not directly do encryption, encryption is handled by dm_crypt, of which LUKS uses as a backend.

---

### Post by Mr._Hope__Change on 2016-02-12
How strong is dm_crypt?

---

### Post by PsychedelicWonders on 2016-02-14
Is anything beyond the SSD's hardware encryption even needed?  According to Trusting Computer Group:

[B]The encryption key is generated during manufacturing, presumably  at an Asian subcontractor. Why should I trust a contractor with a key  that lasts the lifetime of the SED?

[/B]

A: The encryption key is  generated on board the drive and NEVER LEAVES THE DRIVE. The  manufacturer does NOT retain or even have access to the key.  Moreover,  you do not have to trust it.  When putting an SED into service it is  considered good practice to start by directing the SED to regenerate its  encryption key.  Doing this before loading any software on the drive  eliminates the possibility of the drive manufacturer ,or anyone else who  might have had a chance to access the drive before the current owner,  acquiring any secret, like the encryption key, that could be later used  to break into the user data. 

So how do you instruct an SSD to regenerate a new encryption key?  Just by doing a Secure Erase I believe correct?  This should generate a new encryption key right?

---

### Post by PsychedelicWonders on 2016-02-24
Bump...

---

