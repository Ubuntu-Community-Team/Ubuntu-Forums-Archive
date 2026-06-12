---
title: "File Encryption Tools"
date: 2007-05-20
forum: Server Platforms
---

### Post by nick1 on 2007-05-20
Greetings,

I have a file that contains some confidential information (accounts, passwords, etc.).
I would like to encrypt and decrypt this file whenever I need to access the contents of the file.
I am looking for recommendations on encryption software that I can use on Ubuntu 6.06 LTS Dapper Drake.
My company uses the trial version of PGP Desktop but I would prefer to use an open-source solution instead which is just as secure and preferably compatible with PGP Desktop.

It would be ideal if I could carry the encrypted file with me on a USB device and still be able to access the file on a non-Ubuntu computer.

Thank you for your time,

*Nick*

---

### Post by psusi on 2007-05-20
Take a look at gpg.

---

### Post by rich.bradshaw on 2007-05-21
yeah gpg is exactly what you need. I think seahorse is the GUI in GNOME. Kgpg in KDE.

---

### Post by angelmartinezn on 2007-05-22
For file encryption I use truecrypt : [http://www.truecrypt.org/]("http://www.truecrypt.org/")

for password encripted storing I use keepassx : [http://keepassx.sourceforge.net/]("http://keepassx.sourceforge.net/")

Both apps work in Linux and Windows...

---

### Post by wieman01 on 2007-05-22
Been using Truecrypt for years and I am fairly happy with it. Give it a go.

---

### Post by nick1 on 2007-06-08
Greetings,

I just installed Seahorse and now I'm attempting to generate my PGP key by following these steps:

1.) Accessories > Passwords and Encryption Keys

2.) Key > Create a New Key > PGP Key

3.) Filled in my Full name, email address, and a brief comment

4.) Left the default advanced options in place

The key generation process starts but eventually fails with the following error:

"Couldn't generate PGP key: general error"

I installed Seahorse via Synaptic.  Synaptic is showing that GNUPG (version 1.4.2.2-1ubuntu2.5) and Seahorse (version 0.9.7-0ubuntu1~dapper1) are installed.

Surprisingly a Google search didn't return much at all.  I would appreciate your help.

Edit:
According to [http://www.gnome.org/projects/seahorse/download.html](http://www.gnome.org/projects/seahorse/download.html) the current stable release is Seahorse 1.0.1.  I don't see a way to upgrade Seahorse through Synaptic.  How can I upgrade Seahorse to the latest version?

Thank you for your time,

---

### Post by pager on 2007-06-09
Gpg

---

### Post by TradiZ on 2007-06-09
Gringotts is an excellent tool too.... :-) But it does not travel on usb sticks, It would be great with a portable gringotts though... :-)

TradiZ

---

### Post by nick1 on 2007-06-15
Greetings,

I have GPG installed and I just tested it out by encrypting a plain text document called *test*.
GPG encrypted *test*, creating a new file called *test.gpg* and leaving the original *test* file intact.  This is annoying to me and scary at the same time.

Having been told from several security professionals that all data can potentially be recovered from a hard drive even if the data was deleted using the usual delete methods (shift-delete, for example), I would like GPG to encrypt the file I point it to and NOT leave the original file intact.

So, tell GPG to either directly encrypt the file I point it to or, if it can't do that, securely delete the original file after the encryption process completes.

Since data can be recovered from a hard drive even after the data has been deleted, I'm told a more secure method to delete data is to first encrypt it and then delete it.  That way, if the data can be recovered, it would still need to be decrypted to be read.

I would appreciate some suggestions.  Thank you for your time,

---

### Post by psusi on 2007-06-19
After encrypting the file, **shred** it.

---

### Post by vanadium on 2007-06-19
If it is just to store some passwords and account information in a safe place, you can use revelation. There is even a desk bar applet, and in fact, I find myself using it all the time as a shortcut to this forum.

---

### Post by Damiel on 2007-07-12
> **nick1 said:**
> Greetings,

I just installed Seahorse and now I'm attempting to generate my PGP key by following these steps:

1.) Accessories > Passwords and Encryption Keys

2.) Key > Create a New Key > PGP Key

3.) Filled in my Full name, email address, and a brief comment

4.) Left the default advanced options in place

The key generation process starts but eventually fails with the following error:

"Couldn't generate PGP key: general error"

I installed Seahorse via Synaptic.  Synaptic is showing that GNUPG (version 1.4.2.2-1ubuntu2.5) and Seahorse (version 0.9.7-0ubuntu1~dapper1) are installed.

Surprisingly a Google search didn't return much at all.  I would appreciate your help.

Edit:
According to [http://www.gnome.org/projects/seahorse/download.html](http://www.gnome.org/projects/seahorse/download.html) the current stable release is Seahorse 1.0.1.  I don't see a way to upgrade Seahorse through Synaptic.  How can I upgrade Seahorse to the latest version?

Thank you for your time,

I don't know if you still need help, but just in case...

Open a terminal and run this command:
```
gpg --gen-key
```

If you get some "Permission denied" error messages, then for some reason your .gnupg folder is owned by root and not by you. Dunno why I had the same problem. So, run this command in the terminal, replacing *your_username* with your actual username:
```
sudo chown -R your_username:your_username ~/.gnupg/
```

After that, Seahorse (and gpg) should work flawlessly.

---

