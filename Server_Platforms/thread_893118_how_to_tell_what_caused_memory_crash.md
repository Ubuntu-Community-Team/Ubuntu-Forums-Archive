---
title: "how to tell what caused memory crash?"
date: 2008-08-17
forum: Server Platforms
---

### Post by lefnire on 2008-08-17
My server crashed due to "out of memory".  Could have been a PHP script, MySQL, a Java CGI script, etc.... how do I find out what caused the crash?  Is there a log file somewhere?

---

### Post by Yuki_Nagato on 2008-08-17
There should be logs in

/var/log

and perhaps more in

/var/log/apache2

---

### Post by lefnire on 2008-08-17
per-chance do you know which of these logs might help me diagnose the memory crash?  I've been looking at /var/log/apache2/error.log & couldn't seem to find what i was looking for, so I browsed some other .log's at random but none of them make sense to me.

---

### Post by Yuki_Nagato on 2008-08-17
Hee Hee.

NOTHING ever appears in my apache2 access log, so I just believe it stopped running ages ago.  I should be worried that something is wiping the logs to cover up its tracks, but I have had not problems, so I carry on blindly.

Have you tried

/var/log/syslog
/var/log/syslog.0

Those might have some information on you actual machine.

_[I believe this is the application that creates the "syslog"]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch05_:_Troubleshooting_Linux_with_syslog")_

---

