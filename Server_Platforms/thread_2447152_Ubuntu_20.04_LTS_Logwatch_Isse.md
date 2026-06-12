---
title: "Ubuntu 20.04 LTS Logwatch Isse"
date: 2020-07-13
forum: Server Platforms
---

### Post by caldwell on 2020-07-13
Hello,

I have three Ubuntu web servers running logwtach. Two running 20.04 LTS and one running 18.04 LTS.  Logwatch works correctly with version 18.04 LTS and Apache2 with good reporting on failed attempts, etc.  However, 20.04 Logwatch reports omit the http section entirely as if it doesn't see the logs at all.  The log files are there and have data, one of the 20.04 machines is busy so it should have a lot to talk about.  I have the issue on both 20.04 servers.  Is anyone else seeing the same behavior?  

Thanks,

--Dave

---

### Post by LHammonds on 2020-07-13
I have not found any recent logwatch tutorials and of the ones I have quickly glanced over, they were about as basic as basic gets.  There might have been a format change in either Apache2 or how LogWatcher expects it.  You might need to configure Apache to use a specific log option or modify logwatch to adjust how it looks at the data in the log file.

But make sure you document what versions you are dealing with:

```
apache2 -v
logwatch -v
```

Mine is:
Apache 2.4.41
Logwatch 7.5.2 (I just ran an "apt search logwatch" to see the version # in the repository)


Related threads:
[ No logwatch output for apache2 error.log ]("https://sourceforge.net/p/logwatch/discussion/1115929/thread/dd45a1ef/")

LHammonds

---

### Post by caldwell on 2020-07-14
Hello,

apache2 -v
Server version: Apache/2.4.41 (Ubuntu)
Server built:   2020-04-13T17:19:17
logwatch -v
Logwatch 7.5.2 (released 07/22/19)

Logwatch is currently at 7.5.3 on sourceforge.  I'm going to try updating, although I try to avoid having too many parts and pieces that are out of sync with the official repositories.  

[https://sourceforge.net/p/logwatch/git/ci/master/tree/](https://sourceforge.net/p/logwatch/git/ci/master/tree/)

I'll let you know how it goes.

Thank you!

---

### Post by caldwell on 2020-07-16
Upgrading did not resolve the issue.  However, changing the output detail level did.  So on my 18.04 LTS web server I'm running

Logwatch 7.4.3 (released 12/07/16)

It considers entries like this to be important enough to report with "Detail = Low":

httpd


Requests with error response codes
  400 Bad Request
     null: 1 Time(s)
  403 Forbidden
     /: 2 Time(s)
     /manager/html: 1 Time(s)
     /manager/text/list: 1 Time(s)
     /portal/redlion: 1 Time(s)
  404 Not Found
     /favicon.ico: 5 Time(s)
     /4e5e5d7364f443e28fbf0d3ae744a59a: 1 Time(s)
     /TP/html/public/index.php: 1 Time(s)
     /TP/index.php: 1 Time(s)
[...]

However, it appears logwatch raised the bar in 7.5.x so to get the same report you now need to set "Detail = Med" or above in the logwatch.conf file.  

Fixed!

---

