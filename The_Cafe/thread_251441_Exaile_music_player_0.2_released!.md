---
title: "Exaile music player 0.2 released!"
date: 2006-09-05
forum: The Cafe
---

### Post by synic on 2006-09-05
Exaile 0.2 is released today.  This marks the first official "stable" (I hope) release.

See screenshots at [http://www.exaile.org](http://www.exaile.org).

Ideas for the next release include:

* podcast support
* would it be cool to have an "exailed" running on one machine, and have a "remote collection" tab on another?

Come discuss more ideas: irc.freenode.org / #exaile

"Exaile is a media player aiming to be similar to KDE's AmaroK, but for GTK+. It incorporates many of the cool things from AmaroK (and other media players) like automatic fetching of album art, handling of large libraries, lyrics fetching, artist/album information via the wikipedia, last.fm support, optional iPod support (assuming you have python-gpod installed).

In addition, Exaile also includes a built in shoutcast directory browser, tabbed playlists (so you can have more than one playlist open at a time), blacklisting of tracks (so they don't get scanned into your library), downloading of guitar tablature from fretplay.com, and submitting played tracks on your iPod to last.fm."

---

### Post by mostwanted on 2006-09-05
Very nice. Podcast support would be very welcome, as would album art selection ala Amarok (or like Muine for that matter).

Great job with this release, although, I have an issue with it ;) When I have two albums by the same artist, I can't seem to find a way to order the songs chronologically by album - they get all mixed up, seemingly no pattern to it.

What I want is 

Album 1:
- song 1
- song 2
- ...
- song 12

Album 2:
- song 1
. song 2
- ...
- song 10

Sorting them by album gives me

Album 1
- song 4
- song 1
- song 7
- ...

Album 2
- song 8
- song 12
- song 1
- ...

Sorting them by track gives me

song 1 - album 1
song 1 - album 2
song 2 - album 1
song 2 - album 2
etc.

---

### Post by synic on 2006-09-05
> **mostwanted said:**
> Very nice. Podcast support would be very welcome, as would album art selection ala Amarok (or like Muine for that matter).

Great job with this release, although, I have an issue with it ;) When I have two albums by the same artist, I can't seem to find a way to order the songs chronologically by album - they get all mixed up, seemingly no pattern to it.

What I want is 

Album 1:
- song 1
- song 2
- ...
- song 12

Album 2:
- song 1
. song 2
- ...
- song 10

Sorting them by album gives me

Album 1
- song 4
- song 1
- song 7
- ...

Album 2
- song 8
- song 12
- song 1
- ...

Sorting them by track gives me

song 1 - album 1
song 1 - album 2
song 2 - album 1
song 2 - album 2
etc.

How are you adding them to the playlist?

---

### Post by mostwanted on 2006-09-05
I just drag and drop the artist from the side column. Oh, it's like I want it at first, but if I sort them and then try to sort them back it gets all scrambled =/

---

### Post by UbuWu on 2006-09-05
> **synic said:**
> 
* would it be cool to have an "exailed" running on one machine, and have a "remote collection" tab on another?


That is what I use [tangerine]("http://www.snorp.net/log/tangerine") for.

---

### Post by synic on 2006-09-05
> **UbuWu said:**
> That is what I use [tangerine]("http://www.snorp.net/log/tangerine") for.

Isn't that for local network only?

---

### Post by hanzomon4 on 2006-09-05
Nevermind I got it.

Exaile is still listing my m4a files and emusic mp3 files as unknown

---

### Post by synic on 2006-09-05
> **hanzomon4 said:**
> Nevermind I got it.

Exaile is still listing my m4a files and emusic mp3 files as unknown

Are the emusic mp3s DRM somehow?

---

### Post by hanzomon4 on 2006-09-05
No drm free, they play fine they just get listed under unknown.

By the way between your exaile player and listen-gnome my music listening needs are served... Good work ;)

---

### Post by synic on 2006-09-05
> **hanzomon4 said:**
> No drm free, they play fine they just get listed under unknown.

By the way between your exaile player and listen-gnome my music listening needs are served... Good work ;)

I wonder if they are tagged oddly.  What does the "file" command have to say about them?

---

### Post by Suzan on 2006-09-05
I've tried to install the new version 0.2. But the ubuntu paket installer gives me the warning "a newer version is installed..." cause I have version 0.2b5.

Is it a matter of the filename?

---

### Post by synic on 2006-09-05
> **Suzan said:**
> I've tried to install the new version 0.2. But the ubuntu paket installer gives me the warning "a newer version is installed..." cause I have version 0.2b5.

Is it a matter of the filename?

Yes.  I just put 0.2.1 up, it might resolve this problem.  If not, just force the installation.

---

### Post by hanzomon4 on 2006-09-05
Here's the output on one ```
/01 I Slept With Bonhomme At The CBC.mp3: MP3 file with ID3 version 2.3.0 tag
```

---

### Post by synic on 2006-09-05
> **hanzomon4 said:**
> Here's the output on one ```
/01 I Slept With Bonhomme At The CBC.mp3: MP3 file with ID3 version 2.3.0 tag
```

Have you tried removing your music.db and doing a rescan?

---

### Post by hanzomon4 on 2006-09-05
Yeah didn't work but I ran it in the terminal and it spit out some errors
I get this when I start exaile
```
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
```

And this when scanning by library 
```
(exaile:15835): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_object_unref: assertion `GST_IS_OBJECT (object)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_object_unref: assertion `GST_IS_OBJECT (object)' failed

(exaile:15835): GStreamer-WARNING **: Element fakesink is not in bin decoder

(exaile:15835): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_object_unref: assertion `GST_IS_OBJECT (object)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_object_unref: assertion `GST_IS_OBJECT (object)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_object_unref: assertion `GST_IS_OBJECT (object)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_object_unref: assertion `GST_IS_OBJECT (object)' failed

(exaile:15835): GStreamer-WARNING **: Element fakesink is not in bin decoder

