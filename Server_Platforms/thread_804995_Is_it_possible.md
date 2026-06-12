---
title: "Is it possible?"
date: 2008-05-23
forum: Server Platforms
---

### Post by JackBurton on 2008-05-23
Hi,
I need to have an entire partition encrypted (and this is easy with the community tutorials) but I want to have it ready after a reboot without human actions (i.e. without requesting password at boot).

I know this lead me to have the password (or passphrase key) clear on the server, but it's a minor problem for what I have to do.

Could someone help me?
I'd like to use the standard dm-crypt method to encrypt (as exlpained here -> [https://help.ubuntu.com/community/En...ilesystemHowto](https://help.ubuntu.com/community/En...ilesystemHowto) or here -> [https://help.ubuntu.com/community/En...lesystemHowto3](https://help.ubuntu.com/community/En...lesystemHowto3))

Thank you very much!

P.S. I'm using Ubuntu 6.06 Server

---

### Post by SuperCzar on 2008-05-23
> **JackBurton said:**
> 
I know this lead me to have the password (or passphrase key) clear on the server, but it's a minor problem for what I have to do.


Perhaps you can explain why you need to encrypt a partition but do not mind having the password stored on the computer?

---

### Post by JackBurton on 2008-05-23
> **SuperCzar said:**
> Perhaps you can explain why you need to encrypt a partition but do not mind having the password stored on the computer?
Sure...
I'm thinking of a remote server (SSH): I want to put a mysql database of a web application on the encrypted partition.
I'd like to let reset my server (by housing mantainer people) without post-boot human interaction.

In other words, when someone reboot my server I want my web application, after the boot process, online.

Thanks in advance

---

### Post by samosamo on 2008-05-23
He was asking what the point of encryption was, when anyone standing physically in front of the server can access it?  The idea behind encrypting a file system is that anyone with physical access to the hard drive won't be able to read the data on it.

---

### Post by Steve413z on 2008-05-23
yes, but it's completely unpractical

you can put the key (usb stick or smartcard) in the computer and leave it there, but that defeats the purpose of the encryption, because the key is with the computer anyway

if you are trying to encrypt backups, I recommend a program called "duplicity" [http://duplicity.nongnu.org/](http://duplicity.nongnu.org/) it uses GnuPG to encrypt the backup files, and can upload files using many protocols including FTP and SSH

---

### Post by JackBurton on 2008-05-24
If you cannot login you cannot access my encrypted partition (in this way I can save the key or the passphrase on another partition: as soon as you cannot break in as root you cannot read my encrypted partition).

Surely if someone could physically take the hard drives my encryption is lost (although the server case is well protected against opening), but that's another problem.

The point here is: if something goes wrong and I have to reboot my remote server without the possibility to enter a password, can I have my application (i.e. my encrypted database) online and ready?

---

### Post by hyper_ch on 2008-05-25
with physical access you can login and access your encrypted partition...

storing the key unencrypted defeats the whole purpose of encryption.

---

### Post by JackBurton on 2008-05-25
Ok if it's not possible, I don't care if it doesn't have too much sense.

---

