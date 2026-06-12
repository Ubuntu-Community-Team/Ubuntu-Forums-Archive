---
title: "Apache / localhost update question"
date: 2009-06-03
forum: Server Platforms
---

### Post by steinaro on 2009-06-03
Hello Fellow Ubuntutrians,
I am working on making a web page. I have apache2 installed and am using php5. I have written a few html and php files for the first few pages of my website and placed them neatly under /var/www so that when I enter localhost in Firefox the pages load very nicely and look very good I might add.

My problem: when I change something in one of the files in /var/www to make a small change on my webpages (you know, I am debugging stuff) the changes don't show up right away in the browser. What can I do? I am guessing that apache has the old files stored to memory or something. How might I see the changes right away when I reload the page?

---

### Post by bryder on 2009-06-03
Are you sure it's not your browser that is caching the files? You might try clearing your browser cache and then try loading the file again to see if it still loads the old page. I use the Firefox plug in called "Web Developer" to quickly manage this sort of thing.

---

### Post by steinaro on 2009-06-03
YES... You are right. Thank you so much!

---