(exaile:15835): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_element_get_state: assertion `GST_IS_ELEMENT (element)' failed

(exaile:15835): GStreamer-CRITICAL **: gst_object_unref: assertion `GST_IS_OBJECT (object)' failed
```
It just kept spitting out "GStreamer-CRITICAL" errors

---

### Post by maniacmusician on 2006-09-05
some feedback:
- lyrics are usually really slow to load, if they load at all 
- the wikipedia tabs are usually pretty good
- for the tablature, and lyrics, there should be a "next" button so that you can try to find another one if you don't like the one that comes up first.

i feel like this is a really good effort, because you're active on these forums, taking in suggestions and stuff. great job so far, can't wait to see what you come up with next.

edit: also, i love the fact that if you get landed at the wrong wikipedia article, you can easily find the right one. I don't think Listen let me click on links or change the wikipedia page. and emphasis on the slow lyrics, i've tried 4 different tracks from different bands with the same result

---

### Post by synic on 2006-09-05
> **maniacmusician said:**
> some feedback:
- lyrics are usually really slow to load, if they load at all 
- the wikipedia tabs are usually pretty good
- for the tablature, and lyrics, there should be a "next" button so that you can try to find another one if you don't like the one that comes up first.

i feel like this is a really good effort, because you're active on these forums, taking in suggestions and stuff. great job so far, can't wait to see what you come up with next.

edit: also, i love the fact that if you get landed at the wrong wikipedia article, you can easily find the right one. I don't think Listen let me click on links or change the wikipedia page. and emphasis on the slow lyrics, i've tried 4 different tracks from different bands with the same result

I hear ya on the lyrics.  I'm going to spend some effort and try to find a better lyrics server.  I've noticed that leoslyrics has just been extra slow lately (even in Listen).

Any recommendations?

---

### Post by maniacmusician on 2006-09-05
can you use just any lyrics website you want?

i'd recommend either azlyrics.com or just [www.lyrics.com](www.lyrics.com). they're first two that came up in a google search, but the second one especially seems to be very responsive. and plus, they're in a partnership with mtv and google. (as you can see by the google video applet on the page.) more info on that at google's blog ([http://googleblog.blogspot.com/2006/08/i-got-99-problems-but-video.html](http://googleblog.blogspot.com/2006/08/i-got-99-problems-but-video.html))

---

### Post by synic on 2006-09-05
> **maniacmusician said:**
> can you use just any lyrics website you want?

i'd recommend either azlyrics.com or just [www.lyrics.com](www.lyrics.com). they're first two that came up in a google search, but the second one especially seems to be very responsive. and plus, they're in a partnership with mtv and google. (as you can see by the google video applet on the page.) more info on that at google's blog ([http://googleblog.blogspot.com/2006/08/i-got-99-problems-but-video.html](http://googleblog.blogspot.com/2006/08/i-got-99-problems-but-video.html))

Yeah, it can be any website - I'm sure you have to get permission.  Looks like amarok is currently using [http://lyrc.com.ar/](http://lyrc.com.ar/).  I guess this would be a good time to implement plugin support - that way people can write plugins for their favorite lyrics website...

---

### Post by maniacmusician on 2006-09-05
indeed...but more important is a fast default server. I doubt most people would try and right plugins unless they *really* like a website. plus, a lot of people don't even know how to write plugins lol...(one might even say most)

---

### Post by synic on 2006-09-05
> **maniacmusician said:**
> indeed...but more important is a fast default server. I doubt most people would try and right plugins unless they *really* like a website. plus, a lot of people don't even know how to write plugins lol...(one might even say most)

Oh, I'll of course write a nice default one :)

---

### Post by maniacmusician on 2006-09-05
:) you should also consider adding additional sites to search tablature off of. I got hits for popular artists (like Nirvana) but not many others. i can find them on the internet using google of course, but it'd be sweet not to have to use it.

---

### Post by banjobacon on 2006-09-05
Did you get rid of the right-click menu in the 'Collection' tab of the sidebar? Why?

And it would be cool if you set up a [Trac](http://trac.edgewall.org/) for your project so bugs/requests can be filed. It would probably be a lot more useful than a thread in a message board.

---

### Post by maniacmusician on 2006-09-05
> **banjobacon said:**
> Did you get rid of the right-click menu in the 'Collection' tab of the sidebar? Why?

And it would be cool if you set up a [Trac](http://trac.edgewall.org/) for your project so bugs/requests can be filed. It would probably be a lot more useful than a thread in a message board.
that's true, it would be more useful

---

### Post by banjobacon on 2006-09-05
I think Last.fm submissions might have to be submitted in GMT time. Exaile is using local time, and this triggers Last.fm's spam protection if I use Exaile within a certain amount of time as another player which submits GMT times.

---

### Post by Genma on 2006-09-06
Very nice player indeed. While I'm new to Linux I don't miss Foobar too much when using Exaile.

I must say though, I can't seem to install it correctly from source (.deb works fine). I thought it was just a matter of untaring and then

```
~/exaile/ make
~/exaile/ make install
```

But the make command spits out heaps of warnings and errors, mostly about python syntax. Am I doing something wrong?

---

### Post by patwack on 2006-09-06
> **synic said:**
> 
Ideas for the next release include:

* podcast support
* would it be cool to have an "exailed" running on one machine, and have a "remote collection" tab on another?

DAAP support? it's the only thing keeping me from using exaile all through my house, i use exaile on my computer upstairs but have to use rhythmbox or banshee to access the daap shares downstairs. DAAP's really handy for keeping one music collection on a network and it's cross platform to boot

---

### Post by synic on 2006-09-06
> **patwack said:**
> DAAP support? it's the only thing keeping me from using exaile all through my house, i use exaile on my computer upstairs but have to use rhythmbox or banshee to access the daap shares downstairs. DAAP's really handy for keeping one music collection on a network and it's cross platform to boot

How are you access DAAP shares in rhythmbox?  I can't find this feature (nor in Banshee)

---

### Post by synic on 2006-09-06
> **Genma said:**
> Very nice player indeed. While I'm new to Linux I don't miss Foobar too much when using Exaile.

I must say though, I can't seem to install it correctly from source (.deb works fine). I thought it was just a matter of untaring and then

```
~/exaile/ make
~/exaile/ make install
```

But the make command spits out heaps of warnings and errors, mostly about python syntax. Am I doing something wrong?

Probably need to have python2.4-dev installed, and libgtk2.0-dev.

Adam

---

### Post by banjobacon on 2006-09-06
> **synic said:**
> How are you access DAAP shares in rhythmbox?  I can't find this feature (nor in Banshee)
I think you can access shares by default. To enable sharing, go to the "Sharing" tab in Preferences.

I think Listen also supports DAAP, so I guess you can check out their code.

---

### Post by Genma on 2006-09-07
> **synic said:**
> Probably need to have python2.4-dev installed, and libgtk2.0-dev.

Adam

python2.4-dev was the culprit. Worked fine now =)

---

### Post by Corbelius on 2006-09-07
For amd64 system: [http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

---

### Post by jamesford on 2006-09-07
how on earth do i add songs to a playlist in this player?

---

### Post by maniacmusician on 2006-09-07
you just drag and drop from the sidebar into the main window. you can also go to the playlist tab and choose a smart playlist or create your own, i think.

---

### Post by synic on 2006-09-07
> **jamesford said:**
> how on earth do i add songs to a playlist in this player?

Yeah, just go to the Playlists tab on the left and drag tracks to the "Custom Playlist" area.  I just realized that I really ought to add a "Add to Playlist" item in the Collection popup...

Adam

---

### Post by maniacmusician on 2006-09-07
> **synic said:**
> Yeah, just go to the Playlists tab on the left and drag tracks to the "Custom Playlist" area.  I just realized that I really ought to add a "Add to Playlist" item in the Collection popup...

Adam
another welcome feature would be click-to-add support. Like say in the collection tab, I double click on the name of an artist, everything under that artist should be opened in a new playlist. same with if i double clicked an album.

another implementation of this would be in the form of a right click menu. you would right click on an artist or an album, and have options like Play Now (would open it in a new playlist) Append to Playlist (which would add it to the end of the current playlist), Play Next (would add it to the playlist directly after the current track being played. And Play Now could be the default option if you double click. you could maybe even make the "default action" configurable in preferences if you were so inclined.

---

### Post by reacocard on 2006-09-07
> DAAP support? it's the only thing keeping me from using exaile all through my house, i use exaile on my computer upstairs but have to use rhythmbox or banshee to access the daap shares downstairs. DAAP's really handy for keeping one music collection on a network and it's cross platform to boot

+1

---

### Post by synic on 2006-09-07
> **maniacmusician said:**
> another welcome feature would be click-to-add support. Like say in the collection tab, I double click on the name of an artist, everything under that artist should be opened in a new playlist. same with if i double clicked an album.

another implementation of this would be in the form of a right click menu. you would right click on an artist or an album, and have options like Play Now (would open it in a new playlist) Append to Playlist (which would add it to the end of the current playlist), Play Next (would add it to the playlist directly after the current track being played. And Play Now could be the default option if you double click. you could maybe even make the "default action" configurable in preferences if you were so inclined.

Great suggestions.  These help, because I must admit, I'm just an "Entire collection on random with the occasional queued track or shoutcast station" kind of music listener.

They'll certainly be in the next release.

---

### Post by synic on 2006-09-07
> **reacocard said:**
> +1

I'll see what I can do.  DAAP + python libs are fairly beta now, but I'm sure I can figure something out.  This is something I really want too... so it'll mostly be what I'm working on.

---

### Post by grte on 2006-09-07
Looks good, but I've run into a small problem.  I can sort my library by artist and album, but when I try to sort by genre, nothing shows up.

---

### Post by jamesford on 2006-09-08
i still cant work this out. if i drag mp3s from main pane into the playlist pane i get the option to give the new playlist a name. all fine. but if i shut down exaile and start it again, and try to load the newly created playlist its empty.
even if i got that working, how would i add one additional song to an existing playlist?

either something just doesent work, or the exaile playlist feature is totally different from playlists im used to in other players (bmp for example) and beyond my grasp

---

### Post by synic on 2006-09-08
> **jamesford said:**
> i still cant work this out. if i drag mp3s from main pane into the playlist pane i get the option to give the new playlist a name. all fine. but if i shut down exaile and start it again, and try to load the newly created playlist its empty.
even if i got that working, how would i add one additional song to an existing playlist?

either something just doesent work, or the exaile playlist feature is totally different from playlists im used to in other players (bmp for example) and beyond my grasp

Okay, that was a doosey of a bug.  I'm surprised it wasn't noticed earlier.  I released 0.2.3 to fix this.  If you want to add a song to a playlist, just drag it ontop of the playlist you want to add it to.

In svn, there is also a popup menu item for "Add to Playlist" in the playlist area and in the collection.

Adam

---

### Post by grte on 2006-09-08
When I run exaile from a terminal, I get this output:

```
Traceback (most recent call last):
  File "/usr/bin/exaile", line 1794, in ?
    main()
  File "/usr/bin/exaile", line 1786, in main
    exaile = ExaileWindow(fr)
  File "/usr/bin/exaile", line 66, in __init__
    self.database_connect()
  File "/usr/bin/exaile", line 720, in database_connect
    self.db.check_version("sql")
  File "/usr/share/exaile/xl/db.py", line 53, in check_version
    row = self.read_one("version", "version", "1", tuple())
  File "/usr/share/exaile/xl/db.py", line 167, in read_one
    cur.execute(query, args)
