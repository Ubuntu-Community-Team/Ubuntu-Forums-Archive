---
title: "Set password for file?"
date: 2011-04-12
forum: Security
---

### Post by deegaf on 2011-04-12
How do I set a password for a file or folder? By that I mean my own password for the file because I share a computer and im not the admin. Im sorry if my explanation isn't well enough, im in a hurry.  Thanks to whoever has time to answer this. :)

---

### Post by bodhi.zazen on 2011-04-12
use encryption, gpg is one option, and a good one if you can not install applications.

---

### Post by Paddy Landau on 2011-04-13
A few ideas depending on how secure you need the file and how simple you want it to be.


[LIST]
[*]**Permissions:** You could simply change the permissions on the file to read-write for you only (right-click in Nautilus > Properties > Permissions). However, that would not stop an admin from seeing the file.

[I]**Pro:** Very simple.
** Con:** Any admin can see your file.[/I]
[/LIST]


[LIST]
[*]**TrueCrypt:** If you cannot install programs, you can [download TrueCrypt]("http://www.truecrypt.org/downloads"). Choose the "Console-only" option. You can place it in a directory of your choice; probably ~/bin. You will have to use the console, i.e. command line (CLI) in order to use it. (If you want the GUI, you'll have to ask your admin to install the full program.) **Beware:** If you forget your passphrase, the file will be unrecoverable unless it is a short passphrase.

[I]**Pros:** Very high grade encryption; uncrackable with today's computers if you use a proper passphrase; read the [TrueCrypt manual]("http://www.truecrypt.org/docs/") for advice. Cross-platform (you can recover the file on Windows, Mac and Linux).
** Cons:** You need the CLI, unless you can persuade your admin to install the full TrueCrypt program. You cannot use the full "container" option (an encrypted pseudo disk) without admin privileges.[/I]
[/LIST]


[LIST]
[*]** GPG:** The suggestion from bodhi.zazen is also a good one, because you don't have to download any program. First, make your own personal key (Accessories > Password and Encryption Keys). Then you'll have to use the CLI to use GPG. **Beware:** If you lose your encryption key (e.g. the computer hard drive crashes and you don't have a backup), your file will be unrecoverable. That's why I'd prefer TrueCrypt.

[I]**Pro:** As with TrueCrypt, very high grade encryption.
** Cons:** You need the CLI. You need to back up your keys. Cross-platform, but with difficulty.[/I]
[/LIST]


[LIST]
[*]**Compression:** Right-click the file and select Compress. Choose compression option .zip. Select Other Options. Type a password. This will compress and encrypt your file. You have to delete the original file after encrypting. **Beware:** If you forget your passphrase, the file will be unrecoverable unless it is a short passphrase.

[I]**Pros:** Good enough encryption for everyday use. Very easy to use. Cross-platform.
[/I]
[/LIST]

---

### Post by rookcifer on 2011-04-13
> **Paddy Landau said:**
> 
[*]** GPG:** The suggestion from bodhi.zazen is also a good one, because you don't have to download any program. First, make your own personal key (Accessories > Password and Encryption Keys). Then you'll have to use the CLI to use GPG. **Beware:** If you lose your encryption key (e.g. the computer hard drive crashes and you don't have a backup), your file will be unrecoverable. That's why I'd prefer TrueCrypt.

[I]**Pro:** As with TrueCrypt, very high grade encryption.
** Cons:** You need the CLI. You need to back up your keys. Cross-platform, but with difficulty.


You don't need to create a key-pair in order to encrypt with GPG.  All you have to do is:

```
gpg -c file
```

Then enter the password and it will encrypt it symmetrically.  This is probably the easiest way of encrypting individual files on Ubuntu.  Of course, as you said, you will need to make sure the original file has been removed/overwritten, etc.


> 
[*]**Compression:** Right-click the file and select Compress. Choose compression option .zip. Select Other Options. Type a password. This will compress and encrypt your file. You have to delete the original file after encrypting. **Beware:** If you forget your passphrase, the file will be unrecoverable unless it is a short passphrase.

[I]**Pros:** Good enough encryption for everyday use. Very easy to use. Cross-platform.
[/I]


Didn't realize this was available.  I toyed around with it and noticed it only seems to offer the encryption option with the .zip format.  This would be a good alternative to the above GPG method.

---

### Post by Paddy Landau on 2011-04-13
> **rookcifer said:**
> You don't need to create a key-pair in order to encrypt with GPG.
Thank you, I had not realised that. If the OP sticks with Linux, that will make an excellent alternative.

> **rookcifer said:**
>  I toyed around with it and noticed it only seems to offer the encryption option with the .zip format.
I also get it with .exe (I believe this is a Windows variant of zip), .cbz and .7z.

---

### Post by hyperAura on 2011-04-13
Hey guys, I was wondering if gpg also does some kind of compression.

Which is the fastest method? gpg or compression?

Can the gpg be applied on folders or only files?

---

### Post by bodhi.zazen on 2011-04-13
just files, or you could encrypt the entire archive (.tar or .zip).

If you need directories, I suggest cryptkeeper, it is in the repositories.

---

### Post by Enigmapond on 2011-04-13
I use TrueCrypt, Very easy to use & high lever encryption. Just create an encrypted container and put all you goodies in it. It's cross-platform and can be used on a USB.

---

### Post by Paddy Landau on 2011-04-14
> **hyperAura said:**
> Hey guys, I was wondering if gpg also does some kind of compression.

Which is the fastest method? gpg or compression?

Can the gpg be applied on folders or only files?
Encryption usually also encrypts on-the-fly, as it increases the difficulty of breaking the code. If all you want is compression, use specialised compression tools such as bzip2 or, for cross-platform portability, zip.

You can compress from Nautilus. For a single file, use .bz2 or .zip. For a folder, use .tar.bz2 or .zip.

> **Enigmapond said:**
> I use TrueCrypt, Very easy to use & high lever encryption. Just create an encrypted container and put all you goodies in it. It's cross-platform and can be used on a USB.
The OP is not an administrator, and you need admin privileges to use a container with TrueCrypt. I don't understand why.

---

### Post by deegaf on 2011-07-09
Thanks for the help everyone! :)

---

