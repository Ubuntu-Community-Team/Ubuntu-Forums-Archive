---
title: "Timeout or buffer issues?  PHP issues maybe?"
date: 2011-04-29
forum: Server Platforms
---

### Post by rage9 on 2011-04-29
We recently moved our web application from a dedicated server running CentOS to the Amazon EC2 cloud running Ubuntu.  

We've been having this weird problem of PHP scripts not outputting anything, most notably if they have a long run time (over 30 seconds).  We've been able to solve this issue at least in some scripts by using PHP's flush() command to keep the data coming.  It is less than optimal.

We are running Apache2 with PHP 5.3.3.  This particular script takes between 1 and 2 minutes to run.  I am also using error_reporting(-1); and set_time_limit(0); in the file.  The headers are also really weird when no output is displayed:

> 
[http://www.somesite.com/somepath/somefile.php](http://www.somesite.com/somepath/somefile.php)

GET /somepath/somefile.php HTTP/1.1
Host: [www.somesite.com](www.somesite.com)
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.16) Gecko/20110319 Firefox/3.6.16
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive
Cookie: some cookie data
Cache-Control: max-age=0

HTTP/0.9 200 OK

Where as if we use flush() to keep the data coming the headers look like this:

> [http://www.somesite.com/somepath/somefile.php](http://www.somesite.com/somepath/somefile.php)

GET /somepath/somefile.php HTTP/1.1
Host: [www.somesite.com](www.somesite.com)
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.16) Gecko/20110319 Firefox/3.6.16
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 115
Connection: keep-alive
Cookie: some cookie data
Cache-Control: max-age=0

HTTP/1.1 200 OK
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Content-Encoding: gzip
Content-Type: text/html
Date: Fri, 29 Apr 2011 20:03:14 GMT
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Pragma: no-cache
Server: Apache/2.2.16 (Ubuntu)
Vary: Accept-Encoding
X-Powered-By: PHP/5.3.3-1ubuntu9.3
Transfer-Encoding: chunked
Connection: keep-alive

We didn't have these issues on our last server, and I haven't ever run in to this problem.  How do we fix it?  Thoughts?

---

### Post by Ryan Dwyer on 2011-04-30
What's in /var/log/apache2/error.log?

---

### Post by rage9 on 2011-04-30
> **Ryan Dwyer said:**
> What's in /var/log/apache2/error.log?

There are no errors after the 24th even and we've been having these issue.  We've not found anything in the error logs that relate to any scripts we are having issues with, which is why this is so weird!

---

### Post by rage9 on 2011-04-30
After some digging seems related to this:

[http://forums.mozillazine.org/viewtopic.php?f=38&t=1121915](http://forums.mozillazine.org/viewtopic.php?f=38&t=1121915)

Basically you have trailing spaces or the likes after all your content has been generated and it screws up the browsers and they don't actually notice the headers.

---

