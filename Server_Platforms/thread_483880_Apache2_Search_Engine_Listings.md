---
title: "Apache2 Search Engine Listings"
date: 2007-06-25
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-06-25
Hey all,

I'm running an Apache2 server in my office to host a 'phpbb portal' that we use for fun stuff internally, and more recently I've set it up for external access also.

I'm also hosting a friends website on the same machine.

The question is how do I stop search engines from indexing the portal site, but not the site of my mates?

Is there something that I can add to the virtual host directive's per site to tell search engines to lay off indexing sites that are more private?

Thanks :)

---

### Post by whitingx on 2007-06-25
You can use a robots.txt file;

[http://www.searchtools.com/robots/robots-txt.html]("http://www.searchtools.com/robots/robots-txt.html")

Hope this helps.

---

### Post by a.d.gardiner on 2007-06-25
Thanks for your help matey.

Quick question, I'm a little unclear from the documentation I can find, do I need to duplicate this file one for each virtual host on the apache2 or just one file for the whole server which sits in /var/www/?

;)

---

### Post by whitingx on 2007-06-26
You'll need to place a robots.txt file in the DocumentRoot of each virtualhost.

Hope this helps.

---

### Post by a.d.gardiner on 2007-06-26
Many thanks :)

---

