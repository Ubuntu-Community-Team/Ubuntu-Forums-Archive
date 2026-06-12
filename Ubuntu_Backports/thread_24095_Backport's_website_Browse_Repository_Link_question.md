---
title: "Backport's website Browse Repository Link question"
date: 2005-04-05
forum: Ubuntu Backports
---

### Post by jsradley on 2005-04-05
Is the Backports Browse Repository link at

[http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/)

broken?

It reports for me, "Revision 108" and some directories, and I can see pages from the backport website via directory site.

I can userstand that it might be a way into the version control system, but if I may I'd like to put in a plea for a simple listing so I can see the contents of the repository via a Web page.

Thanks
John

---

### Post by jdong on 2005-04-05
It's a browser to the directory structure of the Subversion repository.

I was investigating some PHP indexers for APT repositories, but they all require a checked-out (exported) copy of the repositories, which takes up an extra 7GB of space.


You can go to the [http://backports.ubuntuforums.org/backports/dists/](http://backports.ubuntuforums.org/backports/dists/) folder to browse for packages.

---

