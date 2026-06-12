---
title: "how come i have so many apache2 logs?"
date: 2007-12-05
forum: Server Platforms
---

### Post by winstonzeng on 2007-12-05
how come i have so many apache2 logs? is this normal?

[https://24.85.38.53/files/apache2%20logs.JPG](https://24.85.38.53/files/apache2%20logs.JPG)

---

### Post by MJN on 2007-12-05
The server is down...

Maybe the logs might have been telling you something? ;)

Mathew

---

### Post by conjur3r on 2007-12-05
Why password protect the file?  Upload it to the forum or somewhere public so we can see and better help you.

---

### Post by winstonzeng on 2007-12-05
i removed the .htaccess. please check again

---

### Post by MJN on 2007-12-05
That's perfectly normal - the logs get automatically rotated (weekly by default) and the old one get gzipped up to save space.

The access.log records all the file accesses and hence is generally your 'main' log. The error.log records any errors (check the file sizes - they're relatively tiny as you'd expect). Finally, the rewrite.log records whenever a rewrite rule has been used - you can disable this by commenting out any RewriteLogLevel directive (or setting it to zero) as under normal use you probably have little, if any, need for this logging (and there's no point wasting resources on something you don't need).

Mathew

---

### Post by winstonzeng on 2007-12-05
ooooo okay. that makes alot of sense. wat about the access.log.1 and error.log.1?

---

### Post by MJN on 2007-12-06
The first rotation doesn't get compressed so it leaves you with the current and last logs in an easily-accessible form. Next week access.log.1 will get rotated, and compressed, to form access.log.2.gz and this will ripple up the existing logs. The last log (whos minimum age is defined in /etc/logrotate.d/apache2.conf) will then get deleted.
 
Mathew

---

