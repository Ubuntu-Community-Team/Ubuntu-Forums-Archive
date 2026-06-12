---
title: "File-roller: No compression below 10.2 kB"
date: 2012-10-01
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2012-10-01
i compressed a folder on my 12.10 xubuntu install and it went from 12kb to 10kb
i compressed the same folder on my 10.04 ubuntu install and it went from 12kb to 2.6kb
i was using .tar.bz2
on my 10.04 install i have file rollers compresion level at maimum

how can i get my 12.10 install to do this?

---

### Post by pqwoerituytrueiwoq on 2012-10-08
i made a bug report after the compression level was -66%
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117)

---

### Post by jfernyhough on 2012-10-08
Nice find. I did a couple of quick tests and it looks as though file roller is not actually compressing the tar file, and it doesn't matter which compression method is chosen. Not sure why it has this effect on your files as the command works as expected for other files.

Steps to reproduce:
1) In Nautilus, right click on "backlightx" directory, Compress...
2) Select .tar.bz2
3) Resulting file size is 10.2KB

4) Right click on directory, Compress...
5) Select .tar
6) Resulting file size is 10.2KB

7) Right-click on .tar, Compress...
8) Select .bz2
9) Resulting file is 870KB

---

### Post by mc4man on 2012-10-08
> **jfernyhough said:**
> Nice find. I did a couple of quick tests and it looks as though file roller is not actually compressing the tar file, and it doesn't matter which compression method is chosen. Not sure why it has this effect on your files as the command works as expected for other files.

here file-roller is 'compressing' but will never go below 10.2kB
So - a folder with a number of small files
43.6kB goes to 10.6kB
34kB goes to 10.2kB
15kB goes to 10.2kB
1.5kB goes [COLOR="Blue"]UP[/COLOR] to 10.2kB

---

### Post by mc4man on 2012-10-09
The last file-roller in 12.10 to go below 10.2kB was 3.5.3-0ubuntu1 so this changed with the new 3.5.4 release

If this were to be filed upstream it's likely a response one way or the other would gotten quickly
(the file-roller maintainer/dev is usually quite prompt on bug reports

---

### Post by pqwoerituytrueiwoq on 2012-10-09
3.5.3 you say well i have 3.6 on my 12.10 install
```
chad@Compaq-Presario-CQ60:~$ file-roller -v
file-roller 3.6.0, Copyright © 2001-2012 Free Software Foundation, Inc.
chad@Compaq-Presario-CQ60:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
chad@Compaq-Presario-CQ60:~$
```

---

### Post by pqwoerituytrueiwoq on 2012-10-12
so i decided to switch to xarchiver and it works :)
but this made me lol (see attachment)

---

### Post by cariboo on 2013-03-03
A bump for the move, to bring it to the top of the page

---

### Post by pqwoerituytrueiwoq on 2013-03-04
Thanks for moving it, i really hate this bug

---

