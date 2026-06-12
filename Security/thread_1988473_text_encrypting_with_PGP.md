---
title: "text encrypting with PGP"
date: 2012-05-27
forum: Security
---

### Post by bobzxr on 2012-05-27
How can I encrypt plain text using PGP (that is, without creating any file)?

Update: 

Because there are currently no PGP/GPG plugin for gedit, install geany with PG plugin from the software center. Once installed, encrypting and decrypting is pretty simple from menu. (first someone has to check the plugin in tools-> tools manager in order to be available)

---

### Post by agillator on 2012-05-27
I didn't know there was a version of PGP for linux. Most of the work I have seen on linux is with GPG (GnuPG). To the best of my knowledge GnuPG is designed to encrypt existing files. What are you trying to do? Why do you not have an unencrypted file to begin with?

OK, apparently you answered your own question while I was preparing my reply. Glad it is solved.

---

### Post by ottosykora on 2012-05-28
> **agillator said:**
> I didn't know there was a version of PGP for linux. Most of the work I have seen on linux is with GPG (GnuPG). To the best of my knowledge GnuPG is designed to encrypt existing files. What are you trying to do? Why do you not have an unencrypted file to begin with?

OK, apparently you answered your own question while I was preparing my reply. Glad it is solved.

gpg is in fact pgp, or better say it is openPGP, all is to some extend the same. It is not only to decrypt something, it is for encryption and decryption of text or files as well as signing and verifying signatures on messages and files. Downloaded files from repositories are signed and will be checked by gpg for example too.

---

### Post by codemaniac on 2012-05-28
> **ottosykora said:**
> gpg is in fact pgp, or better say it is openPGP, all is to some extend the same.

Just for information 
> The terms "OpenPGP", "PGP", and "GnuPG / GPG" are often used interchangeably. This is a common mistake, since they are distinctly different.

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

---

### Post by ottosykora on 2012-05-28
well, everybody wants be different and if possible better then the other one, for the end user as much compatibility as possible in the results is important, not the way to reach them. So all matters is that pgp and gpg produces the same and interchangable formats.

---

### Post by ottosykora on 2012-05-28
> **bobzxr said:**
> How can I encrypt plain text using PGP (that is, without creating any file)?

Update: 

Because there are currently no PGP/GPG plugin for gedit, install geany with PG plugin from the software center. Once installed, encrypting and decrypting is pretty simple from menu. (first someone has to check the plugin in tools-> tools manager in order to be available)

you are a hero!
I have no idea why this functionality was removed from the gedit and I am using at present in fact the java based ppgp (portable pgp) which does the task.

However the geany with the plugin works in fact similar as the extension for gedit used to, very nice discovery. Thanks.

---

### Post by codemaniac on 2012-05-28
It was just for information , did not meant to > "be different and if possible better then the other one" .

---

### Post by ottosykora on 2012-05-28
yep, know, not  personal, ;-)

---

