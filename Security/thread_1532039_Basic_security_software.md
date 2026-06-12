---
title: "Basic security software"
date: 2010-07-15
forum: Security
---

### Post by baguahsing on 2010-07-15
I installed Ubuntu netbook remix 10.04 on an older laptop (Toshiba Satellite Pro 6100) about 2 weeks ago, ie I am a noob.  Looking for recommendations on programs:
 
1. Password manager / generator - I want something that uses strong encryption, the database is encrypted,  the key file can be stored anywhere, flexible password generator, and autofill would be nice.  I have used Keypass in windows and I like it but it lacks autofill.  KeypassX is the linux version but I don't know anything about it.
 
2.  Personal finance - I have used Quicken in windows.  So I'm looking for something easy to use, can go online to update finance info, and a good set of tools would be nice (ie basic tracking, planning, report generating)
 
3. File - directory - disk encryption  - must be able to encrypt / decrypt on the fly and not be a resource hog  - my laptop has a P4 1.6GHz cpu, 1Gb mem, 40Gb hard drive.

---

### Post by wacky_sung on 2010-07-16
1. Password manager / generator
- Use the default installation of seahorse which is pretty safe.Everything is crackable unless through your brain which cannot be able to decrypt.
[[IMG]http://img541.imageshack.us/img541/5899/screenshotaboutseahorse.th.png[/IMG]](http://img541.imageshack.us/i/screenshotaboutseahorse.png/)

2. Personal finance
- It depend what you want but you can choose the difference type of it to meet your needs.
[[IMG]http://img594.imageshack.us/img594/2330/screenshotubuntusoftwar.th.png[/IMG]](http://img594.imageshack.us/i/screenshotubuntusoftwar.png/)

3. File - directory - disk encryption 
- The folder is encrypted with a password and what you need to do is drag and drop your files into the encrypted folder.There is also a timeout session if you needed.
[[IMG]http://img293.imageshack.us/img293/2330/screenshotubuntusoftwar.th.png[/IMG]](http://img293.imageshack.us/i/screenshotubuntusoftwar.png/)

---

### Post by baguahsing on 2010-07-16
Thanks for the inputs wacky.  I've heard of gnucash.  It just that there are so many options out there I don't know which one to pick.  I hate easter egging.  Do you know of a website were people write reviews of linux software?

---

### Post by wacky_sung on 2010-07-16
Choose your personal finance software that meet your needs and nobody know the best as you.

Search any search engines for Linux software review and below is an example.
[http://linux.softpedia.com/](http://linux.softpedia.com/)

---

### Post by rookcifer on 2010-07-16
> **baguahsing said:**
> I installed Ubuntu netbook remix 10.04 on an older laptop (Toshiba Satellite Pro 6100) about 2 weeks ago, ie I am a noob.  Looking for recommendations on programs:
 
1. Password manager / generator - I want something that uses strong encryption, the database is encrypted,  the key file can be stored anywhere, flexible password generator, and autofill would be nice.  I have used Keypass in windows and I like it but it lacks autofill.  KeypassX is the linux version but I don't know anything about it.

LastPass.  Not open source, but it's the best I have found so far, that is if you demand having autofill, etc.  There's also PassPack, which is open-source, but I find it more difficult to use.
 
> 2.  Personal finance - I have used Quicken in windows.  So I'm looking for something easy to use, can go online to update finance info, and a good set of tools would be nice (ie basic tracking, planning, report generating)

GnuCash seems popular.  There are others, too.  You can search the repos.
 
> . File - directory - disk encryption  - must be able to encrypt / decrypt on the fly and not be a resource hog  - my laptop has a P4 1.6GHz cpu, 1Gb mem, 40Gb hard drive.

If you want full disk encryption, you need to use the alternate CD and set up dm-crypt/LUKS that way.  This will require a reinstall.  

If you only want an encrypted container (much like what Truecrypt does) then you can follow [this guide]("http://www.lylebackenroth.com/blog/2008/08/29/encrypting-containers-or-partitions-with-cryptsetup-and-luks/").  That's the technique I use for my encrypted containers (on disks where I am not using FDE).  You can simplify the mounting/unmounting of the container by putting the commands all in a script and making it executable.  If you need help on that, just ask.

If you only want file encryption, you can create a public key with GnuPG (can be done in Seahorse) and then merely right click any file you want to encrypt.  It will ask you which key you want to encrypt to, you select the key and that's it.  If you, for some reason, don't want to create a public key, then you can merely do:

```
gpg -c file
```

It will encrypt it symmetrically with the algorithm you have listed first in your gpg cipher preferences. (Gnupg is already installed on your system).

You can also use OpenSSL (which is also already installed) to do the same thing.  It might be better because it lets you easily define the algorithm you want to use:

```
openssl aes-128-cbc -salt -in file.text -out encrypted_file.txt
```

And, finally, another option for single file encryption would be to use mcrypt.  Mcrypt will have to be installed from the repos, but it provides more algorithm choices (including the infamous Serpent for the paranoid amongst us).  

There are other options as well, but these are the best, imo.

---

### Post by wacky_sung on 2010-07-16
What if you used both Mcrypt and Cryptkeeper,then it will be madness just to crack the encrypted folder and files.Just ponder who will actually do that :D

---

### Post by baguahsing on 2010-07-16
Thanks all.

---

