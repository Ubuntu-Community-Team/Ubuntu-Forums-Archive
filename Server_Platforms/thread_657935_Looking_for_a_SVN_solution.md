---
title: "Looking for a SVN solution"
date: 2008-01-04
forum: Server Platforms
---

### Post by Dudsmacka2 on 2008-01-04
I am looking to build a SVN server, to ease my web development.

I'm looking to build a LAMP server, in which apache could access SVN projects.

For example, if I am working on a website, I would like to be able to test it via [http://w.x.y.z/projectName](http://w.x.y.z/projectName).  I would like projectName to be a project inside of SVN.  Is this possible?

---

### Post by Maxtorm on 2008-01-04
It is definitely possible. When I set mine up, I found a few good pages online, but this one seemed to be the most comprehensive: [http://gentoo-wiki.com/HOWTO_Apache2_with_subversion_SVN_and_DAV](http://gentoo-wiki.com/HOWTO_Apache2_with_subversion_SVN_and_DAV)

---

### Post by Dudsmacka2 on 2008-01-04
From what I've read that solution is more for using Apache 2 as authentication, rather than testing a live site.

I ran across the following link, which is more what I was looking for:
[http://subversion.tigris.org/faq.html#website-auto-update](http://subversion.tigris.org/faq.html#website-auto-update)

thanks!

---

### Post by Maxtorm on 2008-01-04
I'm not sure if it is the exact same setup as mine, but it will be close. One hint, for what its worth: When you get to the point where you have a functioning SVN repository under the live site pages, it will appear as though changes you make in SVN are not reflected in the live site. This, of course, is be design since changes are not committed to the live tree until you explicitly export them. The trick was to create a post-commit script that automatically exported the HEAD of the repository after each commit. Perhaps not as elegant as it could be, but it worked. And if you are developing alone or with a small group, you will likely find the solution works just fine.

---

