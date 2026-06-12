---
title: "Count Files in C code and break when more than X nodes"
date: 2017-05-12
forum: Ubuntu Dev Link Forum
---

### Post by tgkprog on 2017-05-12
We sometimes have directories with more than 800,000 files. Is there a command or way to read the the entries, and without blocking, stop reading when count of files is above a certain number?

Or even a direct way to read the file count in a directory, without using ls ?

Looking for the most performant way to count files. And the ability to stop counting (if we need to call an API or com mand) when a certain limit is reached. like say

```
ls -max 20000
```

---

### Post by TheFu on 2017-05-12
Having even 1K files in a single directory is a poor design choice.  Split them up into chunks.
You can use the readdir() function in C. 
[https://stackoverflow.com/questions/1121383/counting-the-number-of-files-in-a-directory-using-c](https://stackoverflow.com/questions/1121383/counting-the-number-of-files-in-a-directory-using-c)
Can't imagine any faster way.  As you can see from the link, there isn't any way to stop reading, once started.
Manpage confirms this:
```
READDIR(3)                 Linux Programmer's Manual                READDIR(3)

NAME
       readdir, readdir_r - read a directory

SYNOPSIS
       #include <dirent.h>

       struct dirent *readdir(DIR *dirp);

       int readdir_r(DIR *dirp, struct dirent *entry, struct dirent **result);

```
I only went with C, because you posted to the Development & Programming subforum.

---

