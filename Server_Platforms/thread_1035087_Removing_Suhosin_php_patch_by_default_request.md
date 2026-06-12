---
title: "Removing Suhosin php patch by default request"
date: 2009-01-09
forum: Server Platforms
---

### Post by johnwards on 2009-01-09
I would like to know how to request to the server team how to remove the Suhosin patch from the default php installation. 

Or at least let people apt-get remove it if they want.

Where do I submit this? 

I would also like to understand the reasoning behind it, especially as Suhosin hasn't been updated for 2 years and it is effecting perfectly secure applications.

Having to recompile debs to do this is mental. I thought that is what package management is meant to avoid.

See this thread:

[http://ubuntuforums.org/showthread.php?t=698306](http://ubuntuforums.org/showthread.php?t=698306)

And this blog
[http://ambitonline.com/nextrelease/archives/113-How-to-Ubuntu-PHP-Remove-Suhosin.html](http://ambitonline.com/nextrelease/archives/113-How-to-Ubuntu-PHP-Remove-Suhosin.html)

---

### Post by johnwards on 2009-01-09
I have filled a bug report on this.

Dunno if that was the right place!

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/315507](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/315507)

---

### Post by cdenley on 2009-01-09
> **johnwards said:**
> I have filled a bug report on this.

Dunno if that was the right place!

How about posting a link to that bug report?

---

### Post by tubezninja on 2009-01-09
> **johnwards said:**
> I have filled a bug report on this.

Dunno if that was the right place!


Thank you for this.  IF the developers really think Suhosin patch is necessary, that's all fine and good, but at the very least there needs to be an option for those of us who know what it is and have a reason NOT to use it to opt out.

And yes, I could compile php on my own.  I could also not use ubuntu at all.  As stated before, use of the packages and configurability through that method is WHY some us use ubuntu for our servers, and it would be nice if this particular choice wasn't forced on us.

Anyway, +1 on the bug link.  If you could post it here, I could put my 2 cents in. :D

---

### Post by johnwards on 2009-01-10
I'm on my phone at the mo so copy and paste is hard.

I've linked to the bug report in a comment i have left in the blog post linked to in the original thread.

If someone could kindly put the link up that would be great. If not i'll do it on monday.

---

### Post by johnwards on 2009-01-12
As promised, here is the link

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/315507](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/315507)

---

### Post by yngens on 2012-04-05
I've hit the same wall - having lot's of issues with Suhosin, can't remove it, can't betray Ubuntu by changing it to some other distros like CentOS. Deadend :(

---

