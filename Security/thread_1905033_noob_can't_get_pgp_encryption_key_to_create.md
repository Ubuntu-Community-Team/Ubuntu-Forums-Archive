---
title: "noob can't get pgp encryption key to create"
date: 2012-01-05
forum: Security
---

### Post by einstein**-7 on 2012-01-05
Hey there, i'm using ubuntu 11.04 64bit and when i try to create a pgp key it just sits there forever saying 'primegen' but never finishes.  Also started seahorse as sudo from the terminal and it gives some error about "couldn't get default keyring name: error communicating with gnome-keyring daemon"  Also i got keys to create one time somehow but they were test keys and they only appeared under the seahorse running without sudo so confusing.  Any ideas or help, thanks in advance.

---

### Post by Paddy Landau on 2012-01-06
OK, first, you should not have to run any normal program as root (i.e. using sudo); that is for administration tasks only. (As a matter of note, if you do run a GUI program as root, use gksudo and not sudo.)

Second, it is not clear from your post how you tried to create a key. Are you trying to create a GPG key (GPG is the open-source equivalent of PGP) using the programs that come with Ubuntu, or are you using something in Seahorse?

---

### Post by einstein**-7 on 2012-01-06
> **Paddy Landau said:**
> OK, first, you should not have to run any normal program as root (i.e. using sudo); that is for administration tasks only. (As a matter of note, if you do run a GUI program as root, use gksudo and not sudo.)

Second, it is not clear from your post how you tried to create a key. Are you trying to create a GPG key (GPG is the open-source equivalent of PGP) using the programs that come with Ubuntu, or are you using something in Seahorse?
I was just using seahorse - create new and then selected the pgp key as the type

---

### Post by Paddy Landau on 2012-01-07
OK, sorry, I'm not familiar with Seahorse.

I hope someone with more knowledge sees this thread.

---

### Post by einstein**-7 on 2012-01-07
Is there any other free programs i could just use instead that will be as secure encryption?
I saw a few in the Ubuntu software center but most reviews said the encryption was useless.

---

### Post by Paddy Landau on 2012-01-07
Well, you can use the standard GPG that comes with Ubuntu. It is fully PGP-compatible.

Password and Encryption Keys > My Personal Keys > File > New > PGP Key > Continue.
Follow the instructions.

---

