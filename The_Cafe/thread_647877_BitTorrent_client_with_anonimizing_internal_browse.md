---
title: "BitTorrent client with anonimizing internal browser :)"
date: 2007-12-22
forum: The Cafe
---

### Post by markybob on 2007-12-22
Hey all...just thought you might like to know that Deluge's new version, 0.5.8RC1, lets bittorrent users browse torrent sites totally anonimously.  Take that, ISPs trying to track and throttle bittorrent users!!  :)
More information here [http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379](http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379)

---

### Post by bufsabre666 on 2007-12-22
gotta love the deluge

now if only it let americans access torrentspy

---

### Post by vishzilla on 2007-12-22
> **markybob said:**
> Hey all...just thought you might like to know that Deluge's new version, 0.5.8RC1, lets bittorrent users browse torrent sites totally anonimously.  Take that, ISPs trying to track and throttle bittorrent users!!  :)
More information here [http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379](http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379http://forum.deluge-torrent.org/viewtopic.php?f=8&p=4382#p4379)

Excellent! Downloaded it! Keep up the good work! Cheers! :)

---

### Post by Lostincyberspace on 2007-12-22
It is broken for me.

---

### Post by jken146 on 2007-12-22
> **Lostincyberspace said:**
> It is broken for me.

You'll have to give more details than that!

---

### Post by Lostincyberspace on 2007-12-22
> lee@lee-desktop:~$ deluge
checking for ubuntu...
found and fixing ubuntu
checking for ubuntu...
found and fixing ubuntu
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin TorrentCreator
Initialising plugin EventLogging
Initialising plugin NetworkHealth
Initialising plugin WebUi
Initialising plugin TorrentPeers
Initialising plugin WebSeed
Initialising plugin FlexRSS
Initialising plugin SpeedLimiter
Initialising plugin DesiredRatio
Initialising plugin MoveTorrent
Initialising plugin Scheduler
Initialising plugin NetworkGraph
Initialising plugin BlocklistImport
Initialising plugin ExtraStats
Initialising plugin TorrentNotification
Initialising plugin TorrentFiles
Applying preferences
Starting DHT...
No DHT file to resume
Showing window
Loading TorrentFiles plugin...
Loading TorrentPeers plugin...
/usr/lib/python2.5/site-packages/deluge/interface.py:1019: GtkWarning: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed
  gtk.main()
/usr/lib/python2.5/site-packages/deluge/interface.py:1019: GtkWarning: gdk_window_resize: assertion `GDK_IS_WINDOW (window)' failed
  gtk.main()
/usr/lib/python2.5/site-packages/deluge/interface.py:1019: GtkWarning: gdk_window_freeze_toplevel_updates_libgtk_only: assertion `window != NULL' failed
  gtk.main()
/usr/lib/python2.5/site-packages/deluge/interface.py:1019: GtkWarning: gdk_window_invalidate_maybe_recurse: assertion `window != NULL' failed
  gtk.main()
Xlib: unexpected async reply (sequence 0x6e4)!

Really confusing I think I am oing to go and purge it from the system and try it again.

---

### Post by Lostincyberspace on 2007-12-22
It is working now kind of but is still really buggy. Needs a major fix.

---

### Post by markybob on 2007-12-23
> **Lostincyberspace said:**
> It is working now kind of but is still really buggy. Needs a major fix.

again, more information would be great.  saying something doesnt work without giving specifics doesnt help anyone

---

### Post by Polygon on 2007-12-23
yeah svn doesnt work for me either.

> 
mark@Cactus-Fantastico:~/svn/deluge$ deluge
checking for ubuntu...
found and fixing ubuntu
checking for ubuntu...
found and fixing ubuntu
create proxy object
create iface
send to iface
mark@Cactus-Fantastico:~/svn/deluge$ deluge
checking for ubuntu...
found and fixing ubuntu
checking for ubuntu...
found and fixing ubuntu
create proxy object
create iface
send to iface
mark@Cactus-Fantastico:~/svn/deluge$ 


i did do a makeclean right before that and i delete ~/.config/deluge....still no go.l

---

### Post by markybob on 2007-12-23
> **Polygon said:**
> yeah svn doesnt work for me either.



i did do a makeclean right before that and i delete ~/.config/deluge....still no go.l

this means it's already running.  check your system tray.  `ps aux |grep deluge`

---

### Post by smartboyathome on 2007-12-23
Will there/is there a way to start deluge without it being in the system tray? Enlightenment still hasn't built it in. :mad:

---

### Post by Polygon on 2007-12-24
yeah i restarted and it works now. Coolio!

but you say the browser is only allowed to visit torrent sites cause the proxy servers have a whitelist, why then can i still go to other sites? or did you mean that only torrent sites go through the proxy server, and therefore if you visit a non proxy site then your not anonmyous?

---

### Post by phorgan1 on 2008-03-31
I'm having exactly the same problem.  I *did* ps and found that deluge is running but doesn't show up in the tray or elsewhere.

---

