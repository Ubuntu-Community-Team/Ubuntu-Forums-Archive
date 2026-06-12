---
title: "Are private home folders supposed to run as root?"
date: 2010-01-03
forum: Security
---

### Post by dogdo on 2010-01-03
Hi

According to the picture i uploaded my private folder is owned by root-should it not be owned by the user? Is my private folder running as a full admin?

---

### Post by teward on 2010-01-03
Owned by root and running as root are different.

Running as root would mean being the root account, where as owned by root means that root has full rights in the folder.

---

### Post by teward on 2010-01-03
Also, what you're double-clicking (the icon) is a Sym-Link, and it links to somewhere else.  This means the link cannot be deleted by anyone other than root.

---

### Post by FuturePilot on 2010-01-03
That is a symlink to a program that will allow you to enter your password and unlock your private directory so you don't have to manually run the commands to do it. The symlink is owned by root. Unlock your private directory and check the permissions on a file in there. It probably belongs to your user.

---

### Post by dogdo on 2010-01-04
Ok mounted private folder and files inside are owned by me the user :)

Though one thing still worries me-if a hacker was able to bypass ip tables firewall and get direct access to my home folder, would the hacker be able to access the files if i was logged on as a low level user who had already mounted the files?

---

### Post by bodhi.zazen on 2010-01-04
> **dogdo said:**
> Ok mounted private folder and files inside are owned by me the user :)

Though one thing still worries me-if a hacker was able to bypass ip tables firewall and get direct access to my home folder, would the hacker be able to access the files if i was logged on as a low level user who had already mounted the files?

Yes, that is the "problem" with encryption. Encryption only helps if the files are not decrypted.

In your example, if you are logged in, and you decrypt your home directory, then the information is decrypted and your protection would be Linux permissions, which wuld not help much if a cracker had root access.

---

