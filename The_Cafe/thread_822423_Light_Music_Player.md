---
title: "Light Music Player"
date: 2008-06-08
forum: The Cafe
---

### Post by intense.ego on 2008-06-08
I have a large collection of music (roughly 34,000 songs) stored on my external HDD and have been using amarok to play it for quite some time. However, it is very slow especially when searching. I am looking at something lightweight that would run super fast.

I just installed mp3blaster and although it is very fast, the search function is terrible. It is not even searching. You can type one letter only and it takes you down to that area of the playlist (because it is organized alphabetically).

I don't care if the music player is terminal-based or not, as long as it is fast and has a good search capability. If it could be minimized to the notification area that would be even better. Essentially, I am looking for a lightweight, faster, less frivolous amarok.

My specs, in case you should need it, is a Core Duo 1.83ghz processor (NOTE: not core 2 duo) and 2.5 gb of DDR2 667mhz RAM (it is a laptop).

Thank you

---

### Post by dsm iv tr on 2008-06-08
Rhythmbox has always been very quick for me (Celeron-D @ ~2 ghz, 1GB), and it does everything you need. One annoyance is that it does not minimize to tray on close, you have to either click the tray icon again, or type CTRL+W.

Something faster and smaller might be xmms2 - you can use any frontend you want, web, gtk, qt, python, etc.

If you want a "light Amarok", you can try Exaile. It's Amarok, but faster.

sudo aptitude install exaile

should do it for you.

Good luck.

---

### Post by Barrucadu on 2008-06-08
Quod Libet is a fairly good music player. The search function isn't amazing, but it gets the job done. You enter a term, and it lists all songs with that term in one of the tags.

---

### Post by Steveway on 2008-06-08
If you haven't allready then you should set up a MySQL or even better a PostgreSQL database for Amarok.
That will speed it up significantly. How-tos are accessable through Google.

---

### Post by loell on 2008-06-08
mpd + ncmpc :KS

---

### Post by intense.ego on 2008-06-08
I tried Rhythmbox first because it was already installed and because i had used it once right at the start, and I have to say, it is very very fast. Faster than amarok and even faster than a terminal based player like mp3blaster.

My only problem is that closing the window, closes the whole application. Is there any way of making it go to the notification area instead? 

Also, is there a way to skin the player? the looks are a bit plain for me

---

### Post by Jesuses Left Leg on 2008-06-08
If you were set on Rhythmbox you could minimize it to the tray with alltray (in the repositories).

---

### Post by urukrama on 2008-06-08
Use mpd with either ncmpc (console) or Gmpc or sonata (gui) as front ends. Gmpc has a nice search feature, and plenty of views to choose from (File system, playlist, artist/album, tags, Database search, etc)

It is light and does a good job of handling large collections. Both Sonata and Gmpc have system tray icons.

---

### Post by speedemonV12 on 2008-06-08
how do you set up mpd with your music collection on an external drive? 

(mines on another partition, similiar to what this guy wants, i have been experiencing a lot of slowness while searching, and banshee freezes all the time, Rhythmbox is the only one that works well, but i am looking for alternatives)

---

### Post by chucky chuckaluck on 2008-06-08
*cplay* is similar to mpd, minus the pain in the butt setup. on my laptop, i found exaile to be an even bigger hog than amarok and slightly more finicky.

---

### Post by loell on 2008-06-08
> **chucky chuckaluck said:**
> *cplay* is similar to mpd, minus the pain in the butt setup. on my laptop, i found exaile to be an even bigger hog than amarok and slightly more finicky.

hey hey :)  , yeah I think cplay is better, i'm trying to use it, is there any additional component to install to play mp3 files?

---

### Post by robertchahine on 2008-06-08
there's defenitly rythmbox.And you can try exaile

---

### Post by bruce89 on 2008-06-08
<sarcasm>
```
gst-launch-0.10 filesrc location=$FILE ! decodebin ! audioconvert ! alsasink
```
</sarcasm>

---

### Post by TenPlus1 on 2008-06-08
I use MPD and Gimmix to play my music as I have loads stored on my pc also...

MPD and Sonata are a good combo as well for easy access AND since MPD is a daemon it plays in the background while you log in and out :)

---

### Post by loell on 2008-06-08
> **bruce89 said:**
> <sarcasm>
```
gst-launch-0.10 filesrc location=$FILE ! decodebin ! audioconvert ! alsasink
```
</sarcasm>

not bad for the minimalist at all, i wonder if there are python script around that uses (gstreamer + ncurses), I'd imagine this will still be considered a lite player.

---

### Post by speedemonV12 on 2008-06-08
this may not be light, but the new Banshee 1.0 is amazing and searches fast, try it out

---

### Post by alwiap on 2008-06-08
i use VLC with a playlist, it works great and I just search for what I want.  Plus, all my media is in the same playlist.

---

### Post by urukrama on 2008-06-08
> **loell said:**
> hey hey :)  , yeah I think cplay is better, i'm trying to use it, is there any additional component to install to play mp3 files?

Use mpg123 to play mp3 files in cplay. You could also use mpg321 (such original names!), but I've found that to use an aweful lot of resources on my old laptop (about 5 times more than mpg123).

---

### Post by loell on 2008-06-08
thanks I installed mpg123, and just passed -n in cplay exec :)

---

### Post by SomeGuyDude on 2008-06-08
> **loell said:**
> mpd + ncmpc :KS

Yes, but Sonata instead of ncmpc. :guitar:

---

### Post by mcduck on 2008-06-09
> **speedemonV12 said:**
> how do you set up mpd with your music collection on an external drive? 

(mines on another partition, similiar to what this guy wants, i have been experiencing a lot of slowness while searching, and banshee freezes all the time, Rhythmbox is the only one that works well, but i am looking for alternatives)

