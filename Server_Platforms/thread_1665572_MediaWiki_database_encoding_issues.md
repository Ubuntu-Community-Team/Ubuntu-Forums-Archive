---
title: "MediaWiki database encoding issues"
date: 2011-01-12
forum: Server Platforms
---

### Post by pytheas22 on 2011-01-12
This query isn't Ubuntu-specific, but I thought I'd ask here before going over to the MediaWiki forums...

I recently upgraded a MediaWiki installation from version 1.8.2 to version 1.16.0.  I left the MySQL database for the wiki in place, and the Web-based installer for MediaWiki recognized it without a problem.  The installation went smoothly and there were no complaints about database issues or anything else.

After the wiki upgrade, however, I found that all page titles on my wiki which contain special, non-English characters had become corrupted.  For example, a page titled "Histoire des troupes étrangères" became "Histoire des troupes Ã©trangÃ¨res"

Interestingly, none of the text within pages themselves was corrupted, even where special characters appear.  It's only the page titles that seem to have issues.

I assume this an encoding problem, but it seems bizarre to me because there was no dump of the database involved in the upgrade.  I simply upgraded the MediaWiki software and left the database tables "in place."  So it's not clear to me how the text in the page titles would have become corrupted, if the database itself was not dumped out and imported back in.

That said, my understanding of encoding-related issues and MySQL is only basic, so I may be missing something.  I'd be very grateful for any help pointing me in the right direction.

---

### Post by pytheas22 on 2011-01-12
I figured out a solution, although I'm still not positive what went wrong.  I found that reinstalling MediaWiki, while again leaving the database in place, worked, as long as I chose the option "MYSQL 4.0 backwards-compatible UTF-8" in the database character set section of the installation page (previously I'd been choosing the default option for this part, which I think is to use binary encoding).  After the reinstallation my page titles are no longer corrupted.

It's still not clear what went wrong originally, however, because my MySQL installation is (and as far as I know always has been, since the wiki was created) version 5.1, and the database's default character set is utf-8.  So I'm not sure why backwards compatibility with MySQL 4.0 would have factored in.

---

