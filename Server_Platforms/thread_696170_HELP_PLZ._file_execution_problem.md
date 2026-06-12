---
title: "HELP PLZ. file execution problem"
date: 2008-02-13
forum: Server Platforms
---

### Post by Bruce420 on 2008-02-13
hello, 
I am trying to execute a pre-compiled server 
exectuion files in directory /opt/mangos/bin.
 Every time i try and execute the files i get an error message stating:

**-bash: ./mangos-worldd: No such file or directory**

As i know full well that the file is contained 
in the directory this is a severe problem to me. 
As verification that the files are there 
when i type dir i get the output:

**mangos-realmd  mangos-worldd**

Both of these files give the error message previously stated.
Also when i type ls -l to check if these files are executable the out put is:

[B]-rwxrwxrwx 1 root root  2028407 2008-01-19 17:35 [color=#00FF00]mangos-realmd[/color]
-rwxrwxrwx 1 root root 52491534 2008-01-19 17:35 [color=#00FF00]mangos-worldd[/color][/B]

Any help on the problem would be greatly appreciated. 
Thank you in advance to anybody who replys.

---

### Post by wirelessmonkey on 2008-02-13
First, I found this, which may be of use. [http://64.233.167.104/search?q=cache:l6wRr5jUBzcJ:www.mangosproject.org/forum/index.php%3Fact%3DPrint%26client%3Dprinter%26f%3D32%26t%3D5514+mangos-realmd+ubuntu&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a](http://64.233.167.104/search?q=cache:l6wRr5jUBzcJ:www.mangosproject.org/forum/index.php%3Fact%3DPrint%26client%3Dprinter%26f%3D32%26t%3D5514+mangos-realmd+ubuntu&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a)


Second, you need to run them as superuser, so :
bash: sudo ./mangos-worldd

---