I usually setup MPD by creating symlinks from all internal & exteral music directories to MPD's default music directory.

Works great, even with removanbble drives (just don't sync your library if the removable drive isn't connected)..

---

### Post by OmniCloud on 2008-06-11
Right now I'm trying to figure out Cplay. So I'm toying between that and MOC right now. Moc is pretty good, I just don't know how to manually change the theme colors instead of using the 5 or 6 pre-installed ones. 

Cplay uses whatever fonts/theme you have for your terminal which I like--but I still haven't found out how to actually view my playlist yet. After you add a song by pressing "a" naturally, how do you view and save the playlist you just created? 

Also, is MPD/Sonata just for people with servers? I have a bunch of music on an external drive thats always connected to my PC, but couldn't figure out how to play it with Sonata before?

I just read the post uptop, how do you create "simlinks"?

---

### Post by mcduck on 2008-06-12
> **OmniCloud said:**
> Right now I'm trying to figure out Cplay. So I'm toying between that and MOC right now. Moc is pretty good, I just don't know how to manually change the theme colors instead of using the 5 or 6 pre-installed ones. 

Cplay uses whatever fonts/theme you have for your terminal which I like--but I still haven't found out how to actually view my playlist yet. After you add a song by pressing "a" naturally, how do you view and save the playlist you just created? 

Also, is MPD/Sonata just for people with servers? I have a bunch of music on an external drive thats always connected to my PC, but couldn't figure out how to play it with Sonata before?

I just read the post uptop, how do you create "simlinks"?

MPD works just great as desktop music player as well. Actually it's the only one I use any more. :D

To create a symbolic link, use the "ln -s"-command. For example to create a link from a music directory on a removable drive to MPD's music directory the command would be something like this: "sudo ln -s /media/usbdrive/music /var/lib/mpd/music/usbdrive".

I recommend labeling the partition on your removable drive so it will always automount with the same name.

---

### Post by mthei on 2008-06-12
I've used MPD for quite some time, and would also recommend it, although I no longer use it because I do not need a full library and sometime just need to play single files from a different location. But the Sonata client for MPD is by far the friendliest of the ones I've tried.

If you're not married to the idea of having a library-based player, you can try Audacious (the Ubuntu repositories have the latest version (1.5), which is far more stable than previous versions, and rests at around 8 to 10mb of RAM usage, which is less than half of what version 1.4 uses - one of the things that makes me want to go back to Ubuntu). Or if you're not opposed to compiling, there's a recent version of XMMS released in December (not too recent, but at least it's still being updated after all).

For library based players, I like QuodLibet. Very fast, you can choose from serveral browser layouts, and customise how artists are categorized.

---

### Post by urukrama on 2008-06-12
> **OmniCloud said:**
> I still haven't found out how to actually view my playlist yet. After you add a song by pressing "a" naturally, how do you view and save the playlist you just created? 

Press 'tab' and you will see the playlist. Press 'tab' again and you are back in the file system. 'd' deletes a song from the playlist, 'D' clears the playlist. You can mark files with 'space'. 

K.Mandla has [a good post about cplay]("http://kmandla.wordpress.com/2007/05/01/howto-use-cplay-like-a-pro/"). You might find it useful.

---

### Post by blithen on 2008-06-12
You could always use the command line for this. I recommend CMUS, very fast and very light(considering it's curses player)

---

### Post by OmniCloud on 2008-06-14
> **mcduck said:**
> MPD works just great as desktop music player as well. Actually it's the only one I use any more. :D

To create a symbolic link, use the "ln -s"-command. For example to create a link from a music directory on a removable drive to MPD's music directory the command would be something like this: "sudo ln -s /media/usbdrive/music /var/lib/mpd/music/usbdrive".

I recommend labeling the partition on your removable drive so it will always automount with the same name.ok...I'm a little slow. What exactly do I have to do here? edit the config file for mpd? 

So how do I go about playing music with Sonata+mpd? 

my music is on my built in drive at home/omnicloud/media 

how do I get sonata to play music from that directory? I edited the config in /mpdconfig to refelct that directory but sonata is still empty?

---

### Post by OmniCloud on 2008-06-14
> **urukrama said:**
> Press 'tab' and you will see the playlist. Press 'tab' again and you are back in the file system. 'd' deletes a song from the playlist, 'D' clears the playlist. You can mark files with 'space'. 

K.Mandla has [a good post about cplay]("http://kmandla.wordpress.com/2007/05/01/howto-use-cplay-like-a-pro/"). You might find it useful.yea, helped a bunch, I use this over moc now simply because it's more configurable in how it looks. tks for the link 2.

---

### Post by mister_k81 on 2008-06-14
> **intense.ego said:**
> 

My only problem is that closing the window, closes the whole application. Is there any way of making it go to the notification area instead? 


Yes, just click on the Rhythmbox icon in the notification area to hide it.. If you're using Gnome that is. I'm not sure if it also works in KDE.

---

### Post by JPorter on 2008-06-30
I'm a huge fan of Audacious.  It's one of the few players that doesn't fall on its face and die when you load large amounts of music into a playlist, has very good file handling behavior, and is flexible enough for my purposes.

I'd really prefer a linux version of Foobar2000, but it doesn't seem that that's actually going to happen anytime soon.

---

### Post by mthei on 2008-06-30
> **JPorter said:**
> 
I'd really prefer a linux version of Foobar2000, but it doesn't seem that that's actually going to happen anytime soon.

Well, if you feel like using Wine, it's supposed to work, or there's [this](http://sourceforge.net/projects/boofar), which I haven't tried, so I can't really say how close it is. Plus it looks like it hasn't been updated in a while.

---

