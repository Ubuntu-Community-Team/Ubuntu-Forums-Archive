---
title: "proftpd server help"
date: 2009-11-28
forum: Server Platforms
---

### Post by jimfuture12345 on 2009-11-28
hi, 
sorry i need little push to do this part ,i am setting up proftpd server l don't know where is etc/shell (folder or file ) in second secure step .
 
2- Add this line in /etc/shells file (sudo gedit /etc/shells to open the file) :
Code:
/bin/false
 

will you explain me more ? 
ftp-shared folder ok done
and stop
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by carl.davis on 2009-11-28
Use the key combination Alt-F2 then type ```
gksudo gedit /etc/shells
``` This will open the file and you can then edit it as instructed.

---

