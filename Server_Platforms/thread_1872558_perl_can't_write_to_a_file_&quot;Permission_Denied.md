---
title: "perl can't write to a file &quot;Permission Denied&quot;"
date: 2011-10-30
forum: Server Platforms
---

### Post by ubun_tu on 2011-10-30
The perl script, perl script directory and the directory that I want to write the file into all have a permission of 777.  I spent about 2 hours researching this issue on Google and have come up empty handed.  I am trying to migrate this script from a 10.04 installation where it works just fine.

I receive a "Permission Denied" through the browser only.  When run through the command line, the file creates successfully.

Here is the line of perl that causes a "Permission Denied" error in the Apache log file (and through the browser):

open FILE, ">/home/scott/file" or die $!;

Any help would be greatly appreciated.

---

### Post by ubun_tu on 2011-10-30
Sorry, forgot to list the versions of Apache:

10.04 (where the perl script worked and can write the file successfully)
2.2.14-5ubuntu8.3

11.10 (where the perl script doesn't work)
2.2.20-1Ubuntu1

---

### Post by vasile002 on 2011-10-31
try this:
```

chmod 755 /home/scott

```

by default user  home directories are not readable by anyone except the user itself

---

### Post by ubun_tu on 2011-10-31
I probably didn't state it very accurately above, but I had already tried this.  The permission on the folder was already 755 and in addition I had mentioned that the script does write the file when run from the command line only - just not when its run through the browser.

Thanks vasile002, but it didn't fix the problem.

---

### Post by ubun_tu on 2011-10-31
I've confirmed that this works on another 11.10 box through the browser, so the version of Ubuntu can't be the problem.  There must be a config setting in Apache that is not allowing the perl script to create a directory maybe due to its permissions.  I've probably spent another hour Googling Apache settings and I don't feel that I am any closer to resolving this problem.

Has anyone come across a problem like this before?

---

### Post by ubun_tu on 2011-10-31
I've found some posts that talk about SELinux not having the correct settings but they all appear to deal with Fedora.  I've confirmed that I don't even have it installed on any of my Ubuntu boxes so this isn't going to provide a fix.

---

