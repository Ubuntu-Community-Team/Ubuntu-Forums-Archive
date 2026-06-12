---
title: "chmod dir"
date: 2009-06-05
forum: Server Platforms
---

### Post by gishaust on 2009-06-05
I want to be able to change the permissions on a whole directory of folders from drwx to drwx r-x r-x. but I am sick of change the directories one by one so I found that you can use the find command and then it will do it automatically but I can't get it to work.

Is anyone able to see my problem.


```

public_html$ sudo find . -type d website/ -exec chmod 755 {} \;
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]


```

---

### Post by gishaust on 2009-06-05
sudo find website/ -type d  -exec chmod 755 {} \;

I had the folder in the wrong spot

---

