---
title: "Upload large file fails (I/O) error"
date: 2011-10-26
forum: Server Platforms
---

### Post by Inexine on 2011-10-26
Hello,


Uploading large files on my web server for some users. It seems to happen when the bandwidth is low. Neither the browser nor the OS seem to be in cause.

The partial file is correctly created in the temporary directory but after several minutes (randomly), the upload stops and returns an I/O error.

All PHP params have been checked again and again and it works well for some users.
I can't find any error.

the version of Ubuntu on my server is 4.2.

Any clue ?

Thanks for your help

---

### Post by vasile002 on 2011-10-27
what I/O error are you talking about? where do you see it, in the apache logs? in /var/log/syslog? please provide more details

---

### Post by Inexine on 2011-10-27
Hello,

Unfortunately I can't find any errors in the apache log file (debug level is activated) nor in syslog.

If I upload a file through a classic web form, the process never returns.
If I upload via plugin flash, flash returns an I/O error.

But in any case, no error on the server.

---

### Post by samosamo on 2011-10-27
We can't help you with your flash plugin. First I would troubleshoot other methods of uploading files to your server and if it works, then I would contact the support for this flash plugin. Or consider using one of the other methods.

---

