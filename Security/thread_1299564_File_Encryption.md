---
title: "File Encryption"
date: 2009-10-24
forum: Security
---

### Post by jarame on 2009-10-24
I'm hoping that this thread is posted in the correct subsection of the forums (forgive me if it isn't).

How do you put a password lock on certain files? I tried *Right clicking>Encrypt *& [I]Right clicking> Sign

[/I]But it all brought up the *Encrpytion and Keyrings *app but I cannot make a password to encrypt my desired folder/file.

Any help?

---

### Post by pootan on 2009-10-24
If you want a hidden storage that you can place files on an account that other people use the best thing  is TrueCrypt. You can choose to create an encrypted file container that you need a password to access. You can then choose the size for it and add as many folders as you want and just drag and drop files or pics to them/it. You can even hide a second encrypted container inside the first. It sounds complicated but it really just acts as a password protected folder only its a mounted drive. 

Check out the tutorial and if you like it theres a deb package for Linux on the right site map to download. You'll have to Extract the download to somewhere first. Took me all of 5 minutes to set up.  

The only annoying thing is you have to enter the password and straight after your admin rights pass as well.

[http://www.truecrypt.org/docs/?s=tutorial](http://www.truecrypt.org/docs/?s=tutorial)

---

### Post by kevdog on 2009-10-24
gnupg symmetric encryption should be what you want to do!!

---

### Post by jarame on 2009-10-24
> **pootan said:**
> If you want a hidden storage that you can place files on an account that other people use the best thing  is TrueCrypt. You can choose to create an encrypted file container that you need a password to access. You can then choose the size for it and add as many folders as you want and just drag and drop files or pics to them/it. You can even hide a second encrypted container inside the first. It sounds complicated but it really just acts as a password protected folder only its a mounted drive.

Thanks man, I'll definitely check it out!

> **kevdog said:**
> gnupg symmetric encryption should be what you want to do!

Is this any different than the program pootan introduced? Please explain :P

---

### Post by update_manager on 2009-10-24
> **jarame said:**
> Thanks man, I'll definitely check it out!



Is this any different than the program pootan introduced? Please explain :P

Some other choices:
mcrypt, bcrypt, aespipe, ccrypt

If you'd like simple nautilus-integrated encryption, right click on the file and then choose "create archive" with a password. You can install p7zip for better encryption than what the zip command offers.

Truecrypt is arguably a more secure solution since its less likely that unencrypted copies of the file will be stored in swap or elsewhere on the disk. Usually this is a bigger concern when dealing with many files - the decryption of each can be tedious and needs to be scripted, and it becomes more likely that copies will be left around.

---

### Post by jarame on 2009-10-24
> **update_manager said:**
> Some other choices:
mcrypt, bcrypt, aespipe, ccrypt

If you'd like simple nautilus-integrated encryption, right click on the file and then choose "create archive" with a password. You can install p7zip for better encryption than what the zip command offers.

Truecrypt is arguably a more secure solution since its less likely that unencrypted copies of the file will be stored in swap or elsewhere on the disk. Usually this is a bigger concern when dealing with many files - the decryption of each can be tedious and needs to be scripted, and it becomes more likely that copies will be left around.

I kinda wanted just a simple "right click>encrypt with password" type of program. But I'm willing to experiment with whatever is out there. How does Truecrypt work? (if you don't mind explaining)

---

### Post by lensman3 on 2009-10-24
Use gzip and strip off the "PK\003\004" first 4 characters of the zipped file.  The compression will make it look like it is encrypted.  Of course, when you want to read (de-crypt) the file you will have to put the 4 characters back on the front.  The "dd" command will strip off the characters for you.


This idea is not mine.  It is from "Unix Power Tools" circa 1990.

---

### Post by sasho_zl on 2009-10-25
The easyest way is with the symmetric encryption of GPG. Just use the following command:
```
 
gpg --symmetric --cipher-algo TWOFISH filename

```

---

### Post by jarame on 2009-10-25
> **sasho_zl said:**
> The easyest way is with the symmetric encryption of GPG. Just use the following command:
```
 
gpg --symmetric --cipher-algo TWOFISH filename

```


i typed a file name and it didnt register.

```
jarame@ubuntu:~$ gpg --symmetric --cipher-algo TWOFISH blah
gpg: can't open `blah': No such file or directory
gpg: symmetric encryption of `blah' failed: file open error
```

i made a test folder to see how it would work out and thats what i got as a result. any help?

---

### Post by update_manager on 2009-10-25
> **jarame said:**
> I kinda wanted just a simple "right click>encrypt with password" type of program. But I'm willing to experiment with whatever is out there. How does Truecrypt work? (if you don't mind explaining)

Its complex and good. It creates an encrypted container that looks like a big file. Once unencrypted the file looks like a disk drive. Its not as easy to use as the others mentioned.

---

### Post by update_manager on 2009-10-25
> **jarame said:**
> i typed a file name and it didnt register.

```
jarame@ubuntu:~$ gpg --symmetric --cipher-algo TWOFISH blah
gpg: can't open `blah': No such file or directory
gpg: symmetric encryption of `blah' failed: file open error
```

i made a test folder to see how it would work out and thats what i got as a result. any help?

"blah" must be a file.

---

### Post by sasho_zl on 2009-10-26
> **jarame said:**
> i typed a file name and it didnt register.

```
jarame@ubuntu:~$ gpg --symmetric --cipher-algo TWOFISH blah
gpg: can't open `blah': No such file or directory
gpg: symmetric encryption of `blah' failed: file open error
```i made a test folder to see how it would work out and thats what i got as a result. any help?

With this command you can encrypt files and archives of a folder but not a normal folder.

---

### Post by kevdog on 2009-10-26
gpg symmetric encryption as stated above is really designed for individual files.  If you want to recursively encrypt a directory with this method -- the only fast implementation I am aware of with this method is a program known as gpgdir: [http://www.cipherdyne.org/gpgdir/](http://www.cipherdyne.org/gpgdir/)

The program author also makes a program called fwknop which is my favorite port knocker implementation(yes a shameless plug but I'm in no way connected to this product!!)

---

### Post by kkady32 on 2009-11-16
$ gpg --symmetric --cipher-algo TWOFISH blah
 that is what i need ,tx

---

