---
title: "[SOLVED] Mount eCryptfs directory automatically with PAM"
date: 2008-12-09
forum: Security
---

### Post by vlc on 2008-12-09
Hi *,

I am trying to mount an eCryptfs-encrypted directory automatically using the PAM module as described in [http://ecryptfs.sourceforge.net/README]("http://ecryptfs.sourceforge.net/README").

But when rebooting my PC, I must still enter the encryption type and password *before* logging in, similar to *mount -t ecryptfs*.

If I understand the description in [http://ecryptfs.sourceforge.net/README]("http://ecryptfs.sourceforge.net/README") correctly, the directory should be mounted *after* login and the password should be derived from the login password:

> You can use the PAM module to automatically use a key based on your login passphrase, which can then be used to perform an eCryptfs mount non-interactively.

I attached a file with all the commands I have executed.

Does anyone have an idea what to do to mount the directory automatically?

Thanks a lot in advance!

---

### Post by vlc on 2008-12-15
It was a missing "noauto" in the README file for the /etc/fstab options.

---

### Post by Thomas Oliveira on 2011-07-25
Vlc, thank you for your help!

Does anyone know how I can avoid the message "Could not find key with description..."

Thanks,

---

