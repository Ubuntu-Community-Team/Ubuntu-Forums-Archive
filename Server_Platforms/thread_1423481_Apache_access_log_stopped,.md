---
title: "Apache access log stopped,"
date: 2010-03-06
forum: Server Platforms
---

### Post by memyselfnie on 2010-03-06
Hyyas, I am running an apache server thru webmin, on a 8.04 install.  Attempting to install awstats I have realized that access.log stopped writing some months ago.  Went back thru the error logs and found I had deleted the virtual server, and started a new one.  Everything else works fine, it never even occurred to me that logging would not also be restarted.  I would just like to get it going again, any clues???

---

### Post by gary441 on 2010-03-09
Mine also stopped logging on Nov. 14th, 2009. I'm just looking into it now.
I didn't have a virtual server running. Error log is working. I did switch to running SSL, instead of running apache on port 80. Might have something to do with it.
Any ideas?  If I find anything, I'll write back.

Gary

Update: Found the issue: ME!
Switching from http to https uses ssl_access.log file instead of access.log.  Learn something new everyday.

---

### Post by memyselfnie on 2010-03-11
Thanks, I had no idea ssl caused a seperate log to be created.  I just looked for one myself and found nothing tho, is it in /var/log/apache2?

---

### Post by memyselfnie on 2010-03-11
Thanks, I had no idea ssl caused a seperate log to be created.  I just looked for one myself and found nothing tho, is it in /var/log/apache2?

---

### Post by gary441 on 2010-03-12
Yes...  /var/log/apache2/ssl_access.log

---

### Post by memyselfnie on 2010-03-18
Just fyi, the problem was the Customlog line in apache2.conf was missing.  Thanks!

---

