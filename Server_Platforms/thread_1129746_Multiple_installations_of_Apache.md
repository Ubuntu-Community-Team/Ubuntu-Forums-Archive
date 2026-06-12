---
title: "Multiple installations of Apache?"
date: 2009-04-19
forum: Server Platforms
---

### Post by swraman on 2009-04-19
Hi,

I am not sure how I got myself in this situation, but I think I have multiple instances of apache running on my system and I want to get rid of one of them.  But I dont know how to find where the installation is and how to uninstall it.

I have one instance at /usr/local/apache2 which I want to keep.

What makes me think that there are 2 installations of it is this:  When I run "service apache2 start" it starts Apache, and when I go to localhost I am greeted with the default "It Works!" page.

However, none of the other files in /usr/local/apache2/htdocs/index.html are visible (I get file not found error), nor are any changes I make to /usr/local/apache2/htdocs/index.html reflected at [http://localhost](http://localhost).

But, if I "service apache2 stop" then "/usr/local/apache2/bin/apachectl start", the server starts again and [http://localhost](http://localhost) points to /usr/local/apache2/htdocs.

So do you think I have 2 installations of apache, or is there something else going on here?  If I do have 2 installations, how do I find the other one?

Thanks

Raman

---

### Post by c3lica on 2009-04-19
not sure but I think that with a standard install of apache the index file is located at /var/www/ try editing it and puting your files there and see if it works how you want.

---

### Post by swraman on 2009-04-19
Hmm yes, that is where the other htdocs folder is!

But why are there 2 - is there any way to remove one of them?

---

