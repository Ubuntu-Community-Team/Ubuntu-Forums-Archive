---
title: "Rsync with foreign file names"
date: 2010-04-04
forum: Server Platforms
---

### Post by Buntubailey on 2010-04-04
Hello,

I've just noticed a small problem I am having with my company file server. When making backups to an external NTFS drive weekly I have noticed that the file names with thai characters are not getting backed up. I receive the below error:

rsync: recv_generator: failed to stat (to the file name...)
Invalid or incomplete multibyte or wide character (84)

There are thousands of files on the server that contain thai characters in there names so how do I get around this problem so it will back up all files and not just the English character ones. 

I read somewhere that each file would need to be converted to a different character set but this would take years as there are so many files, is there an easy way around this or am I screwed.

Thanks in advance,

Buntubailey.

---

### Post by HermanAB on 2010-04-04
Hmm, is this a read problem or a write problem?

You could try unison (similar to rsync).

You could make tar balls of directories and back that up.

---

