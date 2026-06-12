---
title: "Dropbox, where is the email address and password saved"
date: 2011-03-23
forum: Security
---

### Post by StutteringJohnSmith on 2011-03-23
I had ubuntu setup on my computer for a few months with dropbox as a backup...  The computer crash and I reinstalled ubuntu but I dont remember the email address I used for dropbox on the computer.  I mounted the old drive so I can access the files. can someone please tell me what dropbox saves the email adress so I can reinstall it on the new computer

than

---

### Post by dgw on 2011-03-24
The email address is in a file called config.db, which is in a folder called .dropbox in your home folder. It's an sqlite file, not a text file, so you can't just view it in gedit. Go to terminal and type: 
```
sudo apt-get install sqlitebrowser
```
Then open up sqlitebrowser and click File > Open Database. Navigate to the config.db file, and open it. Then click on "Browse Data" and scroll down. Near the bottom, it says email on the left, and your email address on the right.

---

