---
title: "rsync exclude rules nightmare"
date: 2012-03-09
forum: Server Platforms
---

### Post by u-slayer on 2012-03-09
I'm trying to get rsync to only copy certain subfolders by name.

This works:

+ A/*Good*/
A/*

But if I want to get sub-sub folders:

This doesn't work:
+ A/**Good*/
A/*

What do I do?

---

### Post by papibe on 2012-03-09
Hi u-slayer.

One usually end the include/exclude rsync's rules with a '- *', or a '+ *' depending on what are trying to do.

I would be helpful if you also post the actual rsync command you are using. 

For now I would recommend taking a look at post#3 of this [thread]("http://ubuntuforums.org/showthread.php?t=1893841&highlight=rsync"), and the linked example [here]("http://ubuntuforums.org/showthread.php?t=1881554&highlight=rsync+include").

Hope that helps, and tell us if you need more tips with rsync.
Regards.

---

### Post by u-slayer on 2012-03-09
yeah adding that header/footer doesn't do anything

and the command is rsync -van /input/ /output --delete-before --delete-excluded --exclude-from=file

- *
+ mkv/**Good*/
mkv/*
+ *

---

### Post by papibe on 2012-03-09
I'm going to guess a little your file structure and the subdirectories you are trying to copy, but this will:
[INDENT](1) create the 'mkv' directory.
(2) create all directories below 'mkv' matching *Good*.
(3) copy all files and directories (the whole hierarchy) under those dirs created on step (2).[/INDENT]

```
rsync -avn --delete-before --delete-excluded --exclude-from=file  /input/ /output
```
where 'file' contains:
```
+ mkv/
+ mkv/*Good*/***
- *
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by u-slayer on 2012-03-09
That only matches sub folders 1 level in. It doesn't match sub-sub or sub-sub-sub  folders.

---

### Post by papibe on 2012-03-09
It works fine here, even several levels down. May be it is a version problem?

I tested it on 11.04 using rsync version 3.0.7  protocol (version 30).

Just to be clear. Im my example there has to be at least one directory that matches '*Good*' directly under mkv. Then, under that everything is copied. Is that what you are looking for?

Regards.

---

### Post by u-slayer on 2012-03-09
> **papibe said:**
> 
Just to be clear. Im my example there has to be at least one directory that matches '*Good*' directly under mkv. Then, under that everything is copied. Is that what you are looking for?


No. I want it to match a directory like this:

A/B/C/D/Good

---

### Post by papibe on 2012-03-10
Will the pattern '*Good*' match a file, or a directory?

Regards.

---

### Post by u-slayer on 2012-03-10
Directory Only.

---

### Post by papibe on 2012-03-10
Let me cover a couple of cases.

If you know the directory structure (like in post 13), you can use this rules:
```
+ A/
+ A/B/
+ A/B/C/
+ A/B/C/D/
+ A/B/C/D/Good/
+ A/B/C/D/Good/***
- *
```
The reason for the inclusion of every single directory in the path is because rsync search the directory structure and eliminates anything that is not on the rules. Thus:
```
+ A/**/Good/***
- *
```
or even
```
+ A/B/C/D/Good/***
- *
```
won't work because rsync eliminate the A/, A/B/, etc. from the search early on.

In case you don't know the exact directory structure. You can't solve your problem using include/exclude rules. You need other tools to reinforce the rsync.

For example:
```
find -type d -name '*Good*'
```
will find the complete path of the directory you are looking for. Then to get all files and folders under it, you could do another find:
```
find -type d -name '*Good*' | xargs -I dir find dir 
```
Then you'll have all files and folders you want to copy.

rsync has an option called '--files-from' that let's you get the list of file to transfer from a a file or from the standard input (use -). Then this would work:
```
cd /input/
find -type d -name '*Good*' | xargs -I dir find dir | rsync -avn --files-from=- /input/ /output
```
Note that I 'cd' to /input/ so the find can display the names relative to the source directory (as rsync needs it).

Now just to extra safe (in case of spaces or other weird characters on the files names) I would separate the list of files using a null character:
```
cd /input/

find -type d -name '*Good*' -print0 | 
  xargs -0 -I dir find dir -print0 | 
  rsync -0 -avn --files-from=- /input/ /output
```
Hope that helps, and tell us how it goes.
Regards.

---

