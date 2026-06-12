---
title: "Google Reader as a torrent RSS backend, oh my!"
date: 2008-03-12
forum: The Cafe
---

### Post by defrex on 2008-03-12
I wrote a python script I thought some might find useful. It checks a tag in Google Reader for updates to torrent RSS feeds (like those from <snip>), downloads the .torrent file, and opens it with the app of your choice (my choice is deluge).

It's a handy way to manage torrent RSS feeds in the cloud. That way you can subscribe to a new show from anywhere, and can move to a new torrent app and keep all your feeds in order. Very handy, if you ask me.

Credit to [the pyrfed project]("http://code.google.com/p/pyrfeed/") for the Google Reader Python library.

EDIT: There is a new version at github:

[http://github.com/defrex/reader-download/tree/master](http://github.com/defrex/reader-download/tree/master)

---

### Post by defrex on 2009-02-12
New version :)

---

### Post by TuRDMaN on 2009-02-16
Wow, I've been looking for something like this to use with NZBs, gonna try it out now! Thanks :P


Hmm... I seem to have run into some trouble.

```

Running reader-torrent.py at  8:14:09 pm - February 16, 2009
logging into Google Reader...
Checking for new torrents...

New Torrents:
	Fifth Gear S15E07

Downloading  Fifth Gear S15E07
Traceback (most recent call last):
  File "/home/user/bin/reader-torrent.py", line 110, in <module>
    remotefile = urllib2.urlopen(entry['medialink'])
KeyError: 'medialink'

```

Any suggestions?

---

### Post by defrex on 2009-03-11
try the newest version:

[http://github.com/defrex/reader-download/tree/master](http://github.com/defrex/reader-download/tree/master)

---

### Post by PsychedelicReaction on 2009-03-11
nice one but it looks like it's not working to me.

```
michele@michele-jaunty:/media/STORAGE-1/Torrents/Queue$ ./reader-download.py
Running reader-torrent.py at  5:38:25 pm - March 11, 2009
logging into Google Reader...
Checking for new torrents...
user/-/label/Torrents

New Torrents:

```

username, password and label are set in the python file itself...

---

### Post by aeiah on 2009-03-11
oooo this looks pretty interesting. its limitation for me is that i want downloads to be automatic, but i dont want everything in the rss subscription. when i get home im gonna have a play and probably add a keywords section to it so it skips downloading and adding the torrent if the torrent name doesnt contain, say, family guy, simpsons or futurama.

---

