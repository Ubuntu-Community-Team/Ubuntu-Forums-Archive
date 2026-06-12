---
title: "FTP file probelm"
date: 2011-10-20
forum: Server Platforms
---

### Post by AnuragSatish on 2011-10-20
Hi,

I have written a perl program to ftp the files in archive format of either tar.gz of tar.tgz.
After ftp is done i have downloaded back the ftp tar file.But I am unable to open it and the error shown to me is below:

```
An error occurred while loading the archive.

- Command Line Output

tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
```

---

### Post by tors on 2011-10-20
Are you using binary transfer mode when ftp:ing the files?

---

### Post by Lars Noodén on 2011-10-20
Can you say a little more about what your program is supposed to do?  That might give more clue as to the cause of the error.  Also, there might be other tools, say [curl](http://curl.haxx.se/), that might already do the same thing.

---

### Post by tors on 2011-10-24
Did you manage to solve the problem?

---

