---
title: "New music player - Exaile!"
date: 2006-04-13
forum: The Cafe
---

### Post by synic on 2006-04-13
I released Exaile 0.2b2 today.  I really like Amarok, but I was hoping for a gtk+ alternative, so I started Exaile.  I know ... I know, there are tons of media players out there, but I see this as a fun way to learn python and gtk+.

Some screenshots can be found here:

[http://www.exaile.org](http://www.exaile.org)

It's beta, but if you're bored, check it out.  Here's what you'll need to do:

```

# sudo apt-get install python-gtk2 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
# wget http://www.exaile.org/files/exaile_0.2b4_i386.deb
# sudo dpkg -i exaile_0.2b4_i386.deb

```

.. and a new icon will show up in Applications->Sound and Video

Go to Tools->Library Manager, add your music directory, and away you go.

Optional:  If you want mp3 support, install gstreamer0.10-plugins-ugly, and if you want wma, install gstreamer0.10-ffmpeg

Feedback and comments are appreciated!

-synic

---

### Post by Seaman on 2006-04-13
It looks quite nice, you should try to get it into the repos.

A question, what does Exaile have that for example Banshee doesn't?

---

### Post by xXx 0wn3d xXx on 2006-04-13
I like it :) Very nice.

---

### Post by synic on 2006-04-13
re: banshee

It supports streams, automatic cover art, and queueing.  I don't think the banshee version in breezy has these.

---

### Post by renzokuken on 2006-04-13
install went fine

just importing my library now, i like the "random 100" function, gonna be the first thing i try.

ok, all working now, slapped on random 100 and first track up is Simple Minds - Dont You Forget About Me (Breakfast Club, awesome film)

anyways, all looks good, seems to have a bit more functionality than Listen which is good

EDIT: been playing for a bit now dude, i really like it, fast database, simple and effective

one question, how can i create a desktop launcher for this?

---

### Post by xXx 0wn3d xXx on 2006-04-13
[QUOTE=renzokuken]install went fine

just importing my library now, i like the "random 100" function, gonna be the first thing i try.

ok, all working now, slapped on random 100 and first track up is Simple Minds - Dont You Forget About Me (Breakfast Club, awesome film)

anyways, all looks good, seems to have a bit more functionality than Listen which is good

EDIT: been playing for a bit now dude, i really like it, fast database, simple and effective

one question, how can i create a desktop launcher for this?[/QUOTE]

Point the launcher to /home/USERNAME/exaile/exaile <= Replace the USERNAME with your username.

---

### Post by renzokuken on 2006-04-13
that doesnt work....does the run file not need the "./" in front of it to start

could i not make a link to it in /usr/bin then launch ./exaile

or write a little bash script for it?

---

### Post by endersshadow on 2006-04-13
[QUOTE=renzokuken]that doesnt work....does the run file not need the "./" in front of it to start

could i not make a link to it in /usr/bin then launch ./exaile

or write a little bash script for it?[/QUOTE]

You just need to point it to the executable.  Alternatively, you could do:

sudo ln -s /path/to/exaile /usr/bin/exaile

Then you'll be able to run it with just the command "exaile" (sans quotes) instead...going to install now :-D

First impressions:

I'm really impressed with this player.  You did a fantastic job with the interface and the features.  Below, I'm just collecting bugs that I've found and/or noticed for recordkeeping...but all in all fantastic job, and I'd love for this to continue to be improved!

-It doesn't show any other mounted drives in the Library Manager when you go to add a file.  For example, I've got 2 other mounted partitions that I had to go through root (/) to get to...not really a problem, but it might leave users who aren't sure where those are mounted a bit confused at first.

-Customizable smart playlists would be an *awesome* feature.

-My playlists disappear when I have multiple tabs open and I scroll between them...they just...become blank...

---

### Post by synic on 2006-04-13
[QUOTE=endersshadow]
-My playlists disappear when I have multiple tabs open and I scroll between them...they just...become blank...[/QUOTE]

Hrmm, if you have something typed into the filter box, it applies to all tabs - could this be what's happening?

---

### Post by Stormy Eyes on 2006-04-13
Nice work so far, **synic**. I had to write a script to cd to the install directory, but that's no problem. I'd suggest tweaking the cover fetching routine. The first cover that amazon.com returns isn't always the right one. For example, I played *Imaginos* by Blue Oyster Cult, but for some reason, Exaile used the cover from Blind Guardian's *Imaginations from the Other Side* album. Granted, I can easily set a custom cover, but I'm a bit spoiled by gmusicbrowser's offering me a choice of covers.

---

### Post by synic on 2006-04-13
[QUOTE=Stormy Eyes]Nice work so far, **synic**. I had to write a script to cd to the install directory, but that's no problem. I'd suggest tweaking the cover fetching routine. The first cover that amazon.com returns isn't always the right one. For example, I played *Imaginos* by Blue Oyster Cult, but for some reason, Exaile used the cover from Blind Guardian's *Imaginations from the Other Side* album. Granted, I can easily set a custom cover, but I'm a bit spoiled by gmusicbrowser's offering me a choice of covers.[/QUOTE]

You can right click on the cover to try a different search string.  I'll have to take a gander at gmusicbrowser.

---

### Post by endersshadow on 2006-04-13
[QUOTE=synic]Hrmm, if you have something typed into the filter box, it applies to all tabs - could this be what's happening?[/QUOTE]

Nah, it does it in a default state :-|

---

### Post by Lovechild on 2006-04-13
I believe I'll stay with Rhythmbox for now because Exaile visually makes very little sense to me.

---

### Post by flange on 2006-04-13
I think it looks nice.  It has a very clean, uncluttered layout.  I don't understand the metaphors for your tab icons, but overall I think it looks very appealing.  If you can continue down the Amarok path without bringing in the (IMHO) clutter that Amarok suffers from, it would make an excellent addition to the GTK media players available.  Great start!

---

### Post by synic on 2006-04-13
[QUOTE=Lovechild]I believe I'll stay with Rhythmbox for now because Exaile visually makes very little sense to me.[/QUOTE]

That's cool - I mostly wrote this to fit my needs - which I'm sure are mostly different than everyone elses.

---

### Post by synic on 2006-04-13
[QUOTE=flange]I think it looks nice.  It has a very clean, uncluttered layout.  I don't understand the metaphors for your tab icons, but overall I think it looks very appealing.  If you can continue down the Amarok path without bringing in the (IMHO) clutter that Amarok suffers from, it would make an excellent addition to the GTK media players available.  Great start![/QUOTE]

Yeah... I'm not an artist.  I basically just took icons from other apps.  

SO... if you are an artist, and want to help, let me know :)

---

### Post by flange on 2006-04-13
[QUOTE=synic]Yeah... I'm not an artist.  I basically just took icons from other apps.  

SO... if you are an artist, and want to help, let me know :)[/QUOTE]

Sadly, no.  I'm a techie.  My girlfriend says I'm a good photographer, but I think she's way too biased.  And that's about as artsy as I get.  

I'd be far more likely to help with the Python coding, but even with that, I'm just beginning.  I have some reasonable C/C++ experience, but I'm very rusty, and I'm just getting started with Python.

---

### Post by synic on 2006-04-13
[QUOTE=flange]Sadly, no.  I'm a techie.  My girlfriend says I'm a good photographer, but I think she's way too biased.  And that's about as artsy as I get.  

I'd be far more likely to help with the Python coding, but even with that, I'm just beginning.  I have some reasonable C/C++ experience, but I'm very rusty, and I'm just getting started with Python.[/QUOTE]

I think you'll really like it, especially after using C and C++.  I've only been coding in it for ~3 months, and I already know it's my favorite language by far.

---

### Post by Ultimo Aliento on 2006-04-13
Looks great !, i have a little problem adding my music folders with the library tool, the program say this :

[B]loading songs
Running is False
/home/seccion9/Shared
/home/seccion9/Compartidos
/home/seccion9/Incomplete
File count: 4
Traceback (most recent call last):
  File "/home/seccion9/exaile/xl/media.py", line 361, in read_tag
    audio = mad.MadFile(self.loc)
IOError: Object must have a read method
Traceback (most recent call last):
  File "/home/seccion9/exaile/xl/media.py", line 361, in read_tag
    audio = mad.MadFile(self.loc)
IOError: Object must have a read method
Count is now: 4
loading songs
Traceback (most recent call last):
  File "/home/seccion9/exaile/xl/librarychooser.py", line 85, in __OnRemove
    del self.items[indexes[0]]
IndexError: tuple index out of range
Running is False[/B]

Then, i just chose one folder, Exaile indexed one song (of two possible), and when i try to play the song, the program crash.

Keep working in this program! looks promising :D

---

### Post by drummer on 2006-04-13
It looks really nice in the screens, I'll certainly try it out one I get my computer fixed up :(

---

### Post by INMCM on 2006-04-13
I get the same problem as Ultimo, except on a much larger scale. I added my library of ~33000 songs and watching the terminal I see lots of

[B]Traceback (most recent call last):
  File "/home/inmcm/exaile/xl/media.py", line 350, in read_tag
    audio = mad.MadFile(self.loc)
IOError: Object must have a read method[/B]

at the end of scanning (very fast for the task it was given!!) I noticed the count was right

**Count is now: 33602**

but when I look at the track count in Exaile, it only shows 32919. 700ish track missing. I'm working on tracking down which tracks it baulked on, but it is taking some time with all these files to check.

Other than that, just needs to have some sort of tray thingie and it'll be super awesome!

---

### Post by jasay on 2006-04-14
Hmm.  I keep getting the following error:```
$ ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1356, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above exception.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1385, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1381, in main
    app.exaile = ExaileWindow(fr)
  File "exaile.py", line 128, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'esdsink'))
  File "/home/jasay/exaile/xl/media.py", line 43, in set_audio_sink
    player.set_property("audio-sink", audio_sink)
AttributeError: 'NoneType' object has no attribute 'set_property'

```  Any suggestions?  Might I need different/additional dependencies since I'm using Dapper?  I noticed a few guys are on Dapper as well.  Was there anything you had to do differently than in the OP to get it to work?

---

### Post by doclivingston on 2006-04-14
[QUOTE=synic]That's cool - I mostly wrote this to fit my needs - which I'm sure are mostly different than everyone elses.[/QUOTE]

Which is why we have so many different music players around - choice is a good thing.

Welcome to the ever-expanding club of music player hackers.

---

### Post by chronusdark on 2006-04-16
looks great can we expect ipod support in the future?

---

### Post by oxEz on 2006-04-17
I can confirm it works on Gentoo Linux. I had to emerge wxpython, wxgtk, pygtk, and PIL (Python Imaging Library), for the 'Image' module, otherwise Exaile  doesn't start. (the package is named 'imaging' in portage tree).

---

### Post by GarethMB on 2006-04-17
Right straight off this isn't picking up all my media on my PC. ; ;

Also, i beg anyone who is going to develop a media player...include a graphic EQ. 
Its a shame that this isn't detecting all my music, because it seems to be the closest thing i've found yet to my favourite media player Musik Cube.

```
gareth@ubuntu:~/exaile$ cd exaile && ./exaile
bash: cd: exaile: Not a directory
gareth@ubuntu:~/exaile$ svn checkout svn://jbother.org/usr/local/svn/exaile
svn: 'exaile' is already a file/something else
gareth@ubuntu:~/exaile$ cd exaile && ./exaile
bash: cd: exaile: Not a directory
gareth@ubuntu:~/exaile$ exaile
bash: exaile: command not found
gareth@ubuntu:~/exaile$ ./exaile
loading songs
Importing /home/gareth/.exaile/saved_playlist.m3u
Running is False
/media/hda3/gareth/Music
File count: 178
Traceback (most recent call last):
  File "/home/gareth/exaile/xl/tracks.py", line 248, in read_track
    tr.read_tag()
  File "/home/gareth/exaile/xl/media.py", line 404, in read_tag
    f = ogg.vorbis.VorbisFile(self.loc)
TypeError: Argument 1 is not a filename or file object
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/home/gareth/exaile/xl/tracks.py", line 317, in run
    for root, dirs, files in os.walk(dir):
  File "/usr/lib/python2.4/os.py", line 291, in walk
    for x in walk(path, topdown, onerror):
  File "/usr/lib/python2.4/os.py", line 291, in walk
    for x in walk(path, topdown, onerror):
  File "/usr/lib/python2.4/os.py", line 281, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xa0 in position 10: ordinal not in range(128)

Exanding
Exanding
Exanding
Running is True
Running is True
new thread created with Various - Kill Bill: Volume 1 [Enhanced] [Explicit Lyrics] [Soundtrack]
cover thread started
Thread done.... *shrug*, no covers found
Aborted cover thread
playing has been stopped on 'Sword Swings'
gareth@ubuntu:~/exaile$ ./exaile
loading songs
Importing /home/gareth/.exaile/saved_playlist.m3u
Running is False
/media/hda3/gareth/Music
File count: 178
Traceback (most recent call last):
  File "/home/gareth/exaile/xl/tracks.py", line 248, in read_track
    tr.read_tag()
  File "/home/gareth/exaile/xl/media.py", line 404, in read_tag
    f = ogg.vorbis.VorbisFile(self.loc)
TypeError: Argument 1 is not a filename or file object
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/home/gareth/exaile/xl/tracks.py", line 317, in run
    for root, dirs, files in os.walk(dir):
  File "/usr/lib/python2.4/os.py", line 291, in walk
    for x in walk(path, topdown, onerror):
  File "/usr/lib/python2.4/os.py", line 291, in walk
    for x in walk(path, topdown, onerror):
  File "/usr/lib/python2.4/os.py", line 281, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xa0 in position 10: ordinal not in range(128)


```

Thats your bug.

---

### Post by kaamos on 2006-04-17
This project looks great. Thanks for the effort!

---

### Post by ShanghaiTeej on 2006-04-18
Installed it and am impressed.  The queue manager aspect of Amarok is why I keep using it.  Nice to see that same functionality in a Gnome music player.  Ipod support would be wonderful!

---

### Post by graabein on 2006-04-18
Looks interesting. I use XMMS and Banshee at the moment. Some questions:

1) Have you thought about adding toggle support for a smaller winamp-like GUI? You know, the best of two worlds?

2) Can you browse by artist and albums like iTunes and Rythmbox?

3) How about Last.fm/Audioscrobbler plugin?

Good luck with this project! :D

---

### Post by synic on 2006-04-18
[QUOTE=graabein]Looks interesting. I use XMMS and Banshee at the moment. Some questions:

1) Have you thought about adding toggle support for a smaller winamp-like GUI? You know, the best of two worlds?

2) Can you browse by artist and albums like iTunes and Rythmbox?

3) How about Last.fm/Audioscrobbler plugin?

Good luck with this project! :D[/QUOTE]

1) I have thought about a mini-gui - so yeah, that'll be in in the future.
2) Yes
3) Already in and working like a charm (last.fm prefs)

---

### Post by synic on 2006-04-18
[QUOTE=chronusdark]looks great can we expect ipod support in the future?[/QUOTE]


Eventually.  I'll probably add zen micro support, first (as I don't actually own an iPod).

---

### Post by Sheinar on 2006-04-18
Edit: Nevermind, realised I was missing pyxml.

Pretty nice player. Shows a lot of promise. Most gtk music players make me want to scream at how much the interface stabs at my eyes (Rhythmbox for example.)

Seems to take quite a while longer than I'm used to to import my music though, but I assume that's because of SQLite. An option to use an alternative database would be nice.

---

### Post by Omnios on 2006-04-18
Very interesting player though it crashed it looks real good. There is a few things missing in Linux and one of them is music file support where you can brouse through files and shares that contain music guess you could do a bookmark type thing where you can go through your music collection using files as I personaly and many others keep there genders in different files. 

 Also I am looking forward to Zen support though Gnomad2 is pretty good having a player that does it may be better.

---

### Post by synic on 2006-05-09
Lots of changes.... including shoutcast directory support!

Last week someone broke into my car and stole my creative zen micro. (and various other items). I've finally gone to the dark side and purchased an iPod.

So... Exaile now has iPod support.  Included in the svn repository is a python-gpod.deb for dapper in the debs/ dir.

Disclaimer:  Exaile does not currently modify anything on the iPod as far as I can tell, however, there might be something I'm overlooking.  Use at your own risk.

New screenshots can be seen at [http://www.exaile.org]("http://www.exaile.org")

---

### Post by nalmeth on 2006-05-09
How about lyric fetching? This is why listen is my music player right now.
Also, I would be at your feet if you made a "guitar player's" version that fetched tabulatures for songs as well.
I've always thought that would be REALLY COOL ;) ;) nudge nudge

---

### Post by synic on 2006-05-09
Exaile will eventually support lyric fetching and wikipedia...

I like the idea of the tablature feature (I play the guitar too).  Super idea, and yeah, I'll put it in as soon as I can.  Do you have a preferred site for getting tabs?  I use harmony-central...

On a side note:  "listen" is a great player, and I think underused. So... here is a blatant ad:  Seriously, check it out if you haven't already:  [http://listengnome.free.fr]("http://listengnome.free.fr").  I found it by accident whilst perusing the quodlibet site and had never heard of it before... which is suprising to me because it's such a nice app.

---

### Post by DoktorSeven on 2006-05-09
This is a really cool player.  So far, my only problem was that the preferences dialog wouldn't close with OK (therefore losing my preferences) because I didn't have iPod support:

```

Traceback (most recent call last):
  File "/home/stephen/source/exaile/xl/prefs.py", line 369, in __Apply
    panel.Apply()
  File "/home/stephen/source/exaile/xl/prefs.py", line 134, in Apply
    self.settings['ipod_mount'] = self.mount.GetValue()
AttributeError: 'iPodPrefs' object has no attribute 'mount'

```

As a quick solution I just hacked prefs.py, removing the references in def Apply(self) under the iPodPrefs class to the ipod values and replacing them with dummy values (0).  Seems to work fine now.

Edit: I guess a more permanent solution would be to do the dummy values in an **if not IPOD_AVAILABLE:** block and have the real settings in the **else:** clause.  But I'm lazy :)

---

### Post by synic on 2006-05-09
Ah, thanks for the input.  This should be fixed now.

---

### Post by nalmeth on 2006-05-10
fretplay.com seems to have a lot of songs I'm looking for.
I don't like ultimateguitar with all the flash and crap, but it always bails me out when I start to hate it :)
I always thought harmony-central was kind of, weird? It does have a lot of tabs though.
Seriously man, you would be my god if you could pull this out.
I don't know much about programming, but I imagine the difficulty would be in getting a text friendly site with reliable tabs.
I will help you look around for an appropriate site for testing, if you'd like.
I agree listen is super, but one thing that *really* bugs me (and seems absent from exaile :) ) is the stupid white bar/panel in the middle, which takes up all that space, and doesn't even allow you to drag playlists into it to save, or anything. It drives me nuts lookin at it, but otherwise it's such a good player I can look past it.

---

### Post by mpmc on 2006-05-11
Well, What can, I say.. Brilliant..

A few thing you could consider?

1: Add an option to auto play the track you've added to the playlist (Adding it to the top of the list to continue playback, next track etc)

2: Lyric Support, If you visit leoslyrics.com (Ask in the forums how to use his database He will email you, Or, I can give you the info, If you like, It's xml)

3: Mini GUI (Already requested)

4: Tray Icon... (really useful)

Other than those simple things, I love it... Just what I was looking for...

Keep it up, Loving the 'bloatless' feeling :-D

Edit:

Just noticed the program toolbar doesn't update correctly..

---

### Post by synic on 2006-05-11
Thanks :)

There's actually already a tray icon, you just have to enable it in the preferences (wx design rules say you should have it disabled by default).

I emailed the leoslyrics admin, but never got a response - so yeah, if you have the info, that'd be great.

The rest will eventually be in there :)

---

### Post by easyease on 2006-05-11
very nice thanks! just one thing......is there any way it can use streamripper to rip streams? youve done a great job of it. :-D

---

### Post by AndyCooll on 2006-05-11
Would like to try it but alays get the following error. Anyone able to help me fix this?

```
root@snoopy:~# cd exaile && ./exaile
Traceback (most recent call last):
  File "exaile.py", line 1680, in main
    bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 206, in __init__
    Bus.__init__(self, Bus.TYPE_SESSION)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 71, in __init__
    self._connection = dbus_bindings.bus_get(bus_type)
  File "dbus_bindings.pyx", line 1501, in dbus_bindings.bus_get
DBusException: No reply within specified time
***** You can safely ignore the above error.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1724, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1716, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 97, in __init__
    session_bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 206, in __init__
    Bus.__init__(self, Bus.TYPE_SESSION)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 71, in __init__
    self._connection = dbus_bindings.bus_get(bus_type)
  File "dbus_bindings.pyx", line 1501, in dbus_bindings.bus_get
dbus_bindings.DBusException: No reply within specified time
```

---

### Post by synic on 2006-05-12
> 
```

root@snoopy:~# cd exaile && ./exaile

```


Perhaps because you're running it as root?  I'm really not sure.

---

### Post by GarethMB on 2006-05-12
I cant import all of my library. I get this:

```
gareth@ubuntu:~$ cd exaile && ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1684, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
loading songs
mmkeys are available... running gtk.main()
Running is False
/media/hda3/gareth/Music
File count: 179
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/home/gareth/exaile/xl/tracks.py", line 368, in run
    for root, dirs, files in os.walk(dir):
  File "/usr/lib/python2.4/os.py", line 291, in walk
    for x in walk(path, topdown, onerror):
  File "/usr/lib/python2.4/os.py", line 291, in walk
    for x in walk(path, topdown, onerror):
  File "/usr/lib/python2.4/os.py", line 281, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode byte 0xa0 in position 10: unexpected code byte
```

Which is a shame because the interface seems really nice.

---

### Post by mpmc on 2006-05-12
synic:

I've tried to send you the info but it bounces back (email)

I've added you to MSN, but your offline...

---

### Post by UbuWu on 2006-05-12
Great work! With Dapper getting ready for release very soon, it would probably be a good idea to port it over to gstreamer 0.10 instead of 0.8.

---

### Post by ShanghaiTeej on 2006-05-12
Love the player...

I was just wondering when podcast support might be available.  Otherwise, I'm enjoying the work!  Much Thanks.

---

### Post by zenwhen on 2006-05-12
Great work! This is the first player other than MPD that handles my music library without crashing. :) I happen to really like the interface too.

---

### Post by yb1011 on 2006-05-13
Thanks synic! I really like this and hope you keep this up for Dapper :)

PS- Guys... is starting the player via the terminal the only way to run it? I cant see it in my menu and have no idea how to create a launcher for this player. Can someone explain it to me in noob terms? Please :)

Thank you.

---

### Post by ShanghaiTeej on 2006-05-13
[QUOTE=yb1011]Thanks synic! I really like this and hope you keep this up for Dapper :)

PS- Guys... is starting the player via the terminal the only way to run it? I cant see it in my menu and have no idea how to create a launcher for this player. Can someone explain it to me in noob terms? Please :)

Thank you.[/QUOTE]

Well, you've probably noticed an Exaile folder in your Home folder now.  All you have to do is drag the file "exaile" into your applications bar at the top (assuming you are using Gnome) and voila...you have a graphial link.

---

### Post by mikaPELL on 2006-05-15
This happens when I try to load my database...
```
loading songs
mmkeys are available... running gtk.main()
Running is False
/home/mikapell/knato/mp3
File count: 0
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/home/mikapell/exaile/xl/tracks.py", line 368, in run
    for root, dirs, files in os.walk(dir):
  File "/usr/lib/python2.4/os.py", line 281, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode byte 0x86 in position 1: unexpected code byte


```

Except from the fact that I can't listen to my music, it truly looks great!

---

### Post by synic on 2006-05-15
[QUOTE=mikaPELL]This happens when I try to load my database...
```
loading songs
mmkeys are available... running gtk.main()
Running is False
/home/mikapell/knato/mp3
File count: 0
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.4/threading.py", line 442, in __bootstrap
    self.run()
  File "/home/mikapell/exaile/xl/tracks.py", line 368, in run
    for root, dirs, files in os.walk(dir):
  File "/usr/lib/python2.4/os.py", line 281, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode byte 0x86 in position 1: unexpected code byte


```

Except from the fact that I can't listen to my music, it truly looks great![/QUOTE]

Hopefully this problem is fixed.  It still might skip files with weird characters in the path name, so renaming the file will probably work

---

### Post by mikaPELL on 2006-05-17
It worked great now. Your program rules!

---

### Post by Ob1 on 2006-05-17
Is your code open source or an executable file?

---

### Post by synic on 2006-05-17
[QUOTE=Ob1]Is your code open source or an executable file?[/QUOTE]

Open source of course :)

---

### Post by tenshi-no-shi on 2006-05-18
One problem I can see that needs to be fixed is well the library hates anything songs with spaces in it's name. All of my songs are like that, so I am going to have to rename EVERY song in my library to get is working (which I am not, since I only really listen to streams and mplayer in term is all I need for that), but other than that it looks promising, I will probably use it a lot more of the bugs are ironed out.

---

### Post by synic on 2006-05-18
[QUOTE=tenshi-no-shi]One problem I can see that needs to be fixed is well the library hates anything songs with spaces in it's name. All of my songs are like that, so I am going to have to rename EVERY song in my library to get is working (which I am not, since I only really listen to streams and mplayer in term is all I need for that), but other than that it looks promising, I will probably use it a lot more of the bugs are ironed out.[/QUOTE]

I have spaces in almost all of my filenames.  What specific problem are you encountering?

---

### Post by tenshi-no-shi on 2006-05-18
Strange, well anyways when I add my music folder to the music library list it finds all the files then promptly does not register any in the library.

---

### Post by zachtib on 2006-05-18
i get this error (on dapper)
```

zach@notapowerbook:~/exaile$ ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1796, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1839, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1830, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 102, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'esdsink'))
  File "/home/zach/exaile/xl/media.py", line 50, in set_audio_sink
    player.set_property("audio-sink", audio_sink)
AttributeError: 'NoneType' object has no attribute 'set_property'
zach@notapowerbook:~/exaile$

```

---

### Post by synic on 2006-05-18
[QUOTE=zachtib]i get this error (on dapper)
```

zach@notapowerbook:~/exaile$ ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1796, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1839, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1830, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 102, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'esdsink'))
  File "/home/zach/exaile/xl/media.py", line 50, in set_audio_sink
    player.set_property("audio-sink", audio_sink)
AttributeError: 'NoneType' object has no attribute 'set_property'
zach@notapowerbook:~/exaile$

```[/QUOTE]

To fix this error on Dapper, apt-get install gstreamer0.8-plugins and restart exaile.

---

### Post by synic on 2006-05-18
[QUOTE=tenshi-no-shi]Strange, well anyways when I add my music folder to the music library list it finds all the files then promptly does not register any in the library.[/QUOTE]

Are you running it from the command line?  If so, do you see any errors?

---

### Post by Sheinar on 2006-05-18
I keep getting this error when I try to run it on Arch.

```

Traceback (most recent call last):
  File "exaile.py", line 1759, in main
    bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1695, in dbus_bindings.bus_get
DBusException: Unable to determine the address of the message bus
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "exaile.py", line 1806, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1797, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 98, in __init__
    session_bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1695, in dbus_bindings.bus_get
dbus_bindings.DBusException: Unable to determine the address of the message bus

```

---

### Post by synic on 2006-05-18
[QUOTE=Sheinar]I keep getting this error when I try to run it on Arch.

```

Traceback (most recent call last):
  File "exaile.py", line 1759, in main
    bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1695, in dbus_bindings.bus_get
DBusException: Unable to determine the address of the message bus
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "exaile.py", line 1806, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1797, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 98, in __init__
    session_bus = dbus.SessionBus()
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 266, in __new__
    return Bus.__new__(cls, Bus.TYPE_SESSION, use_default_mainloop, private)
  File "/usr/lib/python2.4/site-packages/dbus/_dbus.py", line 99, in __new__
    bus._connection = dbus_bindings.bus_get(bus_type, private)
  File "dbus_bindings.pyx", line 1695, in dbus_bindings.bus_get
dbus_bindings.DBusException: Unable to determine the address of the message bus

```[/QUOTE]

Sounds like you don't have dbus running.  I can't exactly remember how Arch's init system works, but it seems like it's /etc/rc.d/dbus start or something similar to get it going... if you have it installed.

I've just made an update that will make it so that exaile can run even if dbus isn't, you can svn update and try and see if that works.  Note, that without dbus running, you'll probably end up getting multiple instances of exaile if you try to stream to it by clicking on a link in firefox or from streamtuner.

Adam

---

### Post by Sheinar on 2006-05-18
I actually tried it with dbus a while ago and it still wouldn't run. A different error message though, so I guess at least the problem isn't from not running with dbus enabled. I probably should have posted the other one instead. Anyway...

With dbus:
```

[sheinar@nespithe exaile]$ dbus-launch ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1763, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "exaile.py", line 1806, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1797, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 139, in __init__
    self.__SetupLeft()
  File "exaile.py", line 451, in __SetupLeft
    self.radio_panel = panels.RadioPanel(self.tools_nb, self)
  File "/home/sheinar/exaile/xl/panels.py", line 954, in __init__
    cur.execute("SELECT radio_name FROM radio "
pysqlite2.dbapi2.OperationalError: no such table: radio
```

I'm assuming running a dbus enabled X session and running the program through dbus-launch wont make any difference.

---

### Post by synic on 2006-05-19
[QUOTE=Sheinar]I actually tried it with dbus a while ago and it still wouldn't run. A different error message though, so I guess at least the problem isn't from not running with dbus enabled. I probably should have posted the other one instead. Anyway...

With dbus:
```

[sheinar@nespithe exaile]$ dbus-launch ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1763, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "exaile.py", line 1806, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1797, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 139, in __init__
    self.__SetupLeft()
  File "exaile.py", line 451, in __SetupLeft
    self.radio_panel = panels.RadioPanel(self.tools_nb, self)
  File "/home/sheinar/exaile/xl/panels.py", line 954, in __init__
    cur.execute("SELECT radio_name FROM radio "
pysqlite2.dbapi2.OperationalError: no such table: radio
```

I'm assuming running a dbus enabled X session and running the program through dbus-launch wont make any difference.[/QUOTE]

Sounds like I've changed the SQL schema since you last used it.  I'd rm ~/.exaile/music.db.  Exaile will automatically create it again.

---

### Post by Sheinar on 2006-05-19
Ah, that worked. Thanks. Simple.

---

### Post by jasay on 2006-05-19
I've been getting the same error for a several days now.  It looks exactly like Sheinar's (except for line #'s), but I don't have a music.db to delete (never did get it running to create one).```
$ ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1816, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "exaile.py", line 1859, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1850, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 144, in __init__
    self.__SetupLeft()
  File "exaile.py", line 468, in __SetupLeft
    self.radio_panel = panels.RadioPanel(self.tools_nb, self)
  File "/home/jasay/exaile/xl/panels.py", line 949, in __init__
    cur.execute("SELECT radio_name FROM radio "
pysqlite2.dbapi2.OperationalError: no such table: radio

```

---

### Post by synic on 2006-05-19
[QUOTE=jasay]I've been getting the same error for a several days now.  It looks exactly like Sheinar's (except for line #'s), but I don't have a music.db to delete (never did get it running to create one).```
$ ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
Traceback (most recent call last):
  File "exaile.py", line 1816, in main
    iface.TestService("testing dbus service")
  File "/usr/lib/python2.4/site-packages/dbus/proxies.py", line 79, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)  File "dbus_bindings.pyx", line 458, in dbus_bindings.Connection.send_with_reply_and_block
DBusException: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "exaile.py", line 1859, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1850, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 144, in __init__
    self.__SetupLeft()
  File "exaile.py", line 468, in __SetupLeft
    self.radio_panel = panels.RadioPanel(self.tools_nb, self)
  File "/home/jasay/exaile/xl/panels.py", line 949, in __init__
    cur.execute("SELECT radio_name FROM radio "
pysqlite2.dbapi2.OperationalError: no such table: radio

```[/QUOTE]

That message indicates that you /have/ to have a music.db:  rm ~/.exaile/music.db - you wouldn't have gotten that far if you didn't have one.

---

### Post by synic on 2006-05-19
UPDATED:

Exaile now has wikipedia search support for Artist and/or album, lyrics support via leoslyrics.com, and initial tablature support via fretplay.com.

The lyrics were pretty much the last feature I wanted in before I feature freeze to get rid of all the bugs and make a release.

Thanks for your help folks!

---

### Post by bored2k on 2006-05-19
Does it support last.fm? That's a huge one.

---

### Post by jasay on 2006-05-19
[QUOTE=synic]That message indicates that you /have/ to have a music.db:  rm ~/.exaile/music.db - you wouldn't have gotten that far if you didn't have one.[/QUOTE]
Ah, I didn't see the hidden folder in your directions. Sorry.  /Hangs head in shame.:oops: 

Works great.  Thanks a lot.:D

---

### Post by synic on 2006-05-19
[QUOTE=bored2k]Does it support last.fm? That's a huge one.[/QUOTE]

Yeah

---

### Post by Lord Illidan on 2006-05-19
Are you planning any visuals and the like?
Also, can we change lyrics engine?

My only problem is that it feels a bit sluggish. Is this down to python?

Otherwise, this seems like an awesome piece of work. When are you planning to release it in the repos?

I spoke too soon, it seems. Lyrics don't work.
It also failed to save music collection.

---

### Post by synic on 2006-05-19
[QUOTE=Lord Illidan]Are you planning any visuals and the like?
Also, can we change lyrics engine?

My only problem is that it feels a bit sluggish. Is this down to python?

Otherwise, this seems like an awesome piece of work. When are you planning to release it in the repos?

I spoke too soon, it seems. Lyrics don't work.
It also failed to save music collection.[/QUOTE]

When's the last time you ran an svn update?  I only put the lyrics in today.

---

### Post by Lord Illidan on 2006-05-19
[quote=synic]When's the last time you ran an svn update?  I only put the lyrics in today.[/quote]

I installed it today.

---

### Post by synic on 2006-05-19
[QUOTE=Lord Illidan]I installed it today.[/QUOTE]

Try svn updating.  When you say "don't work", how do you mean?  It says it can't find them?  What artist/songtitle are you trying?

---

### Post by patbuntu on 2006-05-19
I want to try this.  From the first post:

```

# apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad gstreamer0.8-mad python-gst subversion
# svn checkout svn://jbother.org/usr/local/svn/exaile
# cd exaile && ./exaile

```

I get this:

```

pat@cube:~$ sudo apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad gstreamer0.8-mad python-gst subversion
Password:
Reading package lists... Done
Building dependency tree... Done
python-wxgtk2.6 is already the newest version.
gstreamer0.8-mad is already the newest version.
python-gst is already the newest version.
The following extra packages will be installed:
  libsvn0
Suggested packages:
  subversion-tools db4.3-util
The following NEW packages will be installed
  libsvn0 python-pymad python-pysqlite2 subversion
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 725kB of archives.
After unpacking 4432kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com dapper/main libsvn0 1.3.1-3ubuntu1 [513kB]
Get: 2 http://gb.archive.ubuntu.com dapper/universe python-pymad 0.5.4-1ubuntu3 [5560B]
Get: 3 http://gb.archive.ubuntu.com dapper/main python-pysqlite2 2.0.5-1ubuntu1 [3012B]
Get: 4 http://gb.archive.ubuntu.com dapper/main subversion 1.3.1-3ubuntu1 [203kB]
Fetched 725kB in 5s (125kB/s)
Selecting previously deselected package libsvn0.
(Reading database ... 128215 files and directories currently installed.)
Unpacking libsvn0 (from .../libsvn0_1.3.1-3ubuntu1_i386.deb) ...
Selecting previously deselected package python-pymad.
Unpacking python-pymad (from .../python-pymad_0.5.4-1ubuntu3_all.deb) ...
Selecting previously deselected package python-pysqlite2.
Unpacking python-pysqlite2 (from .../python-pysqlite2_2.0.5-1ubuntu1_all.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.3.1-3ubuntu1_i386.deb) ...
Setting up libsvn0 (1.3.1-3ubuntu1) ...

Setting up python-pymad (0.5.4-1ubuntu3) ...
Setting up python-pysqlite2 (2.0.5-1ubuntu1) ...
Setting up subversion (1.3.1-3ubuntu1) ...
pat@cube:~$ svn checkout svn://jbother.org/usr/local/svn/exaile
A    exaile/.clean
A    exaile/mutagen
A    exaile/mutagen/_constants.py
A    exaile/mutagen/apev2.py
A    exaile/mutagen/mp3.py
A    exaile/mutagen/__init__.py
A    exaile/mutagen/id3.py
A    exaile/mutagen/_vorbis.py
A    exaile/mutagen/flac.py
A    exaile/license.txt
A    exaile/font.ttf
A    exaile/xl
A    exaile/xl/common.py
A    exaile/xl/shoutcast.py
A    exaile/xl/scrobbler.py
A    exaile/xl/dbusinterface.py
A    exaile/xl/prefs.py
A    exaile/xl/media.py
A    exaile/xl/xlmisc.py
A    exaile/xl/__init__.py
A    exaile/xl/covers.py
A    exaile/xl/panels.py
A    exaile/xl/trackslist.py
A    exaile/xl/track.py
A    exaile/xl/config.py
A    exaile/xl/tracks.py
A    exaile/db.sql
A    exaile/mmkeys
A    exaile/mmkeys/mmkeys.override
A    exaile/mmkeys/mmkeys.defs
A    exaile/mmkeys/MANIFEST
A    exaile/mmkeys/mmkeys.c
A    exaile/mmkeys/setup.py
A    exaile/mmkeys/COPYING
A    exaile/mmkeys/mmkeys.h
A    exaile/mmkeys/mmkeysmodule.c
A    exaile/mmkeys/README
A    exaile/mmkeys/Makefile
A    exaile/mmkeys.so
A    exaile/images
A    exaile/images/remove.png
A    exaile/images/refresh.png
A    exaile/images/player-play.png
A    exaile/images/album.png
A    exaile/images/genre.png
A    exaile/images/player-volume.png
A    exaile/images/delete.png
A    exaile/images/track.png
A    exaile/images/artist.png
A    exaile/images/player-prev.png
A    exaile/images/player-pause.png
A    exaile/images/player-next.png
A    exaile/images/folder.png
A    exaile/images/nocover.png
A    exaile/images/playlist_ipod.png
A    exaile/images/media-audiofile.png
A    exaile/images/player-stop.png
A    exaile/images/exailelogo-sml.png
A    exaile/images/clear.png
A    exaile/images/add.png
A    exaile/images/lite/icon.png
A    exaile/images/ipod.png
A    exaile/exaile
A    exaile/debs
A    exaile/debs/python-gpod_0.3-1_i386.deb
A    exaile/exaile.py
Checked out revision 913.
pat@cube:~$ cd exaile && ./exaile
Traceback (most recent call last):
  File "exaile.py", line 28, in ?
    from xl import *
  File "/home/pat/exaile/xl/config.py", line 17, in ?
    import fileinput, traceback, xlmisc
  File "/home/pat/exaile/xl/xlmisc.py", line 18, in ?
    import trackslist, tracks, covers, md5, threading, re
  File "/home/pat/exaile/xl/trackslist.py", line 19, in ?
    from xl import xlmisc, common, track, tracks
ImportError: cannot import name xlmisc

```

Now what?

Cheers

-Pat

---

### Post by synic on 2006-05-19
[QUOTE=patbuntu]I want to try this.  From the first post:

```

# apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad gstreamer0.8-mad python-gst subversion
# svn checkout svn://jbother.org/usr/local/svn/exaile
# cd exaile && ./exaile

```

I get this:

```

pat@cube:~$ sudo apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad gstreamer0.8-mad python-gst subversion
Password:
Reading package lists... Done
Building dependency tree... Done
python-wxgtk2.6 is already the newest version.
gstreamer0.8-mad is already the newest version.
python-gst is already the newest version.
The following extra packages will be installed:
  libsvn0
Suggested packages:
  subversion-tools db4.3-util
The following NEW packages will be installed
  libsvn0 python-pymad python-pysqlite2 subversion
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 725kB of archives.
After unpacking 4432kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com dapper/main libsvn0 1.3.1-3ubuntu1 [513kB]
Get: 2 http://gb.archive.ubuntu.com dapper/universe python-pymad 0.5.4-1ubuntu3 [5560B]
Get: 3 http://gb.archive.ubuntu.com dapper/main python-pysqlite2 2.0.5-1ubuntu1 [3012B]
Get: 4 http://gb.archive.ubuntu.com dapper/main subversion 1.3.1-3ubuntu1 [203kB]
Fetched 725kB in 5s (125kB/s)
Selecting previously deselected package libsvn0.
(Reading database ... 128215 files and directories currently installed.)
Unpacking libsvn0 (from .../libsvn0_1.3.1-3ubuntu1_i386.deb) ...
Selecting previously deselected package python-pymad.
Unpacking python-pymad (from .../python-pymad_0.5.4-1ubuntu3_all.deb) ...
Selecting previously deselected package python-pysqlite2.
Unpacking python-pysqlite2 (from .../python-pysqlite2_2.0.5-1ubuntu1_all.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.3.1-3ubuntu1_i386.deb) ...
Setting up libsvn0 (1.3.1-3ubuntu1) ...

Setting up python-pymad (0.5.4-1ubuntu3) ...
Setting up python-pysqlite2 (2.0.5-1ubuntu1) ...
Setting up subversion (1.3.1-3ubuntu1) ...
pat@cube:~$ svn checkout svn://jbother.org/usr/local/svn/exaile
A    exaile/.clean
A    exaile/mutagen
A    exaile/mutagen/_constants.py
A    exaile/mutagen/apev2.py
A    exaile/mutagen/mp3.py
A    exaile/mutagen/__init__.py
A    exaile/mutagen/id3.py
A    exaile/mutagen/_vorbis.py
A    exaile/mutagen/flac.py
A    exaile/license.txt
A    exaile/font.ttf
A    exaile/xl
A    exaile/xl/common.py
A    exaile/xl/shoutcast.py
A    exaile/xl/scrobbler.py
A    exaile/xl/dbusinterface.py
A    exaile/xl/prefs.py
A    exaile/xl/media.py
A    exaile/xl/xlmisc.py
A    exaile/xl/__init__.py
A    exaile/xl/covers.py
A    exaile/xl/panels.py
A    exaile/xl/trackslist.py
A    exaile/xl/track.py
A    exaile/xl/config.py
A    exaile/xl/tracks.py
A    exaile/db.sql
A    exaile/mmkeys
A    exaile/mmkeys/mmkeys.override
A    exaile/mmkeys/mmkeys.defs
A    exaile/mmkeys/MANIFEST
A    exaile/mmkeys/mmkeys.c
A    exaile/mmkeys/setup.py
A    exaile/mmkeys/COPYING
A    exaile/mmkeys/mmkeys.h
A    exaile/mmkeys/mmkeysmodule.c
A    exaile/mmkeys/README
A    exaile/mmkeys/Makefile
A    exaile/mmkeys.so
A    exaile/images
A    exaile/images/remove.png
A    exaile/images/refresh.png
A    exaile/images/player-play.png
A    exaile/images/album.png
A    exaile/images/genre.png
A    exaile/images/player-volume.png
A    exaile/images/delete.png
A    exaile/images/track.png
A    exaile/images/artist.png
A    exaile/images/player-prev.png
A    exaile/images/player-pause.png
A    exaile/images/player-next.png
A    exaile/images/folder.png
A    exaile/images/nocover.png
A    exaile/images/playlist_ipod.png
A    exaile/images/media-audiofile.png
A    exaile/images/player-stop.png
A    exaile/images/exailelogo-sml.png
A    exaile/images/clear.png
A    exaile/images/add.png
A    exaile/images/lite/icon.png
A    exaile/images/ipod.png
A    exaile/exaile
A    exaile/debs
A    exaile/debs/python-gpod_0.3-1_i386.deb
A    exaile/exaile.py
Checked out revision 913.
pat@cube:~$ cd exaile && ./exaile
Traceback (most recent call last):
  File "exaile.py", line 28, in ?
    from xl import *
  File "/home/pat/exaile/xl/config.py", line 17, in ?
    import fileinput, traceback, xlmisc
  File "/home/pat/exaile/xl/xlmisc.py", line 18, in ?
    import trackslist, tracks, covers, md5, threading, re
  File "/home/pat/exaile/xl/trackslist.py", line 19, in ?
    from xl import xlmisc, common, track, tracks
ImportError: cannot import name xlmisc

```

Now what?

Cheers

-Pat[/QUOTE]


I apologize.. I'm getting ready for a release, so things are changing in the svn repository a bit.  If you svn update now, it should work.

---

### Post by patbuntu on 2006-05-19
Yep - works fine now.  Imported 4603 tracks (for the record, listen got 4668, amarok got 4695).

Seems to work fine, good stuff:-D 

Nice one

-Pat

---

### Post by GarethMB on 2006-05-20
Ack!
```
gareth@gareth-laptop:~/exaile$ ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1877, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1868, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 111, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'esdsink'))
  File "/home/gareth/exaile/xl/media.py", line 50, in set_audio_sink
    player.set_property("audio-sink", audio_sink)
AttributeError: 'NoneType' object has no attribute 'set_property'

```

---

### Post by croak77 on 2006-05-20
Thanks for your hard work. Cool player.

---

### Post by foxy123 on 2006-05-21
I've got the following error:
```
 ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1877, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1868, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 111, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'esdsink'))
  File "/home/alex/CVS/exaile/xl/media.py", line 50, in set_audio_sink
    player.set_property("audio-sink", audio_sink)
AttributeError: 'NoneType' object has no attribute 'set_property'

```

is svn version broken at the moment? I use Dapper by the way...

---

### Post by tenshi-no-shi on 2006-05-21
Sweetness. I have been away for a couple of days and looking through the postings I found the answer to my own problem, I just had to delete the music.db and it worked fine.

---

### Post by groggyboy on 2006-05-21
Downloaded it, it's populating my music library as we speak.

One annoyance so far: I try to keep my /Home directory nice 'n tidy.  Is there any way I can get exaile to install somewhere else?  Like wherever other programs get installed?

Otherwise its so far so good!

groggyboy

---

### Post by synic on 2006-05-21
[QUOTE=groggyboy]Downloaded it, it's populating my music library as we speak.

One annoyance so far: I try to keep my /Home directory nice 'n tidy.  Is there any way I can get exaile to install somewhere else?  Like wherever other programs get installed?

Otherwise its so far so good!

groggyboy[/QUOTE]

Yeah, hopefully soon I'll have a .deb ready that'll install it like you'd expect.

---

### Post by mmcmonster on 2006-05-23
Whenever I want to install from source something, I just put it in /usr/local/src/applicationname. I then create a symbolic link to the binary in /usr/local/bin (If the build doesn't create it already).

This way I can keep it out of /home while still keep track of what I installed manually.

Edit: I take that back.  When I created the sym-link in /usr/local/bin, I got the following error:

```
python: can't open file 'exaile.py': [Errno 2] No such file or directory
```

---

### Post by synic on 2006-05-23
```
python: can't open file 'exaile.py': [Errno 2] No such file or directory
```[/QUOTE]

If you chmod +x exaile.py and make the symlink to that instead, it should work.

---

### Post by Harold P on 2006-05-23
I would most definitely use this as a replacement for amaroK if I could hear something... I play and a song and nothing happens. 

Help, please?

---

### Post by mrgnash on 2006-05-24
[QUOTE=foxy123]I've got the following error:
```
 ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1877, in ?
    if __name__ == "__main__": main()
  File "exaile.py", line 1868, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 111, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'esdsink'))
  File "/home/alex/CVS/exaile/xl/media.py", line 50, in set_audio_sink
    player.set_property("audio-sink", audio_sink)
AttributeError: 'NoneType' object has no attribute 'set_property'

```

is svn version broken at the moment? I use Dapper by the way...[/QUOTE]

Same error here too.

---

### Post by zAo on 2006-05-24
And agian python... (like Listen)

To slow for me. Looks nice though!

---

### Post by synic on 2006-05-24
[QUOTE=Harold P]I would most definitely use this as a replacement for amaroK if I could hear something... I play and a song and nothing happens. 

Help, please?[/QUOTE]

Have you tried one of the different playback sinks in the preferences?

---

### Post by synic on 2006-05-24
[QUOTE=mrgnash]Same error here too.[/QUOTE]

For this error on Dapper, apt-get install gstreamer0.8-plugins

---

### Post by synic on 2006-05-24
[QUOTE=zAo]And agian python... (like Listen)

To slow for me. Looks nice though![/QUOTE]

Yeah, like Listen and Quod Libet (both great IMHO).

Curious, the Python apps are slower than Amarok?

---

### Post by mrgnash on 2006-05-24
Ah that did the trick :) Great player... only thing missing for me now is that it doesn't seem to have window borders under Compiz.

---

### Post by jasay on 2006-05-24
Wow synic, this is really shaping up.  I like it.  :D 

The only problem I have now is that it doesn't recognize the albums of my .ogg files.  Do you have a bugtracker somewhere?

mrgnash: It works fine for me under compiz.:-k

---

### Post by Harold P on 2006-05-24
[QUOTE=synic]Have you tried one of the different playback sinks in the preferences?[/QUOTE]
Hmm, yeah. I did it last night, and it didn't work. Weird. :-k 

But it works now. :D

Thanks for the help! 

P.S., two things:
[http://img326.imageshack.us/img326/7933/screenshotexaileplayingactappa.png](http://img326.imageshack.us/img326/7933/screenshotexaileplayingactappa.png)

How come all my album titles dissapeared? :( And, also, is there a way to remove certain details, like track # and rating?

---

### Post by synic on 2006-05-24
[QUOTE=Harold P]Hmm, yeah. I did it last night, and it didn't work. Weird. :-k 

But it works now. :D

Thanks for the help! 

P.S., two things:
[http://img326.imageshack.us/img326/7933/screenshotexaileplayingactappa.png](http://img326.imageshack.us/img326/7933/screenshotexaileplayingactappa.png)

How come all my album titles dissapeared? :( And, also, is there a way to remove certain details, like track # and rating?[/QUOTE]

Yeah, that was a bug I introduced last night.  rm ~/.exaile/music.db and refresh, and it'll fix it.

No, not yet there isn't a way to remove details (there will be).

---

### Post by foxy123 on 2006-05-25
[QUOTE=synic]For this error on Dapper, apt-get install gstreamer0.8-plugins[/QUOTE]
any plans to make it work with gstreamer 1.0? I do not mind to have both on my system as they live well togeher but still one wants to keep its system as tidy as possible...

---

### Post by synic on 2006-05-25
[QUOTE=foxy123]any plans to make it work with gstreamer 1.0? I do not mind to have both on my system as they live well togeher but still one wants to keep its system as tidy as possible...[/QUOTE]

Yup

---

### Post by Harold P on 2006-05-25
Okay, thanks. Deleting music database worked. The albums are all back. :)

Two things, could you perhaps make F2 a hotkey for editing track information and is it okay if I promote Exaile in my signature? ;)

---

### Post by synic on 2006-05-25
[QUOTE=Harold P]Okay, thanks. Deleting music database worked. The albums are all back. :)

Two things, could you perhaps make F2 a hotkey for editing track information and is it okay if I promote Exaile in my signature? ;)[/QUOTE]

Yup and yup :)

---

### Post by synic on 2006-05-25
[QUOTE=foxy123]any plans to make it work with gstreamer 1.0? I do not mind to have both on my system as they live well togeher but still one wants to keep its system as tidy as possible...[/QUOTE]

Ok, Exaile now /only/ works with Gstreamer 0.10.  I'm doing this because by the time I actually feel that all the bugs are ironed out for the first release, Dapper will probably be out.

You'll need python-gst0.10, gstreamer0.10, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, and optionally (for mp3 support), gstreamer0.10-plugins-ugly.

---

### Post by Harold P on 2006-05-25
[quote=synic]Yup and yup :)[/quote]

Can't wait! And... done! :p

---

### Post by foxy123 on 2006-05-25
Exaile! looks very sweet. It is quite obvious that it is in the beginning of its development, but I already like it.

---

### Post by hollywoodb on 2006-05-25
```

hollywoodb@hollywoodb ~ $ svn checkout svn://jbother.org/usr/local/svn/exaile
Checked out revision 961.
hollywoodb@hollywoodb ~ $ cd exaile/
hollywoodb@hollywoodb ~/exaile $ ./exaile
Traceback (most recent call last):
  File "exaile.py", line 36, in ?
    import gobject, gst, dbus
ImportError: No module named dbus
hollywoodb@hollywoodb ~/exaile $

```

(dbus is running)

also, after installing required packages as per 1st post, it turned out I also needed python-imaging package.

---

### Post by zenwhen on 2006-05-25
It is broken now:

```
zenwhen@sunball:~/exaile $ python exaile
  File "exaile", line 3
    python exaile.py $@
                ^
SyntaxError: invalid syntax
```

---

### Post by hollywoodb on 2006-05-25
[QUOTE=zenwhen]It is broken now:

```
zenwhen@sunball:~/exaile $ python exaile
  File "exaile", line 3
    python exaile.py $@
                ^
SyntaxError: invalid syntax
```[/QUOTE]

I'm getting that as well, when I run 'python exaile'

When I just run 'exaile' I get the dbus error two posts above

---

### Post by croak77 on 2006-05-25
You need python2.4-dbus.

---

### Post by nalmeth on 2006-05-25
@ Synic, 
Have you put any more thought into developing *guitar *tab fetching?
I have free time now-a-day's and will help you out anyway I can. Put me to work. Unfortunately you'd have to do the coding, I'm illiterate in this domain. I can help out in any other fashion.

Having this feature in a music player is my dream, I will throw out every other music player I have installed. Rather I will throw them in a pile, dump gas over them and... well you get the point.

What do you think about this?

---

### Post by eyesonly on 2006-05-26
I would love to try the player but something went funny on the install

jbs@eyesonly:~$ cd exaile && ./exaile
Traceback (most recent call last):
  File "exaile.py", line 28, in ?
    from xl import *
  File "/home/jbs/exaile/xl/tracks.py", line 18, in ?
    import common, media
  File "/home/jbs/exaile/xl/media.py", line 21, in ?
    import pygst
ImportError: No module named pygst
jbs@eyesonly:~/exaile$

---

### Post by Harold P on 2006-05-26
I think I'm having the same problem too as mentioned above. 

[B] harold@ubuntu:~$ sudo apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad gstreamer0.8-mad python-gst subversion
 Reading package lists... Done
 Building dependency tree... Done
 python-wxgtk2.6 is already the newest version.
 python-pysqlite2 is already the newest version.
 python-pymad is already the newest version.
 gstreamer0.8-mad is already the newest version.
 python-gst is already the newest version.
 subversion is already the newest version.
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 harold@ubuntu:~$ svn checkout svn://jbother.org/usr/local/svn/exaile
 Checked out revision 966.
 harold@ubuntu:~$ cd exaile && ./exaile
 Traceback (most recent call last):
   File "exaile.py", line 28, in ?
     from xl import *
   File "/home/harold/exaile/xl/tracks.py", line 18, in ?
     import common, media
   File "/home/harold/exaile/xl/media.py", line 21, in ?
     import pygst
 ImportError: No module named pygst
 harold@ubuntu:~/exaile$[/B]


Weird... worked fine on my other ubuntu box. pygst is python-gst, correct?

---

### Post by croak77 on 2006-05-26
That's weird. It seemes python-gst in Breezy doesn't have pygst.py but python-gst0.10 on Dapper does.

---

### Post by croak77 on 2006-05-26
I got a couple feature requests: translucent background for OSD, resizable OSD ( sometimes letters get cut off ) and some type of message that reports LastFM submit worked or failed ( maybe there is one and I missed it). Thanks again for your hard work!!!

---

### Post by ronlybonly on 2006-05-26
This app looks very promising! I'll have to check it out.

---

### Post by Starchild on 2006-05-26
Same pygst problem here....

---

### Post by johnnyc on 2006-05-26
VERY nice work synic!
The only issue I have with it is not being able to install python-gpod for ipod support.

---

### Post by Harold P on 2006-05-26
I use breezy on my other ubuntu box and it worked fine. I don't see why it would be conflicting breezy-dapper wise.

---

### Post by jasay on 2006-05-26
[QUOTE=jasay]
The only problem I have now is that it doesn't recognize the albums of my .ogg files.  [/QUOTE]
Fixed.  Thanks synic! 8)

---

### Post by hollywoodb on 2006-05-26
Awesome, I love this player ;)

couple things, I needed python-image and python2.4-dbus, might want to add those to dependencies... (I'm on dapper)


Feature requests:

pause/stop/player/next/previous hotkeys, so that I don't have to use the mouse to jump tracks

auto-sizing OSD (already mentioned I think)

adjustable columns in playlist, and addition of filename column (also already mentioned I believe)... I like to sort by filename, since tags are not always 100% correct, but my filenames are

Bugs:
I set alsasink as output, there were two alsasink options for some reason, whichever one I chose didn't work and exaile refused to start, perhaps on failed output cause it to default to gconf or oss and start with a message

Great work !

---

### Post by zenwhen on 2006-05-26
I wish I had stopped updating. I can't use this awesome music player now.

---

### Post by synic on 2006-05-26
[QUOTE=nalmeth]@ Synic, 
Have you put any more thought into developing *guitar *tab fetching?
I have free time now-a-day's and will help you out anyway I can. Put me to work. Unfortunately you'd have to do the coding, I'm illiterate in this domain. I can help out in any other fashion.

Having this feature in a music player is my dream, I will throw out every other music player I have installed. Rather I will throw them in a pile, dump gas over them and... well you get the point.

What do you think about this?[/QUOTE]

It actually fetches from fretplay.com right now.  It doesn't always guess where to fetch them from correctly... I'm not sure what to do about that.  It would be nice if there was a site that actually had an api for this.

---

### Post by synic on 2006-05-26
[QUOTE=johnnyc]VERY nice work synic!
The only issue I have with it is not being able to install python-gpod for ipod support.[/QUOTE]

I included the deb in the svn repository - it's debs/python-gpod-xxx.deb

---

### Post by synic on 2006-05-26
Regarding the pygst import problems:

Exaile now uses gstreamer0.10, so you'll need to install python-gst0.10.  This is available only in Dapper.  I decided to upgrade now because by the time I release, Dapper will surely be out.

---

### Post by Harold P on 2006-05-26
Oh, okay. :-D It's only a few days, I can wait--after all: I still have my breezy version on my other ubuntu box. :p

I guess I could provide a mirror to the breezy version when I get to my other house tomorrow night.

---

### Post by almahtar on 2006-05-27
I've read through the thread and it sounds like quite an app.  I'm working with a company that uses wxwidgets with their softare in C++, and I've been dying to learn python, so I think I'd like to join in on the dev.  My problem, though, is this....

```

jonathan@Dragonfly:~/exaile$ ./exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in ?
    xlmisc.log_exception()
  File "/home/jonathan/exaile/xl/xlmisc.py", line 306, in log_exception
    wx.CallAfter(__log_exception)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13257, in CallAfter
    assert app is not None, 'No wx.App created yet'
AssertionError: No wx.App created yet

```

I followed all your original instructions and any recommendations I found later on.  Up to this point nothing in this thread has worked.  Any idea what's up?  I'm awful at debugging python stuff as of yet.

---

### Post by Russty of Oz on 2006-05-27
Hi,

I have got Exaile! installed and it looks great but it will only play mp3's!  Can it play wma, wmv etc.?  If so, how.  I have the w32codecs installed.

Russty

---

### Post by Rikostan on 2006-05-27
I installed it last night.. no issues at all and I love the simple interface that still gives me decent control of my  rather large music collection.

---

### Post by synic on 2006-05-27
[QUOTE=Russty of Oz]Hi,

I have got Exaile! installed and it looks great but it will only play mp3's!  Can it play wma, wmv etc.?  If so, how.  I have the w32codecs installed.

Russty[/QUOTE]

I just put support in for .wma.  You'll need to install the gstreamer0.10-ffmpeg package for it to work.

---

### Post by Harold P on 2006-05-27
[QUOTE=synic]I just put support in for .wma.  You'll need to install the gstreamer0.10-ffmpeg package for it to work.[/QUOTE]
Are you going to add that to the first post as a dependancy, or leave it as an option?

---

### Post by synic on 2006-05-27
[QUOTE=Harold P]Are you going to add that to the first post as a dependancy, or leave it as an option?[/QUOTE]

Just an option.

---

### Post by Minyaliel on 2006-05-27
Nice work, being a former AmaroK addict, I love this :)

---

### Post by mynimal on 2006-05-27
Man, this thing is chalk-full of features. Great player, but I just wish you could tweak the layout a bit, and it used icons from your current theme. Also, the panel at the top with the track info is a bit empty for its size; maybe you could move the buttons and progressbar underneath the "from (albumname) by (artistname)", since that's an empty row? I love the blacklist feature though, if this had hotkey settings I'd be all over it like a fly on butter.

For example, ratings hotkeys/arguments (exile --rating=#), playback toggling (exile --toggle), etc, would be great. They'd be very usable with custom buttons added to the gnome panel - I did that with Banshee, but it doesn't support the --rating=# thing. Well, there're some suggestions for ya. :P

Is there an option anywhere to customize the colmn sorting?

---

### Post by almahtar on 2006-05-27
Hah... you're all killing me here.  Sounds like a great product, but I'm still getting that error :-(

---

### Post by Russty of Oz on 2006-05-27
[QUOTE=synic]I just put support in for .wma.  You'll need to install the gstreamer0.10-ffmpeg package for it to work.[/QUOTE]

I looked in Synaptic and I have the gstreamer0.10 but there is no -ffmpeg package there.  Where can I get it?

I am new to all this as you can no doubt tell.

---

### Post by Harold P on 2006-05-27
[QUOTE=Russty of Oz]I looked in Synaptic and I have the gstreamer0.10 but there is no -ffmpeg package there.  Where can I get it?

I am new to all this as you can no doubt tell.[/QUOTE]
Are you using Dapper? It's not available on Breezy.

---

### Post by Russty of Oz on 2006-05-27
[QUOTE=Harold P]Are you using Dapper? It's not available on Breezy.[/QUOTE]

Yes, I did the upgrade the other day.

---

### Post by Harold P on 2006-05-27
[http://packages.debian.org/unstable/libs/gstreamer0.10-ffmpeg](http://packages.debian.org/unstable/libs/gstreamer0.10-ffmpeg)

---

### Post by souled on 2006-05-28
When trying to run the program, I'm getting this error:

```
eric@motherland:~/exaile$ /home/eric/exaile/exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in ?
    xlmisc.log_exception()
  File "/home/eric/exaile/xl/xlmisc.py", line 306, in log_exception
    wx.CallAfter(__log_exception)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13257, in CallAfter
    assert app is not None, 'No wx.App created yet'
AssertionError: No wx.App created yet

```

I can't find libgstreamer0.10-plugins-good in the repositories either...

---

### Post by kpolice on 2006-05-28
[QUOTE=souled]When trying to run the program, I'm getting this error:

```
eric@motherland:~/exaile$ /home/eric/exaile/exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in ?
    xlmisc.log_exception()
  File "/home/eric/exaile/xl/xlmisc.py", line 306, in log_exception
    wx.CallAfter(__log_exception)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13257, in CallAfter
    assert app is not None, 'No wx.App created yet'
AssertionError: No wx.App created yet

```

I can't find libgstreamer0.10-plugins-good in the repositories either...[/QUOTE]

I get the same error message.

---

### Post by almahtar on 2006-05-28
Yep, it's the same one I'm getting.

---

### Post by Russty of Oz on 2006-05-28
[QUOTE=Harold P][http://packages.debian.org/unstable/libs/gstreamer0.10-ffmpeg](http://packages.debian.org/unstable/libs/gstreamer0.10-ffmpeg)[/QUOTE]

HOORAY!!  IT WORKS!!

Thanks Harold!  that did the trick.  I am so relieved that it all works so well.  Now at least Totem will play wma's.

Russty.

---

### Post by Russty of Oz on 2006-05-28
[QUOTE=synic]I just put support in for .wma.  You'll need to install the gstreamer0.10-ffmpeg package for it to work.[/QUOTE]

Well I now have the gstreamer0.10-ffmpeg package installed, but Exaile! still wont play .wma files.  Have I forgot to do something?  They now play in Totem player, but I really like the look and feel of Exaile!

Russty.

---

### Post by hollywoodb on 2006-05-28
I'm getting the wx.App error now as well after updating:

```

hollywoodb@hollywoodb ~/exaile $ ~/bin/exaile_svn_fetch
Checked out revision 974.

hollywoodb@hollywoodb ~/exaile $ ./exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in ?
    xlmisc.log_exception()
  File "/home/hollywoodb/exaile/xl/xlmisc.py", line 306, in log_exception
    wx.CallAfter(__log_exception)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13257, in CallAfter
    assert app is not None, 'No wx.App created yet'
AssertionError: No wx.App created yet

hollywoodb@hollywoodb ~/exaile $

```

---

### Post by Harold P on 2006-05-28
Here's the breezy version from like 4 days ago:

[http://www.harold.liberty-host.com/exaile.tar.gz]("http://www.harold.liberty-host.com/exaile.tar.gz")

Download it to your home directory, then extract it. then run this in terminal:

```
cd ~/exaile && ./exaile
``` 
Or, if you're too lazy to use command line then go into your home directory, open the exaile folder, and double click on exaile. You'll be prompted with this notice:

[IMG]http://img100.imageshack.us/img100/4839/screenshotrunordisplay7xg.png[/IMG]

Click "Run". 

Have fun... ;)

Edit: Umm, is it a bug that if you press X to close the window, it doesn't minimize to the tray? (It just closes the whole thing.) If it isn't, that'd be a nice feature. :)

Edit (2): In order for this to work, you have to have the correct dependencies installed:

```
apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad gstreamer0.8-mad python-gst
```

---

### Post by Harold P on 2006-05-28
[quote=souled]When trying to run the program, I'm getting this error:

```
eric@motherland:~/exaile$ /home/eric/exaile/exaile
Traceback (most recent call last):
  File "exaile.py", line 44, in ?
    xlmisc.log_exception()
  File "/home/eric/exaile/xl/xlmisc.py", line 306, in log_exception
    wx.CallAfter(__log_exception)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13257, in CallAfter
    assert app is not None, 'No wx.App created yet'
AssertionError: No wx.App created yet

``` 
** I can't find libgstreamer0.10-plugins-good in the repositories either**...[/quote]
[http://packages.debian.org/unstable/libs/gstreamer0.10-plugins-good](http://packages.debian.org/unstable/libs/gstreamer0.10-plugins-good)

Does that help?

---

### Post by maxol on 2006-05-28
[QUOTE=Harold P]Here's the breezy version from like 4 days ago:

[http://www.harold.liberty-host.com/exaile.tar.gz]("http://www.harold.liberty-host.com/exaile.tar.gz")

Download it to your home directory, then extract it. then run this in terminal:

```
cd ~/exaile && ./exaile
``` 


max@shiny:~$ cd ~/exaile && ./exaile
Traceback (most recent call last):
  File "exaile.py", line 19, in ?
    import wx, wx.grid, sys, os, re, random, fileinput, gc, urllib, md5
ImportError: No module named wx

Dependency problem?

---

### Post by Harold P on 2006-05-28
[quote=maxol][quote=Harold P]Here's the breezy version from like 4 days ago:

[http://www.harold.liberty-host.com/exaile.tar.gz]("http://www.harold.liberty-host.com/exaile.tar.gz")

Download it to your home directory, then extract it. then run this in terminal:

```
cd ~/exaile && ./exaile
``` 


max@shiny:~$ cd ~/exaile && ./exaile
Traceback (most recent call last):
  File "exaile.py", line 19, in ?
    import wx, wx.grid, sys, os, re, random, fileinput, gc, urllib, md5
ImportError: No module named wx

Dependency problem?[/quote] Only use that one if you have breezy. Make sure you ran this:

```
sudo apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad gstreamer0.8-mad python-gst

``` 
before you try to run it.

---

### Post by maxol on 2006-05-29
OK I'm using Dapper so I'll wait for the next release, looks good though.

---

### Post by Terracotta on 2006-05-29
Looks nice, is it gnome specific, or is it just gtk+? I'm interested in using it in xfce,since Xmedia is horrible, and well amarok rocks so well kinda like this project.

Do you work together with amarok? Both projects could benefit from it I think.

---

### Post by Harold P on 2006-05-31
[quote=Terracotta]Looks nice, is it gnome specific, or is it just gtk+? I'm interested in using it in xfce,since Xmedia is horrible, and well amarok rocks so well kinda like this project.

Do you work together with amarok? Both projects could benefit from it I think.[/quote]
Works fine in XFCE. When's the next release?

---

### Post by madjo on 2006-05-31
will there also be support for the media keys on logitech keyboards, or is there some trick that I can use to enable those keys?

---

### Post by synic on 2006-05-31
[QUOTE=madjo]will there also be support for the media keys on logitech keyboards, or is there some trick that I can use to enable those keys?[/QUOTE]

If you type make, make install, and then type exaile from the CLI, do you see the message "mmkeys are available"?

---

### Post by madjo on 2006-05-31
Yes, it does, and apparently it accepts the "stop" key... but that is the only key it accepts. next, previous and play/pause do nothing for me.

I use a Logitech wireless itouch keyboard. If that makes any difference. :)

oh and another thing, when I press 'stop'. the Titlebar still shows "Exaile playing [song name]" :)

---

### Post by henriquemaia on 2006-06-01
Hi,

The program looks awesome. Great work. It's a pleasure to have an good Amarok alternative.

One thing: can the close button behaviour be changed to work as Amarok's? (not closing the app, but hidding it into the notification area)

---

### Post by nalmeth on 2006-06-01
> It actually fetches from fretplay.com right now. It doesn't always guess where to fetch them from correctly... I'm not sure what to do about that. It would be nice if there was a site that actually had an api for this.
Hey, thanks for implementing this synic, I figured you were busy with other feature request's and bug squashing so I didn't want to press you with it.

I tried exaile out the other day, but happened to get AIGLX going the same day, so I didn't use exaile very much. I will do some testing tomorrow night (during work :) ) and let you know how it's working for me + my songs.

I'll look around for a better site too.

Cheers

:cool:

---

### Post by Harold P on 2006-06-01
Now that I have Dapper working, I'm definitely giving this thing a try... AGAIN! :)

---

### Post by xmastree on 2006-06-01
[QUOTE=synic]
It's still pretty beta, but if you're bored, check it out.  Here's what you'll need to do:

```

# apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 subversion python-pyogg
[COLOR="Red"]# svn checkout svn://jbother.org/usr/local/svn/exaile[/COLOR]
# cd exaile && ./exaile

```[/QUOTE]
Erm... 
```
Couldn't find package libgstreamer0.10
```
I pressed on regardless, but:
```
bash: svn: command not found
``` :confused:

---

### Post by Harold P on 2006-06-01
[quote=xmastree]Erm... 
```
Couldn't find package libgstreamer0.10
``` I pressed on regardless, but:
```
bash: svn: command not found
``` :confused:[/quote]
svn = subversion

apt-get subversion

---

### Post by xmastree on 2006-06-01
[QUOTE=Harold P]svn = subversion

apt-get subversion[/QUOTE]

Thanks.

```
chris@xmastree:~$ cd exaile && ./exaile
Traceback (most recent call last):
  File "exaile.py", line 28, in ?
    from xl import *
  File "/home/chris/exaile/xl/tracks.py", line 18, in ?
    import common, media, db
  File "/home/chris/exaile/xl/media.py", line 22, in ?
    import pygst
ImportError: No module named pygst
chris@xmastree:~/exaile$

```

---

### Post by vrih on 2006-06-01
apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad python-gst0.10 subversion python-pyogg

---

### Post by xmastree on 2006-06-01
> python-wxgtk2.6 is already the newest version.
python-pysqlite2 is already the newest version.
E: Couldn't find package python-gst0.10Not looking good so far, think I'll stick with what works.

---

### Post by xeta on 2006-06-01
BRILLIANT PLAYER! I love it!


1 item I think it needs....pandora support.

Ability to play pandora feeds without having to use their crappy interface. Keep up the good work.

---

### Post by blue_thunder on 2006-06-01
Beautiful player! Great set-up! My one issue: no support for .m4a like Rhythmbox.

---

### Post by synic on 2006-06-02
[QUOTE=xmastree]Not looking good so far, think I'll stick with what works.[/QUOTE]

Only works on Dapper.

---

### Post by xeta on 2006-06-02
Has anyone figured out how to link it from the task bar?

---

### Post by xmastree on 2006-06-03
[QUOTE=synic]Only works on Dapper.[/QUOTE]
Ah, Ok... I'll try it again when I upgrade.

---

### Post by Harold P on 2006-06-03
[quote=xeta]Has anyone figured out how to link it from the task bar?[/quote]
It's under some of the preference options. :P It says something like "Show icon in taskbar" something like that...

---

### Post by croak77 on 2006-06-03
[QUOTE=xeta]Has anyone figured out how to link it from the task bar?[/QUOTE]

Do you want a notification area icon or an application launcher? Like Harold P said there is an option in Preferences -> General -> Apperance -> Show Tray Icon. If you want an application launcher on the panel, Right Click on panel select Add To Panel, select Custum Application Launcher, fill in the name etc.,  under command use 'python /path/to/exaile.py' For a menu item Right Click on Applications menu and select edit menu, highlight Sound & Video, select File -> New Entry from the top menu and it's the same command 'python /path/to/exaile.py'.

---

### Post by synic on 2006-06-03
[QUOTE=xeta]Has anyone figured out how to link it from the task bar?[/QUOTE]

Also, if you type 'make && make install' in the exaile source directory, it will show up in your Applications->Sound and Video menu.

Adam

---

### Post by topyli on 2006-06-05
I love this player. What I'd like to see is command line control a la Rhythmbox and friends (exaile --next, exaile --previous...) I'm using keytouch to configure my multimedia keyboard and the default GNOME keyboard shortcut bindings don't work well together with it. I'm sure people who use a simple window managers like fluxbox would appreciate this too.

Alternatively, if someone knows how to send mm_key signals to exaile via the command line, that would solve this problem as well.

---

### Post by eKoeS on 2006-06-05
[QUOTE=synic]Only works on Dapper.[/QUOTE]
I've Ubuntu Dapper, but exaile does not work for me (svn sources) . :???: 
```
ekoes@ubuntu:~/Dati/exaile$ ./exaile
Traceback (most recent call last):
  File "exaile.py", line 19, in ?
    import wx, wx.grid, sys, os, re, random, fileinput, gc, urllib, md5
ImportError: No module named wx
```
I've read something about python-wxgtk2.6, but I have already installed this package.

---

### Post by synic on 2006-06-05
[QUOTE=topyli]I love this player. What I'd like to see is command line control a la Rhythmbox and friends (exaile --next, exaile --previous...) I'm using keytouch to configure my multimedia keyboard and the default GNOME keyboard shortcut bindings don't work well together with it. I'm sure people who use a simple window managers like fluxbox would appreciate this too.

Alternatively, if someone knows how to send mm_key signals to exaile via the command line, that would solve this problem as well.[/QUOTE]

--next
--prev
--stop
--play (also pauses)

---

### Post by evand on 2006-06-05
is there a way to transfer files to/from the ipod, or just view/play?

---

### Post by topyli on 2006-06-06
[QUOTE=synic]--next
--prev
--stop
--play (also pauses)[/QUOTE]
I've built packages from the current svn. running "exaile --next" or "exaile --play" starts a new exaile instance for me...

---

### Post by synic on 2006-06-06
[QUOTE=topyli]I've built packages from the current svn. running "exaile --next" or "exaile --play" starts a new exaile instance for me...[/QUOTE]

Hrmm, give it an svn update and it should work.

---

### Post by synic on 2006-06-06
[QUOTE=evand]is there a way to transfer files to/from the ipod, or just view/play?[/QUOTE]

Not yet, but eventually.

---

### Post by topyli on 2006-06-06
(Re: Command line control)
[QUOTE=synic]Hrmm, give it an svn update and it should work.[/QUOTE]
Yes it works now! Thanks.

---

### Post by synic on 2006-06-07
Exaile 0.2b released!  See the first post or the freshmeat project page ([http://freshmeat.net/projects/exaile/?branch_id=64911&release_id=229075](http://freshmeat.net/projects/exaile/?branch_id=64911&release_id=229075)) for details.

--synic

---

### Post by mrvw0169 on 2006-06-07
Wow, it looks amazing... can't wait to try this out as soon as Dell sends me back my laptop... No, even better, I'll just boot up a live CD to give Exaile a go once I get home since it looks so good.

Keep up the good work!

---

### Post by croak77 on 2006-06-07
Just tried out the deb file. Everything worked well. One question, do you plan to add any optins to deal with compilations? Amarok puts them in Various Artists by default and was wondering if it is possible to do the same or maybe a way to select an album and mark it as a compilation.

---

### Post by synic on 2006-06-07
[QUOTE=croak77]Just tried out the deb file. Everything worked well. One question, do you plan to add any optins to deal with compilations? Amarok puts them in Various Artists by default and was wondering if it is possible to do the same or maybe a way to select an album and mark it as a compilation.[/QUOTE]

Yes, that will probably be in 0.3.

---

### Post by xplode_me on 2006-06-07
Just to say that exaile is my player since i knew it existed (SVN version 0.1(?))...

IT rocks synic! :D

---

### Post by Dylan103 on 2006-06-07
Any idea?

```
oem@ubuntu:~$ cd exaile && ./exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .ser vice files
Traceback (most recent call last):
  File "exaile.py", line 41, in ?
    import gtk, mmkeys
ImportError: No module named mmkeys

***** You can safely ignore the above error.
Error reading settings file, using defaults.
Traceback (most recent call last):
  File "exaile.py", line 1899, in ?
    main()
  File "exaile.py", line 1888, in main
    exaile = ExaileWindow(fr)
  File "exaile.py", line 110, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'esdsink'))
  File "/home/harold/exaile/xl/media.py", line 49, in set_audio_sink
AttributeError: 'NoneType' object has no attribute 'set_property'


```

Thanks in advance,
Dylan

---

### Post by amunimanghi on 2006-06-07
when i installed it i went to sound and video=>exaile nothing happend. i typed exaile in the terminal and this is what i got ```
manghi@ubuntu:~$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 28, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db
  File "/usr/share/exaile/xl/common.py", line 19, in ?
    from pysqlite2.dbapi2 import OperationalError
ImportError: No module named pysqlite2.dbapi2
manghi@ubuntu:~$ 
```

---

### Post by croak77 on 2006-06-08
[QUOTE=amunimanghi]when i installed it i went to sound and video=>exaile nothing happend. i typed exaile in the terminal and this is what i got ```
manghi@ubuntu:~$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 28, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db
  File "/usr/share/exaile/xl/common.py", line 19, in ?
    from pysqlite2.dbapi2 import OperationalError
ImportError: No module named pysqlite2.dbapi2
manghi@ubuntu:~$ 
```[/QUOTE]


Is python-pysqlite2 installed?

---

### Post by thomashauk on 2006-06-08
A few bug reports.
First the box to choose where the OSD is positioned does not disapper if you close the preferences while on OSD.
Second the artists list should update after adding music to the libary or refressing the libary because it currently lokks as if it has failed.
Also, alhough this may be more of a feture request, there need to be a way of rejecting album artwork if it is wrong and there is no other available.

---

### Post by synic on 2006-06-08
[QUOTE=thomashauk]A few bug reports.
First the box to choose where the OSD is positioned does not disapper if you close the preferences while on OSD.
Second the artists list should update after adding music to the libary or refressing the libary because it currently lokks as if it has failed.
Also, alhough this may be more of a feture request, there need to be a way of rejecting album artwork if it is wrong and there is no other available.[/QUOTE]

1) Ah, good catch, I'll get it fixed.
2) Ok, this has been put in
3) You can change the cover manually by right clicking on it

---

### Post by thomashauk on 2006-06-08
The gstreemer-good package installed but now winges that it is broken.

```
 
gstreamer0.10-plugins-good: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
                              Depends: libdbus-1-2 (>= 0.61) but 0.60-6ubuntu8 is to be installed
                              Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
                              Depends: liboil0.3 (>= 0.3.8) but 0.3.7-0ubuntu5 is to be installed
                              Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be installed

```
](*,)

---

### Post by maxol on 2006-06-08
Great player, using it now.

One slight problem, the tray icon is appearing on the desktop instead of in the tray.

(screenshot attached)

---

### Post by synic on 2006-06-08
[QUOTE=thomashauk]The gstreemer-good package installed but now winges that it is broken.

```
 
gstreamer0.10-plugins-good: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
                              Depends: libdbus-1-2 (>= 0.61) but 0.60-6ubuntu8 is to be installed
                              Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
                              Depends: liboil0.3 (>= 0.3.8) but 0.3.7-0ubuntu5 is to be installed
                              Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be installed

```
](*,)[/QUOTE]

Sounds like you have non-ubuntu repos in your sources.list

---

### Post by synic on 2006-06-08
[QUOTE=maxol]Great player, using it now.

One slight problem, the tray icon is appearing on the desktop instead of in the tray.

(screenshot attached)[/QUOTE]

You have to have the notification area applet added to your panel.

---

### Post by maxol on 2006-06-08
Thanks synic, fixed.

Exaile is just what I wanted. I've tried Listen etc but found them too busy and always ended going back to Rhythmbox but I think I will be sticking with Exaile.

---

### Post by mpmc on 2006-06-08
Installed exaile, tried to run it & got:

> Traceback (most recent call last):
  File "/usr/bin/exaile", line 28, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db
  File "/usr/share/exaile/xl/media.py", line 20, in ?
    import urllib, xlmisc
  File "/usr/share/exaile/xl/xlmisc.py", line 18, in ?
    import trackslist, tracks, covers, md5, threading, re
  File "/usr/share/exaile/xl/covers.py", line 21, in ?
    import Image
ImportError: No module named Image


I'm running xfce

---

### Post by amunimanghi on 2006-06-08
[QUOTE=croak77]Is python-pysqlite2 installed?[/QUOTE]

i did sudo apt-get install python-pysqlite2, but it has A LOT of dependencies. I dont get it.


```
manghi@ubuntu:~$ sudo apt-get install python-pysqlite2
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  exaile: Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1.1 is to be installed
          Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is to be installed
          Depends: libpango1.0-0 (>= 1.12.2) but 1.10.1-0ubuntu1 is to be installed
          Depends: python-pymad
          Depends: libgstreamer0.10-0 but it is not installable
          Depends: gstreamer0.10-plugins-base but it is not installable
          Depends: gstreamer0.10-plugins-good but it is not installable
          Depends: python-gst0.10 but it is not installable
          Depends: gstreamer0.10-esd but it is not installable
          Depends: gstreamer0.10-alsa but it is not installable
  python-pysqlite2: Depends: python2.4-pysqlite2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
manghi@ubuntu:~$

```

---

### Post by synic on 2006-06-08
[QUOTE=mpmc]Installed exaile, tried to run it & got:



I'm running xfce[/QUOTE]

Sorry, you need python2.4-imaging.  This dep will be removed in the next release.

---

### Post by synic on 2006-06-08
[QUOTE=amunimanghi]i did sudo apt-get install python-pysqlite2, but it has A LOT of dependencies. I dont get it.


```
manghi@ubuntu:~$ sudo apt-get install python-pysqlite2
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  exaile: Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1.1 is to be installed
          Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is to be installed
          Depends: libpango1.0-0 (>= 1.12.2) but 1.10.1-0ubuntu1 is to be installed
          Depends: python-pymad
          Depends: libgstreamer0.10-0 but it is not installable
          Depends: gstreamer0.10-plugins-base but it is not installable
          Depends: gstreamer0.10-plugins-good but it is not installable
          Depends: python-gst0.10 but it is not installable
          Depends: gstreamer0.10-esd but it is not installable
          Depends: gstreamer0.10-alsa but it is not installable
  python-pysqlite2: Depends: python2.4-pysqlite2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
manghi@ubuntu:~$

```[/QUOTE]

Sounds like there's something wrong with your package db or sources... are you mixing repos?

---

### Post by amunimanghi on 2006-06-08
[QUOTE=synic]Sounds like there's something wrong with your package db or sources... are you mixing repos?[/QUOTE]


i checked and im not mixing any repos.

---

### Post by croak77 on 2006-06-08
[QUOTE=amunimanghi]i checked and im not mixing any repos.[/QUOTE]
 
Are you on Breezy or Dapper? Looks like you're on Breezy and you used the Exaile .deb which requires Dapper packages.

---

### Post by nalmeth on 2006-06-08
Synic, I've been more busy than usual lately, so I've only now got the time to test exaile out with tab fetching, but I can't find the option? How do you do it? Did you remove the feature? I installed on my PC with the deb.

I have a whole day off tomorrow, I can test her out a lot tomorrow.

If the feature's been removed, can you send me a .deb with it included or something?

I have a whole range of music that I think will be good to test its usability. 

OLGA might be more comprehensive than fretplay, but there are so many other sites too. What is the criteria for a good tab site for this function?

---

### Post by amunimanghi on 2006-06-08
[QUOTE=croak77]Are you on Breezy or Dapper? Looks like you're on Breezy and you used the Exaile .deb which requires Dapper packages.[/QUOTE]

I'm on Breezy. Does this mean it only works on Dapper. I'm going to upgrade really soon. I can wait. :D

---

### Post by xmastree on 2006-06-09
I tried it on Breezy, reported my problems here and was told it only works on Dapper. It's somewhere back in the thread, I don't blame you for not spotting it though...

---

### Post by thomashauk on 2006-06-09
[QUOTE=synic]Sounds like you have non-ubuntu repos in your sources.list[/QUOTE]

But I haven't although the .deb of gstreamer plugins was the one you pointed to earlier which was from the debian repos.


**EDIT Scrach that I've found a repo with a Ubuntu compatable one**

---

### Post by synic on 2006-06-09
[QUOTE=nalmeth]Synic, I've been more busy than usual lately, so I've only now got the time to test exaile out with tab fetching, but I can't find the option? How do you do it? Did you remove the feature? I installed on my PC with the deb.

I have a whole day off tomorrow, I can test her out a lot tomorrow.

If the feature's been removed, can you send me a .deb with it included or something?

I have a whole range of music that I think will be good to test its usability. 

OLGA might be more comprehensive than fretplay, but there are so many other sites too. What is the criteria for a good tab site for this function?[/QUOTE]

Right click on the track, and go to "Track Information"

---

### Post by MeneK on 2006-06-09
Exaile is simple and nice. Great work.

But, could you have a look at this screenshot?

[ATTACH]10949[/ATTACH]

Some files seem to have their ID3 tags corrupted when I'm using Exaile. They looked right in Rhythmbox, but after modifying some of the tags with Exaile, then the opposite happened: the modified files looked right in Exaile and wrong in Rhythmbox, and also in FooBar2000, when I boot with winXP.

I'm using Ubuntu 6.06, and my music library is on a FAT32 partition.

Thanks!

---

### Post by kblake007 on 2006-06-10
This media player is so cool I can hardly stand it. !!! Nice worK

---

### Post by mpmc on 2006-06-10
There a few dependencies missing if your using Xubuntu

Python2.4-dbus
Python2.4-imaging
Python2.4-libxml2
Python-pyogg

Are missing on the default install..
-----------------------------------------------------------------------
Also there is a bug, when changing tracks, It doesn't attempt to fetch the lyrics.... you have to reload the playlist

---

### Post by darehanl on 2006-06-10
Looks good. I'm seriously considering switching:-)

Just a few bug reports/requests:
[LIST=1]
[*]Dependency ***python-pyvorbis*** seems to be missing. But that's all I needed to add, the rest was taken care of by apt.
[*]Whenever I click "Set custom Image," the file browser opens in /usr/share/exaile. It would be nice if the file browser open from **where it was last opened**, or **the directory the music file is in**.
[*]Eventual support for internationalization (gettext). I'd love to translate Exaile.
[/LIST]

---

### Post by synic on 2006-06-10
[QUOTE=mpmc]There a few dependencies missing if your using Xubuntu

Python2.4-dbus
Python2.4-imaging
Python2.4-libxml2
Python-pyogg

Are missing on the default install..
-----------------------------------------------------------------------
Also there is a bug, when changing tracks, It doesn't attempt to fetch the lyrics.... you have to reload the playlist[/QUOTE]

Ah, I'll add these deps.

I'm not sure what you mean about fetching lyrics?

---

### Post by synic on 2006-06-10
[LIST=1]
[*]Dependency ***python-pyvorbis*** seems to be missing. But that's all I needed to add, the rest was taken care of by apt.
Ok, this is now in the control file

[*]Whenever I click "Set custom Image," the file browser opens in /usr/share/exaile. It would be nice if the file browser open from **where it was last opened**, or **the directory the music file is in**.
Done

[*]Eventual support for internationalization (gettext). I'd love to translate Exaile.
I've actually been programming with gettext, so I'll get back to you when I have everything ready for that :)

[/LIST]

Your changes are in SVN and will be in the next release.

--synic

---

### Post by synic on 2006-06-10
Ok.  I think I've got pyggettext2.4 sorta figured out, so I'm guessing this is what translators will need:

[http://synic.ath.cx/messages.pot]("http://synic.ath.cx/messages.pot")

Thanks,

--synic

---

### Post by rshd301 on 2006-06-10
First off, superb player.....however, one small issue I have concerning tags. I have spent a lot of time ensuring that my MP3 tags are correct using Easy Tag and in Amarok all appear as they should. Trouble is, in Exaile, none of my album names have come across. The artist, track number, genre etc all are there but no album name. Any ideas ???

---

### Post by MeneK on 2006-06-10
[QUOTE=MeneK]Exaile is simple and nice. Great work.

But, could you have a look at this screenshot?

[ATTACH]10949[/ATTACH]

Some files seem to have their ID3 tags corrupted when I'm using Exaile. They looked right in Rhythmbox, but after modifying some of the tags with Exaile, then the opposite happened: the modified files looked right in Exaile and wrong in Rhythmbox, and also in FooBar2000, when I boot with winXP.

I'm using Ubuntu 6.06, and my music library is on a FAT32 partition.

Thanks![/QUOTE]

I've just discovered that Windows Media Player 10 doesn't reconigse the same tags than Exaile, while they seem perfect with Rhythmbox or FooBar2000.

---

### Post by T313C0mun1s7 on 2006-06-10
I have not sat and read all 10 (22 in linear display mode) pages, so I am sorry if I repeat anything that was already mentioned.

I am thinking of figguring out if I can get Nero to work under WINE, but until I am able to do that I really liked that I could just drag a Winamp type (as in m3u or pls) playlist into Listen and then hit the button to Burn a CD.

I have not been able to drag and drop files or playlists into Exaile. I don't know if this is a function of Exaile or something else, but it would be a nice feature. Also, it would be nice when I am in a playlist to  be able to rightclick in the playlist and get an option to browse my filesystem for media files or playlist files to add to the current playlist. Finally, a feature to burn CDs such as Listen has would be a nice addition.

Thank you for such a great app. It really was so much more than I expected when I decided to give it a try. It is much more like a Ver 2.x app than a 0.02b app. Great work.

---

### Post by arnieboy on 2006-06-10
First of all:
I am on Dapper and I tried version 0.2b
This player is very impressive and is the best of the lot currently in my opinion.
A few bugs which need to be addressed in the radio section:
1) Exaile is unable to retrieve radio stations in some shoutcast genres like "80's" (not the only one).
2) Everytime, I double click on a radio genre, it opens a new tab. A check should be added to make sure that if a tab is already open for one genre, it should not get re-opened in a new tab if clicked again and preferably, the tab in which it was already open should gain focus.

I am sure the author has already planned to add buttons for "shuffle", "loop" etc in future releases.

This player should become the defacto Gnome media manager in the near future.

Good luck :)

---

### Post by T313C0mun1s7 on 2006-06-10
[quote=arnieboy]
This player should become the defacto Gnome media manager in the near future.
[/quote]

Yes, I agree. I Strongly Agree.

---

### Post by JMO707 on 2006-06-11
Damn. Its so amuzingly functional.

Not an only "just-fancy" thing. Its cuasi-perfect.

Keep on it (seriously)

---

### Post by darehanl on 2006-06-11
A few notes while translating (I'll finish by tommorrow, I think).

[LIST]
[*]Around line 475, there's an empty string.
```
#: xl/trackslist.py:75 xl/trackslist.py:602
msgid ""
msgstr ""
```
**msginit** gives an error because of this.

[*]At exaile.py:255, **Last** means **playlist that was last played**, right?

[*]At exaile.py:336, does "prevent from being added to the library on rescan" mean **the tracks will be removed from the library on rescan**? I'm not too sure what this sentence means.

[*]Is there any difference between a **library** and a **collection**?

[*]When asking the user "Blacklisting the selected tracks..." I *personally* think the choices should be 
**Cancel** **Blacklist**


[/LIST]
----
Also, when I "View Full Image" of a very large (> 800x600) image, the image covers the whole screen and won't go away. I had to **alt+drag** the image to find the **X** button.

---

### Post by synic on 2006-06-11
[QUOTE=darehanl]A few notes while translating (I'll finish by tommorrow, I think).

[LIST]
[*]Around line 475, there's an empty string.
-- this should be fixed if you refresh the messages.pot

[*]At exaile.py:255, **Last** means **playlist that was last played**, right?
-- Yes

[*]At exaile.py:336, does "prevent from being added to the library on rescan" mean **the tracks will be removed from the library on rescan**? I'm not too sure what this sentence means.
-- It means that the track will never be in the library, even if you rescan your collection

[*]Is there any difference between a **library** and a **collection**?
-- No

[/LIST]

---

### Post by shrimphead on 2006-06-11
awesome player I love it, I used to use KDE purely for amarok (I hate running qt apps in a gtk environemt too) and this is exactly what I was looking for.

I haven't used it extensively yet, I only installed it a half hour ago, but the first thing that jumps out at me is that it doesn't remember it's position between instances. It would be awesome if there was an option to start in full screen or something.

---

### Post by synic on 2006-06-11
[QUOTE=shrimphead]awesome player I love it, I used to use KDE purely for amarok (I hate running qt apps in a gtk environemt too) and this is exactly what I was looking for.

I haven't used it extensively yet, I only installed it a half hour ago, but the first thing that jumps out at me is that it doesn't remember it's position between instances. It would be awesome if there was an option to start in full screen or something.[/QUOTE]

Ah, it actually does remember the position and size... problem is that it only remembers when you resize or move the window (these events are not triggered when you maxmize).  I'll add a listener to the maximize event, and it will be available in the next release.

---

### Post by Bogart on 2006-06-11
I'm using it in Arch Linux and it works fine except I can't listen to shoutcast feeds. I don't get any error, just nothing happens, no sound. The feeds work fine in xmms, but not in exaile. I installed all dependencies suggested, but could I miss some gstreamer plugin or something? Does it require gstreamer-ffmpeg to stream these radio feeds? However, opening exaile in a terminal and opening a shoutcast playlist previously downloaded doesn't give any error message.

Apart from that, great player ! Really good. I love it. Great work, thanks !

---

### Post by synic on 2006-06-11
[QUOTE=Bogart]I'm using it in Arch Linux and it works fine except I can't listen to shoutcast feeds. I don't get any error, just nothing happens, no sound. The feeds work fine in xmms, but not in exaile. I installed all dependencies suggested, but could I miss some gstreamer plugin or something? Does it require gstreamer-ffmpeg to stream these radio feeds? However, opening exaile in a terminal and opening a shoutcast playlist previously downloaded doesn't give any error message.

Apart from that, great player ! Really good. I love it. Great work, thanks ![/QUOTE]

Do you see any messages in the terminal when you run it?

---

### Post by Bogart on 2006-06-11
Nothing special apart from the dbus error that tell me I can ignore it. Here is the output when opening exaile and then trying to open a shoutcast playlist:

[alberto@localhost ~]$ exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
[audioscrobbler] logging in
[audioscrobbler] Sleeping for 1 secs
loading songs
Importing /home/alberto/shoutcast-playlist.pls

And there it stops and does nothing else... It's strange 'cause i can listen to my local files without a problem.

---

### Post by Sheinar on 2006-06-11
[QUOTE=Bogart]I'm using it in Arch Linux and it works fine except I can't listen to shoutcast feeds.[/QUOTE]
Same problem here.

---

### Post by synic on 2006-06-11
[QUOTE=Bogart]Nothing special apart from the dbus error that tell me I can ignore it. Here is the output when opening exaile and then trying to open a shoutcast playlist:

[alberto@localhost ~]$ exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
[audioscrobbler] logging in
[audioscrobbler] Sleeping for 1 secs
loading songs
Importing /home/alberto/shoutcast-playlist.pls

And there it stops and does nothing else... It's strange 'cause i can listen to my local files without a problem.[/QUOTE]

Can you paste the contents of that file?

---

### Post by synic on 2006-06-11
[QUOTE=arnieboy]First of all:
I am on Dapper and I tried version 0.2b
This player is very impressive and is the best of the lot currently in my opinion.
A few bugs which need to be addressed in the radio section:
1) Exaile is unable to retrieve radio stations in some shoutcast genres like "80's" (not the only one).
2) Everytime, I double click on a radio genre, it opens a new tab. A check should be added to make sure that if a tab is already open for one genre, it should not get re-opened in a new tab if clicked again and preferably, the tab in which it was already open should gain focus.
[/QUOTE]

1) For some reason there are no stations under "80's" on shoutcast, even if you browse shoutcast.com in firefox.  I'm not sure why this is.

2) I will add this in.

Adam

---

### Post by Bogart on 2006-06-12
The file is just a playlist downloaded from shoutcast to test opening it locally. Here are the contents:

[playlist]
numberofentries=5
File1=http://207.200.96.227:80/stream/1028
Title1=(#1 - 315/3155) S K Y . F M - Classical & Flamenco Guitar - a mix of classical, spanish, and flamenco guitar
Length1=-1
File2=http://207.200.96.227:8000
Title2=(#2 - 105/1000) S K Y . F M - Classical & Flamenco Guitar - a mix of classical, spanish, and flamenco guitar
Length2=-1
File3=http://207.200.96.229:8016
Title3=(#3 - 110/1000) S K Y . F M - Classical & Flamenco Guitar - a mix of classical, spanish, and flamenco guitar
Length3=-1
File4=http://207.200.96.228:80/stream/1028
Title4=(#4 - 760/2207) S K Y . F M - Classical & Flamenco Guitar - a mix of classical, spanish, and flamenco guitar
Length4=-1
File5=http://205.188.215.226:8020
Title5=(#5 - 81/100) S K Y . F M - Classical & Flamenco Guitar - a mix of classical, spanish, and flamenco guitar
Length5=-1
Version=2

It's strange. Exaile's radio works fine in Ubuntu live-CD... In Arch I'm using Xfce instead of Gnome, but that shouldn't be a problem I guess... And opening that same file in xmms works fine here too.

---

### Post by darehanl on 2006-06-12
Got the po file done. I don't speak python, so I don't know how to apply this, though.

---

### Post by synic on 2006-06-12
[QUOTE=darehanl]Got the po file done. I don't speak python, so I don't know how to apply this, though.[/QUOTE]

Ok, I've put this in svn.  You'll have to type 'make' to convert the .po files to .mo.  If you could svn update and let me know if it worked?

Thanks,

--synic

---

### Post by ChaKy on 2006-06-12
I am having this error, while trying to start player after install:

```
chaky@ubuntu:~/Downloads$ exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "/usr/bin/exaile", line 1918, in ?
    main()
  File "/usr/bin/exaile", line 1908, in main
    exaile = ExaileWindow(fr)
  File "/usr/bin/exaile", line 70, in __init__
    self.DBConnect()
  File "/usr/bin/exaile", line 484, in DBConnect
    self.db = db.DBManager("%s%smusic.db" %
  File "/usr/share/exaile/xl/db.py", line 20, in __init__
    cur.execute("PRAGMA synchronize=OFF")
pysqlite2.dbapi2.Warning: You can only execute one statement at a time.

```

---

### Post by Bogart on 2006-06-12
I found the problem. A plugin called gstreamer-neon is needed to listen to http streams from shoutcast. I think this plugin belongs to plugins-bad pack, but for whatever reason it's not included in the arch's gstreamer0.10-bad pack and you have to install it independently.

It's all good now. Thanks ! :)

---

### Post by synic on 2006-06-12
[QUOTE=ChaKy]I am having this error, while trying to start player after install:

```
chaky@ubuntu:~/Downloads$ exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "/usr/bin/exaile", line 1918, in ?
    main()
  File "/usr/bin/exaile", line 1908, in main
    exaile = ExaileWindow(fr)
  File "/usr/bin/exaile", line 70, in __init__
    self.DBConnect()
  File "/usr/bin/exaile", line 484, in DBConnect
    self.db = db.DBManager("%s%smusic.db" %
  File "/usr/share/exaile/xl/db.py", line 20, in __init__
    cur.execute("PRAGMA synchronize=OFF")
pysqlite2.dbapi2.Warning: You can only execute one statement at a time.

```[/QUOTE]

Not really sure about this one.  It happens every time you try to start exaile?

Adam

---

### Post by ChaKy on 2006-06-13
[QUOTE=synic]Not really sure about this one.  It happens every time you try to start exaile?

Adam[/QUOTE]

Yes, it happens every time.

---

### Post by topyli on 2006-06-13
I'm using the 0.2b package from the home page. It works perfectly and I haven't yet stopped loving this player very hard. :)

One thing that makes me wonder us high CPU usage though. I have an old 900MHz box with 256M RAM so these things are easy to notice. When the Exaile UI is visible, My CPU usage is steadily at 50% (this raises CPU temp and fan noise, which is annoying). With Exaile minimized to the notification area, CPU usage is immediately cut down to around 10-20%.

This is strange, the process is running and music playing all the time so I can't imagine why drawing the Exaile window would be so expensive...

---

### Post by Bogart on 2006-06-14
[QUOTE=topyli]One thing that makes me wonder us high CPU usage though. I have an old 900MHz box with 256M RAM so these things are easy to notice. When the Exaile UI is visible, My CPU usage is steadily at 50% (this raises CPU temp and fan noise, which is annoying). With Exaile minimized to the notification area, CPU usage is immediately cut down to around 10-20%.

This is strange, the process is running and music playing all the time so I can't imagine why drawing the Exaile window would be so expensive...[/QUOTE]

I noticed the same thing. When Exaile is visible or even minimized to the taskbar it uses about 20% of my CPU (on a P4 2.6 Ghz). Only closing it to the tray icon gets the CPU usage down to 2% or so.

---

### Post by synic on 2006-06-14
[QUOTE=topyli]I'm using the 0.2b package from the home page. It works perfectly and I haven't yet stopped loving this player very hard. :)

One thing that makes me wonder us high CPU usage though. I have an old 900MHz box with 256M RAM so these things are easy to notice. When the Exaile UI is visible, My CPU usage is steadily at 50% (this raises CPU temp and fan noise, which is annoying). With Exaile minimized to the notification area, CPU usage is immediately cut down to around 10-20%.

This is strange, the process is running and music playing all the time so I can't imagine why drawing the Exaile window would be so expensive...[/QUOTE]

I've done some updates that /may/ fix this problem for you.  I've committed them to svn, so if you want to update and let me know...

Thanks,

Adam

---

### Post by Bogart on 2006-06-15
[QUOTE=synic]I've done some updates that /may/ fix this problem for you.  I've committed them to svn, so if you want to update and let me know...

Thanks,

Adam[/QUOTE]

I updated from svn and the CPU usage problem is fixed. Thanks !

Another thing: I added to my music folder some files that are UTF-8 encoded, while the rest are ISO-8859-1 (my default encoding) and they don't appear in my collection after rescanning the folder (QuodLibet can read them, though, so I guess it's possible to read files with different encondings).

---

### Post by mzilhao on 2006-06-15
very nice player! i've been using Rhythmbox and Listen and i'm really enjoying Exaile.
one thing, though: how can i add more (non shoutcast) radio streams?

great work!

---

### Post by Harold P on 2006-06-15
Loving the .deb :D

---

### Post by topyli on 2006-06-15
[quote=Bogart]I updated from svn and the CPU usage problem is fixed. Thanks !
[/quote]

Yes! Just built the latest SVN and suddenly COU usage is down to around 20% regardless of the Exaile UI being visible or minimized to tray. Exaile seems to use around 7 to 12% (on my 900MHz box) which is very good for a python program I guess. Thanks synic, Exile's level of awesomeness is getting higher by the day :)

---

### Post by INMCM on 2006-06-15
Synic - have you ever looked into using [Psyco]("http://psyco.sourceforge.net/") to improve performance in Exaile? I've heard it can work "miracles" in speeding up python code.

---

### Post by Bogart on 2006-06-16
[QUOTE=INMCM]Synic - have you ever looked into using [Psyco]("http://psyco.sourceforge.net/") to improve performance in Exaile? I've heard it can work "miracles" in speeding up python code.[/QUOTE]

For what I've heard, Psyco improves performance (sometimes dramatically), but it uses more RAM and is a bit less stable. Given the nature of Exaile, I don't think that performance (meaning runtime speed) is as important as RAM usage or stability.

However, it's said to be very easy to use (no code changes, AFAIK) so nothing is lost by trying it, I guess...

---

### Post by synic on 2006-06-16
[QUOTE=INMCM]Synic - have you ever looked into using [Psyco]("http://psyco.sourceforge.net/") to improve performance in Exaile? I've heard it can work "miracles" in speeding up python code.[/QUOTE]

I just put it in, so if you want to update and try it out...

---

### Post by nalmeth on 2006-06-17
Now using 0.2 deb, and already a lot of things fixed from old binary release. 

Tab fetching is the bomb, even if it doesn't always work. I find if I rename the tags for title and album, it will sometimes work, but often still not.

I seem to remember you said the API situation was poor with fretplay, does this explain the searching problem? Could it be that there *are* tabs for the songs and the API fails to corrolate them with the search? I know fretplay has a lot more metallica than anything, (One of the guys behind the site is a huge metallica buff and runs encyclopedia metallica (encycmet)). As a result I get tabs for most any Metallica song I have.

Are you still using fretplay?

One more thing for now, is it possible to have the track information tab refresh when a new song starts? You have to close the tab and open a new one for info on the new song.

:cool: Lovin' the (AFAIK) first ever tab fetching music player :cool:

---

### Post by AThomsen on 2006-06-17
deleted

---

### Post by pgmario on 2006-06-17
Very good work, Exaile runs very stable here and has some great features!
[quote=nalmeth]One more thing for now, is it possible to have the track information tab refresh when a new song starts? You have to close the tab and open a new one for info on the new song.[/quote]That's what I would like to see, too. It would be much more convenient that way, I think.

Another useful feature which I use in Amarok all the time are **custom dynamic playlists** with filters like "all songs with a rating of higher than X".

Exaile is already the best non-KDE player, and it's pretty damn close to Amarok.

Very well done, keep it up!

---

### Post by nalmeth on 2006-06-17
synic, another thing.

for the dependencies you have described to install before the .deb, libgstreamer0.10 and libgstreamer0.10-plugins-good don't exist.

```
sdcb@vaiobuntu:~$ apt-cache search libgstreamer
**libgstreamer-plugins-base0.10-0** - GStreamer libraries from the "base" set
**libgstreamer-plugins-base0.10-dev** - GStreamer development files for libraries from the "base" set
**libgstreamer0.10-0** - Core GStreamer libraries and elements
**libgstreamer0.10-0-dbg** - Core GStreamer libraries and elements
**libgstreamer0.10-dev** - GStreamer core development files
libgstreamer-gconf0.8-0 - GConf support for GStreamer
libgstreamer-gconf0.8-dev - Development files for GConf support for GStreamer
libgstreamer-plugins0.8-0 - Various GStreamer libraries and library plugins
libgstreamer-plugins0.8-dev - Development files for various GStreamer library and library plugins
libgstreamer0.8-0 - Core GStreamer libraries, plugins, and utilities
libgstreamer0.8-dev - GStreamer development libraries and headers
libgstreamer0.8-ruby - GStreamer 0.8 bindings for the Ruby language
``` Should the items in **bold** be installed? What functionality does this add? Exaile seems to run fine without (same situation on my PC, all repositories are enabled BTW).

EDIT: Funny, I already have the items in **bold** installed. Might just want to adjust your dependency directions

---

### Post by topyli on 2006-06-18
I don't like the Last.fm player, so I'm using [Lastfmproxy]("http://vidar.gimp.org/lastfmproxy/") so I can listen to my Last.fm stations with *cough*Exaile!*cough* my favorite player. :)

By adding the lastfmproxy URL and a dummy URL (localhost:1881/skip) into my Last.fm station in Exaile, I can skip songs. (pressing "next track" twice). However, it might be nice to include proper last.fm playback support with all the functions: skip, ban, love at least.

Might actually be pretty easy by cannibalizing code from the [LastamaroK]("http://kde-apps.org/content/show.php?content=39883") plugin, which is itself based on lastfmproxy :)

---

### Post by metafile on 2006-06-18
Have you thought about equalizer? This is one of the crucial reasons for me to use amaroK.

---

### Post by synic on 2006-06-19
[QUOTE=nalmeth]synic, another thing.

for the dependencies you have described to install before the .deb, libgstreamer0.10 and libgstreamer0.10-plugins-good don't exist.

```
sdcb@vaiobuntu:~$ apt-cache search libgstreamer
**libgstreamer-plugins-base0.10-0** - GStreamer libraries from the "base" set
**libgstreamer-plugins-base0.10-dev** - GStreamer development files for libraries from the "base" set
**libgstreamer0.10-0** - Core GStreamer libraries and elements
**libgstreamer0.10-0-dbg** - Core GStreamer libraries and elements
**libgstreamer0.10-dev** - GStreamer core development files
libgstreamer-gconf0.8-0 - GConf support for GStreamer
libgstreamer-gconf0.8-dev - Development files for GConf support for GStreamer
libgstreamer-plugins0.8-0 - Various GStreamer libraries and library plugins
libgstreamer-plugins0.8-dev - Development files for various GStreamer library and library plugins
libgstreamer0.8-0 - Core GStreamer libraries, plugins, and utilities
libgstreamer0.8-dev - GStreamer development libraries and headers
libgstreamer0.8-ruby - GStreamer 0.8 bindings for the Ruby language
``` Should the items in **bold** be installed? What functionality does this add? Exaile seems to run fine without (same situation on my PC, all repositories are enabled BTW).

EDIT: Funny, I already have the items in **bold** installed. Might just want to adjust your dependency directions[/QUOTE]


Hrmm, I'll look into this.

---

### Post by synic on 2006-06-19
[QUOTE=nalmeth]Now using 0.2 deb, and already a lot of things fixed from old binary release. 

Tab fetching is the bomb, even if it doesn't always work. I find if I rename the tags for title and album, it will sometimes work, but often still not.

I seem to remember you said the API situation was poor with fretplay, does this explain the searching problem? Could it be that there *are* tabs for the songs and the API fails to corrolate them with the search? I know fretplay has a lot more metallica than anything, (One of the guys behind the site is a huge metallica buff and runs encyclopedia metallica (encycmet)). As a result I get tabs for most any Metallica song I have.

Are you still using fretplay?

One more thing for now, is it possible to have the track information tab refresh when a new song starts? You have to close the tab and open a new one for info on the new song.

:cool: Lovin' the (AFAIK) first ever tab fetching music player :cool:[/QUOTE]

Yup, still using fretplay.  I wish there was someway to easily get information from harmony-central.  

Yes, having the tab refresh on track change will be implemented in the future.

---

### Post by synic on 2006-06-19
[QUOTE=AThomsen]Using the latest version from svn I get this when scanning my collection:


*Lagersegmentfejl* is danish for *segmentation error*

The program looks really promising if only I could get it to work ;)[/QUOTE]

Do you have libgstreamer0.10-ffmpeg installed?  It looks as if it's dying on a .wma file.

---

### Post by synic on 2006-06-19
[QUOTE=topyli]I don't like the Last.fm player, so I'm using [Lastfmproxy]("http://vidar.gimp.org/lastfmproxy/") so I can listen to my Last.fm stations with *cough*Exaile!*cough* my favorite player. :)

By adding the lastfmproxy URL and a dummy URL (localhost:1881/skip) into my Last.fm station in Exaile, I can skip songs. (pressing "next track" twice). However, it might be nice to include proper last.fm playback support with all the functions: skip, ban, love at least.

Might actually be pretty easy by cannibalizing code from the [LastamaroK]("http://kde-apps.org/content/show.php?content=39883") plugin, which is itself based on lastfmproxy :)[/QUOTE]

Hrm, written in python and everything.  It probably would be pretty easy to use that code.  I'll check into it.

---

### Post by synic on 2006-06-19
[QUOTE=metafile]Have you thought about equalizer? This is one of the crucial reasons for me to use amaroK.[/QUOTE]

Probably with in the next couple of releases.  I personally don't use the equalizer at all :(

---

### Post by AThomsen on 2006-06-19
Using the latest version from svn I get this when scanning my collection:

> 
loading songs
Reloading artist tree
Running is False
/home/anders/mp3
/media/hda1/Mp3
/media/hdb1/Mp3
File count: 18639
artist: Pockets
audio codec: WMA Version 8
title: I Won't Be There Anymore
artist: Pockets
Total Unfree 0 bytes cnt 0 [(nil),0]
Lagersegmentfejl

*Lagersegmentfejl* is danish for *segmentation error*

The program looks really promising if only I could get it to work ;)

---

### Post by amunimanghi on 2006-06-20
Okay, I finally upgraded to dapper and I wanted to try it out. This is what I showed up after i typed   **sudo apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg**
```
 sudo apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
Reading package lists... Done
Building dependency tree... Done
Package python-wxgtk2.6 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-wxgtk2.6 has no installation candidate

```

I didnt know what to do then, so I just went ahead and downloaded the file using wget. Then I did ```
ameen@manghi:~$ sudo dpkg -i exaile_0.2b_i386.deb
```
I got this:
```

(Reading database ... 73264 files and directories currently installed.)
Preparing to replace exaile 0.2b (using exaile_0.2b_i386.deb) ...
Unpacking replacement exaile ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on python-pysqlite2; however:
  Package python-pysqlite2 is not installed.
 exaile depends on python-pymad; however:
  Package python-pymad is not installed.
 exaile depends on python-wxgtk2.6; however:
  Package python-wxgtk2.6 is not installed.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile
ameen@manghi:~$
```

I think I don't have all of my respiratories added or something like that. I'm pretty sure it is the respirtatores. If it is, where can I get them and how can I add them?

Thanks

---

### Post by synic on 2006-06-21
> 
I think I don't have all of my respiratories added or something like that. I'm pretty sure it is the respirtatores. If it is, where can I get them and how can I add them?

Thanks

Looks like python-wxgtk2.6 is in universe:

```


deb-src http://archive.ubuntu.com/ubuntu dapper universe
deb http://archive.ubuntu.com/ubuntu dapper universe

```

Adam

---

### Post by amunimanghi on 2006-06-21
It works. I just had to manually install the files in synaptic. One problem, how do you delete a file from your collection?

---

### Post by synic on 2006-06-22
[QUOTE=amunimanghi]It works. I just had to manually install the files in synaptic. One problem, how do you delete a file from your collection?[/QUOTE]

Do you want to delete it from the filesystem, or just block it from being in the collection?  For the first, just right click and go to "Delete", for the second, highlight the track, go to Tools->Blacklist Selected.

---

### Post by stubby on 2006-06-22
I had a problem with finding out how to delete tracks as well. 

May I put in the suggestion of binding the delete key to the delete function? Also, right clicking on the album sidebar should allow the option to delete/blacklist an album.

---

### Post by synic on 2006-06-22
[QUOTE=stubby]I had a problem with finding out how to delete tracks as well. 

May I put in the suggestion of binding the delete key to the delete function? Also, right clicking on the album sidebar should allow the option to delete/blacklist an album.[/QUOTE]

Currently the Delete key just removes the track from the playlist.

---

### Post by amunimanghi on 2006-06-22
Okay, Thanks a lot. Good luck in your future programs.

---

### Post by synic on 2006-06-22
Exaile 0.2b2 is released!

Changes include:

  * iPod write support
  * Drag & Drop support
  * wma file support
  * removed the track information update from the track timer (caused high cpu
    useage)
  * Updated artwork, exaile now tries to use the current gtk theme icons
  * Removed PIL dependancy

Get it from [http://www.exaile.org](http://www.exaile.org)

---

### Post by stubby on 2006-06-22
[QUOTE=synic]Currently the Delete key just removes the track from the playlist.[/QUOTE]
Yes, what if you wanted to remove the album from the collection though? There doesn't appear to be an easy way

---

### Post by synic on 2006-06-22
[QUOTE=stubby]Yes, what if you wanted to remove the album from the collection though? There doesn't appear to be an easy way[/QUOTE]

Yeah, I'll put this in the next release :)

---

### Post by GuitarHero on 2006-06-22
Nice program, but your site header needs a new font.  I would have no idea what it says if this thread didnt tell me.

---

### Post by jnev on 2006-06-23
I just installed the new version.. for whatever reason it doesn't read the id3 tags of almost my entire collection. it just says unknown for most of the albums (the artists are fine). amarok and all other music apps that I've tried have read them just fine. most of the tracks are id3 2.3 tags, but some are 2.2.

---

### Post by pgmario on 2006-06-24
Nice to see you implemented the automatic updating of track information. Great!

But does anyone else experience problems when **queuing songs**? Suppose I have a playlist with the songs 1,2,3,4,5. I start playback at #1 and queue #4. After #4 has finished, I would expect Exaile to start playback of #5, but it plays #2. Is this intentional? Happens with both betas.

---

### Post by pyros on 2006-06-24
WOW, I just can't belive Exaile is this cool and it's still so new.  You must be quite the programmer in your day job.

---

### Post by synic on 2006-06-24
[QUOTE=pgmario]Nice to see you implemented the automatic updating of track information. Great!

But does anyone else experience problems when **queuing songs**? Suppose I have a playlist with the songs 1,2,3,4,5. I start playback at #1 and queue #4. After #4 has finished, I would expect Exaile to start playback of #5, but it plays #2. Is this intentional? Happens with both betas.[/QUOTE]

It's intentional - the tracks are played in the order that they were queued, unless you specifically double click on another track.

---

### Post by synic on 2006-06-24
[QUOTE=pyros]WOW, I just can't belive Exaile is this cool and it's still so new.  You must be quite the programmer in your day job.[/QUOTE]

Thanks :)

---

### Post by pgmario on 2006-06-24
[quote=synic]It's intentional - the tracks are played in the order that they were queued, unless you specifically double click on another track.[/quote]It's logical that the songs are played in the order they are queued, but in my example #2 wasn't queued, it just happened to be on the playlist. Amarok handles it the way I expect it to, but I don't know, do others consider the way Exaile handles this at the moment to be better?
Anyway, great application, very mature for 0.2beta!

---

### Post by jasay on 2006-06-24
[QUOTE=pgmario]It's logical that the songs are played in the order they are queued, but in my example #2 wasn't queued, it just happened to be on the playlist. Amarok handles it the way I expect it to, but I don't know, do others consider the way Exaile handles this at the moment to be better?
Anyway, great application, very mature for 0.2beta![/QUOTE]
I'm probably not the one to ask since I basically only have two playlists and set whichever to shuffle every time, but anyway.  

I consider queued songs to be inserted or kind of squeezed into the space between the song playing now and the next one.  So if I had a playlist with ten songs and started playing 1 (with shuffle off).  Then if I queued up 4, 9 and 7 I would expect it to finish 1, then play 4,9,7 and go back to it's "regularly scheduled programming," that is 2.  So I personally like the way Exaile does it.  It might be nice to then skip over 4, 7 and 9 when it gets there in the playlist that way I don't hear the same song twice in quick succession.

---

### Post by gray-squirrel on 2006-06-24
Exaile is a great program, no doubt.  This is another reason for me to let go of the Winamp-style players and modernize.

I'm running this under Kubuntu, while I'm trying to decide whether xine or gstreamer is better for my ears and speakers.  (amaroK 1.3.9 ignores the gstreamer engine, despite the fact it's installed on my system.  And with them dropping support for gstreamer altogether, well. . .)  I encountered two minor issues, though.  When I removed songs from the playlist window in 0.2b, I could not get the songs back in there if I changed my mind.  This is true also of the 0.2b2 version I just downloaded and tested.  In addition, the "Remove from playlist" option appears to be always grayed out in the context menu, although songs can be removed from the playlist by highlighting them and pressing Delete.

There's one suggestion I wanted to make, although it's not really a big deal for me.  Running this in KDE means giving up other sounds, even though I'm using alsasink as the playback sink.  (I've already locked out aRts because it once again has been causing trouble on my system.)  If there's a way to add ALSA device configuration options, like amaroK currently has, this would be great - it would not only benefit those who use ALSA's dmix option in KDE to allow simultaneous sounds, it may also benefit those who want to use surround sound and other things.

Thanks for the program.  I too think it should be the default player for Gnome.

---

### Post by synic on 2006-06-24
[QUOTE=pgmario]It's logical that the songs are played in the order they are queued, but in my example #2 wasn't queued, it just happened to be on the playlist. Amarok handles it the way I expect it to, but I don't know, do others consider the way Exaile handles this at the moment to be better?
Anyway, great application, very mature for 0.2beta![/QUOTE]

Hrmm, I think I misunderstood your question at first.  Yeah, the behavior you're describing is a bug, and I'll work on fixing it.

---

### Post by pgmario on 2006-06-24
[quote=synic]Hrmm, I think I misunderstood your question at first.  Yeah, the behavior you're describing is a bug, and I'll work on fixing it.[/quote]Thanks! :D

---

### Post by lapsey on 2006-06-24
i really like how fast it is to load lib from database. as i have 10,000+ files on a samba server i find rhythmbox unusable.

what kind of checking does exaile do, for looking at changes in the library, and how fast is it?

one bug you may want to look at is that changing a 'sort by' of the playlist throws the display off: Nothing returns the list to the playlist order (that is, the order the items were added)
so the 'track playing' pointer points to the wrong items.


also is there any chance of rm/ram support in the future? a certain Winamp plugin did a good job of it with the realalternative codec

---

### Post by synic on 2006-06-25
[QUOTE=pgmario]Thanks! :D[/QUOTE]

Ok, this should be fixed in svn now.

---

### Post by synic on 2006-06-25
[QUOTE=lapsey]i really like how fast it is to load lib from database. as i have 10,000+ files on a samba server i find rhythmbox unusable.

what kind of checking does exaile do, for looking at changes in the library, and how fast is it?

one bug you may want to look at is that changing a 'sort by' of the playlist throws the display off: Nothing returns the list to the playlist order (that is, the order the items were added)
so the 'track playing' pointer points to the wrong items.


also is there any chance of rm/ram support in the future? a certain Winamp plugin did a good job of it with the realalternative codec[/QUOTE]


Yeah, we have about that many files on an NFS server here at work, so it was good testing ground for that :)

Currently it only checks for new files every 20 minutes or so.  I was going to implement something that only scanned changed directories... but I haven't done that yet.

Ah, hrmm... I'll have to think about the sorting problem.

As long as gstreamer supports it, it'll probably work.  I'll have to look into ram support.

---

### Post by pgmario on 2006-06-25
[quote=synic]Ok, this should be fixed in svn now.[/quote]Wow, you're fast! Thanks a lot!

---

### Post by AThomsen on 2006-06-25
[QUOTE=synic]Do you have libgstreamer0.10-ffmpeg installed?  It looks as if it's dying on a .wma file.[/QUOTE]
I have libgstreamer0.10-0 and gstreamer0.10-ffmpeg installed. I can't find any package named libgstreamer0.10-ffmpeg ;) 

I'm a programmer but have no experience with Python. Can you recommend a debugger so I can look deeper into this problem?

---

### Post by rjcsc on 2006-06-27
Great app... thanks!
But it deserves a better icon

---

### Post by synic on 2006-06-27
[QUOTE=rjcsc]Great app... thanks!
But it deserves a better icon[/QUOTE]

Are you volounteering?

---

### Post by pyros on 2006-06-28
hmm, there seems to be a bug in the column sorting for time. when I sort by time, it doesn't take double digit time into account. (version 0.2b2) for example, when arranged by time, a ten minute track is listed with th on minute tracks, the twenty with the two, the thirty with the three minute tracks and so on.

---

### Post by synic on 2006-06-28
[QUOTE=pyros]hmm, there seems to be a bug in the column sorting for time. when I sort by time, it doesn't take double digit time into account. (version 0.2b2) for example, when arranged by time, a ten minute track is listed with th on minute tracks, the twenty with the two, the thirty with the three minute tracks and so on.[/QUOTE]

Ok, I have committed a fix for this.

Adam

---

### Post by dilidon on 2006-06-28
[QUOTE=synic]Probably with in the next couple of releases.  I personally don't use the equalizer at all :([/QUOTE]
Just to support the suggestion of Metafile: I tried exile out and *it is nice*, however, also, a no-hassle equalizer is crucial for me, which made me also give up on Rhythmbox and stick with Amarok while running Gnome.
* Also, as a remark, Exaile did not catalogue any of my m4a files. All the mp3 and ogg ones are there. My problem or general?
* Is there any easy way to convert/copy the Amarok cover-art database to Exaile? It took me a lot of work to get my covers sorted. I'd hate to start all over again in case I switched.

---

### Post by pyros on 2006-06-29
[QUOTE=synic]Ok, I have committed a fix for this.

Adam[/QUOTE]

The dude abides. 
Thanks Adam.

---

### Post by venublood on 2006-06-29
Hi, I get this error when trying to run exaile:
```
fran@menhir:~/Desktop$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 19, in ?
    import wx, wx.grid, sys, os, re, random, fileinput, gc, urllib, md5
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
    from wx._core import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13405, in ?
    from _misc import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc.py", line 4, in ?
    import _misc_
ImportError: /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc_.so: symbol _ZTV11wxLogBuffer, version WXU_2.6 not defined in file libwx_baseu-2.6.so.0 with link time reference

```
I guess is something wrong with wx-2.6 but I don't know what to do :confused:

---

### Post by synic on 2006-06-29
[QUOTE=dilidon]Just to support the suggestion of Metafile: I tried exile out and *it is nice*, however, also, a no-hassle equalizer is crucial for me, which made me also give up on Rhythmbox and stick with Amarok while running Gnome.
* Also, as a remark, Exaile did not catalogue any of my m4a files. All the mp3 and ogg ones are there. My problem or general?
* Is there any easy way to convert/copy the Amarok cover-art database to Exaile? It took me a lot of work to get my covers sorted. I'd hate to start all over again in case I switched.[/QUOTE]

I've committed some changes that should allow your m4a files to be read.  Give it a try and let me know (I couldn't test it, as I have no files like this).

Converting the amarok database wouldn't be too difficult.  Are you using sqlite as your backend?

---

### Post by Schroeder on 2006-07-01
Hi, 

just checked out Exaile for the first time. Works well and definitely looks better than the cluttered amaroK interface. ;)

One thing I noticed:
In the track information panel the BITRATE is displayed in kHz, which is obviously wrong. It should be kbps. 

Is there any way to disable certain columns? I dont use rating so I would like to disable that column.

CHris

---

### Post by dilidon on 2006-07-01
[QUOTE=synic]I've committed some changes that should allow your m4a files to be read.  Give it a try and let me know (I couldn't test it, as I have no files like this).[/QUOTE]
Changed my previous reply from some time ago here, as I did a clean install of Exile and got the latest version via svn. The *.m4a files do indeed play. So that's pefectly fine. Thanks!
Maybe it's interesting to note that the player is only able to display the name of the file in the format of file_name.m4a and no other information stored in the file, so all m4a files are added to the collection under the unknown artist's unknown album.
> Converting the amarok database wouldn't be too difficult.  Are you using sqlite as your backend?
Yup.

---

### Post by krazyd on 2006-07-03
hey synic, this looks awesome! 

A couple of features which would make this a killer app IMHO:
- replaygain support
- gapless playback

I can't believe how quickly you have developed this into a mature app.. looking forward to the upcoming release! Thanks :D

---

### Post by pyros on 2006-07-03
[QUOTE=synic]Ok, I have committed a fix for this.

Adam[/QUOTE]
Ok, I finaly (july 3nd) got it checked out of svn and tested it... it appears to have them sorted by their times correctly, but sometines the first digit is truncated. for example, I have a track that is 69 minutes and 46 seconds long, and, while it is shown in the list as 9 minutes and 46 seconds, it is in the right order for a 69 minute track. I hope that's not confusing, it's been a long day : )

---

### Post by jymbob on 2006-07-03
[QUOTE=krazyd]hey synic, this looks awesome! 

A couple of features which would make this a killer app IMHO:
- replaygain support
- gapless playback

I can't believe how quickly you have developed this into a mature app.. looking forward to the upcoming release! Thanks :D[/QUOTE]

Seconded, on all counts.

As an aside, Exaile doesn't appear to be handling mulit-artist albums properly here: enqueues as: album->a.artist 1st track (eg #7), a.artist 2nd track (eg #8), b.artist 1st track (eg #1) and so on.

Still, I'm using Amarok less and less!

Can I also ask for configurable global keyboard shortcuts?

---

### Post by xplode_me on 2006-07-04
Is there anyway to spill out the currently playing music to xchat?

---

### Post by Polygon on 2006-07-04
i kept getting: 

```
mark@ubuntu:~$ sudo apt-get install python-wxgtk2.6 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgstreamer0.10
```

when i tried to install it. im going to try installing it without that (or libgstreamer0.10-plugins-good, same problem)

and now its stuck on:

```
mark@ubuntu:~$ wget http://www.exaile.org/files/exaile_0.2b_i386.deb
--16:58:02--  http://www.exaile.org/files/exaile_0.2b_i386.deb
           => `exaile_0.2b_i386.deb'
Resolving www.exaile.org... 64.251.22.233
Connecting to www.exaile.org|64.251.22.233|:80...
```

---

### Post by mmcmonster on 2006-07-04
Great player.  I'm using 0.2b right now, and had a few UI suggestions:
1. A keyboard shortcut for "Edit Track Information"
2. An edit menu that mirrors what highlighting a song and right-clicking "Edit"
3. When selecting a track and right-clicking Edit -> Track information, the window that pops up should be active (so that typing text should edit the title), and the Save button should be pressed if the user hits <Enter>.
4. Customize the colums that are viewed on the main window.  Some people don't use ratings, so the colum is quite useless, while others like seeing the file name of the file.

Also, 1 question: Are the album pictures stored in the .mp3 files by default or in a local database?  Personally I would like them stored in the .mp3 files (so they will show up in other applications (or an ipod) without any issues).

---

### Post by Polygon on 2006-07-05
nvm about my eariler post, it seems that your site was just down or something.

i noticed a bug, fooling around with "preferences", i clicked "show on screen display" and it opened a window that says "move this window to the position you want", so i moved it and nothing happened. even after i clicked ok, and closed out of prefs, its still there. even if i declick "on screen display" it still shows up.

---

### Post by samir85 on 2006-07-05
Here, the characters are screwed up.
Have a look here:
[http://home.arcor.de/ar0079218227/pub/pics/exaile.png](http://home.arcor.de/ar0079218227/pub/pics/exaile.png)

anybody experiencing the same issue ?

---

### Post by xplode_me on 2006-07-06
Am i the only one unable to set custom cover images?

Exaile 0.2b2 here...

---

### Post by bvc on 2006-07-07
Nice work. If it hasn't been mentioned yet, may I suggest

1. Let the theme dictate the color of Files, Radio, Playlist, Collections. Main reason I couldn't stand amarok and removed it immediately. Looked horrible...yeah so skins..(yuk)..makes a lot more sense to use gtk theme control, and a lot easier for a unified desktop.

2.Make it default for the tabs to be on top, adding an option to put them elsewhere. Themes that do not have tabs other than the top will look bad, and that's a lot of them. Not that they should be that way, but they are.

---

### Post by feanor_arcamenel on 2006-07-07
Just like previously posted, those libraris couldnt be find:
gstreamer 0.10, gstreamer0.10-plugins-good
And without them, I get this:

aytackubilay@aytackubilay:/etc/apt$ sudo dpkg -i /home/aytackubilay/Desktop/exaile_0.2b2_i386.deb
Selecting previously deselected package exaile.
(Reading database ... 91261 files and directories currently installed.)
Unpacking exaile (from .../Desktop/exaile_0.2b2_i386.deb) ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on libpango1.0-0 (>= 1.12.3); however:
  Version of libpango1.0-0 on system is 1.12.2-0ubuntu3.
 exaile depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not installed.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile

---

### Post by croak77 on 2006-07-07
> **feanor_arcamenel said:**
> Just like previously posted, those libraris couldnt be find:
gstreamer 0.10, gstreamer0.10-plugins-good
And without them, I get this:

aytackubilay@aytackubilay:/etc/apt$ sudo dpkg -i /home/aytackubilay/Desktop/exaile_0.2b2_i386.deb
Selecting previously deselected package exaile.
(Reading database ... 91261 files and directories currently installed.)
Unpacking exaile (from .../Desktop/exaile_0.2b2_i386.deb) ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on libpango1.0-0 (>= 1.12.3); however:
  Version of libpango1.0-0 on system is 1.12.2-0ubuntu3.
 exaile depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not installed.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile

Are you using Dappper?

---

### Post by reacocard on 2006-07-07
> **samir85 said:**
> Here, the characters are screwed up.
Have a look here:
[http://home.arcor.de/ar0079218227/pub/pics/exaile.png](http://home.arcor.de/ar0079218227/pub/pics/exaile.png)

anybody experiencing the same issue ?

yep, same problem.

---

### Post by 3rdalbum on 2006-07-08
I'm using Exaile, and I think it's excellent for such a new program. I think the version I'm using is quite old, so I won't give my suggestions in case they've already been implemented :-)

Except... if you could add the ability to transfer songs to HDD MP3 players, that would be much appreciated :-)

---

### Post by feanor_arcamenel on 2006-07-08
> **croak77 said:**
> Are you using Dappper?

oops, no -mine is badger-. I tried to install and actually installed some of the packages necessary using dapper repositories. But when it came to last 2 ones here I mentioned -libgstreamer 0.10 and the good one - it couldn't find them somehow. Then I added some additional repositories. Then the result was just amazing :) It listed nearly the whole dapper as prerequisite. :D

I thinks there are no other ways but to install dapper for me.

---

### Post by nir78 on 2006-07-08
I try to use it but keep getting this error:
[PHP]Traceback (most recent call last):
  File "/usr/bin/exaile", line 19, in ?
    import wx, wx.grid, sys, os, re, random, fileinput, gc, urllib, md5
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
    from wx._core import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
    import _core_
ImportError: /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core_.so: symbol _ZN12wxAppConsole15CreateLogTargetEv, version WXU_2.6 not defined in file libwx_baseu-2.6.so.0 with link time reference
[/PHP]

Installation went fine and everything looks OK, so what is the issue :confused:

---

### Post by darkenedday on 2006-07-08
This looks GREAT, i love Amarok but I stopped using KDE because I thought GNOME was much more user friendly and clean looking and I'm trying to get my entire house to switch over to ubuntu, i have three of four loving linux, but my step dad is one of those "anything free can't be as good" idiot FOSS haters, I'll actually install it once i can get my house networked, right now the windows pc has to be the one on the internet cuz of him, but seriously it looks great, quite clean and uncluttered. NICELY DONE! and i can't wait to see more

---

### Post by monergist on 2006-07-09
Just wanted to say great job. I've been looking for a good music prog (I don't really like xmms too much, and amarok would never work right on my system (wouldn't add music from my music directory, some of the left side menus would cover the main window, etc), and your program installed flawlessly and works! The only problem I have is that it doesn't find all my music. Not sure as to why, and not sure which ones it didn't find. other than that, flawless! Thanks for giving me hope to finding a good player!

---

### Post by siminone on 2006-07-09
this is an awsome player!!! 

I love Amarok but I find it too cluttered and it does not go well with the Ubuntu theme.

Please make this part of the repos.

---

### Post by lazyd2 on 2006-07-09
Great player....I'm starting to like it more and more!!

---

### Post by elpresidente on 2006-07-09
Thanks for making this. I, too, have been using Amarok but use it on a gnome/xfce system. Amarok slows it way down. So far, I'm not having those problems with your software. Well done!.

---

### Post by elpresidente on 2006-07-10
Installing this on another computer and getting errors. Says wrong architecture (386) being installed on an amd64 (actually intel duo-core system). I forced it to install but it doesn't run. How can I make it work?

---

### Post by synic on 2006-07-11
> **elpresidente said:**
> Installing this on another computer and getting errors. Says wrong architecture (386) being installed on an amd64 (actually intel duo-core system). I forced it to install but it doesn't run. How can I make it work?

Do you get an error if you run it from the CLI?

---

### Post by synic on 2006-07-11
Convert to GTK+

Are there any people interested in Exaile becoming pure GTK+ ?  I've looked into what it would take, and it sure wouldn't be trivial.  I've just heard some people mention that they'd prefer a fully GTK+ application.

Adam

---

### Post by synic on 2006-07-11
1. Let the theme dictate the color of Files, Radio, Playlist, Collections. Main reason I couldn't stand amarok and removed it immediately. Looked horrible...yeah so skins..(yuk)..makes a lot more sense to use gtk theme control, and a lot easier for a unified desktop.

How do you mean?  What version of Exaile are you using?  Currently, it attempts to use icons from the current theme.

2.Make it default for the tabs to be on top, adding an option to put them elsewhere. Themes that do not have tabs other than the top will look bad, and that's a lot of them. Not that they should be that way, but they are.[/QUOTE]

I will put this in.

---

### Post by synic on 2006-07-11
> **monergist said:**
> Just wanted to say great job. I've been looking for a good music prog (I don't really like xmms too much, and amarok would never work right on my system (wouldn't add music from my music directory, some of the left side menus would cover the main window, etc), and your program installed flawlessly and works! The only problem I have is that it doesn't find all my music. Not sure as to why, and not sure which ones it didn't find. other than that, flawless! Thanks for giving me hope to finding a good player!

Are you using the latest SVN version?

---

### Post by Dusk2k2 on 2006-07-11
Hi, just want to give props to Exaile, and I have a question.

With the Ipod, is there anyway to make the library on Exaile and my Ipod library sync?  I don't know if I just can't find it, but it is a real pain to have to look for the song and then transfer it to my Ipod, when on Gtkpod, I can just sync the libraries and not have to deal with that.

---

### Post by Xterminator on 2006-07-12
Nice player, i write a little review in portuguese pt_BR.
[http://gnomosapiens.wordpress.com/2006/07/12/exaile-um-novo-player-para-quem-nao-curtiu-o-listen/](http://gnomosapiens.wordpress.com/2006/07/12/exaile-um-novo-player-para-quem-nao-curtiu-o-listen/)

---

### Post by RafRaf on 2006-07-13
Dusk2k2, I totally agree with you. Of my knowledge there is only one app that can do the library sync and that is Banshee. Unfortunately using Banshees sync screwed up my ipod, now Im hoping that their new version that is out soon will solve this.

Others have had positive results with Banshee, check it out.

And it would be great if Exaile also had the library sync feature.

---

### Post by punkass on 2006-07-13
Would it be possible to have gnome-vfs support?

As I keep most of music on a shared seperate server.

Other than that I think its great.

---

### Post by bvc on 2006-07-14
> **synic said:**
> Convert to GTK+

Are there any people interested in Exaile becoming pure GTK+ ?  I've looked into what it would take, and it sure wouldn't be trivial.  I've just heard some people mention that they'd prefer a fully GTK+ application.

Adamyes! yes! yes! ..because of #1 below. Themer constantly get complaints about firefox and open office, but we have no control over that, and that is ashame. All gnome apps should be gtk....gnome/gtk.....makes sense, nothing else does.

> **synic said:**
> 1. Let the theme dictate the color of Files, Radio, Playlist, Collections. Main reason I couldn't stand amarok and removed it immediately. Looked horrible...yeah so skins..(yuk)..makes a lot more sense to use gtk theme control, and a lot easier for a unified desktop.

How do you mean?  What version of Exaile are you using?  Currently, it attempts to use icons from the current theme.

2.Make it default for the tabs to be on top, adding an option to put them elsewhere. Themes that do not have tabs other than the top will look bad, and that's a lot of them. Not that they should be that way, but they are.

I will put this in.1. the latest. I'm not referring to icons. I mean the color of the tab. Where is that defined? Because I was using a [darker theme]("http://gnomethemes.org/?p=44") which doesn't have white anywhere in the gtkrc, but the tabs where white and not the color I specified for tabs.

2. thank you!!!

---

### Post by GNUbieNZ on 2006-07-14
> **RafRaf said:**
> Dusk2k2, I totally agree with you. Of my knowledge there is only one app that can do the library sync and that is Banshee. Unfortunately using Banshees sync screwed up my ipod, now Im hoping that their new version that is out soon will solve this.

Others have had positive results with Banshee, check it out.

And it would be great if Exaile also had the library sync feature.

The latest release (0.9.5, came out yesterday ;)) of rhymthbox has ipod sync support.
[http://www.gnome.org/projects/rhythmbox/news.html]("http://www.gnome.org/projects/rhythmbox/news.html")

Dave

---

### Post by bvc on 2006-07-15
Concerning Files, Radio, Playlist, Collections.....
I realize we probably don't want yet another notebook there, so I don't know how you'd color them. They could just use the button colors, or just put buttons there? Can't buttons be vertical? My point was that if you used a darker theme the white would kill the look. [This]("http://gnomethemes.org/pre/Clear-Alternative-full2.png") isn't exactly a dark theme, but the only place that is white in the gtkrc is the base[NORMAL] text entry/views but the theme I was using did not have any white at all.

---

### Post by pgmario on 2006-07-16
> **pgmario said:**
> But does anyone else experience problems when **queuing songs**? Suppose I have a playlist with the songs 1,2,3,4,5. I start playback at #1 and queue #4. After #4 has finished, I would expect Exaile to start playback of #5, but it plays #2.I just checked out the latest version of Exaile with svn, and the problem still persists. Any ideas? Thanks!

---

### Post by grte on 2006-07-17
[quote=synic]
Convert to GTK+

Are there any people interested in Exaile becoming pure GTK+ ? I've looked into what it would take, and it sure wouldn't be trivial. I've just heard some people mention that they'd prefer a fully GTK+ application.

Adam[/quote]

Absolutely, *yes!*  The only reason I'm not currently using this app is that because of my theme and the way Exaile handles colours, half of the songs in my queue will be unreadable unless selected.  If Exaile worked as well with my themes as Rhythmbox, I'd be all over it.

---

### Post by feanor_arcamenel on 2006-07-17
hi, I finall upgraded to dapper and installed exaile. I guess it is the latest version, since got it from exaile.org. However I don't have an information tab to use lyrics and wiki stuff :-k

---

### Post by the_fabs on 2006-07-18
please delete

---

### Post by Philaretus on 2006-07-20
Hey Synic!

Just wanted to say I love the app, keep the good job.

---

### Post by synic on 2006-07-20
> **Philaretus said:**
> Hey Synic!

Just wanted to say I love the app, keep the good job.


Thanks :)

---

### Post by synic on 2006-07-20
You folks tracking SVN might have noticed a bunch of changes in the repository lately.  Exaile is now almost completely converted to GTK+ (pygtk).  Some things I still haven't converted yet, but the bulk of the work is already done.

You'll also notice that Exaile has some new artwork!  A super nice guy from Germany has taken up the design task.  You'll soon also see a cool website designed by him.

---

### Post by grte on 2006-07-20
> **synic said:**
> You folks tracking SVN might have noticed a bunch of changes in the repository lately.  Exaile is now almost completely converted to GTK+ (pygtk).  Some things I still haven't converted yet, but the bulk of the work is already done.

You'll also notice that Exaile has some new artwork!  A super nice guy from Germany has taken up the design task.  You'll soon also see a cool website designed by him.

Thank you very much.  Your already excellent player is now the best of the bunch for me, now that it works with my theme.

---

### Post by pgmario on 2006-07-25
I have some problems with the svn version and beta3. The GUI doesn't work anymore. When I start Exaile, the new tray icon appears and playback of the first song in the playlist starts, but left or right-clicking on the icon doesn't do anything.
Thanks a lot for all the work you put into this application!

---

### Post by mmcmonster on 2006-07-25
One quick question - Where are album art stored?  Is it possible to set this?  I would like it to be stored in the mp3 itself, so that when I sync to an ipod (or read the mp3 over a network onto a windows PC running itunes) it's available.

---

### Post by Corbelius on 2006-07-25
I can't compile on amd64 system: 

```
:~/exaile$ make
cd mmkeys && make mmkeys.so && cd ..
make[1]: Entering directory `/home/gianvito/exaile/mmkeys'
pygtk-codegen-2.0 --prefix mmkeys \
        --register `pkg-config --variable=defsdir pygtk-2.0`/gdk-types.defs \
        --register `pkg-config --variable=defsdir pygtk-2.0`/gtk-types.defs \
        --override mmkeys.override \
        mmkeys.defs > gen-tmp
***INFO*** There are no declared global functions.
***INFO*** There are no declared methods.
***INFO*** There are no declared virtual proxies.
***INFO*** There are no declared virtual accessors.
***INFO*** There are no declared interface proxies.
mv gen-tmp mmkeyspy.c
cc -O2 `pkg-config --cflags gtk+-2.0 pygtk-2.0` -I/usr/include/python2.4/   -c -o mmkeyspy.o mmkeyspy.c
cc -O2 `pkg-config --cflags gtk+-2.0 pygtk-2.0` -I/usr/include/python2.4/   -c -o mmkeys.o mmkeys.c
cc -O2 `pkg-config --cflags gtk+-2.0 pygtk-2.0` -I/usr/include/python2.4/   -c -o mmkeysmodule.o mmkeysmodule.c
cc `pkg-config --libs gtk+-2.0 pygtk-2.0` -shared mmkeyspy.o mmkeys.o mmkeysmodule.o -o mmkeys.so
/usr/bin/ld: mmkeyspy.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
mmkeyspy.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [mmkeys.so] Error 1
make[1]: Leaving directory `/home/gianvito/exaile/mmkeys'
make: *** [mmkeys.so] Error 2
```

---

### Post by synic on 2006-07-25
> **mmcmonster said:**
> One quick question - Where are album art stored?  Is it possible to set this?  I would like it to be stored in the mp3 itself, so that when I sync to an ipod (or read the mp3 over a network onto a windows PC running itunes) it's available.

It's stored in ~/.exaile/covers

If you use Exaile to copy tracks to your iPod, the cover art will be copied as well.  

I'll have to look into what the limitations are for storing the album art in the metadata of the actual mp3 itself.  For some reason none of the other media players (amarok, listen, quodlibet) don't do this.

Adam

---

### Post by Aurdal on 2006-07-26
Synic, I love this player. Good work! :D

Any chanse there will be added support for Creative MP3 players?

---

### Post by nicbink on 2006-07-26
This is by-far the best all-around music player I have come across.  It combines all the features that I want.

GTKPOD - great for syncing to ipod but not a media management program and lack of built in player
Banshee - better but no IPOD playlist support
Rhythmbox - decent but minimal IPOD support
Listen - Getting a lot better but a bit buggy (at least for me)
Exaile - has all major requirments, ipod, playlists (export and import), filesystem browsing, streaming radio, queue manager.

One feature that I grew to love in Listen was the "live" playlist that would use last.fm and your local library to make a playlist based on the files you had and what last.fm recommended.

I am seriosly considering picking up some python books so I can help out with this app.  the above being one feature i would integrate and another being an insert into queue feature that would give you the option to insert a song randomly into the top 5, 10, 15, 20 songs (great for parties with open jukebox)

Thanks for the app (and inspiration to start programming again)


and not to bash on the efforts of the graphic designer that offered to help out but i preferred the original graphics.  the new ones are a bit generic.  i will probably throw some other options up here in the near future, that is something that i am currently capable of doing w/o learning new things.

---

### Post by mmcmonster on 2006-07-26
> **synic said:**
> It's stored in ~/.exaile/covers

If you use Exaile to copy tracks to your iPod, the cover art will be copied as well.  

I'll have to look into what the limitations are for storing the album art in the metadata of the actual mp3 itself.  For some reason none of the other media players (amarok, listen, quodlibet) don't do this.

Adam

Unfortunately, there is no standard place for all the different music players to store their cover art (or, if there is, no one is using it :-) ).

I seem to remember an application that converted the cover art in amaroK into id3 tags, but I can't seem to find it now.  I know I tried it once, since most of my album art was screwed up by it. :-(

I also used [Album Cover Art Downloader]("http://louhi.kempele.fi/%7Eskyostil/projects/albumart/"), which has the option to store the art in the ID3v2 APIC frame.

Perhaps the source of that program can help you out a bit?

---

### Post by synic on 2006-07-26
> **Aurdal said:**
> Synic, I love this player. Good work! :D

Any chanse there will be added support for Creative MP3 players?

Probably not unless a programmer that owns a Creative player helps me out.  I have no way to test it.

---

### Post by Bogart on 2006-07-27
I just updated from 0.2b2 to 0.2b4 and I like the new look. Besides, it now handles better some UTF-8 encoded files. Good upgrade ! :)

The problem I'm having is the tray icon doesn't work. I get a message saying:

```
Sorry, egg.trayicon is NOT available
```

By the way, now that I meantion the tray icon, one feature I'd love to see in the future is that you can place your mouse over it and adjust the volume with the mouse wheel. Quod Libet has this and it's really wonderful.

Oh, the wikipedia feature seems to be gone... Is it intentional because it worked so slow?

EDIT: I figured out about the trayicon problem. I needed python-gnome and python-gnome-extras. I think the wikipedia thing is also related to it, but didn't figure it out yet, but I'll do :)

---

### Post by JoWilly on 2006-07-27
Looks good ! I like the UI setup.

Please make amd64 packages available (you can build this from within your 32bit environment). 

And please put this in some repo so it'll update automatically.

---

### Post by synic on 2006-07-27
> **Bogart said:**
> I just updated from 0.2b2 to 0.2b4 and I like the new look. Besides, it now handles better some UTF-8 encoded files. Good upgrade ! :)

The problem I'm having is the tray icon doesn't work. I get a message saying:

```
Sorry, egg.trayicon is NOT available
```

By the way, now that I meantion the tray icon, one feature I'd love to see in the future is that you can place your mouse over it and adjust the volume with the mouse wheel. Quod Libet has this and it's really wonderful.

Oh, the wikipedia feature seems to be gone... Is it intentional because it worked so slow?

EDIT: I figured out about the trayicon problem. I needed python-gnome and python-gnome-extras. I think the wikipedia thing is also related to it, but didn't figure it out yet, but I'll do :)

egg.trayicon is in python-gnome2-extras.  Cool idea with the scroll wheel.

Wikipedia is also there (in python-gnome2-extras), and is a lot faster now :)

---

### Post by tseliot on 2006-07-27
I've just tried Exaile and I find it GREAT!

Keep up the good work!


Alberto


EDIT: I like it better than Amarok!

---

### Post by mmcmonster on 2006-07-27
I noticed that some files that appear correctly id3 tagged in other applications (particularly rhythmbox and quod libet) are not tagged correctly in exaile.

Is this a known bug?

---

### Post by synic on 2006-07-27
> **mmcmonster said:**
> I noticed that some files that appear correctly id3 tagged in other applications (particularly rhythmbox and quod libet) are not tagged correctly in exaile.

Is this a known bug?

How are they appearing in Exaile?

---

### Post by Johan! on 2006-07-27
Does Exaile play .mpc files?

---

### Post by synic on 2006-07-27
> **Johan! said:**
> Does Exaile play .mpc files?

I don't have any .mpc files myself, but I've heard it does.

---

### Post by mmcmonster on 2006-07-27
> **synic said:**
> How are they appearing in Exaile?

In Exaile the title of the mp3 is set to the file name, the artist and album are blank.  In rhythmbox the title, artist and album are all set correctly.  Would you like me to email you one of the mp3s?

---

### Post by synic on 2006-07-27
> **mmcmonster said:**
> In Exaile the title of the mp3 is set to the file name, the artist and album are blank.  In rhythmbox the title, artist and album are all set correctly.  Would you like me to email you one of the mp3s?

sure

---

### Post by Johan! on 2006-07-27
I can play .mpc files OK.
But I don't see them when I search for them in the library, not by artist, not album, and not genre.
If I browse to some .mpc files, I can add them to the playlist.

When I right-click on a playing .mpc file and choose information, it shows the band name, the title and the album...


Keep up the good work, I like this program =D>

---

### Post by populacho on 2006-07-28
i tried installing the deb package (exaile_0.2b4i386) but it says "error: dependency is not satifiable: libpango1.0-0"
i checked, and i do have libpango.
i also have the 0.2 version installed and it works perfectly
does anyone have the same problem? how can i install it?

---

### Post by foxy123 on 2006-07-28
tried the latest beta. The design is much improved, great job guys! 

Of minor annoyances, the album cover does not appear on OSD. Why is that?

---

### Post by lazyd2 on 2006-07-28
The latest beta will not import music...

---

### Post by synic on 2006-07-28
> **lazyd2 said:**
> The latest beta will not import music...

Can you elaborate?

---

### Post by gruvsyco on 2006-07-28
> **lazyd2 said:**
> The latest beta will not import music...
I had the same problem... tried to point it to my library and it crashes as soon as it starts to scan.  My library is on NTFS, not sure if that would make a dif.

---

### Post by synic on 2006-07-28
> **gruvsyco said:**
> I had the same problem... tried to point it to my library and it crashes as soon as it starts to scan.  My library is on NTFS, not sure if that would make a dif.

An error message would be helpful

---

### Post by blackdahliamurder on 2006-07-28
Could we get a new link please? The one in the original post seems to be broken.

---

### Post by synic on 2006-07-28
> **blackdahliamurder said:**
> Could we get a new link please? The one in the original post seems to be broken.

Ok, a new link is up.

---

### Post by synic on 2006-07-28
> **foxy123 said:**
> tried the latest beta. The design is much improved, great job guys! 

Of minor annoyances, the album cover does not appear on OSD. Why is that?

It's working for me?

---

### Post by lazyd2 on 2006-07-28
> **synic said:**
> Can you elaborate?Here's what I get

```
exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Error reading settings file, using defaults.
loading songs
mmkeys are available.
Running is False
/media/sdb6
File count: 39
Count is now: 39

```

(I have over 3000 songs)

---

### Post by blackdahliamurder on 2006-07-28
This player looks very nice. :)

I'll be trying it as soon as I get my internet working under Dapper. But I will try to compile the tarbal in Gentoo tonight if I have the change. :)

Good work.

---

### Post by synic on 2006-07-28
> **lazyd2 said:**
> Here's what I get

```
exaile
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Error reading settings file, using defaults.
loading songs
mmkeys are available.
Running is False
/media/sdb6
File count: 39
Count is now: 39

```

(I have over 3000 songs)

Do you have python2.4-pymad installed?

---

### Post by lazyd2 on 2006-07-28
> **synic said:**
> Do you have python2.4-pymad installed?You're da man :p

Working great again,
Thank you:KS

---

### Post by Touch.Code on 2006-07-28
AAAAAAAAAAHhhhhhhh... Its not working for me!

```
[COLOR="Red"]**Error: Dependency is not satisfiable: libpango1.0-0**[/COLOR]
```

I wanna use it so badly!

---

### Post by gruvsyco on 2006-07-28
> **synic said:**
> An error message would be helpful
OK, just tried again from a terminal (to catch errors) and it worked OK with the scan.

---

### Post by foxy123 on 2006-07-28
> **synic said:**
> It's working for me?

have a look at the screenshot...

---

### Post by synic on 2006-07-28
> **foxy123 said:**
> have a look at the screenshot...

Was the OSD displayed before the cover was actually downloaded?

---

### Post by populacho on 2006-07-28
> **Touch.Code said:**
> AAAAAAAAAAHhhhhhhh... Its not working for me!

```
[COLOR="Red"]**Error: Dependency is not satisfiable: libpango1.0-0**[/COLOR]
```

I wanna use it so badly!


i get exatly the same message when i try to install it. does anyone know to fix this?

---

### Post by Touch.Code on 2006-07-29
Anyone? It would be nice to use this!

---

### Post by -X- on 2006-07-29
Excellent program, just keep on polishing it :)

---

### Post by foxy123 on 2006-07-29
> **synic said:**
> It's working for me?

ok, you need to fetch the covers to have them displayed on OSD. I've got most of them in the album folders as .folder.jpgs

---

### Post by 3rdalbum on 2006-07-29
I've got some more suggestions for Exaile (my favourite music player):

Have the Wikipedia-fetching in a seperate thread to the music playing. If it's taking a while to contact Wikipedia, the player won't switch tracks until the fetching is complete.

Also, if you could make it so that you can set a custom artist name to use for fetching covers and Wikipedia articles... because sometimes my ID3s say, for instance, "Delltones" and the article and cover are filed under "The Delltones" or something like that.

And if the Lyrics and Tabs sites don't find entries for the particular song because the ID3s have the track number at the beginning, Exaile should try again without the number at the beginning.

I know a little bit of Python, so I might just add some of those patches myself a bit later.

---

### Post by songo on 2006-07-29
hi..

this is what I did to get it on xubuntu before wget it. and it's ready for mp3!


```

# sudo apt-get install python-gtk2 python-pysqlite2 python-pymad python-gst0.10 python-pyogg python-libxml2 python-imaging python-dbus python-pyvorbis libgstreamer0.10-0 libgstreamer-plugins-base0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-esd gstreamer0.10-alsa gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad
# wget http://www.exaile.org/files/exaile_0.2b4_i386.deb
# sudo dpkg -i exaile_0.2b4_i386.deb

```

---

### Post by elpresidente on 2006-07-30
> **populacho said:**
> i get exatly the same message when i try to install it. does anyone know to fix this?

I had the same message. What I did:

```
sudo apt-get install libpango1.0-0
sudo apt-get -f install

```

Working great now. Great music player! Simple, effective and fast with large music collections. Keep up the great work!

---

### Post by chucknorris on 2006-07-30
---- Never mind, I solved the minor issue myself ;) Great player btw :)

---

### Post by laninuna on 2006-07-30
Hi,

I'm behind a proxy and it seems that Exaile does not know how to use the General Proxy settings from System -> Preferences -> Network Proxies.

Also there is no option to set up proxies in Exaile Preferences.

How can I make this work?

---

### Post by nalmeth on 2006-07-31
Synic,

Just found out about the new site, look, and .deb!

I was a little worried not seeing it in the website, but was pleased to find that tab fetching is still included in 2b.4.

I gotta hand it to you, man

Before, it was mainly the tab fetching feature that made me love exaile, but overall you have done a standup job with everything else.

=D>

Everything is looking "tight", the features work together quite well, and I've definately noticed the boost with the wikipedia lookup.
Not to mention the information refresh, the WAY better looking icons for the artists, new artwork, ahh, the list goes on.

Only con I have so far is the tab style on the far left as opposed to the old amarok like look. Is this due to the boost in pygtk code? I'll presume it is. Not that big a knock. :p

I have a LOT of ideas for music players in general, but I have some ideas which I think you could use in Exaile for the better. Where can I contact you to contribute some ideas? It is all I can contribute for now, though I may be getting a credit card soon.. Also, I'm going into programming this fall, hopefully I'll be able to help you code someday too.

Cheers man

---

### Post by LordMau on 2006-07-31
Hi testing out exaile now.

Just a suggestion can you not make ```
gstreamer0.10-esd
``` that much a dependency, considering most ubuntu users now use alsa, and I believe its now the deault sound system in dapper as well. Right now I think its  here but doing nothing I guess since I'm on alsa.

Thanks.

---

### Post by chucknorris on 2006-08-01
Any repository for Exaile?

---

### Post by yavez on 2006-08-02
I love this player, and I know I'm asking for the impossible here, but is there any chance of an option to switch from the Amarok style left pane with artist/albums etc to the more rythmbox 3 pane (itunes) like style?  Or maybe there is an option and I'm just missing it.  Anyway, it's a great program, the best player I've used on Gnome so far.  Keep up the good work, and Kudos to you for making it possible :)

---

### Post by oxEz on 2006-08-02
Is exaile.org down for anybody else?

---

### Post by thepizzaking on 2006-08-03
> **oxEz said:**
> Is exaile.org down for anybody else?

Not working here either

---

### Post by telmo on 2006-08-03
I'd like to try it but it's down for me too.... :(

Can i have the deb, anyone?

---

### Post by Sin_fe on 2006-08-03
> **oxEz said:**
> Is exaile.org down for anybody else?
Down here too... two days trying.
I'm also interested in the deb. Could anyone post?
Thanx in advanced.

---

### Post by Sin_fe on 2006-08-03
> **oxEz said:**
> Is exaile.org down for anybody else?
Down here too... two days trying.
I'm also interested in the deb. Could anyone post?
Thanx in advanced.

Edit: Sorry. Double Post.

---

### Post by synic on 2006-08-03
It should be back up now

---

### Post by oxEz on 2006-08-03
Many thanks synic!

---

### Post by synic on 2006-08-03
> **yavez said:**
> I love this player, and I know I'm asking for the impossible here, but is there any chance of an option to switch from the Amarok style left pane with artist/albums etc to the more rythmbox 3 pane (itunes) like style?  Or maybe there is an option and I'm just missing it.  Anyway, it's a great program, the best player I've used on Gnome so far.  Keep up the good work, and Kudos to you for making it possible :)

I'm actually not quite sure how iTunes does it, but maybe listen ([http://listengnome.free.fr](http://listengnome.free.fr)) is what you're looking for?

---

### Post by populacho on 2006-08-03
> **synic said:**
> I'm actually not quite sure how iTunes does it, but maybe listen ([http://listengnome.free.fr](http://listengnome.free.fr)) is what you're looking for?

yeah, I think that's what he means. 
Instead of changing it completely, how about having the option to pick what type of music browser you want? having an option in the preferences dialog instead of changing it completely would be great.

---

### Post by Sin_fe on 2006-08-04
Great player. Many Thanks.

---

### Post by BitTorrentBuddha on 2006-08-04
Is there an easy way to change the images next to artist name or change the locations from which to download the lyrics/tablature?

---

### Post by mmcmonster on 2006-08-04
> **populacho said:**
> yeah, I think that's what he means. 
Instead of changing it completely, how about having the option to pick what type of music browser you want? having an option in the preferences dialog instead of changing it completely would be great.

I've always had a preference of the iTunes interface.  A simple browser of libraries/playlists on the left, and the current contents on the right, with a small box in the lower left with album art.  Rhythmbox would be perfect if they had drag-n-drop changing of the albumart and better id3 tag editing support. :-(

---

### Post by lee_connell on 2006-08-04
keep up the good work, this is excellent!

one simple suggestion so far is that when I opened a stream the play icon that shows up next to the playing song is just a little too big for the column.

Thanks!

---

### Post by dmitriyr333 on 2006-08-04
nOOb need your help!!! 
   First off, this player is amazing! It is the most heavily used app on my box. But recently, I tried to mess around with audio output(???) and switched it to "ossink"(I think) from the default. 
  And now "Exaile" has left me with this:

```
Introspect error: The name org.exaile.DBusInterface was not provided by any .service files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "/usr/bin/exaile", line 1742, in ?
    main()
  File "/usr/bin/exaile", line 1734, in main
    exaile = ExaileWindow(fr)
  File "/usr/bin/exaile", line 112, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'Use GConf'
  File "/usr/share/exaile/xl/media.py", line 85, in set_audio_sink
    audio_sink = gst.element_factory_make(sink)
gst.PluginNotFoundError: ossink

```
Please, ohh please help me to debug/fix this problem. 

Thank you. 

p.s. complete reinstall did not help:confused: 

p.s.^2 Got it!!!!!!!!!!!!!!!  just edited .exaile/settings.ini:cool: 

Dmitriy> 

---

### Post by hanzomon4 on 2006-08-05
I can't add aac files to my library. I can play them off my ipod I just can't import the ones my hard-drive. The extension is m4a

---

### Post by involutaryhaxor on 2006-08-05
I like it alot! Looks like this is my new music player, I only have one problem. I didn't look through all of the pages of replies to see if someone said that they had the same problem as me, but several of the songs in my library are shown as being 0:00 in length, it still plays the song, but the little progress bar at the bottom of the screen doesn't work. But hey, I like it.

---

### Post by chucknorris on 2006-08-07
Does anyone get the Most Played/Least Played/Top 100 playlists to work? Mine shows the same tracks on the Most and Least played lists. The Top 100 is a bit different, but still.. When i check the Information tab, all of my tracks have a play count of 0? And System ratings of -2 or -3, whatever that means.

Great player though :)

---

### Post by m0unds on 2006-08-08
i'm really impressed with this app-- but it seems to ignore mp3's from my music library. it adds mpc, flac and ogg files without issue.. if i drag the files from the file browser, it adds them, but not when i scan the music library. am i missing

---

### Post by synic on 2006-08-08
> **m0unds said:**
> i'm really impressed with this app-- but it seems to ignore mp3's from my music library. it adds mpc, flac and ogg files without issue.. if i drag the files from the file browser, it adds them, but not when i scan the music library. am i missing

Depending on what version you're using, you'll need python-pymad.  This dep has been removed from the svn version.

---

### Post by flaak_monkey on 2006-08-08
ill have to give it a look, but i dig my Banshee so i doubt it will make me switch. :)

---

### Post by qaball on 2006-08-09
Synic - Great Job!  I like the look and it seems to work pretty well for shoutcast but I'm having some trouble with my library.  When I let it do the import or click on rescan it scans for a few seconds then crashes.  Here's the error:

File count: 4305
python: layer3.c:2633: mad_layer_III: Assertion `stream->md_len + md_len - si.main_data_begin <= (511 + 2048 + 8)' failed.
Aborted


My library is almost all mp3's and I'm running Ubuntu 6.06 with all the dependencies installed and at the required versions based on your web site.  If there's anything else you need to know I'll be happy to provide it.

Keep up the good work!

---

### Post by imaiden22 on 2006-08-10
hey synic, everything looks great so far but i haven't gotten a chance to try it out for myself. I'm planning on returning to gnome shortly because i switched over to kde a couple of months back and amarok was amazing to work with, so thanks for giving me exaile so i feel right at home on gnome as well. 

One request i have, like you said earlier, if you could get creative zen support that would be awesome because i plan to buy a vision m in the coming weeks and even though you mentioned the micro photo i would appreciate it if you tried to tackle the MTP problem and got us vision m folk some support too. Thanks in advance and i can't wait to give this thing a shot!!

---

### Post by Nicksha on 2006-08-11
Hi synic! Exaile is really wonderful. I've been looking for a player with media library capabilities to finally replace XMMS, but they all had something that's been putting me off their use. This one is, somehow, just what I've been looking for. Thanks!

Ideas for future implementation:
- configurable keybindings
- gapless playback (I know it has been mentioned already)
- choosing which drive is being used for audio cd's ('Open disc' menu command reads my dvd )
- when saving playlists on exit, how about saving multiple tabs (playlists)

Problem (just one):
- playlist doesn't display track names for audio cd's, but it does display them on the OSD (so, it did fetch the cd info)

None of these are really essential (gapless playback seems particularly hard to achieve; crossfade plugin for XMMS does it, but not many others), so I'm using it full time.

Thanks again!

---

### Post by jbodell on 2006-08-13
Ive been looking for a player as good as amarok to use in gnome. Nothing gets as close to amarok as this does. This is my new player- good work.

---

### Post by Sweet Spot on 2006-08-14
> **Nicksha said:**
> Hi synic! Exaile is really wonderful. I've been looking for a player with media library capabilities to finally replace XMMS, but they all had something that's been putting me off their use. This one is, somehow, just what I've been looking for. Thanks!

Ideas for future implementation:
- configurable keybindings
- gapless playback (I know it has been mentioned already)
- choosing which drive is being used for audio cd's ('Open disc' menu command reads my dvd )
- when saving playlists on exit, how about saving multiple tabs (playlists)

Problem (just one):
- playlist doesn't display track names for audio cd's, but it does display them on the OSD (so, it did fetch the cd info)

None of these are really essential (gapless playback seems particularly hard to achieve; crossfade plugin for XMMS does it, but not many others), so I'm using it full time.

Thanks again!


I'm going to have to second some of these requests/notions. One of the things on my top5 priority list for a media player, is Gapless Playback. Crossfade IMO doesn't cut it. Crossfade only either slices off part of what may be essential to the transition of the songs. I don't know how to code, so I dont' know how difficult this is to implament, but so many players these days do it. Hell, even my iRiver IHP 100 and iPod do it, with the assistance of ROCKbox firmware. 

Gapless is a must for me. But since there's really no options right now, from what I've seen, I'll have to settle for which ever player meets my other needs. So far, I've been pretty happy w/Amarok, but would like to try this one. Gapless would win me over in a second, considering how much people are boasting about it in general. I'm sure I'll try it anyway though, since it looks so good. 

Doug

---

### Post by doclivingston on 2006-08-14
> **Sweet Spot said:**
> I'm going to have to second some of these requests/notions. One of the things on my top5 priority list for a media player, is Gapless Playback. Crossfade IMO doesn't cut it. Crossfade only either slices off part of what may be essential to the transition of the songs. I don't know how to code, so I dont' know how difficult this is to implament, but so many players these days do it. Hell, even my iRiver IHP 100 and iPod do it, with the assistance of ROCKbox firmware. 

In theory any player that can do cross-fading should be able to do gapless - it's just a special case where the cross-over time is zero.

---

### Post by foxy123 on 2006-08-14
It's a great player and may very well replace Quod Libet (as QL replaced amarok) on my lapop. However, I would just like to mention a couple of points about exaile.
Firstly, it's sometimes quite difficult to drag-n-drop to add an album to the play-list. It does not have any pointer or anything like that and I am often left with dropping the album among the song of another one. In QL you can see a line where you actually drop the album. 

ALso if you try to remove the album from the queue the only option which is available is Balcklist. So I have to remove songs one by one.

---

### Post by feanor_arcamenel on 2006-08-17
I get this error (and I'm using xubuntu dapper)
is this about the libgstreamer0.10-plugins-good? I think I couldn't find t in repositories. Instead tried to use debian packages but couldn't. anyone can help? I know libgstreamer0.10-plugins-good is in here:
[http://packages.debian.org/unstable/libs/gstreamer0.10-plugins-good](http://packages.debian.org/unstable/libs/gstreamer0.10-plugins-good)
but cannot install from there :S


Introspect error: The name org.exaile.DBusInterface was not provided by any .ser vice files
***** You can safely ignore the above error.
Traceback (most recent call last):
  File "/usr/bin/exaile", line 1744, in ?
    main()
  File "/usr/bin/exaile", line 1736, in main
    exaile = ExaileWindow(fr)
  File "/usr/bin/exaile", line 111, in __init__
    media.set_audio_sink(self.settings.get('audio_sink', 'Use GConf'
  File "/usr/share/exaile/xl/media.py", line 81, in set_audio_sink
    audio_sink = gst.element_factory_make(sink)
gst.PluginNotFoundError: ossink

---

### Post by Bogart on 2006-08-17
Just installed 0.2b5 and it's looking sweet. It's great that you added this feature to control the volume with the scroll wheel over the trayicon :)

I still couldn't solve the Wikipedia proplem, though. I have gnome-python-extras package installed (that's why I can use the trayicon) but when I look at the information of a song the wikipedia tab doesn't show and I get this message:

gnome-extras not available.  Not showing artist or album information

I use Arch Linux, which installs the original package with the original name (unlike Ubuntu that splits it into 4 [packages]("http://packages.ubuntulinux.org/dapper/source/gnome-python-extras") and changes their name), so maybe that's the problem? I have all the libraries needed I think.

Thanks for your great work !

---

### Post by mrgnash on 2006-08-19
After trying all the usual suspects, I found that Exaile is the only one besides Amarok that properly indexes my collection, and it runs very well :D Great work!!

---

### Post by dmitriyr333 on 2006-08-22
> I get this error (and I'm using xubuntu dapper)
is this about the libgstreamer0.10-plugins-good? I think I couldn't find t in repositories. Instead tried to use debian packages but couldn't. anyone can help? I know libgstreamer0.10-plugins-good is in here:
[http://packages.debian.org/unstable/...0-plugins-good](http://packages.debian.org/unstable/...0-plugins-good)
but cannot install from there :S


Introspect error: The name org.exaile.DBusInterface was not provided by any .ser vice files
***** You can safely ignore the above error.
Traceback (most recent call last):
File "/usr/bin/exaile", line 1744, in ?
main()
File "/usr/bin/exaile", line 1736, in main
exaile = ExaileWindow(fr)
File "/usr/bin/exaile", line 111, in __init__
media.set_audio_sink(self.settings.get('audio_sink ', 'Use GConf'
File "/usr/share/exaile/xl/media.py", line 81, in set_audio_sink
audio_sink = gst.element_factory_make(sink)
gst.PluginNotFoundError: ossink
Reply With Quote
Try editing ~\.exaile/settings.ini and change ossink to alsa. Worked for me.
Hope this helps.

---

### Post by imaiden22 on 2006-08-24
quick question...does anybody know if exaile does the fading out like when you would quit amarok it would fade out the song currently playing, it's not super important but it makes for a wonderful effect and i was wondering if we could expect to see that in exaile?

---

### Post by ubuntublue on 2006-08-25
this music player is amazing man, props to you only thing that could be fixed a little is the lyrics function it only seems to work sometimes could maybe add a function like the cover art function to type in what u want to search for thanks for this program!

---

### Post by hanzomon4 on 2006-08-25
How do I get it to scan my non-drm aac files.

---

### Post by synic on 2006-08-25
> **hanzomon4 said:**
> How do I get it to scan my non-drm aac files.

What is the file extension?

---

### Post by populacho on 2006-08-25
hey man, awesome player... is it possble to have a "--start-hidden" option?

---

### Post by kpkeerthi on 2006-08-25
I think this will soon replace Quod Libet I have. Serves me great so far. Any idea of getting this into repository?

---

### Post by ExMachina on 2006-08-26
Looks good. 
I like having the "filter" / "search" bar.. Am I blind? Bc only listen has it.. xmmz / beep love the style.. but wish they had a search feature leik winamp .

---

### Post by hanzomon4 on 2006-08-26
> **synic said:**
> What is the file extension?

.m4a

---

### Post by gerkin on 2006-08-26
Great work Synic, the player runs great.  

Just what I was looking for a Gtk alternative to Amarok.  I'm still trying to get it to sync with my (non-ipod) Samsung YP-D1 music player (on Ubuntu Dapper), but still really Exaile is really great work.... many thanks

---

### Post by GAZ082 on 2006-08-26
Hey. This piece of software looks promising, but i could not make it work with my DAP, it aint an ipod, it's a iAudio. Ubuntu detects it, but either Banshee or Exaile do it. Any tip in Exaile?

---

### Post by Donnut on 2006-08-26
Ooooohhh, pretty and simple, thanks a lot!

---

### Post by banjobacon on 2006-08-26
I tried registering for the Exaile forum, but I never got a confirmation email.

These are points I wanted to bring up:

Exaile keeps triggering Last.fm's spam protection, so none of my songs are getting logged.

I can't play any of my Fantômas songs. I think the error I get is the same as the one reported by [this user](http://www.exaile.org/forum/thread/54), except I'm trying to play Vorbis files, not MP3s.

I can't append a particular album to the playlist, probably because it has a song called "5'2""

The Cancel button should be moved to the left side in some windows, such as the Open Media, Open Playlist and Export Playlist windows.

---

### Post by garybrlow on 2006-08-27
:-k mmmm is it just me or exaile's OSD during a radio stream does not function properly? Am using Xubuntu Dapper 6.06.1. It displays the default info at the beginning of the stream and when the song changes it doesn't show anymore as in no OSD. The the system tray icon tool tip does reflect the song change. It works fine with local media but with streaming its something else.

When I started using Exaile first on Kubuntu then Xubuntu it was said that there was a system tray icon but there was none that I saw. For Gnome users pehaps the dependencies were already installed but for KDE and XFCE who want to use Exaile, please include gnome-python & gnome-python-extras (and others I may have forgotten to mention) in the dependencies else there will be no system tray icon. :p 

In queueing items in a playlist you can't mix local media and radio streams. Also, when wanting to listen to/accessing a radio stream you can't queue a stream instead you have to double click on a stattion and a tab is open containing the stream(s) and then double click to play a stream. It is not user friendly that way. Most media players have easier straight forward steps for Radio stream/local file listing/saving/queueing. ;) 

For cover art, most of us living outside the US, our collections have items  that do not have US releases for the most part so it would be nice if non- US release covers can be fetched. So aside from amazon.com plus other locales(JAP,SPN,UK etc.) or perhaps other sites that support this kind of data fetching simillar in Amarok or perhaps even better. :rolleyes: 

Overall,this app rocks. :) Been looking for a more lightweight app compared to Amarok. This realy should be placed in the repositories or perhaps installed by default. :mrgreen:

This app is great!!! :KS Thank you Synic for developing such a great app!!!! ;)

-garybrlow

---

### Post by banjobacon on 2006-08-27
I don't mean to be harsh, but the album art grabber is pretty horrible. I understand it not finding album art on Amazon, but it constantly finds the *wrong* art.

---

### Post by Canute on 2006-08-28
Uhm, how does playlists work? I tried to make a new one, added some files, but as soon as i exited Exaile and i tried to open it up again the playlist was just blank. I can't seem to find a save button either.

---

### Post by imaiden22 on 2006-08-28
Another question...the album art, if we get all the art for our albums, is there a way we can download the graphics for local copies on our machines, for transfer to an mp3 player with album art support perhaps, like the vision M i have???

Also, media buttons on some keyboards are working, but not exactly as they should, for example the forward button moves one song forward but then you can't move back with the previous button. And it's not the keyboard, because these functions work perfectly with rhythmbox, but im looking to switch to exaile permanentley.

---

### Post by banjobacon on 2006-08-28
> **Canute said:**
> Uhm, how does playlists work? I tried to make a new one, added some files, but as soon as i exited Exaile and i tried to open it up again the playlist was just blank. I can't seem to find a save button either.
In the preferences, select "Open last playlist on startup".

---

### Post by !nkubus on 2006-08-29
The only missing feature that would be really nice is the Context Browser that Amarok(you can kill me if you want), But it would be really nice.

EDIT:

What I mean is the "Now Playing" with the html file in it that represent the contextual data of the current song.

---

### Post by grte on 2006-08-30
> **imaiden22 said:**
> Another question...the album art, if we get all the art for our albums, is there a way we can download the graphics for local copies on our machines, for transfer to an mp3 player with album art support perhaps, like the vision M i have???

You're album art is stored locally.  Check ~/.exaile/covers

---

### Post by hanzomon4 on 2006-09-01
I just realized that exaile is reading all of my music files, But its not reading the tag data of my m4a files and mp3s that I bought from emusic

---

### Post by maniacmusician on 2006-09-01
I really love this player so far. I think i might be replacing Listen with it. I dont know if this has been suggested for, but i didnt feel like browsing 44 pages of posts (Sheesh! this has gotten pretty popular!), so here I go:
The OSD is pretty cool, but i was wondering if you could add more info, like track time, maybe other things. I remember Listen's OSD was pretty good. 
Also, could there be an option for the OSD being displayed when you hover the mouse over the icon in the notification area? I really miss that. 

Thanks for all your hard work, and keep it up. this is a pretty nifty player. It has most of the features of Listen, but its less buggy and way faster. pretty good for just a "test" project as you said in your first post.

edit: also, it seems to sometimes not detect the album art i have in the tags of most of my songs. not a huge deal, but just thought i'd post it.

---

### Post by hanzomon4 on 2006-09-02
I like exaile, but I can't wait for listen to support playing audio cds

---

### Post by mrgnash on 2006-09-02
Would there be any chance of some kind of 'now listening' plugin that could interface with Gaim? i.e the way that Amarok/Kaffeine/Juk interface with Kopete.

---

### Post by UbuWu on 2006-09-02
It would be really nice to have this in the repositories :KS But universefreeze is coming closer (September 28th), so I hope someone can package this in time for edgy...

---

### Post by Draje on 2006-09-03
A great start though some things could be added to make it much better.
a) - Various Artist suppport. Make it so that if multiple artists are in one folder, it is automatically classified into a Various Artists section in the library, but make it so the user can add and remove freely from this section as he sees fit.
b) - Automatically scan the folders of music for the album art. I have my folders organized by album with the album art named art.jpg. Let the user define names which the art in the folder is called and automatically make it the album art.

---

### Post by synic on 2006-09-05
> **Draje said:**
> A great start though some things could be added to make it much better.
a) - Various Artist suppport. Make it so that if multiple artists are in one folder, it is automatically classified into a Various Artists section in the library, but make it so the user can add and remove freely from this section as he sees fit.
b) - Automatically scan the folders of music for the album art. I have my folders organized by album with the album art named art.jpg. Let the user define names which the art in the folder is called and automatically make it the album art.

Ah, exaile already has B, it just looks for a different (couple of) names.  I like the idea of allowing the user to specify the name.  I'll definitely get this into the next release.

On A, do you want a specific location on disk, or would it be better to have something that you can drag tracks into?

Adam

---

### Post by barmaley on 2006-09-09
Hello, people
Great player, thank you.
I deleted collection inside the player and this way I lost all of my music. Is it normal that player can delete files on hard disk? I don't tink so. Any way, thanks.

---

### Post by synic on 2006-09-09
> **barmaley said:**
> Hello, people
Great player, thank you.
I deleted collection inside the player and this way I lost all of my music. Is it normal that player can delete files on hard disk? I don't tink so. Any way, thanks.

There is a warning when you delete:

"Are you sure you want to permanently remove the selected tracks from _disk_?"

---

### Post by barmaley on 2006-09-09
No complains, synic, I just stupidly did not pay attention. But to my mind player shoud read the files and play them, but never erase. May be you will consider this in the future. Never the less, exile is good for me. Thanks.

---

### Post by Onyros on 2006-09-11
synic, congratulations on a great job with Exaile!, it's my favourite alternative to Amarok, even though it's still lacking one (at least for me), Amarok-killer-feature: equalization.

Is there any chance you'll consider including something to the likes of a parametric equalizer?

BTW, I also noticed there's a typo in the Bitrate column, you have KHz (KiloHertz) instead of kbps.

Keep it up, mate! It's looking good, whole lot of functionality (love the playlist tabs - that's what I believe is another of Exaile's! Amarok-killer-features) ;)

---

### Post by Marklinh89 on 2006-09-11
Me Love You Long Time!

---

### Post by Morbett on 2006-09-12
the new version of iTunes announced today eliminates the silence between songs that has plagued all mp3 programs.  albums don't "flow" when you get that short period of silence between songs.  are there any plans to do this kind of thing in Exaile?

---

### Post by maniacmusician on 2006-09-12
Adam,

Do you have a crossfade effect in exaile so that all the songs fade into each other? Because I just noticed all my songs doing that. I dont know if it's Exaile or if it's the songs that were made that way. If it's exaile, I'd appreciate that you provide an option for the user to control this.

thanks.

---

### Post by synic on 2006-09-12
> **Morbett said:**
> the new version of iTunes announced today eliminates the silence between songs that has plagued all mp3 programs.  albums don't "flow" when you get that short period of silence between songs.  are there any plans to do this kind of thing in Exaile?

This is gstreamer.  Gstreamer does not support gapless playback AFAIK.

---

### Post by Morbett on 2006-09-12
Thanks.  Do you know what supports gapless playback?

---

### Post by pheonix991 on 2006-09-24
This player plays FLAC!!!  THANX A TON!

---

### Post by ChaKy on 2006-09-29
I am getting this error while trying to start exaile, with the latest stable 0.2.4 and also with the latest svn:

```
chaky@ubuntu:~$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 2089, in ?
    main()
  File "/usr/bin/exaile", line 2081, in main
    exaile = ExaileWindow(fr)
  File "/usr/bin/exaile", line 79, in __init__
    self.database_connect()
  File "/usr/bin/exaile", line 793, in database_connect
    self.db = db.DBManager("%s%smusic.db" %
  File "/usr/share/exaile/xl/db.py", line 37, in __init__
    cur.execute("PRAGMA synchronize=OFF")
Warning: You can only execute one statement at a time.

```

---

### Post by Topfs on 2006-09-30
I have just installet Exaile and I must say at a first glance it seems to be quite the software! Good job! Combines the best elements of most audio 
players. I really like the Fetch Album Art thing. Also all those shoutcast radio stations out of the box really make me feel good about this app :)

One question though, How can I change themes to this?
Is it possible to even rearange the layout of the program, as in the windows program Foobar.


Thx

---

### Post by synic on 2006-09-30
> **Topfs said:**
> I have just installet Exaile and I must say at a first glance it seems to be quite the software! Good job! Combines the best elements of most audio 
players. I really like the Fetch Album Art thing. Also all those shoutcast radio stations out of the box really make me feel good about this app :)

One question though, How can I change themes to this?
Is it possible to even rearange the layout of the program, as in the windows program Foobar.


Thx

For now Exaile only follows your gtk theme.  You cannot rearrange the layout yet.

Adam

---

### Post by Topfs on 2006-09-30
Is Compiz themes GTK based? Not really important for now because I don't use compiz for the time being but I'm probably gonna use XGL sometime down the road, and it is always to know :)

New to linux and I really try to learn everything :)

Thx for the help btw.

---

### Post by foxy123 on 2006-09-30
I have already asked that but is it possible to make a pointer or something when dragging an album or song to the play list? Like in Quod Libet? Without it it is quit difficult sometimes to put the album or song in the right place. To illustrate it I am attaching a screenshot of QL with a red circle marking the line, which marks a place where the album is dragged.

---

### Post by synic on 2006-09-30
> **foxy123 said:**
> I have already asked that but is it possible to make a pointer or something when dragging an album or song to the play list? Like in Quod Libet? Without it it is quit difficult sometimes to put the album or song in the right place. To illustrate it I am attaching a screenshot of QL with a red circle marking the line, which marks a place where the album is dragged.

I'd love to have it, but haven't quite figured out how to implement it yet :(

---

### Post by foxy123 on 2006-09-30
> **synic said:**
> I'd love to have it, but haven't quite figured out how to implement it yet :(

thanks for the reply. Hopefully you will eventually find the way. Thanks for that brilliant application of yours anyway!

---

### Post by DOD1951 on 2006-10-01
Would really like to try this out. Does anyone have the latest install details please. The original post of instructions seems to have changed on wading through this thread.

Forget this. I sussed it out and now running.

---

### Post by Athropos on 2006-10-01
Just installed it and I really like it! :)
I was using Amarok and Exaile feels very light and fast compared to it...

---

### Post by Cronjob on 2006-10-01
I would love to know if this works for anyone on AMD64. It looks like a great project (I previously loved amaroK on KDE).

I had wanted to use Listen Music Player or RhythmBox, but neither will play MP3 files and I can't seem to figure it out (yes, I have the gstreamer libs installed, including -ugly, yes I have libxine installed, yes I have mpg123 installed).

I can play mp3 files with no problem in Totem 1.4.3, Mplayer, Beep (after I set it to use ALSA or ESD), VLC and XMMS -- so I'm not sure what's going on here.

Anyway, if anyone has luck with Exaile on AMD64, I'm all over that. Even if it's the i386 version. I'd install it myself, but I don't want to risk ending up unable to play mp3 files in ANYTHING at this point...

I would second the CLI interface, though -- if there isn't one. Great work!

---

### Post by redelephant on 2006-10-01
Okay, so I really love this app. But I'm having a problem with cover art. I can't seem to set custom images anywhere. Right clicking on the art doesn't bring up any menu or anything. I'm using the 0.2.4 deb from the website. Has anyone else experienced this? Some of my covers weren't downloaded and now I can't change them.

---

### Post by cborga1985 on 2006-10-02
here is a amd64 package i built with checkinstall
just extract it somewhere then do
```
sudo dpkg -i exaile_0.2.4-1_amd64.deb
```

---

### Post by synic on 2006-10-08
> **foxy123 said:**
> thanks for the reply. Hopefully you will eventually find the way. Thanks for that brilliant application of yours anyway!

Ok, I figured out how to implement it, and it's in SVN

---

### Post by foxy123 on 2006-10-08
> **synic said:**
> Ok, I figured out how to implement it, and it's in SVN

Oh, thanks a lot. It works very well. Now it is much easier to drop albums in a right place!

---

### Post by gosh on 2006-10-13
Great player!
I used Listen before but had trouble with Ipod on Edgy.
I have now replaced it with Exaile.

Thnx

---

### Post by raublekick on 2006-10-13
hmm i am gonna install this when i get home. all these media players keep getting me confused! this looks like an interface much closer to that of Amarok than Listen has.

---

### Post by raublekick on 2006-10-13
> **raublekick said:**
> hmm i am gonna install this when i get home. all these media players keep getting me confused! this looks like an interface much closer to that of Amarok than Listen has.

and... i really like this! not quite as feature packed as Listen, but it has the interface down almost perfect for me!

---

### Post by gosh on 2006-10-14
I registered at your forum to file a feature request, but I am not allowed to post there:-k

Ok, this is my request:
I would love to see how much space I already used and how much is free on my iPod.

---

### Post by bvc on 2006-10-16
I also tried to register but never received the confirmation email, even after clicking resend.

bug: entire time slider moves with the changing of the clock

looks great though! Thx for the gui/gtk attention!!!
[Onux-Blue](http://gnomethemes.org/pre/screenshots/Onux-Blue_Noir-Blue.png)
[Onux-Pink](http://gnomethemes.org/pre/screenshots/Onux-Pink_Noir-Pink.png)
[Onux-Red](http://gnomethemes.org/pre/screenshots/Onux-Red.png)
[Onux-Purple](http://gnomethemes.org/pre/screenshots/Onux-Purple_Noir-Purple.png)
[Onux-Green](http://gnomethemes.org/pre/screenshots/Onux-Green.png)
[Onux-Orange](http://gnomethemes.org/pre/screenshots/Onux-Orange_Noir-Orange.png)
[Onux](http://gnomethemes.org/pre/screenshots/Onux.png)

---

### Post by Athropos on 2006-10-17
> **bvc said:**
> 
bug: entire time slider moves with the changing of the clock


I believe this is due to GStreamer. I have the same problem with Amarok...

---

### Post by gosh on 2006-10-17
> **gosh said:**
> I registered at your forum to file a feature request, but I am not allowed to post there:-k


Of course, I just had to wait for the confirmation mail...:redface:

---

### Post by bvc on 2006-10-17
> **Athropos said:**
> I believe this is due to GStreamer. I have the same problem with Amarok...gstreamer deals with gtk? weird

> **gosh said:**
> Of course, I just had to wait for the confirmation mail...:redface:how long did that take? It has been a few days, and I haven't received one.

---

### Post by gosh on 2006-10-18
That took just 15 - 30 minutes

---

### Post by cborga1985 on 2006-10-18
Latest Exaile svn as of 10/18/2006 for 64 here [http://www.ubuntuforums.org/attachment.php?attachmentid=17770&stc=1&d=1161172555]("http://www.ubuntuforums.org/attachment.php?attachmentid=17770&stc=1&d=1161172555")
unzip it and install it with
```
sudo dpkg -i exaile_20061018-1_amd64.deb
```

---

### Post by easy_target on 2006-10-18
Does anyone know if this awesome software is gonna make it to the repos? I find it so much better than rythmbox...

---

### Post by Marquis_de_Carabas on 2006-10-20
Excellent! I used Listen for a while but had several little annoyances so I went back to XMMS (of course XMMS rocks, but I want something pretty to show my non-Linux using flatmates...). I was considering Amarok but didn't want to clutter my hard drive up with KDE-stuff. But now there's this, which so far seems to do everything I want in the way that I want it. Thank you! :D

---

### Post by raublekick on 2006-10-20
biggest problem i have with exaile right now (which Listen handles much better but not perfectly) is that it is a pain in the behind to add files to the play list. drag and drop please :)

---

### Post by synic on 2006-10-20
> **raublekick said:**
> biggest problem i have with exaile right now (which Listen handles much better but not perfectly) is that it is a pain in the behind to add files to the play list. drag and drop please :)

Try this deb... the svn handles drag and drop a bit better.

[http://exaile.org/files/exaile_svn20061018_i386.deb](http://exaile.org/files/exaile_svn20061018_i386.deb)

---

### Post by foxy123 on 2006-10-20
> **synic said:**
> Try this deb... the svn handles drag and drop a bit better.

[http://exaile.org/files/exaile_svn20061018_i386.deb](http://exaile.org/files/exaile_svn20061018_i386.deb)
i tried this deb, but have got unsatisfied dependency: libatk1.0-0. though i've got it installed: 
```
~$ sudo apt-cache show libatk1.0-0
Package: libatk1.0-0
Priority: optional
Section: libs
Installed-Size: 188
Maintainer: Akira TAGOH <tagoh@debian.org>
Architecture: i386
Source: atk1.0
Version: 1.11.4-0ubuntu1
Depends: libc6 (>= 2.3.4-1), libglib2.0-0 (>= 2.9.3)
Recommends: libatk1.0-data
Filename: pool/main/a/atk1.0/libatk1.0-0_1.11.4-0ubuntu1_i386.deb
Size: 71138
MD5sum: daabcca7cd9fa5bb9379315da73efe65
Description: The ATK accessibility toolkit
 ATK is a toolkit providing accessibility interfaces for applications or
 other toolkits. By implementing these interfaces, those other toolkits or
 applications can be used with tools such as screen readers, magnifiers, and
 other alternative input devices.
 .
 This is the runtime part of ATK, needed to run applications built with it.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop, xubuntu-desktop

```

---

### Post by raublekick on 2006-10-20
> **synic said:**
> Try this deb... the svn handles drag and drop a bit better.

[http://exaile.org/files/exaile_svn20061018_i386.deb](http://exaile.org/files/exaile_svn20061018_i386.deb)

thanks i'll give 'er a shot when i get home!

---

### Post by cborga1985 on 2006-10-20
as posted above the amd64 one is [here]("http://www.ubuntuforums.org/showpost.php?p=1631435&postcount=473")

---

### Post by hanzomon4 on 2006-10-20
I would love for exaile to support smart playlist and the ability to get album art from google, both are listen features that I kinda like. 

O! and a lastfm radio player functionality

---

### Post by topyli on 2006-10-21
> **foxy123 said:**
> i tried this deb, but have got unsatisfied dependency: libatk1.0-0. though i've got it installed: 

I had the same problem so I built my own package from the tarball. Try it if you like: [Link]("http://www.esnips.com/doc/f111b999-e16e-4482-85be-b75f7400c198/exaile_0.2.4-1_i386.deb")

---

### Post by VCSkier on 2006-10-23
This might seem like a silly question, but how does Exaile's ipod support compare to Amarok's?  A friend of mine is considering trying linux for the first time, and he needs an easy, and as full-featured ipod compatible media player as possible (he is currently very fond of iTunes).  Is there anything ipod related that Exaile and Amarok do differently?

---

### Post by synic on 2006-10-23
> **VCSkier said:**
> This might seem like a silly question, but how does Exaile's ipod support compare to Amarok's?  A friend of mine is considering trying linux for the first time, and he needs an easy, and as full-featured ipod compatible media player as possible (he is currently very fond of iTunes).  Is there anything ipod related that Exaile and Amarok do differently?

Well, I can't really say.  I haven't used Amarok's ipod manager, nor have I used iTunes extensively.  

Here's what Exaile can do:

You can create and manage iPod playlists
You can transfer tracks to your iPod.  If Exaile has downloaded an album cover for the track, it will be transferred as well.
You can remove tracks from your iPod
You can edit metadata for tracks on your iPod

Here's what it can't do (yet):

There is no sync function. I don't know if there will be...  I've never used this function on iTunes and I have no idea what it does exactly.

Adam

---

### Post by huntermix on 2006-10-27
i could not install it, i get this error:
```
hunter@hunter-laptop:~$ sudo dpkg -i exaile_0.2b4_i386.deb 
(Reading database ... 104378 files and directories currently installed.)
Unpacking exaile (from exaile_0.2b4_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing exaile_0.2b4_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/exaile/images/exailelogo.png')
Errors were encountered while processing:
 exaile_0.2b4_i386.deb
hunter@hunter-laptop:~$ 

```

---

### Post by MedivhX on 2006-10-27
This player looks nice but too AmaroKish... It's almos a copy... I'll try it...

---

### Post by synic on 2006-10-27
> **huntermix said:**
> i could not install it, i get this error:
```
hunter@hunter-laptop:~$ sudo dpkg -i exaile_0.2b4_i386.deb 
(Reading database ... 104378 files and directories currently installed.)
Unpacking exaile (from exaile_0.2b4_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing exaile_0.2b4_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/exaile/images/exailelogo.png')
Errors were encountered while processing:
 exaile_0.2b4_i386.deb
hunter@hunter-laptop:~$ 

```



That's a really old version.  Try 0.2.4 or svn.

Adam

---

### Post by synic on 2006-10-27
> **MedivhX said:**
> This player looks nice but too AmaroKish... It's almos a copy... I'll try it...

That's the goal :)

---

### Post by fog on 2006-10-27
I like this player very much, so [here]("http://www.techteam.gr/index.php?s=&showtopic=29913&view=findpost&p=325357") is a howto in my language :)

---

### Post by huntermix on 2006-10-27
> **synic said:**
> That's a really old version.  Try 0.2.4 or svn.

Adam

thanks adam, its working now... nice work, works much faster than amarok

edit: just noticed a little bug, in the about window when i press close nothing happens, but if i click on the "X" then it does close... just a minor glitch:) excellent app!

---

### Post by raintheory on 2006-10-27
Enjoying this so far.  version 0.2.4

I second the Last.fm radio functionality!  That would be great!

I also noticed the about window bug, but hardly an issue since it closes fine with the x.

Great job!  I'm looking forward to watching the progress of this!

---

### Post by cborga1985 on 2006-11-03
**Exaile 0.2.5b for Dapper(Amd64)**

Download package from [here]("http://ubuntuforums.org/attachment.php?attachmentid=18797&stc=1&d=1162572000"). Of course then unpack the archive using file-roller or similiar.

**then** in a terminal

```
sudo dpkg -i exaile_0.2.5b_amd64.deb
```

---

### Post by d3v1ant_0n3 on 2006-11-03
Giving it a try now- Just switched back to Gnome, and Amarok is being a bit sketchy for me:( 

Seems good so far:D

---

### Post by foxy123 on 2006-11-03
Will 0.2.5b be available for Dapper?

---

### Post by NyquistLimit on 2006-11-03
hmm, the opening of m3u files doesn't work. It only loads the first track into the playlist. I've reported a bug on the exaile forums.

---

### Post by cborga1985 on 2006-11-03
> **NyquistLimit said:**
> hmm, the opening of m3u files doesn't work. It only loads the first track into the playlist. I've reported a bug on the exaile forums.
yeah the cvs did that. forgot to report though

---

### Post by cborga1985 on 2006-11-03
[SIZE="5"][COLOR="Magenta"]**Howto: Building exaile from source.**[/COLOR][/SIZE]
[SIZE="3"][COLOR="DarkGreen"]***Update: All Dependencies should be fixed now.***[/COLOR][/SIZE]
**First**
ALT+F2 **gnome-terminal**, click run then
```
wget http://exaile.org/files/exaile_0.2.6.tar.gz
```

**Second**
```
tar xvfz exaile_0.2.6.tar.gz
```

**Third**
```
sudo apt-get install build-essential dpkg-dev debhelper libgstreamer0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly python-gst0.10 gstreamer0.10-esd gstreamer0.10-alsa python2.4 python2.4-dev python2.4-gtk2 python-gtk2-dev python-glade2 python2.4-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree python2.4-gnome2-extras python-cddb streamripper

```

**Forth**
```
cd exaile*
```

**Fifth**
```
make
```

**Sixth**
```
sudo dpkg-buildpackage
```
wait for it to build

**Seventh**
```
cd ..
```

**Eighth**
```
sudo dpkg -i exaile*.deb
```

If it does not work when you go to run it. Do this but I didn't seperate everything. Just follow line by line.
```

wget http://www.sacredchao.net/~piman/software/mutagen-1.8.tar.gz
tar xvfz mutagen-1.8.tar.gz
cd mutagen*
./setup.py build
sudo "./setup.py install"
```

---

### Post by ChaKy on 2006-11-04
Has anyone considered in making an XChat plugin for Exaile, so that you can control Exaile from XChat and also announce what's playing on the current IRC channel?

---

### Post by foxy123 on 2006-11-04
> **cborga1985 said:**
> the package for edgy will probably work

**First**
ALT+F2 type **gnome-terminal** and click run

**Second**
```
wget http://exaile.org/files/exaile_0.2.5b_i386.deb
```
**Third**
```
sudo dpkg -i http://exaile.org/files/exaile_0.2.5b_i386.deb
```

[SIZE="5"]if the above does not work do this with the **gnome-terminal** open[/SIZE]

**First**
```
wget http://exaile.org/files/exaile_0.2.5b.tar.gz
```

**Second**
```
sudo apt-get install build-essential python python-dev python-gtk2 python-gtk2-dev python-gpod python2.4-dbus gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly dpkg-dev

```

**Third**
```
cd exaile*
```

**Forth**
```
make
```

**Fifth**
```
sudo dpkg-buildpackage
```
wait for it to build

**Sixth**
```
cd ..
```

**Seventh**
```
sudo dpkg -i exaile*.deb
```

That was a mouthful :)
Hey, thanks a lot. Edgy package did not work, but making a deb with dpkg-buildpackage was easy. You missed one step though.

```
tar xvfz exaile_0.2.5b.tar.gz
```

It may be a good idea to add this small how-to to the first page or did a separate post on howtos forum.

---

### Post by .t. on 2006-11-04
why don't you just set up a repo? its really easy; reprepro isn't exactly hard.

i'd do it, but my upstream's really slow (61KiB/s)

---

### Post by synic on 2006-11-04
> **ChaKy said:**
> Has anyone considered in making an XChat plugin for Exaile, so that you can control Exaile from XChat and also announce what's playing on the current IRC channel?

Already done!  There's an xchat plugin here: [http://www.exaile.org/files/exaile_xchat.pl](http://www.exaile.org/files/exaile_xchat.pl), and one for irssi here: [http://www.exaile.org/files/exaile_irssi.pl](http://www.exaile.org/files/exaile_irssi.pl) - both you just load and type /exaile when you want to display the song you're playing.

Adam

---

### Post by raublekick on 2006-11-04
ah excellent! loving the  new edgy version!

---

### Post by ChaKy on 2006-11-04
> **synic said:**
> Already done!  There's an xchat plugin here: [http://www.exaile.org/files/exaile_xchat.pl](http://www.exaile.org/files/exaile_xchat.pl), and one for irssi here: [http://www.exaile.org/files/exaile_irssi.pl](http://www.exaile.org/files/exaile_irssi.pl) - both you just load and type /exaile when you want to display the song you're playing.

Thank you, very much.

---

### Post by mrgnash on 2006-11-07
No dice on the latest Edgy package:

```
(exaile:5385): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/exaile", line 46, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

I checked to make sure all the dependencies are installed; which they are.

---

### Post by cborga1985 on 2006-11-07
> **mrgnash said:**
> No dice on the latest Edgy package:

```
(exaile:5385): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/exaile", line 46, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

I checked to make sure all the dependencies are installed; which they are.

you need to be more specific like telling us what platform you using for starters.

---

### Post by cborga1985 on 2006-11-07
on the last page a how to on buiding exaile from source
[http://ubuntuforums.org/showpost.php?p=1711544&postcount=497](http://ubuntuforums.org/showpost.php?p=1711544&postcount=497)

---

### Post by mrgnash on 2006-11-07
> **cborga1985 said:**
> you need to be more specific like telling us what platform you using for starters.

Ubuntu Edgy x86 on an Acer Travelmate (AMD Turion 64 ML-30) 4402.

---

### Post by synic on 2006-11-07
> **mrgnash said:**
> Ubuntu Edgy x86 on an Acer Travelmate (AMD Turion 64 ML-30) 4402.

What is your LANG variable set to?

---

### Post by mrgnash on 2006-11-07
Output of ```
$locale
```:

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_AU
LANGUAGE=en_AU:
LC_CTYPE="en_AU"
LC_NUMERIC="en_AU"
LC_TIME="en_AU"
LC_COLLATE="en_AU"
LC_MONETARY="en_AU"
LC_MESSAGES="en_AU"
LC_PAPER="en_AU"
LC_NAME="en_AU"
LC_ADDRESS="en_AU"
LC_TELEPHONE="en_AU"
LC_MEASUREMENT="en_AU"
LC_IDENTIFICATION="en_AU"
LC_ALL=

```

---

### Post by ChaKy on 2006-11-10
> **synic said:**
> Already done!  There's an xchat plugin here: [http://www.exaile.org/files/exaile_xchat.pl](http://www.exaile.org/files/exaile_xchat.pl), and one for irssi here: [http://www.exaile.org/files/exaile_irssi.pl](http://www.exaile.org/files/exaile_irssi.pl) - both you just load and type /exaile when you want to display the song you're playing.

Adam

Hi Adam, I would like to report that both scripts show the wrong time if the mp3 is longer then 60 min. If that can be fixed, that would be nice. Thank you.

---

### Post by jkwarras on 2006-11-10
Thanks for this great application: I love it. I love the dynamic playlist feature, it's great :)

Somehow I have a problem with album art: I have my covers as nameofthealbum-front.jpg in the album folder, so in the preferences for album art I put *front.jpg but it doesn't find anything. Is this normal? Maybe I'm doing something wrong.

I just have some feature suggestions:

- Replaygain support
- Read APE tags from mpc files
- Advanced tagging like in quodlibet (ex-falso)
- Multiple artist handling (album_artist field)
- Album mode like quodlibet (with cover at the left)
- Dynamic playlist: Include the possibility to include songs outside of my collection (using last.fm suggestions) I'm thinking sort of including last-exit player features into exaile.
- Possibility of saving searches as smart playlists.

If some of this is already possible, I'll appretiate if someone could point me in the right direction.

Thanks.

---

### Post by roadboy on 2006-11-29
it's great but i wish there was equalizer support [-(  that's why i prefer beep-media-player :-|

---

### Post by -Phi- on 2006-12-01
I'm running Exaile 0.2.6 on Xubuntu 6.10 and for some reason the tray icon doesn't show up. I remember it showing up with older versions of Exaile on older versions of Xubuntu so I don't know where the error lies. I have the option checked in the preferences but it changes nothing. I ran out of things to try. Any suggestions?

[Screenshot]("http://phispace.net/lj/Exaile.jpg")

- Phi

---

### Post by thegestetner on 2006-12-04
OK, first of all, you've done a great job - congrats. 
However, I have one big problem.
Quite a sizable chunk of my files are encoded in VBR AAC (not DRMed or anything like that, and they still end in *.m4a). They show up in the library (in 0.26, the most recent), but with filename only and no tags; their times all display as "-1:59" and when clicked on, they show up as playing, but refuse to actually play. 

Opening Exaile in the terminal doesn't give any clues. Nothing out of the ordinary comes up.

---

### Post by synic on 2006-12-05
> **thegestetner said:**
> OK, first of all, you've done a great job - congrats. 
However, I have one big problem.
Quite a sizable chunk of my files are encoded in VBR AAC (not DRMed or anything like that, and they still end in *.m4a). They show up in the library (in 0.26, the most recent), but with filename only and no tags; their times all display as "-1:59" and when clicked on, they show up as playing, but refuse to actually play. 

Opening Exaile in the terminal doesn't give any clues. Nothing out of the ordinary comes up.

You might try the SVN version for the tags.  As far as playback, do you have the gstreamer0.10-ffmpeg package installed?

---

### Post by thegestetner on 2006-12-06
Sorry, I forgot to mention that these files play without problems in Rhythmbox, Totem, etc. And I do have gstreamer ffmpeg support. I'll give SVN a shot.

---

### Post by Ocxic on 2006-12-06
the only thin i don't like, and if I'm wrong please correct me, is that  you can't get a list of all you music files you have to go by the artist, that's thats only thing i don't like.

edit: never mind I just figured it out, sooryy great prgram tho, gonna replace rythmbox for me i think.

---

### Post by cborga1985 on 2006-12-07
> **synic said:**
> You might try the SVN version for the tags.  As far as playback, do you have the gstreamer0.10-ffmpeg package installed?
I'm trying to test out the lastest svn. I compiled and install a package then when I go to launch exaile I get this.

```

boston@boston:~/Desktop/exaile$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 2284, in ?
    main()
  File "/usr/bin/exaile", line 2274, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/bin/exaile", line 96, in __init__
    self.database_connect()
  File "/usr/bin/exaile", line 861, in database_connect
    self.db.check_version("sql")
  File "/usr/share/exaile/xl/db.py", line 133, in check_version
    row = self.read_one("db_version", "version", "1=1", tuple())
  File "/usr/share/exaile/xl/db.py", line 264, in read_one
    cur.execute(query, args)
OperationalError: no such table: db_version

```

---

### Post by synic on 2006-12-08
> **cborga1985 said:**
> I'm trying to test out the lastest svn. I compiled and install a package then when I go to launch exaile I get this.

```

boston@boston:~/Desktop/exaile$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 2284, in ?
    main()
  File "/usr/bin/exaile", line 2274, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/bin/exaile", line 96, in __init__
    self.database_connect()
  File "/usr/bin/exaile", line 861, in database_connect
    self.db.check_version("sql")
  File "/usr/share/exaile/xl/db.py", line 133, in check_version
    row = self.read_one("db_version", "version", "1=1", tuple())
  File "/usr/share/exaile/xl/db.py", line 264, in read_one
    cur.execute(query, args)
OperationalError: no such table: db_version

```

You'll have to wipe out your database and rescan.  The schema has changed a lot... there will be a converter, but not until I think the schema won't change anymore.

---

### Post by cacharreo on 2006-12-09
It's great. I was looking for an amarok for gnome. I'm going to test it strongly. For the moment works fine. I have just imported my music colection
(about 200Gb ogg and m3 mucic files):D

---

### Post by trincamckee on 2006-12-09
> I'm running Exaile 0.2.6 on Xubuntu 6.10 and for some reason the tray icon doesn't show up. I remember it showing up with older versions of Exaile on older versions of Xubuntu so I don't know where the error lies. I have the option checked in the preferences but it changes nothing. I ran out of things to try. Any suggestions?
I do have the same problem as - Phi, i belive some icon is missing, when i run exail from terminal it gives me this:

> 
oscar@BlackMesa:~$ exaile
Sorry, egg.trayicon is NOT available
Streamripper not found
mmkeys are available.
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/oscar/.exaile/saved/playlist0000.m3u
Importing /home/oscar/.exaile/saved/playlist0001.m3u
Importing /home/oscar/.exaile/saved/playlist0002.m3u
Importing /home/oscar/.exaile/saved/playlist0003.m3u


Can someone upload this icon and tell us where to put, please?
Thank you.

---

### Post by trincamckee on 2006-12-09
i solved this problem by installing **python-gnome2-extra** package.
Take care.

---

### Post by synic on 2006-12-09
> **trincamckee said:**
> I do have the same problem as - Phi, i belive some icon is missing, when i run exail from terminal it gives me this:



Can someone upload this icon and tell us where to put, please?
Thank you.

You need python-gnome2-extras

---

### Post by cborga1985 on 2006-12-09
> **synic said:**
> You'll have to wipe out your database and rescan.  The schema has changed a lot... there will be a converter, but not until I think the schema won't change anymore.
that did the trick. thanks, looks nice so far

---

### Post by matchboxfiend on 2006-12-10
I figured this would be a good place to ask this question:

I am running the latest version of Exaile (couldn't see myself using anything else, the program is great!) and everything works wonders except for the organization and metawriting of .wma objects.  I have a ton of WMAs that came with me when I migrated from Windows and while Exaile will play them just fine, they seem to be completely out of order in the Library list and the metadata isn't writing like the other songs are.  Does that make any sense?

UPDATE:  Nevermind, WMA's are evil and I converted them all to .mp3.  I'll see how that works.  

One more question though:  How do you wipe out the database and rescan?  I am getting the same dbus error when trying to run version0.2.7b and the solution you gave made no sense to me.  Thanks!

---

### Post by cborga1985 on 2006-12-11
> **matchboxfiend said:**
> I figured this would be a good place to ask this question:

I am running the latest version of Exaile (couldn't see myself using anything else, the program is great!) and everything works wonders except for the organization and metawriting of .wma objects.  I have a ton of WMAs that came with me when I migrated from Windows and while Exaile will play them just fine, they seem to be completely out of order in the Library list and the metadata isn't writing like the other songs are.  Does that make any sense?

UPDATE:  Nevermind, WMA's are evil and I converted them all to .mp3.  I'll see how that works.  

One more question though:  How do you wipe out the database and rescan?  I am getting the same dbus error when trying to run version0.2.7b and the solution you gave made no sense to me.  Thanks!

If you want to do this in the terminal, this should work. :D 
```

cd ~
rm --recursive .exaile
```

In Nautilus go to your home folder and remove the folder .exaile in Nautilus. You will have to go to view and click show hidden files to do this.

---

### Post by cborga1985 on 2006-12-11
For anybody who wants. I just built the lastest svn for a friend at his house. Just download it from [here]("http://www.megaupload.com/?d=DZVVUDZL") and use this to install.
```
sudo dpkg -i exaile_0.2.7b_i386.deb
```
It was built on Kubuntu Dapper but should work fine on Ubuntu Dapper. If you have problems running it, try installing the latest python-mutagen from [here]("http://www.megaupload.com/?d=2CA2TJFP").

**[SIZE="3"][COLOR="Magenta"]Special Note: Make sure you delete your current .exaile folder that is located in your home directory before you install this. Also, if you are looking for a AMD64 build just refer to my site in my sig. Remember that this is not finished so it might have a few bugs.[/COLOR][/SIZE]**

---

### Post by foxy123 on 2006-12-16
I am not sure if anyone has already requested this. I like in Quod Libet Album List view you can see all your album covers. Sometimes I pick up an album to listen by its cover. I wonder if such option could be added into exaile?

---

### Post by MetalMusicAddict on 2006-12-16
> **foxy123 said:**
> I am not sure if anyone has already requested this. I like in Quod Libet Album List view you can see all your album covers. Sometimes I pick up an album to listen by its cover. I wonder if such option could be added into exaile?

I COMPLETLY 2nd this. That would be awesome.

---

### Post by foxy123 on 2006-12-17
I am trying to customise OSD but do not know how to display a total number of tracks in a album. So far I managed the following:
```
{track}/
```

What should I put after /? Also is it possible to get dynamic progress of the song like 3:56/5:01 (meaning that 3:56 minutes of the song of 5:01 total has already played)? The guide on [www.exaile.org/markup.html](www.exaile.org/markup.html) is a bit too complicated for me :)

---

### Post by merlyn on 2006-12-26
Greetings all,

I've been wondering why on earth, with all the traffic this thread has generated, it hasn't been granted 3rd party project status.

While I'm at it, I've only been using Exaile for two days, and love it. Although it does odd things with two disk albums, fix for this is due in the next release however.

Last night 'local time', I discovered just how easy it is to set up stream ripping on this baby, it's great.

Thanks synic for the groovy player.

Cheers.

---

### Post by synic on 2006-12-26
> **merlyn said:**
> Greetings all,
I've been wondering why on earth, with all the traffic this thread has generated, it hasn't been granted 3rd party project status.
Cheers.

I was actually approached by a forum admin about this early in this thread's life, but I never heard anything back from my reply.   I got the message April 14th, and this is what it said:

[quote=ubuntu-geek]
Hey,

If you wish we can setup a forum for your project in our 3rd party section. It looks pretty cool and I think alot of people will find it usefull..

- Ryan
[/quote]

I replied, but heard nothing back.

Adam

---

### Post by Somenoob on 2006-12-26
It definitely deserves a sub-forum in the 3rd party section.

---

### Post by ComplexNumber on 2006-12-26
i now think that exaile is the best all-round general purpose music application for gnome. i've been having some trials of listen, exaile, rhythmbox, banshee, and quod libet, but i came to the following conclusions:
a) listen is far too buggy. it crashed repeatedly whilst trying to access wikipedia, amongst other things.
b) quod libet is less functional than exaile.
c) rhythmbox, whilst good, is lacking
d) banshee? ditto.

---

### Post by paridoth on 2006-12-27
loving this app! good alternative to amarok and all its kdeness.
 just needs a repo!

---

### Post by ~LoKe on 2006-12-27
I was using this before I switched to MPD.  Solid app and easy transition from Rhythmbox.  Well done!

---

### Post by Artemis3 on 2006-12-27
Does it support ReplayGain values written in Apev2 tags? This is the #1 feature i'm looking for in any audio player. Even better if you can also calculate RG for new files.

---

### Post by merlyn on 2006-12-27
> **synic said:**
> I was actually approached by a forum admin about this early in this thread's life, but I never heard anything back from my reply.   I got the message April 14th. . . .

. . . .I replied, but heard nothing back.

Bugger, never mind, I don't think that a project as good as this can continue to go unoticed.

Keep up the excellent work.

Cheers.

---

### Post by plb on 2006-12-27
This app is now in debian unstable btw :)

---

### Post by lyceum on 2006-12-27
> **synic said:**
> Yeah... I'm not an artist.  I basically just took icons from other apps.  

SO... if you are an artist, and want to help, let me know :)

I am an artist. If you want a logo, let me know. I have some mouse pointers to finish up first, but I will have a bit of free time next week. 

Also, I have not checked it out yet, but plan to. Can it rip CDs? I hate having sound juicer & something else on my machine. I'd rather have an all in one, you know?

---

### Post by cborga1985 on 2006-12-30
Ubuntu Dapper Packages for both AMD64 and I386 [**[COLOR="RoyalBlue"]here[/COLOR]**](http://www.exaile.org/trac/discussion/2/2).

---

### Post by Falcorian on 2007-01-01
Nice player! I keep coming back to it, liking it, and going back to Amarok.

However, at the rate it's advancing, I'm sure I'll be sticking with it soon! :) Keep up the good work!

---

### Post by ice60 on 2007-01-01
hi, is it possible to see how many people are listening to a shoutcast stream like with streamtuner? i only listen to the most listened to streams on shoutcast because the others are generally rubbish!

---

### Post by milkaa on 2007-01-02
> **cborga1985 said:**
> Ubuntu Dapper Packages for both AMD64 and I386 [**[COLOR="RoyalBlue"]here[/COLOR]**](http://www.exaile.org/trac/discussion/2/2).

Hi I installed Exaile using the above package for Dapper. It installed fine but I could not launch it. Please help. Thanks!

---

### Post by foxy123 on 2007-01-03
> **milkaa said:**
> Hi I installed Exaile using the above package for Dapper. It installed fine but I could not launch it. Please help. Thanks!
if you have already had Exaile installed before you have to remove .exaile directory to make a new version work.

---

### Post by jkroto on 2007-01-03
> **cborga1985 said:**
> Ubuntu Dapper Packages for both AMD64 and I386 [**[COLOR="RoyalBlue"]here[/COLOR]**](http://www.exaile.org/trac/discussion/2/2).

cborga1985
Thanks for the package.
Just so you know, I'm running Edgy 64-bit and your Exaile package works great so far.

Synic,
Thank you for this awesome app.  I have tried all the others, and for some reason couldn't get one thing or another to work.  Exaile works great, transfers music to my i-pod, gets and plays my library quickly, right out of the box.  Tried Exaile before and had some issues, but I came back out of frustration and I'm glad I did, what great improvements in just a few months!!
Since I just started playing with Exaile again I don't know if this feature is available, but a right click (send to) from the collection to the i-pod would be nice.  Also, can Exaile be minimized to the tray icon (Edit: just realized that close does this, great program!!)? And can mimi mode be moved?
Thanks again.

---

### Post by cborga1985 on 2007-01-03
> **cborga1985 said:**
> Ubuntu Dapper Packages for both AMD64 and I386 [**[COLOR="RoyalBlue"]here[/COLOR]**](http://www.exaile.org/trac/discussion/2/2).

seems that exaile forums is down so now you might have to get it directly from me. just use the link in my sig.
> **jkroto said:**
> cborga1985
Thanks for the package.
Just so you know, I'm running Edgy 64-bit and your Exaile package works great so far.

Synic,
Thank you for this awesome app.  I have tried all the others, and for some reason couldn't get one thing or another to work.  Exaile works great, transfers music to my i-pod, gets and plays my library quickly, right out of the box.  Tried Exaile before and had some issues, but I came back out of frustration and I'm glad I did, what great improvements in just a few months!!
Since I just started playing with Exaile again I don't know if this feature is available, but a right click (send to) from the collection to the i-pod would be nice.  Also, can Exaile be minimized to the tray icon (Edit: just realized that close does this, great program!!)? And can mimi mode be moved?
Thanks again.

glad to see it worked for you :-)

---

### Post by Cheizzz on 2007-01-03
First i want to give a  great WOOHOO! for this great music player!

I think I've tried them all: Amarok, Banshee, Rhythmbox, Listen, Quod Libet, but none of them had the good vibe that Exaile has.

But, I would like to see some more features added, because I find it still a bit lacking.
My wishlist (in no particular order):

-"partymode" (like Listen and Rhythmbox)
-DAAP support
-Artist suggestions from Last.fm
-Album covers in the "album-list"
-Burning CD's from Exaile

---

### Post by rolando2424 on 2007-01-03
Hum... Strange, I don't seem to have any sound in it...

---

### Post by klato on 2007-01-04
Looks cool.  Altough the thing always locks up when I'm importing my library (using latest 0.2.7)

---

### Post by 3rdalbum on 2007-01-04
> **cborga1985 said:**
> seems that exaile forums is down so now you might have to get it directly from me. just use the link in my sig.


glad to see it worked for you :-)

I actually couldn't get the Dapper package working; Python couldn't find the mutagen.oggvorbis module. I had the same trouble when I tried going from source.

Solution?

```
sudo nano /usr/share/exaile/xl/media.py
Control-W
"oggvorbis"

```
Comment all the "oggvorbis" stuff out. In the Try/Except blocks with "oggvorbis", make sure you put "pass" as the only statement in it. If Python raises SyntaxErrors, check that you haven't left a spare comma at the end of the import statement.

Alternatively, you could replace your media.py file with the one I'm attaching.

If the developer is looking at this thread, maybe he could see what I've done and look into reducing the dependency on "oggvorbis" for Dapper users?

---

### Post by rolando2424 on 2007-01-04
> **rolando2424 said:**
> Hum... Strange, I don't seem to have any sound in it...

Still no sound at all...

My console give me this error:

```
** Message: don't know how to handle video/x-ms-asf

```

```
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3

```

Whoever, all songs work in XMMS, and it does not contain any video (it's strange the video error):-k

---

### Post by xfile087 on 2007-01-04
> **rolando2424 said:**
> Hum... Strange, I don't seem to have any sound in it...

Exactly the same problem here! Apart from that - it looks awesome!!! Just what i've been looking for.

I've just built from source - it ran successfully but I still have no sound...

When I run from the terminal it opens and the terminal says "You have entered an invalid option".

I've just installed via Automatix2 (WITHOUT installing the audio codecs) and the audio works now... I don't know why the others did not...

---

### Post by jasidog on 2007-01-07
> **ShanghaiTeej said:**
> Love the player...

I was just wondering when podcast support might be available.  Otherwise, I'm enjoying the work!  Much Thanks.

Any plans for this in Exaile? I think it would make it a more complete solution for me at least. Perhaps it's not much requested or difficult to do though. :)

---

### Post by geokok1981 on 2007-01-08
Just wanted to say that I believe exaile is the best media player for gnome I 've seen so far....!!!

---

### Post by hanzomon4 on 2007-01-08
Exaile can play podcast......

---

### Post by richieboy on 2007-01-09
i LOVE this player!  thanks synic!!!  but shoutcast has a small problem.  in streamtuner you can click the Alternative channel and load stations as well as OPENING the alternative channel and getting stations for college, punk, hardcore, etc.  in exaile you can't load streams for the channels, only for the subfolders.  check streamtuner if this doesn't make sense.  loading the folders produces different stations than loading the sub folders.  please let me know if this makes sense.  i am very tired right now.
thanks,
rich

---

### Post by jkroto on 2007-01-09
> **hanzomon4 said:**
> Exaile can play podcast......

hanzomon4,
What program do you use (prefer) to get the podcasts?   Does that include video and audio?
Thanks for any info.

---

### Post by ajeetraj on 2007-01-10
there is no way you can find the lyric in the same window as amarok? if someone got it working plz let me know :)

it does look good to me :)

---

### Post by manutdfan2850 on 2007-01-11
> **synic said:**
> I released Exaile 0.2b2 today.  I really like Amarok, but I was hoping for a gtk+ alternative, so I started Exaile.  I know ... I know, there are tons of media players out there, but I see this as a fun way to learn python and gtk+.

Some screenshots can be found here:

[http://www.exaile.org](http://www.exaile.org)

It's beta, but if you're bored, check it out.  Here's what you'll need to do:

```

# sudo apt-get install python-gtk2 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
# wget http://www.exaile.org/files/exaile_0.2b4_i386.deb
# sudo dpkg -i exaile_0.2b4_i386.deb

```

.. and a new icon will show up in Applications->Sound and Video

Go to Tools->Library Manager, add your music directory, and away you go.

Optional:  If you want mp3 support, install gstreamer0.10-plugins-ugly, and if you want wma, install gstreamer0.10-ffmpeg

Feedback and comments are appreciated!

-synic




right now i have Exaile 0.2b4

is this the the latest version?  i would like the latest (stable) version. 

plz let me know,

Thanks

thanks

---

### Post by synic on 2007-01-11
> **manutdfan2850 said:**
> right now i have Exaile 0.2b4

is this the the latest version?  i would like the latest (stable) version. 

plz let me know,

Thanks

thanks

The latest is 0.2.8

---

### Post by manutdfan2850 on 2007-01-11
ok i dont know what is wrong... i installed using the deb i downloaded from the exaile website. 

and when i click the Exaile! icon in Sound/Video nothing happens. i dont know whats wrong. any ideas?

this is what i donwloaded. : 0.2.8 Ubuntu (Dapper) i386 Package (Thanks Chris Borga)

edit: I checked if i met the requirements:
Requirements ¶

    * Python 2.4
    * python-gtk2 (2.8.6)
    * gstreamer 0.10, gstreamer0.10-plugins-good
    * python-dbus
    * python-pysqlite2
    * python-mutagen 

and i have all of them.

when i type exaile in the terminal this is what i get:

> laptop:~$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 61, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media.py", line 19, in ?
    import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis

plz help

thanks



EDIT: got it working by foollowing this: (enter line by line in terminal) 
> wget [http://www.sacredchao.net/~piman/software/mutagen-1.8.tar.gz](http://www.sacredchao.net/~piman/software/mutagen-1.8.tar.gz)
tar xvfz mutagen-1.8.tar.gz
cd mutagen*
./setup.py build
sudo ./setup.py install


this is a reaally great program... i thought Amarok was the best but now i got this since i have Gnome. Thanks a lot and I hope we'll see more updates and features soon!

---

### Post by Jivicin on 2007-01-12
This is a really cool app!  The only thing I'd like to see added is a plugin that handles global hotkeys for basic operations (i.e. play, pause, next track, etc.).

But otherwise, nice job!

---

### Post by ajeetraj on 2007-01-12
but still it doesn't have amarok style lyric thing though :P but i still like it :)

---

### Post by cborga1985 on 2007-01-13
> **ajeetraj said:**
> but still it doesn't have amarok style lyric thing though :P but i still like it :)
right click->information->lyrics tab
i actually like the way exaile does it

---

### Post by dmBriarwood on 2007-01-14
I have been unable to get the pre-built package for
dapper to work ([http://www.exaile.org/trac/wiki/Releases]("http://www.exaile.org/trac/wiki/Releases"))

I get a dependency error :-(

$ sudo dpkg -i exaile_0.2.8_i386dapper.deb
Selecting previously deselected package exaile.
(Reading database ... 161920 files and directories currently installed.)
Unpacking exaile (from exaile_0.2.8_i386dapper.deb) ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on libpango1.0-0 (>= 1.12.3); however:
 Version of libpango1.0-0 on system is 1.12.2-0ubuntu3.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile

i.e., a slightly newer version of Pango is needed than what's included
in Ubuntu Dapper - Does anyone know when the Dapper repository is going to be updated?

---

### Post by manmower on 2007-01-14
Does anyone know if Exaile supports playback of .mp3 with external cuesheets? I tried searching their site but it only mentions .flac embedded cuesheets.

---

### Post by BobSongs on 2007-01-16
I hate to be a pain in the behind. I'm having a problem too.

Process:[LIST]
[*]Installed version 0.2b4 i386 and it ran no problem.
[*]Uninstalled 0.2b4 i386.
[*]Installed version [**0.2.8**]("http://www.exaile.org/files/exaile_0.2.8_i386dapper.deb") (Dapper i386 package).[/LIST]The icon appears under Applications / Sound & Video but nothing launches.

Open a command-line:

> Bob@PC2:~$ exaile
Traceback (most recent call last):
File "/usr/bin/exaile", line 61, in ?
from xl import *
File "/usr/share/exaile/xl/tracks.py", line 18, in ?
import common, media, db, config, trackslist
File "/usr/share/exaile/xl/media.py", line 19, in ?
import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis
Bob@PC2:~$ sudo dpkg -r exaile
(Reading database ... 111766 files and directories currently installed.)
Removing exaile ...


Let me know what to correct if this is due to the installation and later removal of version 0.2b4. If so, I recommend you modify the first page of this thread to reflect the most recent version.

The references to OggVorbis are odd. I know I can both play and rip to Ogg.

Thanks for your time.

BobSongs

Edit: just reinstalled version 0.2b4 and it plays just fine. I still await direction on how to correct the system for the latest player.

---

### Post by bonzodog on 2007-01-16
Just to let you know, us here in the Zenwalk Linux community now have it successfully packaged and working. Good work!

---

### Post by fadder on 2007-01-18
I just installed the latest 0.2.8 exaile (no older versions around), Dapper i386 .deb, and get exactly the same problems as BobSongs. Shows up in Soun and Video, but doesn't
launch, and gives same command line errors as above.  Any fixes?

---

### Post by hexion on 2007-01-19
Hi synic.

First of all thank you for your contribution ;)
I tested exaile some months ago and I'm testing it again. This time I'll comment some points I think it could be improved with.

Maybe some were pointed already in this thread, but it's too long for me to read, so sorry if they are already mentioned :)

Some other "points" could be already implemented... if so, I just didn't notice xD

- **Default organization of the playlists**: Artist - Album - Song
- **Shorting playlist by more than 1 criterium**: Default, first by artist, then by album, and finnaly by track number.
-** Album art collector should search for more than 1 cover at a time:** With huge playlists, searching 1 by 1 results in more than 30 minutes of search.
- **Lyrics feature:** Already implemented?
- **LIRC support**
- **Complex search support in playlist:** Like Amarok does. It supports searching by various tags, using google's codes. In example: "ensiferum" OR "system of a down" will show at playlist all lyrics of those 2 artists.

Another issue... are there translation teams in the exaile project?
I could help in spanish translation when I've got some time if you want :)

Regards

---

### Post by ciscosurfer on 2007-01-19
My tablature tab doesn't seem to work--on *any* files.  

Is this a known bug?  Any workarounds?  Am I doing something wrong?  

I am running Exaile 0.2.8 :guitar:

---

### Post by urukrama on 2007-01-19
> **hexion said:**
> - **Lyrics feature:** Already implemented?


That is already there. View > Information > Lyrics

Or just type Ctrl+L

---

### Post by epimer on 2007-01-22
Does anyone have Exaile running with Python 2.5 installed? I've been running Exaile for months without problems, but yesterday I compiled and installed Python 2.5 and today Exaile won't launch.

---

### Post by MaX on 2007-01-22
Any chance for a feisty package?

---

### Post by hanzomon4 on 2007-01-22
Yeah a feisty deb would be nice, the one in the repo can't play cd's

---

### Post by Morbett on 2007-01-22
I really like Exaile alot and would like it to be my main music app in Ubuntu, but until the whole Gstreamer and gapless playback thing is resolved (which seems doubtful), I still have to stick with Amarok...

---

### Post by Sweet Spot on 2007-01-23
> **Morbett said:**
> I really like Exaile alot and would like it to be my main music app in Ubuntu, but until the whole Gstreamer and gapless playback thing is resolved (which seems doubtful), I still have to stick with Amarok...

Since when does Amarok do gapless ? I've tried concerts in both Ogg and FLAC to no avail. So what do you know, that I don't ? Btw, I DID have the latest version of Amarok, but rolled back to 2.7.3 +patch in order that my FLAC files actually work.  

Also, I can't get Exaile to work. I installed the latest .deb and see it in my app menu, but when I click on it, absolutely nothing happens. I don't see any listed dependencies needed for it either. I'd love some help w/this please. 

Doug

---

### Post by BOBSONATOR on 2007-01-23
I love this program!

---

### Post by Morbett on 2007-01-23
> **Sweet Spot said:**
> Since when does Amarok do gapless ? I've tried concerts in both Ogg and FLAC to no avail. So what do you know, that I don't ? Btw, I DID have the latest version of Amarok, but rolled back to 2.7.3 +patch in order that my FLAC files actually work.  

Also, I can't get Exaile to work. I installed the latest .deb and see it in my app menu, but when I click on it, absolutely nothing happens. I don't see any listed dependencies needed for it either. I'd love some help w/this please. 

Doug


Hi,

I read this:

> xine-lib 1.0.2external link (audio backend) Note: xine-lib 1.1.1 is required for gapless playback.

On [this ]("http://wiki.kde.org/tiki-index.php?page=Amarok") wiki site:

---

### Post by gh0st on 2007-01-23
Great program dude, nice work. I don't need to install Amarok now.

Plus my favorite film is The Big Lebowski and you have the dude as your pic. "The dude abides man, the dude abides" :D

---

### Post by puppy on 2007-01-23
Hmm I can't use this unfortunately - even though I'd like to abandon Amarok. It doesn't support mp3 players that show up as removal drives does it... :(  the precise reason I bought an mp3 player with that sort of functionality was to use it with Amarok - shame I can't use it with exaile - anyone know whether generic mp3 players will be supported at a later date?

---

### Post by synic on 2007-01-24
> **puppy said:**
> Hmm I can't use this unfortunately - even though I'd like to abandon Amarok. It doesn't support mp3 players that show up as removal drives does it... :(  the precise reason I bought an mp3 player with that sort of functionality was to use it with Amarok - shame I can't use it with exaile - anyone know whether generic mp3 players will be supported at a later date?

UMS players will be supported in the next version, although the functionality is more the result of a proof of concept.  It's much easier just to add the mount point to your collection list, this way you don't have to scan it every time.  If you remove the mp3 player, those tracks just won't show up in your collection.

Adam

---

### Post by synic on 2007-01-24
> **gh0st said:**
> Great program dude, nice work. I don't need to install Amarok now.

Plus my favorite film is The Big Lebowski and you have the dude as your pic. "The dude abides man, the dude abides" :D

Mark it an 8!

---

### Post by MkfIbK7a on 2007-01-24
in the words of the program which died after "jumping the shark"

> Hey sit on it!

(if anybody gets this please reply!)

---

### Post by carolinason on 2007-01-24
Great player. Look forward to growing with it.

I haff lingenberry pancakes.

---

### Post by C-A on 2007-01-24
great program! it is now on my top 5 list

---

### Post by arkangel on 2007-01-25
Great i was using it since 2.4  now i am using 2.8 in dapper , i join to the exaile's fan club :P

---

### Post by ninjaPants on 2007-01-27
I can't get iPod device support to work. I've installed the .deb v.0.2.8 from exaile.org, downloaded and copied ipoddriver.py to /usr/share/exaile/plugins and restarted the program and the computer, but still don't see the plugin available in the plugin screen. Help!

---

### Post by synic on 2007-01-27
> **ninjaPants said:**
> I can't get iPod device support to work. I've installed the .deb v.0.2.8 from exaile.org, downloaded and copied ipoddriver.py to /usr/share/exaile/plugins and restarted the program and the computer, but still don't see the plugin available in the plugin screen. Help!

iPod support is built in to 0.2.8, you don't need a plugin.  If you don't see an iPod tab on the left, then you need to install the python-gpod package.

Adam

---

### Post by Cursetheman on 2007-01-28
Ok i just installed the Player and tryed to start playing music (.mp3/and radio) and it would start to play but it would not go anywhere the play icon will turn into a pause icon but it just sits there like nothign happends and playes nothing 
**please help**

---

### Post by SPLASTiK on 2007-01-28
I downloaded the latest .deb (0.2.8 ) yesterday and have been running it. I like it, pretty nice and was impressed at how fast it opened in comparison to Amarok. However, I do have a few qualms. I know it's still pretty young in the dev and I'm not sure what things exactly are in the works for the next release, I just thought I'd mention them.

1. Would be nice if when you opened Exaile, the last track you happened to be playing when you Quit the program was selected on the playlist so you could play where you left off.

2. My monitor is pretty small (13 inch :P) and my mother has poor eyesight so were running Edgy at 800x600. There's not much viewing room for a playlist at 800x600 as it only shows 8 songs due to all the screen room it takes up at the top with the Song title, Album art, bigger playlist font used and on the bootom of the screen with bigger function buttons, etc. Amarok on the other hand shows 18 songs due to it's bigger use of playlist screen space...  

I'm the kind of guy who pretty much just shows my entire library as the playlist, don't really do custom playlists or anything so if the track is highlighted that's playing, I don't really need a big album art and titles up there... But maybe that's just because I don't really have the screen space for it so it just happens to feel like a slight burden for me...

3. Exaile doesn't maximize on the screen properly on 800x600, I'll include a screen shot of what it looks like in 800x600... can see the desktop on left of the screen: [link](http://www.chazlakip.com/pics/exaile.png)

And here's Amarok for comparison sake in 800x600: [link](http://www.chazlakip.com/pics/amarok.png)

Hopefully a much needed BIG monitor upgrade with different resolution will fix that though :P
It seemed to look a lot nicer when I switched to 1024x768 to look at it for a second.

4. Other than that... It'd be nice if somehow you could lock the Information Tab there for the Wiki, Lyrics, etc. next to the playlists. I really loved that Amarok had that stuff and it sucks having to reopen the info tab every time you start the program. I actually really like how that was done in comparison to Amarok though. Nice and wide page to view all the Wiki info was a great idea!

I think that's it. Nice job, will definitely be keeping my eyes open for any future updates!

---

### Post by Protoss on 2007-01-28
I just started using Ubuntu full time, and after a day of just playing around with Listen, Amarok, RhythmBox, and Exaile, I finally chose Exaile as my music player of choice. 
But to get the multimedia keys to work, I had to use KeyTouch to map them to "exaile -a" for Play/Pause, etc, because the MediaKeys plugin wasn't working at all.

I agree with the above, that Information should be a sidebar tab, for quick access.
Great job on the player thus far!

---

### Post by chandru.in on 2007-01-31
Man that is an awesome player.  In fact it is the only one which made me remove Amarok.

Great job.  Congrats on that.  :KS 

I just have a suggestion for you.  I find that you are trying to include support for equalizers.  But, AFAIK, gstreamer does not support equalization.  If you are able to get it working with gstreamer, it would be gr8.

If not, y don't u try switching to the xine engine. I'm by no means a Python/GTK developer, so I dunno if this is gonna be possible.  But, it would be a great idea.

---

### Post by gosh on 2007-01-31
> **ciscosurfer said:**
> My tablature tab doesn't seem to work--on *any* files.  

Is this a known bug?  Any workarounds?  Am I doing something wrong?  

I am running Exaile 0.2.8 :guitar:

+1

---

### Post by chandru.in on 2007-02-01
Hey for xine engine, I just came across a library called pyXine.

[http://pyxine.sourceforge.net/](http://pyxine.sourceforge.net/)

It has been updated long back.  I just thought it might be helpful.

---

### Post by EisenPM on 2007-02-01
hello, just switched from amarok to exaile 0.2.8. !

I like it very much!

just one question:

what does the playback sink setting mean?

and a short wishlist:

- global shortcuts are definitely needed!
- it should be possible to hide the album cover and give more space to the play list
- and finally, a possibility to have the player control buttons above the playlist, not at the bottom

thanks!

---

### Post by Protoss on 2007-02-01
Alright I am having a bit of trouble with Last.fm and Exaile. I just cannot seem to get it to submit every song, it submitted 3 today, then just stopped submitting. Is anyone else experiencing a problem scrobbling in Exaile?

---

### Post by raublekick on 2007-02-01
> **Protoss said:**
> Alright I am having a bit of trouble with Last.fm and Exaile. I just cannot seem to get it to submit every song, it submitted 3 today, then just stopped submitting. Is anyone else experiencing a problem scrobbling in Exaile?

yes, just now while listening to an album, it failed to send the 4th track. however, i am not sure this is the fault of exaile.

---

### Post by Protoss on 2007-02-01
Strange...seems to be working just fine now. 
Oh well.
Great job on the player!

---

### Post by manmower on 2007-02-01
Might be their submissions server is having problems (it happens quite regularly, tracks will just be cached and submitted afterwards). Either that or your file wasn't properly tagged or in some other way not within last.fm regulations (e.g. tracks shorter than 30 secs aren't submitted).

---

### Post by gosh on 2007-02-05
Hi,
I tried out the latest svn version, but that only imported 300-something songs from my database of over 10.000. And it did not connect to my iPod Shuffle.

I removed that version and installed the 0.2.8_i368 edgy version (from deb) and that gave me errors: 
```
Traceback (most recent call last):
  File "/usr/bin/exaile", line 2296, in ?
    main()
  File "/usr/bin/exaile", line 2286, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/bin/exaile", line 179, in __init__
    self.setup_menus()
  File "/usr/bin/exaile", line 1631, in setup_menus
    self.shuffle.set_active(self.settings.get_boolean('shuffle', False))
TypeError: an integer is required

```This also occures after I purged it and compile the source myself.

Any help on this? 
Thanx because I really like this player better than others i've tried so far.

EDIT: it was solved by deleting the /home/username/.exaile folder and reinstalling the 0.2.8-I386.deb

---

### Post by vgrisham on 2007-02-06
> **synic said:**
> UMS players will be supported in the next version

Adam

Man, thank goodness for that. It's pretty frustrating to look long and hard to find an mp3 player that actually supports linux only to find that much of the linux development community is (undertandably) bending over backwards to support the proprietary iPod. I have a Cowon iAudio F2. Amarok plays nicely with it, but I look forward to Exaile as I prefer gnome.

Adam, any idea when the next version will be out?

---

### Post by reacocard on 2007-02-06
For you edgy users who are itching for a newer version of Exaile but don't want to compile it, I maintain a repository with recent Exaile SVN snapshots. You can get it by adding this to your /etc/apt/sources.list:
```
deb http://download.tuxfamily.org/syzygy42/ edgy exaile-svn
```
Then type this in a terminal:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install exaile
```

Otherwise, if you only want the stable versions, you can use this apt line instead:
```
deb http://download.tuxfamily.org/syzygy42 edgy exaile
```
Then use the same commands.

---

### Post by siimo on 2007-02-07
Just a heads up to the developer of this programme: the Tray Icons feature does not work in XFCE. I am using version 4.4 and it is not showing up.  All other apps' tray icon works here for example gaim, azureus, banshee music player written in mono etc.

---

### Post by siafok on 2007-02-07
Can you tell me why some covers dont apear on OSD. I have all my covers in .jpg, all in same folder with songs and all with the same name cover.jpg. All covers aperar properly in internall window over playlist but only few in OSD. It's strange. It's annoying and it's shame because Exaile is very good player.
                           Peace

---

### Post by EvergreyNY on 2007-02-07
> **Protoss said:**
> Alright I am having a bit of trouble with Last.fm and Exaile. I just cannot seem to get it to submit every song, it submitted 3 today, then just stopped submitting. Is anyone else experiencing a problem scrobbling in Exaile?


I'm having a similar problem. Random tracks won't get submitted for some reason. If I listen to the same songs in another player, they all get submitted.:confused:

---

### Post by SunnyRabbiera on 2007-02-07
Exaile is good, but amarok is still better for me as its media support is more vast to me.

---

### Post by reacocard on 2007-02-07
> **siimo said:**
> Just a heads up to the developer of this programme: the Tray Icons feature does not work in XFCE. I am using version 4.4 and it is not showing up.  All other apps' tray icon works here for example gaim, azureus, banshee music player written in mono etc.

I'm using xfce4.4, and the tray icon works fine for me.  Maybe you don't have python-gnome2-extras?

---

### Post by EisenPM on 2007-02-08
I switched back to Amarok now, beacuse Exaile is a lot slower when handling large playlists, und is not as responsive in general. additionally, when I select several mp3s in my file manager, it does open one exaile program for every file. amarok just puts them all in a playlist. But I'll check back back now an then ;-)

---

### Post by André on 2007-02-08
Hi Synic,

i really like your player. It works very well for me but i would prefer it in my language (german).

This thread is now 62 pages long and i may have missed a solution. AFAIK til now the language is set via the locales, isn't it?

Here is my locale output:

> 
andre@watson:~$ locale
LANG=de_DE.UTF-8
LANGUAGE=de_DE:de:en_GB:en
LC_CTYPE="de_DE.UTF-8"
LC_NUMERIC="de_DE.UTF-8"
LC_TIME="de_DE.UTF-8"
LC_COLLATE="de_DE.UTF-8"
LC_MONETARY="de_DE.UTF-8"
LC_MESSAGES="de_DE.UTF-8"
LC_PAPER="de_DE.UTF-8"
LC_NAME="de_DE.UTF-8"
LC_ADDRESS="de_DE.UTF-8"
LC_TELEPHONE="de_DE.UTF-8"
LC_MEASUREMENT="de_DE.UTF-8"
LC_IDENTIFICATION="de_DE.UTF-8"
LC_ALL=


Any idea what to do? I hope this was not solved too often before.

Greetings and keep up the good work!
André

P.S.: i use the stable exaile version.

---

### Post by gosh on 2007-02-09
I have a question on connecting my iPod _after_ Exaile is started-up.
If I first plugin my ipod and then startup Exaile, it is connected.
If I first startup Exaile and then plugin the ipod, Exaile says: not connected.

How can I connect the Ipod without restarting Exaile?

---

### Post by gosh on 2007-02-09
> **gosh said:**
> +1

tab works now, although about one in two songs isn't tabbed.

---

### Post by Drakx on 2007-02-09
Hey nice work :) I also have been waiting for a gtk amarok! keep up the good work.

---

### Post by synic on 2007-02-11
> **gosh said:**
> I have a question on connecting my iPod _after_ Exaile is started-up.
If I first plugin my ipod and then startup Exaile, it is connected.
If I first startup Exaile and then plugin the ipod, Exaile says: not connected.

How can I connect the Ipod without restarting Exaile?

Hit the refresh button.

---

### Post by gosh on 2007-02-11
> **synic said:**
> Hit the refresh button.
:oops:, sorry didn't noticed that.

BTW: I think it's a great! player

---

### Post by Polygon on 2007-02-11
ive been using exaile for a couple of months now after switching from listen, and i really like it, but there are some things that really annoy me (ive filed tickets for all of them so hopefully they should be addressed and or fixed.

---

### Post by ostlund on 2007-02-12
I have one problem with Exaile.
All my mp3's are not added to the music libary, some where there once, then i made a rescan an they disapere.

---

### Post by cephlon on 2007-02-12
Greetings, 
Nice Player!

This might sound like a weird question/request, but is there anyway to get the OSD to stay up and on top of all my other windows? Or is there an applet that I can have always open showing the Cover Art and Artist/sound etc..?

---

### Post by ciscosurfer on 2007-02-12
> **cephlon said:**
> Greetings, 
Nice Player!

This might sound like a weird question/request, but is there anyway to get the OSD to stay up and on top of all my other windows? Or is there an applet that I can have always open showing the Cover Art and Artist/sound etc..?I am running Exaile 0.2.8 and you can find what you are looking for under Tools > Plugins > Desktop Cover (enable it and configure it as you like).  As for the OSD staying up permanently, I can't say.  I do know that by default, once Exaile is running and playing a song, you can check which song is playing (and the OSD will pop up) by hovering your mouse over the exaile icon located in your Notification Area (like the system tray in Windows).

---

### Post by gosh on 2007-02-13
Hi there again,

I have trouble with the "watch directory" function.
When I choose tools -> preferences -> general -> library and mark "Watch directory for new songs" and click OK or apply this window hangs. None of the buttons work then anymore.

I have gamin installed.

---

### Post by gosh on 2007-02-15
> **gosh said:**
> I have a question on connecting my iPod _after_ Exaile is started-up.
If I first plugin my ipod and then startup Exaile, it is connected.
If I first startup Exaile and then plugin the ipod, Exaile says: not connected.

How can I connect the Ipod without restarting Exaile?

Well, I still have some trouble. The refresh button doesn't do the job.

This is my mount information:
```
/dev/sdc1 on /media/ipod type vfat (rw,noexec,nosuid,nodev,fmask=0111,dmask=0000)

```

It is properly mounted:
```
~$ ls /media/ipod/
iPod_Control

```

Mount point in Exaile is /media/ipod

Any help?

---

### Post by Drakx on 2007-02-15
run into a small problem with exaile and feisty :)

```

drakx@Laptop:~$ exaile 
/usr/lib/python2.5/site-packages/mutagen/m4a.py:41: DeprecationWarning: mutagen.m4a is deprecated; use mutagen.mp4 instead.
  "mutagen.m4a is deprecated; use mutagen.mp4 instead.", DeprecationWarning)
Error grabbing key 162, 0x83af418
Traceback (most recent call last):
  File "/usr/bin/exaile", line 2299, in <module>
    main()
  File "/usr/bin/exaile", line 2289, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/bin/exaile", line 179, in __init__
    self.setup_menus()
  File "/usr/bin/exaile", line 1637, in setup_menus
    self.repeat.set_active(self.settings.get_boolean('repeat', False))
TypeError: an integer is required
```

Any ideas? thanks.

---

### Post by giacomolg on 2007-02-20
Thank you so much for your program. It's beautiful !!
Only a few points: It would be useful (for me) to be able to edit the track properties from the sidebar as well and to be able to decide the size of the cover.
...and for the menu, why don't make it Gnome compliant ?


Thanks again for your work:guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar:

---

### Post by Athropos on 2007-02-21
For those who are using Gajim as their instant messenger, I wrote a plugin for Exaile that updates your online status: see [here](http://fingelrest.silent-blade.org/index.php?n=Hobbies.ProgrammingGajimStatus).

---

### Post by ArtInvent on 2007-02-22
I've heard Exaile is cool so I'd like to see for myself. I have Edgy, downloaded the "0.2.8 Ubuntu (Edgy) Package." So the Exaile install opens nicely and I notice that it says "Requires the removal of 33 packages." Well, uh, maybe one or two minor packages might have to be replaced for something like this, but 33? So I open the details and it's trying to remove some pretty non-trivial packages like, oh, gdebi, nautilus, gedit, and things like gnome-applets, gnome-terminal . . . and a whole bunch of others. So it is actually removing these actual programs or just some hooks or references to these? (I can post a screenshot if needed.)

This looks pretty horribly wrong to me. Am I missing something? I've googled and searched the forums with no reference to this found. Needless to say, I'm not installing this anytime soon without some kind of explanation.

(No, I'm not on Dapper and downloaded the Edgy package by mistake, or vice versa.)

---

### Post by Athropos on 2007-02-22
Do you have some extra sources in your repository list? Have you installed some other more recent package on top of official ones?

---

### Post by synic on 2007-02-22
> **ArtInvent said:**
> I've heard Exaile is cool so I'd like to see for myself. I have Edgy, downloaded the "0.2.8 Ubuntu (Edgy) Package." So the Exaile install opens nicely and I notice that it says "Requires the removal of 33 packages." Well, uh, maybe one or two minor packages might have to be replaced for something like this, but 33? So I open the details and it's trying to remove some pretty non-trivial packages like, oh, gdebi, nautilus, gedit, and things like gnome-applets, gnome-terminal . . . and a whole bunch of others. So it is actually removing these actual programs or just some hooks or references to these? (I can post a screenshot if needed.)

This looks pretty horribly wrong to me. Am I missing something? I've googled and searched the forums with no reference to this found. Needless to say, I'm not installing this anytime soon without some kind of explanation.

(No, I'm not on Dapper and downloaded the Edgy package by mistake, or vice versa.)

Definitely sounds like your sources.list is jacked up (or it used to be), or you had some non-official repos in there at some point.

---

### Post by PARO on 2007-02-24
Hey great program! Only I can't get radio stations to play. I've added them in the radio saved stations list, and in file>open url. All are mp3 streams, and play fine in both vlc and quod libet.  Do I need something in order to get this working in exaile? BTW they appear in the list and it counts the time they are playing, but I get no sound.

Also, not a problem but a preference, it would be great if I could shrink the size of exaile to at least less than 2/3 of my screen size (preferably 1/4 or less), I can manipulate the size of columns still, but the overall size wont go smaller.  I'm using Xubuntu, and have grown used to sending things back with a middle mouse click, and so like to keep window sizes rather small (except my browsers), so I can more easily multi-task w/o bothering too much with multiple workspaces. Thanks.

EDIT: BTW I'm using 0.2.8 in Edgy

---

### Post by olavjunior on 2007-03-04
Great player!

The first thing I'm missing is click'n drag album covers that aren't autofetched. 
But really -the album art collector is GREAT!

Thanx!

---

### Post by olavjunior on 2007-03-04
> **Athropos said:**
> For those who are using Gajim as their instant messenger, I wrote a plugin for Exaile that updates your online status: see [here](http://fingelrest.silent-blade.org/index.php?n=Hobbies.ProgrammingGajimStatus).

I can't configure your plugin. Nothing happens when I push configure..

---

### Post by Athropos on 2007-03-04
> **olavjunior said:**
> I can't configure your plugin. Nothing happens when I push configure..

Which version are you using? There's a new version that handles multiple IM clients (currently Gaim, Gajim and Gossip):

[http://fingelrest.silent-blade.org/index.php?n=Hobbies.ProgrammingExaileIMStatus](http://fingelrest.silent-blade.org/index.php?n=Hobbies.ProgrammingExaileIMStatus)

Are you sure you are using the good plugin? There was another plugin for Exaile without configuration dialog.

---

### Post by olavjunior on 2007-03-04
Yes! I'm using the latest version. Strange. I'm gonna try putting it in again, and restart exaile. If others get it to work then there shouldn't be any problems here I guess..

---

### Post by Athropos on 2007-03-04
Please try to launch Exaile from a console and see if there's an error when you try to display the configuration dialog.

---

### Post by olavjunior on 2007-03-04
When I start exaile, I get this output: 
[I]Plugins 'Alarm Clock' version '0.1' loaded successfully
Plugins 'Desktop Cover' version '0.1' loaded successfully
desktopcover.py_geometry
Cover geometry: 150x150-40+20
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 41, in load_plugins
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/usr/share/exaile/plugins/exailenotify.py", line 17, in ?
    import gtk, pynotify, plugins, traceback, cgi
ImportError: No module named pynotify
Plugins 'Mini Mode' version '0.1' loaded successfully
Plugins 'Serpentine Plugin' version '0.1' loaded successfully
Plugins 'Streamripper!' version '0.1' loaded successfully
Plugins 'IM Status' version '0.09' loaded successfully
Created db for thread Thread-1
{'Thread-1': <pysqlite2.dbapi2.Connection object at 0xb6a3a278>}
mmkeys are available.
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Gamin not available, not watching directories[/I]

Seems to lack something for the notifyer. And it says that gamin is not availeble (I have the package installed) But there's nothing on the gaim-plugin except that it loaded succsessfully. 

But when I push config, this is the error: 
[I]Traceback (most recent call last):
  File "/usr/share/exaile/plugins/gui.py", line 132, in configure_plugin
    plugin.configure()
  File "/home/junior/.exaile/plugins/imstatus.py", line 306, in configure
    entryFormat.set_text(APP.settings.get_str('format', DEFAULT_STATUS_FORMAT, PID))
AttributeError: 'Config' object has no attribute 'get_str'
[/I]

---

### Post by Athropos on 2007-03-04
You are not using Exaile 2.9, are you? :)

It seems that some of the functions used for the configuration have been added in 2.9, I didn't know that.

---

### Post by olavjunior on 2007-03-04
I'm using 2.8

Ok, I didn't realize that there was a newer verison when I downloaded exaile earlier this day. So now I have the 2.9, and there's some changes yes :)
(inkluding a larger cpu-usage I think?) Now the plugin works! Great :)

---

### Post by Athropos on 2007-03-04
V2.9 is beta. You may continue to v2.8, but then you won't be able to configure my plugin. This is because the functions used for this have been added in v2.9, and do not exist in v2.8.

---

### Post by Polygon on 2007-03-04
speaking of exaile 2.9b, does anyone still have it show version 2.8 when you go to help > about?

and i tried to go the terminal and do exaile --version, and it gave me some dbus error and then said 2.9b...

and i also tried that plug in you wrote, and it appears to work as it shows up in the plugins list and i enabled it, but how do i know it worked? it does not appear in my info for 'gaim" and at the bottom of gaim 2.0 it still just says "available"

---

### Post by olavjunior on 2007-03-04
Same question here! I asked my friends if it showed what I was listening to, and the answer was nope.. I'm using Gaim 2.0.0beta3.1

Gonna update to beta6. Maby that's it

EDIT:

Nope, didn't help. Here's my output: 

[I]Plugins 'IM Status' version '0.09' loaded successfully
Introspect error: The name org.gajim.dbus was not provided by any .service files
Introspect error: The name net.sf.gaim.GaimService was not provided by any .service files
Introspect error: The name org.gnome.Gossip was not provided by any .service files
Created db for thread Thread-1
{'Thread-1': <pysqlite2.dbapi2.Connection object at 0xb6ace980>}
Logging in to audioscrobbler
mmkeys are available.
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/junior/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0

[/I]

---

### Post by Athropos on 2007-03-04
The status message should be written at the bottom of the roster. D-BUS support was not available in previous versions of Gaim, (<2.0) so I don't know whether it was already present (and with the same API) in previous beta versions. At least, I'm sure it's working with beta6.

---

### Post by olavjunior on 2007-03-04
Well, it's not displayed :S

Do I have to configure gaim in a special way?

---

### Post by Polygon on 2007-03-04
im using 2.0 beta 3

and in the help>about box, it does say

> 
   D-BUS: Enabled


---

### Post by olavjunior on 2007-03-04
ok, so d-bus is my problem. It's disabled. How do I enable it?

EDIT: Now I remember I had problems with dbus-1 and dbus-glib-1 missing when I tried to install some other thing (can't remember what) So instead of installing it manually from the web-page, I installed via synaptics (an older version though) And then the installation worked. I have the regular dbus and dbus-1 utility installed in synaptics. 

Any ideas?

---

### Post by Polygon on 2007-03-04
is an option to enable it or disable it at compile time... so if you know how to compile it, try it with dbus enabled

---

### Post by olavjunior on 2007-03-05
But the other program that was needing the dbus-1 ect. said the packages was missing! 
So how do I get them when they're not in the regular dbus from synaptics?

---

### Post by rjcsc on 2007-03-13
There are any plans to suport MTP devices (like Creative Zen) in Exaile?

---

### Post by synic on 2007-03-13
> **rjcsc said:**
> There are any plans to suport MTP devices (like Creative Zen) in Exaile?

Sure, if a programmer with a Zen wants to write a plugin, or if someone wants to send me a Zen :D

---

### Post by brodiepearce on 2007-03-14
Christ this is ridiculous, I get the feeling this thing will never bloody install, so far had to download 4 new packages because the Synaptic utility doesn't have new enough packages for certain things, and must have installed about 10 packages so far in synaptic.

Some of the config requirements even loop back on themselves!  At one point I had to install liboil-0.3, I did that through Synaptic, ten minutes later another package wants me to install liboil-0.3.8 to satisfy the config.  :mad:

*edit*  
Arrived at the latest error, I have no idea about this one... I've installed everything else to satisfy the Exaile configure script, but I get this error now:
```
Error: Dependancy is not satisfiable: libatk1.0-0
```

---

### Post by Elijah on 2007-03-14
awesome app, I really like kde's (forgot the name) but a gtk version is preferable, which is here! . :KS

---

### Post by synic on 2007-03-14
> **brodiepearce said:**
> Christ this is ridiculous, I get the feeling this thing will never bloody install, so far had to download 4 new packages because the Synaptic utility doesn't have new enough packages for certain things, and must have installed about 10 packages so far in synaptic.

Some of the config requirements even loop back on themselves!  At one point I had to install liboil-0.3, I did that through Synaptic, ten minutes later another package wants me to install liboil-0.3.8 to satisfy the config.  :mad:

*edit*  
Arrived at the latest error, I have no idea about this one... I've installed everything else to satisfy the Exaile configure script, but I get this error now:
```
Error: Dependancy is not satisfiable: libatk1.0-0
```

Sounds like you've got a seriously messed up sources.list.  This is what happens when you put non-official repos in there.

---

### Post by dmg025 on 2007-03-14
Looks pretty sleek.  Props man.   I am new to linux, but the feature list looks pretty good.

---

### Post by digidrake on 2007-03-15
This thing is pretty kewl. Now if only I can get my my bloody drm wma music tranferred over to some other format, I'd be thrilled.

:guitar:

---

### Post by ciscosurfer on 2007-03-15
> **digidrake said:**
> This thing is pretty kewl. Now if only I can get my my bloody drm wma music tranferred over to some other format, I'd be thrilled.

:guitar:Good luck!

---

### Post by brodiepearce on 2007-03-16
Has anyone else had issues with libatk1.0-0?

---

### Post by boast on 2007-03-16
is there a plugin, or some way, to be able to play music through samba?

---

### Post by reacocard on 2007-03-16
> **boast said:**
> is there a plugin, or some way, to be able to play music through samba?

Use fusesmb or smbfs to make the share appear in a directory, then either add it to your library folders or just use the filebrowser.

A better way, however, would be to use DAAP to share your music over the network. The Exaile DAAP plugin isn't quite released yet, but I can get you set up with it if you're interested.

---

### Post by jseiser on 2007-03-16
as soon as this supports my vision M id use it :(

---

### Post by merlyn on 2007-03-16
Call me slow, but I just recently got around to installing 0.2.8. 

Not going to play with the beta just yet.

Why did it take me so long? I just couldn't be bothered setting up my album art collection again, as the previous version pulled down the wrong cover on a number of ocassions.

Getting to the point, I really ought to have done it sooner. I'm really impressed at how much better it behaves, not to mention how much faster it indexed my collection.

Good stuff.

BTW are there any plans to add visualisations, perhaps a plugin?

Cheers

---

### Post by reacocard on 2007-03-17
> **merlyn said:**
> BTW are there any plans to add visualisations, perhaps a plugin?

There are visualizations in 0.2.9

---

### Post by travishume on 2007-03-17
ETA on the daap plugin?  Not being able to listen to my daap share is the only reason I'm not using exaile.

---

### Post by reacocard on 2007-03-17
> **travishume said:**
> ETA on the daap plugin?  Not being able to listen to my daap share is the only reason I'm not using exaile.

Preliminary version is attached. It's not final, so I would greatly appreciate feedback on it. I have only tested it against SVN, but the 0.2.9 beta should also work.

Place the file in /home/<user>/.exaile/plugins/ to install.

Note that it will not work with iTunes 7, this is a limitation of python-daap, the backend library I use. Any other server should work fine though.

---

### Post by Sweet Spot on 2007-03-19
I'm having the same problem which someone posted about 4 pages ago. None of my Mp3 files show up when I try and import them, at all. Why would this be ? Only seeing Ogg and FLAC files.

Sorry, forgot to mention that I just installed it last night, using the code from page one, the original post of this thread. Version 0.2b4

---

### Post by reacocard on 2007-03-19
> **Sweet Spot said:**
> I'm having the same problem which someone posted about 4 pages ago. None of my Mp3 files show up when I try and import them, at all. Why would this be ? Only seeing Ogg and FLAC files.

Sorry, forgot to mention that I just installed it last night, using the code from page one, the original post of this thread. Version 0.2b4

You should use the newer version (0.2.8!) from exaile.org instead. You'll need the gstreamer0.10-plugins-bad package for mp3 support, iirc.

---

### Post by Sweet Spot on 2007-03-19
So then should I completely uninstall the version which is currently installed before installing the new one ? If so, what's the command to purge it from Ubuntu ?  And for the record, I was looking at the exaile.org site, and didn't see the download for the newest version ?

Doug

Edit: Nevermind... Just looked again and found it. Must've been tired first time I looked. Question now is, should I just install it over the previous version ?

Edit for the edit: Never mind on that too. I installed it. :) Hopefully there will be no further edits, particularly ones which say that I'm having the same problems.

---

### Post by Sweet Spot on 2007-03-19
Guess this deserves more than an edit. I've tried opening Exaile several times now, and it just won't do anything. I'm using the applications drop down list > sound and video> Exaile icon, and nothing. I've checked in System Monitor, and it doesn't show up in there at all either, so why isn't the icon directing me to the app anymore ?

I've even gone and tried to redirect it by going into usr>bin>exaile   as the point of reference, and that does nothing either.

---

### Post by Tuna-Fish on 2007-03-19
> **Sweet Spot said:**
> Guess this deserves more than an edit. I've tried opening Exaile several times now, and it just won't do anything. I'm using the applications drop down list > sound and video> Exaile icon, and nothing. I've checked in System Monitor, and it doesn't show up in there at all either, so why isn't the icon directing me to the app anymore ?

I've even gone and tried to redirect it by going into usr>bin>exaile   as the point of reference, and that does nothing either.

You need to nuke the old library files. They are under /home/<you>/.exaile
Just delete the entire folder. The format for them changed in some version and now it crashes trying to load them.

for exaile makers: It would probably be prudent, that if exaile cannot load the files, but they exist, it deletes them and makes new ones. There are plenty of newbies asking this very question.

---

### Post by Sweet Spot on 2007-03-19
Tried that, but still doesn't load, even after re installing Exaile. For the record, I searched the dependencies, and found that when I searched for  "python-dbus" I got no search results (synaptec). I have all other pre requisites installed though. 

How can I totally as you say.. Nuke exaile from my system, so that there's not a trace anywhere at all ? I deleted the folder as you said though. Wondering if the first thing I did messed it up. I deleted the folder which was in : >Home, only. Inside the Home folder, is an Exaile folder, but there was probably one in : >file system> home> user> as well, right ?

Edit: Must've screwed something because now, I don't even see the executable exaile file which was found in "usr>bin. Even after reinstalling exaile twice. Alright, what to do eh ?

---

### Post by Sweet Spot on 2007-03-19
bumpage

---

### Post by foxy123 on 2007-03-19
I have noticed that if the format of a track number is say 1/8 (fist track of total eight tracks) Exaile does not recognise it. I have a number of albums tagged with Ex Falso and Exaile sort them alphabetically rather than by track number.

---

### Post by reacocard on 2007-03-19
> **Sweet Spot said:**
> Tried that, but still doesn't load, even after re installing Exaile. For the record, I searched the dependencies, and found that when I searched for  "python-dbus" I got no search results (synaptec). I have all other pre requisites installed though. 

How can I totally as you say.. Nuke exaile from my system, so that there's not a trace anywhere at all ? I deleted the folder as you said though. Wondering if the first thing I did messed it up. I deleted the folder which was in : >Home, only. Inside the Home folder, is an Exaile folder, but there was probably one in : >file system> home> user> as well, right ?

Edit: Must've screwed something because now, I don't even see the executable exaile file which was found in "usr>bin. Even after reinstalling exaile twice. Alright, what to do eh ?

I just noticed your profile says you use Dapper. Exaile currently doesn't play nice with dapper, because dapper's mutagen packages are too old. If you compile new ones or upgrade to edgy everything should be fine.

---

### Post by Sweet Spot on 2007-03-19
I guess that means Oh well for now then. Why is it offered for Dapper in that case ? And how the heck to I purge its remains from my system please ?

---

### Post by reacocard on 2007-03-20
> **Sweet Spot said:**
> I guess that means Oh well for now then. Why is it offered for Dapper in that case ? And how the heck to I purge its remains from my system please ?

```
sudo apt-get remove --purge exaile
```

---

### Post by cborga1985 on 2007-03-20
> **manutdfan2850 said:**
> ok i dont know what is wrong... i installed using the deb i downloaded from the exaile website. 

and when i click the Exaile! icon in Sound/Video nothing happens. i dont know whats wrong. any ideas?

this is what i donwloaded. : 0.2.8 Ubuntu (Dapper) i386 Package (Thanks Chris Borga)

edit: I checked if i met the requirements:
Requirements ¶

    * Python 2.4
    * python-gtk2 (2.8.6)
    * gstreamer 0.10, gstreamer0.10-plugins-good
    * python-dbus
    * python-pysqlite2
    * python-mutagen 

and i have all of them.

when i type exaile in the terminal this is what i get:



plz help

thanks



EDIT: got it working by foollowing this: (enter line by line in terminal) 



this is a reaally great program... i thought Amarok was the best but now i got this since i have Gnome. Thanks a lot and I hope we'll see more updates and features soon!

you can also do this which is probably more supported by the distribution
```
cd ~/Desktop
wget http://janvitus.interfree.it/ubuntu/pool/dapper-janvitus/main-amd64/python-mutagen_1.6-0ubuntu1~janvitus_all.deb
sudo dpkg -i python-mutagen_1.6-0ubuntu1~janvitus_all.deb
rm python-mutagen_1.6-0ubuntu1~janvitus_all.deb
```

---

### Post by Sweet Spot on 2007-03-20
Cborga 1985: It looks to me like this is the same thing I was going through. I just totally wiped Exaile from my system (Thanks a lot for that command reacocard) but wouldn't mind trying again if what you listed works. In that case, should I sudo those commands which you posted before installing the Exaile .deb again ?  For the record, when I searched the repository for :

Python-dbus"  It never showed up for me, so I'm assuming it isn't installed on my system. 

Doug

---

### Post by Sweet Spot on 2007-03-20
Actually looks like I do have Python dbus. It's now listed under 'libdbus' though. :
Might I need any of the other ones though ?


[[img]http://img1.putfile.com/thumb/3/7811545249.jpg[/img]](http://www.putfile.com/pic.php?img=5029279)

---

### Post by travishume on 2007-03-20
Ok, just downloaded the plugin and am now listening to my openvpn bridged home dapp share at work :)

Plugin worked fine.  I guess my only suggestion would be the work performed in the UI thread.  Because it's over a vpn it's a bit slow to connect and the UI is frozen solid during that time.  After connecting though the plugin seems very performant.

I have a friend here at work with a 150G itunes share I'll try next.  Let me know if you want some testing help.  I'll be using the plugin a lot during the day while at work.

Thanks for your work, it's appreciated.

---

### Post by reacocard on 2007-03-20
> **travishume said:**
> Ok, just downloaded the plugin and am now listening to my openvpn bridged home dapp share at work :)

Plugin worked fine.  I guess my only suggestion would be the work performed in the UI thread.  Because it's over a vpn it's a bit slow to connect and the UI is frozen solid during that time.  After connecting though the plugin seems very performant.

I have a friend here at work with a 150G itunes share I'll try next.  Let me know if you want some testing help.  I'll be using the plugin a lot during the day while at work.

Thanks for your work, it's appreciated.

Thanks for the feedback. The library fetcher is actually in the same thread as the UI, hence the slowdown. I hadn't thought it'd be an issue, but I didn't consider VPNs. I'll have to fix that. I would greatly appreciate your helping test this plugin, since that's what I need most at this point. I'm interested to see how it'll perform with your friend's library (150G?!!), as I don't have anywhere near that big of a library to test with.

---

### Post by Yellowbelly on 2007-03-20
I just downloaded Exaile after Amarok is failing to work properly and everything else sucks. After using iTunes, there are hardly any programs that come close. I've used winamp for a long time but after having an ipod and having tons of music, itunes it great for organization. Amarok so far is the only thing that came close and in some ways better than itunes. I'm dissappointed with amarok right now (1.4.5) I think it's buggy. Updating the collection, won't play music, and freezes all the time.

 I tried exaile and I like it. It's a different set up which is good but I realize it's still not perfect. One thing I wish this and Amarok would search similar to itunes - like type in a letter and it goes straight to the artists names that starts with that letter while showing the other bands too. Search function still works the same as the others too. But then I found out I can't change the file names and tags in Exaile. I hope this gets fixed soon. So far it's a really good, intuitive program. Much better than the ugly Banshee and Rythmbox. Those didn't work out for me.

Just curious, what plugins would y'all recommend for this?

---

### Post by reacocard on 2007-03-20
> **Yellowbelly said:**
> I just downloaded Exaile after Amarok is failing to work properly and everything else sucks. After using iTunes, there are hardly any programs that come close. I've used winamp for a long time but after having an ipod and having tons of music, itunes it great for organization. Amarok so far is the only thing that came close and in some ways better than itunes. I'm dissappointed with amarok right now (1.4.5) I think it's buggy. Updating the collection, won't play music, and freezes all the time.

 I tried exaile and I like it. It's a different set up which is good but I realize it's still not perfect. One thing I wish this and Amarok would search similar to itunes - like type in a letter and it goes straight to the artists names that starts with that letter while showing the other bands too. Search function still works the same as the others too. But then I found out I can't change the file names and tags in Exaile. I hope this gets fixed soon. So far it's a really good, intuitive program. Much better than the ugly Banshee and Rythmbox. Those didn't work out for me.

Just curious, what plugins would y'all recommend for this?

File names you can't change, but you can edit the tags when they're in the main playlist area, just right-click, edit track, edit information. Exaile's tag editor is pretty limited, but Ex Falso is a good stand-alone alternative that more than makes up for that.

As for plugins, I'd say Mini Mode, Serpentine and  Sound Juicer are essential, and the DAAP plugin I posted earlier is good too, if you don't mind the fact that it still has a few issues. Streamripper is also nice if you like internet radio.

---

### Post by travishume on 2007-03-21
No luck with my friends itunes share.  I can see it, but I keep asked for authentication but my friend doesn't have password protection turned on.  

Rhythmbox and Banshee don't ask for credentials, but they also don't ever load the library.

---

### Post by reacocard on 2007-03-21
> **travishume said:**
> No luck with my friends itunes share.  I can see it, but I keep asked for authentication but my friend doesn't have password protection turned on.  

Rhythmbox and Banshee don't ask for credentials, but they also don't ever load the library.

Is it iTunes 7? If so, that's the problem. Apple made changes to DAAP in iTunes 7, so no current open-source clients can connect to it yet.  Ask your friend to use a stand-alone DAAP server instead, like [Tangerine]("http://www.snorp.net/log/tangerine").

---

### Post by jseiser on 2007-03-21
just waiting for this to support my MPT device and id love to use it!

---

### Post by reacocard on 2007-03-21
> **jseiser said:**
> just waiting for this to support my MPT device and id love to use it!

As none of the devs has an MTP music player (so far as I know), this probably won't happen soon. Writing a plugin for it shouldn't be too difficult, but its kinda hard to do that when you don't have any way to test it. :)

---

### Post by synic on 2007-03-21
> **reacocard said:**
> As none of the devs has an MTP music player (so far as I know), this probably won't happen soon. Writing a plugin for it shouldn't be too difficult, but its kinda hard to do that when you don't have any way to test it. :)

Well, actually, I've convinced a girl that she needs to let me borrow hers.  I'll be getting it tonight, so we'll see what happens.

---

### Post by Yellowbelly on 2007-03-23
just encountered my first problem with exaile. Sound quality is garbage. Maybe I don't have a right codec or something but it's scratchy and fuzzy.

---

### Post by synic on 2007-03-24
> **Yellowbelly said:**
> just encountered my first problem with exaile. Sound quality is garbage. Maybe I don't have a right codec or something but it's scratchy and fuzzy.

Turn the volume down in Exaile itself, and turn it up on the hardware.  This should take care of the problem.

---

### Post by synic on 2007-03-24
Hey folks, I've started a blog if you're interested.  The url is [http://www.vimtips.org](http://www.vimtips.org).  It will mostly be of interest to programmers and vim users, but I'll throw Ubuntu info and general server information in there occassionally.

Adam

---

### Post by kenrowe410 on 2007-03-26
Long time Exaile user, just experienced my first problem.

A recent update to the beta version of Feisty seems to have killed the multimedia keys on my laptop, at least in Exaile 0.2.9b.  They still seem to work in Rhythymbox, though.

Anyone else experience this?

Thanks for the help,

Ken

---

### Post by yesdup on 2007-03-28
Hi all,

Newbie here. 

Like the program but it won't play radio streams, i can't seem to find a user guide for this program and i'm getting frustrated as other people seem to be having success. I'm not trying to rip the stream YET, just play. I have installed gstreamer-ugly libs but all streams seem to do the same.

I open the radio tab and highlight a predefined station then press play. the timer starts counting the pop up box displays the station but no music. 

Are ther any other steps required? is there a user guide? 

First sound then ripping?

Thanks in advance

---

### Post by sudhansh on 2007-03-28
ken:
me too facing the same problem. but the problem is due to feisty upgrade and not because of exaile. i hope to get it sorted out with the next feisty upgrade (rc1) due in fist week of april.

---

### Post by merlyn on 2007-03-29
Actually I just noticed that an 'old' annoyance is **still **present, my 'only' annoyance at that.

Having just opened a double album, Exaille insists on listing the  tracks as 1,1,2,2,3,3, etc rather than 1,2,3,.... 1,2,3,.... 

Not that I'm suggesting this is how the database stores track information, but merely trying to demonstrate the order in which the tracks are displayed.

I thought that this was to have been fixed some time ago? 

Even dusty old Rhythmbox, or perhaps I should say 'old faithful', handles this properly.

---

### Post by jseiser on 2007-03-29
> **synic said:**
> Well, actually, I've convinced a girl that she needs to let me borrow hers.  I'll be getting it tonight, so we'll see what happens.

anything come of this?

---

### Post by Dirty Ole on 2007-03-29
Just installed .29 from exaile repo. It has changed a great deal from .25. Good work!!

OK. Exaile is not recognizing some of my songs although Ryhthmbox and QuodLibet do tha fine, and to make the matters worse they are songs of my favourite artist.

---

### Post by merlyn on 2007-03-29
> **Dirty Ole said:**
> Just installed .29 from exaile repo. It has changed a great deal from .25. Good work!!

OK. Exaile is not recognizing some of my songs although Ryhthmbox and QuodLibet do tha fine, and to make the matters worse they are songs of my favourite artist.

Out of curiosity, what format(s) are those particular files?

---

### Post by merlyn on 2007-03-30
I'd thought about editing my previous post, but as this is a different 'topic' decided not to.

I would like to know where to submit screenshots of Exaille these day's as the revamped site no longer has it's own forum?

---

### Post by afljafa on 2007-03-30
I don`t think it`s anywhere near as good as Amarok at the moment - It certainly doesn`t handle moving from track to track particularly well if the music is continuous between the tracks.

---

### Post by Dirty Ole on 2007-03-30
> **merlyn said:**
> Out of curiosity, what format(s) are those particular files?

mp3.

---

### Post by merlyn on 2007-03-30
> **Dirty Ole said:**
> mp3.

Check out this site [here]("https://help.ubuntu.com/community/RestrictedFormats/MP3"), hopefully you will find it useful.

Cheers.

---

### Post by reacocard on 2007-03-30
> **afljafa said:**
> I don`t think it`s anywhere near as good as Amarok at the moment - It certainly doesn`t handle moving from track to track particularly well if the music is continuous between the tracks.

That's a gstreamer problem, unfortunately. Not much Exaile can do about that.

---

### Post by Dirty Ole on 2007-03-30
> **merlyn said:**
> Check out this site [here]("https://help.ubuntu.com/community/RestrictedFormats/MP3"), hopefully you will find it useful.

Cheers.

Cheers Mate. I don't have problems playing the files, but that Exaile doesn't add mentioned files to its library while other audio players do. And those of which it adds they appear to be inappropriately tagged but actually they are. 

Thanks for the reply anyways.

---

### Post by merlyn on 2007-03-30
That's most bizarre indeed, mp3's appear in my library no dramas.

I use 'easytag' to modify my mp3 tags, you might like to try that, (perhaps you already do). :confused:

---

### Post by reacocard on 2007-03-30
If the mp3s' tags have Unicode characters in them, that could be the problem. Exaile still has some issues with Unicode.

---

### Post by Dirty Ole on 2007-03-30
> **reacocard said:**
> If the mp3s' tags have Unicode characters in them, that could be the problem. Exaile still has some issues with Unicode.

They were tagged using iTunes which uses Unicode. So does that mean I'll have to wait?

---

### Post by klep on 2007-03-31
hello all, 

i'm trying out exaile as a possible replacement to amarok (which i absolutely love, but the startup time is horrible on gnome). I have a few issues:

I'm using .29. I note a few pages back someone saying about double albums getting ordered wrongly (1,1,2,2,..) and that this was supposed to be fixed. Presumably it hasnt? Or am i missing a setting somewhere.

Second is just a suggestion. It seems tiny, but the X clear search button in amarok is really useful. In exaile if ive searched for Pearl Jam for example, I dont know if there's any other way to see the rest of my collection again without selecting the search term and deleting it manually.
.

Cheers

---

### Post by reacocard on 2007-03-31
> **Dirty Ole said:**
> They were tagged using iTunes which uses Unicode. So does that mean I'll have to wait?

Well, you could use something like easytag or cowbell to remove the Unicode charachers from the tags, but aside from that, yes.

> **klep said:**
> hello all, 

i'm trying out exaile as a possible replacement to amarok (which i absolutely love, but the startup time is horrible on gnome). I have a few issues:

I'm using .29. I note a few pages back someone saying about double albums getting ordered wrongly (1,1,2,2,..) and that this was supposed to be fixed. Presumably it hasnt? Or am i missing a setting somewhere.

Second is just a suggestion. It seems tiny, but the X clear search button in amarok is really useful. In exaile if ive searched for Pearl Jam for example, I dont know if there's any other way to see the rest of my collection again without selecting the search term and deleting it manually.
.

Cheers

I don't think the two-disc issue has been resolved. In the meantime, you could just edit the album tag to add disc 1 or disc 2 to the end, alleviating the problem.

 If you install sexy-python it'll add a clear button to the search fields.

---

### Post by klep on 2007-03-31
thanks for the tip about sexy-python. Works a treat!

---

### Post by merlyn on 2007-03-31
> **reacocard said:**
> I don't think the two-disc issue has been resolved. In the meantime, you could just edit the album tag to add disc 1 or disc 2 to the end, alleviating the problem.

I made the earlier post regarding the 'double' album problem.

A bit of background on this; I made a post on the 'official' Exaile forums regarding this before the site underwent it's transformation. The response that I recieved was that it was being looked into and ought to be fixed in the 'next' release.

This was some time ago, and I'm sorry but I cannot remember the actual release number at the time.

My query on **this **thread, was intended to get an update on the progress of the problem.

Also to determine why Rhythmbox interpret, (perhaps 'parse' is a better term), the tag data correctly and Exaile not.

As far as editing the album tag data, I've attached an Easytag screen showing how I've entered the 'data' into the 'field' in question. 

Perhaps there is another 'format' I could use, as suggested above.

Cheers.

---

### Post by reacocard on 2007-03-31
> **merlyn said:**
> I made the earlier post regarding the 'double' album problem.

A bit of background on this; I made a post on the 'official' Exaile forums regarding this before the site underwent it's transformation. The response that I recieved was that it was being looked into and ought to be fixed in the 'next' release.

This was some time ago, and I'm sorry but I cannot remember the actual release number at the time.

My query on **this **thread, was intended to get an update on the progress of the problem.

Also to determine why Rhythmbox interpret, (perhaps 'parse' is a better term), the tag data correctly and Exaile not.

As far as editing the album tag data, I've attached an Easytag screen showing how I've entered the 'data' into the 'field' in question. 

Perhaps there is another 'format' I could use, as suggested above.

Cheers.

I just tested the multidisc thing, and I can confirm it doesn't work. At all. The best temporary solution is to take the songs' 'album' tag and append '(disc 1)', etc. to it. eg., "Random Album" becomes "Random Album (disc 1)". Not a perfect solution by any means, but it works.

---

### Post by merlyn on 2007-03-31
That seems a sensible enough work around.

It would be nice to see it working though at some point in the future.

Cheers

---

### Post by joshed_240sx on 2007-04-01
so does anybody know if Exaile will be in the list for Foxytunes anytime soon!

---

### Post by jseiser on 2007-04-04
how would one go about manually adding MTP to exhale?  I always wanted to learn to progam, so this would help by giving me an actually goal to accomplish.  I own a creative vision m, so i got one part covered :)

---

### Post by Drunner611 on 2007-04-04
This might seem like a dumb question, but can I use exaile in 64 ubuntu?

---

### Post by Kasper42 on 2007-04-04
> so does anybody know if Exaile will be in the list for Foxytunes anytime soon!


According to this thread it's in the pipeline. How long that will be, I have no idea!
[http://forums.foxytunes.com/viewtopic.php?t=2345&sid=d76728ef4dcfb1abfb5da3861b2695a2](http://forums.foxytunes.com/viewtopic.php?t=2345&sid=d76728ef4dcfb1abfb5da3861b2695a2)

---

### Post by reacocard on 2007-04-04
> **jseiser said:**
> how would one go about manually adding MTP to exaile?  I always wanted to learn to progam, so this would help by giving me an actually goal to accomplish.  I own a creative vision m, so i got one part covered :)

Well, it's just a plugin. Download the source and take a look at the existing ipod and mass storage drivers to see how they do it, it doesn't look hard. Thing is, you'll need a python library or python bindings to a C library for accessing MTP devices, and I don't think that exists yet, so you'd have to create one. There is a [libmtp]("http://libmtp.sourceforge.net/") C library (same one amarok uses), so if you could figure out how to make python bindings for that, you'd have everything you need.

If you need any help, don't be afraid to ask. I'll help if I can, and the programming talk section on these forums is also good. 

Python documentation (lots!): [http://docs.python.org/](http://docs.python.org/)

Good luck!

EDIT: It appears I spoke too soon: [https://launchpad.net/pylibmtp](https://launchpad.net/pylibmtp). Assuming those bindings are good, you won't have to deal with that at all, just with the plugin to bridge it to Exaile, a much easier task.

---

### Post by giacomolg on 2007-04-05
Hi, very nice player. I've only one major problem: even if I've installed gamin (with its python binding) I can't automatically update my collection.
And a request (maybe I'll post it on exaile website aswell): it will be wonderful to be able to search in all Artist, Album, Genre at the same time (see how Rhythmbox).

Hope the gamin issue is due my ignorance and will be easily solved.

Bye, Giacomo

---

### Post by reacocard on 2007-04-05
> **giacomolg said:**
> Hi, very nice player. I've only one major problem: even if I've installed gamin (with its python binding) I can't automatically update my collection.
And a request (maybe I'll post it on exaile website aswell): it will be wonderful to be able to search in all Artist, Album, Genre at the same time (see how Rhythmbox).

Hope the gamin issue is due my ignorance and will be easily solved.

Bye, Giacomo

Gamin support has been removed in 0.2.9 and later.

---

### Post by reacocard on 2007-04-05
> **Drunner611 said:**
> This might seem like a dumb question, but can I use exaile in 64 ubuntu?

Yep, but you'll have to compile it yourself, as there aren't any 64-bit packages yet.

---

### Post by giacomolg on 2007-04-05
> **reacocard said:**
> Gamin support has been removed in 0.2.9 and later.
thanks a lot...what does it mean exactly ? That Exaile doesn't support automatic update of the library? Or that I have to enable it in some other way? Or that it should be olready working fine?

bye

---

### Post by reacocard on 2007-04-05
> **giacomolg said:**
> thanks a lot...what does it mean exactly ? That Exaile doesn't support automatic update of the library? Or that I have to enable it in some other way? Or that it should be olready working fine?

There is no automatic updating, period. I don't like to see it go either, it was useful.

---

### Post by giacomolg on 2007-04-05
> **reacocard said:**
> There is no automatic updating, period. I don't like to see it go either, it was useful.
ok, I guess I'll stick with the good old rhythmbox and the power of its plugins.

---

### Post by x1a4 on 2007-04-06
> **synic said:**
> 
```

# sudo apt-get install python-gtk2 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
# wget http://www.exaile.org/files/exaile_0.2b4_i386.deb
# sudo dpkg -i exaile_0.2b4_i386.deb

```


No joy on install: can't find *libgstreamer0.10*--which repo is it in?  

Here's what I have: 

# ubuntu
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse universe main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# debian
# deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
# deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free
# deb [http://security.debian.org](http://security.debian.org) stable/updates main contrib non-free
deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
deb-src [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free

# clamav
deb [http://ftp2.de.debian.org/debian-volatile/](http://ftp2.de.debian.org/debian-volatile/) sarge/volatile main

# asher
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy main dupdate
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate

# tolero (xfce)
deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0 main
deb-src [http://ubuntu.tolero.org](http://ubuntu.tolero.org) edgy main

# seveas
deb [http://seveas.imbrandon.com/](http://seveas.imbrandon.com/) edgy-seveas extras custom
deb-src [http://seveas.imbrandon.com/](http://seveas.imbrandon.com/) edgy-seveas extras custom

# easyubuntu
# deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu

# postgresql
#    pgadmin
# deb [ftp://ftp5.ca.postgresql.org/postgresql/pgadmin/release/debian](ftp://ftp5.ca.postgresql.org/postgresql/pgadmin/release/debian) sarge pgadmin

# ntfs-3g
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all

# selinux
deb [http://www.coker.com.au/newselinux/](http://www.coker.com.au/newselinux/) ./

# ubuntu backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted

---

### Post by bahn on 2007-04-06
I can't wait to get home to try this. I love amarok but don't care for kde. So i have been waiting for a GTK media player like this for some time.

---

### Post by reacocard on 2007-04-06
> **x1a4 said:**
> No joy on install: can't find *libgstreamer0.10*--which repo is it in?  

<snip>

Those are *really* old instuctions, see Exaile's [Releases page]("http://www.exaile.org/trac/wiki/Releases") for up-to-date instructions.

---

### Post by x1a4 on 2007-04-06
> **reacocard said:**
> Those are *really* old instuctions, see Exaile's [Releases page]("http://www.exaile.org/trac/wiki/Releases") for up-to-date instructions.

Success!  Thank you.

---

### Post by x1a4 on 2007-04-06
> **x1a4 said:**
> Success!  Thank you.

Once again I celebrate too soon.  Installation went okay, but when I ran it I received the following error: 

```

 /usr/local/share/exaile/exaile.py
Traceback (most recent call last):
  File "/usr/local/share/exaile/exaile.py", line 2502, in ?
    main()
  File "/usr/local/share/exaile/exaile.py", line 2491, in main
    exaile = ExaileWindow(options, fr)
  File "/usr/local/share/exaile/exaile.py", line 112, in __init__
    self.settings = config.Config("%s%ssettings.ini" % (SETTINGS_DIR, os.sep))
  File "/usr/local/share/exaile/xl/config.py", line 250, in __init__
    self.config = XlConfigParser(loc)
  File "/usr/local/share/exaile/xl/config.py", line 50, in __init__
    converter = ConvertIniToConf(self, self.loc)
  File "/usr/local/share/exaile/xl/config_convert.py", line 97, in __init__
    v[1](setting, v[0])
  File "/usr/local/share/exaile/xl/config_convert.py", line 104, in conv_int
    self.settings.set_int(new_key, int(self.osettings[old_key]))
ValueError: invalid literal for int(): Top

```

WTF?

---

### Post by divisionbyzero on 2007-04-09
Anyone else getting a bit of crashes with exaile?

I'm on Feisty and I've just installed version 0.2.9 hoping it'll solve the frequent crashes I had with 0.2.8 but still no luck.

---

### Post by juanhunglow on 2007-04-09
> **divisionbyzero said:**
> Anyone else getting a bit of crashes with exaile?

I'm on Feisty and I've just installed version 0.2.9 hoping it'll solve the frequent crashes I had with 0.2.8 but still no luck.

I've been getting exaile 'crash' notifications since I started with Herd3. However, the program doesn't crash, it continues to work fine, i'm not sure what is crashing exactly.

Has anyone got and ipod working with exaile in feisty??  I'm still trying to figure that one out.

---

### Post by SishGupta on 2007-04-09
I compile exaile from svn and I don't get any crashes, however the ipod plugin doesn't load the songs on my ipod. The driver is enabled and works, but i just get a "connecting..." status message and that never changes.

---

### Post by divisionbyzero on 2007-04-10
> **juanhunglow said:**
> I've been getting exaile 'crash' notifications since I started with Herd3. However, the program doesn't crash, it continues to work fine, i'm not sure what is crashing exactly.


Yup. Those are what I'm getting - "crash notifications" but Exaile! still playing. It needs a "kill" from the CLI though to exit because the quit command doesn't work anymore.

---

### Post by rsm2296 on 2007-04-10
Finally got exaile working (Dapper) by following the above instructions for mutagen.oggvorbis support, and then editing MPC.py to look like the one for quodlibet.  Nice player - I'd prefer to swap out Amarok in favour of a gnome app.

As a classical music listener, a couple of change need to happen before I switch over, though.  Most importantly, composers are far more important than artists, so there needs to be a composers column in the playlist; also better ID3 tag editing.

Hopefully these changes are forthcoming - will stay tuned to further improvements of this great program.

---

### Post by reacocard on 2007-04-10
> **rsm2296 said:**
> Finally got exaile working (Dapper) by following the above instructions for mutagen.oggvorbis support, and then editing MPC.py to look like the one for quodlibet.  Nice player - I'd prefer to swap out Amarok in favour of a gnome app.

As a classical music listener, a couple of change need to happen before I switch over, though.  Most importantly, composers are far more important than artists, so there needs to be a composers column in the playlist; also better ID3 tag editing.

Hopefully these changes are forthcoming - will stay tuned to further improvements of this great program.

I searched [Exaile's Trac]("http://www.exaile.org/trac") for these for you, there's nothing on the Composer issue, so you might want to file a request for that, but for the tag editor there appears to be a fair bit of demand in [Ticket #4]("http://www.exaile.org/trac/ticket/4"), and also some in [Ticket #112]("http://www.exaile.org/trac/ticket/112"). There's no target set though, so don't expect it soon. In the meantime, I suggest Ex Falso as a superb standalone tag editor.

---

### Post by EvergreyNY on 2007-04-15
> **divisionbyzero said:**
> Anyone else getting a bit of crashes with exaile?

I'm on Feisty and I've just installed version 0.2.9 hoping it'll solve the frequent crashes I had with 0.2.8 but still no luck.


i haven't had it crash yet (im using feisty), but it is using 100mb+ of memory. seems quite high for any media player.

---

### Post by Takmadeus on 2007-04-15
Mr. Synic.... I congratulate you for your software.... I have used it and enyojed it a lot since I could try it.... everyday when I use this PC of mine.... but I would like to ask you if you could implement an automatic rating system (like the one in amarok) in a further release...

thanks and keep the good job!

---

### Post by guitarmaniac on 2007-04-15
Its nice, but I like amarok so much that this seems to pale in comparison.
I'd really like to see someone make a direct clone of amarok (in GTK), and THEN make it intigrate into GNOME.
Also its crashed on me a few times and the database seems slower than amarok (even running it in GNOME).
But then again, maybe I'm being too biased.
I'd like to see how this ends up in a few releases though.

---

### Post by divisionbyzero on 2007-04-19
Something strange with a fresh install of Ubuntu 7.04 Feisty and the .deb package from the exaile website.

Radio streaming doesn't work anymore. The station list shows but when I try to play one station, exaile just hangs - on the statusbar it says "loading stream sources. Please wait...".

I never had this problem with same .deb package but on Feisty beta with daily updates.

---

### Post by SyL on 2007-05-08
Hi Synic,
 just wanted to say that Exaile rules!!
Very good job, that's the best MP GTK based  :)

---

### Post by screaminj3sus on 2007-05-13
It won't let me add my lbrary, when I choose to import my library it starts scanning the files and then just freezes and stops responding.

---

### Post by reacocard on 2007-05-13
> **screaminj3sus said:**
> It won't let me add my lbrary, when I choose to import my library it starts scanning the files and then just freezes and stops responding.

Could you please run it from a terminal and give us the output? Also, what version are you using?

---

### Post by synic on 2007-05-14
> **Ultimo Aliento said:**
> Looks great !, i have a little problem adding my music folders with the library tool, the program say this :

[B]loading songs
Running is False
/home/seccion9/Shared
/home/seccion9/Compartidos
/home/seccion9/Incomplete
File count: 4
Traceback (most recent call last):
  File "/home/seccion9/exaile/xl/media.py", line 361, in read_tag
    audio = mad.MadFile(self.loc)
IOError: Object must have a read method
Traceback (most recent call last):
  File "/home/seccion9/exaile/xl/media.py", line 361, in read_tag
    audio = mad.MadFile(self.loc)
IOError: Object must have a read method
Count is now: 4
loading songs
Traceback (most recent call last):
  File "/home/seccion9/exaile/xl/librarychooser.py", line 85, in __OnRemove
    del self.items[indexes[0]]
IndexError: tuple index out of range
Running is False[/B]

Then, i just chose one folder, Exaile indexed one song (of two possible), and when i try to play the song, the program crash.

Keep working in this program! looks promising :D

You are running a VERY old version.  Updating to the latest may help :)

---

### Post by screaminj3sus on 2007-05-18
How can I run it from the terminal? I'm using .2.8 I installed it via synaptic.

---

### Post by Tenicus on 2007-05-18
just type in exaile

---

### Post by screaminj3sus on 2007-05-18
wow, it spouts ALOT of gibberish when importing, Had to zip the txt file.
[ATTACH]32916[/ATTACH]

---

### Post by reacocard on 2007-05-18
> **screaminj3sus said:**
> wow, it spouts ALOT of gibberish when importing, Had to zip the txt file.
[ATTACH]32916[/ATTACH]

Ouch!! That's not normal. Could you please upgrade to version 0.2.9 and try again? There's a deb on the [downloads page]("http://www.exaile.org/downloads").

---

### Post by screaminj3sus on 2007-05-19
excat same thing happens with .2.9, it freezes and the console spewes out the same gibberish

---

### Post by reacocard on 2007-05-19
> **screaminj3sus said:**
> excat same thing happens with .2.9, it freezes and the console spewes out the same gibberish

Odd. Try doing a 
```
rm -rf ~/.exaile
```
and trying again.

---

### Post by screaminj3sus on 2007-05-19
entered the command, ran exaile through the terminal again it asked me to import my library, and still the same results.

---

### Post by reacocard on 2007-05-19
> **screaminj3sus said:**
> entered the command, ran exaile through the terminal again it asked me to import my library, and still the same results.

Huh. Try running the command again, then skipping the library setup and just play some of the files directly. Do they all cause it to crash, or just some?

---

### Post by screaminj3sus on 2007-05-19
I can go to the files tab and open my music folder and play songs, and it does not crash. It only seems to crash importing my library. During the import it gets about a quarter of the way done on the progressbar and then just stops responding,I've tried leaving it but nothing happens.

---

### Post by reacocard on 2007-05-19
> **screaminj3sus said:**
> I can go to the files tab and open my music folder and play songs, and it does not crash. It only seems to crash importing my library.

Good! Now try adding subfolders of your music folder into Exaile's library one by one. If any of them cause it to crash, see if there's anything that sets it apart from the other files. In particular, look for unusual characters (Unicode) in the tag data. Exaile still has some trouble with that.

---

### Post by screaminj3sus on 2007-05-19
I added three artists successfully, it crashed adding Alice cooper, I could start playing it if I went to file, but exaile would eventually freeze. If I remove the alice cooper folder and add my library without it it works.
Now I'm just having some tag trouble, exaile puts some random songs that show up fine in their correct albums in other players as unknown(strange thing is the songs put as unknown have other songs from the SAME album that are grouped fine under the correct album.), when I try to edit the tags I get this (from terminal) I get an error from exaile that says unknown error.

on_save ( /usr/share/exaile/xl/track.py @ 421):
-----------------------
Traceback (most recent call last):
  File "/usr/share/exaile/xl/track.py", line 446, in on_save
    media.write_tag(track)
  File "/usr/share/exaile/xl/media/__init__.py", line 74, in write_tag
    formats[ext].write_tag(tr)
  File "/usr/share/exaile/xl/media/mp3.py", line 26, in write_tag
    id3 = mutagen.id3.ID3(tr.io_loc)
  File "/usr/lib/python2.5/site-packages/mutagen/id3.py", line 74, in __init__
    super(ID3, self).__init__(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/mutagen/__init__.py", line 39, in __init__
    self.load(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/mutagen/id3.py", line 136, in load
    for frame in self.__read_frames(data, frames=frames):
  File "/usr/lib/python2.5/site-packages/mutagen/id3.py", line 275, in __read_frames
    try: yield self.__load_framedata(tag, flags, framedata)
  File "/usr/lib/python2.5/site-packages/mutagen/id3.py", line 298, in __load_framedata
    return tag.fromData(self, flags, framedata)
  File "/usr/lib/python2.5/site-packages/mutagen/id3.py", line 984, in fromData
    raise ID3BadUnsynchData, '%s: %r' % (err, data)
ID3BadUnsynchData: string ended unsafe: 'Windows Media Player 9 Series\x00\xff'

If I could get these artists tagged correctly in exaile I would defiantly use it.

---

### Post by reacocard on 2007-05-19
> **screaminj3sus said:**
> I added three artists successfully, it crashed adding Alice cooper, I could start playing it if I went to file, but exaile would eventually freeze. If I remove the alice cooper folder and add my library without it it works.

Good, it's definitely something with certain files then. Keep trying different folders, and note which ones fail. Then go through the files within them one by one, to figure out exactly which are making it crash.

I'm going to bed now, but I'll check back in the morning. You might be able to get more help in [#exaile]("http://exaile.org/cgi-bin/cgiirc/irc.cgi") (ask for synic or sjohannes), but you'll likely have to wait a while before anyone notices you.

---

### Post by shen-an-doah on 2007-05-19
Seems very nice. Definitely cool to have something that blends better with Gnome than Amarok does. Unfortunately, the lack of the context menu (the suggested songs, ratings, etc), keyboard shortcuts not working properly and the fact I couldn't get the cover art patch to work, means I'm sticking with Amarok for now...

---

### Post by Gen2ly on 2007-05-19
Definitely theres a few errors in it.  I really like it though.  Just discovered that radio streams won't save when they are playing.  Oh and the icons awesome.

---

### Post by rjcsc on 2007-05-21
> **synic said:**
> Well, actually, I've convinced a girl that she needs to let me borrow hers.  I'll be getting it tonight, so we'll see what happens.

Any news about MTP support?

---

### Post by synic on 2007-05-21
> **rjcsc said:**
> Any news about MTP support?

Yup.  [http://exaile.org/trac/ticket/489](http://exaile.org/trac/ticket/489)

---

### Post by Technoviking on 2007-05-24
I'm trying and loving Exaile, all ready switched from Rhythmbox mostly. The one feature that is lacking is support  of playing m3u streams.  I hope they plan to add this feature.

Mike

---

### Post by synic on 2007-05-24
> **Mike said:**
> I'm trying and loving Exaile, all ready switched from Rhythmbox mostly. The one feature that is lacking is support  of playing m3u streams.  I hope they plan to add this feature.

Mike

This should work.  What stream are you trying to play?

---

### Post by prince_alfie on 2007-05-24
> **synic said:**
> I released Exaile 0.2b2 today.  I really like Amarok, but I was hoping for a gtk+ alternative, so I started Exaile.  I know ... I know, there are tons of media players out there, but I see this as a fun way to learn python and gtk+.

Some screenshots can be found here:

[http://www.exaile.org](http://www.exaile.org)

It's beta, but if you're bored, check it out.  Here's what you'll need to do:

```

# sudo apt-get install python-gtk2 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
# wget http://www.exaile.org/files/exaile_0.2b4_i386.deb
# sudo dpkg -i exaile_0.2b4_i386.deb

```

.. and a new icon will show up in Applications->Sound and Video

Go to Tools->Library Manager, add your music directory, and away you go.

Optional:  If you want mp3 support, install gstreamer0.10-plugins-ugly, and if you want wma, install gstreamer0.10-ffmpeg

Feedback and comments are appreciated!

-synic

Thanks for the link... I really like this idea! :D

---

### Post by Technoviking on 2007-05-24
> **synic said:**
> This should work.  What stream are you trying to play?
BinRev Radio
[http://www.ddphackradio.org/stream.m3u](http://www.ddphackradio.org/stream.m3u)

---

### Post by urukrama on 2007-05-24
That m3u works absolutely fine on exaile here, Mike.

---

### Post by Technoviking on 2007-05-24
> **urukrama said:**
> That m3u works absolutely fine on exaile here, Mike.

I'm hit the + sign on the radio tab to add the stream, then double clicking on the added station to play.

Mike

---

### Post by robertpolson on 2007-05-27
Does Exaile support writing music to ipod ?

So far I only managed to read, but not write.

---

### Post by DJ Wings on 2007-05-27
Exaile integrates well with an XFCE desktop, in my experience. It's a great media playback program, but for a lighter-weight app, you want Xfmedia.

---

### Post by reacocard on 2007-05-27
> **robertpolson said:**
> Does Exaile support writing music to ipod ?

So far I only managed to read, but not write.

It's supposed to, but it appears to be a bit buggy ATM: [http://www.exaile.org/trac/ticket/433](http://www.exaile.org/trac/ticket/433)

---

### Post by Kuraudo on 2007-05-30
I would just like to say that this player is really great. Has everything I want from a player.

But I had some problems installing it on my amd64 system. I found an old version 2.5.x that was converted into a .deb package. I was just wondering, how do I install a i386 software on a x86_64 system? Because the latest version would be nice.

---

### Post by reacocard on 2007-05-30
> **Kuraudo said:**
> I would just like to say that this player is really great. Has everything I want from a player.

But I had some problems installing it on my amd64 system. I found an old version 2.5.x that was converted into a .deb package. I was just wondering, how do I install a i386 software on a x86_64 system? Because the latest version would be nice.

Just compile it from source, Exaile's really easy to do. Grab the latest tarball, extract it somewhere, open a terminal in that folder, and then enter these commands:
```
sudo apt-get install build-essential python-dev gstreamer0.10-plugins-good python-gst0.10 python python-gtk2 python-glade2 python-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree
make
sudo make install
```

---

### Post by Ocxic on 2007-05-30
"sudo dpkg -i --force-archetecture your_pakage.deb" will work, but I'm fairly certain there is a 64bnit version out there, try using automatix.

the spelling for that command may be wrong, i dunno how to spell archatechture

---

### Post by reacocard on 2007-05-30
> **Ocxic said:**
> "sudo dpkg -i --force-archetecture your_pakage.deb" will work, but I'm fairly certain there is a 64bnit version out there, try using automatix.

the spelling for that command may be wrong, i dunno how to spell archatechture

It'd work, but it's still not a good idea. Exaile is mostly python for which it doesn't matter, but the multimedia keys support is C so you'd want to have that built properly for 64-bit.

---

### Post by voodoochild on 2007-06-04
Hey guys....

Really digging Exaile, having a gnome media player comparable to amarok is awesome.... Thankyou kindly for all the good work.

Quick question though... having patched for the updated amazon-thingermajiger, is there a way to force exaile to fetch album art from scratch again? (i'm missing loads of covers as they were attempted before the patch...)


regards,

Luke

---

### Post by voodoochild on 2007-06-04
Also, just as an side note... by far the the coolest thing about exaile is that when select information, for example, on Pelican, i get this:

> [SIZE="5"]Pelican[/SIZE]
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/94/75923093.lOoJxWty.jpg/240px-75923093.lOoJxWty.jpg[/IMG]
A **pelican** is any of several very large water birds with a distinctive pouch under the beak belonging to the bird family **Pelecanidae.** Along with the darters, cormorants, gannets, boobies, frigatebirds, and tropicbirds, it makes up the order Pelecaniformes. Like other birds in that group, pelicans have all four toes webbed (they are totipalmate). Modern pelicans are found on all continents except Antarctica. They are birds of inland and coastal waters and are absent from polar regions, the deep ocean, oceanic islands, and inland South America.


Please never change.....


Luke

---

### Post by reacocard on 2007-06-04
> **voodoochild said:**
> Hey guys....

Really digging Exaile, having a gnome media player comparable to amarok is awesome.... Thankyou kindly for all the good work.

Quick question though... having patched for the updated amazon-thingermajiger, is there a way to force exaile to fetch album art from scratch again? (i'm missing loads of covers as they were attempted before the patch...)


regards,

Luke

Close Exaile and run this in a terminal:
```
rm -r ~/.exaile/covers/
```
Now Exaile will refetch art as normal, or you can do them all at once with the 'Album Art Collector' in the tools menu.

---

### Post by QwUo173Hy on 2007-06-04
This doesn't work for me (0.2.9). The Collector says "0 Covers left to collect". I can do them indivdually by dragging a track from each album into the playlist and using the context menu on the information area up top.

---

### Post by reacocard on 2007-06-04
> **jarlath said:**
> This doesn't work for me (0.2.9). The Collector says "0 Covers left to collect". I can do them indivdually by dragging a track from each album into the playlist and using the context menu on the information area up top.

Ok, then do this one too:
```
rm ~/.exaile/music.db
```
Note that this will also erase any ratings and playlists you have.

---

### Post by QwUo173Hy on 2007-06-04
Thanks, that did the trick!

---

### Post by voodoochild on 2007-06-04
Sorted for me too... thankyou muchly!

---

### Post by synic on 2007-06-04
This is a less destructive way:

```

echo "update albums set image=NULL where image='nocover';" | sqlite3 ~/.exaile/music.db

```

..... assuming you've installed sqlite3.

---

### Post by voodoochild on 2007-06-05
och well.... too late now.......

---

### Post by zgerrz on 2007-06-05
I'm using the latest SVN version of exaile, and I cannot get the function --play to work when configuring my multimedia keys using keytouch.

I started with the latest stable version of exaile, but whenever i use 'exaile --play' for my play/pause key, it simply restarts to the beginning of the song. The SVN version is no different.

Any advice?

---

### Post by reacocard on 2007-06-05
> **zgerrz said:**
> I'm using the latest SVN version of exaile, and I cannot get the function --play to work when configuring my multimedia keys using keytouch.

I started with the latest stable version of exaile, but whenever i use 'exaile --play' for my play/pause key, it simply restarts to the beginning of the song. The SVN version is no different.

Any advice?

Good catch on that bug. It should now be fixed in SVN as of revision 2520.

---

### Post by zgerrz on 2007-06-05
Works perfectly now with the latest version. Thanks a lot.

---

### Post by zgerrz on 2007-06-07
It appears to be broken again in version 0.2.10-svn2532

---

### Post by reacocard on 2007-06-07
> **zgerrz said:**
> It appears to be broken again in version 0.2.10-svn2532

Yeah, turns out that --play-pause had been implemented for that, but the man page hadn't been updated. The man page is now correct, and you should use --play-pause instead of --play.

---

### Post by zgerrz on 2007-06-08
OK thanks, it works great again.

---

### Post by woodsmoke on 2007-06-08
how about we talk?
IRC or something or just here?
woodsmoke

---

### Post by reacocard on 2007-06-08
> **woodsmoke said:**
> how about we talk?
IRC or something or just here?
woodsmoke

Just stop by #exaile on freenode.

---

### Post by jugendstil on 2007-06-09
i get this output:

/usr/share/exaile/xl/xlmisc.py:1717: GtkWarning: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
  pixmap.set_colormap(colormap)
/usr/share/exaile/xl/xlmisc.py:1740: GtkWarning: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
  pixmap.draw_layout(gc, x, y, layout)
/usr/share/exaile/xl/xlmisc.py:1740: GtkWarning: No colormap in gc_get_foreground
  pixmap.draw_layout(gc, x, y, layout)
/usr/share/exaile/xl/xlmisc.py:1744: GtkWarning: gdkpixbuf-drawable.c:1255: Depth of the source drawable is 24 where as the visual depth of the colormap passed is 16
  0, width, height)
Traceback (most recent call last):
  File "exaile.py", line 2646, in <module>
    main()
  File "exaile.py", line 2638, in main
    exaile = ExaileWindow(options, fr)
  File "exaile.py", line 202, in __init__
    self.setup_left()
  File "exaile.py", line 1031, in setup_left
    self.collection_panel = panels.CollectionPanel(self)
  File "/usr/share/exaile/xl/panels.py", line 237, in __init__
    self.setup_widgets()
  File "/usr/share/exaile/xl/panels.py", line 259, in setup_widgets
    self.create_popup()
  File "/usr/share/exaile/xl/panels.py", line 354, in create_popup
    icon_set = gtk.IconSet(pixbuf)
TypeError: pixbuf should be a GdkPixbuf


can anybody help me? this has happened with the last 4 svns

---

### Post by jugendstil on 2007-06-11
anybody?

please help!!!

---

### Post by robertpolson on 2007-06-11
With the latest SVN release, how do I put music on to ipod? I have it connected and all plugins are installed, but how do I actually put music to ipod ?

Edit: Found it "well.. thats one of the nasty things of the ipod plugin

you must select your titles you want to have on your iPod drag them over the *devices*-tab.. wait till it swaps.. and then drop it there

this is really going on my nreves.. but well.. better than none
"

[http://www.exaile.org/trac/ticket/433#comment:12](http://www.exaile.org/trac/ticket/433#comment:12)

---

### Post by henriquemaia on 2007-06-12
Is there a way to startup exaile minimized on tray? This is very useful when the computer starts and exaile is on the startup programs list.

---

### Post by reacocard on 2007-06-12
> **henriquemaia said:**
> Is there a way to startup exaile minimized on tray? This is very useful when the computer starts and exaile is on the startup programs list.

Not that I know of, but it shouldn't be too hard to add.

---

### Post by henriquemaia on 2007-06-12
> **reacocard said:**
> Not that I know of, but it shouldn't be too hard to add.

Thanks for you reply. That’s a must have (IMHO).
Exaile is a great player, nonetheless.

Other thing: I have the latest build installed and the the resume plugin doesn’t work. Any ideas why this happens? (I select it from the plugins menu and when exaile is restarted, the plugin is always unchecked).

Also, is there a way to import playlists? Amarok has a tool for that and I don’t find anything similar in exaile.

Thanks.

---

### Post by reacocard on 2007-06-12
> **henriquemaia said:**
> Thanks for you reply. That’s a must have (IMHO).
Exaile is a great player, nonetheless.

Other thing: I have the latest build installed and the the resume plugin doesn’t work. Any ideas why this happens? (I select it from the plugins menu and when exaile is restarted, the plugin is always unchecked).

Also, is there a way to import playlists? Amarok has a tool for that and I don’t find anything similar in exaile.

Thanks.

The resume plugin works fine for me. Do you have the latest version of the plugin? It should be 0.2.  AFAIK, there isn't a way to import playlists, but you're right, there should be.  You can [get an account]("http://www.exaile.org/trac/register") on[ Exaile's Trac]("http://www.exaile.org/trac") and [submit your feature requests]("http://www.exaile.org/trac/newticket") yourself, or if you don't want to bother with that, I can submit them for you.

---

### Post by henriquemaia on 2007-06-13
> **reacocard said:**
> The resume plugin works fine for me. Do you have the latest version of the plugin? It should be 0.2.  AFAIK, there isn't a way to import playlists, but you're right, there should be.  You can [get an account]("http://www.exaile.org/trac/register") on[ Exaile's Trac]("http://www.exaile.org/trac") and [submit your feature requests]("http://www.exaile.org/trac/newticket") yourself, or if you don't want to bother with that, I can submit them for you.

Thanks for your support. I would appreciate if you submitted the request, since I&#8217;m not familiar with that. If you could also add the start hidden on tray feature also, it would be awesome. Thanks a lot for this.

About the resume playing plugin, I have the 0.2 version installed and exaile 0.2.8, running on Ubuntu feisty amd64. The plugin does not work nor it remains checked upon exaile restart. Thanks.

---

### Post by reacocard on 2007-06-13
> **henriquemaia said:**
> Thanks for your support. I would appreciate if you submitted the request, since I&#8217;m not familiar with that. If you could also add the start hidden on tray feature also, it would be awesome. Thanks a lot for this.

About the resume playing plugin, I have the 0.2 version installed and exaile 0.2.8, running on Ubuntu feisty amd64. The plugin does not work nor it remains checked upon exaile restart. Thanks.

Ok, playlist import request filed: [http://www.exaile.org/trac/ticket/591](http://www.exaile.org/trac/ticket/591)
I'll try to get the start minimized option done today.

As for the resume plugin, you should upgrade Exaile to 0.2.9 (or even SVN), plugins usually work best with the latest version of Exaile.

EDIT: --start-minimized option is in SVN as of r2557, enjoy!

---

### Post by henriquemaia on 2007-06-13
> **reacocard said:**
> Ok, playlist import request filed: [http://www.exaile.org/trac/ticket/591](http://www.exaile.org/trac/ticket/591)
I'll try to get the start minimized option done today.

As for the resume plugin, you should upgrade Exaile to 0.2.9 (or even SVN), plugins usually work best with the latest version of Exaile.

EDIT: --start-minimized option is in SVN as of r2557, enjoy!

First of all, thanks a lot for posting the request. 

Also, I have installed a newer version (Exaile 0.2.11svn) and resume playing is now working. I just love it. Exaile&#8217;s resume playing works even better than Amarok&#8217;s (in my particular case), so I&#8217;m really thrilled by this. And it&#8217;s great to have exail starting up minimized - great work!

I have now elected exaile as my music player. Thanks for all the help.

---

### Post by reacocard on 2007-06-13
> **henriquemaia said:**
> First of all, thanks a lot for posting the request. 

Also, I have installed a newer version (Exaile 0.2.11svn) and resume playing is now working. I just love it. Exaile’s resume playing works even better than Amarok’s (in my particular case), so I’m really thrilled by this. And it’s great to have exail starting up minimized - great work!

I have now elected exaile as my music player. Thanks for all the help.

Glad you like it! Also, it's worth noting that (as I found out after filing the request), the 'Open Media' option supports playlists (m3u at least, I think pls support is still buggy) as well. We're now discussing renaming the menu items to create less confusion in the future.

---

### Post by henriquemaia on 2007-06-14
> **reacocard said:**
> Glad you like it! Also, it's worth noting that (as I found out after filing the request), the 'Open Media' option supports playlists (m3u at least, I think pls support is still buggy) as well. We're now discussing renaming the menu items to create less confusion in the future.

I read that on the request, thanks. 

I wouldn’t have guessed that by the name "open media". Anyway, I was more like wanting a feature that imported all my playlists at once, so that I choose them later on the playlists tab. If you try that on Amarok, you understand what I mean.

---

### Post by reacocard on 2007-06-14
> **henriquemaia said:**
> I read that on the request, thanks. 

I wouldn’t have guessed that by the name "open media". Anyway, I was more like wanting a feature that imported all my playlists at once, so that I choose them later on the playlists tab. If you try that on Amarok, you understand what I mean.

Ah, I see, a 'bulk import'. I'll mention that on the feature request.

---

### Post by henriquemaia on 2007-06-14
> **reacocard said:**
> Ah, I see, a 'bulk import'. I'll mention that on the feature request.

Yes, precisely that. Thanks.

A side note: I have shown exaile to my girlfriend and she loved it. Now she’s also using it.

---

### Post by henriquemaia on 2007-06-15
Is there any way of removing the size column of the file browser (files tab)?

---

### Post by reacocard on 2007-06-15
> **henriquemaia said:**
> Is there any way of removing the size column of the file browser (files tab)?

I don't think so

---

### Post by hidey on 2007-06-29
Erm ,is it just me or are the Custom playlists and Smart playlists not arrangede by name? And you can't freely drag them around to your liking either. I've got the 0.2.10.

---

### Post by Gen2ly on 2007-06-29
I think it's perfect exaile.  I recently installed 2.10 and it gets better.  Visit my blog if you want additional information.

---

### Post by Weav on 2007-07-02
Thanks for this program, runs awesome and is just what I need.

---

### Post by rjcsc on 2007-07-02
> **Dirk.R.Gently said:**
> I think it's perfect exaile.  I recently installed 2.10 and it gets better.

I still miss MTP devices support... Rhythmbox 0.11.1 now has.

---

### Post by racoq on 2007-07-02
Hi

I recently installed Listen, and i didn't like it (come from a long history of winamp, xmms, etc..) i wanted a player that would integrate well with shoutcast, since was not usable in terms of connecting to any radio station.

However Listen gave me the following issues

- it is way slow / sluggish
- Shoutcast integration sucks :P (not to flexible)
- don't have a Stop button

As i installed Exaile, i was amazed, by its quality, and the above issues got adressed. 
Exaile its a fine piece of music player. I also enjoyed the intuitive interface.

Please keep the development. Don't let this project die, as many great projects i have seen in the years turned into dust.

Just one question all your hard work and costs maintaining could be self provided by  donations. Any chance you guys include a paypal account in order for people to contribute to your project?

Best regards

---

### Post by GMU_DodgyHodgy on 2007-07-02
Excellent Application. 

Keeps the traditional clean lines of a Gnome GTK+ aplication with just the right amount of additional functionality to make me switch from RhythmBox. 

Well done sir!!  :D

---

### Post by reacocard on 2007-07-02
> **racoq said:**
> Hi

I recently installed Listen, and i didn't like it (come from a long history of winamp, xmms, etc..) i wanted a player that would integrate well with shoutcast, since was not usable in terms of connecting to any radio station.

However Listen gave me the following issues

- it is way slow / sluggish
- Shoutcast integration sucks :P (not to flexible)
- don't have a Stop button

As i installed Exaile, i was amazed, by its quality, and the above issues got adressed. 
Exaile its a fine piece of music player. I also enjoyed the intuitive interface.

Please keep the development. Don't let this project die, as many great projects i have seen in the years turned into dust.

Just one question all your hard work and costs maintaining could be self provided by  donations. Any chance you guys include a paypal account in order for people to contribute to your project?

Best regards

Glad you like it. :D As for Paypal, I'll run the idea by synic, maybe he'll add it.

---

### Post by total wormage on 2007-07-03
after weeks of enjoying exaile i ran into this, exaile wouldn't load.
```
worm@wormage:~$ exaile&
[1] 6003
worm@wormage:~$ Traceback (most recent call last):
  File "exaile.py", line 69, in <module>
    from xl import *
  File "/home/worm/Desktop/exaile_0.2.10/xl/tracks.py", line 18, in <module>
  File "/home/worm/Desktop/exaile_0.2.10/xl/media/__init__.py", line 1, in <module>
  File "/home/worm/Desktop/exaile_0.2.10/xl/media/mp3.py", line 1, in <module>
ImportError: No module named mutagen

```

i figured it had something to do with the 'apt-get autoremove' i ran yesterday because it removed some python packages. so i installed python-mutagen (again) and exaile did not complain. everything works again
i wonder why apt thought it could remove that package.. because when i run it again now 'python-mutagen' doesn't get uninstalled.

i installed too much interesting things over the past few days, there is no way to trace back what package could have made this one 'not necessary'

i hope this post is in some way valuable for someone :]
and i really like exaile! :D

---

### Post by andrewsomething on 2007-07-03
I've been using Exaile for awhile and am extremely excited about its direction. I'm a dedicated Gnome user for better or worse, and I'd love to get rid of Amarok completely, and Exaile is very close!

Just a couple random thoughts for discussion:

One thing I miss when using Exaile and not Amarok is its support of Various Artist albums. Maybe it's just a personal thing, but I like having those listed separately.

Another is Amarok's ability to manage files by right clicking on them. It's very convenient to be able to organize your music directory automatically like that. For instance, I usually down load thing straight to the desk top. With Amarok I can simply right click on a recently added album in my collection an it is moved to the directory with the rest of my music and put into the same sort of file hierarchy.   (Probably a bit complicated, but a lot of it could be ported from Amarok. Of course I say this with being able to code at all, so I have no real idea what I'm talking about. :wink:)

PS: Man, Reacocard, you seem to be involved in most of the projects that I'm excited about! :p

---

### Post by QwUo173Hy on 2007-07-03
I'm also a big fan of this app. From the usability side of things - I have a question / request.

Instead of browsing artists / albums by strings of text, could you include a tab where I can browse by album cover? I think a lot of people find the visual index more usable. Personally, I have difficulty finding things in text compared to when I have a purely graphical index - even when the text is alphabetized.

Windows Media player has something similar to this and I like the idea a lot.

---

### Post by reacocard on 2007-07-03
> **andrewsomething said:**
> I've been using Exaile for awhile and am extremely excited about its direction. I'm a dedicated Gnome user for better or worse, and I'd love to get rid of Amarok completely, and Exaile is very close!

Just a couple random thoughts for discussion:

One thing I miss when using Exaile and not Amarok is its support of Various Artist albums. Maybe it's just a personal thing, but I like having those listed separately.

Another is Amarok's ability to manage files by right clicking on them. It's very convenient to be able to organize your music directory automatically like that. For instance, I usually down load thing straight to the desk top. With Amarok I can simply right click on a recently added album in my collection an it is moved to the directory with the rest of my music and put into the same sort of file hierarchy.   (Probably a bit complicated, but a lot of it could be ported from Amarok. Of course I say this with being able to code at all, so I have no real idea what I'm talking about. :wink:)

PS: Man, Reacocard, you seem to be involved in most of the projects that I'm excited about! :p

The Various Artists thing in Amarok is a dirty hack. I've looked at the code, and I really would prefer to find a better way to implement it in Exaile, it's that bad. A way of marking tracks as 'part of a compilation' would work, but I'm not sure how hard to implement that would be.

The directory structure sorting is perfectly doable (and pretty easy too!), you should file a feature request for it in Exaile's Trac (if there isn't one already). Tell me the ticket number once you've done so and I'll put it on my to-do list.

> **jarlath said:**
> I'm also a big fan of this app. From the usability side of things - I have a question / request.

Instead of browsing artists / albums by strings of text, could you include a tab where I can browse by album cover? I think a lot of people find the visual index more usable. Personally, I have difficulty finding things in text compared to when I have a purely graphical index - even when the text is alphabetized.

Windows Media player has something similar to this and I like the idea a lot.

There's already a ticket for something similar: [http://www.exaile.org/trac/ticket/145](http://www.exaile.org/trac/ticket/145)

---

### Post by Gen2ly on 2007-07-04
> **jarlath said:**
> I'm also a big fan of this app. From the usability side of things - I have a question / request.

Instead of browsing artists / albums by strings of text, could you include a tab where I can browse by album cover? I think a lot of people find the visual index more usable. Personally, I have difficulty finding things in text compared to when I have a purely graphical index - even when the text is alphabetized.

Windows Media player has something similar to this and I like the idea a lot.

I like this idea!  Visual clues are much nicer.  I like 0.2.10, very nice.

---

### Post by QwUo173Hy on 2007-07-04
> **Reacocard]There's already a ticket for something similar: [http://www.exaile.org/trac/ticket/145](http://www.exaile.org/trac/ticket/145)[/QUOTE]

That's great, and the mock-up looks good

[QUOTE=Dirk.R.Gently said:**
> I like this idea!  Visual clues are much nicer.  I like 0.2.10, very nice.

I think so too. The way WMP11 stacks up the artists albums makes searching not only visual (which is more efficient in itself) but improves on speed again by cutting down the amount of albums you have to look through.

I tried to make something similar a few years ago, but I had no real knowledge of GUI programming and found it a bit of a chore on my own. Here's a[ pic of the app]("http://www24.brinkster.com/jreidy/") I made (just for fun!)

---

### Post by andrewsomething on 2007-07-04
> **reacocard said:**
> 
The directory structure sorting is perfectly doable (and pretty easy too!), you should file a feature request for it in Exaile's Trac (if there isn't one already). Tell me the ticket number once you've done so and I'll put it on my to-do list.

I didn't see any thing similar so I went ahead and added it. Ticket #663 "[Feature Request] manage directory structure" has been filed. 

Keep up the awesome work!

---

### Post by Dgurion on 2007-07-04
I dont know if this has been mentioned/implement (I havent found a way to do it yet), but it would be really awesome if you could set custom Album images for the whole album instead of one song at a time..

---

### Post by reacocard on 2007-07-05
> **Dgurion said:**
> I dont know if this has been mentioned/implement (I havent found a way to do it yet), but it would be really awesome if you could set custom Album images for the whole album instead of one song at a time..

It should automatically work across the whole album if you set it for one song in that album, the exception being compilation albums, which Exaile doesn't yet handle gracefully.

---

### Post by RR1991 on 2007-07-05
I really love exaile, no more Amarok here! To bad there's still an old version in the repo, so I needed to add exaile's own repo. 

I don't know all the functions yet, but in Listen there's a nice page which shows the most played songs, favourite album an something else which I can't remember. Favourite Albums is a very handy app, because it makes playlists himself. Maybe you can take a look at it?

Anyway, I'll keep using exaile, doesn't eat so many of my RAM's too:D

---

### Post by reacocard on 2007-07-05
> **RR1991 said:**
> I really love exaile, no more Amarok here! To bad there's still an old version in the repo, so I needed to add exaile's own repo. 

I don't know all the functions yet, but in Listen there's a nice page which shows the most played songs, favourite album an something else which I can't remember. Favourite Albums is a very handy app, because it makes playlists himself. Maybe you can take a look at it?

Anyway, I'll keep using exaile, doesn't eat so many of my RAM's too:D

There are built-in smart playlists for 'most played' and 'highest rated', but they go by song rather than album. It would be an interesting feature though, you should file a request to have smart playlists that can go by albums instead of songs.

---

### Post by cdiem on 2007-07-05
Usually I'm an rhythmbox user, but I'm also keeping an eye on Exaile, which from many months I consider a very promising music application. If I may add a request (not sure though if here is the place for this), one thing I still miss in Exaile is the "find as you type" function, that for instance is present in rhythmbox and nautilus. It is, if you just start typing something in a focused window, the program takes you to the filename (and it is not case sensitive!), without the need of further searching; that's one of my favourite gnome features, and I'd like to see it implemented in such  nice music application like Exaile. I still remain a rhythbox user, but I think I'm going to change my mind in favor to Exaile, if it keeps being developed the way it does now. Great job!

---

### Post by walkerk on 2007-07-05
can it connect to mtp devices?

---

### Post by loserboy on 2007-07-05
I've been using Exaile! for a while, but just thought I'd say thanks for a great program, it's just what I wanted.

---

### Post by ScreamingNoises on 2007-07-07
First of all, i've been trying to find a great player like this one for months and this one is the best one i've ever found...

But now, exaile has stopped scrobbling, the error message is this one:
```
[13:25:57] Attempting to submit track 05. Friend Of A Friend from In Your Honor: Two by Foo Fighters to last.fm
[13:25:57] -----------------------
[13:25:57]  submit_to_scrobbler ( /usr/share/exaile/xl/audioscrobbler.py @ 7):
[13:25:57] -----------------------
[13:25:57] Traceback (most recent call last):
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 25, in submit_to_scrobbler
[13:25:57]     album=tr.album)
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 762, in posttrack
[13:25:57]     self.post()
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 821, in post
[13:25:57]     self.auth()
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 669, in auth
[13:25:57]     raise AudioScrobblerHandshakeError(msg)
[13:25:57] AudioScrobblerHandshakeError: AudioScrobblerHandshakeError: Tried to reauthenticate too soon after last try (last try at 2007-07-07 12:19:11)
[13:25:57] 
```

I've already updated to the new version, and made a clean install and it is still not scrobbling...

---

### Post by Delirious on 2007-07-07
Is there anyway of installing exaile 2.10 on feistyamd64, all thats in the repos is 2.8 :( 

I downloaded 2.10 deb but it gives me a libc6 dependancy error. When i go to install libc6 2.5.5 it gives me an error that it conflicts with tzdata.

Is there anyway to get it working on feisty amd64?

---

### Post by reacocard on 2007-07-07
> **Delirious said:**
> Is there anyway of installing exaile 2.10 on feistyamd64, all thats in the repos is 2.8 :( 

I downloaded 2.10 deb but it gives me a libc6 dependancy error. When i go to install libc6 2.5.5 it gives me an error that it conflicts with tzdata.

Is there anyway to get it working on feisty amd64?

You'll have to compile it from source. This is quite easy, just download the source package from the site and extract it somewhere. Open a terminal in the source dir and enter
```
sudo apt-get build-dep exaile
sudo apt-get remove exaile
make
sudo make install
```

If you want to remove Exaile at some later point, open a terminal in that same folder and enter
```
sudo make uninstall
```

I will hopefully be getting a 64-bit comp in a month or so, when I do, I will start providing 64-bit packages for all Exaile releases. Until then, you just have to do this.

---

### Post by Ralob on 2007-07-07
I just switched over to Exaile and I adore it. Awesome work :D

---

### Post by Delirious on 2007-07-08
Thanks!


> **reacocard said:**
> You'll have to compile it from source. This is quite easy, just download the source package from the site and extract it somewhere. Open a terminal in the source dir and enter
```
sudo apt-get build-dep exaile
sudo apt-get remove exaile
make
sudo make install
```

If you want to remove Exaile at some later point, open a terminal in that same folder and enter
```
sudo make uninstall
```

I will hopefully be getting a 64-bit comp in a month or so, when I do, I will start providing 64-bit packages for all Exaile releases. Until then, you just have to do this.

---

### Post by ScreamingNoises on 2007-07-10
> **ScreamingNoises said:**
> First of all, i've been trying to find a great player like this one for months and this one is the best one i've ever found...

But now, exaile has stopped scrobbling, the error message is this one:
```
[13:25:57] Attempting to submit track 05. Friend Of A Friend from In Your Honor: Two by Foo Fighters to last.fm
[13:25:57] -----------------------
[13:25:57]  submit_to_scrobbler ( /usr/share/exaile/xl/audioscrobbler.py @ 7):
[13:25:57] -----------------------
[13:25:57] Traceback (most recent call last):
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 25, in submit_to_scrobbler
[13:25:57]     album=tr.album)
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 762, in posttrack
[13:25:57]     self.post()
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 821, in post
[13:25:57]     self.auth()
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 669, in auth
[13:25:57]     raise AudioScrobblerHandshakeError(msg)
[13:25:57] AudioScrobblerHandshakeError: AudioScrobblerHandshakeError: Tried to reauthenticate too soon after last try (last try at 2007-07-07 12:19:11)
[13:25:57] 
```

I've already updated to the new version, and made a clean install and it is still not scrobbling...


Problem kind of solved:p
I think that the problem is this:
I've extracted some cd's with soundjuicer, and the tags of the music from  this cd were "music bleh.mp3" for example (I didn't had yet noticed the .mp3 termination), and when audioscrobbler from exaile tried to send the information regarding this music the last.fm rejected it... 
But what was bothering me was that i couldn't submit some musics that once had been submited...
My guess is that when Exaile tried to submit several incorrect musics, last.fm canceled my rights of scrobbling for awhile...
This is my theory ;)

Anyway, just deleted the termination and now it's scrobbling smoothly.
Great program BTW:D

---

### Post by Delirious on 2007-07-12
exaile is nice, i like it better than amarok but the BIGGEST thing i miss in any must player in linux is .cue sheet support for flac files. Foobar handled them beautifully in windows but there isnt a player i have found that handles them correctly.

I would hate to have to redo my music collection just to be able to move around to different tracks in a flac image file.

---

### Post by zgerrz on 2007-07-12
Don't know if this is being addressed, but I'm using the SVN versions of exaile and for about a week the ability of pausing the playlist by middle clicking on the tray icon has removed.

It was previously possible to pause the playing by middle clicking. Can you restore this functionality in the SVN version of exaile?

---

### Post by reacocard on 2007-07-12
> **Delirious said:**
> exaile is nice, i like it better than amarok but the BIGGEST thing i miss in any must player in linux is .cue sheet support for flac files. Foobar handled them beautifully in windows but there isnt a player i have found that handles them correctly.

I would hate to have to redo my music collection just to be able to move around to different tracks in a flac image file.

I believe this has been requested before, but noone has worked much on it AFAIK.

> **zgerrz said:**
> Don't know if this is being addressed, but I'm using the SVN versions of exaile and for about a week the ability of pausing the playlist by middle clicking on the tray icon has removed.

It was previously possible to pause the playing by middle clicking. Can you restore this functionality in the SVN version of exaile?

It works fine for me in latest svn.

---

### Post by skrribble on 2007-07-12
hey... im having trouble making a playlist and then putting the playist on my iPod.... i tried just creating the playlist on the iPod to start, but then it wont let me save the playlist after I put songs on it, so i made a playlist from the collection and i can't figure out how to drag it to the iPod or anything.... any help???

great player btw

---

### Post by 89c51 on 2007-07-13
Hello

i installed exaile and the only problem i have is that the tags on ogg files are not displayed and also it doesnt give any info on time of track etc

the only thing displayed is the name of the file

thanks in advance

---

### Post by Pahanilmanlintu on 2007-07-15
In addition to the resume playback plugin, an option to play a specific radio station or a smart playlist on startup would be nice.

I'm usually too lazy to rename the new playlists i make, so quite often i can't find the one that's currently playing. How about making that one's title boldprint, italic or different colour?

---

### Post by reacocard on 2007-07-15
> **Pahanilmanlintu said:**
> In addition to the resume playback plugin, an option to play a specific radio station or a smart playlist on startup would be nice.

I'm usually too lazy to rename the new playlists i make, so quite often i can't find the one that's currently playing. How about making that one's title boldprint, italic or different colour?

Those are both very good suggestions, you should file feature requests for those.

---

### Post by Dgurion on 2007-07-24
Is there a place I can get an AMD64 version? or would I have to compile that myself?

---

### Post by reacocard on 2007-07-26
> **Dgurion said:**
> Is there a place I can get an AMD64 version? or would I have to compile that myself?

Not yet (although I will hopefully have a 64bit comp to build packages on in a few weeks!), but compiling it yourself is very easy, see this post for instructions: [http://ubuntuforums.org/showpost.php?p=2982067&postcount=826](http://ubuntuforums.org/showpost.php?p=2982067&postcount=826)

---

### Post by xat_ on 2007-07-31
> **Delirious said:**
> exaile is nice, i like it better than amarok but the BIGGEST thing i miss in any must player in linux is .cue sheet support for flac files. Foobar handled them beautifully in windows but there isnt a player i have found that handles them correctly.

I would hate to have to redo my music collection just to be able to move around to different tracks in a flac image file.
The feature request has been around for a while actually:
[http://www.exaile.org/trac/ticket/183](http://www.exaile.org/trac/ticket/183)

It's been around half a year since it was requested. Not sure when it will be implemented, sadly.

---

### Post by gl0wst1ckn1nja on 2007-07-31
i love it ... its so much better than screwing with banshee and rythmbox ... thanks! ... finally some decent ipod support

---

### Post by timo1023 on 2007-07-31
I want to use this but i cannot get the other theme from the website to work or the paned browser. Help?

---

### Post by jamieh on 2007-07-31
Does this work with iPods?

---

### Post by Nekiruhs on 2007-07-31
> **jamieh said:**
> Does this work with iPods?
Yes, there is a plugin for Ipods.

---

### Post by QwUo173Hy on 2007-07-31
I can't find the ticket for this (if there is one)  but are there any plans to implement album covers in the browser like the attachment below? (Quod Libet). Exaile is the best GTK media playerout there, and this feature would make it the best player, full stop.

Personally, I'm a very visual person and can work a lot faster and more naturally this way.

Thanks,
Jarlath

---

### Post by Montsegur87 on 2007-08-01
Great work , I love Exaile. I didnt find any freedb/cddb support , that would be nice. But  EasyTag solves that :P

keep the good work

---

### Post by reacocard on 2007-08-02
> **Montsegur87 said:**
> Great work , I love Exaile. I didnt find any freedb/cddb support , that would be nice. But  EasyTag solves that :P

keep the good work

you have to install python-cddb

---

### Post by Montsegur87 on 2007-08-02
> **reacocard said:**
> you have to install python-cddb
Ive done that but I cant find that feature in the player. 
For example , in foobar you choose some songs from the playlist -> context menu -> get tags and loads them from fredb.

---

### Post by reacocard on 2007-08-02
> **Montsegur87 said:**
> Ive done that but I cant find that feature in the player. 
For example , in foobar you choose some songs from the playlist -> context menu -> get tags and loads them from fredb.

Oh, Exaile's doesn't work like that. When you load a CD into Exaile, it'll automatically check the cddb for the track info, but that's the only time it will.

---

### Post by Koybe on 2007-08-08
Exaile sounds great! I haven't read the whole thread but :

Is it possible to play mpc files?

I installed libmpcdec3 but I already had it. So I installed gstreamer0.8-musepack but anyway it didn't help...

---

### Post by reacocard on 2007-08-08
> **Koybe said:**
> Exaile sounds great! I haven't read the whole thread but :

Is it possible to play mpc files?

I installed libmpcdec3 but I already had it. So I installed gstreamer0.8-musepack but anyway it didn't help...

It should be possible, but you need the gstreamer 0.10 codec not the 0.8 one. try this:

```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstremer0.10-ffmpeg
```

That should let you play just about anything in Exaile.

---

### Post by Koybe on 2007-08-08
Thank you, I missed gstreamer0.10-plugins-bad ;-)

Another question : 

How to remove something from the library without removing it from the disk?

Also, some files aren't detected and I have no idea why...

---

### Post by reacocard on 2007-08-08
> **Koybe said:**
> Thank you, I missed gstreamer0.10-plugins-bad ;-)

Another question : 

How to remove something from the library without removing it from the disk?

Also, some files aren't detected and I have no idea why...

You can blacklist files to remove them from the library. For the ones that don't show, its likely a unicode issue, Exaile still has some problems with that. Try adding the missing ones by hand. If that doesn't work, run exaile from a terminal and try adding the files by hand again, then post the output (if any) here.

---

### Post by Koybe on 2007-08-08
```
jerome@cormyr:~$ exaile
/usr/share/exaile/xl/xlmisc.py:42: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon
/usr/lib/python2.5/site-packages/mutagen/m4a.py:41: DeprecationWarning: mutagen.m4a is deprecated; use mutagen.mp4 instead.
  "mutagen.m4a is deprecated; use mutagen.mp4 instead.", DeprecationWarning)
Plugins 'Mini Mode' version '0.1' loaded successfully
Plugins 'Serpentine Plugin' version '0.1' loaded successfully
Plugins 'Desktop Cover' version '0.1' loaded successfully
desktopcover.py_geometry
Cover geometry: 150x150+5+895
Plugins 'Alarm Clock' version '0.1' loaded successfully
Plugins 'LibNotify Plugin' version '0.1' loaded successfully
Plugins 'Streamripper!' version '0.1' loaded successfully
Plugins 'AWN' version '0.7.2' loaded successfully
mmkeys are available.
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x88f44d0>}
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/jerome/.exaile/saved/playlist0000.m3u
Created db for thread Thread-5
{'Thread-5': <sqlite3.Connection object at 0x88f4b60>}
Running is False
File count: 36
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 185, in _execute
    cur.execute(query, args)
IntegrityError: column name is not unique
INSERT INTO artists( id, name ) VALUES( ?, ? ) (38, 'An Pierl\xc3\xa9')
Closed db for thread Thread-5
Count is now: 36
```Here it is.

For your information, i Had 3 directories under that one, they were all nicely detected, but the Tags were wrong. I changed the tag, remade the m3u playlists and then reimport them and only one song is imported for the 3 directories.

It seems to be an encoding problem as you said. It should be  INSERT INTO artists( id, name ) VALUES( ?, ? ) (38, **'An Pierlé - and the next of the filename**') instead of  INSERT INTO artists( id, name ) VALUES( ?, ? ) (38, 'An Pierl\xc3\xa9')

Is rename all of this using Easytag and I guess I'm using UTF8 as it is the default in Ubuntu (I think).


SOLVED : I had to remake the database.

I removed ~/.exaile, reimport, it works now.

---

### Post by BDNiner on 2007-08-08
I am too lazy to read all 80 something pages in the topic. Does this player support network shares? The default Gnome music app does, but it is ugly as sin. Amarok doesn't, at least i could not find a way t make it work.

---

### Post by Koybe on 2007-08-08
I presume it'll work as soon as you mount your network share locally.

---

### Post by smoker on 2007-08-08
> **reacocard said:**
> It should be possible, but you need the gstreamer 0.10 codec not the 0.8 one. try this:

```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstremer0.10-ffmpeg
```

That should let you play just about anything in Exaile.

will it play .wma's with these installed?

---

### Post by Koybe on 2007-08-08
Each time I modify tag and/or filename, I Try rescanning the library but changes does not appear or goes wrong. Any idea?

---

### Post by reacocard on 2007-08-08
> **smoker said:**
> will it play .wma's with these installed?

I believe so, if not you'll need to install the w32codecs.

> **BDNiner said:**
> I am too lazy to read all 80 something pages in the topic. Does this player support network shares? The default Gnome music app does, but it is ugly as sin. Amarok doesn't, at least i could not find a way t make it work.

yes, install the Music Sharing plugin. Note that it only works with iTunes 6 and earlier shares, iTunes 7 hasn't been reverse-engineered yet.

---

### Post by Sweet Spot on 2007-08-08
Wow, this thread got pretty long. I was thumbing through problems with (annoyances) Rhythmbox and thought to check and see where Exaile is at these days. It seems that a lot of progress has been made, and the last time I tried it, I was using Dapper which was not compatible. 

I've finally gone Feisty, and would like to know if now is a good time to switch to Exaile. Is it stable ? Before I go off and ask a ton of questions (and I really can't be bothered to flip through 90 pages just to get different answers...) I'm wondering if there's a total progress page for it ?

What I mean by that is, a list of up to date working features that perhaps were not working before. Pretty much like an  current addendum list if you will. 

The main things I'm concerned about is speed, stability (no crashing or choking on large libraries) and out of the box good codec support such as FLAC, Ogg, Wavpack, muspac etc etc...  And most of all, does it do gapless ?  From what I understand, Rhythmbox will be doing gapless in Gutsy, and if no other player does it by then, it is the one I'll use. 

Thoughts ?

---

### Post by CaptMorgan on 2007-08-09
I admit I havent read the whole post but I have some bugs and a reccomendation

1. I have added a launcher to AWN and each time i reboot it is gone?
2. I have been ranking my songs, but each time I load it they ratings are gone (star system)
3. I installed the plugin for it to show my status on my messenger program (gaim)  as the current song, worked only once and is stuck on that song, P.S. that song is the only song that ever saved the stars I gave it

and it would be cool if the artist and albums were in a database or something so when we go to change an artist name thats mis-spelled when you have them correctly on other track you dont have to type the whole name

for example, I have one song thats Jay Z and the rest are Jay-Z, when I start typing JA a list would pop down and show similar matches like Jack Johnson
Jay-Z

thanks - Morgan

---

### Post by reacocard on 2007-08-09
> **Sweet Spot said:**
> Wow, this thread got pretty long. I was thumbing through problems with (annoyances) Rhythmbox and thought to check and see where Exaile is at these days. It seems that a lot of progress has been made, and the last time I tried it, I was using Dapper which was not compatible. 

I've finally gone Feisty, and would like to know if now is a good time to switch to Exaile. Is it stable ? Before I go off and ask a ton of questions (and I really can't be bothered to flip through 90 pages just to get different answers...) I'm wondering if there's a total progress page for it ?

What I mean by that is, a list of up to date working features that perhaps were not working before. Pretty much like an  current addendum list if you will. 

The main things I'm concerned about is speed, stability (no crashing or choking on large libraries) and out of the box good codec support such as FLAC, Ogg, Wavpack, muspac etc etc...  And most of all, does it do gapless ?  From what I understand, Rhythmbox will be doing gapless in Gutsy, and if no other player does it by then, it is the one I'll use. 

Thoughts ?

It is very stable, has good support for a wide variety of codecs (it should play anything gstreamer supports, but it doesn't do tags for some of the more-obscure formats), and has lots of new features. There are really too many to list, I'd just say to install it and see for yourself. be sure to check out the plugins, there are a bunch of them and do a ton of useful things.

> **CaptMorgan said:**
> I admit I havent read the whole post but I have some bugs and a reccomendation

1. I have added a launcher to AWN and each time i reboot it is gone?
2. I have been ranking my songs, but each time I load it they ratings are gone (star system)
3. I installed the plugin for it to show my status on my messenger program (gaim)  as the current song, worked only once and is stuck on that song, P.S. that song is the only song that ever saved the stars I gave it

and it would be cool if the artist and albums were in a database or something so when we go to change an artist name thats mis-spelled when you have them correctly on other track you dont have to type the whole name

for example, I have one song thats Jay Z and the rest are Jay-Z, when I start typing JA a list would pop down and show similar matches like Jack Johnson
Jay-Z

thanks - Morgan

1) Likely an AWN issue not Exaile.
2) No idea about this one.
3) The IM client has to be started before Exaile for it to work nicely.

Also, that's a really good idea, you should post a request for it in Exaile's trac.

---

### Post by Koybe on 2007-08-09
> **Koybe said:**
> Each time I modify tag and/or filename, I Try rescanning the library but changes does not appear or goes wrong. Any idea?

Ok, it seems to be an mpc tag problem. I saw some related bug are experienced now. Waiting the next release :D

---

### Post by reacocard on 2007-08-09
> **Koybe said:**
> Ok, it seems to be an mpc tag problem. I saw some related bug are experienced now. Waiting the next release :D

Should be soon, they're debating on the exaile-devel list whether to prepare for releasing 0.2.11. Once feature freeze for 0.2.11 is announced it should be less than a month to release.

---

### Post by Sweet Spot on 2007-08-09
What about gapless ? 

And what initially drew me back to this thread was an irritation caused by something that Rhythmbox does *or rather doesnt*  

Let's say you're in Nautilus and browsing some music files which you have just either downloaded, or ripped. You decide that you will either click on a file, or right click and "open with" (in my current case rhythmbox) and then, OK... Rhythmbox opens, but it does absolutely NOTHING with the file.  In fact, I don't even see it listed anywhere near the playlist. 

What it SHOULD do, is queue the song either on it's own in a "now playing" list (separate from the main playlist)  or just add it to the current ALL list and highlight where it is within the list so you can see it, as well as have it play. 

How does Exaile handle such things ?
Oh and, did I ask about Gapless ? :lolflag:

---

### Post by CaptMorgan on 2007-08-09
> **reacocard said:**
> 
1) Likely an AWN issue not Exaile.
2) No idea about this one.
3) The IM client has to be started before Exaile for it to work nicely.


Also, that's a really good idea, you should post a request for it in Exaile's trac.

 kinda figured that was just seeing if it was common

I have started going file>quit and this has been saving them over hitting the x, dont ask why just does

and worked like a charm thank you

---

### Post by reacocard on 2007-08-10
> **Sweet Spot said:**
> What about gapless ? 

And what initially drew me back to this thread was an irritation caused by something that Rhythmbox does *or rather doesnt*  

Let's say you're in Nautilus and browsing some music files which you have just either downloaded, or ripped. You decide that you will either click on a file, or right click and "open with" (in my current case rhythmbox) and then, OK... Rhythmbox opens, but it does absolutely NOTHING with the file.  In fact, I don't even see it listed anywhere near the playlist. 

What it SHOULD do, is queue the song either on it's own in a "now playing" list (separate from the main playlist)  or just add it to the current ALL list and highlight where it is within the list so you can see it, as well as have it play. 

How does Exaile handle such things ?
Oh and, did I ask about Gapless ? :lolflag:

No gapless yet, though it should be possible as rb does it iirc. 

As for the files, exaile doesn't handle multiple files well, but individual files are handled by appending them to the current playlist and playing them immediately. You can also simply drag files onto a playlist to add them in a specific spot and without playing them immediately.

---

### Post by Athropos on 2007-08-10
> **reacocard said:**
> No gapless yet, though it should be possible as rb does it iirc. 


Hi,

I'm the guy who wrote the IMStatus plugin. Some times ago I started to write my own music player for two reasons:
 * I was using Exaile but I was always faced with a lot of annoying details
 * The patches I submitted somehow got stuck on the Trac

Now I'm happy with my own player as it's exactly how I want it to be, minus the features that are not already coded. So if you want gapless playing of tracks, just look at how I did it:

[http://decibel.silent-blade.org](http://decibel.silent-blade.org)

Basically, I'm using two GStreamer players, and I start the second one just before the first one stops. Then I swap them.

You can re-use my code if you want, it's GPL and even written in Python, but don't ask me to write a patch ;-)

---

### Post by Sweet Spot on 2007-08-10
> **Athropos said:**
> Hi,

I'm the guy who wrote the IMStatus plugin. Some times ago I started to write my own music player for two reasons:
 * I was using Exaile but I was always faced with a lot of annoying details
 * The patches I submitted somehow got stuck on the Trac

Now I'm happy with my own player as it's exactly how I want it to be, minus the features that are not already coded. So if you want gapless playing of tracks, just look at how I did it:

[http://decibel.silent-blade.org](http://decibel.silent-blade.org)

Basically, I'm using two GStreamer players, and I start the second one just before the first one stops. Then I swap them.

You can re-use my code if you want, it's GPL and even written in Python, but don't ask me to write a patch ;-)

That sounds like some funky work around for cross fading, rather than utilizing code which works with the algorithms which are designed for LAME encoding or Ogg encodings. Am I correct in thinking that ? If true, I'd rather see a real implementation of true gapless playback, as is used for players such as Foobar, J.River Media Center etc. ...

---

### Post by reacocard on 2007-08-10
> **Athropos said:**
> Hi,

I'm the guy who wrote the IMStatus plugin. Some times ago I started to write my own music player for two reasons:
 * I was using Exaile but I was always faced with a lot of annoying details
 * The patches I submitted somehow got stuck on the Trac

Now I'm happy with my own player as it's exactly how I want it to be, minus the features that are not already coded. So if you want gapless playing of tracks, just look at how I did it:

[http://decibel.silent-blade.org](http://decibel.silent-blade.org)

Basically, I'm using two GStreamer players, and I start the second one just before the first one stops. Then I swap them.

You can re-use my code if you want, it's GPL and even written in Python, but don't ask me to write a patch ;-)

Thanks! I'll add this info to the ticket. I don't have time to work on it right now, but I'm sure it'll get in eventually.

Also just a note, trac is more just a way to keep track of stuff for us, if you have something that you think really needs to get fixed or added, go to #exaile and talk to a dev (synic, sjohannes or myself) about it, or if you can't reach anyone, post it to exaile-devel.

---

### Post by goumples on 2007-08-10
Aye, Exaile is my new default music player.

---

### Post by Athropos on 2007-08-11
> **Sweet Spot said:**
> That sounds like some funky work around for cross fading, rather than utilizing code which works with the algorithms which are designed for LAME encoding or Ogg encodings. Am I correct in thinking that ? If true, I'd rather see a real implementation of true gapless playback, as is used for players such as Foobar, J.River Media Center etc. ...

GStreamer actually really lacks of good documentation, many of its capabilities are badly documented or not documented at all. The way I'm doing it works perfectly for me, and as I said I made it primarily for myself ;-)

---

### Post by Caffeine_Junky on 2007-08-11
Nice player mate! ..I have been using it for a few weeks and I really like it.. 
 pure-class = Exaile!

nice work  ...cheers

---

### Post by Montsegur87 on 2007-08-11
This has been probably asked but there are > 80 pages in this Thread.

How do I install from svn?


 I manage to download 
```
svn co svn://exaile.org/usr/local/svn/exaile/trunk exaile 
```

and execute the new version
```
nagel@nagel-rahxephon:~$ cd trunk/
nagel@nagel-rahxephon:~/trunk$ python exaile.py build
A supported CD burning program was not found in $PATH, disabling burning capabilities.
Using multimedia keys from: None
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x868d7a0>}
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/nagel/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0
```

But I cant install it , because when I run exaile from console it loads the old version.

---

### Post by the badger on 2007-08-12
Incase any other newbie-types are kicking around this thread, looking to find an alternative to amaroK (which is what i am, and how I ended up here), I just installed exhaile as per the three-lines-of-code directions found on the first page, first post (thanks synic!). 

however, i ran into the following glitch
```
badger@clank:~$ sudo apt-get install python-gtk2 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
Password:
Reading package lists... Done
Building dependency tree... Done
python-gtk2 is already the newest version.
E: Couldn't find package libgstreamer0.10
badger@clank:~$ wget http://www.exaile.org/files/exaile_0.2b4_i386.deb
--14:35:19--  http://www.exaile.org/files/exaile_0.2b4_i386.deb
           => `exaile_0.2b4_i386.deb'
Resolving www.exaile.org... 64.251.22.233
Connecting to www.exaile.org|64.251.22.233|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 205,480 (201K) [application/x-debian-package]

100%[====================================>] 205,480      117.31K/s

14:35:31 (117.06 KB/s) - `exaile_0.2b4_i386.deb' saved [205480/205480]

badger@clank:~$ sudo dpkg -i exaile_0.2b4_i386.deb
Selecting previously deselected package exaile.
(Reading database ... 84459 files and directories currently installed.)
Unpacking exaile (from exaile_0.2b4_i386.deb) ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on python-pysqlite2; however:
  Package python-pysqlite2 is not installed.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile
```
heck knows what's going on there.
however, I logged into synaptic and clicked on "fix broken packages" (in the edit menu). this seems to have done the trick, and I now have a lovely media player!

---

### Post by reacocard on 2007-08-12
> **the badger said:**
> Incase any other newbie-types are kicking around this thread, looking to find an alternative to amaroK (which is what i am, and how I ended up here), I just installed exhaile as per the three-lines-of-code directions found on the first page, first post (thanks synic!). 

however, i ran into the following glitch
```
badger@clank:~$ sudo apt-get install python-gtk2 python-pysqlite2 python-pymad libgstreamer0.10 libgstreamer0.10-plugins-good python-gst0.10 python-pyogg
Password:
Reading package lists... Done
Building dependency tree... Done
python-gtk2 is already the newest version.
E: Couldn't find package libgstreamer0.10
badger@clank:~$ wget http://www.exaile.org/files/exaile_0.2b4_i386.deb
--14:35:19--  http://www.exaile.org/files/exaile_0.2b4_i386.deb
           => `exaile_0.2b4_i386.deb'
Resolving www.exaile.org... 64.251.22.233
Connecting to www.exaile.org|64.251.22.233|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 205,480 (201K) [application/x-debian-package]

100%[====================================>] 205,480      117.31K/s

14:35:31 (117.06 KB/s) - `exaile_0.2b4_i386.deb' saved [205480/205480]

badger@clank:~$ sudo dpkg -i exaile_0.2b4_i386.deb
Selecting previously deselected package exaile.
(Reading database ... 84459 files and directories currently installed.)
Unpacking exaile (from exaile_0.2b4_i386.deb) ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on python-pysqlite2; however:
  Package python-pysqlite2 is not installed.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile
```
heck knows what's going on there.
however, I logged into synaptic and clicked on "fix broken packages" (in the edit menu). this seems to have done the trick, and I now have a lovely media player!

Um, those are VERY old instructions for a VERY old version. Go to exaile.org and click the downloads link to get a much newer and better Exaile.

> **Montsegur87 said:**
> This has been probably asked but there are > 80 pages in this Thread.

How do I install from svn?


 I manage to download 
```
svn co svn://exaile.org/usr/local/svn/exaile/trunk exaile 
```

and execute the new version
```
nagel@nagel-rahxephon:~$ cd trunk/
nagel@nagel-rahxephon:~/trunk$ python exaile.py build
A supported CD burning program was not found in $PATH, disabling burning capabilities.
Using multimedia keys from: None
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x868d7a0>}
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/nagel/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0
```

But I cant install it , because when I run exaile from console it loads the old version.

Use this command in the source dir to install it:
```
sudo make install
```
it would also be a VERY good idea to remove the old exaile first.

---

### Post by Montsegur87 on 2007-08-12
Thanks reacocard , that made it.

---

### Post by SLA_leandrin on 2007-08-13
Great work with Exaile.. I love it.
I'm still waiting for MTP players supprt however...!!!

---

### Post by drobvice on 2007-08-16
I have been playing from a daap share with exaile and having a little problem.  If I add a whole cd to a list and play a middle track, it will go to the first file in the list on the next track change and not the next in line.  There are also blue numbered sqares next to the track numbers and am not sure what those mean.  Am I doing something wrong?  I am having touble finding documentation on remote sharing.

---

### Post by reacocard on 2007-08-16
> **drobvice said:**
> I have been playing from a daap share with exaile and having a little problem.  If I add a whole cd to a list and play a middle track, it will go to the first file in the list on the next track change and not the next in line.  There are also blue numbered sqares next to the track numbers and am not sure what those mean.  Am I doing something wrong?  I am having touble finding documentation on remote sharing.

there are no docs because its indended to work just like the local collection. In your case, the blue numbers mean you're adding it to the queue, add it to the playlist instead and see if that helps ('append to current')

---

### Post by drobvice on 2007-08-16
That helps but the track duplicates at the end of the list.  Will try to attach a screenshot.

---

### Post by reacocard on 2007-08-16
> **drobvice said:**
> That helps but the track duplicates at the end of the list.  Will try to attach a screenshot.

hm, that doesn't happen to me. very strange


Also one quick announcement: exaile.org is going to be down for a few hours for maintenance.

---

### Post by drobvice on 2007-08-16
I don't know if it matters, but I am using firefly media server on a windows machine for the daap share.

---

### Post by reacocard on 2007-08-16
> **drobvice said:**
> I don't know if it matters, but I am using firefly media server on a windows machine for the daap share.

firefly/mt-daapd has for some reason always been buggy with the exaile daap plugin. I use [Tangerine]("http://www.snorp.net/log/tangerine/") instead, which works much better.

---

### Post by drobvice on 2007-08-16
I tried tangerine first but it would always crash when xp would start up.  I had to find an alternative and came across firefly.  It's been really solid so far.

---

### Post by joeinnes on 2007-08-18
I'm not running Ubuntu, but since the exaile.org website is down, this is the only method I can see to get my message to the developer. It's not a showstopper, but enough for me to consider changing my audio player. When I run exaile, it refuses to play a second song consecutively. However, I'm unable to produce any error details for this, because it doesn't reproduce this behaviour when launched from the console.

I'm running Debian unstable on amd64 architecture, using the debian package.

If the problem is the package, then let me know. If the problem is with the software, then let me know the fix, please. I don't frequent these forums often, but I can be contacted at [email]joeinnes_nospam_@gmail.com[/email] (obviously, take out the _nospam_

Joe

---

### Post by reacocard on 2007-08-18
> **joeinnes said:**
> I'm not running Ubuntu, but since the exaile.org website is down, this is the only method I can see to get my message to the developer. It's not a showstopper, but enough for me to consider changing my audio player. When I run exaile, it refuses to play a second song consecutively. However, I'm unable to produce any error details for this, because it doesn't reproduce this behaviour when launched from the console.

I'm running Debian unstable on amd64 architecture, using the debian package.

If the problem is the package, then let me know. If the problem is with the software, then let me know the fix, please. I don't frequent these forums often, but I can be contacted at [email]joeinnes_nospam_@gmail.com[/email] (obviously, take out the _nospam_

Joe

there's something buggy in the player code right now since a number of people have experienced similar bugs. I myself have experienced this one, but it mysteriously stopped happening a couple weeks ago. My suggestion is to wait for exaile.org to come up and then add your confirmation to [the bug on trac]("http://www.exaile.org/trac/ticket/756"), the more people known to experience it the better the odds are it will get fixed.

---

### Post by puratu on 2007-08-20
hello everyone. I installed Exaile, it looks very nice, just like Amarok but I couldn't use it. I added my mp3 folder to "tools" - "library manager", it scanned my folders but it didn't create a collection.
Am I doing something wrong? What should I do?

---

### Post by GFree678 on 2007-08-20
> **puratu said:**
> hello everyone. I installed Exaile, it looks very nice, just like Amarok but I couldn't use it. I added my mp3 folder to "tools" - "library manager", it scanned my folders but it didn't create a collection.
Am I doing something wrong? What should I do?
Nah, you're doing things right. The problem is that since the necessary mp3 codecs aren't installed, Exaile currently won't understand them and as such will skip them when scanning.

Unfortunately I can't remember exactly what package contains the codecs, so just go to Applications - Add/Remove... -> change selector to "All Available applications", enter the word **codec** in the search bar and install anything starting with the word **GStreamer**. Should be about four entries.

---

### Post by puratu on 2007-08-20
> **GFree678 said:**
> Nah, you're doing things right. The problem is that since the necessary mp3 codecs aren't installed, Exaile currently won't understand them and as such will skip them when scanning.

Unfortunately I can't remember exactly what package contains the codecs, so just go to Applications - Add/Remove... -> change selector to "All Available applications", enter the word **codec** in the search bar and install anything starting with the word **GStreamer**. Should be about four entries.

Thanks for your reply but I &#305;nstalled necesarry codecs with Automatix. Everything starting with "GStreamer" is installed and I can play my mp3s with Audacious and other applications. Exaile can play them too.  but my problem is that it can't build collection.

---

### Post by FuturePilot on 2007-08-20
I have a question. Most of my album art is embedded in the mp3 itself but Exaile does not display it. Is this a bug, or a feature that hasn't been implemented yet?

---

### Post by reacocard on 2007-08-20
> **puratu said:**
> Thanks for your reply but I &#305;nstalled necesarry codecs with Automatix. Everything starting with "GStreamer" is installed and I can play my mp3s with Audacious and other applications. Exaile can play them too.  but my problem is that it can't build collection eith Exaile.

Can you run exaile from a terminal and posting the output after a rescan?

> **FuturePilot said:**
> I have a question. Most of my album art is embedded in the mp3 itself but Exaile does not display it. Is this a bug, or a feature that hasn't been implemented yet?

Feature that hasn't been implemented yet. Here's the request: [http://www.exaile.org/trac/ticket/271](http://www.exaile.org/trac/ticket/271)

---

### Post by puratu on 2007-08-20
Terminal output is too long to paste the forum :)
[ATTACH]41178[/ATTACH]

---

### Post by reacocard on 2007-08-20
> **puratu said:**
> Terminal output is too long to paste the forum :)
[ATTACH]41178[/ATTACH]

Hm, that shouldn't be happening. What version are you using? If its not 0.2.10 go to exaile.org and download the latest version.

---

### Post by puratu on 2007-08-20
that didn't solve my problem :( I downloaded 0.2.10 ( before it was 0.2.8 ) but it didn't create a collection too. I have the same output from terminal.

---

### Post by reacocard on 2007-08-20
> **puratu said:**
> that didn't solve my problem :( I downloaded 0.2.10 ( before it was 0.2.8 ) but it didn't create a collection too. I have the same output from terminal.

try removing the config and starting over:
```
rm -r ~/.exaile
```

---

### Post by puratu on 2007-08-20
> **reacocard said:**
> try removing the config and starting over:
```
rm -r ~/.exaile
```

no. that didn't work. :(

---

### Post by puratu on 2007-08-20
I think I should use Banshee. It is not as good as Exaile but run correctly on my system.

---

### Post by Depressed Man on 2007-08-20
Is there anyway to get my hotkeys working with it? I know I can pass arguements like exaile - play but I want the keys availiable for other programs too. I have taken a look at ReMoot but I'm still trying to figure it out. I can't figure out how to get any program to accept ReMoot commands (even if I specify them in hotkeys) like remoot play

---

### Post by reacocard on 2007-08-20
> **puratu said:**
> I think I should use Banshee. It is not as good as Exaile but run correctly on my system.

Maybe so. If you use IRC, you could try to catch synic in #exaile, he might be able to help you better than I can.

> **Depressed Man said:**
> Is there anyway to get my hotkeys working with it? I know I can pass arguements like exaile - play but I want the keys availiable for other programs too. I have taken a look at ReMoot but I'm still trying to figure it out. I can't figure out how to get any program to accept ReMoot commands (even if I specify them in hotkeys) like remoot play

Exaile should simply accept the multimedia keys from gnome automatically, if its not you need to upgrade to a newer version.

---

### Post by GFree678 on 2007-08-20
OMG, I just solved a really big issue today. I was having trouble getting Exaile to seek to the right spot in a track when I clicked the time progress bar. Turns out to solve this I had to install the "gstreamer0.10-fluendo-mp3", which was a complete guess since it was already playing mp3s properly without it. This was becoming really annoying.

A side effect though is that Totem displays N/A for the codec and bitrate entries for any MP3 now, although Exaile displays the bitrates properly though. I prefer proper seek ability to Totem's file analysis though

---

### Post by Depressed Man on 2007-08-20
> **reacocard said:**
> Maybe so. If you use IRC, you could try to catch synic in #exaile, he might be able to help you better than I can.



Exaile should simply accept the multimedia keys from gnome automatically, if its not you need to upgrade to a newer version.

I'm using the SVN (or whatever is the one that has me updating so frequently lol). The problem is I changed the hotkeys in it, and I can't get it back to normal. :(

---

### Post by reacocard on 2007-08-20
> **Depressed Man said:**
> I'm using the SVN (or whatever is the one that has me updating so frequently lol). The problem is I changed the hotkeys in it, and I can't get it back to normal. :(

Gnome keys are set in System -> Preferences -> Keyboard Shortcuts I believe (I don't use gnome anymore so the name might be slightly different)

---

### Post by Depressed Man on 2007-08-20
Yeah I know, I'm saying I changed the hotkeys in Exaile (I'm using the plugin that should be getting it from metacity/gnome). Now it no longer detects them. :(

---

### Post by reacocard on 2007-08-20
> **Depressed Man said:**
> Yeah I know, I'm saying I changed the hotkeys in Exaile (I'm using the plugin that should be getting it from metacity/gnome). Now it no longer detects them. :(

don't use that plugin, its never worked well for me. All it does is map the keystrokes to exaile --play and such in the metacity config. It is MUCH better to use the gnome mmkeys if possible.

---

### Post by Depressed Man on 2007-08-20
Ok, how do I set it so exaile can use the keys in gnome? I know it's in keyboard shortcuts but currently my play/pause, stop, etc.. is set to be a generic play and stuff which seems to work for most media (audio and video players).

---

### Post by reacocard on 2007-08-20
> **Depressed Man said:**
> Ok, how do I set it so exaile can use the keys in gnome? I know it's in keyboard shortcuts but currently my play/pause, stop, etc.. is set to be a generic play and stuff which seems to work for most media (audio and video players).

It's automatic, just disable the hotkeys plugin and set the keys up in gnome's keyboard shortcuts.

---

### Post by Depressed Man on 2007-08-20
Ok I disabled the plugin and my play, next, previous, stop keys are already configured. (They work in other applications) Yet they don't seem to work in Exaile. :(

Edit: Figured it out. I had recently uninstalled keytouch and had to restart it to get it back to normal.

---

### Post by owlicksander on 2007-08-21
I'm running version 2.10 in Ubuntu Feisty and every time I attempt to import a directory it locks up and has to be force quit.

Any ideas? I've posted this around and no one seems to know how to help me.

---

### Post by likemindead on 2007-08-21
It's Rhythmbox for me. Exaile only brought up 1/3 of my album covers.

---

### Post by jbysmith on 2007-08-23
Have a silly question.

Fixed a couple of minor quirks by updating to the current version from the Exaile repository.  (Wish Ubuntu would update theirs, was trying to figure out the coverart/OSD thing till I saw the newer version.. and I love the feature where it grabs coverart automatically by a filename.  Migrated from Windows a while back,and pointed it to the existing folder images)

The one thing about Amarok that I like over Exaile is that I can start it up minimized to the tray.  Is that currently possible with Exaile?  (Just a minor thing, I'm sticking with Exaile regardless, works great)

Thanks

---

### Post by reacocard on 2007-08-23
> **jbysmith said:**
> Have a silly question.

Fixed a couple of minor quirks by updating to the current version from the Exaile repository.  (Wish Ubuntu would update theirs, was trying to figure out the coverart/OSD thing till I saw the newer version.. and I love the feature where it grabs coverart automatically by a filename.  Migrated from Windows a while back,and pointed it to the existing folder images)

The one thing about Amarok that I like over Exaile is that I can start it up minimized to the tray.  Is that currently possible with Exaile?  (Just a minor thing, I'm sticking with Exaile regardless, works great)

Thanks

It certainly is, add the --start-minimized option to the command you use to start it.

---

### Post by Depressed Man on 2007-08-25
Is there anyway to track why crashes occur? I've noticed that sometimes when I use Exaile the music stops and the window is gone (I'm guessing it crashed). Is there an error log output somewhere?

---

### Post by reacocard on 2007-08-25
> **Depressed Man said:**
> Is there anyway to track why crashes occur? I've noticed that sometimes when I use Exaile the music stops and the window is gone (I'm guessing it crashed). Is there an error log output somewhere?

yes, in ~/.exaile/exaile.log

you usually get better feedback by running it in a terminal and looking at the output though.

---

### Post by phyzik on 2007-08-31
I've spent couple of months searching for a decent audio player for my ubuntu system. I needed a player/collection manager, so I tried Rhythmbox (too simple), Banshee (simple & buggy), Listen (sloooow and kept crashing) and others, but then turned back to Rhythmbox because I thought exaile was just the same (it's only in 0.2 stage!).
Yesterday I decided to give it a shot (after reading this thread and an article on the web), and I was positively surprised!!


It's very fast, practically bugless, works with keytouch, last.fm, has a great way of sorting music and has lots of useful plugins.

I only encountered 2 problems so far:
1) Alarm Clock plugin doesn't seem to work. I tried with closed, trayed and open window (always with music stopped), but it just doesn't start...

2) DAP device keeps creating problems. I have a Cowon iAudio X5 30GB media player with almost 6000 songs on it. It takes Exaile couple of minutes to load them each time I plug in the player, and after that the songs (album, artist or genre style) aren't listed. I have to manually search for a certain artist/album, and even when Exaile lists search results, they're still buggy (right click doesn't work, duplicate entries, tag editing freezes,...) The entire Exaile freezes (or almost) after couple of songs...


I also have a couple of suggestions (from mediamonkey and my own ideas):
1) is it possible to rename filenames of songs based on their tags (ATM, only the reverse option is available)?

2) could more websites be added to coverart search (for example, last.fm)? That would be really helpful for non-english-speaking nations (my country's artists don't sell albums on amazon ;) )

3) when adding tags from filenames, only a couple of options are included. Could a "manual" option be added where you create your own tag style?


Anyway, kudos to developer(s) you've made a great player! I've already uninstalled Rhythmbox and moved to Exaile :)
Thank you guys

---

### Post by reacocard on 2007-08-31
> **damien37 said:**
> I've spent couple of months searching for a decent audio player for my ubuntu system. I needed a player/collection manager, so I tried Rhythmbox (too simple), Banshee (simple & buggy), Listen (sloooow and kept crashing) and others, but then turned back to Rhythmbox because I thought exaile was just the same (it's only in 0.2 stage!).
Yesterday I decided to give it a shot (after reading this thread and an article on the web), and I was positively surprised!!


It's very fast, practically bugless, works with keytouch, last.fm, has a great way of sorting music and has lots of useful plugins.

I only encountered 2 problems so far:
1) Alarm Clock plugin doesn't seem to work. I tried with closed, trayed and open window (always with music stopped), but it just doesn't start...

2) DAP device keeps creating problems. I have a Cowon iAudio X5 30GB media player with almost 6000 songs on it. It takes Exaile couple of minutes to load them each time I plug in the player, and after that the songs (album, artist or genre style) aren't listed. I have to manually search for a certain artist/album, and even when Exaile lists search results, they're still buggy (right click doesn't work, duplicate entries, tag editing freezes,...) The entire Exaile freezes (or almost) after couple of songs...


I also have a couple of suggestions (from mediamonkey and my own ideas):
1) is it possible to rename filenames of songs based on their tags (ATM, only the reverse option is available)?

2) could more websites be added to coverart search (for example, last.fm)? That would be really helpful for non-english-speaking nations (my country's artists don't sell albums on amazon ;) )

3) when adding tags from filenames, only a couple of options are included. Could a "manual" option be added where you create your own tag style?


Anyway, kudos to developer(s) you've made a great player! I've already uninstalled Rhythmbox and moved to Exaile :)
Thank you guys

Great to hear you like it! You should file bug reports on launchpad about those two problems. As for your suggestions, someone was talking about maybe doing 2, 3 can be done (click the + next to the box), and 1 is certainly possible. Again, just file your requests on launchpad, that way we can keep track of them.

---

### Post by PsycoGeek on 2007-09-03
A Q about Exaile!...  Is there or will there be and equalizer for it?  I like the app a lot so far, but the Eq thing is holding me back from testing it even further.

---

### Post by Onyros on 2007-09-03
> **PsycoGeek said:**
> A Q about Exaile!...  Is there or will there be and equalizer for it?  I like the app a lot so far, but the Eq thing is holding me back from testing it even further.You mean... something like...

[[IMG]http://img123.imageshack.us/img123/2699/exailescreenielm2.th.jpg[/IMG]](http://img123.imageshack.us/my.php?image=exailescreenielm2.jpg)

this? :P

(On Feisty you need Reacocard's Gstreamer packages, on Gutsy you should have the equalizer enabled by default; same thing goes for Arch Linux... Exaile working perfectly there, with equalizer enabled by default, too)

---

### Post by xat_ on 2007-09-04
> **Onyros said:**
> 
(On Feisty you need Reacocard's Gstreamer packages, on Gutsy you should have the equalizer enabled by default; same thing goes for Arch Linux... Exaile working perfectly there, with equalizer enabled by default, too)

Just got those gstreamer packages installed. Equalizer works very well for me, but since upgrading to those new packages I've noticed a considerable drop in bass tones by default. Did something fundamental change for that to have happened? On one hand I'm sort of tempted to downgrade, but on the other hand I don't want to lose the equalizer.

---

### Post by reacocard on 2007-09-04
> **xat_ said:**
> Just got those gstreamer packages installed. Equalizer works very well for me, but since upgrading to those new packages I've noticed a considerable drop in bass tones by default. Did something fundamental change for that to have happened? On one hand I'm sort of tempted to downgrade, but on the other hand I don't want to lose the equalizer.

This is believed to be a gstreamer issue, it actually drops volume across all ranges, not sure why it only does bass for you. This might be fixed in newer releases of gstreamer, but I don't know. Apps that do not use the EQ shouldn't be affected.

---

### Post by xat_ on 2007-09-05
Yes indeed I noticed a volume drop overall but for some reason it seems as if bass tones were affected the most. :S

---

### Post by Depressed Man on 2007-09-05
Hmm I can't  get some plugins to install (Exaile will install them but they don't show up, and launching exaile from the terminal shows a couple errors).

---

### Post by reacocard on 2007-09-05
> **Depressed Man said:**
> Hmm I can't  get some plugins to install (Exaile will install them but they don't show up, and launching exaile from the terminal shows a couple errors).

Could you post the errors please? It's possible you just need some dependencies or a newer version  of exaile.

---

### Post by Depressed Man on 2007-09-05
Sure. :)

```
vforviktor@vendetta:~$ exaile

(exaile.py:13029): libglade-WARNING **: unknown attribute `comment' for <property>.

(exaile.py:13029): libglade-WARNING **: unknown attribute `comment' for <property>.

(exaile.py:13029): libglade-WARNING **: unknown attribute `comment' for <property>.
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/awn.py", line 19, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'Send via Bluetooth' version '0.2.1' loaded successfully
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/ipoddriver.py", line 22, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'Panel List' version '0.1.1' loaded successfully
Plugins 'Shoutcast Radio' version '0.4.1' loaded successfully
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/massstoragedriver.py", line 22, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/alarmclock.py", line 21, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'Desktop Cover' version '0.3' loaded successfully
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/resume.py", line 4, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/updates.py", line 6, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/imstatus.py", line 6, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'No Taskbar Entry' version '0.1' loaded successfully
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x8694db8>}
Logging in to audioscrobbler
Using multimedia keys from: gnome
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/vforviktor/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0

```

---

### Post by reacocard on 2007-09-05
> **Depressed Man said:**
> Sure. :)

```
vforviktor@vendetta:~$ exaile

(exaile.py:13029): libglade-WARNING **: unknown attribute `comment' for <property>.

(exaile.py:13029): libglade-WARNING **: unknown attribute `comment' for <property>.

(exaile.py:13029): libglade-WARNING **: unknown attribute `comment' for <property>.
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/awn.py", line 19, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'Send via Bluetooth' version '0.2.1' loaded successfully
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/ipoddriver.py", line 22, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'Panel List' version '0.1.1' loaded successfully
Plugins 'Shoutcast Radio' version '0.4.1' loaded successfully
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/massstoragedriver.py", line 22, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/alarmclock.py", line 21, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'Desktop Cover' version '0.3' loaded successfully
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/resume.py", line 4, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/updates.py", line 6, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Failed to load plugin
Traceback (most recent call last):
  File "/usr/share/exaile/plugins/manager.py", line 60, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/vforviktor/.exaile/plugins/imstatus.py", line 6, in <module>
    import xl.plugins as plugins
ImportError: No module named plugins
Plugins 'No Taskbar Entry' version '0.1' loaded successfully
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x8694db8>}
Logging in to audioscrobbler
Using multimedia keys from: gnome
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/vforviktor/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0

```

Yep, you need a newer version of Exaile. See the [exaile downloads]("http://www.exaile.org/downloads") page for instructions.

---

### Post by Depressed Man on 2007-09-05
[CODE]Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  exaile-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/CODE

I figured.. but I've been getting this error lately when I run sudo apt-get update]

---

### Post by reacocard on 2007-09-05
> **Depressed Man said:**
> [CODE]Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  exaile-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/CODE

I figured.. but I've been getting this error lately when I run sudo apt-get update]

The repo has moved, remove the current deb lines from your sources.list and follow the new ones on the exaile downloads page.

---

### Post by Depressed Man on 2007-09-05
Wow, do I feel stupid. :lolflag:

---

### Post by Onyros on 2007-09-05
> **reacocard said:**
> This is believed to be a gstreamer issue, it actually drops volume across all ranges, not sure why it only does bass for you. This might be fixed in newer releases of gstreamer, but I don't know. Apps that do not use the EQ shouldn't be affected.reaco*, as far as I know the volume was affected overall, but I also had to compensate a little more on the bass.

Even so, the first equalizer implementation was much worse than it is right now. I suppose it was done at Gstreamer level, but still, good work going with Exaile! ;)

---

### Post by reacocard on 2007-09-05
> **Onyros said:**
> reaco*, as far as I know the volume was affected overall, but I also had to compensate a little more on the bass.

Even so, the first equalizer implementation was much worse than it is right now. I suppose it was done at Gstreamer level, but still, good work going with Exaile! ;)

yeah this is not the newest GST, its a rather old backport. I'm likely going to upgrade to gutsy soon so I'll be able to see if the newer GST in gutsy is affected the same way.

---

### Post by p_quarles on 2007-09-05
Just wanted to say that I've been using Exaile for a week now, and love it. It loads a *lot *faster than Amarok in GTK, and it even picked up the media keys without my having to do anything. 

One problem, though: it seems to think it's fetched all of the album art, but doesn't display any. Not a big deal, but just thought I'd pass that along.

---

### Post by kingofpain on 2007-09-07
Actually album art fetching works wonderful in 0.2.11 version (daily svn packages). Unfortunately, a few days ago I had to switch back to 0.2.10 because I made a plugin update and plugins weren't working anymore, but I kept my album art cache :).

---

### Post by Montsegur87 on 2007-09-08
Fresh 7.04 install , fully upgraded.
```
nagel@nagel-desktop:~$ exaile 
You have entered an invalid option
Traceback (most recent call last):
  File "/usr/share/exaile/xl/xlmisc.py", line 36, in <module>
    from xl import mozembed
  File "/usr/share/exaile/xl/mozembed.py", line 29, in <module>
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory

```

What happened to the SVN repository?
```
$ sudo apt-get install bzr
$ bzr checkout http://bazaar.launchpad.net/~exaile-devel/exaile/main exaile
```

---

### Post by ubromtoo on 2007-09-11
In Dapper , I installed Exaile 0.2.10 , but it won't start..

trying to run it from the command line, there is the message :

  " import error  no module named oggvorbis"

 tried Synaptic for this, no luck . What to do?

---

### Post by reacocard on 2007-09-11
> **ubromtoo said:**
> In Dapper , I installed Exaile 0.2.10 , but it won't start..

trying to run it from the command line, there is the message :

  " import error  no module named oggvorbis"

 tried Synaptic for this, no luck . What to do?

Exaile does not run well on dapper because dapper's version of mutagen (the tag-reading library exaile uses) is too old. You'll have to either use an older exaile, install a newer mutagen, or upgrade to a more recent version of ubuntu.

---

### Post by Scotty562 on 2007-09-29
Seems to work just fine. I wish it showed album art next to the artists  when looking for a new cd to play. Maybe that's just a dirty joy from windows media player though.

---

### Post by pienose on 2007-10-08
Ok, I have looked every where for an answer and not found one, so I finally signed up to the forums! I can't seem to play .wma files in Exaile it loads all of my mp3's and plays them fine, but it won't load any of my wma's, help? I am pretty shore they are not protected, but is there a way I can check this?

hope some one can help!!

---

### Post by Gremlinzzz on 2007-10-08
I use exaile on xubuntu no problem its great but i did have to install these
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

---

### Post by reacocard on 2007-10-08
> **pienose said:**
> Ok, I have looked every where for an answer and not found one, so I finally signed up to the forums! I can't seem to play .wma files in Exaile it loads all of my mp3's and plays them fine, but it won't load any of my wma's, help? I am pretty shore they are not protected, but is there a way I can check this?

hope some one can help!!

It's likely just missing the right gstreamer plugin to open wma files, this should fix it:

```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg
```

---

### Post by pienose on 2007-10-08
ok, now if I go to the files tab and load a wma it will play it but even after re-building the database it still won't load it into the collection.

---

### Post by Polygon on 2007-10-08
in both 2.10 and 2.11... the star icons for the ratings do not show up and if i right click > info and then click on lyrics or artist... the program crashes.

---

### Post by Pathfinder_ on 2007-10-08
is there a way to import playlists in Exaile? I downloaded the newest version from the official website and can't figure it out. There is no import playlist button and drag 'n drop doens't work.

---

### Post by reacocard on 2007-10-08
> **Pathfinder_ said:**
> is there a way to import playlists in Exaile? I downloaded the newest version from the official website and can't figure it out. There is no import playlist button and drag 'n drop doens't work.

I believe file->open media can handle playlists.

---

### Post by Pathfinder_ on 2007-10-08
> **reacocard said:**
> I believe file->open media can handle playlists.

I just tried it and it does not work. Nothing happens :confused:

---

### Post by zarathustra on 2007-10-12
I'm having problems playing audio CDs with Exaile. I'm using an external USB CD drive and when I try to play a CD Exaile will not play it, it just says it's playing but nothing happens.

---

### Post by Depressed Man on 2007-10-17
Odd I've noticed a recent issue on both my Feisty desktop and Gutsy laptop..

Even if repeat is on, it won't go on to the next song in the playlist. I can queue any amount of songs and it'll just play the one I click and stops after it ends...

---

### Post by krul on 2007-10-19
Anyone knows how you can specify a soundcard explicitly in Exaile? It takes the wrong soundcard, can I put something in the settings.ini file?

Btw Rhythmbox is respecting the settings of the Ubuntu Gnome music&movie sound settings and playing on the right card (also using ALSA).

---

### Post by reacocard on 2007-10-19
> **krul said:**
> Anyone knows how you can specify a soundcard explicitly in Exaile? It takes the wrong soundcard, can I put something in the settings.ini file?

Btw Rhythmbox is respecting the settings of the Ubuntu Gnome music&movie sound settings and playing on the right card (also using ALSA).

Exaile just sends that data to the selected backend, usually ALSA or ESD. Try setting it to use ALSA explicitly in Edit->Preferences->Advanced->Playback Sink.

---

### Post by krul on 2007-10-19
> **krul said:**
> Anyone knows how you can specify a soundcard explicitly in Exaile? It takes the wrong soundcard, can I put something in the settings.ini file?

Btw Rhythmbox is respecting the settings of the Ubuntu Gnome music&movie sound settings and playing on the right card (also using ALSA).

I found back the Multimedia Systems Selector by loading gstreamer-properties, this will work! Strange that this settings differs from the settings under the System->Sound menu.....:confused:

Anyway, Exaile looks promising, clean, mean and powerful!

---

### Post by FuturePilot on 2007-10-19
Exaile 0.2.11 is out. It has video support! I am very impressed with Exaile. I love it.\\:D/

---

### Post by Polygon on 2007-10-20
the exaile site is down atm....but im using 2.11b and i still have the star ranking / lyric issues =/

---

### Post by olavjunior on 2007-10-21
When I try editing tags, the changes aren't kept. I push the save-button, but the file doesn't get updated. Am I missing some dependencies?

---

### Post by Soarer on 2007-10-22
It's more likely to be a permissions problem. Do you have permission to edit those files?

---

### Post by olavjunior on 2007-10-22
ok, maybe that was the problem. The files are kept on an external fat drive, so that's probably the case..

---

### Post by pt123 on 2007-10-22
Exaile has a nice interface with the tabs. Rating the songs is a pain compared to RB where you can do it on the playlist, while with Exaile you have to select the song then move your mouse up and use a drop down list to rate the song. And then move back down to select the next song to rate.

Also with dynamic playlists you can't limit the number of tracks to select like in Amarok, which is useful for mp3 players.

---

### Post by reacocard on 2007-10-22
> **pt123 said:**
> Exaile has a nice interface with the tabs. Rating the songs is a pain compared to RB where you can do it on the playlist, while with Exaile you have to select the song then move your mouse up and use a drop down list to rate the song. And then move back down to select the next song to rate.

Also with dynamic playlists you can't limit the number of tracks to select like in Amarok, which is useful for mp3 players.

Actually you can right-click the song and set the rating there as well.

---

### Post by sovereign_soul on 2007-10-23
Hi,

Exaile is no doubt a fantastic player, but there's one feature that I find missing. When we select songs from the collection in the side panel, there's no option to replace the current playlist by the selection. 

Like other players , I believe there should be an option to decide whether on double click the default action is to enqueue or to replace.

Another thing is about the plugins. Is there any reference from where I can get the list of available hooks or functions to develop plugins Or is it that the only way out is to browse the source ?

Thanks

---

### Post by reacocard on 2007-10-23
> **sovereign_soul said:**
> Hi,

Exaile is no doubt a fantastic player, but there's one feature that I find missing. When we select songs from the collection in the side panel, there's no option to replace the current playlist by the selection. 

Like other players , I believe there should be an option to decide whether on double click the default action is to enqueue or to replace.

Another thing is about the plugins. Is there any reference from where I can get the list of available hooks or functions to develop plugins Or is it that the only way out is to browse the source ?

Thanks

Those are good ideas, you should file requests for that on exaile's launchpad page. As for the plugins, exaile basically exposes EVERYTHING in the code to the plugins, so yeah, browsing the source is the way to go.

---

### Post by madmatrixz3000 on 2007-10-23
I cannot get the AWN plugin to work any ideas?

---

### Post by reacocard on 2007-10-24
> **madmatrixz3000 said:**
> I cannot get the AWN plugin to work any ideas?

are you running AWN? it has no purpose without it.

---

### Post by ajeffreys on 2007-10-24
Whenever I try and play an mp3 file in Exaile, it says I don't have the correct gstreamer plugin. Where can I find this plugin?

---

### Post by Soarer on 2007-10-24
You can install the gstreamer libraries from Synaptic. They come in 'good', 'bad' and 'ugly' flavours - install them all. The current version is 0.10 on my (Gutsy) machine.

No need to install the 'dbg' or 'doc' entries, just the one without an extension. You'll see what I mean in Synaptic.

You will need to have the 'Universe' repository enabled for the bad & ugly ones.

---

### Post by reacocard on 2007-10-24
> **ajeffreys said:**
> Whenever I try and play an mp3 file in Exaile, it says I don't have the correct gstreamer plugin. Where can I find this plugin?
```

sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg
```

that should let you play just about any file, including mp3s

---

### Post by ajeffreys on 2007-10-24
Thankyou very much, now it works great :)

---

### Post by pt123 on 2007-10-24
> **reacocard said:**
> Actually you can right-click the song and set the rating there as well.

You have to bring up 3 menus to set the rating.

Ridiculous.

---

### Post by reacocard on 2007-10-24
> **pt123 said:**
> You have to bring up 3 menus to set the rating.

Ridiculous.

In bzr it's only 2, might be 2 in 0.2.11 as well.

EDIT: and its not exactly trivial to allow setting the rating inline, you have to create a completely custom widget to do that.

---

### Post by Polygon on 2007-10-25
> **pt123 said:**
> You have to bring up 3 menus to set the rating.

Ridiculous.

what are you talking about?

when a song is playing, there is a rating thing on the top right. Click it and set a number...thats one menu. You can ALSO use the scroll wheel if your really lazy....0 menus

and like you said, if you right click a song > rating > select rating...thats 3

so...three ways of doing it.

and also...exaile 2.11 finally fixed the star rating / lyric crashing problem. woo and yay

---

### Post by Soarer on 2007-10-25
Great! I Love Exaile.


Any chance of an update to the 64bit version in the Exaile repos?

---

### Post by reacocard on 2007-10-25
> **Soarer said:**
> Great! I Love Exaile.


Any chance of an update to the 64bit version in the Exaile repos?

Maybe. I have to get the deb source from synic (or redo it myself), then ping tgm4883 to rebuild it as I don't yet have a 64-bit computer. (I should have one by the next exaile release so hopefully this will be the last time that 64-bit takes so long.)

---

### Post by Soarer on 2007-10-25
Thanks. 

I'm not nagging - I just used to have the latest & greatest Exaile when I was on 32bit machines, and there was always something worthwhile in every release.

---

### Post by NoSmokingBandit on 2007-10-27
Im on x86 gusty with a SBLive! card and when i use exaile i get no sound at all yet rhythmbox plays just fine. i dont even know where to start troubleshooting, so...

edit:
nvm, now it works. I uninstalled both exaile and rhythmbox, rebooted, installed exaile and now it works. Hopefully after my next reboot it will still work :\

---

### Post by kabanta on 2007-10-27
> **Pathfinder_ said:**
> I just tried it and it does not work. Nothing happens :confused:

Make sure to select "Playlist Files" (rather than "Media Files") in the pull-down menu below the file/directory listing pane. (Lower right-hand corner).

Apropos: does anyone know how to import Amarok *rating* information about music files? Importing playlists works fine, but it doesn't capture the rating information of the associated files (and I don't want to go back and enter all the rating information that has already been done).

---

### Post by reacocard on 2007-10-28
> **kabanta said:**
> Make sure to select "Playlist Files" (rather than "Media Files") in the pull-down menu below the file/directory listing pane. (Lower right-hand corner).

Apropos: does anyone know how to import Amarok *rating* information about music files? Importing playlists works fine, but it doesn't capture the rating information of the associated files (and I don't want to go back and enter all the rating information that has already been done).

There is no way to do that without MAJOR hacks, so no, its not currently possible to import ratings.

---

### Post by reacocard on 2007-10-28
> **Soarer said:**
> Thanks. 

I'm not nagging - I just used to have the latest & greatest Exaile when I was on 32bit machines, and there was always something worthwhile in every release.

A 64bit gutsy deb is now available on the site, enjoy!

---

### Post by Saneless on 2007-10-29
Just wanted to say thanks for this.

Amarok refused to install mp3 support, and all the other stupid players want soo badly to be itunes, they all forgot that sometimes I just want to PLAY a damn file.

Thank you for having the basic functionality of playing something instead of forcing me to add it to the library first, it's very appreciated.

---

### Post by NoSmokingBandit on 2007-10-29
on thing i would like to request in a future release:
In the pane on the left listing the artists, i would like to be able to highlight any artist, begin typing "c-o-h-e-e-d-......" and it would automatically scroll down to Coheed and Cambria. That works better for me than scrolling down through a ton of artists or trying to use the search.

---

### Post by reacocard on 2007-10-29
> **NoSmokingBandit said:**
> on thing i would like to request in a future release:
In the pane on the left listing the artists, i would like to be able to highlight any artist, begin typing "c-o-h-e-e-d-......" and it would automatically scroll down to Coheed and Cambria. That works better for me than scrolling down through a ton of artists or trying to use the search.

I'm not sure how simple that would be to implement... Perhaps simply move focus to the search box on typing?

---

### Post by NoSmokingBandit on 2007-10-29
i dont want it to go to the search box because i dont want it to narrow dont my artist list, i just want it to automatically scroll to what i am typing. I know wxMusik does this (the windows version at least, the linux version is hard as hell to compile) so maybe someone could have a look at their source? Im no programmer so i cant help out at all.

---

### Post by tarkka on 2007-10-29
So I tried to install it, and this is the problem I have...

Selecting previously deselected package exaile.
(Reading database ... 124908 files and directories currently installed.)
Unpacking exaile (from exaile_0.2b4_i386.deb) ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on python-pysqlite2; however:
  Package python-pysqlite2 is not installed.
 exaile depends on python-pyogg; however:
  Package python-pyogg is not installed.
 exaile depends on python-pyvorbis; however:
  Package python-pyvorbis is not installed.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile

---

### Post by NoSmokingBandit on 2007-10-29
install it from "Add/Remove." It should be in the repos if you enabled them all in gusty.

---

### Post by reacocard on 2007-10-29
> **NoSmokingBandit said:**
> i dont want it to go to the search box because i dont want it to narrow dont my artist list, i just want it to automatically scroll to what i am typing. I know wxMusik does this (the windows version at least, the linux version is hard as hell to compile) so maybe someone could have a look at their source? Im no programmer so i cant help out at all.

I see your point, you should file a wishlist bug for this against [exaile in launchpad]("https://launchpad.net/exaile").

> **tarkka said:**
> So I tried to install it, and this is the problem I have...

Selecting previously deselected package exaile.
(Reading database ... 124908 files and directories currently installed.)
Unpacking exaile (from exaile_0.2b4_i386.deb) ...
dpkg: dependency problems prevent configuration of exaile:
 exaile depends on python-pysqlite2; however:
  Package python-pysqlite2 is not installed.
 exaile depends on python-pyogg; however:
  Package python-pyogg is not installed.
 exaile depends on python-pyvorbis; however:
  Package python-pyvorbis is not installed.
dpkg: error processing exaile (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exaile

use gdebi instead of dpkg, or just 'sudo apt-get install' the things it says are not installed and try again.

EDIT: and that's a REALLY old version you're trying to install, get a newer one from exaile.org first.

---

### Post by tarkka on 2007-10-29
easy enough...thanks.  Out of curiosity, what do those files I was missing do?

---

### Post by reacocard on 2007-10-29
> **tarkka said:**
> easy enough...thanks.  Out of curiosity, what do those files I was missing do?

python-pysqlite2 is the python interface to SQLite databases which exaile uses to store the music library.
python-pyogg and python-pyvorbis allow python to handle .ogg files.

---

### Post by pt123 on 2007-10-29
> **Polygon said:**
> what are you talking about?

when a song is playing, there is a rating thing on the top right. Click it and set a number...thats one menu. You can ALSO use the scroll wheel if your really lazy....0 menus

That is the point I don't want to play the song just to rate it. 

In RB you can do it on the playlist. 

In Foobar2k the best music player, you can use shortcuts to assign 1 key - 1 star, 2 -star

---

### Post by uxbod on 2007-10-30
can it play RealAudio feeds ? I just tried and it hung the application :(

---

### Post by NoSmokingBandit on 2007-10-30
lol, i cant believe anyone actually has real files anymore :)
They are a really proprietary format so i dont think any app will handle them. I may be completely wrong, but im used to that. Do the files work in rhythmbox or something else?

---

### Post by xat_ on 2007-10-30
> **pt123 said:**
> That is the point I don't want to play the song just to rate it. 

In RB you can do it on the playlist. 

In Foobar2k the best music player, you can use shortcuts to assign 1 key - 1 star, 2 -star

Because Exaile is so extendible it's probable that your qualms can be easily rendered obsolete (assuming they haven't already). As far as accessing it goes, I can't really say I agree. Taking a look at the menu hierarchy it makes sense that you have to go through a few before you hit ratings.

Sounds more like you've simply grown accustom to Amarok. Especially if you believe it's the best player. Regardless, this "ridiculous" setup in Exaile isn't anything a simple plugin couldn't remedy.

---

### Post by reacocard on 2007-10-30
> **uxbod said:**
> can it play RealAudio feeds ? I just tried and it hung the application :(

If gstreamer supports it, exaile should be able to play it, though we may have to tweak some things to get stuff like tags working. Hanging the application sounds like maybe its having trouble contacting the server, see if it'll play in another gstreamer-based app like rhythmbox or totem-gstreamer.

---

### Post by pt123 on 2007-10-31
> **xat_ said:**
> Sounds more like you've simply grown accustom to Amarok. 

Amarok?? I mentioned RB- Rhythmbox & Foobar2k.

It is absurd to think that I have to go through and play every god damn song in my collection to rate them. 

Players that are new should make an assumption that people already have been using another music player. To import those settings & values would be beneficial in converting the user.

---

### Post by macogw on 2007-10-31
> **pt123 said:**
> Amarok?? I mentioned RB- Rhythmbox & Foobar2k.

It is absurd to think that I have to go through and play every god damn song in my collection to rate them. 

Players that are new should make an assumption that people already have been using another music player. To import those settings & values would be beneficial in converting the user.

shouldnt the rating be stored in the ogg or mp3's id3 data?  i know some players (like banshee) don't store id3 tags right (just like most photo managers suck at exif *looks at f-spot*) and just throw the info in their own db instead of doing it right

---

### Post by xat_ on 2007-10-31
> **pt123 said:**
> Amarok?? I mentioned RB- Rhythmbox & Foobar2k.

It is absurd to think that I have to go through and play every god damn song in my collection to rate them. 

Players that are new should make an assumption that people already have been using another music player. To import those settings & values would be beneficial in converting the user.

Misread; was responding to your post and reading another which really pressed upon Amarok. Anyway, it's already been pointed out that you don't *have* to play songs to rate them. Why not alter Exaile's default theme or functionality to suit your needs? Or at least make a feature request?

---

### Post by koleoptero on 2007-10-31
Does exaile have a graphic equaliser?

---

### Post by macogw on 2007-10-31
> **koleoptero said:**
> Does exaile have a graphic equaliser?

Yes, Tools > Equalizer

---

### Post by koleoptero on 2007-10-31
Really???? :-O

I'm downloading it now then :D


EDIT: They should replace Rhythmbox with Exaile. Far better, and better looking. Great job. Finally a GTK player that's worth it. Great great great. I don't know what else to say... :D

---

### Post by Morbett on 2007-11-01
figured it out

---

### Post by yongkailoon on 2007-11-01
Can anyone give me a full guide in installing Exaile from the requisites and then installing Exaile. I tried to install but I it is always the old Exaile that is installed. :(

---

### Post by NoSmokingBandit on 2007-11-01
you can get the newest version in Add/Remove programs. Also if you run 
sudo apt-get install exaile
it should install the latest version in the repos.

---

### Post by koleoptero on 2007-11-01
> **yongkailoon said:**
> Can anyone give me a full guide in installing Exaile from the requisites and then installing Exaile. I tried to install but I it is always the old Exaile that is installed. :(

Just go to the program's homepage [www.exaile.org](www.exaile.org) and download the package that's there for your system. It has both for gutsy and feisty. If you lack any dependencies they will be installed automatically.

---

### Post by Montsegur87 on 2007-11-02
Great app , I noticed that using exaile on a large database raises the memory footprint.

I have > 10 GB music and a constant 40 MB ram

---

### Post by reacocard on 2007-11-02
> **Montsegur87 said:**
> Great app , I noticed that using exaile on a large database raises the memory footprint.

I have > 10 GB music and a constant 40 MB ram

that's normal, exaile stores a large part of the db in ram, so the more music you have, the more ram it will use.

---

### Post by pt123 on 2007-11-02
> **macogw said:**
> shouldnt the rating be stored in the ogg or mp3's id3 data?  i know some players (like banshee) don't store id3 tags right (just like most photo managers suck at exif *looks at f-spot*) and just throw the info in their own db instead of doing it right

Rhythmbox stores it an XML which has all the info on your collection. So I was hoping Exaile would be able to read it. 

> **xat_ said:**
> Misread; was responding to your post and reading another which really pressed upon Amarok. Anyway, it's already been pointed out that you don't *have* to play songs to rate them. Why not alter Exaile's default theme or functionality to suit your needs? Or at least make a feature request?

That method would give me arthritis. I will check other themes. 

It's just that I was really impressed with the layout and look of Exaile, but its a pain to convert the collection from Rhythmbox. 

That said I fear like other Gnome apps this will become dead when the developer loses interest. This is where KDE has a better community development environment. 


I am still waiting for Google to develop a music player that uses Labels, because the Genre tag field is so limiting. 

Death to "Browse by Genre" :)

---

### Post by cwrann on 2007-11-03
nevermind

---

### Post by imdano on 2007-11-04
> **pt123 said:**
> That said I fear like other Gnome apps this will become dead when the developer loses interest. This is where KDE has a better community development environment. I'd say it's actually in very good shape as far as developer interest goes.  The project has has three full-time developers right now, and there are a bunch of us that regularly submit patches (and could probably step in if one or more developer leaves).

---

### Post by averagebeatboy on 2007-11-04
Exaile Rulez!  Try it you'll like it not as difficult as some others.

Cheers,

Averagebeatboy

---

### Post by koleoptero on 2007-11-05
I had a nice surprise from exaile :)

I noticed when I first used it that the equalizer was behaving a bit weird. The two last bands weren't doing what they were supposed to do. One was making sound from dull to overly-stereophonic like virtual surround or something, and the other was affecting speaker separation. I couldn't well place the effects at first. But yesterday it hit me.

In windows my sound card had some built in effects that you can manipulate from its app. I discovered that those two last bands of exaile's equalizer were the levels for SRS wow, and speaker separation. I couldn't do anything about those effects before in linux. Now I can LOL

Although I know this is sort of a bug or something, please don't fix it. :)

---

### Post by reacocard on 2007-11-05
> **koleoptero said:**
> I had a nice surprise from exaile :)

I noticed when I first used it that the equalizer was behaving a bit weird. The two last bands weren't doing what they were supposed to do. One was making sound from dull to overly-stereophonic like virtual surround or something, and the other was affecting speaker separation. I couldn't well place the effects at first. But yesterday it hit me.

In windows my sound card had some built in effects that you can manipulate from its app. I discovered that those two last bands of exaile's equalizer were the levels for SRS wow, and speaker separation. I couldn't do anything about those effects before in linux. Now I can LOL

Although I know this is sort of a bug or something, please don't fix it. :)

heh, its probably not us, more likely upstream gstreamer. Don't worry, we won't tell them. :mrgreen:

---

### Post by wyth on 2007-11-06
I so want to use this.  I've been checking back in on it for about three years now, and use it for streaming audio and playing music.  

But there's a few things that it really needs before it's as functionally as it could/should be.  Those fall under the categories of device support and granular podcast management, and granular control.

[U][B]Device Support
[/B][/U]This is getting better. The mass storage device plugin was a big help, and now Dan O'Reilly has been working on an mtp plugin ([see the launchpad page here]("https://bugs.launchpad.net/exaile/+bug/136061")). This isn't quite ready yet.  It will see items on a device, but I've had no success in getting it to transfer.  Seamless device support will push Exaile up a few notches.

_**Granular Podcast Management**_
This is one that irks me personally the most.  Exaile wants to be the Gnome answer to Amarok, but Amarok has got this one figured out, and Exaile doesn't. (Actually no Gnome app that I know of does.)  To wit:[LIST]
[*]Amarok will allow you to choose when you want to download a podcast with a right-click
[*]Amarok will allow you to choose where your podcasts are saved.[/LIST]Exaile and podcasts:[LIST]
[*]Exaile downloads all podcasts at once; you don't have control over what podcasts you download when.
[*]Exaile puts all its podcasts in a podcast file in the hidden .exaile folder.  This doesn't make sense.  At least keep them visible with the rest of the audio files.
[*]Exaile changes the titles of downloaded podcasts from human readable to a string of letters and numbers.
[*]If you delete a feed, it keeps the files.  Should have the option of deleting the files as well.[/LIST]These issues are showstoppers in some cases.  In my case, I keep all my audio on a separate partition available to a few different systems.  This makes using Exaile for my podcasts unusable.

It should be possible to determine the location where you want your podcasts saved.  Rhythmbox and Amarok manage this.  Amarok will also allow you to do it for each podcast feed -- keep one in your home folder, another with your music, another in another partition.  

Rhythmbox doesn't handle podcasting as well as Amarok, and when you transfer to an mtp device, it doesn't group them (so instead of one folder for This Week in Tech, you get five TWiT files in the topmost folder on the device).  This is again something else Amarok has figured out.

If Exaile could manage to get the device support up to snuff, allow you to keep files organized on the device, make it possible to choose where you save your podcasts, and choose to download each podcast one by one when you want to, then you'll really have something here.

---

### Post by reacocard on 2007-11-06
> **wyth said:**
> I so want to use this.  I've been checking back in on it for about three years now, and use it for streaming audio and playing music.  

But there's a few things that it really needs before it's as functionally as it could/should be.  Those fall under the categories of device support and granular podcast management, and granular control.

[U][B]Device Support
[/B][/U]This is getting better. The mass storage device plugin was a big help, and now Dan O'Reilly has been working on an mtp plugin ([see the launchpad page here]("https://bugs.launchpad.net/exaile/+bug/136061")). This isn't quite ready yet.  It will see items on a device, but I've had no success in getting it to transfer.  Seamless device support will push Exaile up a few notches.

_**Granular Podcast Management**_
This is one that irks me personally the most.  Exaile wants to be the Gnome answer to Amarok, but Amarok has got this one figured out, and Exaile doesn't. (Actually no Gnome app that I know of does.)  To wit:[LIST]
[*]Amarok will allow you to choose when you want to download a podcast with a right-click
[*]Amarok will allow you to choose where your podcasts are saved.[/LIST]Exaile and podcasts:[LIST]
[*]Exaile downloads all podcasts at once; you don't have control over what podcasts you download when.
[*]Exaile puts all its podcasts in a podcast file in the hidden .exaile folder.  This doesn't make sense.  At least keep them visible with the rest of the audio files.
[*]Exaile changes the titles of downloaded podcasts from human readable to a string of letters and numbers.
[*]If you delete a feed, it keeps the files.  Should have the option of deleting the files as well.[/LIST]These issues are showstoppers in some cases.  In my case, I keep all my audio on a separate partition available to a few different systems.  This makes using Exaile for my podcasts unusable.

It should be possible to determine the location where you want your podcasts saved.  Rhythmbox and Amarok manage this.  Amarok will also allow you to do it for each podcast feed -- keep one in your home folder, another with your music, another in another partition.  

Rhythmbox doesn't handle podcasting as well as Amarok, and when you transfer to an mtp device, it doesn't group them (so instead of one folder for This Week in Tech, you get five TWiT files in the topmost folder on the device).  This is again something else Amarok has figured out.

If Exaile could manage to get the device support up to snuff, allow you to keep files organized on the device, make it possible to choose where you save your podcasts, and choose to download each podcast one by one when you want to, then you'll really have something here.

These are very well-thought-out suggestions! Thanks for taking the time to put this together, I've shown this to the other devs and they agree with your points, so it's really just a matter of someone getting the motivation to work on this, maybe it'll get in the plans for 0.3.

---

### Post by imdano on 2007-11-07
> **wyth said:**
> The mass storage device plugin was a big help, and now Dan O'Reilly has been working on an mtp plugin ([see the launchpad page here]("https://bugs.launchpad.net/exaile/+bug/136061")). This isn't quite ready yet.  It will see items on a device, but I've had no success in getting it to transfer.Really?  That should be working with the latest couple of patches I uploaded on launchpad.  If you run exaile from a console, do you see any error messages popping up when you try transferring a track to the device?  Also, what kind of player are you using?

It'd probably be best to reply in the launchpad bug report, just so all the information regarding the plugin is in one place.

---

### Post by wyth on 2007-11-07
Hey, I'm glad the suggestions help.  I hope it didn't come off as sniping; if I had the python skills, I'd be doing what I can to help with this.  But I'm trained for a different kind of writing.

I just tried transferring files again, and  I think I didn't give it enough time last time.  There's no progress bar, and after a couple minutes, I didn't see any status change, and assumed the transfer didn't take.  I gave it a bit more time this time, and it worked just fine.  I noticed that sometimes it said "transferring" at the bottom of the application; it didn't always say this, but that may have been between transfers.

I'm using an iRiver T10 1gb media player that's perpetually stuck in the hell of mtp.  Turns out iRiver locked in mtp firmware for U.S. devices shortly before I bought it, and didn't advertise this fact until shortly after I bought it.  So much for iRiver.

Like Rhythmbox, Exaile puts all the files in the top-most folder of the device.  When the device is plugged in, it shows the files in folders organized by album in the application, but on the device itself, this isn't so.

I know I asked a lot in the first post, so I won't go too much farther now, but as I was adding files, I thought a right-click "add to device" option would be fantastic -- something that would add the file to the transfer queue.  Right now you have to add the files to a playlist and then drag them over.  It's no biggee, just a little clunky.

Thanks for the good response.  I've been watching this project since it began, and really like the direction it's heading.

---

### Post by imdano on 2007-11-07
> **wyth said:**
> I just tried transferring files again, and  I think I didn't give it enough time last time.  There's no progress bar, and after a couple minutes, I didn't see any status change, and assumed the transfer didn't take.  I gave it a bit more time this time, and it worked just fine.  I noticed that sometimes it said "transferring" at the bottom of the application; it didn't always say this, but that may have been between transfers.I think it should say "transferring" every time.  At the moment, most of the GUI related aspects of the transferring process are handled by exaile itself, not the MTP plugin.  I do think exaile provides a way to have a progress bar though, as does libmtp, so that's something I can probably add in the future.

> Like Rhythmbox, Exaile puts all the files in the top-most folder of the device.  When the device is plugged in, it shows the files in folders organized by album in the application, but on the device itself, this isn't so.I'm planning on storing tracks as Artist/Album/Title on the device, but it's being held back by some limitations in pymtp right now. Once that gets worked out upstream or I figure out a workaround that will get added.

---

### Post by wyth on 2007-11-07
imdano, you're a prince! (or a princess -- not sure.)

---

### Post by Steve Fisher on 2007-11-11
I loved Exaile, but for some reason it's not working for me anymore. Just hangs on "loading database...." :(

Back to Rhythmbox then, but it's not a patch on Exaile.

---

### Post by reacocard on 2007-11-11
> **Steve Fisher said:**
> I loved Exaile, but for some reason it's not working for me anymore. Just hangs on "loading database...." :(

Back to Rhythmbox then, but it's not a patch on Exaile.

hm, you could try resetting your db:
```
mv ~/.exaile/music.db ~/.exaile/music.db-old
```
you'll lose ratings and playcounts, but it might make it work again.

---

### Post by Sutur on 2007-11-14
Does anyone see a chance of exaile adding support/plugins for DSP/Effects?

The only things I think it really lacks are:

[LIST]
[*]Ability to just "Play" an item from the library instantly from a right click context menu, rather than adding it to the bottom of the playlist and/or queueing it.
This would also allow people to not have to add their entire collection as a playlist in order to find and play a song immediately.
[*]More layout themes, because gtk2.0 themes are great anyway :-)
[*]DSP/Effect Plugins. It's not remotely fair to compare Exaile with XMMS, but perhaps there is a way to enable support for XMMS plugins? I don't know, I'm not a programmer.
[/LIST]

---

### Post by reacocard on 2007-11-14
> [*]Ability to just "Play" an item from the library instantly from a right click context menu, rather than adding it to the bottom of the playlist and/or queueing it.
This would also allow people to not have to add their entire collection as a playlist in order to find and play a song immediately.
I like this idea, file a feature request ('wishlist' bug) [on launchpad]("https://launchpad.net/exaile/+filebug")
> 
[*]More layout themes, because gtk2.0 themes are great anyway :-)
contributions are welcome...

> [*]DSP/Effect Plugins. It's not remotely fair to compare Exaile with XMMS, but perhaps there is a way to enable support for XMMS plugins? I don't know, I'm not a programmer.
adding support for xmms plugins would likely be a nightmare. however, any sort of effect supported by gstreamer should be perfectly possible to add. we already support the equalizer and ReplayGain, adding more filters could be done the same way.

---

### Post by Sutur on 2007-11-14
> **reacocard said:**
> I like this idea, file a feature request ('wishlist' bug) [on launchpad]("https://launchpad.net/exaile/+filebug")

I tried to sign up but I still haven't received the registration E-mail. I smell a fuckup on my mailserver's part.

> **reacocard said:**
> adding support for xmms plugins would likely be a nightmare. however, any sort of effect supported by gstreamer should be perfectly possible to add. we already support the equalizer and ReplayGain, adding more filters could be done the same way.

OK, well I just did a tiny bit of research.

I'm in over my head but...from what I can understand ubuntu 7.10 comes with gstreamer-plugins-good, bad & ugly installed by default.

Regardless of whether they are or not, wouldn't that mean it should be quite easy to enable them...for example, some of the TAP-Plugins for LADSPA in Exaile through gstreamer.

I may be speaking absolute garbage here but I found a few gst-*-0.10 commands, and some examples on [this]("http://linux.die.net/man/1/gst-launch-0.10") website:

```
gst-launch filesrc location=music.mp3 ! mad ! audioconvert ! audioresample ! osssink
```

So then can I assume that every time someone clicks the play button in Exaile that's what's really happening?

Couldn't it be easy to just add a simple TAP-Plugin to the end of this command to add a specific effect?

Maybe you can clear this up for me, I'm sure I'm muddled somewhere.

---

### Post by reacocard on 2007-11-15
> **Sutur said:**
> I tried to sign up but I still haven't received the registration E-mail. I smell a fuckup on my mailserver's part.


Oh no problem, I'll file it for you then. I just prefer people to post their own requests since then they get notifications when its updated and it's easier to get more info if needed.

EDIT: bug filed: [https://bugs.launchpad.net/exaile/+bug/162811](https://bugs.launchpad.net/exaile/+bug/162811), you can subscribe youself to it once you get your account working.

> OK, well I just did a tiny bit of research.

I'm in over my head but...from what I can understand ubuntu 7.10 comes with gstreamer-plugins-good, bad & ugly installed by default.

Regardless of whether they are or not, wouldn't that mean it should be quite easy to enable them...for example, some of the TAP-Plugins for LADSPA in Exaile through gstreamer.

I may be speaking absolute garbage here but I found a few gst-*-0.10 commands, and some examples on [this]("http://linux.die.net/man/1/gst-launch-0.10") website:

```
gst-launch filesrc location=music.mp3 ! mad ! audioconvert ! audioresample ! osssink
```

So then can I assume that every time someone clicks the play button in Exaile that's what's really happening?

Couldn't it be easy to just add a simple TAP-Plugin to the end of this command to add a specific effect?

Maybe you can clear this up for me, I'm sure I'm muddled somewhere.

exactly, that's how the EQ and replaygain work, we just add one more component to the line.

---

### Post by koleoptero on 2007-11-15
Adding support for ladspa plugins would be excellent! With a good combination of TAP's parametric equalizer/BW, dynamics and tube warmth I have turned my simply good speakers sounding like studio professional ones :D

---

### Post by Sutur on 2007-11-15
> **reacocard said:**
> exactly, that's how the EQ and replaygain work, we just add one more component to the line.

Hah! I can't believe I actually worked that out myself. I'm not a dumbass after all lol

Okay well that sounds easy, is there any way I can help?

---

### Post by Steve Fisher on 2007-11-15
> **reacocard said:**
> hm, you could try resetting your db:
```
mv ~/.exaile/music.db ~/.exaile/music.db-old
```
you'll lose ratings and playcounts, but it might make it work again.

Yeah, thanks that worked. I did a bit of googling to try and see what was going wrong. It seems the database (pysql ??) was having trouble reading non-unicode characters, and was just stalling. I basically reinstalled that, and exaile (after removing the .exaile directory) and it seems fine now. I have noticed that this time the files it was having trouble reading simply havent been put into my library. Not a problem though - i didnt really like them anyway.

---

### Post by reacocard on 2007-11-15
> **Sutur said:**
> Hah! I can't believe I actually worked that out myself. I'm not a dumbass after all lol

Okay well that sounds easy, is there any way I can help?

It would help a lot if you could figure out exactly what you add to the gstreamer pipeline to use these plugins. If you know python at all and want to dig into the code a little replaygain and equalizer can be found in xl/player.py, starting at about line 357 in _create_sink().

---

### Post by Sutur on 2007-11-15
> **reacocard said:**
> It would help a lot if you could figure out exactly what you add to the gstreamer pipeline to use these plugins. If you know python at all and want to dig into the code a little replaygain and equalizer can be found in xl/player.py, starting at about line 357 in _create_sink().

OK I had a look at it but it's way over my head. I wish I could help but I'm not a programmer :(

---

### Post by reacocard on 2007-11-15
> **Sutur said:**
> OK I had a look at it but it's way over my head. I wish I could help but I'm not a programmer :(

that's alright. I'll file it as another feature request so we don't forget about it completely.

---

### Post by yakovyarmo on 2007-11-17
why the rating stars disappeared in exaile?
what can i do to see them back?

someone maybe know yhis problem?

---

### Post by Skorzen on 2007-11-17
Exaile is heavier than Audacious, so I still prefer this one.

---

### Post by Onyros on 2007-11-17
> **Skorzen said:**
> Exaile is heavier than Audacious, so I still prefer this one.OT: howdy, neighbour! ;)

---

### Post by Skorzen on 2007-11-17
> **Onyros said:**
> OT: howdy, neighbour! ;)

Hey mate! :)

(PM sent)

You guys sorry for the OT.

---

### Post by AJerman on 2007-11-17
Hey I just started using this yesterday and I've gotta say. I like it a lot. Great job with it so far. Keep up the great work. I hope development continues strong!

---

### Post by imdano on 2007-11-17
> **yakovyarmo said:**
> why the rating stars disappeared in exaile?
what can i do to see them back?

someone maybe know yhis problem?It's a known bug, but I don't think the root cause has been tracked down yet.

---

### Post by yakovyarmo on 2007-11-17
so what do you recomend to do?
not to use the rating system??

---

### Post by Kingsley on 2007-11-17
Have any of you experienced lower sound output with Exaile? It doesn't play my music as loud as Rhythmbox does.

---

### Post by reacocard on 2007-11-17
> **Kingsley said:**
> Have any of you experienced lower sound output with Exaile? It doesn't play my music as loud as Rhythmbox does.

its a bug in the gstreamer equalizer, either start exaile with --no-equalizer ro adjust the sliders in the EQ to fix it.

---

### Post by Kingsley on 2007-11-18
I didn't realize Exaile has an adjustable equalizer. Thanks for the tip.

---

### Post by boast on 2007-11-18
exaile does not keep saved equilizer settings upon reboot.

---

### Post by rabid9797 on 2007-11-18
i wish exaile had a nicer looking interface :( thats the only thing that is holding me back from using it full-time(right now im using songbird)

---

### Post by reacocard on 2007-11-18
> **boast said:**
> exaile does not keep saved equilizer settings upon reboot.

Um, yes it does, at least as long as you save it as a new profile.

> **rabid9797 said:**
> i wish exaile had a nicer looking interface :( thats the only thing that is holding me back from using it full-time(right now im using songbird)

what's wrong with it, specifically? I prefer it's appearance over songbird's myself.

---

### Post by andrewabc on 2007-11-18
Is it possible to remember the last played song? I have a playlist, and when I'm done listening to music I close exaile. When I reopen exaile it starts at the beginning of the playlist. I want it to start with the song I stopped at.

---

### Post by reacocard on 2007-11-18
> **andrewabc said:**
> Is it possible to remember the last played song? I have a playlist, and when I'm done listening to music I close exaile. When I reopen exaile it starts at the beginning of the playlist. I want it to start with the song I stopped at.

enable the 'resume playback' button

---

### Post by FuturePilot on 2007-11-18
I'm trying to play an audio CD in Exaile. It told me to install the python-cddb package, so I did. Now all of the tracks show up, but it won't play any of them. When I try to play a track the OSD comes up as if it's playing, but there's no activity on the CD drive and the progress bar just sits there at 0:00/x:xx

Odd, if I put the CD in the DVD drive it plays???

---

### Post by SomeGuyDude on 2007-11-19
I bow to ye, sir. This player is fantastic. I think it could be cleaned up in some ways (it feels like there's a bit too much blank space, but I'm a minimalist), but otherwise it's fan-dabby-dabulous.

One thing, though: what's with the 1-8 rating system? Who goes base-8 on ratings?

---

### Post by graabein on 2007-11-19
8-star rating? Strangeness... Why not go with the 5 stars and allow half stars like many magazines do. Just my opinion, no offence.

---

### Post by andrewabc on 2007-11-19
> **reacocard said:**
> enable the 'resume playback' button

I don't see this button anywhere. Screenshot?

EDIT:
I'd also like to say that I think Exaile is quieter than other programs. I'm listening to music, and if I go to youtube or something it drowns out the music and is louder than it. Same with ubuntu sounds, much louder than exaile. And I have to turn down my sound when I hear other sounds, then turn it back up for music.

EDIT:
According to exaile website, 0.2.11 has been released. I am still using 0.2.10
Is there a reason ubuntu has not notified me it has been updated? I have it on my repository. Or you I need to manually update it via the 
wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
sudo apt-get update
sudo apt-get install exaile
because ubuntu has not updated it yet on its servers?
Where is the changelog for exaile? It's nice to see the changes to know whether to update or not.

---

### Post by reacocard on 2007-11-19
> **andrewabc said:**
> I don't see this button anywhere. Screenshot?
Oh sorry, I meant plugin, not button. My bad.

> 
EDIT:
I'd also like to say that I think Exaile is quieter than other programs. I'm listening to music, and if I go to youtube or something it drowns out the music and is louder than it. Same with ubuntu sounds, much louder than exaile. And I have to turn down my sound when I hear other sounds, then turn it back up for music.

A known bug, see [http://ubuntuforums.org/showpost.php?p=3792199&postcount=1032](http://ubuntuforums.org/showpost.php?p=3792199&postcount=1032)
> 
EDIT:
According to exaile website, 0.2.11 has been released. I am still using 0.2.10
Is there a reason ubuntu has not notified me it has been updated? I have it on my repository. Or you I need to manually update it via the 
wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
sudo apt-get update
sudo apt-get install exaile
because ubuntu has not updated it yet on its servers?
Where is the changelog for exaile? It's nice to see the changes to know whether to update or not.
Ubuntu does not update versions after release, you have to add the Exaile repo via those commands to get continuous updates.

---

### Post by pt123 on 2007-11-19
> **graabein said:**
> 8-star rating? Strangeness... Why not go with the 5 stars and allow half stars like many magazines do. Just my opinion, no offence.


Yeah the rating feature is one of the few poorly thought aspects in this otherwise very good program.

---

### Post by koleoptero on 2007-11-19
So much hate... C'mon ppl show some love too :mrgreen:

---

### Post by SomeGuyDude on 2007-11-19
> **koleoptero said:**
> So much hate... C'mon ppl show some love too :mrgreen:

I got rid of amaroK to use this. Isn't that enough love? :guitar:

---

### Post by reacocard on 2007-11-19
The 8 star system was synic's decision, it's been in exaile from the start.  If you don't like it, take it up with him, but I doubt he'll change it.

---

### Post by andrewabc on 2007-11-19
> **reacocard said:**
> its a bug in the gstreamer equalizer, either start exaile with --no-equalizer ro adjust the sliders in the EQ to fix it.
I have EQ disabled. So in order to fix this bug I need to have some command run when starting exaile? Or enable the EQ and move the sliders until it sounds ok?
I'm a linux noob :)

---

### Post by reacocard on 2007-11-19
> **andrewabc said:**
> I have EQ disabled. So in order to fix this bug I need to have some command run when starting exaile? Or enable the EQ and move the sliders until it sounds ok?
I'm a linux noob :)

exactly. having EQ set to 'disabled' doesn't actually disable it, it just means it passes the sound through exactly as it was. Except, due to a bug, it lowers the volume instead. So, you must either change your exaile launcher to use 'exaile --no-equalizer', or adjust the sliders until it is at the desired level.

---

### Post by andrewabc on 2007-11-19
So I have an exaile shortcut on my taskbar, I go to icon properties and input
exaile --no-equalizer

Where it currently only has 
exaile
in the command area?
:)

Thanks. doing that seems to have worked so far. I'm really happy about the resume playback after closing plugin :)

Hmm, resume playback works funny. If I close exaile while playing and reopen it it auto starts playing where it left off in the song. If I stop the music playing, close exaile, reopen it it does not remember the last song that was playing when I stopped it. That is what I was looking for.
Even if I pause the song and restart exaile it does not remember the song. :(

---

### Post by reacocard on 2007-11-19
> **andrewabc said:**
> So I have an exaile shortcut on my taskbar, I go to icon properties and input
exaile --no-equalizer

Where it currently only has 
exaile
in the command area?
:)

Thanks. doing that seems to have worked so far. I'm really happy about the resume playback after closing plugin :)

Hmm, resume playback works funny. If I close exaile while playing and reopen it it auto starts playign where it left off in the song. If I stop the music playing, close exaile, reopen it it does not remember the last song that was playing. That is what I was looking for.

if you stop the music, exaile forgets what was playing even if you don't close it. Just use pause instead of stop.

---

### Post by andrewabc on 2007-11-19
> **reacocard said:**
> if you stop the music, exaile forgets what was playing even if you don't close it. Just use pause instead of stop.
Ok, I understand about the stop not remembering.

But I have tried pausing it numerous times, but it won't remember it after I reopen it.

---

### Post by reacocard on 2007-11-19
> **andrewabc said:**
> Ok, I understand about the stop not remembering.

But I have tried pausing it numerous times, but it won't remember it after I reopen it.

You should file a bug then: [https://bugs.launchpad.net/exaile/+filebug](https://bugs.launchpad.net/exaile/+filebug)

---

### Post by andrewabc on 2007-11-20
I replied to an existing "bug" that was there already.
[https://bugs.launchpad.net/exaile/+bug/157736](https://bugs.launchpad.net/exaile/+bug/157736)
:)
I think I had the same problem with amarok, which is one reason why I didn't like it. I forget if default ubuntu music player remembered my last played song, I don't think it did. How can these multimedia players not have this option? It is very basic and for me makes listening to music on linux pointless since I would have to remember the last song I was playing on my playlist.

Ok I tried updating exaile to the latest version 0.2.11, but it keeps saying I have the latest version and when I go to help->about it says I have the previous version 0.2.10

I tried the commands in terminal, and I also downloaded the deb file. If I go to synaptic package manager, it says I have exaile 0.2.11 installed.

Does this mean the "about" box in exaile is wrong?

---

### Post by Soarer on 2007-11-20
Mine says 0.2.11in 'help>>about' - I have the Exaile repositories enabled.

---

### Post by andrewabc on 2007-11-20
I didn't have it listed in my repositories so I added it, then ran terminal commands, and it still didn't install anything new. So I must have it installed since synaptic package manager says I have 0.2.11 installed. 

Now I check and it says in help->about 0.2.11 (Only thing different I did was edit sources, nothing was installed/upgraded).
This is odd because when I ran terminal commands it did not say anything was installed/upgraded/removed.

At least now it is up to date. Although it uninstalled my plugins that were running. But that took 1 min to re-enable

---

### Post by fedex1993 on 2007-11-24
i install exaile and when i try to play a song it says no gstreamer plugin or wrong gstreamer plugin any ideas

---

### Post by DjBones on 2007-11-24
> **fedex1993 said:**
> i install exaile and when i try to play a song it says no gstreamer plugin or wrong gstreamer plugin any ideas

do you have the good/bad/ugly plugin sets for gstreamer?
just sayin lol

---

### Post by erissiva on 2007-11-26
Is there any good reason why I wouldn't be able to use the exaile-bzr from the Gutsy repo? I get this error when starting:
```
 <module> ( /usr/lib/exaile/exaile.py @ 19):
-----------------------
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 145, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 137, in main
    exaile = exailemain.ExaileWindow(options, xl.path.firstrun)
  File "/usr/lib/exaile/xl/gui/main.py", line 147, in __init__
    self.setup_col_menus('track', trackslist.TracksListCtrl.col_map)
  File "/usr/lib/exaile/xl/gui/main.py", line 409, in setup_col_menus
    self.col_menus[v].set_active(show)
AttributeError: 'NoneType' object has no attribute 'set_active'

```

I have just seen some of the bug fixes on Launchpad and would love to reap the benefits. Is there a way to get get builds other than this? Or are there no daily/periodical builds?

---

### Post by reacocard on 2007-11-26
> **erissiva said:**
> Is there any good reason why I wouldn't be able to use the exaile-bzr from the Gutsy repo? I get this error when starting:
```
 <module> ( /usr/lib/exaile/exaile.py @ 19):
-----------------------
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 145, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 137, in main
    exaile = exailemain.ExaileWindow(options, xl.path.firstrun)
  File "/usr/lib/exaile/xl/gui/main.py", line 147, in __init__
    self.setup_col_menus('track', trackslist.TracksListCtrl.col_map)
  File "/usr/lib/exaile/xl/gui/main.py", line 409, in setup_col_menus
    self.col_menus[v].set_active(show)
AttributeError: 'NoneType' object has no attribute 'set_active'

```

I have just seen some of the bug fixes on Launchpad and would love to reap the benefits. Is there a way to get get builds other than this? Or are there no daily/periodical builds?

exaile-bzr tends to be updated at least once a week, I'll run an update right now, see if that fixes your problem.

EDIT: uploaded

---

### Post by erissiva on 2007-11-26
> **reacocard said:**
> exaile-bzr tends to be updated at least once a week, I'll run an update right now, see if that fixes your problem.

EDIT: uploaded

Hmmm...Well, the identifying part of the error changed, but the rest seems to be the same.

```
Exaile 0.2.12b
-----------------------
 <module> ( /usr/lib/exaile/exaile.py @ 19):
-----------------------
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 145, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 137, in main
    exaile = exailemain.ExaileWindow(options, xl.path.firstrun)
  File "/usr/lib/exaile/xl/gui/main.py", line 147, in __init__
    self.setup_col_menus('track', trackslist.TracksListCtrl.COLUMNS)
  File "/usr/lib/exaile/xl/gui/main.py", line 408, in setup_col_menus
    menu.set_active(col_struct.id in column_ids)
AttributeError: 'NoneType' object has no attribute 'set_active'

```

It starts up and closes without me seeing anything.
Is there a better log I could post for you to figure out what's wrong? Am I missing dependencies or something? Or is something just wrong on my end?

Sorry to bother!

[B]
EDIT[/B]: Actually, it was because the database or something wasn't correct. I just deleted the original .exaile folder and it seems to work fine.

---

### Post by onero on 2007-11-27
Hey, I just updated to the latest exaile-bzr, but now my playlists show nothing @_@ As in the playlists have no content, and even when I try to create a new playlist and add songs, nothing appears. Anyone have any idea what happened?

---

### Post by imdano on 2007-11-27
I think this will help you, onero.
[quote=One of Exaile's developers]The main devel branch has a bug caused by the fix for bug 144698 [1].
I'm working on it, but in the meantime you can simply re-enable columns
from View -> Columns.[/quote]Basically a fix for another bug caused everyone's columns to disappear.  Just reenable in the View menu.

---

### Post by onero on 2007-11-28
Yeah, that fixed it, thanks :D I feel silly now, haha.

---

### Post by imdano on 2007-11-28
Haha, yeah, it took me a pretty long time to figure out what was going on there.

---

### Post by fatejudger on 2007-12-05
I've been using the daily Exaile builds for a couple of weeks now, and I must admit I'm very impressed. The interface is leaps and bounds above current media players.

My only problem seems to lie with the MTP plugin. I installed all of the dependencies and the plugins able to get the list of songs, but it can't seem to play any of them. It just says this after trying to play 3 songs off of my Creative Vision:M:

[18:34:00] File does not exist: 390337
[18:34:03] File does not exist: 390027
[18:35:59] File does not exist: 673875

If someone knows how to fix this, please let me know!

---

### Post by reacocard on 2007-12-05
> **fatejudger said:**
> I've been using the daily Exaile builds for a couple of weeks now, and I must admit I'm very impressed. The interface is leaps and bounds above current media players.

My only problem seems to lie with the MTP plugin. I installed all of the dependencies and the plugins able to get the list of songs, but it can't seem to play any of them. It just says this after trying to play 3 songs off of my Creative Vision:M:

[18:34:00] File does not exist: 390337
[18:34:03] File does not exist: 390027
[18:35:59] File does not exist: 673875

If someone knows how to fix this, please let me know!

the mtp plugin is relatively new, it's not surprising there are still problems. [reporting a bug about this on launchpad]("https://bugs.launchpad.net/exaile/+filebug") is probably the best way to resolve your issue.

---

### Post by imdano on 2007-12-06
> **fatejudger said:**
> I've been using the daily Exaile builds for a couple of weeks now, and I must admit I'm very impressed. The interface is leaps and bounds above current media players.

My only problem seems to lie with the MTP plugin. I installed all of the dependencies and the plugins able to get the list of songs, but it can't seem to play any of them. It just says this after trying to play 3 songs off of my Creative Vision:M:

[18:34:00] File does not exist: 390337
[18:34:03] File does not exist: 390027
[18:35:59] File does not exist: 673875

If someone knows how to fix this, please let me know!Do you have the newest version of the plugin?  I updated it a couple of days ago, before then there wasn't support for playing files from the device.  You should also note that MTP players don't actually support playing directly from the device, the tracks have to be transfered to a temporary directory on the user's hard drive and played from there.  So if you try to drag a bunch of songs from the device panel into your playlist the player might freeze up for a little bit while the tracks transfer.

---

### Post by betes on 2007-12-07
I've just installed exaile to give it a try and I'm impressed.  Excellent work to all involved. I have a few questions that I searched around for answers to but can't find answers to. Thanks for any help with one or all of these:

1) Exaile playback is slightly quieter than Amarok (that is if both are set at the same %Volume).  Its not a problem, since Exaile is plenty loud, but I'm just curious if this is normal. 

2) This is more annoying: all of my aac files are organized alphabetically instead of in track order. I assume Exaile isn't reading the aac track number tag.  Is there a fix for this? 

3) When the collection is sorted by Artist, is there a way to make Various Artists albums appear as a single artist (rather than having each individual artist on a V/A album appear as a unique artist)? In Amarok you can right click and album and choose "Show Under Various Artists".  Any equivalent in Exaile?

Again, thanks for this great program.

---

### Post by zarathustra on 2007-12-09
Are there any plans to use musicbrainz for metadata retrieval? I listen to a lot of audio CDs and it can be annoying when it doesn't pick up track info.

---

### Post by panaretos22 on 2007-12-09
how did you find it?is really good?any bugs on it?

---

### Post by imdano on 2007-12-09
> **betes said:**
> I've just installed exaile to give it a try and I'm impressed.  Excellent work to all involved. I have a few questions that I searched around for answers to but can't find answers to. Thanks for any help with one or all of these:

1) Exaile playback is slightly quieter than Amarok (that is if both are set at the same %Volume).  Its not a problem, since Exaile is plenty loud, but I'm just curious if this is normal. .This is caused by a bug in the gstreamer equalizer.  Running exaile with the command line option --no-equalizer will bring the volume back to a normal level.

---

### Post by zarathustra on 2007-12-09
> **panaretos22 said:**
> how did you find it?is really good?any bugs on it?

If you're asking me then I really do like Exaile, and consider it the best audio player for the Gnome desktop at the moment. It's got a nice design and everything that I want to it to do works.

---

### Post by reacocard on 2007-12-09
> **zarathustra said:**
> Are there any plans to use musicbrainz for metadata retrieval? I listen to a lot of audio CDs and it can be annoying when it doesn't pick up track info.

No there are no plans right now, perhaps you should request this feature. (file a 'wishlist' bug against exaile in launchpad)

> **panaretos22 said:**
> how did you find it?is really good?any bugs on it?
Try it and find out. [http://www.exaile.org/downloads](http://www.exaile.org/downloads)

---

### Post by jdackle on 2007-12-09
You could also see synic (Exaile's author) first opening post for this thread... :lolflag:

Just trying it out - the official gutsy's repo's 0.2.10 version of it...

Finding it awesome though painfully slow on my 450Mhz Pentium III 512MB RAM PC...

Oh well...

---

### Post by reacocard on 2007-12-09
> **jdackle said:**
> You could also see synic (Exaile's author) first opening post for this thread... :lolflag:

Just trying it out - the official gutsy's repo's 0.2.10 version of it...

Finding it awesome though painfully slow on my 450Mhz Pentium III 512MB RAM PC...

Oh well...

try using the devel version (there's a repo on exaile's downloads page), and installing python-psyco. that may speed things up a bit (at the cost of using more ram).

---

### Post by plun on 2007-12-10
> **reacocard said:**
> and installing python-psyco. that may speed things up a bit (at the cost of using more ram).

Thanks reacocard....:)

python-psyco really boost my PC and I cannot say that it "eats" so
much resources.

(running exaile from bzr)

---

### Post by betes on 2007-12-10
Thanks to Imdano I got the volume worked out.

Also, updating to 0.2.11 seemed to solve the problem of not sorting aac a in tracks order (within an album). However, using daap streaming to listen to my music on my laptop (streamed from my desktop) the aac files still appear in my library in alphabetical order rather than according to the track number tag.

Is this a problem related to daap streaming or is there a chance one of my machines isn't as up-to-date as the other?

One more question: Does anyone know where to find a large image (.png or other) of the Exaile icon.  I use a launcher screenlet/widget and the Exaile icon is too small to appear clearly next to the other launchers.

Thanks, and again, this is a great program.

---

### Post by reacocard on 2007-12-10
> **plun said:**
> Thanks reacocard....:)

python-psyco really boost my PC and I cannot say that it "eats" so
much resources.

(running exaile from bzr)

it's about 5-10MB overhead for me. not terrible but noticable.

> **betes said:**
> Thanks to Imdano I got the volume worked out.

Also, updating to 0.2.11 seemed to solve the problem of not sorting aac a in tracks order (within an album). However, using daap streaming to listen to my music on my laptop (streamed from my desktop) the aac files still appear in my library in alphabetical order rather than according to the track number tag.

Is this a problem related to daap streaming or is there a chance one of my machines isn't as up-to-date as the other?

One more question: Does anyone know where to find a large image (.png or other) of the Exaile icon.  I use a launcher screenlet/widget and the Exaile icon is too small to appear clearly next to the other launchers.

Thanks, and again, this is a great program.

the daap plugin has its own sorting code, it's likely just not been updated to reflect the changes in the collection.  as for the icon, I have no idea but synic probably has one so you could ask him (arolson at gmail dot com).

---

### Post by jdackle on 2007-12-13
> **reacocard said:**
> try using the devel version (there's a repo on exaile's downloads page), and installing python-psyco. that may speed things up a bit (at the cost of using more ram).

Thanks reacocard!

I'll try it out the python-psyco thing and update to the latest stable Exaile - my system hasn't been so healthy lately and I don't want to install any development version at this moment; actually, I try and avoid dev unstable versions as much as possible.

Cheers!


EDIT: BTW, I've just noticed the GPG key from the Exaile repo is signed by you - are you the new main developer or the Ubuntu maintainer?

---

### Post by reacocard on 2007-12-13
> **jdackle said:**
> Thanks reacocard!

I'll try it out the python-psyco thing and update to the latest stable Exaile - my system hasn't been so healthy lately and I don't want to install any development version at this moment; actually, I try and avoid dev unstable versions as much as possible.

Cheers!


EDIT: BTW, I've just noticed the GPG key from the Exaile repo is signed by you - are you the new main developer or the Ubuntu maintainer?

You have to use the devel version to get psyco support, that's the only reason I say to do that.  Exaile devel tends to be quite stable though, and you can always upgrade smoothly to the next stable release when it comes out.

As for GPG, I maintain that repo and I am an exaile dev, but I am not the lead dev, synic is.

---

### Post by najames on 2007-12-18
Hmm, did the command for Exaile change or something?  

I have been using it to play streams from streamtuner for a long time, but since I updated Exaile this week it is borked.  Exaile will only play my MP3s on the hard drive now, no streams.

Exaile version 0.2.11
Streamtuner 0.99.99

Using the command exaile %q in streamtuner.

---

### Post by reacocard on 2007-12-18
> **najames said:**
> Hmm, did the command for Exaile change or something?  

I have been using it to play streams from streamtuner for a long time, but since I updated Exaile this week it is borked.  Exaile will only play my MP3s on the hard drive now, no streams.

Exaile version 0.2.11
Streamtuner 0.99.99

Using the command exaile %q in streamtuner.

Exaile has built-in internet radio support (you may need to enable a plugin or two), why not use that instead?

---

### Post by jdackle on 2007-12-18
> **reacocard said:**
> You have to use the devel version to get psyco support, that's the only reason I say to do that.  Exaile devel tends to be quite stable though, and you can always upgrade smoothly to the next stable release when it comes out.

As for GPG, I maintain that repo and I am an exaile dev, but I am not the lead dev, synic is.

Thanks for the clarification, reacocard!
I'll take a look at that later, no time now! :(

BTW, something in the latest stable release is weird! I made a typo for the album name of a local band's cd and now I can't seem to fix it. And I believe I could in the version Gutsy provides.

Later!

Tahnks! :)

---

### Post by najames on 2007-12-20
> **reacocard said:**
> Exaile has built-in internet radio support (you may need to enable a plugin or two), why not use that instead?

Ok, I installed the Exaile plugin for Shoutcast, but  it doesn't seem to have the ability to search for stuff like Streamtuner.  It also doesn't sort by bitrate correctly for some reason.

I have used Streamtuner/ripper for several years.  I guess it is a comfort factor plus I already have it set up to record to certain directories, etc.

I still don't see why it broke after the recent update, might be Streamtuner.  I changed Streamtuner to use Rhythmbox but still no joy.

---

### Post by mandrill on 2007-12-20
You do realize that Amarok works just fine in Ubuntu? As far as I'm concerned, Exaile is, well, NOT Amarok.........

---

### Post by SomeGuyDude on 2007-12-20
> **mandrill said:**
> You do realize that Amarok works just fine in Ubuntu? As far as I'm concerned, Exaile is, well, NOT Amarok.........

You're right! Good job. Exaile is, in fact, an entirely different piece of software that is quite independent of amaroK. Similarly, Ubuntu is not Sabayon and apple pie is not a cake. 

However, I don't like amaroK very much. It's a very nice program and if I used KDE I'd probably have it as default, but Exaile has a number of things that make it superior in my eyes.

1) Faster. amaroK takes a good 10 seconds to start up every damn time.

2) Less cluttered. amaroK has far too many features I don't need hogging screen space.

3) I love that Exaile has the little popup notification thingy. Mouse over the icon in the notification area, you get a little window of what the song is.

Amongst others. The application is simply better in my opinion and dangit it's gonna be hard for that to change.

---

### Post by shen-an-doah on 2007-12-20
> **SomeGuyDude said:**
> 3) I love that Exaile has the little popup notification thingy. Mouse over the icon in the notification area, you get a little window of what the song is.

Amarok does that too. As does Rhythmbox. As does probably most mp3 players...

---

### Post by FuturePilot on 2007-12-20
Just wondering if anyone knows if it's possible to have Exaile place songs in subdirectories when transferring to a device. Currently I have all my music on my player set up in Artist/Album/Song order. But I noticed when I transferred some songs it just dumped them in the root directory which could make a mess with a lot of songs.

---

### Post by koleoptero on 2007-12-20
> **mandrill said:**
> You do realize that Amarok works just fine in Ubuntu? As far as I'm concerned, Exaile is, well, NOT Amarok.........

Have you tried to use amarok with a dark GTK theme? It may work fine, but it doesn't follow gnome's appearance in no manner. That is reason enough for me not to use it.

---

### Post by imdano on 2007-12-21
> **FuturePilot said:**
> Just wondering if anyone knows if it's possible to have Exaile place songs in subdirectories when transferring to a device. Currently I have all my music on my player set up in Artist/Album/Song order. But I noticed when I transferred some songs it just dumped them in the root directory which could make a mess with a lot of songs.What kind of device is it?

---

### Post by Depressed Man on 2007-12-21
Hmm for some reason the playlist still isn't working for me, but starting exaile from the terminal doesn't show any messages.

---

### Post by FuturePilot on 2007-12-21
> **imdano said:**
> What kind of device is it?


It's my phone. I have it set up with the USB Mass Storage plugin to transfer the songs to the memory card and it works, but it seems to just throw the songs right into the root of my music directory.

---

### Post by imaca on 2007-12-21
Has anyone got Exaile working with spdif?
I have installed it but no sound - there doesn't seem to be any options to change settings, and spdif works with pretty much everything else.

---

### Post by stanna on 2007-12-23
how can i add a remote directory of music into this player? then ill be happy

---

### Post by krul on 2007-12-24
> **imaca said:**
> Has anyone got Exaile working with spdif?
I have installed it but no sound - there doesn't seem to be any options to change settings, and spdif works with pretty much everything else.

Try to fine-tune your settings in the multimedia selector by executing: "gstreamer-properties"

---

### Post by reacocard on 2007-12-24
> **stanna said:**
> how can i add a remote directory of music into this player? then ill be happy

not sure how you're accessing this 'remote directory', but exaile has a Music Sharing plugin that supports DAAP music shares (up to v6), and for smb shares you can always just mount them with cifs and access them like normal files.

---

### Post by Lukasz Tarkowski on 2007-12-29
Dude you saved me a lot of trouble :)
First I downloaded those files you said and then downloaded the newest version of exile from official site :)
[http://www.exaile.org](http://www.exaile.org)

---

### Post by coffee on 2007-12-30
This looks great.  I have run into one bug though, probably to do with my music organization.  some of my songs load and will play while a large majority give me this error:  

[14:28:42] File does not exist: /home/dad/Music/Jewel/Spirit/07_-_Jupiter.ogg
[14:28:42] File does not exist: /home/dad/Music/Jewel/Spirit/08_-_Fat_Boy.ogg
[14:28:42] File does not exist: /home/dad/Music/Jewel/Spirit/09_-_Enter_From_the_East.ogg
[14:28:42] File does not exist: /home/dad/Music/Jewel/Spirit/10_-_Barcelona.ogg
[14:28:42] File does not exist: /home/dad/Music/Jewel/Spirit/11_-_Life_Uncommon.ogg
[14:28:42] File does not exist: /home/dad/Music/Jewel/Spirit/12_-_Do_You.ogg
[14:28:42] File does not exist: /home/dad/Music/Jewel/Spirit/13_-_Absence_of_Fear.ogg
[14:28:42] File does not exist: /home/dad/Music/Jewel/This_Way/01_-_Standing_Still.ogg
[14:28:45] File does not exist: /home/dad/Music/Nirvana/Sliver (The Best Of The Box)/Lithium (Solo Acoustic Radio Appearance).ogg
[14:28:49] File does not exist: /home/dad/Music/Nirvana/Sliver (The Best Of The Box)/Sliver (Home Demo).ogg
[14:28:56] File does not exist: /home/dad/Music/Bob Dylan/Bob_Dylan - 02Bob_Dylan/02 - Talkin__New_York.ogg
[14:41:08] File does not exist: /home/dad/Music/Morphine/The Night/I'm Yours, You're Mine.ogg
[14:41:29] File does not exist: /home/dad/Music/Morphine/The Night/I'm Yours, You're Mine.ogg


If I can get this fixed I think I found me a new music player.

Thank you

After a reboot or two the problem seems to have gone away, I am able to listen to my songs know.  At least the ones I have tried.

> **Soarer said:**
> Mine says 0.2.11in 'help>>about' - I have the Exaile repositories enabled.

I have not been able to finde the Exaile repo string.  can you send me the string I need to add to my /etc/apt/source.list?  Thanks

---

### Post by CaptMorgan on 2008-01-02
I was wondering if there is a way to view the albums by  thier cover like in WMP or even a cover flow thing like iTunes? 

Exaile is my fav by far just love visualtions, thanks - Morgan

---

### Post by reacocard on 2008-01-03
> **CaptMorgan said:**
> I was wondering if there is a way to view the albums by  thier cover like in WMP or even a cover flow thing like iTunes? 

Exaile is my fav by far just love visualtions, thanks - Morgan

not yet, though it has been requested before and likely will be implemented at some point, probably as a plugin.

---

### Post by starfry on 2008-01-04
Hi, just found this looks great. I've installed 0.2.8 from Feisty repos, is there a way to get the latest version please? The exaile web site only mentions Gutsy. Thanks!

---

### Post by kissoffboardy on 2008-01-04
A while back in this thread, it was mentioned that Exaile would soon be usable with Foxytunes. Does anyone know how far away this is likely to be?

---

### Post by reacocard on 2008-01-05
> **starfry said:**
> Hi, just found this looks great. I've installed 0.2.8 from Feisty repos, is there a way to get the latest version please? The exaile web site only mentions Gutsy. Thanks!

latest version 0.2.11 is only packaged for gutsy, however under older versions you can probably find at least 0.2.10 for feisty. 

> **kissoffboardy said:**
> A while back in this thread, it was mentioned that Exaile would soon be usable with Foxytunes. Does anyone know how far away this is likely to be?

no idea. I've never seen the appeal of foxytunes myself though.

---

### Post by BreathEasy on 2008-01-05
I apologise if this has been answered before - I'm pretty sure it's been asked, but couldn't find a resolution.

Most radio streams I want to listen too are encapsulated in an .m3u playlist file. Maybe I'm doing this wrong, but if I try to add the playlist file to Exaile via Add Save Station, clicking on the station and clicking on the m3u URL I specified will just present a message of "Importing playlist..." in the status bar, but won't actually connect.

I find I have to download the .m3u file manually, cat/less/more it so I can find the URL of the ACTUAL radio stream, and embed that instead. Why is this necessary when Totem will load the .m3u and play the radio stream URL located inside it just fine?

My ideal situation would be so that I can go to my list of radio streams, which is a web page with a whole lot of .m3u files, click on one, and it'll open and start playing in Exaile. Until that happens, I have to keep using Totem since it knows what I want to do.

---

### Post by reacocard on 2008-01-05
> **BreathEasy said:**
> I apologise if this has been answered before - I'm pretty sure it's been asked, but couldn't find a resolution.

Most radio streams I want to listen too are encapsulated in an .m3u playlist file. Maybe I'm doing this wrong, but if I try to add the playlist file to Exaile via Add Save Station, clicking on the station and clicking on the m3u URL I specified will just present a message of "Importing playlist..." in the status bar, but won't actually connect.

I find I have to download the .m3u file manually, cat/less/more it so I can find the URL of the ACTUAL radio stream, and embed that instead. Why is this necessary when Totem will load the .m3u and play the radio stream URL located inside it just fine?

My ideal situation would be so that I can go to my list of radio streams, which is a web page with a whole lot of .m3u files, click on one, and it'll open and start playing in Exaile. Until that happens, I have to keep using Totem since it knows what I want to do.

file -> open file can handle playlists, maybe that will work better.

---

### Post by BreathEasy on 2008-01-05
> **reacocard said:**
> file -> open file can handle playlists, maybe that will work better.
I tried that. I went to "Open URL", entered the URL of a file ending in .m3u, got the same message - Importing playlist..., but all I could find was an extra entry at the bottom of my "Entire Playlist" list, with the same .m3u file!

Also, out of curiosity, in the Radio tab there are two extra folders: Podcasts and Radio Streams. I've been unable to work out what has to happen for Exaile to populate those.

---

### Post by chandru.in on 2008-01-05
Exaile rocks.  It is the only gnome audio player which can compete with Amarok.

Hope Ubuntu includes it by default.

---

### Post by Moustacha on 2008-01-05
I hope they sort out importing playlists. until then it's a big thumbs down from me unfortunately.

---

### Post by kissoffboardy on 2008-01-06
> **reacocard said:**
> latest version 0.2.11 is only packaged for gutsy, however under older versions you can probably find at least 0.2.10 for feisty. 



no idea. I've never seen the appeal of foxytunes myself though.

Ok, no problem. I guess it's horses for courses with that kind of thing. It appeals to me as I listen to a lot of random playlists whilst surfing the net, and it's nice to be able to skip from within the browser when a track I'm not in the mood for comes on. Also, most forums I go on have a "I'm now listening to" thread, but Foxytunes lets you stick that in your signature with a link for the curious. Saves time, but no good for post whores!



----------------
Now playing: [Psychic Ills - January Rain](http://www.foxytunes.com/artist/psychic+ills/track/january+rain)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by guren on 2008-01-12
Very nice player!
Finally something similar to Amarok, but a little lighter =)

The radio function is also fantastic! I get clear streams from japan and china =)

---

### Post by kodak on 2008-01-20
taking a look now

---

### Post by kodak on 2008-01-21
well, i had a blast with it and found it very nice, and would keep it installed if it was not for one limited feature

it's limited to playing 150.00 minutes so if i have an mp3 three hours long it will miss off the last 30 mins
to be fair most people will not have mp3's over 150.00

all in all a thumbs up

---

### Post by Pahanilmanlintu on 2008-01-24
I used exaile from maybe 0.2.2 or so onwards, but lately i've reverted to xmms, because of several showstopper bugs in 0.2.11. First it didn't seem to survive through scanning my collection. After i resolved character encoding issues in tags and filenames (musicbrainz picard <3), it managed to build the library, but didn't display anything in the library browser. I could still use the directory browser or drag files from nautilus, except that exaile would display the corresponding tags from some other, seemingly random, tracks instead of the ones i dragged. The right ones would still play, but those wrong ones would get uploaded to last.fm. In addition, at some version change the ipod plugin stopped exporting played tracks, which used to be one of exaile's attractive features.

Well anyway. I'll keep on checking out new versions when they come out, since it's still my favourite player, as long as it works. IIUC the next phase in exaile's developement is a rewrite towards version 0.3, correct? Is it coming along nicely?

Btw, A real working "start iconified" option is at the top of my feature wishlist.:)

---

### Post by pt123 on 2008-01-24
Is it possible to get the drag and drop cover management in RhythmBox? which is great as it is 10 times faster to fix crappy/wrong covers.

---

### Post by SomeGuyDude on 2008-01-24
My only desire would be to fix the weird AWN issues when using mini-mode.

I have Exaile as a launcher, and normally it's fine. I can minimize/maximize the window from the launcher icon. I go into mini-mode and a NEW icon pops up in my taskbar, and then the other one doesn't seem to work right. No idea why.

Also, when using "desktop cover", if a song comes around without an album cover, after that each album cover appears as a dark square on the desktop and it's only fixed after turning the plugin off and then turning it on again.

---

### Post by reacocard on 2008-01-25
> **SomeGuyDude said:**
> My only desire would be to fix the weird AWN issues when using mini-mode.

I have Exaile as a launcher, and normally it's fine. I can minimize/maximize the window from the launcher icon. I go into mini-mode and a NEW icon pops up in my taskbar, and then the other one doesn't seem to work right. No idea why.

AWN bug, not exaile.

> Also, when using "desktop cover", if a song comes around without an album cover, after that each album cover appears as a dark square on the desktop and it's only fixed after turning the plugin off and then turning it on again.

no idea, file a bug on launchpad.

---

### Post by sporkubus on 2008-01-26
I have one album that's behaving kind of strangely... none of the tag information loads in Exaile, and when I try to save tag info within Exaile, I get an "Unknown error"...

---

### Post by Chessmaster on 2008-02-01
I am very impressed with Exaile so far. I prefer it to Amarok which was crashing and doing a few funny things, especially after I had been using another audio aplication. 

One thing, do other people have problems retriving album covers from compilation albums. The Cover Art retriver thingy wants to pick album covers for each of the artists, not the actual album. So, if there are twenty different artists on the one album it will download a selection of *different* album covers. 

The album cover retriver seems to want to select by artist first, then album. Is it possible to change this to album first then artist without going through each cover individually? - especially annoying if you have lots of compiltaion albums. Or, is then another solution? I didn't have this problem in Amarok. 

Other than that, Exaile rocks.

---

### Post by KrazyPenguin on 2008-02-02
Wow this is the most amazing Music Player I have come across yet!!!!

Only been using it for about an hour, and it doesn't seem to be missing anything.

Much more stable than Amarok and it plays MMS streams and has an equalizer.

Response times are good and it blends into gnome nicely.

Just awesome!!!

Exaile should be included in Hardy.

+1 from me

;-)

---

### Post by komodojay on 2008-02-04
I love this player! Anyone figured out a way to make exaile the default player for your multimedia key instead of Rythmbox? I've tried to do the GConf-editor but I can find the keyboard shortcuts anywhere like others have suggested elsewhere  to try to change the default player.

---

### Post by chandru.in on 2008-02-04
Has anyone come across this bug while playing MP3s?

[https://bugs.launchpad.net/exaile/+bug/188633](https://bugs.launchpad.net/exaile/+bug/188633)

If so pls confirm it.

---

### Post by chandru.in on 2008-02-04
@komodojay

I just removed Rhythmbox and set Exaile as the multimedia app in "Preferred Applications".  Everything including global gnome shortcuts work now.

---

### Post by syxbit on 2008-02-04
i tried searching, but i can't seem to see anyone mentioning how everytime you load exaile it resets the sound to 70%
this has happened on every machine (x86 or x64) from edgy to gutsy.
i've heard some talk of it being alsa's fault, but no other app does it.
can i get rid of this?

---

### Post by Fraktyl on 2008-02-05
Move the volume slider above your playlist to 100%.  It'll stop setting the volume, then you can use alsa to control the volume.

---

### Post by syxbit on 2008-02-05
> **Fraktyl said:**
> Move the volume slider above your playlist to 100%.  It'll stop setting the volume, then you can use alsa to control the volume.

i tried that, but then i just get the same message with 100%
"Changing volume: 100%"

this is ridiculous

---

### Post by 3pleT on 2008-02-06
is there any way to make exaile read east european characters in the id3 tags? i wouldn't really care about it if i wasn't using audioscrobbler...

and i'm sorry if it was already mentioned, you wouldn't want me to read more than 100 pages now would you :P

---

### Post by reacocard on 2008-02-07
> **3pleT said:**
> is there any way to make exaile read east european characters in the id3 tags? i wouldn't really care about it if i wasn't using audioscrobbler...

and i'm sorry if it was already mentioned, you wouldn't want me to read more than 100 pages now would you :P

exaile still has a lot of trouble with unicode characters.  Try upgrading to the newest version (or even the devel version). If that doesn't fix it, it's probably not trivial to fix.

---

### Post by Radiera on 2008-02-18
I have 2 soundcards. The onboard hda-intel I want to use it for movies, browser sounds, headphones, so I gave it index=0 in alsa-base.
The second one, Audigy SE, is connected to my amplifier, I use it only for music. In amarok it was easy to configure the sound output. I can't find something similar in Exaile.

Has anybody found a way to change the sound output? I did some research, but found nothing.

---

### Post by reacocard on 2008-02-18
> **Radiera said:**
> I have 2 soundcards. The onboard hda-intel I want to use it for movies, browser sounds, headphones, so I gave it index=0 in alsa-base.
The second one, Audigy SE, is connected to my amplifier, I use it only for music. In amarok it was easy to configure the sound output. I can't find something similar in Exaile.

Has anybody found a way to change the sound output? I did some research, but found nothing.

Exaile always uses the default playback device, this is currently not configurable.

---

### Post by picpak on 2008-02-18
Anyone else have this bug?

[https://bugs.launchpad.net/exaile/+bug/164695](https://bugs.launchpad.net/exaile/+bug/164695)

It's very frustrating.

---

### Post by hrisk on 2008-03-01
I would like to add about Exaile too:
Pros:
1)Very nice looking 
2)Better functionality
3)Compact size
4)Ease in plugin adding-removal 
Cons:
 The only problem is that when i open the visualization effects from menu->view->Show visualizations the sound had a small glitch like a gap (or like something this)

---

### Post by SomeGuyDude on 2008-03-01
> **syxbit said:**
> i tried that, but then i just get the same message with 100%
"Changing volume: 100%"

this is ridiculous

After the first time, in 2.12b anyway, it doesn't do that any more. That used to drive me nuts, but it looks like for the new version they fixed it.

---

### Post by chandru.in on 2008-03-02
I had reported/commented on few bugs in Launchpad for Exaile.  Thought posting the links here would help in getting more people to look into it.

[https://bugs.launchpad.net/exaile/+bug/162760](https://bugs.launchpad.net/exaile/+bug/162760)
[https://bugs.launchpad.net/exaile/+bug/194994](https://bugs.launchpad.net/exaile/+bug/194994)
[https://bugs.launchpad.net/exaile/+bug/188633](https://bugs.launchpad.net/exaile/+bug/188633)

---

### Post by mAkKoOo210 on 2008-03-07
Well, I think I will upgrade my exaile soon, but I hope that a problem that I encountered has been solved (please, see [http://ubuntuforums.org/showthread.php?p=3756816#poststop)]("http://ubuntuforums.org/showthread.php?p=3756816#poststop")

---

### Post by rudihawk on 2008-03-08
Hey guys! Greetings from a new adoptee of exaile! - me likes it very much! :) Thanks.
Better than amarok IMHO

---

### Post by Beire on 2008-03-09
I really like exaile, although it seems to miss a very simple feature like every other music player i came across on linux.
I really need a way to sort my collection on "Album Artist" not just "artist" or "album".
I have a lot of albums with about 30 tracks per cd that all have different artists, yet the same Album artist.

This results in exaile (and every other audio player in linux) showing me tons of artists with only 1 song or so.

Windows media player handles this fine, although itunes can't do it either!

---

### Post by reacocard on 2008-03-09
> **Beire said:**
> I really like exaile, although it seems to miss a very simple feature like every other music player i came across on linux.
I really need a way to sort my collection on "Album Artist" not just "artist" or "album".
I have a lot of albums with about 30 tracks per cd that all have different artists, yet the same Album artist.

This results in exaile (and every other audio player in linux) showing me tons of artists with only 1 song or so.

Windows media player handles this fine, although itunes can't do it either!

this is a rather longstanding problem - there's a ticket on it and we have some ideas on implementing it, but noone has managed to implement it yet. It will be fixed by 0.3 at least, but hopefully sooner.

---

### Post by Beire on 2008-03-10
> **reacocard said:**
> this is a rather longstanding problem - there's a ticket on it and we have some ideas on implementing it, but noone has managed to implement it yet. It will be fixed by 0.3 at least, but hopefully sooner.


that would be fantastic!

---

### Post by BLWedge09 on 2008-03-12
I'm trying to enable the MTP support plugin which requires libmtp (which I have) and pymtp.  I can't find pymtp anywhere.  The link given by the app itself ( [http://nick125.com/projects/pymtp/](http://nick125.com/projects/pymtp/) ) has nothing there right now.

---

### Post by BLWedge09 on 2008-03-12
Well, nevermind.... I found it.  For anyone else confused like me, it's now here: [http://nick125.com/node/1](http://nick125.com/node/1)

---

### Post by reacocard on 2008-03-12
> **BLWedge09 said:**
> I'm trying to enable the MTP support plugin which requires libmtp (which I have) and pymtp.  I can't find pymtp anywhere.  The link given by the app itself ( [http://nick125.com/projects/pymtp/](http://nick125.com/projects/pymtp/) ) has nothing there right now.

hm, it appears the link has changed, here's the correct one: [http://nick125.com/node/1](http://nick125.com/node/1)

EDIT: ah you found it.

---

### Post by ctyc on 2008-03-13
its a good player.

---

### Post by Jahkel on 2008-03-14
On the front page of the Exaile website, it mentions a build-in shoutcast directory browser. Presumably this is the one you have to enable in the plugins list? (This isn't what id call "built-in"). Unfortunately it doesn't seem to work fro me at the moment in 0.2.11.  Is it broken?

Apart from this (and the character encoding bug) I really like Exaile and use it by default. It integrates very well in gnome and does pretty much what I want it for.  Excellent project.

---

### Post by cisforcojo on 2008-03-28
Love love love exaile!!! It's by far the best player for GNOME imo.

The only suggestion I have is improve the Album Art Collection function. A LOT of my songs are wrong and I'm pretty anal about naming the songs correctly on the id3 tags. (I usually don't include which album a song is from though but I figure it should at least get the artist right. And under no circumstances should it ever put a Best of the 70s CD as the source for the song ;)) 

It's a really really petty suggestion. If you never do it, it'll still be number 1.

---

### Post by zgerrz on 2008-04-29
Is there any way to implement LIRC support?

It would be a great convenience.

---

### Post by reacocard on 2008-04-29
> **zgerrz said:**
> Is there any way to implement LIRC support?

It would be a great convenience.

It could probably be done trivially as a plugin.  Its just not implemented because none of the devs use LIRC.  If you know some python you could probably write it yourself (look at the various keybinding plugins for examples). We'd certainly be willing to accept such a plugin were it to be made, and could also provide assitance to whoever is writing it.

---

### Post by zgerrz on 2008-04-30
ah that's too bad that i don't know any computer languages and have no time to learn one.

i hope someone with the right skills can implement this eventually.

---

### Post by Xorp21 on 2008-05-01
My new favourite player. Absolutely love it, I recommend it to everyone!

---

### Post by SomeGuyDude on 2008-05-01
It literally does not play on my machine. It scans my collection, I see all my files, when I click on an MP3 it loads up the album art and puts the right time on the progress bar, but it does not move past 0:00. I thought MPD was messing with it, but after killing MPD I still got the error. What's up?

---

### Post by swoll1980 on 2008-05-01
Does it have an eq?

---

### Post by SomeGuyDude on 2008-05-02
> **swoll1980 said:**
> Does it have an eq?

Exaile? Yeah. It's all right, but not great.

---

### Post by ivotron on 2008-05-05
> **SomeGuyDude said:**
> It literally does not play on my machine. It scans my collection, I see all my files, when I click on an MP3 it loads up the album art and puts the right time on the progress bar, but it does not move past 0:00. I thought MPD was messing with it, but after killing MPD I still got the error. What's up?

Try checking the value of the playback sink in Edit>Preferences>Advanced If auto is not working, then try picking the one that corresponds to your sound server (if any) or ALSA/OSS.

---

### Post by piterhansel on 2008-05-08
> **SomeGuyDude said:**
> It literally does not play on my machine. It scans my collection, I see all my files, when I click on an MP3 it loads up the album art and puts the right time on the progress bar, but it does not move past 0:00. I thought MPD was messing with it, but after killing MPD I still got the error. What's up?


The same with me...

I fixed that in hardy by installing “libflashsupport”

```
sudo apt-get install libflashsupport
```

---

### Post by prd on 2008-05-14
Exaile is the only player that I can use right now, but not without flaws. It's far above other linux player, but I still need something to be done in exaile, like ability to feed from directory in command line.

---

### Post by jryprt on 2008-05-14
> **swoll1980 said:**
> Does it have an eq?

Yes  you need to go to synaptic package manager search for gstreamer0.10-plugins-bad & install all the packages that are there 5 or 6 .
Then under tool in Exaile there is a eq.
Exaile is a GREAT player

---

### Post by _sAm_ on 2008-05-14
Tried Exaile now - it starts faster then Rhytmebox(I have a big collection), the coverart is very small, it cant tell if I am playing flac, I cant see if Exaile can use crossfade as Amarok and Rhytmebox. Hmm

---

### Post by reacocard on 2008-05-14
> **_sAm_ said:**
> Tried Exaile now - it starts faster then Rhytmebox(I have a big collection), the coverart is very small, it cant tell if I am playing flac, I cant see if Exaile can use crossfade as Amarok and Rhytmebox. Hmm

double-clicking on the coverart gives you the full view. 

what do you mean by "it can't tell if I'm playing flac"?

crossfade/gapless is not supported.

---

### Post by _sAm_ on 2008-05-15
> **reacocard said:**
> double-clicking on the coverart gives you the full view. 

I know. Its nice - but I would like to have a bigger picture all the time(like in Rhytmebox, Amarok and Banshee). One cool solution I think would bee a bigger picture all the time, and if you double-clicked the picture you would see the back-picture of the cd:-D

> what do you mean by "it can't tell if I'm playing flac"?
If you play mp3, ogg ++ Exaile will tell you witch bitrate/quality it has. If you play flac no information will show up at all, in Rhytmebox it will say "unknown" and in Amarok "flac", and in Audacious the bitrate.

> crossfade/gapless is not supported.
And thats a dealbraker.

---

### Post by LonelyTraveler on 2008-05-20
I blacklisted all my tracks because I wanted to do it over and could not find another way of removing it. The problem is that I also removed it from the blacklisting list, and now nothing wants to scan in again. How do I unblacklist the tracks? I uninstalled Exaile, delete the .exaile and all the other exaile files I could find, but I still have the same problem.

---

### Post by reacocard on 2008-05-20
> **LonelyTraveler said:**
> I blacklisted all my tracks because I wanted to do it over and could not find another way of removing it. The problem is that I also removed it from the blacklisting list, and now nothing wants to scan in again. How do I unblacklist the tracks? I uninstalled Exaile, delete the .exaile and all the other exaile files I could find, but I still have the same problem.

there's a blacklist manager in the edit menu, or deleting ~/.exaile/music.db should also work.

---

### Post by LonelyTraveler on 2008-05-20
> **reacocard said:**
> there's a blacklist manager in the edit menu, or deleting ~/.exaile/music.db should also work.

Thanks, but that didn't help. I removed everything from the blacklist manager before, but it doesn't help.

---

### Post by Xanderfoxx on 2008-05-20
Cool Beans! Amarok for GTK+! Amarok is one of the reasons I use Kubuntu. If I can get a killer app like that for GNOME Ubuntu, then I would need to have it.

---

### Post by amdlintuxos on 2008-05-23
[B]awesome player, i really like Amarok, but now i prefer GTK more than QT, so i am looking forward that this player became the best GTK player for GNOME and will be in standart repos in next ubuntu releases. 

Many thanks to originator and his project helpers, that take care around this stuff, u r doing great work.!!!
Player works fine, instead two things, 

1) there is no big usability to play files directly from sub-folders and sub-sub-folders. 
/folder1/
/folder1/file1.mp3
/folder1/folder2/file2.mp3
/folder1/folder2/folder3/file3.mp3
I know that i can use function to make library, but i want simple way just play music and that's all,if i don't like music i don't have to add it into DB
But i think that is because my stupid, i am queit new in GNOME invaroment, so it might be wrong hand ;) 
2) It would me nice to see function like in amarok,to get rid off right pannel when u don't need it, just simly hide it. That only playlist will be visible :) . But that can be my wrong hand too(((

In generally that is my favorite player
[/B]
**:guitar:let us cool music in GNOME GTK begin:lolflag:**

---

### Post by reacocard on 2008-05-23
> **amdlintuxos said:**
> [B]awesome player, i really like Amarok, but now i prefer GTK more than QT, so i am looking forward that this player became the best GTK player for GNOME and will be in standart repos in next ubuntu releases. 

Many thanks to originator and his project helpers, that take care around this stuff, u r doing great work.!!!
Player works fine, instead two things, 

1) there is no big usability to play files directly from sub-folders and sub-sub-folders. 
/folder1/
/folder1/file1.mp3
/folder1/folder2/file2.mp3
/folder1/folder2/folder3/file3.mp3
I know that i can use function to make library, but i want simple way just play music and that's all,if i don't like music i don't have to add it into DB
But i think that is because my stupid, i am queit new in GNOME invaroment, so it might be wrong hand ;) 
2) It would me nice to see function like in amarok,to get rid off right pannel when u don't need it, just simly hide it. That only playlist will be visible :) . But that can be my wrong hand too(((

In generally that is my favorite player
[/B]
**:guitar:let us cool music in GNOME GTK begin:lolflag:**

1) If you drag a folder from you file browser iinto the playlist pane it will recursively add all music in that folder

2) the side panel can be resized down to nothing using the grippy between it and the playlist area.

---

### Post by ubuhick on 2008-06-16
Can Exaile save preferred columns settings?  EXaile always starts with the default Columns "Title, Artist, Album, Length."  I add extras like "play count, Rating, ect.." and have to do this each time I start Exaile.

Is this a bug or am I missing the options somewhere?

---

### Post by RiceMonster on 2008-06-16
I'm looking forward to when the equalizer problem with Hardy gets fixed. I'm using the development version and it's still not working. In fact, it makes my flac files really noisy when I turn it on.

---

### Post by reacocard on 2008-06-16
> **ubuhick said:**
> Can Exaile save preferred columns settings?  EXaile always starts with the default Columns "Title, Artist, Album, Length."  I add extras like "play count, Rating, ect.." and have to do this each time I start Exaile.

Is this a bug or am I missing the options somewhere?

they should be saved. Make you're using the latest version (0.2.13), and if that version has this problem file a bug on launchpad.

> **RiceMonster said:**
> I'm looking forward to when the equalizer problem with Hardy gets fixed. I'm using the development version and it's still not working. In fact, it makes my flac files really noisy when I turn it on.
Sadly gstreamer's EQ just isn't very good, there's not much we can do about it.

---

### Post by RiceMonster on 2008-06-16
Ah, well I suppose I'll have to live without an equalizer for now. Keep up the good work by the way!

---

### Post by Commander_Bob on 2008-06-17
Excellent! I was using Listen 0.5 but when ever I tried to load my music it would freeze after 400 songs it also would not let me seek through the song. Exaile dose!
Thank you! Great player.
Justin

---

### Post by tabithaboof on 2008-06-18
I just started using exaile and I am a huge fan. There are a couple of amarok features I would like to know if are planned to be implemented. First one is the "statistics" which gives info like "most played artist/album/song" and the second is the context style browser?

Love the player though.

---

### Post by reacocard on 2008-06-18
> **tabithaboof said:**
> I just started using exaile and I am a huge fan. There are a couple of amarok features I would like to know if are planned to be implemented. First one is the "statistics" which gives info like "most played artist/album/song" and the second is the context style browser?

Love the player though.

there are no plans to implement either, but both could be implemented as plugins without much trouble.

---

### Post by besseriym on 2008-06-29
This player freakin rules. I just downloaded it today and I'm already a huge fan. Thank you for taking the time to make it so awesome! :D

---

### Post by blazemore on 2008-07-29
I really like the Dynamic Playlist feature in Exaile, and I want to know 
a) Is there an easy way of getting exaile to run on Windows? I can't seem to get gtk / libglade up and running
b) Is there a Windows app with similar functionality
c) Is there any chance of Exaile getting ported to native Windows?

---

### Post by reacocard on 2008-07-29
> **blazemore said:**
> I really like the Dynamic Playlist feature in Exaile, and I want to know 
a) Is there an easy way of getting exaile to run on Windows? I can't seem to get gtk / libglade up and running
b) Is there a Windows app with similar functionality
c) Is there any chance of Exaile getting ported to native Windows?

a) No, there is no automated installer, it has to be done by hand.
b) not to my knowledge
c) none of the current devs really use windows, but we are certainly open to contributions towards making the exaile experience on windows as good as the one in linux, should anyone be inclined to provide such support.

---

### Post by MatthewPlanchard on 2008-08-06
Hey Reacocard,

I'm picking a media player to use on default - I've been using Amarok, and so far today I've given Songbird and Banshee extensive testing.  Songbird uses way too much RAM for my tastes, and Banshee is really really excellent.  Now I'm tasting Exaile, and I really like its Amarokish left-side pane for browsing through media (probably the only feature Banshee lacks).

My only complaint with Exaile, and this is a deal breaker for me, is that it won't fetch my covers.  My music is 90% downloaded from Jamendo, and so the format is Album - Artist - JamendoInfo/Title.mp3 for the music and Album - Artist - JamendoInfo/[cover] Title.jpg for the covers.

I have put *.jpg *.png *.gif for the cover manager, and there are no other images in the music folders.

It still does not seem to work; Exaile will not grab a single cover, and the only way for me to get them to show is to Add a custom cover.

---

### Post by reacocard on 2008-08-06
> **MatthewPlanchard said:**
> Hey Reacocard,

I'm picking a media player to use on default - I've been using Amarok, and so far today I've given Songbird and Banshee extensive testing.  Songbird uses way too much RAM for my tastes, and Banshee is really really excellent.  Now I'm tasting Exaile, and I really like its Amarokish left-side pane for browsing through media (probably the only feature Banshee lacks).

My only complaint with Exaile, and this is a deal breaker for me, is that it won't fetch my covers.  My music is 90% downloaded from Jamendo, and so the format is Album - Artist - JamendoInfo/Title.mp3 for the music and Album - Artist - JamendoInfo/[cover] Title.jpg for the covers.

I have put *.jpg *.png *.gif for the cover manager, and there are no other images in the music folders.

It still does not seem to work; Exaile will not grab a single cover, and the only way for me to get them to show is to Add a custom cover.

I'm afraid that * syntax isn't supported right now. The only way to get it to work is to either rename all the covers to cover.jpg or the like, or to set them all by hand. 0.3's cover handling system should be a bit more flexible for things like this, but that will not be released for a while yet.

---

### Post by MatthewPlanchard on 2008-08-06
Thanks for the info!

If the wildcard function is implemented, please do post here! I've got a subscription set up.

---

### Post by Atallicus on 2008-08-07
I've seen a couple screenshots where on their gnome panel they have a thing that says "Exaile-"song playing".  I would love to have my panel say what song I am listening to all the time.  I use Music Applet but it doesn't show the song name all the time.  Is there a plugin for this?

---

### Post by Tucatts on 2008-08-07
Hey, wow thanks Synic! Great job, installed and running fine. Man I am actually understanding the Linux file system. lol. Taken a while but I am getting there. Good thing too since my XP HD died a horrible death a couple of days ago, wondered where all that grinding noise was coming from, LOL. Hey dual booted with Ubuntu so I have not missed a step and I am going windows free now! Anyway listening to Alison Krauss right now on my new music player.

---

### Post by ntowakbh on 2008-08-08
I found this media player not two days ago....and I instantly replaced Quod Libet with it.  It doesn't crash like Quod Libet was.  I even made a script for conky that displays the currently playing song, artist, and album, if anyone wants the script they can message me.

But yes, Exaile is amazing, I was able to configure pretty much all of my keyboard shortcuts over ten times faster for fluxbox, than I spent on Quod Libet.

---

### Post by tromort on 2008-08-09
Awesome! But, when I exit exail and on a different time open it again, the colums are reset to the defaults, my other settings are still normal the way I like them but the colums get reset.

---

### Post by misterspider on 2008-08-20
> **imaca said:**
> Has anyone got Exaile working with spdif?
I have installed it but no sound - there doesn't seem to be any options to change settings, and spdif works with pretty much everything else.

I would love to use Exaile, but i am connected with spdif and cannot get it working satisfactorily. 
I have Mythbuntu installed, and currently use Amarok for music. Both are using sound through spdif and working well. 
I tried configuring Exaile with "gstreamer-properties" but no sound whatsoever.

I created a ".asoundrc" file and put 

pcm.!default spdif

in the file. This works (sound now comes out) but quality is no good, it sounds like my speakers are vibrating badly 
(same songs with Amarok are crystal clear).
 What else can i try? Is there a simple plugin for Exaile, or one planned?

---

### Post by reacocard on 2008-08-20
> **misterspider said:**
> I would love to use Exaile, but i am connected with spdif and cannot get it working satisfactorily. 
I have Mythbuntu installed, and currently use Amarok for music. Both are using sound through spdif and working well. 
I tried configuring Exaile with "gstreamer-properties" but no sound whatsoever.

I created a ".asoundrc" file and put 

pcm.!default spdif

in the file. This works (sound now comes out) but quality is no good, it sounds like my speakers are vibrating badly 
(same songs with Amarok are crystal clear).
 What else can i try? Is there a simple plugin for Exaile, or one planned?

Currently there's no way to do this, but Exaile 0.3 will allow you to set the audiosink parameters however you want, enabling things like this.

---

### Post by hullap on 2008-09-09
> **synic said:**
> Already done!  There's an xchat plugin here: [http://www.exaile.org/files/exaile_xchat.pl](http://www.exaile.org/files/exaile_xchat.pl), and one for irssi here: [http://www.exaile.org/files/exaile_irssi.pl](http://www.exaile.org/files/exaile_irssi.pl) - both you just load and type /exaile when you want to display the song you're playing.

Adam

anyone still got the script? irssi one

---

### Post by reacocard on 2008-09-09
> **hullap said:**
> anyone still got the script? irssi one

its in the scripts directory in the exaile source tarball.

---

### Post by hullap on 2008-09-09
thanks

---

### Post by ZootHornRollo on 2008-11-04
i upgrade mt ubuntu 7.10 machine to 8.04 yesterday and now i can't get exaile - or any other music player - to play any audio files.

in exaile which is my prefered programme i get ```
'NoneType' object has no attribute 'songs'
```

any ideas?

---

### Post by LunaEqualsLuna on 2008-11-11
Brilliant music player, really great job, thanks a ton for this it works great!:guitar:

---

### Post by eternalnewbee on 2008-11-11
I have compiz running. Are there any conflicts when running both applications at the same time?

---

### Post by DoctorBeaver on 2008-11-11
I got this error message when trying to install:-

Couldn't find package libgstreamer0.10

---

### Post by ratmandall on 2008-11-11
> **DoctorBeaver said:**
> I got this error message when trying to install:-

Couldn't find package libgstreamer0.10
Are you sure you did the first terminal command? on the first post.
If not then.
```

sudo apt-get install libgstreamer0.10-0
```

---

### Post by reacocard on 2008-11-11
> **ratmandall said:**
> Are you sure you did the first terminal command? on the first post.
If not then.
```

sudo apt-get install libgstreamer0.10-0
```

note that the instructions on the first post are a couple years out of date. See [http://www.exaile.org/downloads](http://www.exaile.org/downloads) for more up to date instructions.

---

### Post by DoctorBeaver on 2008-11-11
Ratmandall - That command said:-

libgstreamer0.10-0 is already the newest version.
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 lmms-common libqt3-i18n libflac++6 libsdl-sound1.2 libmikmod2
  libwxbase2.6-0 stk libstk0c2a libsmpeg0

But I still got:-

Couldn't find package libgstreamer0.10

I can't be bothered with all that stuff it says to do on the downloads page so I'll stick with what I've got. Thanks for your help anyway.

---

### Post by Moustacha on 2009-04-25
Exaile is finally usable for me. It supports loading a playlist made somewhere else. About time. It's replaced my amarok needs now.

---

### Post by schnelle on 2009-04-26
I hate new Amarok... I tried all players I heard of... but I didn't like any of them. But Exaile rocks! Clean and simple look... It was love at first sight... a few minutes ago ;)   :lolflag:    :guitar:

---

### Post by schnelle on 2009-04-26
Ok I have problem now. I cannot find commands for next song, stop, play...
In Windows Winamp are c,x,b,z, the similar are in Amarok but in Exaile are different... Please help me with this simple task ;)

---

### Post by poulixgr on 2009-06-23
Hi, I'm new to this forum and this is my first post.

I have a question, especially for you who are actively developing this great player or things about it(like the plugin for gtk-desktop-info for example).

Is there a way for me to get the cover art of the currently playing song? And then do whatever I want with it, like save it in a file or work with it with things like imagemagick? Perhaps any of the plugins available right now does something similar and saves it somewhere in a temporary file(like the Desktop Cover plugin)?

I tried to read the python code in the gtk-desktop-info plugin and try to find how it grabs the artwork to display it on the desktop but I was completely lost in the code. ConkyExaile has helped me to grab any other info that I wanted(title, artist, track number, album, year etc) but I have no luck with the artwork.

---

### Post by inkisbetter on 2009-10-16
> **reacocard said:**
> It's likely just missing the right gstreamer plugin to open wma files, this should fix it:

```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg
```

this one worked for me 10/16/09 in Kubuntu 9.04 (just thought I'd share since the rest of these posts are pre-9.04). 

Thanks!

---

### Post by RiceMonster on 2009-10-16
Old thread is old

---

### Post by Megrimn on 2009-10-16
haha, really old.  But I hadn't heard of exaile before now.

---

### Post by Elfy on 2009-10-16
Now you have I can close the thread :)

---

