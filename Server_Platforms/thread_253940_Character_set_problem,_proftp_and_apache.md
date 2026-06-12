---
title: "Character set problem, proftp and apache"
date: 2006-09-09
forum: Server Platforms
---

### Post by [h2o] on 2006-09-09
Hi!

I recently upgraded my webbserver from Gentoo to Ubuntu Server 6.06. The installation was a breeze, but I'm experiencing some problems with my charsets.
MySQL is properly installed to show UTF-8, but some old pagesare all encoded as iso-8859-1, and thus they show strange signs (as apache is set to display utf-8 as default). This wouldn't be a problem unless I have pages that mix "HTML" with output from MySQL, so just setting the HTML charset to iso-8859-1 will not help me.

I know I can write a script to convert a large batch of files to utf-8 so that is no problem, but what really bugs me is that all new files that are uploaded to the server from users with iso-8859-1 coding (i.e all Windows users, which is the largest group of users) keep their original file format.
Is there a way to tell proftpd to automatically convert all incoming non UTF-8 text-files (as in sent as text and not binary) to UTF-8?
This would really solve a lot of troubles for me.

Thanks for listening!

---

