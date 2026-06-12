---
title: "Archiving very large directory structures with API access"
date: 2012-05-25
forum: Server Platforms
---

### Post by pzs on 2012-05-25
This probably isn't the right forum. If somebody can suggest somewhere better, please do so.

I want to archive very large directory structures for tape backup and restore purposes. Currently we do this with tar and gzip. Each directory is around 300GB as a tgz archive. We have software that operates on these directory structures (sometimes several at once) in their unpacked form. We have to create around 5-10 of these archives per day (this is a bioinformatics application, in case anybody is wondering).

One disadvantage of these huge tar archives is that they take a long time to pack and unpack - about 24 hours each way - and you cannot access a file within the archive without unzipping the whole thing. We are looking for a replacement system where we can read specific files directly from the archive. This would mean that once an archive is created, we never need to unpack it. We could alter the software we use to read files directly from these archives. This would make the archive the primary data, so we'd have one file instead of a huge unwieldy directory structure, which would be very convenient

Windows zip has this random-access within the file feature, but we've found it unreliable on these huge archives. We've also considered dar:

[http://dar.linux.free.fr/](http://dar.linux.free.fr/)

but the documentation is pretty poor and it's not very standard. I can't immediately see from the dar API documentation how you read a file from within the archive.

Another option is writing into a big ISO file, which is standard but again, how it will cope with such huge data volumes?

Does anybody have any expertise about these matters? Advice very gratefully received.

---

### Post by poolet on 2012-05-25
> **pzs said:**
> This probably isn't the right forum. If somebody can suggest somewhere better, please do so.

I want to archive very large directory structures for tape backup and restore purposes. Currently we do this with tar and gzip. Each directory is around 300GB as a tgz archive. We have software that operates on these directory structures (sometimes several at once) in their unpacked form. We have to create around 5-10 of these archives per day (this is a bioinformatics application, in case anybody is wondering).

One disadvantage of these huge tar archives is that they take a long time to pack and unpack - about 24 hours each way - and you cannot access a file within the archive without unzipping the whole thing. We are looking for a replacement system where we can read specific files directly from the archive. This would mean that once an archive is created, we never need to unpack it. We could alter the software we use to read files directly from these archives. This would make the archive the primary data, so we'd have one file instead of a huge unwieldy directory structure, which would be very convenient

Windows zip has this random-access within the file feature, but we've found it unreliable on these huge archives. We've also considered dar:

[http://dar.linux.free.fr/](http://dar.linux.free.fr/)

but the documentation is pretty poor and it's not very standard. I can't immediately see from the dar API documentation how you read a file from within the archive.

Another option is writing into a big ISO file, which is standard but again, how it will cope with such huge data volumes?

Does anybody have any expertise about these matters? Advice very gratefully received.


Hello, 

**First** you need to focus into your target... What the real purpose of zipping such a big files?? 

**Second:** Do you know that all file have MD5 hash ?? So zip files can easily  corrupted during the compression ??  Even if the compression success you don't know if the files of zip are good or not.. Sometimes corrupted for such a big files...!!  

**Third:** Since you want a backup for such a big files why u don't used  something like NAT-T or NAS? 

**Forth:** If you want to read the files from zips, Unfortunately, I have never heard about any program that can do that without unpacked.. Even if you focus into a specific file, the program it will unpacked (sometimes first the program that you select) and then it will continue with others... Still you will not able to see the specific file before the unpacking...

**At the end::** The best solution for your problem is to build or buy a NAT-T or NAS, set your requirement on that, end then set any computer that you want to have access on NAT-T to backup (read & write) your file, the bad thing is that it will take time especially if you will used an external network, if your network is internal and your files will backup as locally(on localhost) you will have a progress of 2-3GB's per second always depends on your NAT-T interfaces mbps and your computer interfaces..!!

Hope that helps you..!!

---

