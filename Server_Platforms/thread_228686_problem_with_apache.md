---
title: "problem with apache"
date: 2006-08-03
forum: Server Platforms
---

### Post by careca on 2006-08-03
do:
sudo apache2ctl -k restart

and says:
httpd not running, trying to start

but it really doesn't start. I check going to 'ubuntu' (my 'localhost').

Previously I edited apache2.cong but apache2ctl configtest said Syntax OK.

---

### Post by slakkie on 2006-08-03
What do you see in your Apache error logs?

Try the restart procedure manually, by first stopping apache, and then starting apache.

Check with netstat -an | grep .80 to check wheter its actually listening on port 80.

---

### Post by careca on 2006-08-03
httpd seems to be off always, because everytime i type:
apache2 -k restart
it says that http is not on, trying to start.

The strange thing is that. There is no error log or message.

---

### Post by slakkie on 2006-08-04
I think this thread can be closed, you opened another one as well: [http://ubuntuforums.org/showthread.php?t=228685](http://ubuntuforums.org/showthread.php?t=228685)

---

