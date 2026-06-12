---
title: "No seahorse plugins in Ubuntu 12.04 - why?"
date: 2012-05-30
forum: Security
---

### Post by yeehi on 2012-05-30
There seem to be no [seahorse plugins]("https://launchpad.net/ubuntu/precise/+source/seahorse-plugins") available for ubtuntu 12.04.

I am a bit surprised about this.

Why weren't they included? They are useful for GPG encryption and decryption.

---

### Post by cariboo on 2012-05-30
This was discussed fairly recently in this subforum, see this thread:

[http://ubuntuforums.org/showthread.php?t=1928660](http://ubuntuforums.org/showthread.php?t=1928660)

Is seahorse-nautilus what you are looking for? It's in the repositories.

---

### Post by ottosykora on 2012-05-31
Just I would add that this new plugin is some kind of broken. It works for decryption of files, but when it comes to encryption it is buggy and it selects rather random key from the keyring. It offers to select a key as it should be, but will then pick just about any key it finds. So not very useful.

---

### Post by cariboo on 2012-05-31
> **ottosykora said:**
> Just I would add that this new plugin is some kind of broken. It works for decryption of files, but when it comes to encryption it is buggy and it selects rather random key from the keyring. It offers to select a key as it should be, but will then pick just about any key it finds. So not very useful.

Have you created a bug report? Or is there an existing one?

Bugs effecting security, usually get repaired fairly quickly.

---

### Post by ottosykora on 2012-05-31
well actually I have send a mail to one of the devs listed in the about.

There are many other problems as well, the seahorse has its own passphrase deamon and this one fights with other passphrase caching agent. In some cases it is not possible to clear the passphrase from the cache which makes the whole seahorse plugin very dangerous as it has no own control over the caching of the passphrase.

For that reason I had to remove the nautilus components of seahorse until they get fixed.

---

### Post by ottosykora on 2012-05-31
> **cariboo907 said:**
> Have you created a bug report? Or is there an existing one?

Bugs effecting security, usually get repaired fairly quickly.

so now I had some time and filed two more bugs for the seahorse and its components, but there are so many bugs reported and apparently there is nobody interested in clearing them.

It did all work fine in 10.10 still, but now all seem to be broken.

Also I was surprised why the text encryption decryption addon was simply removed from the gedit, for no reason I would say, as similar mechanism is now found in geany and works there fine.

---

### Post by ottosykora on 2012-06-01
Just want to mention: got some response from one of the devs of seahorse, basically meaning the problem is with ubuntu and not with seahorse, I should complain with ubuntu.

:-(

---

