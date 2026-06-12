---
title: "Approx Cache not Starting"
date: 2009-11-04
forum: Server Platforms
---

### Post by gareththered on 2009-11-04
I've just upgraded my Jaunty server to Karmic and since then the 'approx' package isn't running.  I've seen an identical issue in Karmic Development but that's now closed:-
[http://ubuntuforums.org/showthread.php?t=1301334](http://ubuntuforums.org/showthread.php?t=1301334)
As the original poster said:  Is this a bug?
Basically, 'approx' isn't in /etc/init.d any more but I'm also aware that Karmic has changed the way it starts services.

SORRY!!!

Blonde-moment:  approx uses inetd to start.  I'm sure I checked inetd.conf, but must have missed it the first time!  Oops!

---

