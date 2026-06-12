---
title: "Apache 302 requests"
date: 2008-11-25
forum: Security
---

### Post by Blairboy on 2008-11-25
Ok, I'm seeing in my access log that apache is processing all kinds of what look like spam requests.
```
222.93.242.204 - - [25/Nov/2008:18:40:19 -0600] "GET http://www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//media.adrevolver.com/adrevolver/banner?place=31445&cpy=2657941 HTTP/1.0" 302 - "http://www.lqgaming.com/data/3413~adamdavidson.php" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR 3.0.04506)"
222.93.242.204 - - [25/Nov/2008:18:40:21 -0600] "GET http://www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//media.adrevolver.com/adrevolver/banner?place=31445&cpy=222948 HTTP/1.0" 302 - "http://www.lqgaming.com/coh/gallery/album02/screenshot25/index.php" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.11) Gecko/20071127 Firefox/2.0.0.11"
222.93.242.204 - - [25/Nov/2008:18:40:27 -0600] "GET http://www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//www.kincke.com//media.adrevolver.com/adrevolver/banner?place=31445&cpy=2657941 HTTP/1.0" 302 - "http://www.lqgaming.com/data/3413~adamdavidson.php" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR 3.0.04506)"
72.14.199.40 - - [25/Nov/2008:18:40:32 -0600] "GET /?feed=rss2 HTTP/1.1" 304 - "-" "Feedfetcher-Google; (+http://www.google.com/feedfetcher.html; 17 subscribers; feed-id=7109266665264747625)"
```

Am I misreading this?  And if not, any ideas on how to get rid of this issue?

---

### Post by lemming465 on 2008-11-28
Any exposed e-mail or web server is going to be probed by spammers, yes.  This is only a problem if the load from the bogus requests is interfering with the main purpose of the box, or if it's actually emitting spam.

---

### Post by Blairboy on 2008-12-01
Is there any way to block this crap other than entering in ip addresses into .htaccess files?

---

### Post by lemming465 on 2008-12-02
Not really.  You may be able to reduce the risks with things like mod_security.

---

