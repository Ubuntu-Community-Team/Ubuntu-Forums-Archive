---
title: "about logrotate script"
date: 2010-12-16
forum: Server Platforms
---

### Post by hyuk48 on 2010-12-16
HI~ I hava a question about logrotate.
 
in logrotate script, usually there are a lot of postrotate script like this
 
postrotate
/etc/init.d/XXXXX restart(or kill -HUP syslogd)
endscript
 
what is the reason that restart the process after making new logfile?
And is that necessary?
 
thanks for reading.

---

### Post by Calimo on 2010-12-18
Hi,

This is because the old file is moved in the directory tree, but this doesn't change its physical position in the drive. So programs would not even notice the file was moved and they would continue to append their output to the moved file and the new one would stay empty. At least it is something of this kind.
Therefore the servers have to re-open their log connections to write to the new files.

If the program cannot be told to re-open the log file, you can use "copytruncate" which will copy and empty the log instead of creating a new one.

---

