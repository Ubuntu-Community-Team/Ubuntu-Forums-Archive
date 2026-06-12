---
title: "Apache2 PHP5 child pid exit segmentation fault (11)"
date: 2008-07-17
forum: Server Platforms
---

### Post by daniel_summers on 2008-07-17
I googled for this and found several things that can cause it, but none of the hits I found applied to my situation.

I've got a pretty fresh install of Apache2 and PHP5 using the modules from the repositories.  I enabled several modules, and I made sure that I had mpm-prefork installed (from what I found on my search, a common error).  I've had several installations of WordPress work flawlessly, phpMyAdmin and phpPgAdmin both work great, and the custom web app I'm developing has worked well up to this point.  The only difference here is that I'm posting data to it.

In my custom script, I've put "echo" statements in, but it doesn't even get to the first one.  I suspect this may be either a configuration problem or a conflict between different modules, but I'm at a loss.  I've attached my phpinfo() output, which shows the PHP version and its modules, plus the Apache2 modules that are loaded.  Any ideas?

---

### Post by daniel_summers on 2008-07-17
Well, it appears that I'm just a really talented programmer.  I moved this code to another server, and got the same results.  I've run similar code on both, and it worked.  Never mind about the configuration - it must be my awesome code!

---

