---
title: "How to extract text from log file Apache - 12.04"
date: 2013-10-31
forum: Server Platforms
---

### Post by Dominic--- on 2013-10-31
Hi all,

I don't know whether I am posting this in the right section, so my apologies if I placed it in the wrong section.

There is a lot of information in the error.log and access.log from the Apache logs.
Most of the time I am only interested in only a certrain type of log entry.

My question is how can I extract a certain type of entry/sentence and extract it to another text file?
For example, copy all 404 access attempts to a text file?

I am new to Linux and have no clue where to begin...

Thanks in advance!

---

### Post by Lars Noodén on 2013-10-31
Usually [grep](http://manpages.ubuntu.com/manpages/raring/en/man1/grep.1posix.html) and [awk](http://manpages.ubuntu.com/manpages/raring/en/man1/awk.1posix.html) are the go-to tools for preliminary log work.  grep is simple and will find lines that match a pattern.  So the following will print any lines with the string 404 anywhere on the line.

```

grep 404 /var/log/apache2/access.log

```

awk is actually a scripting language, but still can be used for one-liners.  It can be much more precise than grep.  The following will print any lines with the response code 404.  The response code being in the 9th column of text, as separated by spaces.

```

awk '$9 == "404" { print }' /var/log/apache2/access.log 

```

Or you can have it just print out the file that was missing, which happens to be in the 7th column:

```

awk '$9 == "404" { print $7 }' /var/log/apache2/access.log 

```

You can capture the output by using a [redirect](http://www.tldp.org/LDP/abs/html/io-redirection.html) which will put it into a file for you.

```

awk '$9 == "404" { print $7 }' /var/log/apache2/access.log  > missing-files.txt
awk '$9 == "404" { print $7 }' /var/log/apache2/access.log | sort -u > missing-files.txt

```

You'll find lots of guides and howtos on grep and awk, but you can always ask here, too.

---

### Post by Dominic--- on 2013-10-31
Thanks Lars! Helped me a lot.

---

