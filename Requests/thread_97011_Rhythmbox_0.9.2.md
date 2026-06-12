---
title: "Rhythmbox 0.9.2"
date: 2005-11-30
forum: Requests
---

### Post by dexae on 2005-11-30
```
Includes a large number of fixes, improvements and new features. Notable new features include Podcast support, audio CD playback and native AudioScrobbler song submission.
```

---

### Post by strikeforce on 2005-11-30
There will be a new version uploaded after there was a missing dep found.  After that I 'believe' jdong will approve backporting but don't quote me on that.

---

### Post by Kuolio on 2005-11-30
Yey for native audioscrobler support! That's the ONE function that has keeping me with bmp (bmp has easy-to-set-up plugin for scrobler).

---

### Post by tom-ubuntu on 2005-11-30
This looks like a huge update :) Can't wait for this release. Rhythmbox is doing very well lately. Looking forward for the next releases.

---

### Post by trondd on 2005-11-30
Aye! One more vote for Rhythmbox 0.9.2

---

### Post by duffman25 on 2005-11-30
[QUOTE=trondd]Aye! One more vote for Rhythmbox 0.9.2[/QUOTE]

This has already been asked here:
[http://ubuntuforums.org/showthread.php?t=96456](http://ubuntuforums.org/showthread.php?t=96456)

It's defered until now:
> 
a dependency needs to be placed on libgpod-dev by the Dapper
Rhythmbox package. If someone is reading this e-mail and could do so, thanks
in advance... Otherwise I'll get on it eventually :)


So... we have to wait for now.

---

### Post by dexae on 2005-12-01
About this version

* Add podcast support (Renato Araujo:309372)
* Podcast fixes and improvements (Renato Araujo, Dennis Cransto, James Livingston, Jonathan Matthew, William Jon McCann)
* Add support for audioscrobbler/last.fm submission (Ruben Vermeersch:106669)
* Add audio CD support (James Livingston:110928)
* Use libgpod, add support for ipod playlists (Christophe Fergeau)
* Make more strings translatable (Funda Wang)
* Stop when reaching end of playlist in linear mode (Caio Marcelo)
* Fix lots of window-state weirdness (James Livingston:122806)
* Remember window position (Caio Marcelo:315289)
* Fix memory leaks (Christopher Aillon)
* Make hidden/shown window policy better (Caio Marcelo:308053)
* DBus interface improvements (Paul Kuliniewicz)
* Use natural sorting order (James Livingston:158599)
* Fix "show window" in tray icon menu to toggle correctly (Caio Marcelo:318053)
* Don't share hidden tracks with DAAP (James Livingston)
* Make connecting to DAAP shares asynchronous (Jonathan Matthew:316225)
* Make DAAP work on 64 bit systems (Jonathan Matthew:319304)
* Make tag-writing safer (Artem Baguinski, James Livingston)
* Fix memory leaks (Christopher Aillon)
* Make default stations actually show up (James Livingston)
* Make dragging playlists copy not move files (James Livingston:319817)
* Fix re-ordering problems (Jonathan Matthew:319718)
* Save the database regularly (James Livingston:155306)
* Show disc number in info window (Jonathan Matthew:311199)
* UI and HIG fixes (Dennis Cranston:313158, 320184, 320579)
* Allow search box to match multiple properties (139196)
* Report iradio errors better (James Livingston)
* Make date formats correct in all locales (James Livingston)
* Fix drag-and-drop of URLs (Jonathan Matthew)
* Mork better with autofs mounts (Shun-ichi Tahara:320571)
* Don't wedge gnome-vfs-daemon (Shun-ichi Tahara:320570)
* Use chunked loading/sending of daap files (Jonathan Matthew)
* Allow Anjuta to import the source tree (Artem Baguinski)
* Add support for year/date metadata (Christophe Fergeau:166093)
* Display errors in the radio properties (Jonathan Matthew:320749)
* Add file-overwrite dialogs for GTK 2.8 (Jaap A. Haitsma)
* Add "Edit Playlist" item to main menu (James Livingston:311470)
* Make new radio station use the properties dialog (Jonathan Matthew)
* Display the count in the "All" line of browsers (James Livingston)
* Fix query-model refcount and polling problems (Jonathan Matthew:321410)
* Fix emission of entry-changed signals on startip (Jonathan Matthew)
* Support gzip encoded DAAP (Jonathan Matthew:321157)
* Allow pause by middle-clicking on the tray icon (James Livingston)
* Start some RhythmDB API docs (James Livingston)
* Don't display error if Avahi daemon isn't running (James Livingston)
* Emit single "icon missing" warning (Jonathan Matthew:321698)
* Store the bitrate for radio streams (Jonathan Matthew:321702)
* Bring back per-source search box text (James Livingston:321593)
* GObject-ify rb-daap-connection.c (James Livingston:321930 and 322007)
* Make disabling and re-enabling daap work (James Livingston:321748)
* Give playlists and entry-type (Jonathan Matthew)
* Use g_list_prepend to make things not O(n^2) (James Livingston:321696)
* Don't hang with broken DAAP servers (Jonathan Matthew:321919)
* Update quick-reference to have right keys (Baptiste Mille-Mathias)
* Fix libsoup tests for DAAP (Tom Parker)
* Don't have date-added column for cds and ipods (James Livingston:322269)
* Support Avahi 0.6 (Daniel S. Haischt)
* Disable saving, renaming, and deletion of DAAP playlists (Jonathan Matthew)
* Assorted other bug fixes
* Disable the close button's minimise-to-tray action

And some screenshots [http://www.simplifiedcomplexity.com/matt/](http://www.simplifiedcomplexity.com/matt/)

---

### Post by atom on 2005-12-15
this appears to have been remedied.

---

### Post by PsychoTrauma on 2005-12-16
I just compiled this today and I think it is a huge improvement because it removes the need for the gnome cd player. It also remembers the window placement now so when I maxamize it from tray it returns to the position I had it before sending it to tray. The cd playback sounds wonderful without the gaps that most programs have between songs.

---

### Post by Noah0504 on 2005-12-16
Let's hope this makes it to the backports quickly! :)

---

### Post by ubuntu_demon on 2005-12-16
it's made Ubuntu Desktop News :
[http://lists.ubuntu.com/archives/ubuntu-desktop/2005-December/000097.html](http://lists.ubuntu.com/archives/ubuntu-desktop/2005-December/000097.html)

> 
Light on... rhythmbox
=====================
Rhythmbox is a music player for GNOME. It enables you to organize and
listen to all your music with a nice and easy-to-use interface. The
development is very active again, and in the latest releases, we can
find some interesting features:

 * podcast support
 * audio cd support
 * ipod support
 * DAAP support (unavailable for now in Dapper, but it will be soon!):
   this enables you to share your music on the network
 * support to burn CD
 * tag editing for some formats
 * and of course, a lot of bug fixes


Here's the website : [http://www.gnome.org/projects/rhythmbox/](http://www.gnome.org/projects/rhythmbox/)

I want it :-D

---

### Post by akurashy on 2005-12-16
really worth compiling and installing, hope it get backported, the audioscrobbler integration is sweet!

---

### Post by jdong on 2005-12-16
Excellent, looks like build is OK. Will check with James to see if it's possible to build Backports against new Backports libraries. If so, then we're set.

---

### Post by potrick on 2005-12-16
joy joy joy.

---

### Post by r0nin on 2005-12-17
I'm looking forward to see this in the Backports! Thanks!

---

### Post by duffman25 on 2005-12-17
[QUOTE=r0nin]I'm looking forward to see this in the Backports! Thanks![/QUOTE]

me too

---

### Post by Kuolio on 2006-01-01
Hey, has someone forgot to backport this request? 0.9.2 is already in the dapper repos (has been for a long time) and I for one have really been waiting for a backport. Anything happening with it? 

Oh, and one offtopic question: is a backport always made for all arch's, or are bp's 1st made to i386 and then, maybe two months later ;) , for amd64 and such?

I haven't been following bp-forums very actively lately, so I dont know what has changed sinse Hoary.. but definetly something has, because with Hoary/Warty backports were generaly made much more faster, and the whole "bp-team" felts snappier.

Still, keep up the good work, it's really much apresiated!

---

### Post by potrick on 2006-01-01
Kuolio, jdong has been taking time off for the Holidays, said he would not process anything until new years. Now that that's over maybe we'll see it soon, but I think the break was a well deserved one.

Happy new year, everyone.

---

### Post by majikstreet on 2006-01-01
I hope this does get  backported... I need to compile it myself..

majik

---

### Post by jdong on 2006-01-02
Weird, the build didn't go through properly.... /me grumbles about buildd

---

### Post by potrick on 2006-01-06
So what happens now, jdong? This particular backport seems to have had a long  and storied history involving many complications. I think I'm not the only one who has been following this thread for a while. 
  We all respect the work you do. A lot.  I would just like to know what is happening with this package and if we can expect it to be done anytime soon or if we should forget about the DAAP.

---

