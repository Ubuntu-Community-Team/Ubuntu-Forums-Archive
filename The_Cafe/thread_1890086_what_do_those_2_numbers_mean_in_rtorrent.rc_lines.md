---
title: "what do those 2 numbers mean in rtorrent.rc lines"
date: 2011-12-02
forum: The Cafe
---

### Post by kossatzd on 2011-12-02
schedule = watch_directory,1,1, ...
schedule = tied_directory,10,10, ...
schedule = low_diskspace,5,60, ...

I looked everywhere and can't find an explanation of what those 2 numbers mean in the rtorrent.rc file.

I figured it was how often it checks....but why two?

---

### Post by CharlesA on 2011-12-02
Just how it is.

See here:
[http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc#latest](http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc#latest)

---

### Post by marshmallow1304 on 2011-12-02
From the man page:
[quote=man rtorrent]schedule = id,start,interval,command
              Call command every interval seconds,  starting  from  start.  An
              interval  of  zero  calls  the  task once, while a start of zero
              calls it immediately. Currently  command  is  forwarded  to  the
              option  handler.   start  and interval may optionally use a time
              format, dd:hh:mm:ss. F.ex to start a task every  day  at  18:00,
              use 18:00:00,24:00:00.
[/quote]

---