OperationalError: no such table: version

```

Any idea what it means?

---

### Post by synic on 2006-09-08
> **grte said:**
> When I run exaile from a terminal, I get this output:

```
Traceback (most recent call last):
  File "/usr/bin/exaile", line 1794, in ?
    main()
  File "/usr/bin/exaile", line 1786, in main
    exaile = ExaileWindow(fr)
  File "/usr/bin/exaile", line 66, in __init__
    self.database_connect()
  File "/usr/bin/exaile", line 720, in database_connect
    self.db.check_version("sql")
  File "/usr/share/exaile/xl/db.py", line 53, in check_version
    row = self.read_one("version", "version", "1", tuple())
  File "/usr/share/exaile/xl/db.py", line 167, in read_one
    cur.execute(query, args)
OperationalError: no such table: version

```

Any idea what it means?

Your database was created before I started versioning so the database could update itself when the schema changed.  You'll have to rm your music.db and rescan.

Adam

---

### Post by grte on 2006-09-08
> **synic said:**
> Your database was created before I started versioning so the database could update itself when the schema changed.  You'll have to rm your music.db and rescan.

Adam

Ah, okay, thanks.

---

### Post by mrgnash on 2006-09-08
Now I can safely say that this is hands-down the best Gnome music player I have used. The only features that I find myself wanting are some sort of 'now listening' function compatible with Gaim/aMSN and native Last.FM stream support. Neither of these are a huge deal though, so many thanks for producing such a great player :D

---

### Post by maniacmusician on 2006-09-08
> **mrgnash said:**
> Now I can safely say that this is hands-down the best Gnome music player I have used. The only features that I find myself wanting are some sort of 'now listening' function compatible with Gaim/aMSN and native Last.FM stream support. Neither of these are a huge deal though, so many thanks for producing such a great player :D
+1

obviously you can't implement every feature that every user wants, but it seems like you have a little bit of everything. kudos on creating such a great player (and thats only on the first release!) can't wait to see how it evolves.

---

### Post by grte on 2006-09-08
And I see you've also made the Artist/Album/Genre view default to the last one selected.

A saint amongst men, truly.

---

### Post by veli on 2006-09-09
This is really a good player, having nice features. I do want to get the developer attention to some performance tweaks. When started Exaile consumes about 30 MB of RAM, after few hours of continuous playing the memore usage jumps above 70 MB. Is it a memory leak, or what? A fix for that would be necessary IMO. My version is 0.2.3.

Good job anyway, keep on working on this project.

---

### Post by veli on 2006-09-09
Consumed RAM is already 105 MB.

---

### Post by synic on 2006-09-09
> **veli said:**
> This is really a good player, having nice features. I do want to get the developer attention to some performance tweaks. When started Exaile consumes about 30 MB of RAM, after few hours of continuous playing the memore usage jumps above 70 MB. Is it a memory leak, or what? A fix for that would be necessary IMO. My version is 0.2.3.

Good job anyway, keep on working on this project.

I just added a explicit garbage collect statement when you start playing a track.  I've been watching memory usage, and this seems to have helped.  Probably not a leak, just objects weren't getting gced right away.  It's in SVN - give it a try and let me know.

Adam

---

### Post by hanzomon4 on 2006-09-09
Well good and weird. I ran the 2.2 bin that was in the svn dir and it would crash alot with this error
```
Traceback (most recent call last):
  File "exaile.py", line 1800, in ?
    main()
  File "exaile.py", line 1792, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 198, in __init__
    self.show_library_manager()
  File "exaile.py", line 443, in show_library_manager
    dialog = xlmisc.LibraryManager(self)
  File "/home/hanzomon4/.development/svn/exaile/trunk/xl/xlmisc.py", line 1260, in __init__
    self.dialog = self.xml.get_widget('LibraryManager', 'exaile')
