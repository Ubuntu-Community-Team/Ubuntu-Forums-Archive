---
title: "Announcing Collectl - a performance monitor like no other"
date: 2008-06-12
forum: Server Platforms
---

### Post by markseger on 2008-06-12
I'm new to this forum and wanted to take a minute to introduce folks to a performance monitoring tool I developed almost 5 years ago and released to the open source community about a year ago.  It combines the best of a lot of existing tools and adds additional features I've yet to see in others such as monitoring for Slabs, Infiniband, Quadrics, Lustre and Interrupts by CPU just to mention a few.  Today I released a new version that also lets you watch your top processes sorted by I/O use.

The key point is while a lot of tools can do a lot of these, none of them can do all it it and present the results in an integrated format.  But don't take my word for it, check out [http://collectl.sourceforge.net/](http://collectl.sourceforge.net/).  There is a page that lists collectl's features and in the documentation section I've tried to include a lot of examples and details on specific components like interrupt or process monitoring.

But one of the more important reasons for posting this note is to get more feedback from the Ubuntu community since I really haven't done much with this distro and I want to make sure collectl meets the community's needs.  So by all means kick the tires and let me know what you think.

-mark

---

### Post by surisaabh on 2009-01-09
The tool is very good and provides a lot of information about the system.The amount of information it provides sometimes becomes difficult to comprehend.The collectl commands output **columns with abbrevations** are difficult to understand.Request you to please provide some info or documents to help me understand(comprehend) the output.

---

### Post by markseger on 2009-03-13
re column headings - sorry for the last reply, I just saw this.

I guess I've been looking at them so long it never occurred to me they may not all be obvious.  I think I did an ok job of documenting them in - [http://collectl.sourceforge.net/Data.html](http://collectl.sourceforge.net/Data.html) having chosen a separate section for each of the 3 main types of data.  If any definitions could be improved, and I'm sure many could, I'll be happy to incorporate any that do a better job.

As a side note, I just released a new version on sourceforge.  The 2 biggies here are NFS V4, something I'd been wanting to do for awhile and just couldn't find the time.  The other was adding support for /proc/buddyinfo.  Every wonder just how fragmented you memory really is?  I'm still not sure how useful this sort of data is, but perhaps better definitions could help.

I guess saying what something means is one thing, trying to understand what normal values are, especially in the context of others, is real hard to describe, let alone how to react to.

-mark

---

