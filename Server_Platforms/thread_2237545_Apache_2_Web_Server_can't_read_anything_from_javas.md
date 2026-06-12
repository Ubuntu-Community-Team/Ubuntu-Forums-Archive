---
title: "Apache 2 Web Server can't read anything from javascript directory!"
date: 2014-08-02
forum: Server Platforms
---

### Post by Luft on 2014-08-02
This is a strange one!  I have a website that uses javascript code.  The code is in a sub directory called javascript.  Everything WAS working fine, then one day it all stopped working.  I was getting 404 errors any time I tried to read anything from that directory.  I checked the folder permissions and they appear to be the same as all of the other directories.  I checked the file permissions and they appear to be the same as all of the other file permissions.

My access.log isn't much help:
 192.168.1.7 - - [01/Aug/2014:20:25:48 -0700] "GET /javascript/sideBar.js HTTP/1.1" 404 512 "-" "Mozilla/5.0 (Windows NT 6.3; rv:31.0) Gecko/20100101 Firefox/31.0"

I have double, triple, quadruple checked the spelling of the directory and file name.  I am really out of trouble shooting ideas.  My site is working again because I created a new directory and moved the javascript file and changed the references but I want to understand what's going on here.

I can't pull the javascript file via a direct url: i.e. [www.stellar-portal.net/javascript/sideBar.js](www.stellar-portal.net/javascript/sideBar.js) yet if I pull it from it's new directory it is fine: [www.stellar-portal.net/Jscript/sideBar.js](www.stellar-portal.net/Jscript/sideBar.js)

I put a simple webpage into the javascript directory and then made a direct request for the page via a url i.e. [www.stellar-portal.net/javascript/test.html](www.stellar-portal.net/javascript/test.html) 

The page was not found.  Same page in a different directory gets served!

Can anyone give me some troubleshooting ideas?

Thanks.

---

### Post by Doug S on 2014-08-02
What does the error.log say? It gives the entire path to the file name with respect to the computer file system, not the apache web docroot system. Example:```
doug@doug-64:~$ [COLOR=#ff0000]tail -2 /var/log/apache2/error.log[/COLOR]
[Sat Aug 02 12:09:24 2014] [error] [client 81.229.X.XXX] File does not exist: /home/doug/public_html/linux/ubuntu-docs/help.ubuntu.com/new/14.04/ubuntu-help/sharing-remote-login.html
[Sat Aug 02 12:56:05 2014] [error] [client 174.71.54.240] File does not exist: /var/www/browserconfig.xml

doug@doug-64:~$ [COLOR=#ff0000]tail -70 /var/log/apache2/access.log (edited)[/COLOR]
81.229.X.XXX - - [02/Aug/2014:12:09:24 -0700] "GET /~doug/linux/ubuntu-docs/help.ubuntu.com/new/14.04/ubuntu-help/sharing-remote-login.html HTTP/1.1" 404 551 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:31.0) Gecko/20100101 Firefox/31.0"

```

---

### Post by Luft on 2014-08-02
That's weird.  I just sent a request that I knew would fail so that I could look into the error log.  That error was not recorded.

Last message in access log:
```

192.168.1.7 - - [02/Aug/2014:16:33:17 -0700] "GET /javascript/sideBar.js HTTP/1.1" 404 522 "-" "Mozilla/5.0 (Windows NT 6.3; rv:31.0) Gecko/20100101 Firefox/31.0"

```

Last message in error.log:
```

[Sat Aug 02 15:41:22.264252 2014] [:error] [pid 2020] [client 192.168.1.15] ModSecurity: Warning. Match of "eq 1" against "&ARGS:CSRF_TOKEN" required. [file "/usr/share/modsecurity-crs/activated_rules/modsecurity_crs_43_csrf_protection.conf"] [line "31"] [id "981143"] [msg "CSRF Attack Detected - Missing CSRF Token."] [hostname "www.stellar-portal.net"] [uri "/roleplaying/namefactory.php"] [unique_id "U91pEn8AAQEAAAfkFjIAAAAB"]

```

Notice the time stamp difference.

---