TypeError: GladeXML.get_widget() takes exactly 1 argument (2 given)

```

But I was determined to scan my collection to see if it would fix my tagging problems.
I deleted music.db and rescanned, The resulting library was awful.
I then ran my 0.2beta exaile and had a perfect library.
So I killed the 0.2beta and relaunched 2.2 and the Library was perfect. :biggrin: 

Great Job!! =D>

Edit:I can't figure out how to install it

---

### Post by hanzomon4 on 2006-09-09
Spoke to soon it's still sticking some of my m4a and all of my emusic-mp3 in unknown.
I tried editing the tag information and to my surprise the info was already their...

Edit: I clicked save and got this ```
1: Track /media/MAXTOR/KiN/Music/iTunes/Cold/Cold/11 Makes Her Sick.m4a: writing metadata to this filetype is not currently supported.

```
Then it puts the file where its suppose to be... :confused:

---

### Post by maniacmusician on 2006-09-10
synic,

after using 0.2.3 for a little while, here's some more things I came up with: 
Library Scanning - It feels like it does this too often, especially with a pretty large collection like mine. It brings the CPU up to 100% and effectively slows down or freezes me up for a few seconds. I think two parameters should be set for this...one is increase the time between checks (or let this be chosen by the user) and on top of this, have it scan while the computer is idle, not being used. this would be fabulous.

another thing is, sometimes in the collection tab, i'll expand an artist and drag an album into the playlist. After a while, i'll go back to explore more albums by the same artist, but it will have collapsed back to a full tree and back up to the top of the list. I like it to remain as I left it because I'm usually in the mood for a certain artist...this is not a huge deal of course, but just giving some feedback.

i'd also like to point out that your feature of having multiple playlists open is a powerful one. You could make full (or better) use of it by adding a "Play Now" option to the right click menu in the Collections tab...this would open it in a new playlist, not in the current one.

btw, i love the "Append to Playlist" option, super useful.

keep up the good work sir, this is a brilliant player...

edit: forgot to add the other improvements you've made that I love.  Thanks a lot for taking my suggestion about having the OSD come up when I hover over Exaile in the taskbar, I love that. And also, thank you so much for updating the lyrics server...it even gives suggestions if it can't find the right one! brilliant...i wouldn't dream of using anything else. even in KDE...

---

### Post by banjobacon on 2006-09-10
> **maniacmusician said:**
> 
Library Scanning - It feels like it does this too often, especially with a pretty large collection like mine. It brings the CPU up to 100% and effectively slows down or freezes me up for a few seconds. I think two parameters should be set for this...one is increase the time between checks (or let this be chosen by the user) and on top of this, have it scan while the computer is idle, not being used. this would be fabulous.

Could inotify be used, like in Muine, instead of periodic scans?

---

### Post by maniacmusician on 2006-09-10
sorry, i don't use muine...what is inotify?

---

### Post by banjobacon on 2006-09-10
> **maniacmusician said:**
> sorry, i don't use muine...what is inotify?
Filesystem event notification something-or-other.

[http://en.wikipedia.org/wiki/Inotify](http://en.wikipedia.org/wiki/Inotify)

---

### Post by maniacmusician on 2006-09-10
> **banjobacon said:**
> Filesystem event notification something-or-other.

[http://en.wikipedia.org/wiki/Inotify](http://en.wikipedia.org/wiki/Inotify)
sounds perfect for this app.

---

### Post by synic on 2006-09-11
> **maniacmusician said:**
> sounds perfect for this app.

Very cool.  I'll look into this.

---

### Post by synic on 2006-09-11
> **maniacmusician said:**
> synic,

after using 0.2.3 for a little while, here's some more things I came up with: 
Library Scanning - It feels like it does this too often, especially with a pretty large collection like mine. It brings the CPU up to 100% and effectively slows down or freezes me up for a few seconds. I think two parameters should be set for this...one is increase the time between checks (or let this be chosen by the user) and on top of this, have it scan while the computer is idle, not being used. this would be fabulous.

another thing is, sometimes in the collection tab, i'll expand an artist and drag an album into the playlist. After a while, i'll go back to explore more albums by the same artist, but it will have collapsed back to a full tree and back up to the top of the list. I like it to remain as I left it because I'm usually in the mood for a certain artist...this is not a huge deal of course, but just giving some feedback.

i'd also like to point out that your feature of having multiple playlists open is a powerful one. You could make full (or better) use of it by adding a "Play Now" option to the right click menu in the Collections tab...this would open it in a new playlist, not in the current one.

btw, i love the "Append to Playlist" option, super useful.

keep up the good work sir, this is a brilliant player...

edit: forgot to add the other improvements you've made that I love.  Thanks a lot for taking my suggestion about having the OSD come up when I hover over Exaile in the taskbar, I love that. And also, thank you so much for updating the lyrics server...it even gives suggestions if it can't find the right one! brilliant...i wouldn't dream of using anything else. even in KDE...


Ok, good news.  Exaile now uses gamin to monitor directories for changes - so a rescan doesn't happen at all unless something changes in your library area (new music added, directory created, timestamp on a track changed) and it _only_ rescans the directory that the change happened in.

If there's music that you think should be in the collection view but isn't, you just have to hit refresh.

This should greatly reduce the problems you're having.  I've completely removed the "periodic" scan.

Adam

---

### Post by maniacmusician on 2006-09-11
sweet! you are amazing. i'm going to go download it right now. any other changes we should know about? because last time, you just kinda sneaked some changes in there.

edit: err i gather these changes havnt been implemented yet because there's no new download. is it in the svn? i don't know how to use those lol.

---

### Post by synic on 2006-09-11
> **maniacmusician said:**
> sweet! you are amazing. i'm going to go download it right now. any other changes we should know about? because last time, you just kinda sneaked some changes in there.

edit: err i gather these changes havnt been implemented yet because there's no new download. is it in the svn? i don't know how to use those lol.

Yeah, it's all in svn.  

svn co svn://jbother.org/usr/local/svn/exaile/trunk exaile && cd exaile && make && ./exaile

I'm still working on this part of it (it only detects changes while it's running, so if you close exaile, move some music into your library area, and reopen exaile, it won't notice anything changed yet), but mostly it works.  You'll have to enable "watch directories for changes" in the prefs window.

About the snuck in changes... I dunno, heh.

Adam

---

### Post by maniacmusician on 2006-09-11
before i attempt a trunk version, do i have to uninstall my current exaile or does it just go over that? I want to do this as neatly as possibly

---

### Post by hanzomon4 on 2006-09-11
There's some thing wrong with it....
```
make[1]: Leaving directory `/home/hanzomon4/Desktop/exaile/mmkeys'
cp mmkeys/mmkeys.so .
cd po && python fmt.py && cd ..
python: can't open file 'fmt.py': [Errno 2] No such file or directory
make: *** [build] Error 2


```
I got past it in the exaile svn folder that I would update every now and then, but exaile said it was v0.2.2.
I tried your command and it said that I had the same  folder from a different url.
       So I deleted mine and ran the command again. When I got the error above I tried using my old work around. 
 ```
hanzomon4@EIDOKIN:~/.development/svn/exaile$ make -f trunk/Makefile 
```
but it didn't work this time cause that svn address you posted dosen't have the same directories in it.

