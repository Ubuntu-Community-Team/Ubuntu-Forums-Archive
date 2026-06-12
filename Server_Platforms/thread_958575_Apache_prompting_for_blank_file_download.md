---
title: "Apache prompting for blank file download"
date: 2008-10-25
forum: Server Platforms
---

### Post by rmunsch on 2008-10-25
Note this thread marked solved:

[http://ubuntuforums.org/showthread.php?t=814606](http://ubuntuforums.org/showthread.php?t=814606)

None of the posted solutions, barring reinstall, are working.  There are suggestions re: various combinations of DirectoryIndex directives and cache-clearing.  No effect.

Rather than blindly reinstall with no understanding of how this happened, nor guarantee of it not happening again in 10 minutes, I was hoping to track down the actual issue.  Any ideas?

I've a RT install (3.6) running on the box.  Last week i got to at-a-glance (its index) just fine.  Didn't use it for a couple days (it's in progress).  Went to check on it just now, and got this "download a [large space] file" prompt.  Very odd.

Assuming this will be a production server and randomly reinstalling apache at unknown intervals will not be a viable option... what caused this breakage, and what will permanently fix it?

Thanks.

---

### Post by cariboo on 2008-10-25
I'm not sure what RT is, but have you checked /var/log/apache2/access.log and error.log to see if there is anything unusual showing?

Jim

---

### Post by rmunsch on 2008-10-25
Nothing in the error logs.

Interesting to note in access logs:

192.168.1.16 - - [18/Oct/2008:02:39:01 +0000] "GET /NoAuth/css/3.5-default/login.css HTTP/1.1" 200 461 "http://rt.[mydomain].loc/NoAuth/css/3.5-default/main.css" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.
3"

That's when it worked, just going to the machine name (local network).  RT is 'request tracker,' by the way, a web-based ticketing system.

Now, a couple days later, punching up the machine name in a browser gets this annoying "download [blank] file" dialog box, and the access log shows

192.168.1.55 - - [25/Oct/2008:14:30:08 -0400] "GET / HTTP/1.1" 200 - "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3"

I've added DirectoryIndex lines where suggested in the other thread, but no effect - and i didn't have them before, when it was working.  Something else changed, not sure what.  I am hesitant to blindly reinstall without understanding what broke.

---

