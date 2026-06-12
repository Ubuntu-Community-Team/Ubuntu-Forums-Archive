---
title: "Calamaris won't work"
date: 2010-05-28
forum: Server Platforms
---

### Post by cong06 on 2010-05-28
I can't figure out how to get Calamaris to work.
I'm using squid3, so I understand that there could be a problem with that, however I installed links for the logs, so that even though it uses "squid" it should work for squid3...
```

ls -al squid
lrwxrwxrwx 1 root root 7 2010-05-05 12:21 squid -> squid3/

```

I even tried going into the /etc/cron.daily/calamaris file, and changing squid to squid3...

But when I run the crontask, it gives no output and there's no file in /var/www/calamaris

What's going on? How can I fix it?
I need a program to analyze computer bandwidth.

---

### Post by technoanarkst on 2010-10-13
Hello!

Calamaris doesn't work out of the box.  You'll need to do some configuration.  Once you've read through the config file (/etc/calamaris/calamaris.conf) you'll need to go into /etc/cron.daily, and edit the "shebang".  It seems that this minor error has managed to slip past the package maintainer. *shrug* 

change:
```

#! /bin/sh

```
to
```

#!/bin/sh

```

...

Now... if I can just get my calamaris to produce HTML reports on the cron job.

Good luck!

---

### Post by IgorRafael on 2012-05-09
Hello, 
with calamaris, you can generate reports of the all the logs for the complete cluster? Or just will do of a single cache?
If so what is the syntax?
thanks!

---

