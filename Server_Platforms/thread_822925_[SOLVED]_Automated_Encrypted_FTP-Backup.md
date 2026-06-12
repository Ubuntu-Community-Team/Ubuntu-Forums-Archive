---
title: "[SOLVED] Automated Encrypted FTP-Backup"
date: 2008-06-08
forum: Server Platforms
---

### Post by The Devil Is A Squirrel on 2008-06-08
Hi guys,

I'm looking for something like '[duplicity]("http://duplicity.nongnu.org/")+[ftplicity]("http://ftplicity.sourceforge.net/")', but little bit more secure. I don't like the fact that I have to expose my GPG password in the ftplicity config file. I wish it would just take my public key and encrypt the files with that.

Does anybody know an ***easy*** solution for that?

Cheers


Howto: [http://howtoforge.com/ftp-backups-with-duplicity-ftplicity-debian-etch](http://howtoforge.com/ftp-backups-with-duplicity-ftplicity-debian-etch)

---

### Post by hyper_ch on 2008-06-09
where's the difference whether you store the gpg password in ftplicity or whether it just takes your public key?

If somebody gains access to the machine as root then either is compromised...

---

### Post by The Devil Is A Squirrel on 2008-06-09
> **hyper_ch said:**
> where's the difference whether you store the gpg password in ftplicity or whether it just takes your public key?

If somebody gains access to the machine as root then either is compromised...

True. I didn't think this through...  :lolflag:

---

### Post by hyper_ch on 2008-06-09
;) just make sure you have a backup of the privat gpg key somewhere else ;)

---

### Post by chmac on 2008-12-15
> **hyper_ch said:**
> where's the difference whether you store the gpg password in ftplicity or whether it just takes your public key?

If somebody gains access to the machine as root then either is compromised...

There's some advantage in using only a single piece of software.

The GPG key can be provided to duplicity directly in the form of an environment variable PASSPHRASE. See [point 9 here]("http://www.rsync.net/resources/howto/duplicity.txt"). That might be a little cleaner than using the ftplicity wrapper.

---

### Post by HermanAB on 2008-12-15
If you want strong security, then you should use SSH (SFTP).

---

### Post by chmac on 2008-12-15
> **HermanAB said:**
> If you want strong security, then you should use SSH (SFTP).

There's no reason not to use SFTP, but if you're transferring securely encrypted files, pushing them over FTP shouldn't be a major concern. Data transmitted over FTP is not "secure" but it's also not readily available to anyone who wants it.

---

