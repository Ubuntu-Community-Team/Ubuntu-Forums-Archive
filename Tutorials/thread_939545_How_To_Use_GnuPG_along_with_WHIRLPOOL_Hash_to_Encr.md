---
title: "How To: Use GnuPG along with WHIRLPOOL Hash to Encrypt an Individual File"
date: 2008-10-06
forum: Tutorials
---

### Post by kevdog on 2008-10-06
**[SIZE="4"]Introduction[/SIZE]**

A question often arises in this forum about how to best encrypt an individual file, group of files, directory tree, partition, or entire system.  Although not likely applicable to more than an individual file or collection of files********, GnuPG ([_http://www.gnupg.org/_]("http://www.gnupg.org/")) offers a very secure way to symmetrically encrypt a file that is password protected.  Although it is possible for asymmetric encryption to be used in conjunction with GnuPG (a method whereby one key encrypts the file, and another decrypts the file), this method is sometimes impractical and cumbersome depending on the situation.  Additionally, use of GnuPG represents a method of file encryption that is truly cross-platform compatible.  Since GnuPG is available on Linux, MAC, and Windows, it is possible to encrypt a file on one platform and decrypt the file utilizing a totally different operating system type.  This makes use of GnuPG very advantageous when sharing files across multiple operating architecture types. 

The downside of using any symmetric encryption method is the simplicity of the password used to protect the encrypted data.  Often complex passphrases that provide additional security are hard to remember and are very cumbersome to type.  Use of hash digests as an alternative to short passphrases, produce very long outputs that can in turn be used as passphrases.  Use of a hash algorithm such as WHIRLPOOL which always produces a 128-digit hash digest, allows the user to turn any passphrase into a 128-digit passphrase to provide additional security benefits.  Because the 128-digit output is hexidecimal, it is not prone to dictionary attack.   

[B][SIZE="4"]
GnuPG -- the --symmetric Option[/SIZE][/B]

Use of Gnupg along with the --symmetric flag makes it possible to encrypt and password protect a file.  The same password is used to decrypt the file.  The process of using the same password for encryption and decryption is known as a symmetrical encryption process.


All the ciphers that are normally available in Gnupg can be used to encrypt your file.  Because additional cipher types are included periodically with each new release of Gnupg, its first important to discover the ciphers available with the currently installed version.  Using my own installation as an example, discovery of the ciphers included in within GnuPG can be accomplished via:

```
$ gpg -v --version
gpg (GnuPG) 1.4.10-svn4847
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: IDEA (S1), 3DES (S2), CAST5 (S3), BLOWFISH (S4), AES (S7), AES192 (S8), AES256 (S9), TWOFISH (S10), CAMELLIA128 (S11), CAMELLIA192 (S12),CAMELLIA256 (S13)
Hash: MD5 (H1), SHA1 (H2), RIPEMD160 (H3), SHA256 (H8), SHA384 (H9), SHA512 (H10), SHA224 (H11)
Compression: Uncompressed (Z0), ZIP (Z1), ZLIB (Z2), BZIP2 (Z3)
```

Any algorithm listed under the Cipher heading is
available for the encryption method.  I usually prefer AES256 in all cases, however other methods might be applicable given the situation.  (Personal Recommendation: Avoid CAST5).

The basics of how to symmetrically encrypt a file are:
```

gpg --symmetric --cipher-algo <CIPHER_ALGO> <filename>
```

An example with the file named ENCRYPT.txt would be
```

gpg --symmetric --cipher-algo AES256 ENCRYPT.txt
```

This would produce a file name ENCRYPT.txt.gpg

This is going to produce a binary file that is unreadable.  If for some reason you would like to make an ASCII file, that you could actually include in-line in an email, then you would include the --armor flag (Something like this):

```
gpg --symmetric --cipher-algo AES256 --armor ENCRYPT.txt
```

This will produce a file called ENCRYPT.txt.asc

During either of the two above options, you will be prompted to enter the passphrase, and then re-enter it for confirmation.

In either case if you want to decrypt the file:

```
gpg -d ENCRYPT.txt.gpg
gpg -d ENCRYPT.txt.asc
```

If you need to save the results to a file, then it would be like this:

```
gpg -d ENCRYPT.txt.gpg > ENCRYPT.txt
gpg -d ENCRYPT.txt.asc > ENCRYPT.txt
```

You will be prompted for the passphrase during the decryption process. If you need verbose output, use the -v flag in addition.

[B][SIZE="4"]
Using a Hash Digest to Improve Password Strength[/SIZE][/B]

Although the method described above is very reasonable, its weakness centers around the strength of the password. Passphrase choice is the weak link in all modern symmetrical encryption methods (Modern day ciphers for the most part are currently considered unbreakable).

One way to improve on this method would be to use a really strong passphrase.  Again there are general rules of thumbs about how to accomplish this, however the stronger the passphrase -- the more burden it carries.  With longer passwords with unique symbols and letters, it is often very difficult to remember, and it very laborious to enter during the encryption/decryption process.  A different method around this cumbersomeness would be to utilize hashes as passwords since hashes usually result in very long text/number outputs (although it doesn't totally solve the problem entirely).  

If you are not familiar with Hash Algorithms, they are one way algorithms for converting a large set of data into a smaller subset.  This conversion is a one-way process -- meaning that its not possible to take the hash product and reproduce the original data.  Theoretically, no two input sets of data can reproduce the same hash product, however in real world cases, this rule is not always true.  The case where two unique sets of data that produce the same hash product is known as a collision.  The strength of a hash algorithm is graded on its "collision-free" ability, or the probability of the occurrence of producing a collision.    

Ubuntu stores hash products as passphrases associated with the User Logon process to provide additional security.  Using the same methodology, a hash digest of an individual password or file could be used to generate the passphrase for the encryption process.  Although use of an individual file removes the burden of remembering passwords, it does introduce the need to have a copy of the file available.  It would theoretically also be possible to hash the hash product multiple times to further provide additional security.  Again this process would take calculate the hash of a password or file additionally, and then recursively recalculate the hash of the resultant hash product. Examples are included below.

In comparison to Encryption Algorithms, Hash Algorithms are relatively dated.  Hash Algorithms used in most products are either members of the SHA family (SHA-1, SHA256, SHA512 (or variants like SHA-224, SHA-384)), MD5, or RIPEMD160.  In fact all the hash algorithms used within GnuPG or PGP fall within these 3 categories.

The newest algorithm currently creating the newest "buzz" within the cryptography world is known as WHIRLPOOL.  WHIRLPOOL generates a 512-bit hash product -- similar to SHA512, however its distinctly different than the SHA family.  Weakness within the SHA-1 algorithm, have led many to seek different hash algorithms.  At the current time however, this debate remains unsettled.  Using the Whirlpool hash, 128-digit hexadecimal number is produced, equating to a 128-digit password.  Hence utilizing this method, even a simple passphrase such as "Password", can be turned into a 128-digit passphrase:

```
$ echo "Password" | whirlpooldeep
456b2bbf1ebd860aa5751d7c017ad652529de5cbb03259d3334acd97a17c95481be545ea9675c6cb60ab86a6a399123ef34fe0a62b812722bbaa6d36f013511b

```

To take advantage of the WHIRLPOOL Hash, a program known as md5deep can be utilized: [_http://md5deep.sourceforge.net_]("http://md5deep.sourceforge.net/")  This program is available for both linux and windows architectures (as is GnuPG -- cross-platform compatible).  Despite the name of the product, its capable of calculating md5, sha1,sha256, tiger192 and Whirlpool hash digests.  An alternative to this program would be the OpenSSL product ([_http://www.openssl.org/_]("http://www.openssl.org/")) included in all base Ubuntu installations, however within the current 0.9.8 release tree, no current version can calculate WHIRLPOOL are TIGER hashes. md5deep was written by a programmer turned cryptographer for the US NAVY - [_http://en.wikipedia.org/wiki/Md5deep_]("http://en.wikipedia.org/wiki/Md5deep").  Because it was released by the US Government, it is not subject to any patent or copyright restrictions.

md5deep can either be installed as a binary on a windows platform, or compiled/installed from source if using cygwin from within windows or any linux distributions: _[http://md5deep.sourceforge.net/#download](http://md5deep.sourceforge.net/#download)_
Additionally if on ubuntu, installation without compilation can be accomplished utilizing the apt system with one of the following two commands:

```
sudo aptitude install md5deep
sudo apt-get install md5deep
```

[B][SIZE="4"]
Examples of Using GnuPG encryption with a Whirlpool Hash as a Passphrase[/SIZE][/B] 
 
These examples assume the md5deep package has been included which includes the whirlpooldeep executable.

Lets assume there exists two files:

ENCRYPT.txt <--- The file I want to Encrypt
Hash.txt <----  The passphrase file or file I will calculate the
WHIRLPOOL hash from and use the hash as the password.

Assuming an ascii armored file output:
```

whirlpooldeep -q Hash.txt | gpg --symmetric --armor --cipher-algo
AES256 --passphrase-fd 0 ENCRYPT.txt
```

This would of course produce a file name ENCRYPT.txt.asc.  To decrypt:

```
whirlpooldeep -q Hash.txt | gpg -v -d --passphrase-fd 0 ENCRYPT.txt.asc
```

To save the output to file rather than having it output to the screen:

```
whirlpooldeep -q Hash.txt | gpg -v -d --passphrase-fd 0
ENCRYPT.txt.asc > ENCRYPT.txt

```

To use a multiply hashed file hash as a passphrase:

```
whirlpooldeep -q Hash.txt | whirlpooldeep | whirlpooldeep | gpg --symmetric --armor --cipher-algo AES256 --passphrase-fd 0 ENCRYPT.txt
```

To decrypt:

```
whirlpooldeep -q Hash.txt | whirlpooldeep | whirlpooldeep | gpg -v -d --passphrase-fd 0 ENCRYPT.txt.asc
```

A plain vanilla password could also be hashed three times and used as the gpg passphrase:

```
echo <password> | whirlpooldeep | whirlpooldeep | whirlpooldeep | gpg --symmetric --armor --cipher-algo AES256 --passphrase-fd 0 ENCRYPT.txt
```

And to decrypt:

```
echo <password> | whirlpooldeep | whirlpooldeep | whirlpooldeep | gpg -v -d --passphrase-fd 0 ENCRYPT.txt.asc
```

With hashing repetitively, this may be better accomplished through the use of a custom shell script or bat file depending on the platform.

_____________________________________________
******gpgdir - A Recursive directory encryption with GnuPG - _[http://cipherdyne.org/gpgdir/](http://cipherdyne.org/gpgdir/)_**

---

### Post by Sef on 2008-10-06
moved to tips and tutorials.

---

### Post by Dr Small on 2008-10-06
Thanks for writing this, kevdog. That was a good read. Of course, having the passphrase in a plain text document allows for some insecurity as far as someone obtaining it (they would still have to figure out how to use it), along with echo'ing the password in the terminal has it's disadvantages (unless you turn off histcontrol).

But still, this method sounds appeasing, and I will have to try it sometime soon (and probably write another script to further simplify the process :D) I just wish I was as knowledgeable in cryptography as you ;)

Regards,
Dr Small

---

### Post by kevdog on 2008-10-06
Dr. Small -- maybe you could clarify the history thing for me.  In actuality the passphrase is not stored in the file per se -- since its the file hash that is being used as the passphrase.  The file could even be encrypted -- and then the digest of this encrypted file could be used as the passphrase. In some respects it is security by obscurity.

If uncomfortable with the use of a plain file, a password could simply be used in much the same way.  Truecrypt offers a similar option in that a volume can be encrypted/decrypted via use of a passphrase, a file, or combination.

Possibly you could again help me with the histcontrol off -- that would be great.

---

### Post by 4llf0rn0t on 2011-02-12
Hi,

This could also be used aside from plain text and echo and/or cat..

**fpassphrase.txt.gpg** - gpg encrypted file to be use to get whirlpool hash
ifile.txt - file to be encrypted

First, you encrypt your text file with gpg -c --cipher-algo AES256 fpassphrase.txt.Remember the password for this (1*).

**to encrypt:**
```
gpg - <  fpassphrase.txt.gpg | whirlpooldeep | gpg -c --cipher-algo AES256 --passphrase-fd 0 ifile.txt

Reading passphrase from file descriptor 0 ...gpg: AES256 encrypted data
gpg: gpg-agent is not available in this session
Enter passphrase: Use the password from (1*)

```

**to decrypt:**
```
gpg - < fpassphrase.txt.gpg | whirlpooldeep | gpg --passphrase-fd 0 ifile.txt.gpg
Reading passphrase from file descriptor 0 ...gpg: AES256 encrypted data
gpg: gpg-agent is not available in this session
Enter passphrase: Use the password from (1*)

```

---

### Post by kevdog on 2011-02-19
Good example 4llf0rn0t.  I'm liking your approach.

---

### Post by reg360 on 2011-11-14
Hi all

I'm trying to complete some perpetually-work-in-progress blogspot posts, and I came across kevdog's great tutorial! Which I discovered, um, 3 years after it was written? :) So I'm registering specifically to contribute here.

For my own specific purpose of scrambling passwords, here's the essence of what I've been using for quite a while now:
```
openssl dgst -whirlpool
```
or to satisfy the usual "uppercase/lowercase/numbers" requirement:
```
echo -n "somepassphrase" | openssl dgst -whirlpool | base64 -w0
```

> along with echo'ing the password in the terminal has it's disadvantages (unless you turn off histcontrol)
Dr Small, yeah I worried about that too, so I researched how other folks temporarily disabled it.

> An alternative to this program would be the OpenSSL product

Actually I **had** started using Jesse Kornblum's [md5deep]("http://md5deep.sourceforge.net/") implementation because of the very situation kevdog presented. Back then, the openssl version on my system didn't have the whirlpool algorithm.

```
currstty=`stty -g` && stty -echo && whirlpooldeep | base64 -w0 | xclip -selection clipboard && stty $currstty
```

This turns off echoing Standard Input (take that, TEMPEST!), Whirlpools it, converts to UpperLowerNumbers, copies to the clipboard, then turns echoing back on. You could even add in the "cut" function to just keep a smaller amount of characters, further obfuscating things.

thanks
reg360

---

