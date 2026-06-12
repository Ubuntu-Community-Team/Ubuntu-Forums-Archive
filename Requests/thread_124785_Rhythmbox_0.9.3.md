---
title: "Rhythmbox 0.9.3"
date: 2006-02-02
forum: Requests
---

### Post by idn on 2006-02-02
There seems to be a whole load of improvements to this one, so how about sticking it in the backports :)

___________________________________________________

Rhythmbox is an integrated music management application, originally inspired by Apple's iTunes.

About this version
* disable column auto-sizing, improves speed [Jonathan Matthew: 312122]
* resort in a faster way [James Livingston: 315389]
* don't try to burn long playlists [William Jon McCann: 321753]
* other cd-burning fixes and HIG improvements [William Jon McCann: 321754]
* fix "Post" and "Episode" wording [James Livingston: 321653]
* display tag-writing errors to the user [James Livingston]
* make the podcast dialog look like the song one [William Jon McCann]
* use glib class private data everywhere [William Jon McCann: 313688]
* add "Move to trash" command [Bastien Nocera: 315389]
* support DBus 0.6 [William Jon McCann]
* add support for "Watched Libraries] [James Livigston: 160159]
* add support for remote gnome-vfs [James Livingston: 140355]
* select source when hovering with drag [Thomas de Grenier de Latour: 323044]
* fix parsing of some RSS feeds [Ryan P Skadberg: 323153]
* use toolbar [William Jon McCann, James Livingston: 316238]
* always hide rather than remove db entries until old [James Livingston]
* ellipsise source names, instead of adding scroll bar [James Livingston]
* allow year to be changed on multiple songs [Alex Lancaster]
* refactor playlist classes [Jonathan Matthew]
* add gstreamer 0.10 support [Jan Schmidt, James Livingston]
* fix drag-and-drop of URLs [Jonathan Matthew:323610]
* save metadata when forward/next are pressed [James Livingston: 320952]
* fix complaints about deprecated libnautilusburn API in 2.13 [James Livingston]
* make entry-views just a display, and fix play orders [Jonathan Matthew:323612]
* remove distro-packaging stuff [James Livingston]
* fix 5 sec pause when finding non-audio files with gst 0.10 [James Livingston]
* fix playlist saving and shutdown [William Jon McCann: 322940]
* submit songs longer than 30 mins to AudioScrobbler [Ståle Lyngaas: 323639]
* make iradio dialog look like song one [William Jon McCann: 323306]
* make genre tag-writing not use artist [Alex Lancaster: 323642]
* more entry-view cleanup and refactoring [Jonathan Matthew: 323640]
* fix problem with dropping artist/album into an entry view [James Livingston]
* add play queue [Jonathan Matthew: 107787]
* about dialog fixes and update AUTHORS and MAINTAINERS [William Jon McCann]
* remove use of GMemChunks [James Livingston]
* remove unused podcast feed column [William Jon McCann: 322961]
* add support for the search box to playlists. [James Livingston]
* add support for more date formats in podcast feeds [William Jon McCann]
* use "friendly time" for properties display [William Jon McCann]
* add fulscreen mode [William Jon McCann: 324075]
* allow iradio stations to be stream URLs [Jonathan Matthew]
* fix parsing of itunes:image element in podcasts [William Jon McCann]
* allow podcasts with no pubication date [Jonathan Matthew]
* add disc number to multiple-track properties window [Jonathan Matthew, 324777]
* read playcount and year from ipod db [Gunnar Steinn Magnusson]
* add 'last episode' field to the podcast feed dialog [Jonathan Matthew]
* assorted DAAP fixes [James Livingston, Jonathan Matthew, William Jon McCann]
* add libnotify support [Jonathan Matthew]
* use G_DEFINE_TYPE [James Livingston, Lubomir Marinovm, William Jon McCann]
* many play-order fixes [Jonathan Matthew]
* add default playlists [William Jon McCann: 323004]
* add support for Year criteria in auto playlists [Alex Lancaster: 321341]
* give names to playlists created via drag-n-drop [William Jon McCann: 326116]
* allow dbus to chaneg volume [Jonathan Matthew]
* stop playback after a podcast finished [James Livingston: 322077]
* fill in multi-track property window fields [James Livingston: 326054]
* don't lose hidden entries from playlists [James Livingston: 319278]
* add support for generic mass-storage audio players [James Livingston: 325602]
* don't get stuck on recursive symlinks [James Livingston: 125452]
* don't crash on hybrid audio+data cds [Jonathan Matthew]
* make startup faster [James Livingston, Jonathan Matthew: 323348 and others]
* display number of tracks in browsers [William Jon McCann: 327372]
* add support for Year metadata from DAAP shares [Alex Lancaster: 327700]
* support chunked-encoding for DAAP [Jonathan Matthew: 326738, 318852]
* change default rating back to 0 [James Livingston]
* sort URIs when artist/album is dragged [Jonathan Matthew: 327494]
* remove items from browsers when tracks are hidden [James Livingston: 327061]
* don't spin when all tracks are unplayable [Jnonathan Matthew: 329329]
* minor UI and HIG fixes [Dennis Cranston, Jaap A. Haitsma, James Livingston, Jonathan Matthew, William Jon McCann, Bastien Nocera]
* assorted other bug fixes and minor improvements

