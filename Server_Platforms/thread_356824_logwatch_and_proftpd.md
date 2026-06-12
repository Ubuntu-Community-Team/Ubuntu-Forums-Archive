---
title: "logwatch and proftpd"
date: 2007-02-08
forum: Server Platforms
---

### Post by reeseslover531 on 2007-02-08
Ok so I am running ubuntu-server edgy.  I just installed logwatch, and now I want to configure logwatch to look at my proftpd logs and the proftpd xferlog.  How would I do this??  Thanks for the help!

---

### Post by reeseslover531 on 2007-02-09
so does nobody know.  There must be some people who use proftp and logwatch.  please I really need help!

---

### Post by Mr. C. on 2007-02-13
I don't use proftp, but lets see if we can get somewhere.

What's the full path to your logfile (s) where proftp logs its messages?

Show a line or two from those logfiles, exactly as they are.

MrC

---

### Post by jamietre on 2007-03-16
I came across this forum while trying to answer the same question myself. I guess there aren't many people using ProFTP and logwatch because nobody seems to have bothered to fix the script! Anyway it wasn't that hard to correct the filter. This is mostly untested (since I haven't gotten a lot of the messages so far in my logs since I made the changes), but the format didn't change that much. Any messages that still have the same text from whenever this filter was created should work now.

You can get the updated script here. This works for me so far, but isn't extensively tested over time. If you find any ProFTP log entries that are not recognized please contact me through the blog, send me a copy (or post a comment) of the offending log entry and I'll update the script.

[http://thebraindrive.blogspot.com/2007/03/logwatch-support-for-proftpd.html](http://thebraindrive.blogspot.com/2007/03/logwatch-support-for-proftpd.html)

---

### Post by Mr. C. on 2007-03-16
How about posting your updates to the logwatch list.  Other's may find it beneficial, and if it works, it will likely be included in the next release.  See the logwatch site for how to create a patch to submit.

MrC

---

### Post by jamietre on 2007-03-16
I did send a copy to the logwatch-devel mailing list. I didn't want to submit it as a formal patch/update because it is quite untested at this point.

---

