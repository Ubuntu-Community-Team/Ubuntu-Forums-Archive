---
title: "Encrypting OS, how do I do this?"
date: 2008-06-16
forum: Security
---

### Post by tuproxy on 2008-06-16
I'm considering adding an extra level of security to my servers and  am considering encrypting my OS. 
-Is this a waste of time?  
-Should I be looking more at encryting my data, my OS or both?  
-Does encrypting decrease system performance very much?  
-Does the length of my passphrase determine the security of my encryption? ( I have a 44 character passphrase that is TOUGH).

Any suggestions or ideas?

---

### Post by tamoneya on 2008-06-16
unless someone is requiring you to encrypt the OS I would recommend just encrypting your data.  There really isnt much additional security when you encrypt the OS files especially when you talk about linux.  It really only helps when you have consider physical access.  It has no effect if someone attempts to hack your network.  However if someone physically takes your harddrives they wouldnt be able to run the OS until they crack the encryption.  If they are able to crack this proctection then I am willing to bet that they can crack the encryption on your data.  On top of that it only adds additional complexity to your OS and will make it sluggish because all reads and writes to the harddrive will require encryption or decryption.

---

### Post by hyper_ch on 2008-06-17
> **tamoneya said:**
> unless someone is requiring you to encrypt the OS I would recommend just encrypting your data.
I would adivce differently. Do you know what you all have to encrypt so that every last part of a data file in the system is encrypted? Just data would mean only /home folder (normally)... what about swap? what abuot /tmp? what /var/lib/mysql? ....? Full disk encryption will make it simpler to not forget anything.

There will be decreased performance but you don't notice much. I only notice it when I move large files accross different partitions. For normal usage you don't notice anything. At least I don't notice when I'm playing WoW with Wine on my 1.6ghz Athlon with 1 GB ram and 128mb nvidia card.

Well, longer passwords are harder to brute force. However if you have a 20 char password that should be - at least today - virtually impossible to bruteforce.

> **tamoneya said:**
> It really only helps when you have consider physical access.  It has no effect if someone attempts to hack your network.
Encryption only helps against someone who gets physical access. It will not help in any network related event.

And you encrypt your system (easiest) upon installation using the alternate cd. In there you can then set it all up.

---

