---
title: "postfix problems php mail doesn't work"
date: 2015-03-30
forum: Server Platforms
---

### Post by jackylyn on 2015-03-30
Hello,
I have some problems with php mail.

I configured it a few days ago and everything worked fine.

Now I changed the owner of /var/www/ directory and files in it, cause a svn hook didn't work else. I have no idea what this has to do with postfix or php mail, but suddenly sending mails via php doesn't work anymore.

I guess it could have messed up the ownership of some files, but I have no idea which ones. Averything else would be very strange, cause I din't do anything else. Mysql was broken, too becuase of this, but I could already fix it. 
Google didn't help a lot, so I hope anyone here could help me.

I already tried to chance ownership like in this example:
[http://lists.mailscanner.info/pipermail/mailscanner/2007-January/068905.html](http://lists.mailscanner.info/pipermail/mailscanner/2007-January/068905.html)
but that didn't help. Before the owner of this files was www-data. But that didn't work, too.

If you need to get any other data feel free to ask for it.

---

### Post by jackylyn on 2015-04-03
I reinstalled postfix and it works fine again.

---

