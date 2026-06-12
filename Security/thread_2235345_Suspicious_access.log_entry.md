---
title: "Suspicious access.log entry"
date: 2014-07-20
forum: Security
---

### Post by Luft on 2014-07-20
I noticed this in my apache2 access.log:
162.243.28.237 - - [19/Jul/2014:23:50:29 -0700] "GET / HTTP/1.1" 200 2284 "-" "curl/7.35.0"
104.131.244.31 - - [20/Jul/2014:00:54:56 -0700] "GET / HTTP/1.1" 200 2284 "-" "curl/7.35.0"

I googled "curl/7.35.0" and it appears that Curl is a command line tool used to transfer data.  What bothers me is that the log entry has a code of 200  ie OK!

Does anyone know what these people are trying to do?
 
This library is outside of the Document root so how can a hacker get access to it?

I have removed the curl libaries.  Does anyone know an attack vector using this library?  What more should I do to stop this threat?

---

### Post by Lars Noodén on 2014-07-20
The last column is the browser's identification string.  It's what the browser calls itself when it connects to your server.  Someone used curl to get your homepage.  See the "combined" log format, which is one pre-defined log format:

[http://httpd.apache.org/docs/2.2/logs.html#accesslog](http://httpd.apache.org/docs/2.2/logs.html#accesslog)

Try getting your homepage with wget, it's included by default in Ubuntu, and you will see wget's default identification string in your logs, too.  You can use [-U or --user-agent](http://manpages.ubuntu.com/manpages/trusty/en/man1/wget.1.html) to set it to something else.

---

### Post by Lars Noodén on 2014-07-20
This link might be a little hard to find.  It explains the log file formats used in [LogFormat](http://httpd.apache.org/docs/2.4/mod/mod_log_config.html#logformat):

[http://httpd.apache.org/docs/2.4/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/2.4/mod/mod_log_config.html#formats)

---

### Post by ubudog on 2014-07-20
The same thing happens when you visit your homepage with a web browser.  It sends a GET request to the server.  Someone just used curl to do it.  Try running:
```
curl yoursite.com
```

And you will get the same thing those people got.

---

### Post by TheFu on 2014-07-23
Relax. This isn't anything bad or abusive, unless they are doing it constantly every second.  Once a day, heck, I'd love to have 20,000 people do that for my blog.  Curl is just a CLI http tool. It is probably someone just pulling your home page daily. I wouldn't worry at all.

By removing the curl libraries on your system, you've probably broken a few tools you will miss. Just sayin'.

---

### Post by Habitual on 2014-07-23
> **Luft said:**
> What more should I do to stop this threat? First Off, until you're certain it ***is*** a "threat (it isn't), STOP REMOVING STUFF from the system.

curl yoursite.com in one terminal tab|window and watch the remote log simultaneously in another tab|window. You'll 'see'.
Nothing nefarious and all _quite common_.

And since I'm scolding you... since you removed the curl libraries from the host, did the log entries stop? I very much doubt it.

Good Luck!

---

