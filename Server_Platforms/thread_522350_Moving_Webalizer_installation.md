---
title: "Moving Webalizer installation"
date: 2007-08-10
forum: Server Platforms
---

### Post by Enigmatic on 2007-08-10
I'm having some trouble moving my webalizer installations.

I had copied the directory of output stats over to the new host. Made sure it was outputting a separate logfile for the website. Changed paths in webalizer.conf.

However, whenever I run webalizer -c /pathtowebalizer.conf/ it finds new records but does not update! I can confirm that there are log entries for it to process.

For instance:

Reading history file... webalizer.hist
Reading previous run data.. webalizer.current
1155 records (1155 ignored) in 0.01 seconds

---

### Post by Enigmatic on 2007-08-11
Figured it out, just wait a day past the last day covered in the records and then an incremental update works, strange as that may sound.

---

