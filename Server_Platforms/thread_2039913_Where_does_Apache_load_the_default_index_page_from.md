---
title: "Where does Apache load the default index page from?"
date: 2012-08-09
forum: Server Platforms
---

### Post by Maheriano on 2012-08-09
I loaded my website's files to my new server and changed the index.html page to index.html.bak so it would load the index.php page by default instead. Somehow it's still loading the generic "It Works!" page instead of the one I want. When I go to index.php specifically it works great, how do I get it to load this by default?

---

### Post by kennethconn on 2012-08-09
Sounds like a caching issue on client side.

---

### Post by Maheriano on 2012-08-09
How do I fix that? I have SSH access to the server.

---

### Post by Doug S on 2012-08-09
I think what kennethconn was suggesting was to refresh the page from the client web browser. Forcing a re-load (refresh) would flush the local cache of the page.

---

### Post by Maheriano on 2012-08-09
Oh, client, right. No, I tried refreshing my web browser many times, it keeps loading the default "It Works!" page.

---

### Post by LHammonds on 2012-08-09
> **Maheriano said:**
> Where does Apache load the default index page from?
[Apache Configuration Dox](https://help.ubuntu.com/12.04/serverguide/httpd.html#http-configuration) - Pay particular attention to your "sites-available" directive.

---

### Post by Maheriano on 2012-08-09
> **LHammonds said:**
> [Apache Configuration Dox](https://help.ubuntu.com/12.04/serverguide/httpd.html#http-configuration) - Pay particular attention to your "sites-available" directive.
Thanks, I fixed it using this. I opened up /etc/apache2/mods-enabled/dir.conf which originally had the following line in it:
```
index.html index.cgi index.pl index.php index.xhtml index.htm
``` and changed it to ```
index.php index.html index.cgi index.pl index.xhtml index.htm
``` to put the "index.php" in front so it gets loaded first. When no specific file name is given, it will load any found files in the order they appear there. Not sure if I needed to but I ran```
sudo service apache2 reload
```just in case.

---

### Post by kennethconn on 2012-08-10
Odd that, seeing as how you renamed it to index.html.bak (which is why I thought it was a caching issue on client).
 
Glad it got sorted.

---

