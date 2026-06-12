---
title: "ssh-keygen with no passphrase?"
date: 2008-07-18
forum: Security
---

### Post by ubunuub on 2008-07-18
Hello...

What are the repercussions for doing a ssh-keygen -t dsa without a passphrase, i.e., unencrypted keys?

I'm following [this guide]("http://www.ibm.com/developerworks/linux/library/l-backup/index.html") for a simple automated remote backup setup. 

But then, even if I use the recommended keysafe utility, the passphrase is only 'remembered' until the computer is restarted, and ideally I'd rather not enter the passphrases with each restart.

I'm seeing plenty of other guides that explicitly say to not use a passphrase.

TIA :)

---

### Post by kevdog on 2008-07-18
It just means if any one gets a hold of your private key, they could use it.  If your private key is relatively secure -- good, if you carry it around on a usb stick -- probably not a good idea.

---

### Post by Yuki_Nagato on 2008-07-18
There is nothing wrong I believe to what you are doing.  If you use that public key for ONLY the backup, and you do not care if anyone is able to access the backup files, then what you are doing is fine.  If you want to use keygen for something else, create a 2nd key with a pass phrase.

---

