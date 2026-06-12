---
title: "Apache Fails to start, tried most everything..."
date: 2009-09-17
forum: Server Platforms
---

### Post by geudrik on 2009-09-17
I have read and read, and have yet to find a solution to this issue.  When I run sudo apache -k start (or restart) it fails, and the only message displayed is a warning.  I can stop it fine, but it refuses to start properly.  What's weird is this: regardless of wether or not its been started or stopped, I can still access the "It works!" page by going to my lcoalhost.  PHP doesnt work though.

Anyone have any ideas as to whats going on?

---

### Post by Udayakiran on 2009-09-18
Can you post what the warning message is?

And have you tried searching for the warning message in google? At times, you may get a solution.

---

### Post by openfly on 2009-09-18
At a guess I'd say you aren't loading the php module properly.

I suggest running an apachectl configtest to be certain there's no obvious syntax errors in you httpd conf files.

Also be sure you have handlers setup for .php and (optionally) .phps

---

