---
title: "Can FreeNAS also run as an rtorrent slave?"
date: 2008-12-21
forum: Server Platforms
---

### Post by handy on 2008-12-21
Hi, is it possible to use FreeNAS to control a NAS box & also use the box as an rtorrent slave?

Will FreeNAS allow rtorrent to be installed on it?

I'd be happy to only have to run one box instead of two for those two jobs.

If I have 2 boxes the rtorrent slave would be storing the download on the NAS box, which is a waste of resources.

See here for details of setting up an rtorrent slave:

***_[http://kmandla.wordpress.com/2008/08/04/case-in-point-an-rtorrent-slave-setup/](http://kmandla.wordpress.com/2008/08/04/case-in-point-an-rtorrent-slave-setup/)_***

---

### Post by handy on 2008-12-21
I found this Chinese site on the web, which has instructions for installing rtorrent on FreeNAS.

Due to the language being interpreted it is quite possible that there are errors in the code, which is a worry.

Anyway I'll keep looking, as this site confirms that it is possible to do:

***_[http://bbs.m0n0china.org/viewthread.php?tid=10850](http://bbs.m0n0china.org/viewthread.php?tid=10850)_***

Just found this page regarding a web based torrent client for FreeNAS:

***_[http://sourceforge.net/forum/forum.php?thread_id=1953847&forum_id=507589](http://sourceforge.net/forum/forum.php?thread_id=1953847&forum_id=507589)_***

---

### Post by handy on 2008-12-21
OK, I have learned a lot by reading the last link in my previous thread (actually I still haven't finished reading it, it is huge).

The Transmission torrent client is included these days in FreeNAS, & it has a Web GUI.

I'll continue reading & see what else I can find out.

---

### Post by handy on 2008-12-22
It looks like using Transmission is the easy way to go, even though Transmission doesn't have all of the features that rtorrent has, Transmission is in constant development, so the general consensus is that it is only a matter of time.

There are instructions in the [***_Sourceforge FreeNAS Open Discussion_***]("http://sourceforge.net/forum/forum.php?thread_id=1953847&forum_id=507589") for installing rtorrent, though I would not call them complete, there is also instructions for installing MLDonkey which do look to be complete.

---

### Post by windependence on 2008-12-22
Since FreeNAS runs on FreeBSD, I don't see any reason you couldn't install rtorrent from the ports collection for FreeBSD. 

For more detailed instructions, you can ask here in [www.daemonforums.org](www.daemonforums.org). This is a great BSD board.

-Tim

---

### Post by handy on 2008-12-22
> **windependence said:**
> Since FreeNAS runs on FreeBSD, I don't see any reason you couldn't install rtorrent from the ports collection for FreeBSD. 

For more detailed instructions, you can ask here in [www.daemonforums.org](www.daemonforums.org). This is a great BSD board.

-Tim

What I read in the open discussion page had usage of rtorrent via ssh, where to me (not that I have used rtorrent yet) it's the ability to have rtorrent on a server & have a network shared folder on that server accessible from a client, which rtorrent watches &  automatically starts downloading any .torrent files that have been dropped in it, & automatically ceases downloading .torrent files that get deleted from  the watched folder.

This is something that Transmission is not capable of as yet.

---

