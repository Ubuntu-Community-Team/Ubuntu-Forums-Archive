---
title: "ext3 filesystem limits"
date: 2005-12-06
forum: Server Platforms
---

### Post by mhirons on 2005-12-06
I am looking for information regarding the limits of the ext3 filesystem.  I've searched for quite awhile and haven't found anything definitive.

How many files can there be in one directory?
How many files total can there be across all directories?
How many directories can there be?
How many subdirectories can there be in a directory?
Is there any way to get around the 2GB filesize limitation?

Thanks for you help.

---

### Post by dudus on 2005-12-06
[QUOTE=mhirons]I am looking for information regarding the limits of the ext3 filesystem.  I've searched for quite awhile and haven't found anything definitive.

How many files can there be in one directory?
How many files total can there be across all directories?
How many directories can there be?
How many subdirectories can there be in a directory?
Is there any way to get around the 2GB filesize limitation?

Thanks for you help.[/QUOTE]

EXT3 does not limit file sizes by 2GB. In fact the max file size is 2TB or 2000GB.

The files have a limit of 255 bytes for names.

And the total volume has a limit of 32TB or 32000GB.

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by mhirons on 2005-12-06
Thanks for the 2GB filesize correction and the excellent link!  Gotta love wikipedia!  Why didn't I try that first?  :-)

Eventually, I could have several million pictures in one or more directories.  It sounds like I won't have anything to worry about in terms of limits, though.

---

