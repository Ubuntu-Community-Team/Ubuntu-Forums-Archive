---
title: "How to tail log file and printout?"
date: 2010-09-29
forum: Server Platforms
---

### Post by hendraorhnd on 2010-09-29
Hallo,

I need to printout auth.log each line by log event, I think it should be running using the following command:

~# tail -f /var/log/auth.log | lpr

but it's not, why?

the lpr package already is installed in myserver, there is no problem to print directly.

~# cat /var/log/auth.log | lpr

is anyone can help?, thanks.

---

### Post by hendraorhnd on 2010-09-29
sorry my mistake,

~# tail -f /var/log/auth.log > /dev/lp0

and it's ok now.

---

### Post by the_original_billq on 2010-09-29
Or you could just get yourself an ASR33 :-)

[http://www.columbia.edu/acis/history/teletype.html](http://www.columbia.edu/acis/history/teletype.html)

---

