---
title: "PGP help needed"
date: 2009-12-02
forum: Security
---

### Post by knottshawk on 2009-12-02
I have a system running XP with PGP desktop installed. This system contains all my business contacts PGP keys. I need to know how to export these keys and import them for use in Ubuntu 8.10 with Thunderbird (I have enigmail installed). I've tried on my own, and it doesn't work... I've heard and read there may be special steps to take, but I'm unsure.

---

### Post by tubbygweilo on 2009-12-02
knottshawk,
If your business contacts PGP keys are on keyserver somewhere on the net is should be possible to being them into Thunderbirs/Enigmail via:

ThunderBird> OpenPgp> OpenPgP Key Management> Keyserver> Search For Keys.
Then search via email address or key identifier via select Keyserver.
Then select key to download via Download Open Pgpkey.

If all goes well you should now have access to the pgp keys of your customers.

An other away would be to find the windows file containing your pgp keys, export the file to Ubuntu, set the correct folder file permissions, start Tunderbird and see if the keys are visible.

---

### Post by knottshawk on 2009-12-02
Thanks... I actually figured it out... imported them in and we're golden.

---

### Post by Agent ME on 2009-12-02
Important: Doing that doesn't copy your private key(s) because they aren't stored on the server.

Though I'm not too sure how to convert them PGP -> GPG.

---

### Post by john19691969 on 2012-05-08
> **knottshawk said:**
> I have a system running XP with PGP desktop installed. This system contains all my business contacts PGP keys. I need to know how to export these keys and import them for use in Ubuntu 8.10 with Thunderbird (I have enigmail installed). I've tried on my own, and it doesn't work... I've heard and read there may be special steps to take, but I'm unsure.

I use vista with thunderbird and enigmail.... I can encrypt files and send to adele  [email]adele-en@gnupp.de[/email]    but can not decrypt the response. I searched by email and can't get anything! Help!!

---

### Post by oldos2er on 2012-05-08
Thread closed. john19691969, if you need help with Vista you should visit a Microsoft forum.

---

