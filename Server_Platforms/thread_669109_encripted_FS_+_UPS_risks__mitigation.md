---
title: "encripted FS + UPS risks ?? mitigation ?"
date: 2008-01-16
forum: Server Platforms
---

### Post by jcolo on 2008-01-16
Hi,

 I am considering using EncFS to keep a set of tables of MySql out of reach in case of physical break in. The server is powered by a UPS.

My concerns are, what happens when power is cut off and database is running. May I loose / corrupt data ?? and thus loose access to it for ever...:-(. I mean, MySql recovery tools would have any chance ??

The UPS happily connects via RS232 to a windows monitoring program that can shutdown ( in windows ) the system politely.

I am sure that is possible in Linux. Any ideasas to  how is done in Linux, or possible brands and models of UPS that would allow an ordered shutdown once UPS is exhausted ?


Thanks.

JCG

---

### Post by andol on 2008-01-16
If, and I repeat If, you are going to store your MySQL-files encrypted I would say dmcrypt/Luks is the way to go. That is a stable implemenation i Kernelspace. Sure, encfs is a rather charmy solution, but somehow it doesn't feel the same. After all, you are root on the server, right?

Without giving you any odds in this specific case there is always a larger risk of dataloss if you encrypt your data. Encrypted data should be even more rigorously backed up than mere unencrypted data.

Without being an expert in the field I somehow connect file- and diskencryption with protection laptops and maybe workstations. When it comes to servers I associate them more with extra physical security.

In the end thought, only you can do the analysis. What threats does your data face? What would be most expensive; you losing it or someone else getting their hands on it?

---

### Post by HermanAB on 2008-01-16
I second dmcrypt.  That is pretty much the Linux standard now.

Note that you have to use Ext3 on that.  Do not use any other file system, since a single bit error can corrupt the whole thing.  With Ext3, there is a chance of reading some of the data if there is a corruption.

Cheers,

Herman

---

