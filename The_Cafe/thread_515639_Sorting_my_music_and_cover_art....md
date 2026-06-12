---
title: "Sorting my music and cover art..."
date: 2007-08-02
forum: The Cafe
---

### Post by mmcmonster on 2007-08-02
Hi.
  I am in the process of updating all my mp3s with proper ID3 tags and coverart.  Is there a standard naming convention for cover art so that it is picked up my various applications (ie: amarok, itunes, rhythmbox, songbird)?

Currently, I am naming them "artist name - album name.jpg" (with songs named "artist name - album name - song name.mp3"), but that's definitely not being picked up my amarok. :-(

---

### Post by djgrandmarquis on 2007-08-02
For some reason, amarok doesn't seem to like long names for cover art. When I use "cover.jpg" that tends to work well. I would avoid spaces in the names too.

Have you tried Kid3? It's really nice for tagging mp3's.

---

### Post by Circus-Killer on 2007-08-02
great tagging prog --> easytag

best file convention for cover art  --> cover.jpg

unfortunetly, rhythmbox NEVER looks locally for cover art, which i think is stupid. always ends up fetching the wrong cover art off of the net.
my recommendation, use Exaile! instead of rhythmbox, its in the repos, and it kicks rhythmbox's ***. (its like amarok for gtk) 

:guitar:

---

### Post by happy-and-lost on 2007-08-02
> **Circus-Killer said:**
> 
unfortunetly, rhythmbox NEVER looks locally for cover art, which i think is stupid. always ends up fetching the wrong cover art off of the net.
my recommendation, use Exaile! instead of rhythmbox, its in the repos, and it kicks rhythmbox's ***. (its like amarok for gtk) 


