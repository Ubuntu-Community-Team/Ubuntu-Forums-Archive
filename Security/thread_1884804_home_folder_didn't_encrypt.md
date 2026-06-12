---
title: "home folder didn't encrypt"
date: 2011-11-22
forum: Security
---

### Post by dd76 on 2011-11-22
Had an interesting reinstall this week.  I recently tried Mint Linux 11 and upon realizing that it gave my PC acid indigestion I went back to Ubuntu 10.04.  When I reloaded I formated the partitions and then told the loader to encrypt the home folder (requiring password for login and encryption).  Now this is the strange part the home folder did not encrypt and the 2nd user account I created did not encrypt its home folder despite the box being checked.  Even stranger was the fact that the second user account had full access to the primary user account.  I have never had this happen and its about the 5th time I have reloaded or changed things around.  I manually encrypted the home folders so no harm done, I think.  What I was wondering was if anyone else has had this happen?  Also is there a quick terminal command that will tell if a folder(s) is encrypted?

---

### Post by OpSecShellshock on 2011-11-22
What method did you use to check the encryption of the folders? When the users are logged in their home folders won't be encrypted.

---

### Post by dd76 on 2011-11-22
what first alerted me was me browsing in the /home folder (as user2) I noticed that my admin folder did not have an X over the icon indicating it was not accessible from user2 so i clicked on it and was able to browse and open any file in admin folder.  Thats when it occurred to me that I had never been prompted to get the passphrases after the reload.

---

