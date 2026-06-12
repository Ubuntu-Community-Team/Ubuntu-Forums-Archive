---
title: "Home Server: Automatically Encrypt Files?"
date: 2007-04-15
forum: Server Platforms
---

### Post by SSTwinrova on 2007-04-15
I'm in the process of setting up an old computer out in our garage to act as a backup server and media storage server for all of my music and ripped DVDs. For the backup part, a big focus of it is so that my dad can backup his important personal things off of his laptop in case of a crash. I realized yesterday that this would include our TurboTax files, but I would prefer to encrypt those on the server in case it ever got stolen or something. I plan on having him back stuff up (or have it run automatically) over FTP, so is there a setup that will automatically encrypt files when added to a directory?

---

### Post by BoneKracker on 2007-04-17
You probably want to create an encrypted partition to put your "dad's turbotax files" on.

---

### Post by tone77 on 2007-04-17
If I were you, I would use TrueCrypt to encrypt a partition on the backup server.  [http://www.truecrypt.org/](http://www.truecrypt.org/)

to quote their site: 
> 
Main Features:

    * Creates a virtual encrypted disk within a file and mounts it as a real disk.

    * Encrypts an entire hard disk partition or a storage device such as USB flash drive.

    * Encryption is automatic, real-time (on-the-fly) and transparent.

    * Provides two levels of plausible deniability, in case an adversary forces you to reveal the password:

      1) Hidden volume (steganography – more information may be found here).

      2) No TrueCrypt volume can be identified (volumes cannot be distinguished from random data).

    * Encryption algorithms: AES-256, Serpent, and Twofish. Mode of operation: LRW.

      Further information regarding features of the software may be found in the documentation.


---

