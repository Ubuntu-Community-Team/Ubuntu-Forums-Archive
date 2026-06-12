---
title: "File and Folder Encryption"
date: 2007-06-15
forum: Server Platforms
---

### Post by TorchlightJay on 2007-06-15
Ya, so I we all have files that we don't want any tom, dick, or harry to see and so encryption is neccessary. Anyone know how to encrypt files and folders? What's a good program to use and what tutorials apply to it? Thank you for your time and assistance.

---

### Post by earobinson on 2007-06-15
you could zip them with a password

---

### Post by netlogic on 2007-06-15
There might be a better solution, but I like Truecrypt. It is for Windows and Linux. Linux version is CLI only.

[http://www.truecrypt.org/](http://www.truecrypt.org/)
documentation
[http://www.truecrypt.org/docs/](http://www.truecrypt.org/docs/)

---

### Post by cobrn1 on 2007-06-15
Truecrypt is quite cool, but it's quite complicated and linux has only a CLI ver. To be honest, if he just wants to hide a few files then it's a bit like using a sledgehammer to crack a nut (however, it would work, if you have very sensitive files it very good and it sort-of gives you plausible deniability - you'd have to look at the website to find out more).

However, if my memory serves me right if they are zipped into a .rar file you can but a password on that and that's unbreakable (it is encrypted - not just 'passworded') - brute force is the only way, so choose a long password.

Have a look at the truecrypt website and see if it interests you. If not then zipping files almost certainly covers your needs.

---

### Post by netlogic on 2007-06-15
I don't know anything about using passwords on a zip or rar. If it uses some form of hash and it is possible to extract the hash key, It is possible to use predefined tables to crack within few minutes. That isn't a brut force. This is just matching the key someone already defined. I haven't really researched it.  I would go with an encryption. Once, Truecrypt is setup, it is really easy to use. Gpg is easier, but less robust compare to Truecrypt.

To encrypt with gpg
gpg -c filename
To extract
gpg filename

---

### Post by Mike'sHardLinux on 2007-06-16
During my usual reading at Ubuntuforums, I am sure I have come across at least 1 gui frontend for Truecrypt. Do a search.....

---

### Post by elst on 2007-06-17
FWIW, Seahorse provides a graphical interface to GnuPG.

---

### Post by HeadGeek on 2007-06-17
> **Mike'sHardLinux said:**
> During my usual reading at Ubuntuforums, I am sure I have come across at least 1 gui frontend for Truecrypt. Do a search.....
If that was Forcefield, I haven't gotten it to work properly so far.

---

### Post by Konqi on 2008-07-11
> **elst said:**
> FWIW, Seahorse provides a graphical interface to GnuPG.

Seahorse is only a GPG and SSH key manager ([http://en.wikipedia.org/wiki/Seahorse_(software)]("http://en.wikipedia.org/wiki/Seahorse_(software)")).

GPA "aims to be the standard GnuPG graphical frontend" ([http://www.gnupg.org/related_software/frontends.en.html]("http://www.gnupg.org/related_software/frontends.en.html")).

---

### Post by vanadium on 2008-07-11
Another option is encfs. While truecrypt creates an encrypted volume where you store your files, encfs encrypts at the "file" level. There is a nice how-to here:
[http://www.debuntu.org/node?page=5](http://www.debuntu.org/node?page=5)

---

