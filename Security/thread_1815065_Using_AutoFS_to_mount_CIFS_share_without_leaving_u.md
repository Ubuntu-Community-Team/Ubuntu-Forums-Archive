---
title: "Using AutoFS to mount CIFS share without leaving unencrypted passwords"
date: 2011-07-30
forum: Security
---

### Post by r.darwish on 2011-07-30
I followed [this howto]("http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs") in order to mount CIFS shares on demand. This works great, however, this guide suggests leaving my network passwords unencrypted on the disk. This is a very bad security practice, as the passwords can be easly retrieved by booting the computer using a different OS.

I was looking for a way to secure things up, so I came up with this solution: Instead of storing the passwords plain text on the disk, I store them in a tar file encrypted using GPG. When I boot my system, I open this file to a directory in /dev/shm, and order AutoFS to retrieve the passwords from there.

This does the trick, but I presume this solution is not that secure, since /dev/shm content can be written to the swap partition. Is there any other solution which is a better security practice? Maybe using some sort of keyring service?

---

### Post by bodhi.zazen on 2011-07-30
> **r.darwish said:**
> I followed [this howto]("http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs") in order to mount CIFS shares on demand. This works great, however, this guide suggests leaving my network passwords unencrypted on the disk. This is a very bad security practice, as the passwords can be easly retrieved by booting the computer using a different OS.

I was looking for a way to secure things up, so I came up with this solution: Instead of storing the passwords plain text on the disk, I store them in a tar file encrypted using GPG. When I boot my system, I open this file to a directory in /dev/shm, and order AutoFS to retrieve the passwords from there.

This does the trick, but I presume this solution is not that secure, since /dev/shm content can be written to the swap partition. Is there any other solution which is a better security practice? Maybe using some sort of keyring service?

If you are going to be that paranoid, encrypt the entire installation.

---

### Post by r.darwish on 2011-07-31
Is it possible to do so after the system has already been installed? Can I only encrypt root's home folder which actually contains the passwords?

---

### Post by bodhi.zazen on 2011-07-31
> **r.darwish said:**
> Is it possible to do so after the system has already been installed? Can I only encrypt root's home folder which actually contains the passwords?

No you would need to re-install

---

