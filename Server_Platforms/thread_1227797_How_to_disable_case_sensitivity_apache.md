---
title: "How to disable case sensitivity apache"
date: 2009-07-31
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2009-07-31
I saw this thread and they had a solution [http://bytes.com/topic/apache/answers/608164-apache-case-sensitive-urls](http://bytes.com/topic/apache/answers/608164-apache-case-sensitive-urls)

But I don't understand how to use this solution...
They mentioned this
Did you enable mod_speling with directive CheckSpelling on in Apache configuration file?

Then the other guy replied with CheckSpelling on

Worked for me :D thanks buddy

---------
How do I do this? I am in /etc/apache2 but what files do I change? Also I saw this [http://httpd.apache.org/docs/1.3/mod/mod_speling.html](http://httpd.apache.org/docs/1.3/mod/mod_speling.html)

---

### Post by JigglyWiggly_ on 2009-07-31
fixed I just saw this [http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/](http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/)

---

### Post by wojox on 2009-07-31
LAMP doesn't ship with mod_speling. If greatly reduces the time it takes to load pages. You would have to go download it from apache. Why do you want that anyhow? Your scripts would be better of written without it.

---

### Post by JigglyWiggly_ on 2009-07-31
> **wojox said:**
> LAMP doesn't ship with mod_speling. If greatly reduces the time it takes to load pages. You would have to go download it from apache. Why do you want that anyhow? Your scripts would be better of written without it.

Reason I needed this is was because I host a garrysmod server and the http server can't be case sensitive. Because garrysmod is poorly made, and some of the files have case sensitive letters, yet garrysmod always sends the requests to the download server as lower case...

---

