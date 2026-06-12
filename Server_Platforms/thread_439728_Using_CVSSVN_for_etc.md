---
title: "Using CVS/SVN for /etc"
date: 2007-05-11
forum: Server Platforms
---

### Post by mvip on 2007-05-11
Today I read an interesting article about how it would be beneficial to use a different filesystem for /etc. The article brought up two different ideas that would enable the use of CVS/SVN for /etc. Using a repository system would make it much easier to track and locate changes made to the server over time.

Check out the article at [http://www.playingwithwire.com/2007/05/etc-deserves-its-own-filesystem/](http://www.playingwithwire.com/2007/05/etc-deserves-its-own-filesystem/)
I think it brings up an interesting point. What do you guys think? Is it a reasonable approach?

---

### Post by craigp84 on 2007-05-11
<$0.02>

Hmmm. This is really environment specific, your solution is probably going to be vastly different at a site with a few thousand nodes compared to a 3 server SMB.

For me, all changes are recorded elsewhere anyway, so this would be a bit overkill.

I do however have rsnapshot running across all nodes in production, a simple "cd /.snapshot/etc/<hourly|daily|weekly|monthly>.<0|1|2|3>" will take me back to a previous view of etc and i can diff against current /etc.

I think it's easier to have my changes logged with the business request that requires the change (normally in my ticket queue) - then everything's in one place, and the rsnapshot is purely a convenience.

Whatever floats your boat.

</$0.02>

---

### Post by mvip on 2007-05-11
Valid point. If you're administrating thousands of nodes, you're unlikely to find this solution to be the most optimal. I would imagine that it is suitable for <50 or so servers. 

Interesting idea about using snapshot though.

---

