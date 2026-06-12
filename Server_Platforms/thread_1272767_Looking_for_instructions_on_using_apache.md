---
title: "Looking for instructions on using apache"
date: 2009-09-22
forum: Server Platforms
---

### Post by slvfx on 2009-09-22
Looking for instructions on using apache to host a website. I have installed apache2 with lamp. Does anyone have a link for using with ubuntu.

Thanks in advance

---

### Post by HarrisonNapper on 2009-09-22
Here are instructions for downloading the repos and packages:

[https://wiki.ubuntu.com/Ubuntu-with-Firebird-Database](https://wiki.ubuntu.com/Ubuntu-with-Firebird-Database)

[http://ubuntuforums.org/showthread.php?t=1111873&highlight=host+website](http://ubuntuforums.org/showthread.php?t=1111873&highlight=host+website)

That should get you started. Happy hosting!

---

### Post by A_Fiachra on 2009-09-22
The Apache project's documentation is ... **thorough**

[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

the most important trick I learned when developing is :

```

tail -f error.log

```

I usually keep a terminal window open and looking at the error and access logs.

I also use wget a lot!!!

```

wget -O something_that_should_work.html -d -v http://localhost/path/to/some/script

```

wget will print errors to stdout as well as useful information on the request and response (when -d and -v flags are used).

The Apache.org docs also carefully explain setting up virtual servers which one would need if running a true LAMP stack (Python, Perl, or PHP).

Remember always to restart apache after making a change to the apache.conf!!!


HTH

---

### Post by hessiess on 2009-09-22
Apache is a very complicated program and takes a lot of time to learn. Read the manual linked to above and experiment creating configurations for different situations (single user server, multi user server, perl, PHP, Secure CGI etc)

---

### Post by Iowan on 2009-09-22
There's a starter page [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

