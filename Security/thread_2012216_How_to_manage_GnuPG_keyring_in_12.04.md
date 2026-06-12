---
title: "How to manage GnuPG keyring in 12.04?"
date: 2012-06-28
forum: Security
---

### Post by skywriter on 2012-06-28
I have used seahorse since 9.04. But in 12.04 I unable to use it because of it's poor interface. And it's buttons are disabled. What is going wrong?

---

### Post by ottosykora on 2012-06-30
> **skywriter said:**
> I have used seahorse since 9.04. But in 12.04 I unable to use it because of it's poor interface. And it's buttons are disabled. What is going wrong?

well you need to install seahorse-nautilus, this is how they call it today. For key management it is ok then , the GUI di dnot much change.
For decryption it seems to work too, but encryption makes problems, as it often chooses rather random key from the keyring instead the one select.

---

### Post by skywriter on 2012-07-04
How to use seahorse-nautilus for managing keys? I have obtain only encrypt option by right-click.

---

### Post by ottosykora on 2012-07-05
it is not in the right click, it is in the menu or simply under manage keys.
you can also start seahorse from command line and this GUI for managing keyring will come up.

---

### Post by skywriter on 2012-07-05
If I start seahorse from command line, I cannot generate new key. I also unable to find how to generate new key and export existing key from nautilus.

---

### Post by cariboo on 2012-07-05
You can create new keys by going to File->New and import them via File->Import. See the screenshot.

---

### Post by skywriter on 2012-07-07
Thank you very much! I forgot about Unity's main menu at the top of the deskop!

---

