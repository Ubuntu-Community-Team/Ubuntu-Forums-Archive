---
title: "svn version control"
date: 2007-12-01
forum: The Cafe
---

### Post by PurposeOfReason on 2007-12-01
As I usually always get the newest and best, I never thought I'd had to do this and never read how; so how would I go about checking out an earlier version of something (ttm) through svn?

---

### Post by saulgoode on 2007-12-01
Like you, I have rarely had to do this and so my method may not be optimal. 

I perform a '***svn log | less***' in order to find out the revision number of the version I wish to fetch (I am usually looking for a change which I wish to undo but sometimes it is based upon the date). 

I then checkout that particular revision with '***svn checkout -r ####***'. I have never figured out how to directly replace my current revision with an older one, I have always just checked out a new tree and, if necessary, delete the old one (this is probably not right).


The official Subversion document [is here](http://svnbook.red-bean.com/en/1.4/index.html).

---

