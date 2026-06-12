---
title: "Automatic Folder Copy/tar under Ubuntu Server 10.10"
date: 2011-05-26
forum: Server Platforms
---

### Post by CGW on 2011-05-26
Hello:

I've searched and found some similar threads, but nothing 100% so here goes...

First off I'm running a headless Ubuntu server 10.10 box.

I have a single folder on a ntfs drive that I wish to copy somewhere else on the same HD.  I'd like this to automatically happen about once a week or so.  It would be even better if it would tarball the copy also..but this isn't a 100% necessary.

Something like "XFOLDER" would be copied to "/backup/XFOLDER1.tar" then next time "/backup/XFOLDER2.tar" and so on.

I know similar questions like this have been asked so please bear with me.

Thanks in advance.

Chris

---

### Post by CGW on 2011-05-26
Alright, I believe I may have figured it out own my own.  I created a weekly cron job with this command:

```
tar -cf /data/hbr_backup/hbr-$(date --iso).tar /data/hbr/*
```

I test ran it and all seems well.  Anything here jump out to anyone as far it running longterm?

Thanks

---

