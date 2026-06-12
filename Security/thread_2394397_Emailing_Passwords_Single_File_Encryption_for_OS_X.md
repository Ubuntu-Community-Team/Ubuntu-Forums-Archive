---
title: "Emailing Passwords: Single File Encryption for OS X and Linux??"
date: 2018-06-15
forum: Security
---

### Post by Kurt_Alan on 2018-06-15
I am sending my financial account passwords to the executor of my final will. Needless to say, I will not do this without file encryption!

aescrypt.com had a successful cross-platform app that no longer works with LibreOffice (in my case). VeraCrypt and GNUPrivacyGuard are all too complicated for a single one-off use.

What's the easist way to go, a GUI app that works out of the box for OS X and Linux ???

---

### Post by Dennis N on 2018-06-16
In Ubuntu, the file manager (Files) can encrypt any file with a plugin. All you have to do is right-click on the file name, select "encrypt" from the menu, and specify the recipient. 

If OS X also has gpg encryption/decryption capability, then you are in business.

Any recipient has to first email you his gpg public key so that it is available to encrypt files you sent to him. Only the recipient can decrypt the file.

If you are interested, plugin package to install is "seahorse-nautilus".

There is also one for MATE's Caja file manager, "seahorse-caja".

---

### Post by TheFu on 2018-06-23
I would use a KeePassX compatible DB.  It is cross platform.  You can attach files to an entry. It uses AES encryption.
There isn't any need to provide financial logins and doing so might get your family/friends into trouble.  At your death, only your spouse should have access, but anyone else should not make **any** changes to anything until the financial institution gets the death certificate and creates new accounts for the "Estate" from which the appointed estate executor manages things.

I'm the executor for 2 of my siblings.  This is how my family shares important data for *after-I'm-dead* stuff. 

I've been through this 2 times already. 

Of course, different countries and provinces will have different laws.  I'm only familiar with 3 US states around this, but will probably have to learn 2 more, since none of my family lives in the same state.

---

### Post by HermanAB on 2018-07-03
KeepassX is a very good suggestion, since it is cross platform.

Another tool which is cross platform and which everyone and his dog is familiar with, is pkzip.  Many tools can make encrypted zip files and most people know how to handle them.

---

### Post by TheFu on 2018-07-03
> **HermanAB said:**
> KeepassX is a very good suggestion, since it is cross platform.

Another tool which is cross platform and which everyone and his dog is familiar with, is pkzip.  Many tools can make encrypted zip files and most people know how to handle them.

KeePassX is kinda deprecated. I think the new project is called KeePassXC or CX, I forget. But the underlying DB format is still solid and cross-platform.

ZIP is the lowest common denominator solution and much better than what 95% of the world does. ZIP is a reasonable file format for sharing things with extremely non-technical people, but *only if the passphrase is long and random.*  There are ZIP cracking tools which can do amazing things.  Long, random.

---

