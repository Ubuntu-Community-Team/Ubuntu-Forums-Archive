---
title: "Port 143 not available? Something is listening on 143, but what?"
date: 2005-05-13
forum: Server Platforms
---

### Post by amnesia on 2005-05-13
Hello all...

How can I tell what is listening on port 143.  I try to start IMAP and it says that it can't connect to port 143 because something is listening on it.  I did stop cyrus (cyrus21?) but am not sure what is taking 143.  

**issue resolved - thanks!**

---

### Post by heimo on 2005-05-13
netstat -lp | grep 143
l = listening
p = program

Probably cyrus or dovecot.

---

### Post by amnesia on 2005-05-13
ahh - very cool!

thank you for that, I did not know!

---

