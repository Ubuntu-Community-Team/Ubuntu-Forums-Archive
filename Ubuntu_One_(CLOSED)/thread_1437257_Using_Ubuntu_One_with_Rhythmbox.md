---
title: "Using Ubuntu One with Rhythmbox"
date: 2010-03-23
forum: Ubuntu One (CLOSED)
---

### Post by kernco on 2010-03-23
How easy is it to use Rhythmbox with Ubuntu One, so that my statistics like play count and ratings stay synced over multiple computers?  Is this something I can do with Ubuntu One?

---

### Post by dabomb1022 on 2010-03-23
You can purchase songs and they will sync to your other computers but I don't know if it syncs the play count.

---

### Post by duanedesign on 2010-03-23
kernco,
it wouldnt be hard at all. In fact there was a user in freenode channel #ubuntuone just the other day making a Rhythmbox plugin that synced playlists. Little knowledge of Python and CouchDB is all thats required. I myself had made a Python Script that syncs my application list and .config files to a CouchDB that then replicates to all my computers via Ubuntu One.

Here are the links I have to help you get started.

**Making a Rhythmbox PLugin**
[Opportunistic Developer Week Presentation]("http://www.kryogenix.org/code/RBMicroBlog/")
[Rhythmbox PLugin Writing Guide]("http://live.gnome.org/RhythmboxPlugins/WritingGuide#Adding_UI")
[PLugin Examples]("http://live.gnome.org/Rhythmbox%20Plugins/Python%20Plugin%20Examples")

**Desktopcouch & CouchDB**
[CouchDB wiki]("http://wiki.apache.org/couchdb/")
[Desktopcouch Wiki]("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/#Iamadeveloper.2CandIwanttheapplicationsIwritetostoredatainandworkwithdesktopcouch")
[Tutorial:Make you application sync with Ubuntu One]("http://arstechnica.com/open-source/guides/2009/12/code-tutorial-make-your-application-sync-with-ubuntu-one.ars")

good luck,
duanedesign

---

