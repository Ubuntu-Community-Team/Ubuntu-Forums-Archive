---
title: "Secure Backup Files"
date: 2009-07-27
forum: Security
---

### Post by dansku on 2009-07-27
Hi, i have a dedicated server, and want to use it to backup my files, like it was a amazon s3, but i want to upload my files in a way they stay cryptographed on the server.

Is there any program or how should i do it?

thanks

---

### Post by Rob_H on 2009-07-27
I would suggest using TrueCrypt, LUKS, or eCryptfs to create an encrypted file system on the server to store the backups. But I believe all of these will require you to supply a passphrase to unlock the file system when the machine starts up, which could be inconvenient for a server. Maybe some of them support a hardware key as an alternative. I don't have experience with that.

Anyway, once you have the encryption set up on the server file system, just copy your files over using your favorite tool. Or, for automated backups of many clients on a regular basis, I'd highly recommend [BackupPC]("http://backuppc.sourceforge.net/"). Among many nice features, BackupPC supports doing backups over an encrypted SSH connection for added protection.

---

### Post by sasho_zl on 2009-07-27
You can encrypt your files with gpg with a command like this:
gpg -v --symmetric --cipher-algo TWOFISH filename
Then you can upload with a method that works best for you.

---

### Post by dansku on 2009-07-27
lets say I have a folder called backup

gpg -v --symmetric --cipher-algo TWOFISH filename

can i use it with a folder?

alseo twofish is the password?

---

### Post by sasho_zl on 2009-07-27
With this command you can only encrypt files. You can create an archive of a folder and then encrypt it. Also TWOFISH is the encryption algorithm. You will be asked for password after you enter the command. A list of the other algorithms that gpg supports you can see by typing **gpg --version**.

---

### Post by jflaker on 2009-07-27
gpg would be the better way...the files are encrypted then transferred....downside, if you lose you private key, your encrypted files are useless, by design.

---

### Post by sasho_zl on 2009-07-28
> **jflaker said:**
> gpg would be the better way...the files are encrypted then transferred....downside, if you lose you private key, your encrypted files are useless, by design.
The symmetric encryption doesn't use the private key. It is done with a password.

---

### Post by FakeOutdoorsman on 2009-07-28
[Duplicity](http://duplicity.nongnu.org/) fits what you are looking for.  It creates remote, encrypted (via GnuPG), incremental backups and is also in the Ubuntu repository.  I currently use it for encrypted backups onto a rented server.

---

### Post by amac777 on 2009-07-30
Hi FakeOutdoorsamn, that Duplicity program looks really neat. I see on its website that it's still in beta though. Have you encountered any bugs while using it? I poked around on launchpad to see how it was doing and looks like it's just getting some bugs worked out, but otherwise looks like a great program for storing encrypted backups on an unsecured server.

---

### Post by FakeOutdoorsman on 2009-08-03
Hi amac777,

I just started using Duplicity and haven't encountered any errors yet.  Development is active (the project started in 2002 I think) and I consider it stable.  You might be interested in joining the [Duplicity mailing list](http://lists.nongnu.org/mailman/listinfo/duplicity-talk) to keep up with new releases and bug fixes.

---

