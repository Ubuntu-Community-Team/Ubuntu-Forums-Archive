---
title: "installing xamp problem"
date: 2009-07-11
forum: Server Platforms
---

### Post by kxhitiz on 2009-07-11
I downloaded xamp which is tar.gz format and according to the instruction i read i tried to extract it with following code in terminal
> tar xvfz xampp-linux-1.7.1.tar.gz -c /optbut error occurs which says
> tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.Now please tell me guys what should I do?

---

### Post by rylFlush on 2009-07-15
I think you need a capital "C" not lower case on this cmd line.

You can cut and paste into terminal. Paste is Ctrl+Shift+V.

Hope this helps.

---

### Post by Tux.Ice on 2009-07-15
try:

```
tar xfz <file>
``` 

instead of

```
tar xfcz <file>
```

---

### Post by kxhitiz on 2009-07-16
now this time I did this according to u guys reply to my thread  > tar xfz xampp-linux-1.7.1.tar.gz -C /opt 
and it still gave the error
> tar: /opt: Cannot chdir: Not a directory
tar: Error is not recoverable: exiting now


please help me.

---

### Post by Tux.Ice on 2009-07-17
Stop adding the -C !!!!

---

### Post by kxhitiz on 2009-07-18
Finally my xamp started. When i typed localhost after starting xampp, it worked but when i went to phpmyadmin the following error occured > Wrong permissions on configuration file, should not be world writable!.
Guys do you have any idea about this?

---

### Post by enz1m3 on 2009-07-19
The configuration file (and probably more files and directories) have chmod 777, you should change them to chmod 755.

If you don't know how to change permissions, simply go to the directory you need:

<code>cd whatever/directory/</code>

And then assign the permissions to all files and directories recursively (if you don't want it recursively, remove the -R):

<code>sudo chmod -R 755 ./*</code>

---

