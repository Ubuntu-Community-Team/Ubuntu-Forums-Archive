---
title: "No Option to Encrypt/Sign Files on Pop-up Menu"
date: 2010-05-16
forum: Security
---

### Post by TroyMW on 2010-05-16
I'm using Ubuntu 10.04 64-bit.  I created a PGP key pair using Applications|Accessories|Passwords and Encryption Keys.  I used DSA El Gamal as the encryption type and a key strength of 2048 bits.  However; when I right click on a file or folder I don't see the Encyrpt... and Sign options.  Any suggestions?

---

### Post by TroyMW on 2010-05-17
I think I just solved this by installing the seahorse-plugins package.

---

### Post by zorkerz on 2010-05-23
Installing the seahorse-plugins package did not give me an encrypt option when I right click?

Any ideas how to get this?

---

### Post by OpSecShellshock on 2010-05-23
> **zorkerz said:**
> Installing the seahorse-plugins package did not give me an encrypt option when I right click?

Any ideas how to get this?

This should do it:

[http://ubuntuforums.org/showpost.php?p=9329323&postcount=2](http://ubuntuforums.org/showpost.php?p=9329323&postcount=2)

Basically it looks like you need to stop and restart Nautilus.

---

### Post by zorkerz on 2010-05-24
Your are correct. I just did a second restart and it worked. Not sure why the first did not.

---

