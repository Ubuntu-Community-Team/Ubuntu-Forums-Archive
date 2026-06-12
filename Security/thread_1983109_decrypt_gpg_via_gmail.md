---
title: "decrypt gpg via gmail"
date: 2012-05-19
forum: Security
---

### Post by jon zendatta on 2012-05-19
Hi all

Not sure if I should be here or general. Have created a GPG key and registered on Ubuntu server.
I have an email from launchpad to validate my key via gmail. FireGPG doesn't work. 
How do I save as txt file to open in Terminal and enter my passphrase?
I tried copying & paste in to gedit and save as file.txt and file.gpg. Both times I got error I didn't have priveleges. I assume I use gksudo?
Could someone be more specific in this proceedure please?:KS

---

### Post by jon zendatta on 2012-05-19
Mystery solved.
Saved encrypted message as file.txt, as Super user. Then:
```
gpg --decrypt file.txt
```:KS

---

### Post by ottosykora on 2012-05-20
yes, one those step backs , before it was possible to decrypt/encrypt text with a plugin directly in  the gedit. It is now gone unfortunately.

Still you can decrypt text in thunderbird/enigmail or evolution comfortably.

Decryption of files is still possible in nautilus/seahorse, thought encryption is broken.

---

### Post by kevdog on 2012-05-21
I think the Chrome browser also has a firegpg like extension but its definitely not as useful as firegpg in terms of functionality.

---

