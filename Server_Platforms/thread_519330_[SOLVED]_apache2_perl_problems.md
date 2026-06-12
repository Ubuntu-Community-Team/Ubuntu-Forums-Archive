---
title: "[SOLVED] apache2 perl problems"
date: 2007-08-06
forum: Server Platforms
---

### Post by spur on 2007-08-06
I have installed and can't get it too work properly. Others have similar problems unsolved. I have searched this forum and the apache web site for a solution. (googled even)
The problem is (I have used a ScriptAlias line to change my directory for files.)
when I use > [http://localhost/cgi-bin/hello-worl.pl](http://localhost/cgi-bin/hello-worl.pl) I get the download dialog box.
If I use > [Http://localhost/cgi-bin/](Http://localhost/cgi-bin/) I get the 403 forbidden error message.
I have the > AddHandler cgi-script .cgi .pl line added and mod perl installed and configured. I checked it is loaded as well.
All the files and directories are 755 for permissions and I get the same if I change them to 777.:frown:

---

### Post by spur on 2007-08-07
A partial answer is to use Eclipse with Epic. I can view and test my perl programs as if they were going through a server so my immediate need is handled but the problem of configuring apache2 is not.
I found that configuring epic to use Firefox not the internal browser worked best.
:lolflag:

---

### Post by gene02 on 2007-08-07
Can you post the lines that appear in /var/log/apache2/access.log and /var/log/apache2/error.log when you access those URLs?

---

### Post by spur on 2007-08-09
I found my problem with the help of this forum, on another thread. I was adding in extra stuff to my she-bang line. Thanks all for your input.

---