Updated Translations
--------------------
* de Hendrik Brandt
* en_CA Adam Weinberger
* es Francisco Javier F. Serrador
* fi Ilkka Tuohela
* fr Christophe Bliard
* gl Ignacio Casal Quinteiro
* hu Gabor Kelemen
* ja Takeshi AIHANA
* lt Žygimantas Beru&#269;ka
* nb Kjartan Maraas
* nl Vincent van Adrighem, Tino Meinen
* no Kjartan Maraas
* pt_BR Evandro Fernandes Giovanini, Raphael Higino
* vi pclouds, Clytie Siddall
* zh_CH Funda Wang
* zh_TW Abel Cheung

---

### Post by MighMoS on 2006-02-02
I've been using the new version of rhythmbox, and I even have gotten debs out for the new version at [http://mighmos.org](http://mighmos.org) .  But I believe this would include backporting libgpod to Breezy, unless you didn't want iPod support, and from what I've seen, tag editing is _increadibly_ unstable.  I haven't tried DAAP yet, as I have no network to test it on.

I'm no "official" dev, but that's just my heads up on what to expect.

---

### Post by potrick on 2006-02-03
I doubt it'll be backported too, seeing as 0.9.2 has been requested a lot since November and nothing's happened. Really exciting to see changes to rhythmbox, though, thank you for the link. Has anyone else managed to get DAAP to work?

---

### Post by Noah0504 on 2006-02-03
[QUOTE=potrick]I doubt it'll be backported too, seeing as 0.9.2 has been requested a lot since November and nothing's happened. Really exciting to see changes to rhythmbox, though, thank you for the link. Has anyone else managed to get DAAP to work?[/QUOTE]
Yes, it's exciting to see Rhythmbox being imporved upon as fast as it is, but it's sad to see the lack of backporting to help "noobs" like myself.

---

### Post by doclivingston on 2006-02-03
[QUOTE=MighMoS]from what I've seen, tag editing is _increadibly_ unstable.  I haven't tried DAAP yet, as I have no network to test it on.[/quote]

Both of those should be be much more stable then they used to be. However tag-editing only work on mp3 and flac files at the moment.

If anyone wants a more readable overview of new stuff, rather than the huge list which includes behind-the-scenes things you won't care about, see [my blog post about 0.9.3](http://doctau.blogspot.com/2006/02/rhythmbox-093_02.html)

---

### Post by idn on 2006-02-04
[QUOTE=MighMoS]I've been using the new version of rhythmbox, and I even have gotten debs out for the new version at [http://mighmos.org](http://mighmos.org) .  But I believe this would include backporting libgpod to Breezy, unless you didn't want iPod support, and from what I've seen, tag editing is _increadibly_ unstable.  I haven't tried DAAP yet, as I have no network to test it on.

I'm no "official" dev, but that's just my heads up on what to expect.[/QUOTE]


Thanks for the packages, everything seems ot work ok so far, let you know if i have any problems

---

### Post by homerhomer on 2006-02-08
Thanks for the great package

any chance you could compile it again with daap support?

Thanks again

---

### Post by kaamos on 2006-02-08
Thanks for the package!

This is so much better than the version that comes with breezy. Lighter, less crash-happy and I like the new UI. Had to fix the shuffle-icon to be a bit bigger png than 16x16px, but besides that everything worked just fine just by installing the packages.

---

