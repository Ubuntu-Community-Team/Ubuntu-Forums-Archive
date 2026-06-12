---
title: "Errors installing Postfix"
date: 2009-09-29
forum: Server Platforms
---

### Post by Fliggerty on 2009-09-29
Hello,

I've been trying to get my server to send emails after an HDD reformat and reinstall.

I can't seem to get Postfix to install though.

First I tried to use tasksel to install "Mail Server," but it always gives me this error:

tasksel: aptitude failed (100)

When I use sudo apt-get install postfix I get this error:

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: fargoth.hsd1.ut.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: fargoth.hsd1.ut.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 75
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?

---

### Post by Fliggerty on 2009-09-29
No one has any suggestions on what I could try here?

---

### Post by cariboo on 2009-09-29
Please don't bump your thread more than once every 24 hours. Remember, we are all volunteers here, the person that may be able to answer your question just hasn't seen it yet.

---

