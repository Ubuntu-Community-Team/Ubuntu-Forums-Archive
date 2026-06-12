---
title: "Totall Wired:a music player"
date: 2012-11-27
forum: Ubuntu Application Development
---

### Post by | MM | on 2012-11-27
Hello good people,

I've been mucking about with python, glib, gtk, gstreamer, qt, qml & dbus (it's a total Frankenstein! They can coexist...) working on a music player as a bit of a distraction from the real world.  It's called *Totally Wired* or in my shorthand *tw*.

It's quite usable (for me... ymmv).  I figure it would be a total waste for me not to put it out into the www to see if there was any community interest in the project.

Raison d'etre: 
I wanted a music player that handles itinerant music sources more gracefully than the current crop. What's more you can 'hide' sources, say, if music is duplicated across multiple sources you could prefer one source over another.

It has some last.fm integration such that it can suggest similar artists or tracks as well as cover art fetching.  tw can enqueue similar tracks based on last.fm similar artist suggestions that are locally available.

tw includes a very WIP audio cd player which cannot import tracks yet but can retrieve metadata from musicbrainz based on discid.

tw includes a simple radio player which when a new stream url is supplied will fetch the hostname favicon and page title.

It has a playback queue but no playlist support.

I am keen for any contributions, be they code or concepts.


Here are some screenshots and a wee video of it in action.

Screenshots:
[https://picasaweb.google.com/109445252479985672297/TotallyWired?authuser=0&feat=directlink](https://picasaweb.google.com/109445252479985672297/TotallyWired?authuser=0&feat=directlink)

Video:
[https://dl.dropbox.com/u/123544/tw.ogv](https://dl.dropbox.com/u/123544/tw.ogv)

To get it running locally you need to branch tw from launchpad (you need bzr installed):
**bzr branch lp:totallywired**


You need to also have the following packages installed from the repositories: 
python-mutagen
python-lxml
python-qt4
python-qt4-dbus

A bit more tricky as you need to enable a ppa but you also need to install:
qt-components-desktop (from Forum Nokia PPA)([https://launchpad.net/~forumnokia/+archive/fn-ppa](https://launchpad.net/~forumnokia/+archive/fn-ppa))


When all of those packages are installed... from a terminal you need to run ./twsetup from whichever folder you have tw.  twsetup will copy over the font I've created into .fonts and update the font-cache (requires sudo) and also create some .cache dirs.

From the same dir you can then launch tw with ./totally-wired in the terminal or double-click the .desktop file included within the tw folder. 

Launchpad:
[https://launchpad.net/totallywired](https://launchpad.net/totallywired)



Cheers,
Matt

---

