---
title: "[SOLVED] Apache Web Server Help"
date: 2008-05-11
forum: Server Platforms
---

### Post by napoli3 on 2008-05-11
I have set up my first web server with everything working on a fresh install of Ubuntu Server 8.04.  I must be missing something because although I can access my website from both my network and from the outside, entering the domain for the website only brings up the "Index of/" with the two files I have on the server.  How do I get Apache to serve up the html file rather than the Index of/?  :confused:

---

### Post by windependence on 2008-05-11
> **napoli3 said:**
> I have set up my first web server with everything working on a fresh install of Ubuntu Server 8.04.  I must be missing something because although I can access my website from both my network and from the outside, entering the domain for the website only brings up the "Index of/" with the two files I have on the server.  How do I get Apache to serve up the html file rather than the Index of/?  :confused:

Do you have an index.html or index.php page?

-Tim

---

### Post by napoli3 on 2008-05-11
> **windependence said:**
> Do you have an index.html or index.php page?

-Tim

Solved.....

I guess I just needed to play with the configuration settings a bit more.

---

### Post by Dr Small on 2008-05-11
Ok. I am confused. Let's sort things to the bottom before we move on.
What is displayed from localhost, or when you access your webserver from on the network? What page is displayed?

Now, when accessing it from your domain, what is being displayed?
Also, what are these two files that you have? Is one of them an index file?

Dr Small

---

