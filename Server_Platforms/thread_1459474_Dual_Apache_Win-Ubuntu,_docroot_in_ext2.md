---
title: "Dual Apache Win-Ubuntu, docroot in ext2 ?"
date: 2010-04-21
forum: Server Platforms
---

### Post by Rallg on 2010-04-21
I have a dual boot machine (XP and Ubuntu 9.10 desktop, to be upgraded to 10.04 soon). Both sides have Apache, PHP5, and Perl properly configured. I also have MySQL but do not use it, so that doesn't matter. I only use Apache to pre-test files before uploading them to my web host.

My localhost document root is copied both to my Ubuntu home folder, and to a suitable folder in Windows. I do this because my web host is configured very similarly to the way I have Apache and PHP on Ubuntu, but I also wish to look at stuff in Windows browsers before it goes live. Other than server logs, I don't need to write files via Apache.

It's my understanding that Apache on Linux (any Linux) doesn't like to have a document root sitting in a Windows (or FAT32) folder, due to file permission issues. But what about the other way around? I have IFS installed in Windows. This allows me to mount my Ubuntu ext2 partition as if it were a Windows volume, and read-write from Windows.

I am thinking of having my Apache on Windows use the document root that sits in Ubuntu. Before I try it, is there anyone else who has tried it, and can share the experience? That is, did Ubuntu complain if Apache-Windows had been using its documents?

---