So I just downloaded the src-tarball, and it made fine

---

### Post by synic on 2006-09-11
> **hanzomon4 said:**
> There's some thing wrong with it....
```
make[1]: Leaving directory `/home/hanzomon4/Desktop/exaile/mmkeys'
cp mmkeys/mmkeys.so .
cd po && python fmt.py && cd ..
python: can't open file 'fmt.py': [Errno 2] No such file or directory
make: *** [build] Error 2


```
I got past it in the exaile svn folder that I would update every now and then, but exaile said it was v0.2.2.
I tried your command and it said that I had the same  folder from a different url.
       So I deleted mine and ran the command again. When I got the error above I tried using my old work around. 
 ```
hanzomon4@EIDOKIN:~/.development/svn/exaile$ make -f trunk/Makefile 
```
but it didn't work this time cause that svn address you posted dosen't have the same directories in it.

So I just downloaded the src-tarball, and it made fine

should work now if you svn update.

---

### Post by hanzomon4 on 2006-09-11
That got it thanks. Great job everything works great, keep up the good work.

---

### Post by synic on 2006-09-11
> **maniacmusician said:**
> before i attempt a trunk version, do i have to uninstall my current exaile or does it just go over that? I want to do this as neatly as possibly

You don't need to uninstall, and if you find you don't like the svn version, you can just go back to the other without a problem.

Adam

---

### Post by hanzomon4 on 2006-09-12
Ok I noticed an issue with the album art collecter, it searches amazon and pops up the preview box but the box remains empty.
    
       Sometimes even the next box is clickable but the album art preview box remains empty.

---

### Post by synic on 2006-09-12
> **hanzomon4 said:**
> Ok I noticed an issue with the album art collecter, it searches amazon and pops up the preview box but the box remains empty.
    
       Sometimes even the next box is clickable but the album art preview box remains empty.

Any errors if you press CTRL+D ?

---

### Post by maniacmusician on 2006-09-12
thanks, adam.

how do i know when you've updated the svn?

edit: noticed a typo. Under "View" It says "Go to Play**l**ing Track" instead of playing.

---

### Post by hanzomon4 on 2006-09-12
No error, here's some of the out put

```
[10:48:04] cover thread started
[10:48:11] 346c2002e8c021700bcf53363acbc8ba.jpg
[10:48:12] 7755103d65d5861289818a0640188fa3.jpg
[10:48:13] d46712919e0e88ad9d5c632a67d41222.jpg
[10:48:13] 6f649d9aaf857905d5328373b9533afd.jpg
[10:48:13] e2f91462e6acf58e6fa12566b6268710.jpg
[10:48:13] 8d6a5e0bd70dbabde545416a7cc33469.jpg
[10:48:13] f4efcfbd40dc0a5ec1af46279a6c3cfc.jpg
[10:48:14] 1f2a54ee045c79ace8f307736f2d77c2.jpg
[10:48:14] 72ccf8c4dbb2b5ca58e1ce75db46cf53.jpg
[10:51:48] Aborted cover thread
```
I'm guessing the aborted is were I clicked cancel.

---

### Post by synic on 2006-09-12
> **maniacmusician said:**
> thanks, adam.

how do i know when you've updated the svn?

edit: noticed a typo. Under "View" It says "Go to Play**l**ing Track" instead of playing.

Hrmm, there's not really a way to publish it without a lot of work.  Just type svn update in the exaile directory every once in a while

---

### Post by synic on 2006-09-15
> **maniacmusician said:**
> sweet! you are amazing. i'm going to go download it right now. any other changes we should know about? because last time, you just kinda sneaked some changes in there.

edit: err i gather these changes havnt been implemented yet because there's no new download. is it in the svn? i don't know how to use those lol.

Hey, how is the scanning part working for you now?  Have you noticed any bugs with it?

---

### Post by maniacmusician on 2006-09-15
no I havn't, and I played for about 7 hours straight. no CPU spikes, it was all smooth sailing.

though I have to admit, i occasionally use amarok now that i'm in kd, it's nice. But i still find myself missing exaile lol. But it's a pain to use the svn version so sometimes I just 0.2.3 instead. I suppose I should make a launcher. 

when is 0.2.4 coming out?

---

### Post by synic on 2006-09-15
> **maniacmusician said:**
> no I havn't, and I played for about 7 hours straight. no CPU spikes, it was all smooth sailing.

though I have to admit, i occasionally use amarok now that i'm in kd, it's nice. But i still find myself missing exaile lol. But it's a pain to use the svn version so sometimes I just 0.2.3 instead. I suppose I should make a launcher. 

when is 0.2.4 coming out?

As soon as I feel that everything is working ok.  The last release had a few bugs that I had to make bugfix releases for, and I want to avoid that this time.

0.2.4 has the super fantastic streamripper integration.  <3 internet radio.

Adam

---

### Post by maniacmusician on 2006-09-15
^ streamripper??? that's the program that saves songs from internet radio onto your computer right? i was just going to start using that! you're a genius, my friend. does amarok have that? 


on another note, here's the post I actually came to make:
have you thought about forking your project to simultaneously create a tag editor to go along with your audio player? Exaile can already download images from Amazon...why not tags? A good tag editor is something that is sorely lacking in linux...easytag is so unstable, it crashes every time i try to download tags...and thats pretty much all i want to do.

I used Tag&Rename in windows...all I had to do was arrange the tracks in the correct order, click a button, enter the cd name and artist, click the right option from the list, and voila. I could appy the normal tags, and then some extra ones like the Label, Review, etc, and could even embedd an image into the ID3 tags! I kind of like the sound of Exaile Tag Editor being an addon to Exaile. but i know that this is a gargantuan task, and probably a pain in the *** to undertake. but it was just a thought.


I can't wait for 0.2.4, thanks for this great app.

---

### Post by synic on 2006-09-20
> **hanzomon4 said:**
> No error, here's some of the out put

```
[10:48:04] cover thread started
[10:48:11] 346c2002e8c021700bcf53363acbc8ba.jpg
[10:48:12] 7755103d65d5861289818a0640188fa3.jpg
[10:48:13] d46712919e0e88ad9d5c632a67d41222.jpg
[10:48:13] 6f649d9aaf857905d5328373b9533afd.jpg
[10:48:13] e2f91462e6acf58e6fa12566b6268710.jpg
[10:48:13] 8d6a5e0bd70dbabde545416a7cc33469.jpg
[10:48:13] f4efcfbd40dc0a5ec1af46279a6c3cfc.jpg
[10:48:14] 1f2a54ee045c79ace8f307736f2d77c2.jpg
[10:48:14] 72ccf8c4dbb2b5ca58e1ce75db46cf53.jpg
[10:51:48] Aborted cover thread
```
I'm guessing the aborted is were I clicked cancel.

This should be fixed in svn now.

---

### Post by synic on 2006-09-20
> **maniacmusician said:**
> ^ streamripper??? that's the program that saves songs from internet radio onto your computer right? i was just going to start using that! you're a genius, my friend. does amarok have that? 


on another note, here's the post I actually came to make:
have you thought about forking your project to simultaneously create a tag editor to go along with your audio player? Exaile can already download images from Amazon...why not tags? A good tag editor is something that is sorely lacking in linux...easytag is so unstable, it crashes every time i try to download tags...and thats pretty much all i want to do.

I used Tag&Rename in windows...all I had to do was arrange the tracks in the correct order, click a button, enter the cd name and artist, click the right option from the list, and voila. I could appy the normal tags, and then some extra ones like the Label, Review, etc, and could even embedd an image into the ID3 tags! I kind of like the sound of Exaile Tag Editor being an addon to Exaile. but i know that this is a gargantuan task, and probably a pain in the *** to undertake. but it was just a thought.


I can't wait for 0.2.4, thanks for this great app.

I'll have to see Tag&Rename on a windows box to get an idea.   Have you used Ex Falso ?

Adam

---

### Post by dolny on 2006-09-20
Great app, since I moved to XFCE from KDE, switched from Thunderbird to Sylpheed, Exaile took Amarok's place. Good job! Can't wait for new version!!!

---

### Post by hesee on 2006-09-20
Can I install Exaile for Edgy?

---

### Post by synic on 2006-09-20
> **hesee said:**
> Can I install Exaile for Edgy?

Dunno, I haven't tried it.  I would imagine it would work...

Adam

---

### Post by hesee on 2006-09-20
Ok, I tried. Not much experience with compiling, but make and make install seemed to be ok. But, couldn't start program:

heikki@edgy:~/exaile_0.2.3$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 30, in ?
    from pysqlite2 import dbapi2 as sqlite
ImportError: No module named pysqlite2

Any ideas?

Edit: I have python-pysqlite2 package installed. This package could be related to the problem? There seems to be problem with the package: I cannot do anything with it (reinstall/uninstall...) There's no different versions in edgy repo, so I can't downgrade...

---

### Post by maniacmusician on 2006-09-20
> **synic said:**
> I'll have to see Tag&Rename on a windows box to get an idea.   Have you used Ex Falso ?

Adam
I have, believe me, it doesn't even hold a candle to Tag&Rename. <-- it is basically like EasyTag (same capabilities), except stuff actually **works** in tag&rename. I can't give you the version that I have (it's commercial), but I suppose you could temporarily pirate it to get a feel for it.

actually, I think they have a demo. [digs up link] [http://www.softpointer.com/tr.htm](http://www.softpointer.com/tr.htm) <-- 30 day trial. i'm pretty sure it has full functionality during the trial. 


If you could actually pull this off, you'd be a god. There's no tag editor  in linux that I know of that has these capabilities, and is stable.

---

### Post by Johan! on 2006-09-20
[Mediamonkey]("http://www.mediamonkey.com/") is also a great mp3manager for windows, and it's free.

---

### Post by maniacmusician on 2006-09-20
yeah i used it on windows, it was good. but amarok and exaile are kind of better.

seriously, the only program i miss from windows is tag&rename. it sucks not being able to tag my mp3's automatically.

---

### Post by Johan! on 2006-09-20
It's really hard to find good tag-editors.
I found some programs, but they're all old, or not good enough.

[http://www.debain.org/software/cantus/](http://www.debain.org/software/cantus/)
[http://freshmeat.net/projects/audiotagtool/](http://freshmeat.net/projects/audiotagtool/)
[http://freshmeat.net/projects/jtagger/](http://freshmeat.net/projects/jtagger/)
[http://freshmeat.net/projects/prokyon3/](http://freshmeat.net/projects/prokyon3/)
[http://freshmeat.net/projects/easytag/](http://freshmeat.net/projects/easytag/)
[http://freshmeat.net/projects/smrt/](http://freshmeat.net/projects/smrt/)
[http://freshmeat.net/projects/mp3c/](http://freshmeat.net/projects/mp3c/)

I think that mp3c, smrt and easytag are the best programs i can find

---

### Post by maniacmusician on 2006-09-20
I havn't tried smrt, but easytag is a pretty crappy program. unstable, crashes almost every time I try to retrieve tags from Amazon (i've only succeeded once)

---

### Post by croak77 on 2006-09-20
> **maniacmusician said:**
> I havn't tried smrt, but easytag is a pretty crappy program. unstable, crashes almost every time I try to retrieve tags from Amazon (i've only succeeded once)

You sure you are talking about easytag? It has never crashed on me and it gets info via freedb not amazon. Cowbell uses amazon.

---

### Post by maniacmusician on 2006-09-20
[sorry] i didnt realize it used freedb. but yes i'm talking about easytag. It crashes everytime i try to download tags.

---

### Post by hesee on 2006-09-21
Response to my own question about problems with exaile in edgy:

There was a bug in python, which is now solved:
[https://launchpad.net/distros/ubuntu/+source/python-central/+bug/58915](https://launchpad.net/distros/ubuntu/+source/python-central/+bug/58915)

Exaile is running now just fine in Edgy! Thank you synic about this awesome app! I can now safely remove amarok, exaile integrates much better into gnome. =D>  

One little feature request:
When I quit amarok, it doesn't stop playing abruptly, but fades away during about one second.That would be a little nice feature to have in exaile too. :)


Edit: Oh, one little bug I noticed. When I click "Help" -> "About", the info window pops up, but don't go away if I click "Close"- I have to close the window from upper right corner

Edit again: You seem to have forum for bugs and feature requests, my bug seems to be already in the forums.

---

### Post by pulper on 2006-09-21
i started using it and enjoyed the lyrics and artist information.  couple of questions about the lyrics:

1.  once you download the lyrics for a song, are they now on the hard drive or do they need to get redownloaded afterwards again each time the song plays?
2.  is there a way to add your own lyrics for songs if the lyrics aren't being found on the net?

as far as album information, there is no differentiation between any of the greatest hits albums.  if i search for the correct album and find it, will it be remembered next time?  if not, any way to set this up?

thanks,

paul

---

### Post by dolny on 2006-09-22
It takes up a lot of CPU % and MEM on my computer, I think more than Amarok. Are you planning some optimizations? BTW Streamripper is a great idea. I e-mailed you. Didn't get the reply. Hope it reached you.

Another question, are you planning a feature that will add the songs from the podcasts you listen to last.fm? Like in Amarok.

I would like to suggest adding a possibility to tag favourite radio stations that would show up in separate folder.

---

### Post by maniacmusician on 2006-10-01
this thread has been Forgotten. i'm trying out 0.2.4 right now (a little late, yes) i'm sure it will be great.

adam, have you looked at tag&rename at all? i'm not trying to be pushy, just wondering are you considering the idea i proposed or not so much?

---

### Post by dolny on 2006-10-02
I tried to contact the author - no luck. :/
Wanted to do the polish translation and suggest some things.

---

### Post by cborga1985 on 2006-10-02
here is a amd64 package. you have to extract and install in using
```
sudo dpkg -i exaile_0.2.4-1_amd64.deb
```

finally a player that uses gnome but is easy to use like amarok :D 
keep up the good work, all it needs is dyanmic mode and i would use it as a full time player

---

### Post by maniacmusician on 2006-10-02
@dolny: in recent days, i've seen adam on the other exaile thread. i bumped this one in hopes that he'd stumble on it again today.

---

### Post by cborga1985 on 2006-10-02
> **cborga1985 said:**
> here is a amd64 package. you have to extract and install in using
```
sudo dpkg -i exaile_0.2.4-1_amd64.deb
```

finally a player that uses gnome but is easy to use like amarok :D 
keep up the good work, all it needs is dyanmic mode and i would use it as a full time player

anybody tried my package to verify it works on other systems?

---

### Post by synic on 2006-10-02
> **maniacmusician said:**
> this thread has been Forgotten. i'm trying out 0.2.4 right now (a little late, yes) i'm sure it will be great.

adam, have you looked at tag&rename at all? i'm not trying to be pushy, just wondering are you considering the idea i proposed or not so much?

It'd be very cool to have a nice tag editor... though I haven't been able to try tag & rename yet.

---

### Post by dolny on 2006-10-02
Synic, in my email to you I wrote about:
- being ready to do polish translation of the app and website
- suggested choosing your fav radio
- suggested an option, like in amarok: being able to enable sending the song information from the online radios to last.fm
- suggested something I don't remember atm

What is the best way to contact you?

---

### Post by synic on 2006-10-02
> **dolny said:**
> Synic, in my email to you I wrote about:
- being ready to do polish translation of the app and website
- suggested choosing your fav radio
- suggested an option, like in amarok: being able to enable sending the song information from the online radios to last.fm
- suggested something I don't remember atm

What is the best way to contact you?

You can do the translation - the messages.pot is [http://binary.twi.gs/messages.pot](http://binary.twi.gs/messages.pot)

- I'm not sure what you mean by choosing your fav radio
- currently, exaile will send played track information to last.fm

---

### Post by henriquemaia on 2006-10-02
Having tried exaile just now, I'm pretty amazed by the progress.

It's very usable for me. 

Just one thing:

I close the window and it minimizes to tray - sweet! But then I reopen the window and the window is always centered on the screen and not on the last place I left it. Amarok, for example, respect that.

---

### Post by dolny on 2006-10-03
You don't have permission to access /messages.pot on this server.

---

### Post by synic on 2006-10-03
> **dolny said:**
> You don't have permission to access /messages.pot on this server.

Ah, try it again

---

### Post by synic on 2006-10-03
> **henriquemaia said:**
> Having tried exaile just now, I'm pretty amazed by the progress.

It's very usable for me. 

Just one thing:

I close the window and it minimizes to tray - sweet! But then I reopen the window and the window is always centered on the screen and not on the last place I left it. Amarok, for example, respect that.

Ok, this is fixed in svn

---

### Post by DOD1951 on 2006-10-06
I am using Exaile ver 0.2b4 which is really great.
I am trying to use RAID 0 (long story!) and have copied all music files to it. Am now trying to add music file through library manager but noticed that i cannot delete the /home/name/Music folder but can add /mnt/raid/music folder however Exaile does not appear to be 'importing' the files to the library. Is it a requirement to have the music files in the /home folder? Ideally i just want the one place for all the music files.

---

### Post by synic on 2006-10-06
> **DOD1951 said:**
> I am using Exaile ver 0.2b4 which is really great.
I am trying to use RAID 0 (long story!) and have copied all music files to it. Am now trying to add music file through library manager but noticed that i cannot delete the /home/name/Music folder but can add /mnt/raid/music folder however Exaile does not appear to be 'importing' the files to the library. Is it a requirement to have the music files in the /home folder? Ideally i just want the one place for all the music files.

You should be using a newer version.  Try 0.2.4

---

### Post by cborga1985 on 2006-10-18
Latest Exaile svn as of 10/18/2006 for 64 here [http://www.ubuntuforums.org/attachment.php?attachmentid=17770&stc=1&d=1161172555]("http://www.ubuntuforums.org/attachment.php?attachmentid=17770&stc=1&d=1161172555")
unzip it and install it with
```
sudo dpkg -i exaile_20061018-1_amd64.deb
```

---

### Post by veli on 2006-10-20
> **synic said:**
> I just added a explicit garbage collect statement when you start playing a track.  I've been watching memory usage, and this seems to have helped.  Probably not a leak, just objects weren't getting gced right away.  It's in SVN - give it a try and let me know.

Adam

I tried one of the SVNs, not the last one because it complained about dependences on Dapper. The memory consumption seems stable within 31-47MB for about 2.5 hours continuos playing. For your info, with the normal 0.2.4 version .deb Ubuntu Dapper, I got memory increase with time. 

The memory usually goes up when opening the author info tab to around 50 MB. 

At this stage of the game, I'll give it a try. But the most important thing-stability now has been corrected. Thanks for your work and sharing it with us.

Keep on working on the player. Can it be ported into the repos or even being a default music manager in future Ubuntu releases? 

Regards, 

Veli

---

### Post by veli on 2006-10-20
I'd like to point few things about the new player.
In the information tab-autor for example, when the track moves forward, it automatically changes the author info as well.

I wish when I'm reading something in the author tab to stay ther until I decide, and not the player to change it when changing tracks. This is because while listening to music I'm browsing wiki for many other things in the player window. I can start from Queen and end up with National geographic, for example.

Also, the opening of the wiki page is a bit slow, and the memory goes up to around 70 MB . And stays there when I close the info tabs. (opss, it dropped down to 57 MB after some time) It would be better to release the memory in that case, or even it's best during any operations the memory consumption being at the same level, saying ideally around 30-40 MB. 

I also noticed that the library is being scanned at a specific time intervals, I don't know exactly. IMO, scanning the library at program start up would be enough.

Regards,

---

### Post by cborga1985 on 2006-10-24
> **veli said:**
> I tried one of the SVNs, not the last one because it complained about dependences on Dapper. The memory consumption seems stable within 31-47MB for about 2.5 hours continuos playing. For your info, with the normal 0.2.4 version .deb Ubuntu Dapper, I got memory increase with time. 

The memory usually goes up when opening the author info tab to around 50 MB. 

At this stage of the game, I'll give it a try. But the most important thing-stability now has been corrected. Thanks for your work and sharing it with us.

Keep on working on the player. Can it be ported into the repos or even being a default music manager in future Ubuntu releases? 

Regards, 

Veli

yeah i noticed the memory usage in latest svn went up allot. hopefully this can be fixed easily. lastest svn works ideally better to me so i still use it.

---

### Post by synic on 2006-10-24
> **veli said:**
> I'd like to point few things about the new player.
In the information tab-autor for example, when the track moves forward, it automatically changes the author info as well.

I wish when I'm reading something in the author tab to stay ther until I decide, and not the player to change it when changing tracks. This is because while listening to music I'm browsing wiki for many other things in the player window. I can start from Queen and end up with National geographic, for example.

Also, the opening of the wiki page is a bit slow, and the memory goes up to around 70 MB . And stays there when I close the info tabs. (opss, it dropped down to 57 MB after some time) It would be better to release the memory in that case, or even it's best during any operations the memory consumption being at the same level, saying ideally around 30-40 MB. 

I also noticed that the library is being scanned at a specific time intervals, I don't know exactly. IMO, scanning the library at program start up would be enough.

Regards,

There's an area in the preferences to turn it off.

Adam

---

### Post by cborga1985 on 2006-11-03
**Exaile 0.2.5b for Dapper(Amd64)**

Download package from [here]("http://ubuntuforums.org/attachment.php?attachmentid=18797&stc=1&d=1162572000"). Of course then unpack the archive using file-roller or similiar.

**then** in a terminal

```
sudo dpkg -i exaile_0.2.5b_amd64.deb
```

---

### Post by skrribble on 2007-07-15
is there anyway to get exaile to play .m3u or .pls playlist files.... i have playlists on my ipod and i've saved them as files to my machine, but cant seem to get them to open in exaile... i also cant get exaile to just play the playlist straight from the ipod using the ipod plugin ... .any help would be greatly appreciated

---

### Post by forestpixie on 2007-07-15
It seems to work allright here - open media and it'll import an mru. But maybe if you're trying to get a playlist from your ipod to work - could be it's looking in the wrong place, ie playlist refers to files on the ipod. My playlists refer to files on my pc?!
 
As far as getting an ipod to work with Exaile I have no idea even what they look like :D

---

