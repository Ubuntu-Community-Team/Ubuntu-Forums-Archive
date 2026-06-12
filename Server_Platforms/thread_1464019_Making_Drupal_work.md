---
title: "Making Drupal work"
date: 2010-04-27
forum: Server Platforms
---

### Post by JKyleOKC on 2010-04-27
I'm setting up a small demonstration website for a non-profit group of which I'm a director, and doing it all in Hardy. I've got Apache2, PHP5, MySQL, and various MySQL admin tools installed with no problems and can navigate the site nicely. However, all its pages are copies of the group's existing site that was built with NetObjects Fusion on a Windows server, and I simply used wget to copy them down to my demo system.

Now I want to include a simple CMS so that a not-tech-savvy webmaster can maintain the site, so I've installed Drupal from the repositories. Upon attempting to follow a tutorial that I found, by entering "httx://localhost/drupal5" into my Netscape browser, all I get is a long list of error messages telling me that the "drupal5" database doesn't contain any of the tables that the program requires in order to run!

My question is simple: How do I bootstrap those tables into the MySQL database? My feeling is that for some reason they should have been initially created by Synaptic's rear-end processes, but were not. Checking MySQL via phpmyadmin confirms that the database contains no tables at all. So what's next?

---

### Post by JKyleOKC on 2010-04-28
Found the answer: run the installmysql.inc file through the browser; all is now working and all I have to do is figure out the rather arcane approach that this package uses :)

---

### Post by isbiyanto on 2010-05-06
> **JKyleOKC said:**
> Found the answer: run the installmysql.inc file through the browser; all is now working and all I have to do is figure out the rather arcane approach that this package uses :)

nice info, thanks

---