### Post by MighMoS on 2006-02-08
Since its not going to be backported, I'm not sure if this is thread hijacking or not, but I've uploaded new Rhythmboxes (including a patch bump to .1) to [http://mighmos.org](http://mighmos.org).

---

### Post by stoffepojken on 2006-02-09
Thank you for the debs. Works great

---

### Post by mmcmonster on 2006-02-11
Thanks for the .debs.  It installs fine (once I made sure I had installed the necessary libraries)

One thing I noticed.  In the version that comes with Ubuntu, hitting the close button got rid of the window but let it minimize to the area in the right side of the status bar (forgot what it's called. :-) ), while the .deb I downloaded doesn't do this.  Not a big deal, really.

Still, I'm just glad that Rhythmbox is being updated.  Now if I could only figure out why it doesn't sort based on clicking on a column header in playlists, even though it does so for the Library, and why I can't add album art yet...

---

### Post by doclivingston on 2006-02-12
[QUOTE=mmcmonster]One thing I noticed.  In the version that comes with Ubuntu, hitting the close button got rid of the window but let it minimize to the area in the right side of the status bar (forgot what it's called. :-) ), while the .deb I downloaded doesn't do this.  Not a big deal, really.[/quote]

While some people like that behaviour, a lot of people don't, and it got reverted. If you want the full details of the debate, you can search the archives of [rhythmbox-devel](http://lists.gnome.org) for it. It will probably return as a trivial plugin, once plugin support lands.


> Still, I'm just glad that Rhythmbox is being updated.  Now if I could only figure out why it doesn't sort based on clicking on a column header in playlists, even though it does so for the Library

If you're using an automatic playlist, without a limit, it should do that. Automatic playlists with limits are always sorted on the property that is used in the limit.

---

### Post by mmcmonster on 2006-02-12
[QUOTE=doclivingston]If you're using an automatic playlist, without a limit, it should do that. Automatic playlists with limits are always sorted on the property that is used in the limit.[/QUOTE]
Yeah.  Unfortunately, I'm creating my own playlists manually so that doesn't help much.  Still, that's not a big deal.

Also, Anyone notice crashing when trying to drag multiple songs at once to a playlist?

---

### Post by kanem on 2006-02-12
[QUOTE=doclivingston]If you're using an automatic playlist, without a limit, it should do that. Automatic playlists with limits are always sorted on the property that is used in the limit.[/QUOTE]
Would it be a silly or hard/impossible thing to make an auto-playlist generated from a static one? Like using the actual playlists.xml file as a search field?

Wow, I didn't know about that trick adding the .is_a_player to my device 'till I read your blog. Thanks.

Also, back when the patch was added to get around the gtk column resizing bug, startup was really fast. But I've noticed that now it's pretty slow again. Not as slow as a year ago, but slower than cvs was a couple of months ago. I thought it was maybe the new feature of listing how many tracks are in each genre/album/artist but from your blog I see one slowdown is the missing track check. Is the slowdown just from this?

Thanks

---

### Post by doclivingston on 2006-02-12
[QUOTE=mmcmonster]Yeah.  Unfortunately, I'm creating my own playlists manually so that doesn't help much.  Still, that's not a big deal.[/quote]

The issue with allowing this, is that there is no way to undo the sorting. Accidently clicking on a column header and destroying you're carefully ordered playlist wouldn't be good.

In theory we could allow sorting, and return the the original order by clicking on the track# number column. However it will get complicated if people re-order the playlist while it is sorted.


> Also, Anyone notice crashing when trying to drag multiple songs at once to a playlist?

The best thing to do is file a bug.

---

### Post by doclivingston on 2006-02-13
[QUOTE=kanem]Would it be a silly or hard/impossible thing to make an auto-playlist generated from a static one? Like using the actual playlists.xml file as a search field?[/quote]

It's possible, but not that easy. Playlists exist above the database, so it would require a way of letting higher-level things add query criteria. There are some vague plans on this, but it might be a while before it gets done.


> Also, back when the patch was added to get around the gtk column resizing bug, startup was really fast. But I've noticed that now it's pretty slow again. Not as slow as a year ago, but slower than cvs was a couple of months ago. I thought it was maybe the new feature of listing how many tracks are in each genre/album/artist but from your blog I see one slowdown is the missing track check. Is the slowdown just from this?

It's mostly due to that, for two different reasons:

1) Tracks aren't shown until the check completes, which means it takes a while for them to show up in the UI. This is fixed in cvs, by remembering which ones are hidden between sessions.

2) Because we queue up so many stat operations (the check to see if they still exist), gnome-vfs blocks because we are doing it too quickly. We need to limit how fast we do that, but that hasn't been done yet.

---

### Post by Baptiste on 2006-02-13
Thanks for all this is a great package!

---

### Post by mjsoccer1 on 2006-02-20
Thanks for the debs, they work great... 0.9.3.1 is definitely more stable than 0.9.2, it used to crash all the time.  The DAAP support is awesome

---

### Post by MighMoS on 2006-02-20
[QUOTE=mjsoccer1]Thanks for the debs, they work great... 0.9.3.1 is definitely more stable than 0.9.2, it used to crash all the time.  The DAAP support is awesome[/QUOTE]
Thanks for the feedback.  You're the first person to tell me if I compiled DAAP support correctly or not :-)

---

### Post by daveg on 2006-03-09
I've been using these packages for a few days. Looking great! 0.9.3.1 is definitely more stable than previous versions in the 0.9.x series.

---

### Post by Coolit on 2006-03-09
Thanks for the .debs! Ive been after an updated rhythmbox for a while now, its damn hard to find especially in 64-bit, I couldn't believe my luck when I stumbled on this thread.

With ought hijacking this thread, Is there any chance you could compile a 64-bit Banshee .deb MighMos? it's the last of my main apps that I'd like to update atm.

Thanks :-)

---

### Post by chusome on 2006-03-26
I tried installing this package the other day and had some trouble with dependencies. So, I got a litle experimental, long story short I had to reinstall......

Could someone possibly document the install?
I particularly had trouble with gpod0, and then of cousre its dependancies.

---

### Post by MighMoS on 2006-03-26
No problem, I always try to provide 64-bit packages.  No need to give people another reason not to use AMD64.  

Anyway, chusome, could you contact me privately on what happened, what went wrong, etc so I can document this?

---

### Post by Abdi110 on 2006-04-08
Thanks for the deb, you rock!

---

