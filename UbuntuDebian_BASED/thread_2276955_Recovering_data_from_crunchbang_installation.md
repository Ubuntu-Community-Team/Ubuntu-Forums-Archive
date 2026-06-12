---
title: "Recovering data from crunchbang installation"
date: 2015-05-06
forum: Ubuntu/Debian BASED
---

### Post by dinkobicakcic on 2015-05-06
Hello.

I was given a notebook from a co-worker to diagnose / evaluate it and apparently to pull data from it.

The laptop reports smart failure and it's a crunchbang distribution 3.2 I think.  I did not obtain password so I hooked up the hard disk via enclosure to my Ubuntu installation.

I was able to see home folder with the user "tom" but there is no data in any of the folders but also I did not see desktop folder where most of the users will generally save data.

Well now the crunchbang will not boot as fsck has to be ran.

Now, considering that I have had it attached to my Ubuntu install is there likelyhood that I would have seen all the data that was there, or I was not able to see the data because of permissions (nothing in documents, downloads, etc, but no desktop folder also).

The boot now stops at root@tom on original notebook - is there a way to access files from just command line or at least see contents?

Thanks

---

### Post by nerdtron on 2015-05-06
> Now, considering that I have had it attached to my Ubuntu install is  there likelyhood that I would have seen all the data that was there, or I  was not able to see the data because of permissions (nothing in  documents, downloads, etc, but no desktop folder also). 

Considering the hard drive still mounts on Ubuntu, you'll most likely restricted by permission issue when you view the other hard drive folder when you are in Ubuntu, so you can launch nautilus to root mode and view/copy all the files you want.

```
 gksudo nautilus 
```
or 
```
gksu nautilus 
```

---

### Post by dinkobicakcic on 2015-05-06
Thanks, I was able to do that, and also reset passwords for both root and tom user eventually after fsck ran.  Well even after all that I get is  gray desktop with computer stats in the upper right corner and that's it.

All I can do is rightclick and run program, o-clock, Xterm and couple of other apps.  Nothing else is working.  It looks like the only office app that was there was abiword.  I used Testdisk and couldn't find any data to be recovered also.  My last option might be RAW recovery with ontrack easy recovery, tough I doubt I will find anything that way also.

Big thanks nonetheless.

---

### Post by Bucky Ball on 2015-05-06
*Thread moved to **Ubuntu/Debian BASED**.*

---

