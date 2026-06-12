---
title: "Loaded hard drive ..."
date: 2008-05-23
forum: Security
---

### Post by apollon1234 on 2008-05-23
Hi, I have recently discovered that my hard drive as been filled with a lot of the by someone that I don't know.

I would like to know if there's a way to find on my hard drive all the files that has been installed recently (lets say during the last 5 days) by who and where. I've been trough the log files but I am not good enough to recognize witch entries are bad and witch aren't.


Thank you for your help and sorry for my approximate English :)

---

### Post by Rewil on 2008-06-09
I don't know of a way to do it with a graphical interface, but the "find" command in a terminal window can be used to search for files altered since a specified date. There are many options to this command, so it is possible to select different aspects (accessed, modified, etc.) As an example:

find $HOME -mtime -2

will find all files under your home directory that have been modified in the last two days. This will descend into all the subdirectories and display the full paths for each file.

If you want to see all the options, type "man find" to bring up the man pages for this command. To exit the man pages, type 'q'.

---

### Post by Biochem on 2008-06-09
I had once a daemon set with a log level a tiny bit to high which filled my partitions in a day.

So you might want to look in /var/log for unusually large files.

Might not be as fancy as Rewil's method but surely covers the "By someone I don't know" part. 

good luck

---

