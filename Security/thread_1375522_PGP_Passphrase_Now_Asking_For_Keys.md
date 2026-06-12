---
title: "PGP Passphrase Now Asking For Keys?"
date: 2010-01-08
forum: Security
---

### Post by OrionXIII on 2010-01-08
Okay, I'm a relatively new Ubuntu user (SO much better than Windows!) so I'm guessing that this is a really simple issue.

While on deployment to an unnamed Middle Eastern desert with my Army unit, I encrypted several files by right-clicking on them and entering a passphrase. I was given the option to have several files grouped together in a .tar file, which I selected. Previously, I could decrypt the files by double-clicking on the file and entering the passphrase.

My hard drive was destroyed during my deployment and I was forced to reinstall everything and restore the data from a backup. My installation of Ubuntu is completely up to date. But now when I double-click on the files, I am told that I do not have the key-pair. I've tried running the 'keys' application and entering the passphrase as a PGP key, but all that happens when I double-click on the file, I get the same pop-up that I don't have the right key-pair...

I'm guessing I'm making a really simple newbie error here...any help would be greatly appreciated!

Respectfully,

Orion

---

### Post by Agent ME on 2010-01-08
What happens if you open a terminal (Applications -> Accessories -> Terminal), and type "gpg *filename.gpg*"? Make sure to give the path to the file if its not in your home directory.

---

### Post by OrionXIII on 2010-01-08
I get the following:
gpg: encrypted with ELG-E key, ID <HEX>
gpg: decryption failed: secrety key not availableI

---

### Post by tubbygweilo on 2010-01-08
Orion, Do you have a separate disk or usb  stick containing a backed up copy of your .gnupg folder and associated files? I fear that without this you may well not be able to decrypt objects due to the loss of your secret key.

---

### Post by OrionXIII on 2010-01-08
Nope - the drive was physically destroyed, I'm afraid and the backup was just the data files.

I know the passphrase that was used to encrypt the files; is there no way to regenerate that type of key? I've tried using Windows PGP with both types of keys but no luck...

Thank you for your help!

---

### Post by tubbygweilo on 2010-01-08
Sorry to be the bringer of bad news but you can not recreate the secret key needed. I am now out of ideas:(

---

### Post by OrionXIII on 2010-01-08
Drat!!

Ah well, nothing that can't be recreated, I suppose...Thanks again for the help! At least now I can stop wasting time on it!

---

### Post by BkkBonanza on 2010-01-08
And you've learned the hard way in future to always backup your .gnupg directory. Probably not with your regular data either but in some secret place. Also if you use ssh to access other systems then backup the .ssh directory too.

I've found those little microSD cards good for this because they are so tiny you can hide them in very small places. I used to tape one under a "hard to reach place" as a last resort backup.

Another great thing is "keepassx" password safe. It stores data encrypted with a master password and can store keys as well. I keep a copy out on the web so that I can always get it if I lose my notebook.

---

### Post by OrionXIII on 2010-01-08
See, that's one of the things I really loathe about the whole 'keyring' concept. What's the point of encrypting my files if all someone needs to do is gain access to my hard drive and they have all my keys?

That makes it about as secure as titling the file "DO NOT READ ME.txt"...

I much prefer the passphrase system where you have to enter the right passphrase each time you want to decrypt a file. Don't suppose there's any way to set things up that way, is there?

Thanks again for all your help!

Orion

---

### Post by rookcifer on 2010-01-08
> **OrionXIII said:**
> See, that's one of the things I really loathe about the whole 'keyring' concept. What's the point of encrypting my files if all someone needs to do is gain access to my hard drive and they have all my keys?

Your private key is itself encrypted and cannot be decrypted without providing a key (which is usually a password).  So, even if they have physical access to your machine, they cannot get your private key without knowing the pass phrase to unlock it.

The problem you are having is that your private key must be present in order to decrypt files (even if you know the password).  Since your private key was not backed up, it doesn't help to know the password since the key itself is missing.

Think of it this way:

passphrase ---> private key ----> encrypted files

You are missing the middle part of this chain.  If someone had access to your machine they would be missing the first part of the chain, so they couldn't decrypt the files, just as you cannot right now since you are missing the 2nd part of the chain.


I hope this makes sense.

---

### Post by OrionXIII on 2010-01-08
> **rookcifer said:**
> 
Think of it this way:

passphrase ---> private key ----> encrypted files

You are missing the middle part of this chain. If someone had access to your machine they would be missing the first part of the chain, so they couldn't decrypt the files, just as you cannot right now since you are missing the 2nd part of the chain.


I hope this makes sense.

Makes lots of sense and an excellent explanation - I can't recreate the key as the  prime number will be different, so I'm screwed on that one. :-)

So, if someone copies my key file off of my laptop, it's not usable? It looks to me like whenever I log in, I can load whatever key file I want and use it and it only asks me for the passphrase when I want to change it...Thank you, by the way, for educating me in my ignorance!

I'm already creating backups of my current data files for the programs that I use, as well as the PGP directory now too! :-D

I'm loving using Ubuntu after years and years of supporting Microsloth's garbageware...I just keep being stunned at how easy it is to use, how stable and how reliable...I haven't had a crash (barring my doing stupid stuff that thrashes the O/S) since I started using it...

You might enjoy this:

[New O/S-based Airlines In The Works!]("http://blog-in-the-box.blogspot.com/2009/10/new-airlines-in-works.html")

Though I'd bet you've seen it. LOL

---

### Post by zero244 on 2011-07-01
I think what most people posting on this issue are missing is it is much easier to remember a pass phrase than it is to save a backup of a key file in the case of a hard drive failure.

Windows has several encryption programs the encrypt and decrypt with just a pass phrase.
Now I realize this is not as secure, but some people like myself just want some extra security, not stop the CIA or FBI.
 
A correct me if I am mistaken, a person can decrypt your files with the key file.....he just has to guess the pass phrase which is no harder than guessing the pass phrase for a pass phrase only program
So if someone steals your computer which will probably have the key file on board he can decrypt your files as soon as he cracks your pass phrase.

It would be nice if programs like decrypt in Nautilus would give you the option to use a keyless encryption routine.

---

### Post by Irihapeti on 2011-07-01
If you want to encrypt a file without using a key, use the following command:
```
gpg -c <filename>
```
(Sorry, I don't know how to do this with a GUI.)

This can be decrypted with ```
gpg <filename>.gpg
```

Alternatively, you can decrypt it using "open with decrypt file".

Source: [http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html](http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html)

Further options for encryption/decryption are mentioned here: [http://www.cyberciti.biz/tips/linux-or-unix-password-protecting-files.html](http://www.cyberciti.biz/tips/linux-or-unix-password-protecting-files.html)

I've only tried the openSSL method.

---

