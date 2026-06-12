---
title: "Copy/Verify Large Number of Files"
date: 2009-02-13
forum: Server Platforms
---

### Post by thornomad on 2009-02-13
Hi - am looking for some guidance ... recently setup a new file server and I was getting ready to transfer the files from the old server to the new one ... but then I go to thinking:

Should I just use cp -R ?  Or, is there a better way to copy a large number of files and verify their integrity ?

I plan to copy the files from the external hard drive backup (eSATA) so it should be fast; but there are a *lot* of files and I want to make sure I get them all right.

Thanks,
Damon

---

### Post by HermanAB on 2009-02-13
Rsync is your friend.

Read the man page, it is very easy to use.

Cheers,

Herman

---

### Post by thornomad on 2009-02-13
> **HermanAB said:**
> Rsync is your friend.

Yea - I had thought about that.  The backups are created using rsync (with --link-dest for hard links) ... so, am familiar with it.  I can give that a go -- thanks for the advice.

---

