---
title: "Major problem with encrypted /home"
date: 2010-05-05
forum: Security
---

### Post by schristo on 2010-05-05
Hello all,

I have a major major issue with an encrypted /home directory. I had used encryption on my home directory when I installed 9.10. However, I had not noticed that I needed to store the automatically generated passphrase anywhere. Now, upon installing 10.04, my home directory would not decrypt. I checked my .encryptfs directory and the wrapped-passphrase file is GONE. I only have the Private.sig files from my 9.10 installation and of course know the login password I binded to the passphrase. I can see my .Private directory with filenames starting with ECRYPTFS_FNEC_ENCRYPTED.

Now, my PhD thesis which I have to deliver in 2 weeks is in there. With no backups. I would truly appreciate it if anyone could help me recover my data. If no 'normal' method would work, is it possible to use a brute force attack and feed it my login password??

I would truly appreciate any help, as you can imagine losing 4 years of very hard work is a bit more than devastating.

---

### Post by DZ* on 2010-05-05
> **schristo said:**
> I checked my .encryptfs directory and the wrapped-passphrase file is GONE

Prior to 9.10, it used to sit in /var/lib/ecryptfs/$USER/wrapped-passphrase
([http://blog.dustinkirkland.com/2010/02/attention-encrypted-home-users.html](http://blog.dustinkirkland.com/2010/02/attention-encrypted-home-users.html))
Perhaps it's still there?

---

### Post by Kobalt on 2010-05-06
Or you can re-record your passphrase : [http://blog.nschirrer.com/change-login-password-ecryptfs-passphrase](http://blog.nschirrer.com/change-login-password-ecryptfs-passphrase)

---

### Post by Irihapeti on 2010-05-07
I found this link among my bookmarks.

[http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

---

