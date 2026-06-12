---
title: "which is the most secure archive encryption"
date: 2013-11-29
forum: Security
---

### Post by sam_baker2 on 2013-11-29
Hi,
There are many compression formats to choose from when using the archiver,
I was wondering which is best for password protection?
There is zip ( my favorite ), tar, ar, jar, gz, etc, etc, etc, etc.
Also, I have read that a hash of <= 8 characters ( all random,
lc, uc, nums and misc character set ) can be cracked in
less than a day just using a standard home pc using the graphics card.

---

### Post by varunendra on 2013-12-01
As far as I know, not all of the listed formats allow password encryption of the archive. Also, of the ones you listed (apart from "etc, etc, etc," ;)), only zip format allows encryption.

My personal favourite is 7zip (.7z) format which not only has the best compression ratio, but is also free, allows for password encryption and gets integrated with File Roller - the default GUI archive manager of Ubuntu. The only drawback (for which there are easy workarounds) is that it can't preserve Linux file permissions. The recommended workaround is to use 'tar' first to archive the files, then compress the .tar file with 7z.

For encryption, the "**AES-256**" algorithm provides arguably the strongest encryption against cracking, and this is exactly what 7z format uses. But regardless of the encryption strength, it is highly recommended to use at least 9-characters long, random passwords containing alphabets (both lower and UPPER case letters), numbers and special characters. It should not be easy to guess for others, because most of the passwords are broken by guessing, not cracking.

For best practices, just read about encryption and password security on the net. What I suggested is just my personal choice and opinion.

---

### Post by sam_baker2 on 2013-12-02
I had tried earlier to archive using 7z, but I noticed that there was no password option.
I installed 7zip, as you mentioned, and now I can. I think I will use it as I am not
 concerned about the permissions on these files.
~thanks~

---

### Post by varunendra on 2013-12-03
You're welcome ! :)

The man page of 7z command (man 7z) provides a very limited information about its (commandline) usage. Its extensive usage has been given in its html documentation whose index page is "/usr/share/doc/p7zip-full/DOCS/MANUAL/index.htm" file. The linked pages (all offline documents within "/usr/share/doc/p7zip-full/DOCS/MANUAL/" directory) provide a very detailed information about its usage and available options/switches etc with examples, which is almost essential if you are fond of its commandline usage and/or want to use its full power with maximum flexibility.

---

