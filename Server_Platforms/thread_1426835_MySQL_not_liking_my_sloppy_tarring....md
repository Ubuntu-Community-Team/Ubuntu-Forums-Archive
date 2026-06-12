---
title: "MySQL not liking my sloppy tarring..."
date: 2010-03-10
forum: Server Platforms
---

### Post by Kareeser on 2010-03-10
In backing up my server, I back up my databases with *mysqldump*. I save that file in /tmp, tar it (w/ gzip), and move it to the backup storage.

However, while phpmyadmin handles .tar.gz, it doesn't like my file, since the .sql file isn't in the root directory of the archive.

That is... when I run *tar*, it saves the entire directory structure leading up to the file... which is what it's supposed to do.

If I want to import my database back, I need to untar it first, which I don't mind, but I was wondering if there was a way around having to do so...

There has to be, since precompiled software untars right to the current directory...!

---

### Post by r-senior on 2010-03-10
There's an option you can pass to tar to get it to change to a directory for the context of the archive:

```
-C, --directory DIR
           change to directory DIR
```

See manual page for tar.

So, I believe something like this would leave the .sql file in the root:

$ tar -C /tmp -czf myArchive.tar.gz myFile.sql

---

### Post by Kareeser on 2010-03-10
Perfect... I knew about -C, but I had no clue where to use it, since anywhere I put it, it didn't do diddly-squat...

Before "czf"... I see...

---

### Post by DaithiF on 2010-03-11
or you could have just cd'ed to the /tmp directory before running your tar command, in which case the tar archives files would be relative to that directory
```
$ cd /tmp
$ tar czf somefile.tgz somefile
$ tar tzf somefile.tgz
somefile
```

---

