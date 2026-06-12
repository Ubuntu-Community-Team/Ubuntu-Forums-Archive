---
title: "Fastest archive directory read extract method"
date: 2021-02-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Alistair George on 2021-02-28
Greetings I have backup directorys with large files already compressed, videos, backups and so on. Objective to compress where needed, compression size not an issue, required for being able to move a single archive between drives.

Perhaps TAR alone would be the best method? but due to the high volume of compressible files, I prefer some compression.

I thought lz should be most flexible for this eg: sudo tar --ignore-failed-read -cf - backintime | lz4c > ext4_backups_backintime.tar.lz

However, when going to read such a large resulting archive, it takes ages to get a directory showing (eg on a 100Gb archive), and to extract a file is very slow.

Google gives me no relevant result for 'fastest archive extraction method'.

Question is: recommended archive for fastest show directory structure within archive and access/extract file(s) fastest?

Thanks kindly, Al.

---

### Post by TheFu on 2021-02-28
Archive files over 10G aren't recommended.  100G is archive abuse.  ;)

Use **ls -Rl** into a text file if you want to keep a single file directory of all the files from ./ down.  Or you can use **find . -ls -print > everything.list** for the same purpose, if you want more details.

BTW, back-in-time uses hardlinks to drastically reduce the size of backups.  If your copy/mirror/archive tool doesn't recognize and handle hard links, perhaps a better solution is needed?  Perhaps a backup tool that doesn't use hardlinks?

---

