---
title: "Permanently delete &quot;Deleted Files&quot; from hard disk."
date: 2011-02-06
forum: Security
---

### Post by iisr on 2011-02-06
How do I erase my hard disk of "Deleted Files"?
I mean how do I make "Deleted Files"-----> "Non Recoverable"?

Thank You.

---

### Post by Jimtheplanner on 2011-02-06
Try Bleach bit from the software centre in the preferences you can set it to "overwrite files to hide contents".

Jim.....

---

### Post by scarey9 on 2011-02-06
I use the secure delete package.
```
sudo apt-get install secure-delete
```You can delete a file by it's self by using the srm command or you can remove an entire directory and sub-directories by using recursive mode. 

for single file (i like to use verbose mode to see what it is doing with the -v option
```
srm -v (path)filename
```for an entire directory and subdirectory use recursive mode (also with verbose option so i can see that it is happening but that is prefrence)
```
srm -rv (path to directory)
```use man to find out more on other options ***warning it can take a while to do lots of files**** it writes over each file 38 times bit by bit.

link to some more info about this topic [http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

---

### Post by rookcifer on 2011-02-06
man shred

---

