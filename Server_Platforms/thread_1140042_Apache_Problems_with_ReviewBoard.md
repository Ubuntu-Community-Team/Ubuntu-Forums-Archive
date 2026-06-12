---
title: "Apache Problems with ReviewBoard"
date: 2009-04-27
forum: Server Platforms
---

### Post by gogo809 on 2009-04-27
At work we are trying to check out [ReviewBoard]("http://www.review-board.org/") to see what we think. I got through the nightmare of an installation only to run into issues with the webserver portion. Anyone that knows alot about apache2 can help.

ReviewBoard admits there is a problem if you have the "default site" enabled on Ubuntu, and they recommend disabling it to get reviewboard to function. ([http://www.review-board.org/docs/manual/dev/admin/sites/creating-sites/#creatingsites](http://www.review-board.org/docs/manual/dev/admin/sites/creating-sites/#creatingsites)   "Note" at the bottom) The problem we have with this approach is we also use Trac and Subversion. They use the default site to load. defaultsite/Trac and defaultsite/Subversion. In a browser we access it like [http://LocalServerName/Trac](http://LocalServerName/Trac), [http://LocalServerName/svn](http://LocalServerName/svn). Reveiwboard I think tries to reinvent the wheel and specifies ```
/var/www
``` as the "document root" just like the default site. (Is it important that Trac and Reviewboard both use python?)

I don't know if I know what to ask here, seems like there should be multiple solutions, so if you have any recommendations, I am all ears. Thanks in advance!!

**Server details**: Ubuntu Server 8.10 (Intrepid) Intel based

**ReviewBoard config**:
[LIST]
[*]Python 2.5
[*]memcache
[*]PyLucene 2.4.0.2
[*]JCC
[*]Java6
[*]MySQL
[*]Apache2
[/LIST]
ReviewBoard install instructions: [http://www.review-board.org/docs/manual/dev/admin/installation/linux/#installing-pylucene](http://www.review-board.org/docs/manual/dev/admin/installation/linux/#installing-pylucene)

---

### Post by BbUiDgZ on 2010-07-06
I also run reviewboard and have the same issue, although mine is with reviewboard/phpmyadmin on debian lenny, sorry i have no solution for you but just thought i'd add to he topic.

A reviewboard support forum would be nice ;)

did you get the search feature to work?

---

### Post by gogo809 on 2010-10-21
We just couldn't get going with reviewboard. We looked at several review software, and went with the one we liked the best. We ended up with Crucible + Fisheye by Atlassian. It works, offered the fewest steps to create a review, and it completely integrates with SVN. The Fisheye stuff is what allows for 1 click reviews. There is NOT a great way to do re-reviews. You have to basically create a new review and link it to the old one.

---

