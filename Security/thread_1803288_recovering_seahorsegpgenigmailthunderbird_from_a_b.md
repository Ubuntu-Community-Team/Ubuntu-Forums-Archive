---
title: "recovering seahorse/gpg/enigmail/thunderbird from a backup of /home?"
date: 2011-07-13
forum: Security
---

### Post by brallan on 2011-07-13
I was using enigmail and thunderbird to do gpg encryption, and now that I reinstalled, I cannot get them working to decrypt my old messages again. From a backup of my old /home directory, I copied the .gnupg and .thunderbird folders to my new /home and restarted, but it says I am missing the private key.  I tried reinstalling thunderbird, enigmail, and seahorse, but no luck. 

Are the keys NOT stored in the home directory? Is there another folder that I need to copy? Could this be a permissions issue?

---

### Post by brallan on 2011-07-14
bump

---

### Post by DZ* on 2011-07-15
Perhaps you don't have gpg-agent installed or running. Try
```
sudo apt-get install gnupg-agent
```
and re-login

---

