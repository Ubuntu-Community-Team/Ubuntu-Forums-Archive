---
title: "pyogg and pyvorbis not updated in Dapper?"
date: 2006-11-20
forum: Repositories &amp; Backports
---

### Post by metafile on 2006-11-20
Hi there.
I`m trying to install the latest version of [Exaile](http://exaile.org) music player on Dapper, but I get the following error after I try to launch it:

```

Traceback (most recent call last):
  File "/usr/bin/exaile", line 67, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media.py", line 18, in ?
    import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis

```

On Exaile`s forum I`ve [found](http://www.exaile.org/forum/thread/22) the following answer for the problem:

> this morning (2006-07-20) came an update to pyogg in edgy and now everything works fine.

According to Synaptic, I`ve got the latest pyogg and pyvorbis (1.3-1ubuntu1) versions.

---

