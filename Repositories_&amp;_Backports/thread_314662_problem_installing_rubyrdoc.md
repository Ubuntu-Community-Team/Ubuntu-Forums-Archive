---
title: "problem installing ruby/rdoc"
date: 2006-12-07
forum: Repositories &amp; Backports
---

### Post by rpm13 on 2006-12-07
I am trying to install rubyand rails on my dapper ubuntu box.
I was getting some problems which I narrowed down to rdoc.

This is the output of choosing rdoc1.8 in synatptic as well as apt-get install rdoc1.8.
--------------------


The following packages have unmet dependencies:
  rdoc1.8: Depends: ruby1.8 (>= 1.8.4-1ubuntu1.2) but it is not going to be installed
           Depends: irb1.8 (>= 1.8.4-1ubuntu1.2) but it is not going to be installed
           Depends: libruby1.8 (>= 1.8.4-1ubuntu1.2) but 1.8.4-1ubuntu1 is to be installed
E: Broken packages

---

