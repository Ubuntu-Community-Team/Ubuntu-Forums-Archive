---
title: "Best way to setup an ebook site"
date: 2013-06-03
forum: Server Platforms
---

### Post by ki4jgt on 2013-06-03
I have an employer who wishes to charge a monthly fee for users to be able to read ebooks (unlimited number of them). The employer has a text format in which the ebook must be submitted to the site, the site will then pick apart the book as the user requests it's individual chapters. I wondered if it would be better to place the books into a MySQL directory (chapter by chapter) and show them to the user that way. The book list could get pretty large so the database itself would get big soon as well. How would I go about a distributed database scheme? We're expecting thousands of books as we will accept user submitted content. The entire site is also running off of python with an Ubuntu server (if that makes any difference).

---

### Post by Cheesehead on 2013-06-03
Seems like the user should have a local client, to track the current books/chapters, hold bookmarks, download the next, update account information, etc.
That client should be in charge of "showing" titles and handling the user's search/browse input and translating that into your server SQL search.

Are you only doing the database? Or are you involved with the larger customer activity flow design?

---

### Post by tgalati4 on 2013-06-03
I would look at [http://drupal.org](http://drupal.org) or another content management system (CMS).  There are several plug-ins to drupal for e-commerce and it uses mysql or PostgreSQL so it will scale as your book collection grows.

---

### Post by SeijiSensei on 2013-06-04
I generally prefer to let the operating system manage file storage and just place URIs in the database.  I don't see any gains to putting the books themselves into the database.

---

### Post by gordintoronto on 2013-06-04
Excellent thought! That way a book probably takes, I dunno, maybe 10 KB of space in the database. A million books, 10 GB.

You certainly don't want a single folder containing all the chapters of all the books. Even advanced files systems bog down at some point.

---

