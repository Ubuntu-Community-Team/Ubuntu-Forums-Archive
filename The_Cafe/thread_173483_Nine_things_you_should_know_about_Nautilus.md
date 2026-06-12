---
title: "Nine things you should know about Nautilus"
date: 2006-05-10
forum: The Cafe
---

### Post by jc87 on 2006-05-10
I just saw this [Article](http://linuxboxadmin.com/articles/nautilus.php) at /. , has got a lot of nice tricks for Nautilus , i´m specially interested in the scripts thing:-D

---

### Post by Resurrection on 2006-05-10
Good article.  While I too am fascinated by the scripts idea, my question is what would I really use this for?  I'd love to learn some more about scripting languages (I understand programming in general, like C) but I haven't ever use a script before.  I wonder if there are any good scripting projects to start with out there?  Something like a top ten list of most implemented scripts in Nautilus?

---

### Post by Keith_Beef on 2006-05-10
[QUOTE=jc87]I just saw this [Article](http://linuxboxadmin.com/articles/nautilus.php) at /. , has got a lot of nice tricks for Nautilus , i´m specially interested in the scripts thing:-D[/QUOTE]

Scripts are great, and so easy to use.

I made a set of scripts for frequently-needed operations like creating a set on directories named with the months of the year, and for rotating images.

Then I found exiftran and siplified all my rotation scripts.

One trap, is that I found that the variables set by Nautilus, and made available to my scripts, didn't work properly if there is a whitespace somewhere in the path...

Anyway, here is a very simple example of a nautilus script:

```
## autorotate
#
# takes a new-line delimited list of files
#
# loop through the list, for each file it
# calls exiftran to rotate the image so
# as to be the right way up.
#
# The Canon A610 has an orientation sensor built-in,
# and sets the EXIF tag, but this doesn't work when the
# camera is completely upside-down.
#
for a in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
	exiftran -ai $a
done

```

Try it, then try it with your images in a directory called "Test\ with\ spaces" to see what I mean.


Beef.

---

### Post by ice60 on 2006-05-10
you can get lots of Nautilus scripts from here -
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

i just downloaded them all, plus i have afew others.

i use Nautilus Actions too so i have an 'open terminal here' 'search' 'open nautilus as root' etc in my right-click menu
[http://www.grumz.net/index.php?q=node/8](http://www.grumz.net/index.php?q=node/8)

---

### Post by Omnios on 2006-05-10
Very nice article and I actualy learn't something about gnome. Scripts are cool I wrote this one after looking at the other scripts I had in the folder guess its my first nautalis script
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal

```
 It opens terminal in the current directory.

---

### Post by egon spengler on 2006-05-10
[QUOTE=Keith_Beef]Scripts are great, and so easy to use.

I made a set of scripts for frequently-needed operations like creating a set on directories named with the months of the year, and for rotating images.

Then I found exiftran and siplified all my rotation scripts.

One trap, is that I found that the variables set by Nautilus, and made available to my scripts, didn't work properly if there is a whitespace somewhere in the path...

Anyway, here is a very simple example of a nautilus script:

```
## autorotate
#
# takes a new-line delimited list of files
#
# loop through the list, for each file it
# calls exiftran to rotate the image so
# as to be the right way up.
#
# The Canon A610 has an orientation sensor built-in,
# and sets the EXIF tag, but this doesn't work when the
# camera is completely upside-down.
#
for input_file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
	exiftran -ai $a
done

```

Try it, then try it with your images in a directory called "Test\ with\ spaces" to see what I mean.


Beef.[/QUOTE]
Try wrapping the var in double quotes and it should work, I use scripts on directories with spaces all the time

---

### Post by 23meg on 2006-05-10
I open things as root with [this method]("http://ubuntuforums.org/showthread.php?t=24008").

---

### Post by briancurtin on 2006-05-10
im a fan of this script: [http://directory.fsf.org/audio/wav/editors/audio-convert.html](http://directory.fsf.org/audio/wav/editors/audio-convert.html)

---

