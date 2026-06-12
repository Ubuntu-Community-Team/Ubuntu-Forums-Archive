---
title: "Full Drive Encryption without Passprompt"
date: 2010-08-25
forum: Security
---

### Post by Bill.Scott on 2010-08-25
Is it possible to encrypt the entire drive and not be prompted for the passphrase? 

I have a request for a demo of our application and I am looking to create a virtual for VMware's player but need to make sure that the vmdk file cannot be mounted and files pulled from it to protect us from reverse engineering of the application.

---

### Post by Bachstelze on 2010-08-25
Well, if you don't put a passphrase, what's to keep someone from mounting it normally and extract your data?

---

### Post by Bill.Scott on 2010-08-25
If the system is booted normally the logon that is provided can be locked down so that the access is limited. where as if the disk is mounted as a secondary unencrypted, the root permissions will be inherited across the now secondary mounted volume providing full access, which is what I am trying to avoid.

We do this for all our portable computers running Windows, and are looking for a way to provide the same level of security within a Linux VM.

---

### Post by Bachstelze on 2010-08-25
> **Bill.Scott said:**
> If the system is booted normally the logon that is provided can be locked down so that the access is limited. where as if the disk is mounted as a secondary unencrypted, the root permissions will be inherited across the now secondary mounted volume providing full access, which is what I am trying to avoid.

We do this for all our portable computers running Windows, and are looking for a way to provide the same level of security within a Linux VM.

No, no, no, you're doing it wrong, wrong, wrong.  In order to decrypt the filesystem, the system has to know the key.  If you don't enter the key, the system can't invent it: it has to store it somewhere, in clear.  Someone can recover it.

---

### Post by Bill.Scott on 2010-08-25
Don't know what to tell you...
we use a product called safeguard (a windows only product) on laptops, etc (mobile devices). this product does full disk encryption (except for the loader) and can prompt for pre-boot authentication but we opt for it not to. as by encrypting the disk using password crackers are useless and unless you know the actual password for a account you are not gaining access to the data stored on the system.

Looking for a product offering the same level of protection for Linux/ubuntu.

Giving out the encryption key would provide the same level of access to someone mounting the drive as a secondary without encryption as they would have the key to un-encrypt the drive.
Lots of good that would do!!!

---

### Post by Agent ME on 2010-08-25
How is the VM supposed to be able to read itself unless it has its own encryption key somewhere?

---

### Post by BkkBonanza on 2010-08-26
The Ubuntu encrypted home option allows for auto-encrypting data in home and only needing to know the user login pwd, not an extra encryption key. Presumably you do want to have user login security still. 

I haven't tested it but I think if you mount the external drive in the correct location then all data should be encrypted there. Normally for /home/userX the encrypted files are stored in /home/.ecryptfs/userX/.Private. So if you mount the external drive at that location then all files for that user would be encrypted on the drive, but be accessed in home as usual. You could get more flexibility by using symbolic links, or by manually installing/configuring ecryptfs to get everything to suit.

You could also look at Truecrypt which has some auto-mount options that should be amenable to mounting only when logged in. I haven't used it that way but I recall seeing options along that lines. It's also very easy to install as a package.

---

### Post by Bill.Scott on 2010-08-26
BkkBonaza, 

Sounds like there is no solution (even purchasable) to my request as the automount for truecrypt is stored and can be copied to another system if mounted to another system. being that the system itself is open the encrypted files are exposed. and the configuration files for truecrypt are also.

---

### Post by BkkBonanza on 2010-08-26
I don't think I understand what you want then. Any system that has encryption either has to prompt for the key or store it somewhere. If the system isn't protected by a login/pwd then no matter what it's always going to be copyable. The key doesn't just disappear into the ether and magically re-appear. Even on your current Windows setup it has to have the key somewhere. You should be able to setup something that is at least as sufficient as your "open" Windows system.

---

### Post by Bill.Scott on 2010-08-26
In ubuntu's integrated disk encryption is it possible for the passphrase to be stored and passed directly?

Overall goal is we are looking for a way to control access to the entire volume and not hand out the key to unlock, kinda bypasses the entire purpose of encrypting it in teh first place...

Thinking a little further TrueCrypt seems like it would be a fit for encrypting file structures. 

Questions:

You said that it asks for a password not the passphrase for the encryption itself. correct?

being that the entire disk is not encrypted. Could the filesystem be mounted to another system and the encrypted files and TrueCrypt configuration be copied from one system to another and being that the configuration has been copied password entered and files decrypted/exposed?

---

### Post by BkkBonanza on 2010-08-26
With Ubuntu encrypted home, when you login as a user it uses your login pwd to decrypt a stored key that is then used for encrypting/decrypting the home files. So you only login as usual to have access to your files. On disk without being logged in (as root even, or if mounted on another machine) the files remain encrypted.

If you put your sensitive files there then they should be safe unless a user can login. 

Ecryptfs can be installed for alternate uses as well but the simplest ready-to-use mode is when chosen during install as encrypted home. 

If you want to do this without requiring any kind of login then I don't see any way on any system that the encryption key cannot be found and used. It may depend on obscurity to hide away the key but someone with knowledge will know where to look. At some point there has to be something that decides who has access and who doesn't.

With Truecrypt I think the idea would be to store the auto-mount info in the users encrypted home so that logging in gets access to info needed to mount the Truecrypt drive.

---

### Post by Entropy512 on 2010-08-26
> **Bill.Scott said:**
> Don't know what to tell you...
we use a product called safeguard (a windows only product) on laptops, etc (mobile devices). this product does full disk encryption (except for the loader) and can prompt for pre-boot authentication but we opt for it not to. as by encrypting the disk using password crackers are useless and unless you know the actual password for a account you are not gaining access to the data stored on the system.

Looking for a product offering the same level of protection for Linux/ubuntu.

Giving out the encryption key would provide the same level of access to someone mounting the drive as a secondary without encryption as they would have the key to un-encrypt the drive.
Lots of good that would do!!!
What you have described has to be one of the dumbest, most worthless FDE implementations I have ever seen if you have indeed described it correctly.

If it is able to decrypt the drive without prompting for a password, that means it is storing the key in the clear somewhere.  So it is, at best, security through obscurity.

Unless you're not telling us something, such as whether it uses some sort of keyfile approach.  (e.g. key stored on removable media)

To obtain the same level of protection (read - very little beyond just not encrypting it in the first place) in Linux, try seeing if dm-crypt will let you use a fixed key stored on the hard drive somewhere.

---

