---
title: "gpg help"
date: 2007-01-23
forum: Server Platforms
---

### Post by healthpellets on 2007-01-23
Hello all.  I have limited previous experience with PGP having used it briefly in college some 6 years ago.  I didn't do much with it other than decrypt email messages from a secure contact.  

The purpose of using an encryption tool is that I am an attorney and I have client files that I do not want accessed by anyone who may come into possession of my computer.  With that in mind, please keep reading....  

Anyway, fast forward to yesterday.  I was looking for a good encryption tool and came across gpg and am giving it a shot.  However, I have some questions that if someone could answer, I would appreciate it.

1.  My main goal is to encrypt certain files / folders (at this point, I am not educated enough in Linux or encryption in general, to attempt to encrypt an entire drive / partition).  Should gpg be my encryption tool of choice, or is there a better alternative for my needs?

2.  When using gpg to encrypt files, apparently gpg creates an archive of the file, and then encrypts the archived file.  But the original file is still accessible and is not encrypted.  Is there a way to have gpg encrypt the original file w/o creating a separate encrypted file?

Again, if there is another tool out there would better serve my needs, please let me know.

Thanks.

---

### Post by jtc on 2007-01-23
> **healthpellets said:**
> 
1.  My main goal is to encrypt certain files / folders (at this point, I am not educated enough in Linux or encryption in general, to attempt to encrypt an entire drive / partition).  Should gpg be my encryption tool of choice, or is there a better alternative for my needs?

GnuPG is an excellent tool if you want to send someone something encrypted, no matter if it's an email or a file. When it comes to protect your own files, especially if you're actively using them, there are better solutions.

If you don't want to encrypt an entire drive, then I'd at least suggest that you use some kind of virtual block device. In its unmounted stage it would simply be a large file of encrypted/meaningless data. When you want to use your private files you simply mount the blockfile, by using a passphrase and/or a keyfile, as if it were a regular partion. Then that mountpoint is where all the encryption and decryption takes place. Files which are being read from the mountpoint are decrypted on the fly, while files written to the mountpoint are encrypted into your blockfile. When you're done working with your private files you unmount the blockfile and the files within are safe / unreachable.

This setup, as with encrypted partion/harddrives, only protect your files while it's unmounted. If you leave your computer powered on, and with your blockfile unmounted, anyone can read the files. Still, it is kind of hard to find any encryption solution without this vulnerability, in any form. After all, to be able to work with your data you need it decrypted.

The big flaw in using a encrypted blockfile, compared to an entire encrypted harddrive is that you still have unencrypted swapspace and temporary files. When you work with a document some of its content can also be found afterwards in above mentioned places.

I guess it, as always, comes down to how bad you need to protect your data and how forcefull a potential thief/opponent is.

If you want to work with encrypted blockfiles I'd recommend [Truecrypt]("http://www.truecrypt.org/"). It uses strong encryption, it is easy to use as well as being available both on Linux and for Windows. If you want you could also use the kernels own dmcrypt, but if your going to use it on blockfiles it requires some extra steps you don't have to worry about in Truecrypt.


> **healthpellets said:**
> 
2.  When using gpg to encrypt files, apparently gpg creates an archive of the file, and then encrypts the archived file.  But the original file is still accessible and is not encrypted.  Is there a way to have gpg encrypt the original file w/o creating a separate encrypted file?

Well, yes, when gpg encrypts a file the encrypted files is a new one, leaving the original file there. That is kind of a logical result of the way file-encryption generally work. If you want to get rid of the originall file, you'll have to erase it by use nonsensedata to overwrite it. A good tool for this purpose is shred. Note that this method isn't always entirely successfull on a journaled filesystem.

---