Seems to be the exact opposite for me. RB will pick up coverart in local folders (which I've lovingly collected), but Exaile picks up the wrong art 9 times out of 10 and ignores my local art. Amarok has a good cover manager, but uses its own strange database.

---

### Post by Nekiruhs on 2007-08-02
> **happy-and-lost said:**
> Seems to be the exact opposite for me. RB will pick up coverart in local folders (which I've lovingly collected), but Exaile picks up the wrong art 9 times out of 10 and ignores my local art. Amarok has a good cover manager, but uses its own strange database. +1 for Exaile
In Exaile you can just drag and drop on to the Album Art place and it will replace whatevers there.

---

### Post by mmcmonster on 2007-08-03
cover.jpg sucks if you want to have more than one album per directory.

I bought a lot of compilation CDs over the last couple decades, and am going through them and retagging all the songs with the original album information.

It's a lot of work, but it lets me scan my library for all songs from 1973, etc.

---

### Post by UbuWu on 2007-08-03
[Pinky-Tagger]("http://pinkytagger.sourceforge.net/") is very nice for this.

---

### Post by mmcmonster on 2007-08-06
> **djgrandmarquis said:**
> For some reason, amarok doesn't seem to like long names for cover art. When I use "cover.jpg" that tends to work well. I would avoid spaces in the names too.

Have you tried Kid3? It's really nice for tagging mp3's.


It's too bad about amarok, since that's what I've been using. :-(

Is there a bug open for using other naming conventions for cover art images?

---

### Post by reacocard on 2007-08-06
Ex Falso is the best tag editor I know of.

For covers, doing cover.jpg is the safest, it is picked up by almost all players.

---

### Post by Xaviar on 2007-08-18
I'm about to make make the move back to Ubuntu from Vista, and I have a library of thousands of painstakingly tagged MP3's.  Do none of the players simply read the ID3 tags and use embedded cover art?   I have many folders which contain MP3's with different cover art, will I really have to go back to putting them in their own folders with a separate picture file?  Will the MP3's show up as icons in the music folder instead of being displayed as thumbnails of their embedded cover art?

---

### Post by reacocard on 2007-08-18
> **Xaviar said:**
> I'm about to make make the move back to Ubuntu from Vista, and I have a library of thousands of painstakingly tagged MP3's.  Do none of the players simply read the ID3 tags and use embedded cover art?   I have many folders which contain MP3's with different cover art, will I really have to go back to putting them in their own folders with a separate picture file?  Will the MP3's show up as icons in the music folder instead of being displayed as thumbnails of their embedded cover art?

I do not think any do yet. It has been requested for Exaile, but has not been implemented yet.

---

### Post by Golyadkin on 2007-08-18
I love Rhythmbox, it just downloads album art on the fly when I play music. That way I never have to actually go and find it.

---

### Post by reacocard on 2007-08-18
> **Golyadkin said:**
> I love Rhythmbox, it just downloads album art on the fly when I play music. That way I never have to actually go and find it.

Exaile does so too, but neither is 100% accurate.

---

### Post by maniacmusician on 2007-08-18
> **reacocard said:**
> I do not think any do yet. It has been requested for Exaile, but has not been implemented yet.
I'm pretty sure amarok always does this? I always embedd images right into the tags, since it's the most reliable method.

---

### Post by Xaviar on 2007-08-31
> **Golyadkin said:**
> I love Rhythmbox, it just downloads album art on the fly when I play music. That way I never have to actually go and find it.

That wouldn't work out too well for me.  I have a lot of obscure stuff (including my own music) and I'm pretty particular (perhaps a little too particular) about what art is displayed. 

> **maniacmusician said:**
> I'm pretty sure amarok always does this? I always embedd images right into the tags, since it's the most reliable method.

Really?  Do the ID3 thumbnails show up in Nautilus instead of MP3 file icons like they do in Vista Explorer?  Or does the cover art only show up in the player?

---

### Post by Spike-X on 2007-09-01
> **Xaviar said:**
> Do none of the players simply read the ID3 tags and use embedded cover art?  

That'd be too bloody easy.

As would allowing player software to actually embed artwork in ID3 tags, so they can be read across platforms*, apparently.



* ie, If I associate album art with songs using AmaroK, why not embed the artwork in the actual file so it can be read by, say, iTunes?

---

### Post by joshzam on 2007-09-02
I've been using Amarok for my entire Linux Life (aka, the past four months). I've recently grown curious as to other apps. Here's my current opinions and how they handle cover art:

_Amarok:_ correctly reads the embedded artwork directly from the file. Too bad the app takes so darn long to load! I'm gonna try to avoid KDE based apps on my Ubuntu setup from now on.

_Exaile:_ can't read embedded artwork but offers an "Album Art Collector" to download images. I have meticulously tagged my collection (including images) and starting from scratch is not an option for me. Too bad, too, since the app shows promise. Similar to Amarok but runs faster. I'm looking forward to future versions.

_Banshee:_ correctly reads the embedded artwork directly from the file. But I've had nothing but problems with this one - it hung three times while trying to import my collection! Buggy with hiccups. It's running now but it's just too 'simple' for my needs/wants.

Still waiting for the "perfect" solution.

---

### Post by Parkotron on 2007-09-02
As has been mentioned, Amarok pretty much leads the way in album art support (other than that long filename thing). But,as has also been mentioned, it stores the images in its internal database.

Enter [CopyCover]("http://www.kde-apps.org/content/show.php?content=22517"), an Amarok script that copies album covers out of the database and into the album folder. 

I realise Amarok's not for everyone, but with this script it might be the best tool for organising your album covers, even if you don't use it to play your music.

Now if only there were script to copy covers from the database into the files themselves.

---

### Post by joshzam on 2007-09-02
Wow, I had no idea that Amarok stored the cover art in a separate database. I don't like that at all! I need my art embedded in the mp3 itself so I can migrate to other players and/or OSs whenever I want.

---

### Post by ThrobbingBrain66 on 2007-09-02
I haven't read the whole thread, but I prefer using folder.jpg for my cover art and using tagtool for mp3 tagging.

---

### Post by macogw on 2007-09-02
I really like Banshee, but it doesn't "watch" the library for songs you've manually put into its folder.  I switched to Songbird because of that, but Songbird doesn't do cover art, it appears...Doesn't matter so much since I don't stare at my music player, but I liked Banshee's notification area thing that'd pop up the song, artist, and album art.

---

### Post by joshzam on 2007-09-02
There's a Windows app called *Album Cover Art Downloader* and that's exactly what it does - beautiful simplicity. It's one of the three reasons why I still visit my Win partition. I hope someone comes up with an elegant Linux version sometime soon.

---

### Post by joshzam on 2007-09-04
Album Cover Art Downloader is available for Linux!

So, for those interested, you can either [download the tarball]("http://ftp.roedu.net/mirrors/gentoo.org/distfiles/") (search for *albumart-1.6.0.tar.gz*) and and compile it yourself, or you can alternately [pick up the DEB]("http://www.unrealvoodoo.org/hiteck/projects/albumart/") - but If you use Ubuntu 7.04, make sure to add the following magic comment:
[COLOR="Blue"]#coding:utf-8[/COLOR]
in the first line of this file:
[COLOR="Blue"]/usr/lib/albumart/albumart_images.py[/COLOR]
in order for Python to interprete the encoding of the file properly, otherwise the file is wrongly interpreted as an ASCII file and a syntax error is thrown when the application launches.

---

### Post by martin_prince on 2007-09-06
> **joshzam said:**
> Album Cover Art Downloader is available for Linux!

So, for those interested, you can either [download the tarball]("http://ftp.roedu.net/mirrors/gentoo.org/distfiles/") (search for *albumart-1.6.0.tar.gz*) and and compile it yourself, or you can alternately [pick up the DEB]("http://www.unrealvoodoo.org/hiteck/projects/albumart/") - but If you use Ubuntu 7.04, make sure to add the following magic comment:
[COLOR="Blue"]#coding:utf-8[/COLOR]
in the first line of this file:
[COLOR="Blue"]/usr/lib/albumart/albumart_images.py[/COLOR]
in order for Python to interprete the encoding of the file properly, otherwise the file is wrongly interpreted as an ASCII file and a syntax error is thrown when the application launches.

Thanks a lot!  I downloaded it, made the change, and yep, it works great.  I think it does add some sort of meta-data to the .ogg files, as when I set an albumn cover for a directory full of oggs, it goes through all of them and updates them.  I don't know if it is just putting in the path of the album art or if it is actually embedding the image, but it looks like it is putting something in there.

I was able to do my whole collection pretty quickly and now discs that were iffy on albumn art before, work great, thanks for the tip!

---

### Post by manfo on 2007-09-14
> **maniacmusician said:**
> I always embedd images right into the tags

Uh! How do you do that?

---

### Post by maniacmusician on 2007-09-14
> **manfo said:**
> Uh! How do you do that?
I use easytag to tag all the mp3's that I have. it's in the repos. The interface is a bit clunky, but once you get used to it, it's pretty easy to use.

---

### Post by linuxguy on 2007-10-17
I had always embedded artwork into the ID3 tags with easytag, and Amarok read them correctly... until I upgraded to Mandriva 2008. Now Amarok does not display the cover art anymore. It is very aggravating...

---

### Post by n3tfury on 2007-10-17
> **linuxguy said:**
> I had always embedded artwork into the ID3 tags with easytag, and Amarok read them correctly... until I upgraded to Mandriva 2008. Now Amarok does not display the cover art anymore. It is very aggravating...

good to know, because all of my lossy and lossless files are embedded in this fashion.  hopefully it works under ubuntu.

---

### Post by maku-d on 2007-10-24
I just found that problem in amarok too. For some reason now all the 
artwork is garbled. I also tag my files using easytag with embedded 
images. Hadn't noticed the problem until today. Not sure what would 
be causing it. Anyone know how to fix this problem? While I'm at it... 
does anyone recommend the switch to amarok-svn for gutsy?

---

### Post by pt123 on 2007-10-24
> **Nekiruhs said:**
> +1 for Exaile
In Exaile you can just drag and drop on to the Album Art place and it will replace whatevers there.

I tried this on 2.10 and it does nothing.

---

### Post by bb10 on 2007-10-24
Try gmusicbrowser or foobar2000 if you're on windows.

---

### Post by pt123 on 2007-10-24
> **bb10 said:**
> Tfoobar2000 if you're on windows.

yeah foobar2000 owns, you can even set it up so it will look in your repository of covers. So that it if there was no album cover in there then it would look for an image of the artist.

---

### Post by n3tfury on 2007-10-24
foobar is indeed the holy grail

---

### Post by maku-d on 2007-10-25
Anyone wondering about the amarok prob I mentioned above, I just fixed it by removing all the embedded pictures from files using easytag, took twenty seconds. Album artwork is displaying properly again. Hopefully the problem with embedded cover art not being displayed correctly will be fixed in amarok 2.0, cause now I'm gonna have to manually add artwork when I want it to display on my ipod then remove it when I want to play it in amarok... a bit annoying.

---

