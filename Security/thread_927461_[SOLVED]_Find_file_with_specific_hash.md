---
title: "[SOLVED] Find file with specific hash"
date: 2008-09-23
forum: Security
---

### Post by osx on 2008-09-23
I want to be able to search an entire directory tree (including branches) for a file (e.g., malware); however, I want to be able to find the file based on its MD5 hash value rather than name since names are easily changed.

I've experimented with "find <path to search> | md5sum * | grep <insert hash>"

This works as long as "<path to search>" contains only files. It stops when it encounters a directory.

Anybody know how I can do this?

Thanks.

---

### Post by ds[de] on 2008-09-23
Hi,

if you add a '-type' switch to the 'find'-command, you can alter your command to only return files instead of files and directories.

```
find -type f <path> | md5sum | grep <hash>
```
^^ this actually doesn't work, read below to find an answer.

Note: This excludes block and character devices for example.


Regards,
ds[de]

---

### Post by osx on 2008-09-23
> **'ds[de] said:**
> Hi,

if you add a '-type' switch to the 'find'-command, you can alter your command to only return files instead of files and directories.

```
find -type f <path> | md5sum | grep <hash>
```

Note: This excludes block and character devices for example.


Regards,
ds[de]

I tried that and it didn't work. Here's what I used:

```
 sudo find -type f / | md5sum | grep 42dcbe3b3f91e7febc40375f538be530 
```

The message I get back says "find: paths must precede expression". I want to search from the top of the directory tree down since I will have no idea where the file might be hiding.

Thanks.

---

### Post by osx on 2008-09-23
I figured out part of the problem. If I do this

```
 find / -type f -exec md5sum '{}' \; 
```

Then I am able to walk the tree and compute a hash for each file; however, I can't seem to pass it to grep for searching.

---

### Post by osx on 2008-09-23
Now I have this working, but it seems WAY too sloppy.

```
find / -type f -exec md5sum '{}' \; > list.txt | cat list.txt | grep b2a0715172d9448a00e464513f1069870
```

Any suggestions?

---

### Post by cdenley on 2008-09-23
```

md5=42dcbe3b3f91e7febc40375f538be530
sudo find / -type f|xargs md5sum|grep $md5|cut -d ' ' -f 3

```

---

### Post by Gamma746 on 2008-09-24
```
 find /foo/bar|xargs md5sum|grep YOUR_MD5_SUM_HERE
```

---

### Post by osx on 2008-10-06
That helps. Thanks.

---

### Post by rovae on 2008-10-06
im actually interested who can make the best [Lace Wigs](http://www.royalmewigs.com), i think the one to get the best [Lace Human Hair Wigs](http://www.royalmewigs.com/lace-human-hair-wigs-c-10.html) is one with its own music and properly edited. besides [Cosplay Wigs](http://www.cosprops.com/cosplay-wigs-c-5.html)  [Buy Cheap Lace Wigs](http://www.royalmewigs.com)  [Diablo 2 CD Key](http://www.mmovp.com/buy-cd-key-diablo-2-cd-key-c-1268_1270.html)

---

