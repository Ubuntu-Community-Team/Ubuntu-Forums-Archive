---
title: "Guayadeque Music Player"
date: 2010-02-04
forum: The Cafe
---

### Post by nothingspecial on 2010-02-04
This is your chance........ Take it! YOU can influence the development of this software!

There`s an awesome new music player out there.

Feature include -

- Supports mp3, ogg, flac, wma, aac, etc
- Label support. You can add as many labels as you want to any artist, album or track
- Cover fetching from google, amazon, last.fm
- Tag editor with Musicbrainz support
- Gapless play support
- Replaygain support
- Automatic Lyrics fetch and save to tracks
- Shoutcast or User defined radios support
- Podcasts support with automatic download with filters
- Dynamic/Static playlists
- Show Last.fm information
- Smart play mode that suggest music based on the actual track
- Customizable layout
- VU Meters
- Crossfading


and much more.

It`s under heavy active development and the developer is seeking feedback, feature requests, reports of bugs etc.

I`ve been using it as my default music player for a while now and I must say it`s the best music player I`ve come across yet.

[ATTACH]148113[/ATTACH]

[ATTACH]146053[/ATTACH]

[ATTACH]146052[/ATTACH]


[COLOR="Red"]
[SIZE="3"]
Please bear in mind that this is a thread for discussing Guayadeque, please, please post any feature requests, bug reports etc to[/COLOR] [COLOR="Blue"][this thread]("http://ubuntuforums.org/showthread.php?t=1380811")[/COLOR] [COLOR="Red"]so the developer does not have to check multiple threads.[/COLOR]
 [/SIZE]

To install the latest version on 10.04 Lucid or 9.10 Karmic open up a terminal and type


```

 sudo apt-get install subversion build-essential cmake gstreamer0.10-plugins-good gstreamer0.10-plugins-base libwxgtk2.8-dev libtagc0-dev libsqlite3-dev libcurl4-openssl-dev libdbus-1-dev libgstreamer0.10-dev libflac-dev
```
```
svn co http://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk guayadeque
```   ```
cd guayadeque/
```
 ```
./build
```
 ```
sudo make install
```

To install on 9.04 Jaunty
```
apt-get install build-essential subversion cmake zlib1g-dev 
libwxgtk2.8-dev libgstreamer0.10-dev libsqlite3-dev libcurl4-openssl-dev libdbus-1-dev libflac-dev
```

```

wget https://launchpad.net/ubuntu/+archive/primary/+files/taglib_1.6.orig.tar.gz
mv taglib_1.6.orig.tar.gz taglib-1.6.tar.gz
tar xfvz taglib-1.6.tar.gz
cd taglib-1.6
./configure --prefix=/usr --enable-asf --enable-mp4
make
sudo make install

```
```

cd 
svn co http://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk guayadeque-svn
cd guayadeque-svn
./build
sudo make install
```

There is a ppa available that is updated regularly but not as regularly as svn. To install -

```
add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn
```




There is a deb available [[COLOR="Magenta"]here[/COLOR]]("http://sourceforge.net/projects/guayadeque/"), although it is not as up to date and you won`t be able to test the new features as they become available.

This is an excellent piece of software, please check it out.

Leave your feedback [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

Translations are very welcome.

To donate click [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/donate/index.php?group_id=250783")

enjoy  :popcorn:

[http://www.omgubuntu.co.uk/2010/02/choose-new-icon-for-guayadeque-music.html]("http://www.omgubuntu.co.uk/2010/02/choose-new-icon-for-guayadeque-music.html")

---

### Post by anonbeat on 2010-02-04
Just wanted to add that to update to the current svn version you just need to do 
```

cd guayadeque
svn update
make
sudo make install

```

Thanks VastOne

---

### Post by nothingspecial on 2010-02-04
Done that twice already this morning. You are busy! :D

---

### Post by Uncle Spellbinder on 2010-02-04
Updated here as well. 

Guayadeque is by far the best player I've seen on Ubuntu for LARGE libraries. Really like this player an awful lot!

[img]http://content.imagesocket.com/images/Guayadeque2530.jpeg[/img]

**[SIZE="1"]Click Image To Enlarge:[/SIZE]**
[[IMG]http://content.imagesocket.com/thumbs/Guayadeque141f.jpeg[/IMG]](http://content.imagesocket.com/images/Guayadeque141f.jpeg)

---

### Post by anonbeat on 2010-02-04
> **Uncle Spellbinder said:**
> Updated here as well. 

Guayadeque is by far the best player I've seen on Ubuntu for LARGE libraries. Really like this player an awful lot!

[img]http://content.imagesocket.com/images/Guayadeque2530.jpeg[/img]

**[SIZE="1"]Click Image To Enlarge:[/SIZE]**
[[IMG]http://content.imagesocket.com/thumbs/Guayadeque141f.jpeg[/IMG]](http://content.imagesocket.com/images/Guayadeque141f.jpeg)

Just a note Uncle Spellbinder: Double click over the word Filters will hide it as u are not using it its more clear to hide it.

Thanks for your help

---

### Post by arnab_das on 2010-02-04
looks good. but i think i'll stick to songbird.

---

### Post by Uncle Spellbinder on 2010-02-04
> **anonbeat said:**
> Just a note Uncle Spellbinder: Double click over the word Filters will hide it as u are not using it its more clear to hide it.

Thanks for your help


Thanks anonbeat. ;)

---

### Post by anonbeat on 2010-02-04
> **Uncle Spellbinder said:**
> Thanks anonbeat. ;)

Just for curiosity can you tell me the memory usage with this collection?

btw the same can be done in last.fm panel. You can hide the different sections by double clicling over the section title.

---

### Post by Uncle Spellbinder on 2010-02-04
> **anonbeat said:**
> Just for curiosity can you tell me the memory usage with this collection?

CPU usage hovers between 2% and 7%. Toipping out at 10% every now and then.

Memory:
[[IMG]http://content.imagesocket.com/thumbs/1504.jpeg[/IMG]](http://content.imagesocket.com/images/1504.jpeg)

---

### Post by kelvin spratt on 2010-02-04
This is a very good player just need to support devices, rip CDs, and write to my MP5 player, and of course link songs to youtube and it will be as good as Atunes with less resources.

---

### Post by Elfy on 2010-02-04
I like the look of it - but how do you import a playlist :)

Can't find how to do that anywhere ... 

Installled from svn not the deb a short while ago.

---

### Post by anonbeat on 2010-02-04
> **Uncle Spellbinder said:**
> CPU usage hovers between 2% and 7%. Toipping out at 10% every now and then.

Memory:
[[IMG]http://content.imagesocket.com/thumbs/1504.jpeg[/IMG]](http://content.imagesocket.com/images/1504.jpeg)

Sorry didnt noticed the screenshot. Ok thank you. Its not bad 184Mb for 140000+ tracks :)

---

### Post by anonbeat on 2010-02-04
> **forestpiskie said:**
> I like the look of it - but how do you import a playlist :)

Can't find how to do that anywhere ... 

Installled from svn not the deb a short while ago.

Playlist tab select static playlist and right click over it then select import.

---

### Post by Elfy on 2010-02-04
> **anonbeat said:**
> Playlist tab select static playlist and right click over it then select import.

It says it asks for a name - which I give - then the import box closes and then nothing happens.

Its an m3u playlist file

---

### Post by anonbeat on 2010-02-04
> **forestpiskie said:**
> It says it asks for a name - which I give - then the import box closes and then nothing happens.

Its an m3u playlist file

Can you send it to my email ? anonbeat at gmail dot com

BTW we should talk about this here -> [http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)
Thanks

---

### Post by nothingspecial on 2010-02-04
> **forestpiskie said:**
> It says it asks for a name - which I give - then the import box closes and then nothing happens.

Its an m3u playlist file

Can confirm this with a .pls file. Using revision 623.

---

### Post by nothingspecial on 2010-02-04
> **anonbeat said:**
> 
BTW we should talk about this here -> [http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)
Thanks

Ok sorry.

---

### Post by Elfy on 2010-02-04
so am I :P

---

### Post by docus on 2010-02-04
This looks very interesting, nice clean interface.  (I wonder if it's in the Arch repos???  I'm posting from work so will check later...)

Where do you see it going in the future - any plans for ipod sync support?

Good luck with the development!

---

### Post by suprman2020 on 2010-02-04
Can it scrobble to last.fm?

---

### Post by nothingspecial on 2010-02-04
yes

---

### Post by suprman2020 on 2010-02-04
Can you let me know how to set it up?

---

### Post by anonbeat on 2010-02-04
> **suprman2020 said:**
> Can you let me know how to set it up?

Library -> Preferences -> Last.fm

---

### Post by Ric_NYC on 2010-02-04
I HAVE to install it.
:)

---

### Post by suprman2020 on 2010-02-04
This is MUCH lighter and better than Songbird. I have one issue though: when you play a song from an album, it doesn't continue playing the album. It plays a random song instead. Is there a way to change this?

---

### Post by Eisenwinter on 2010-02-04
I haven't actually tested out the program, but from the screenshot, it looks way too bloated for me.

I want my music player to display artist and track names, and play music.

---

### Post by nothingspecial on 2010-02-04
> **Eisenwinter said:**
> I haven't actually tested out the program, but from the screenshot, it looks way too bloated for me.

I want my music player to display artist and track names, and play music.

It depends what you mean by bloated. This is feature rich, but light.

Or you could use cmus, I`ve been using it for years. Guayadeque has finally led me back to the gui.

---

### Post by piousp on 2010-02-04
Will there be a QT port? :P

I'm installing it right now

---

### Post by Eisenwinter on 2010-02-04
> **nothingspecial said:**
> Or you could use cmus.
I do use cmus.

---

### Post by SuperSonic4 on 2010-02-04
It's an excellent little player but amarok suits my needs more

---

### Post by koleoptero on 2010-02-04
Interesting, I'll check this out when I get the time. Thanks for posting this.

---

### Post by anonbeat on 2010-02-04
> **piousp said:**
> Will there be a QT port? :P

I'm installing it right now

Nope anytime soon

---

### Post by piousp on 2010-02-04
Oh man,

```
piousp@LEPTON:~$ guayadeque                                                          
13:59:37: Deleted stale lock file '/home/piousp/.guayadeque/.guayadeque-piousp'.     
13:59:37: Initialized locale ( es_CR )                                               
13:59:37: Library Db Version 7                                                       
13:59:37: Library Paths:
13:59:37: Error: Could not find a valid audiosink

```

---

### Post by anonbeat on 2010-02-04
> **Eisenwinter said:**
> I haven't actually tested out the program, but from the screenshot, it looks way too bloated for me.

I want my music player to display artist and track names, and play music.

Here you go

[IMG]https://sourceforge.net/apps/gallery/guayadeque/main.php?g2_view=core.DownloadItem&g2_itemId=65&g2_serialNumber=2[/IMG]

---

### Post by anonbeat on 2010-02-04
> **piousp said:**
> Oh man,

```
piousp@LEPTON:~$ guayadeque                                                          
13:59:37: Deleted stale lock file '/home/piousp/.guayadeque/.guayadeque-piousp'.     
13:59:37: Initialized locale ( es_CR )                                               
13:59:37: Library Db Version 7                                                       
13:59:37: Library Paths:
13:59:37: Error: Could not find a valid audiosink

```

you need gstreamer0.10  gstreamer0.10-plugins-good gstreamer0.10-plugins-base installed

---

### Post by nothingspecial on 2010-02-04
> **anonbeat said:**
> you need gstreamer0.10  gstreamer0.10-plugins-good gstreamer0.10-plugins-base installed

Updated post #1 to reflect this.

---

### Post by Elfy on 2010-02-04
> **nothingspecial said:**
> Can confirm this with a .pls file. Using revision 623.

Recent update allows m3u to work.

---

### Post by anonbeat on 2010-02-04
> **nothingspecial said:**
> Updated post #1 to reflect this.

done

> **forestpiskie said:**
> Recent update allows m3u to work.

And pls shoudl work too

---

### Post by nothingspecial on 2010-02-04
I`m afraid not.

I could be doing it wrong though. Like I said, I don`t use playlists.

---

### Post by corney91 on 2010-02-04
Looks good :) It seems very, very similar to gmusicbrowser, except slicker, from my minute-long first impression though... I'll explore a little more in the morning because I'm exhausted at the minute but I like the randomly fill playlist feature, although admittedly I've not played any songs yet :p

---

### Post by suprman2020 on 2010-02-05
After using this for a day, this is probably one of the best music players I've used in Ubuntu. Its amazing how little resources this program uses. 22 Mib for a almost 6000 track library. One last question, is there a way to sort the albums alphabetically instead of by year?

---

### Post by anonbeat on 2010-02-05
> **suprman2020 said:**
> After using this for a day, this is probably one of the best music players I've used in Ubuntu. Its amazing how little resources this program uses. 22 Mib for a almost 6000 track library. One last question, is there a way to sort the albums alphabetically instead of by year?

If you are using the deb from sourceforge : In preferences there is an option to sort the albums. You can select Alphabetically, by Year or Yeas descending.

If you are using it from svn version : Right click over albums and select ordering -> by name

---

### Post by nothingspecial on 2010-02-05
A ppa has just become available, see post #1.

---

### Post by Elfy on 2010-02-05
Ok - been playing about and I have lost the filters ;)

Anyone know how to get them back

---

### Post by nothingspecial on 2010-02-05
> **forestpiskie said:**
> Ok - been playing about and I have lost the filters ;)

Anyone know how to get them back

Under the player - the section with what`s playing now and what`s coming up - whare the filters were........ Double click :D

---

### Post by Elfy on 2010-02-05
I had tried that - nothing - possibly because I've been playing about with things - it looks like this at the moment - any clues?

---

### Post by nothingspecial on 2010-02-05
Only what I said before, but you don`t seem to have the same space to click on as I do.

I kind of thought you`d be playing some sort of Gong derivative though.

P H Pixies of the world unite ;)

---

### Post by Elfy on 2010-02-05
:lol:

well I am sure I will find out somewhere and somehow - I have the rest of the time I use it for :)

---

### Post by anonbeat on 2010-02-05
> **forestpiskie said:**
> I had tried that - nothing - possibly because I've been playing about with things - it looks like this at the moment - any clues?

Update to latest svn version and do what its said in post #1

Let me know if that dont work. Sorry but all gui changes are now a work in progress not finished and there are details still to solve

Thanks

---

### Post by ybd on 2010-02-05
I gave this a spin.

The interface is clunky and is unusable unless the window is at or close to the full screen's resolution (I'm using 1440x900).

---

### Post by Uncle Spellbinder on 2010-02-05
> **ybd said:**
> I gave this a spin.

The interface is clunky and is unusable unless the window is at or close to the full screen's resolution (I'm using 1440x900).As has been mentioned, the GUI is a work in progress. But I do agree that some resizing is necessary.

---

### Post by nothingspecial on 2010-02-06
Any more willing testers out there?

This is a chance to get involved in a top notch open source project and actually influence the finished product.

---

### Post by Uncle Spellbinder on 2010-02-06
> **nothingspecial said:**
> This is a chance to get involved in a top notch open source project and actually influence the finished product.

Couldn't agree more. The developer, anonbeat, is fantastic at implementing suggestions. A developer who truly listens to those testing. Surely everything suggested won't make it to the finished product, but the fact that some suggestions made it thus far says a lot about the developer.

Head over to the [ Guayadeque Music Player Test Thread](http://ubuntuforums.org/showthread.php?t=1380811) and join us!

---

### Post by nothingspecial on 2010-02-06
You need to ????????

---

### Post by mister_k81 on 2010-02-07
I just downloaded and installed this from the PPA, and I have to say that I like what I see so far. 

True, the interface is a bit clunky on default, but after playing around with it a bit, I managed to find a layout that works well for me (see attachment). It's also missing some features, like being able to sync to my iPod Touch (like Rhythmbox can), the ability to show album artwork/ music notifications when minimized to the system tray, nor does it have an equalizer (but then again, not many Linux music players have one).  But since this is a work in progress, it is very easy to look past those things. 

This is a great light weight music player with some nice features, It could end up being a permanent replacement for Rhythmbox for me.  Nice work.


**EDIT: ** after a little more use, it turns out that this does have an equalizer with presets. Nice! Scratch that off my wish list. ;)

---

### Post by Luke has no name on 2010-02-07
Help! Revision 633 took away my "Now playing"/Control window! I can't find anything to fix it. Last known working revision was 631, for me.

Therefore, I deleted the sources and rolled back to revision 631 ("svn co -r 631 <rest of command>" for those interested)

EDIT: Before rolling back,
-Close the program
-delete your non-.db files (not folders) in ~/.guayadeque/
-Restart. GUI and preference settings will be reset, but your music db won't have to be reloaded.

EDIT: 
Do what Anonbeat says below. Heh.

---

### Post by anonbeat on 2010-02-07
> **Luke has no name said:**
> Help! Revision 633 took away my "Now playing"/Control window! I can't find anything to fix it. Last known working revision was 631, for me.

Remove LastLayout entry in the file ~/.guayadeque/guayadeque.conf

Sorry. Im trying to fix all this issues with the layouts

Thank you for your help on testing

---

### Post by OutOfReach on 2010-02-07
I installed from the ppa, and I must say it's pretty good.
I have 2 suggestions though:
- Automatically update the library when the library paths change? Not really a big problem but it'd be nice
- System tray icon? It'd be nice to have it out of your way when you're not using it

Otherwise, it has potential. But I must agree with the clunky interface problem, the interface needs to be a bit more simplified IMO

---

### Post by anonbeat on 2010-02-07
> **OutOfReach said:**
> I installed from the ppa, and I must say it's pretty good.
I have 2 suggestions though:
- Automatically update the library when the library paths change? Not really a big problem but it'd be nice
- System tray icon? It'd be nice to have it out of your way when you're not using it

Otherwise, it has potential. But I must agree with the clunky interface problem, the interface needs to be a bit more simplified IMO

Thank you for helping with guayadeque. I will note your requests but the system tray icon can be disabled from the preferences. Its in the General Tab.

---

### Post by OutOfReach on 2010-02-07
> **anonbeat said:**
> Thank you for helping with guayadeque. I will note your requests but the system tray icon can be disabled from the preferences. Its in the General Tab.

Oh! Ok, I didn't see that option. I guess that's solved.
Thanks and good work :)

---

### Post by nothingspecial on 2010-02-09
oooops

---

### Post by nothingspecial on 2010-02-13
I now consider this a stable music player.

Have a go :D

---

### Post by Henry Flower on 2010-02-14
Another player designed only for pop music - no composer field. :(

---

### Post by nothingspecial on 2010-02-14
Post your feature requests [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by TJUndead on 2010-02-15
Man, I installed this music player yesterday from PPA, when I was looking for some good music player to remove the buggy Exaile, and to leave aside the heavy Banshee, and I was really impressed with Guayadeque. It is a wonderful music player. 

My congratulations to the creator. Well, I liked a lot, but I miss something in the music player as an option to configure the download of covers, because I don't know how to download covers automatically, and also the lack of integration with the Ubuntu OSD notifications. Maybe it already exists in the player and I didn't find, so I hope someone can give me a hand with this, because I'm a little lazy. 

And one last thing. I have 2 questions about the lirycs. When the player is to download a letter, it is automatically integrated with the music file, or I need to do something to integrate the lirycs in mp3? And I see a button near the drop-down menu on lirycs tab, and I don't know what that button is for, because the button is always disabled... 

Congratz again for the great work, and sorry for my bad english. LOL

---

### Post by anonbeat on 2010-02-15
> **TJUndead said:**
> Man, I installed this music player yesterday from PPA, when I was looking for some good music player to remove the buggy Exaile, and to leave aside the heavy Banshee, and I was really impressed with Guayadeque. It is a wonderful music player. 

My congratulations to the creator. Well, I liked a lot, but I miss something in the music player as an option to configure the download of covers, because I don't know how to download covers automatically, and also the lack of integration with the Ubuntu OSD notifications. Maybe it already exists in the player and I didn't find, so I hope someone can give me a hand with this, because I'm a little lazy. 

And one last thing. I have 2 questions about the lirycs. When the player is to download a letter, it is automatically integrated with the music file, or I need to do something to integrate the lirycs in mp3? And I see a button near the drop-down menu on lirycs tab, and I don't know what that button is for, because the button is always disabled... 

Congratz again for the great work, and sorry for my bad english. LOL

There is an option to auto download covers but its not like what I think you suggest. I think you are talking about a way the player to download covers when a track is played and no cover found. I will note it as feature request.

About the notifications I will add it soon.

About Lyrics, if you want it to be saved to files you need to check the Preference 'Save lyrics to audio files' in Library preferences page

You probably have it already enabled and this is why you have this button disabled. Because its handled automatically. Let me know if its not the case.

Thank you for testing guayadeque and let me know any bug, feature request or simply a comment.

---

### Post by TJUndead on 2010-02-15
> **anonbeat said:**
> I think you are talking about a way the player to download covers when a track is played and no cover found. I will note it as feature request.

Yes, this is exactly what I mean. Thanks for add this as a request. ^^

> **anonbeat said:**
> About the notifications I will add it soon.

WOW, Very nice man. ^^

> **anonbeat said:**
> About Lyrics, if you want it to be saved to files you need to check the Preference 'Save lyrics to audio files' in Library preferences page

You probably have it already enabled and this is why you have this button disabled. Because its handled automatically. Let me know if its not the case.

Ahhhh, I see. I'll take a look on this now to see if work or not. Thanks for the info.

> **anonbeat said:**
> Thank you for testing guayadeque and let me know any bug, feature request or simply a comment.
No man, thanks for you to make so good player. 
And if you need some more help on tests or something else related, call me on tiagojpavan (at) gmail.com, or on my personal twitter @tiagojpavan.

Thanks again for your hard work and congratz. ^^

---

### Post by Pifilatakanemu on 2010-02-17
look's good at the first sight, i'll try it.

if you are looking for features: check out foobar2000, I still miss hits cute little player, it's a shame it is not available for linux. anyway, there are a couple of extensions for foobar that really are helpful, e.g. : 

[LIST]
[*]syncing a playlist with a folder
[*]upnp
[*]...
[/LIST]
what i loved most is the lightness of it, so keep an eye on that! This is really an important aspect as other players totally fail when handling big libraries.

anyway, keep up the good work!

---

### Post by Carlos C on 2010-02-17
Excellent player. I have only one question: it supports ReplayGain? I can't find anything about it.

---

### Post by anonbeat on 2010-02-18
> **Carlos C said:**
> Excellent player. I have only one question: it supports ReplayGain? I can't find anything about it.

Yes supports replaygain but only in read mode. It reads tags and set volumen acording to the tags

---

### Post by Pifilatakanemu on 2010-02-18
Every time I change the song the CPU load rises up to 120% (1,6 Dual Core) and get's back after a couple of seconds. Is this a bug?

---

### Post by anonbeat on 2010-02-18
> **flohmann said:**
> Every time I change the song the CPU load rises up to 120% (1,6 Dual Core) and get's back after a couple of seconds. Is this a bug?

See the last.fm panel or lyrics or both when changing a track...

---

### Post by Pifilatakanemu on 2010-02-18
Ok. 

I'm just now creating a Wiki-Entry in the German Ubuntu Wiki. Any nice Screanshot to use? ;)

---

### Post by anonbeat on 2010-02-18
> **flohmann said:**
> Ok. 

I'm just now creating a Wiki-Entry in the German Ubuntu Wiki. Any nice Screanshot to use? ;)

There are few there [http://sourceforge.net/apps/gallery/guayadeque/index.php](http://sourceforge.net/apps/gallery/guayadeque/index.php)

---

### Post by Pifilatakanemu on 2010-02-18
Ok, nice. 

My Player is in English. Is there any way to get a German Version?
 (I saw Spanish in the Screenshots.)

---

### Post by anonbeat on 2010-02-18
> **flohmann said:**
> Ok, nice. 

My Player is in English. Is there any way to get a German Version?
 (I saw Spanish in the Screenshots.)

One guy told me he is working in the german translation. For now there is no german translation. I use personally Spanish translation. This is why its spanish in screenshots. In the gallery there are a few with english.

Thanks

---

### Post by Carlos C on 2010-02-18
> **anonbeat said:**
> Yes supports replaygain but only in read mode. It reads tags and set volumen acording to the tags
I've been looking in the preferences menu, but can't find  the ReplayGain option. How can I enable it?  I cannot hear any change, each track  maintains a diferent volume and all  labels are ignored.  :confused:

---

### Post by anonbeat on 2010-02-18
> **Carlos C said:**
> I've been looking in the preferences menu, but can't find  the ReplayGain option. How can I enable it?  I cannot hear any change, each track  maintains a diferent volume and all  labels are ignored.  :confused:

Its enabled by default and not configurable. At least for now. What files are you playing with replaygain tags ?

---

### Post by Ric_NYC on 2010-02-18
Ugly interface.

---

### Post by nothingspecial on 2010-02-18
> **Ric_NYC said:**
> Ugly interface.

So change it - you can, you know.

[ATTACH]147484[/ATTACH]

[ATTACH]147485[/ATTACH]

[ATTACH]147486[/ATTACH]

How do you want it to look?

---

### Post by nothingspecial on 2010-02-18
Even just

[ATTACH]147490[/ATTACH]

Guayadeque is soooo customizable!

And you can save each layout and switch between them as you wish.

How cool is that?!

---

### Post by joeknoodle on 2010-02-19
Trying to build this on 9.04 and get the following error/s:

```

In file included from /home/joe/guayadeque/src/CoverFrame.cpp:24:
/home/joe/guayadeque/src/TagInfo.h:42:20: error: mp4tag.h: No such file or directory
/home/joe/guayadeque/src/TagInfo.h:43:21: error: mp4file.h: No such file or directory
In file included from /home/joe/guayadeque/src/CoverFrame.cpp:24:
/home/joe/guayadeque/src/TagInfo.h:178: error: ‘TagLib::MP4’ has not been declared
/home/joe/guayadeque/src/TagInfo.h:178: error: ISO C++ forbids declaration of ‘Tag’ with no type
/home/joe/guayadeque/src/TagInfo.h:178: error: expected ‘;’ before ‘*’ token
make[2]: *** [src/CMakeFiles/guayadeque.dir/CoverFrame.o] Error 1
make[1]: *** [src/CMakeFiles/guayadeque.dir/all] Error 2
make: *** [all] Error 2

```Please help.

---

### Post by anonbeat on 2010-02-19
> **joeknoodle said:**
> Trying to build this on 9.04 and get the following error/s:

```

In file included from /home/joe/guayadeque/src/CoverFrame.cpp:24:
/home/joe/guayadeque/src/TagInfo.h:42:20: error: mp4tag.h: No such file or directory
/home/joe/guayadeque/src/TagInfo.h:43:21: error: mp4file.h: No such file or directory
In file included from /home/joe/guayadeque/src/CoverFrame.cpp:24:
/home/joe/guayadeque/src/TagInfo.h:178: error: ‘TagLib::MP4’ has not been declared
/home/joe/guayadeque/src/TagInfo.h:178: error: ISO C++ forbids declaration of ‘Tag’ with no type
/home/joe/guayadeque/src/TagInfo.h:178: error: expected ‘;’ before ‘*’ token
make[2]: *** [src/CMakeFiles/guayadeque.dir/CoverFrame.o] Error 1
make[1]: *** [src/CMakeFiles/guayadeque.dir/all] Error 2
make: *** [all] Error 2

```Please help.

You need taglib 1.6 or greater
sorry

---

### Post by Carlos C on 2010-02-19
> **anonbeat said:**
> Its enabled by default and not configurable. At least for now. What files are you playing with replaygain tags ?

I'm playing flac files and I added tags using Soundkonverter's Replay Gain Tool

---

### Post by rotwang888 on 2010-02-19
> **Henry Flower said:**
> Another player designed only for pop music - no composer field. :(

 There is a composer field in the latest version.  In the tag editor as well, which you don't always see.

---

### Post by joeknoodle on 2010-02-19
> **anonbeat said:**
> You need taglib 1.6 or greater
sorry
Yeah, now I'm gettting all kinds of errors trying to get taglib going.

Oh well.

I'll keep my eyes open for an installer that works for us noobs.

---

### Post by Dagon^ on 2010-02-20
I'm requesting a function that would make this app a killer.

Mini-mode, that is an important function, at least it is to me :P

---

### Post by Pifilatakanemu on 2010-02-22
Some font colors seem strange in the last.fm-Tab.  see Screenshot. 
It's probably due to my theme, but I think I did not change my colors manually... no idea.
[IMG]http://img19.imageshack.us/img19/8224/bildschirmfoto1r.png[/IMG]


Is there any way to tag songs as "popular" @ last.fm ? (The heart-button...)

---

### Post by anonbeat on 2010-02-22
> **flohmann said:**
> Some font colors seem strange in the last.fm-Tab.  see Screenshot. 
It's probably due to my theme, but I think I did not change my colors manually... no idea.
[IMG]http://img19.imageshack.us/img19/8224/bildschirmfoto1r.png[/IMG]


Is there any way to tag songs as "popular" @ last.fm ? (The heart-button...)

Not at this time. This colour is from your theme. Its telling you which albums, artists, tracks you have and which you dont have. The hightlighted ones are missing in your library. The black ones are present.

---

### Post by anonbeat on 2010-02-22
> **Dagon^ said:**
> I'm requesting a function that would make this app a killer.

Mini-mode, that is an important function, at least it is to me :P

Can you explain me what mini mode means?

---

### Post by koleoptero on 2010-02-22
> **anonbeat said:**
> Can you explain me what mini mode means?

He means a way to switch the interface to just show song info and some controls. Not permanently, a one-button way to do this.

---

### Post by anonbeat on 2010-02-22
> **koleoptero said:**
> He means a way to switch the interface to just show song info and some controls. Not permanently, a one-button way to do this.

I suggest him then to see the screenshot gallery to check all posibilities guayadeque have

For example this 
[IMG]https://sourceforge.net/apps/gallery/guayadeque/main.php?g2_view=core.DownloadItem&g2_itemId=87&g2_serialNumber=1[/IMG]

or this
[IMG]https://sourceforge.net/apps/gallery/guayadeque/main.php?g2_view=core.DownloadItem&g2_itemId=65&g2_serialNumber=2[/IMG]

You can do your own layout and save it for future use. You can switch between layouts with a menu click.
This is what you meant?

The screenshots gallery is at [https://sourceforge.net/apps/gallery/guayadeque/index.php?g2_itemId=22&g2_page=2](https://sourceforge.net/apps/gallery/guayadeque/index.php?g2_itemId=22&g2_page=2)

---

### Post by nothingspecial on 2010-02-22
Added instructions for installation on 9.04 Jaunty to the first post.

---

### Post by Carlos C on 2010-02-22
> **Carlos C said:**
> I'm playing flac files and I added tags using Soundkonverter's Replay Gain Tool

any clues what's wrong?

---

### Post by anonbeat on 2010-02-22
> **Carlos C said:**
> any clues what's wrong?

Can you send me one of this flac files?

---

### Post by Islington on 2010-02-22
I did not know whether to post here or in that other thread in DE section:
Here is a proposal for a new icon:

[URL="http://www.flickr.com/photos/47414073@N07/4380624254/"][IMG]http://farm3.static.flickr.com/2736/4380624254_f7592efe39_o.png[/IMG]
[/URL]

---

### Post by anonbeat on 2010-02-22
> **Islington said:**
> I did not know whether to post here or in that other thread in DE section:
Here is a proposal for a new icon:

[URL="http://www.flickr.com/photos/47414073@N07/4380624254/"][IMG]http://farm3.static.flickr.com/2736/4380624254_f7592efe39_o.png[/IMG]
[/URL]

Better post it here
[http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)

---

### Post by Carlos C on 2010-02-22
> **anonbeat said:**
> Can you send me one of this flac files?

Ok:

[http://dl.dropbox.com/u/3697948/01%20%C3%81guas%20de%20Mar%C3%A7o.flac](http://dl.dropbox.com/u/3697948/01%20%C3%81guas%20de%20Mar%C3%A7o.flac)
[http://dl.dropbox.com/u/3697948/02%20Tango%2C%20Isaac%20Alb%C3%A9niz.flac](http://dl.dropbox.com/u/3697948/02%20Tango%2C%20Isaac%20Alb%C3%A9niz.flac)

---

### Post by anonbeat on 2010-02-23
> **Carlos C said:**
> I'm playing flac files and I added tags using Soundkonverter's Replay Gain Tool

Hello Carlos I have been looking at the problem and seems something was wrong. I tested this long ago and it was working but after you told me I rechecked and there was a problem. Finally I think I fixed it but I need you to check updating to latest svn revision 693.

Please let me know if its still not following volume tags. Guayadeque prefers track tags over album tags but will use album if tracks tags are not present.

Thank you for your bug report

Please if you dont mind post about it [here]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by theLegend on 2010-02-24
2 thumbs up for this excellent music player! Just a quick query, but is there a changelog available for each version? I've done an update but didn't notice what bugs/features were implemented since last time. I would like to be able to test them for you to give you feedback on them.

--Update---
Sorry, too quick to request this, have now found this on another thread! [http://http://ubuntuforums.org/showthread.php?t=1380811]("http://http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by anonbeat on 2010-02-24
> **theLegend said:**
> 2 thumbs up for this excellent music player! Just a quick query, but is there a changelog available for each version? I've done an update but didn't notice what bugs/features were implemented since last time. I would like to be able to test them for you to give you feedback on them.

--Update---
Sorry, too quick to request this, have now found this on another thread! [http://http://ubuntuforums.org/showthread.php?t=1380811]("http://http://ubuntuforums.org/showthread.php?t=1380811")

Try to continue in the other thread about feature requests, bug reports, etc

Thanks

---

### Post by VastOne on 2010-02-24
@nothingspecial

Hey...I just stumbled upon this thread and was surprised...So many additional questions and ideas I was unaware of!

Why not propose to the admins here to merge this thread with anonbeats?

---

### Post by nothingspecial on 2010-02-24
I have thought about it, and even pmd anon about it but in the end I felt it might generate more testers, being in the cafe. Aslong as there are just 2 threads and no others in Desktop environments for example :-\" :D
anon can handle it, although he (and I) try to nudge feature requests, bugs etc to the original multimedia thread.

---

### Post by VastOne on 2010-02-24
> **nothingspecial said:**
> I have thought about it, and even pmd anon about it but in the end I felt it might generate more testers, being in the cafe. Aslong as there are just 2 threads and no others in Desktop environments for example :-\" :D
anon can handle it, although he (and I) try to nudge feature requests, bugs etc to the original multimedia thread.

I put that in Desktop Environments with the blessings from anonbeat before I  posted because that is where the artists tend to hang out and we agreed it would be a better area for the request. 

You may want to check with anonbeat again as his workload seems to be getting out of control and having two locations to keep track of may add to it....

Just a thought, and again I did not know this was here so I could not glean any of the great info here. I never thought to look for another G-Que thread...:D :popcorn:

---

### Post by anonbeat on 2010-02-24
> **VastOne said:**
> I put that in Desktop Environments with the blessings from anonbeat before I  posted because that is where the artists tend to hang out and we agreed it would be a better area for the request. 

You may want to check with anonbeat again as his workload seems to be getting out of control and having two locations to keep track of may add to it....

Just a thought, and again I did not know this was here so I could not glean any of the great info here. I never thought to look for another G-Que thread...:D :popcorn:

Its true that check two threads are more work than a single one. Also I think its better for other users to keep all related to bug reports, feature requests and so in the other thread. Keep this to let ppl know about it and to help ppl installing or doing this or things like this.
Just my thought

---

### Post by nothingspecial on 2010-02-24
Doesn`t matter

---

### Post by nothingspecial on 2010-02-24
Nor does this, sorry

---

### Post by nothingspecial on 2010-02-24
> **anonbeat said:**
>  Keep this to let ppl know about it and to help ppl installing or doing this or things like this.
Just my thought

Just read this bit propperly, I shall continue steering feature/bugs etc to the other thread. In fact, if you like, I`ll check this thread and send stuff to the other thread if you like.

Obviously being in different tome zones there will be a lag. I for one sleep sometimes :D

---

### Post by anonbeat on 2010-02-24
> **nothingspecial said:**
> Just read this bit propperly, I shall continue steering feature/bugs etc to the other thread. In fact, if you like, I`ll check this thread and send stuff to the other thread if you like.

Obviously being in different tome zones there will be a lag. I for one sleep sometimes :D

Thank you for your help nothingspecial.

---

### Post by VastOne on 2010-02-27
OMG! UK is hosting a poll on their blog site here

[_[COLOR="DarkRed"]Here[/COLOR]_]("http://www.omgubuntu.co.uk/2010/02/choose-new-icon-for-guayadeque-music.html")

Please go there to vote for the icon scheme for G-Que!

A special thank you to Joey-Elijah at OMG! for this great work and time put in to put up the poll.:guitar:

---

### Post by nothingspecial on 2010-02-27
Voted :D

---

### Post by Uncle Spellbinder on 2010-02-27
> **VastOne said:**
> OMG! UK is hosting a poll on their blog site here

[_[COLOR="DarkRed"]Here[/COLOR]_]("http://www.omgubuntu.co.uk/2010/02/choose-new-icon-for-guayadeque-music.html")

Please go there to vote for the icon scheme for G-Que!
Voted. 

:)

---

### Post by VastOne on 2010-03-01
> **Uncle Spellbinder said:**
> Voted. 

:)

1509 votes there as of 10:20am CT US

Not too shabby

[http://node4.nirvanix.com/polldaddy/polldaddy/images/1267296486_4463-x.jpg](http://node4.nirvanix.com/polldaddy/polldaddy/images/1267296486_4463-x.jpg)

holding a slim lead

---

### Post by Swagman on 2010-03-01
When you say "Shoutcast support" does that mean "built in **Broadcast** "(with mic) support ?

---

### Post by VastOne on 2010-03-01
> **Swagman said:**
> When you say "Shoutcast support" does that mean "built in **Broadcast** "(with mic) support ?

No. It means a very good connectivity to radio from Shoutcast and the majority of it's genre

---

### Post by nothingspecial on 2010-03-01
> **Swagman said:**
> When you say "Shoutcast support" does that mean "built in **Broadcast** "(with mic) support ?

You could request it. However the developer is fixing bugs for a milestone release rather than adding requests atm.

Also it is worth remembering (I`m pretty sure of this) that the prime purpose of this player is to be fast and lightweight even with huge music collections and anything that detracts from this will not be implemented - I think.

Please make feature requests[[COLOR="Magenta"] here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by Swarms on 2010-03-01
Looks quite good, awful name for an application though. I know it is a place in Gran Canaria but try make anyone who does not know a little spanish how to pronounce it. Like the appearance of the program, it is so important that it is recognized beyond being the program with the weird name.

---

### Post by nothingspecial on 2010-03-01
> **Swarms said:**
> Looks quite good, awful name for an application though. I know it is a place in Gran Canaria but try make anyone who does not know a little spanish how to pronounce it. Like the appearance of the program, it is so important that it is recognized beyond being the program with the weird name.

I agree ...... in part, however I kind of think it helps in someways.

My grandfather was a surveyor.

He used to go around in crazy clothes with a "ZZTop beard", long grey hair and a crazily painted old Rolls Royce. (He was very good at his job btw)

I asked him once why he liked to look like that. He said, people don`t remember blokes (guys) in suits. When someone who has used me before or has seen me and knows what I do, needs a surveyor, they`re more likely to say

-What about the one with the crazy car and the long hair - than

-what about the one in the boring suit

Worked for him

---

### Post by moore.bryan on 2010-03-01
No Lucid love in the PPA?

---

### Post by Swarms on 2010-03-01
> **nothingspecial said:**
> I agree ...... in part, however I kind of think it helps in someways.

My grandfather was a surveyor.

He used to go around in crazy clothes with a "ZZTop beard", long grey hair and a crazily painted old Rolls Royce. (He was very good at his job btw)

I asked him once why he liked to look like that. He said, people don`t remember blokes (guys) in suits. When someone who has used me before or has seen me and knows what I do, needs a surveyor, they`re more likely to say

-What about the one with the crazy car and the long hair - than

-what about the one in the boring suit

Worked for him

I think there can be a difference between something which could be the name of some weird scifi planet and a name that stands out.

Great story about your grandfather though! :)

---

### Post by VastOne on 2010-03-01
> **moore.bryan said:**
> No Lucid love in the PPA?

Soon I am sure...Anon would be grateful for help on this if anyone can.

---

### Post by VastOne on 2010-03-02
> **nothingspecial said:**
> I agree ...... in part, however I kind of think it helps in someways.

My grandfather was a surveyor.

He used to go around in crazy clothes with a "ZZTop beard", long grey hair and a crazily painted old Rolls Royce. (He was very good at his job btw)

I asked him once why he liked to look like that. He said, people don`t remember blokes (guys) in suits. When someone who has used me before or has seen me and knows what I do, needs a surveyor, they`re more likely to say

-What about the one with the crazy car and the long hair - than

-what about the one in the boring suit

Worked for him

Nothingpecial, great story about your grandfather...I would love to meet him and pick his brain on a few things...

After all we have read and all that has been posted at OMG! on the name subject, I am still unclear as to how to pronounce it. G-Que is very easy to recall and to tell others about, of course if you cannot pronounce it you have to come up with something...My point is this, Amarok, Exaile, Winamp Songbird all have emphasis as a brand that worked in their titles. I agree it does not matter what the name is if you have a superior product, but I am really concerned with the amount of people who have flat out rejected trying G-Que because of the name. I know this is a very idiotic reason, but it is real...](*,)

What is the solution? I do not know...But I do know that anonbeat loves the name Guayadeque and since we are so global, a name is just as important in one place as in another.  Branding is important, it ties into marketing in so many ways...I want more than anything for anyone on a linux box to give G-Que a ride to see it's many qualities, but I really do not know how many people will give Guayadeque a chance when they see it in the software center or in Synaptic... In all the time I have been collecting MP3 files (14 years), I have never heard of Media Monkey or Foobar... I AM SURE THAT I HAVE, but I never associated either as an mp3 player. It just does not make sense to me that either is remotely connected to music.. But I have heard so much about their features compared to G-Que and how great they are, I wonder how I could have missed them... 

I just hope Guayadeque does not fall into that category...I also hope others will join in on this discussion and bring their views to the table..

I know a certain Uncle who will be with us as soon as he reads my long blog of hot air masses 8)

---

### Post by Uncle Spellbinder on 2010-03-02
> **moore.bryan said:**
> No Lucid love in the PPA?
I asked about this in the testing thread.....

> **anonbeat said:**
> It will be available soon

;)

---

### Post by moore.bryan on 2010-03-02
> **VastOne said:**
> Soon I am sure...Anon would be grateful for help on this if anyone can.
If only I had the time...

> **Uncle Spellbinder said:**
> I asked about this in the testing thread.....
Excellent! Thanks for the info...

---

### Post by VastOne on 2010-03-05
With less than 4 hours to go Mrmotinjo Icon # 12 has a 3 vote lead over his other icon # 11.

Polling stops at Midnight tonight CST

---

### Post by ruffwuk on 2010-03-06
I installed Guayadeque 2 weeks ago and I am loving it!  I have over 120,000 songs in my collection and it handles them nicely.  I have a Dell Precision 870 with 4 Intel Xeon processors and just 2 GB RAM and I am humming baby.
Not a developer or anything such, just a Linux user who converted from Microsoft a couple years back.  I used Exaile, Amarok, Rhythmbox and this one is the best by far.  the ease of use and simplicity, yet the speed and subtle bells and whistles make this bad boy one nice player.
Granted I am not into all these bells and whistles the younger cats are into, (all I want to do is play and catalog my music nicely) with your IPods and podcasts and such, but overall it is awesome.  I have found my Gnome music player at last.

---

### Post by VastOne on 2010-03-06
Poll results are now final with Mrmotijo's the clear winner

Icon 1 by dichtbijzee <1% (5 votes)
Icon 2 by dichtbijzee <1% (3 votes)
Icon 3 by hojgaard 3% (56 votes)
Icon 4 by hojgaard 5% (83 votes)
Icon 5 by hojgaard 4% (67 votes)
Icon 6 by hojgaard 5% (87 votes)
Icon 7 by hojgaard 11% (189 votes)
Icon 8 by DanRabbit 5% (94 votes)
Icon 9 by Islington 11% (201 votes)
Icon 10 by MaXeR 1% (24 votes)
Icon 11 by Mrmotinjo 25% (441 votes)
Icon 12 by Mrmotinjo 25% (444 votes)
Icon 13 by Rotave 5% (85 votes)

Thank you to all of the artists!

Thanks to all who voted and participated

Thanks go to OMG! for hosting the poll and the great work they did

---

### Post by Ric_NYC on 2010-03-06
I messed up the settings in Guayadeque.
How can I have it reinstalled with all the default settings?

I need a fresh start. :)

Thanks.

---

### Post by Uncle Spellbinder on 2010-03-06
If you really want a fully clean slate for Guayadeque, I just delete the .guayadeque folder in my home directory and start Guayadeque. All settings are as if it's a clean, fresh install. You'll lose your library settings as well, so you'll need to start from scratch.


Further support questions should be in the "testing thread". The ink is in my sig.

---

### Post by Ric_NYC on 2010-03-06
> **Uncle Spellbinder said:**
> If you really want a fully clean slate for Guayadeque, I just delete the .guayadeque folder in my home directory and start Guayadeque. All settings are as if it's a clean, fresh install. You'll lose your library settings as well, so you'll need to start from scratch.


Further support questions should be in the "testing thread". The ink is in my sig.

Thanks. I'll do that.

---

### Post by Pifilatakanemu on 2010-03-07
What about the German translation?
Who is doing it (somebody said that there is someone on it) ?

I'd write a small article for the German Ubuntu Community News at the moment when there is a German version available.

I just love this player!

---

### Post by ssj6akshat on 2010-03-07
Awesome Awesome Awesome^100000000000000000000

---

### Post by anonbeat on 2010-03-07
> **flohmann said:**
> What about the German translation?
Who is doing it (somebody said that there is someone on it) ?

I'd write a small article for the German Ubuntu Community News at the moment when there is a German version available.

I just love this player!

Some guy told me he was going to do it but seems he is not having the time.
If you want to do it you need to 1st update the translation template

```
cd guayadeque
./buildt
```

then use the po/guayadeque.pot as the template for the translation

Thanks

---

### Post by anonbeat on 2010-03-07
> **ssj6akshat said:**
> Awesome Awesome Awesome^100000000000000000000

Thanks

---

### Post by Pifilatakanemu on 2010-03-07
> **anonbeat said:**
> Some guy told me he was going to do it but seems he is not having the time.
If you want to do it you need to 1st update the translation template

```
cd guayadeque
./buildt
```then use the po/guayadeque.pot as the template for the translation

Thanks

Can you contact the guy? If he already started it would be nice to have the stuff he did.

I would try to find someone willing to work on it. I can't afford the time right now but would like to see progress on it. ;)

---

### Post by PatrickMoore on 2010-03-07
i'm thrilled to try it once i finish my paper. 
two things i would like to know.

#1 will you include a coverflow like extension?
#2 are you going to integrate into conky?

---

### Post by nothingspecial on 2010-03-07
> **PatrickMoore said:**
> i'm thrilled to try it once i finish my paper. 
two things i would like to know.
#1 will you include a coverflow like extension?

Maybe, but I happen to think the library browser is better. Check with the dev. I hope not. Nothing that will make this player slower.


> **PatrickMoore said:**
> #2 are you going to integrate into conky?

I think you have that the wrong way round. You have to integrate it with conky, or wait till someone else does.

Anyway, did you try it yet?

I think it`s the best music player for linux.

You?

---

### Post by nothingspecial on 2010-03-07
When I first came across this player, one of my first thoughts and comments was that iPod support is a must.

Now, I`m perfectly happy listening with G-Que and managing iPods with gtkpod.

I wouldn`t want ipod support to slow guayadeque.

I may be wrong


What do you think?

---

### Post by anonbeat on 2010-03-07
> **flohmann said:**
> Can you contact the guy? If he already started it would be nice to have the stuff he did.

I would try to find someone willing to work on it. I can't afford the time right now but would like to see progress on it. ;)

Sent email asking about it. I will tell you once I get his reply.
Thanks

---

### Post by anonbeat on 2010-03-07
> **PatrickMoore said:**
> i'm thrilled to try it once i finish my paper. 
two things i would like to know.

#1 will you include a coverflow like extension?
#2 are you going to integrate into conky?

@#1 Not anytime soon. I will add more features to the album browser and plan to make it more easy to filter what you want to find.

@#2 Im not going to add conky integration. But I dont think it should be too hard to do as using mpris interface you can access all player information needed to do it. If you have other supported player using mpris write it for guayadeque will be damn easy.

Thanks for your interest

---

### Post by Pifilatakanemu on 2010-03-07
Some thoughts:


[LIST=1]
[*]It would be nice if there would be new images for the browser and the player for the standard "front/label" when there is none related to the song/album. Perhaps the designer of the new icon has an idea suiting his recent artwork?
[*]What about a "file structure" panel to search the collection via the folder structure?
[*]I'd love to be able to choose different colors for the highlighted titles etc. in Guayadeque. (My main one suits my needs for Ubuntu but looks rather odd in guayadeque.
[*]Just to consider: What about "search as you type" in the library search?
[/LIST]

---

### Post by VastOne on 2010-03-07
> **flohmann said:**
> Some thoughts:


[LIST=1]
[*]It would be nice if there would be new images for the browser and the player for the standard "front/label" when there is none related to the song/album. Perhaps the designer of the new icon has an idea suiting his recent artwork?
[*]What about a "file structure" panel to search the collection via the folder structure?
[*]I'd love to be able to choose different colors for the highlighted titles etc. in Guayadeque. (My main one suits my needs for Ubuntu but looks rather odd in guayadeque.
[*]Just to consider: What about "search as you type" in the library search?
[/LIST]

These are best answered at this thread


[http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)

---

### Post by nothingspecial on 2010-03-07
> **flohmann said:**
> Some thoughts:



[*]Just to consider: What about "search as you type" in the library search?
[/LIST]

guayadeque does this.

Try again. Click on the library tab and type.

---

### Post by PatrickMoore on 2010-03-07
im installing it now. is there a different repo for 64 bit, will it work for 64 bit?

---

### Post by jasonbird01 on 2010-03-07
Thanks for sahring~~~~~~~~
I have fount this long time

---

### Post by Pifilatakanemu on 2010-03-08
> **nothingspecial said:**
> guayadeque does this.

Try again. Click on the library tab and type.


Nope. I type and nothing happens until I hit Enter.


edit:


This is what anonbeat answered:
> 
About search as you type its implemented in the different listboxes. For example you can be at the artists listbox and start typing. That way you will start searching what you are typing. 

Its not implemented in the search text entry.

---

### Post by nothingspecial on 2010-03-09
There is a new place to request features.

[COLOR="Magenta"]http://sourceforge.net/apps/ideatorrent/guayadeque/[/COLOR]

Other users can vote for these ideas and the more popular the idea is, the more chance it has of being implemented.

Remember though, the prime goal of Guayadeque is to be fast, even for large music collections. Anything that slows it down, however popular, will not be implemented.

---

### Post by VastOne on 2010-03-09
> **PatrickMoore said:**
> im installing it now. is there a different repo for 64 bit, will it work for 64 bit?

All I have and use is 64 bit and this [http://_sourceforge.net/projects/guayadeque_](http://_sourceforge.net/projects/guayadeque_)  works

---

### Post by h!v on 2010-03-09
Installation on Jaunty
We have this listed.
```
gstreamer0.10-dev
```
Should rather be 
```

libgstreamer0.10-dev

```
Vide here.
```

 sudo aptitude search gstreamer0.10-dev
i   libgstreamer0.10-dev                     - GStreamer core development files      

```

---

### Post by nothingspecial on 2010-03-09
Sorted, thanks.

I`m only trying to help.

If I have anything else wrong....... please post :D

---

### Post by h!v on 2010-03-09
I'm actually grateful for info on Jaunty. I dumped it after some crash when configuring ( taglib). Now went with no problems.
Most people that compile will catch it anyway. It's ubuntu anyway, most people paste commands. One thing I'd point out sign of end of line after "zlib1g-dev".  This sign pastes as "enter" while pasting. Maybe on purpose.

Cheers.

---

### Post by anonbeat on 2010-03-10
> **flohmann said:**
> What about the German translation?
Who is doing it (somebody said that there is someone on it) ?

I'd write a small article for the German Ubuntu Community News at the moment when there is a German version available.

I just love this player!

Hello,
   the german translation is in svn now. The guy who did it said it was not complete so if you want to fill the gaps let me know if you need help to start. 

Thanks

---

### Post by Pifilatakanemu on 2010-03-10
Great news!

I'm busy at the moment but I will update my call for translators at the German Forum.

---

### Post by Pifilatakanemu on 2010-03-12
Perhaps the idea torrent would get more feedback if it would be displayed on the guayadeque main page at sourceforge?

---

### Post by Mrmotinjo on 2010-03-12
[COLOR=Black]Hi all,
I'm excited to see my icon in action, and I'm also very glad I could contribute to the visual design of such a fine new music player.
Thank you guys for chosing my work to represent [/COLOR][COLOR=Black][COLOR=Black]Guayadeque[/COLOR]! It means a lot to me :)
Props to anonbeat for making such a great piece of software.[/COLOR] :KS

---

### Post by Daveth on 2010-03-12
um, I get up to the Jaunty /guayadeque-svn$ ./build command but it fails to build because of this:

/guayadeque-svn$ ./build
rm: cannot remove `CMakeCache.txt': No such file or directory
./build: line 2: cmake: command not found

Any suggestions? Should I just start again?
David

---

### Post by nothingspecial on 2010-03-12
> **Daveth said:**
> um, I get up to the Jaunty /guayadeque-svn$ ./build command but it fails to build because of this:

/guayadeque-svn$ ./build
rm: cannot remove `CMakeCache.txt': No such file or directory
./build: line 2: cmake: command not found

Any suggestions? Should I just start again?
David

Try again, I have edited the instructions. Don`t have jaunty to test it. Should work now. Post any errors though. Thanks

---

### Post by Uncle Spellbinder on 2010-03-12
I can't say how much I'm really loving Guayadeque Music Player. The best player I've used in Lunux to be sure.


*And Guayadeque's presence on the web is growing!* 

Guayadeque is up on Gnome Files: [http://www.gnomefiles.org/app.php?soft_id=2490](http://www.gnomefiles.org/app.php?soft_id=2490)

and LastFM: [http://www.last.fm/group/Guayadeque](http://www.last.fm/group/Guayadeque)

and OMG!Ubuntu!: [http://www.omgubuntu.co.uk/2010/02/guayadeque-music-player-light-unique.html](http://www.omgubuntu.co.uk/2010/02/guayadeque-music-player-light-unique.html)

and Ubutu Geek: [http://www.ubuntugeek.com/guayadeque-nice-music-player.html](http://www.ubuntugeek.com/guayadeque-nice-music-player.html)

and Web Upd8: [http://www.webupd8.org/2009/05/guayadeque-lightweight-linux-audio.html](http://www.webupd8.org/2009/05/guayadeque-lightweight-linux-audio.html)

and Softpedia: [http://linux.softpedia.com/get/Multimedia/Audio/Guayadeque-Music-Player-46023.shtml](http://linux.softpedia.com/get/Multimedia/Audio/Guayadeque-Music-Player-46023.shtml)

and Buckycomputing.net: [http://buckycomputing.net/blog/how-to-install-guayadeque-music-player/](http://buckycomputing.net/blog/how-to-install-guayadeque-music-player/)

and Tech Blog Parade: [http://techblogparade.blogspot.com/2010/02/guayadeque-music-player-light-unique.html](http://techblogparade.blogspot.com/2010/02/guayadeque-music-player-light-unique.html)

and Winxperts: [http://www.winxperts.net/503/ubuntu-spotlight-guayadeque-music-player](http://www.winxperts.net/503/ubuntu-spotlight-guayadeque-music-player)

and Winxperts Forums: [http://www.forums.winxperts.net/index.php?/topic/1313-ubuntu-spotlight-guayadeque-music-player/](http://www.forums.winxperts.net/index.php?/topic/1313-ubuntu-spotlight-guayadeque-music-player/)

and My Linux Exploits: [http://linux.zachjones.net/2010/02/27/guayadeque-say-who-whatta-a-light-big-library-music-player/](http://linux.zachjones.net/2010/02/27/guayadeque-say-who-whatta-a-light-big-library-music-player/)

and FreshMeat: [http://freshmeat.net/projects/guayadeque](http://freshmeat.net/projects/guayadeque)

and OpenSUSE: [http://en.opensuse.org/OpenSUSE_Weekly_News/100#New.2FUpdated_Applications_.40_openSUSE](http://en.opensuse.org/OpenSUSE_Weekly_News/100#New.2FUpdated_Applications_.40_openSUSE)

and Twitter: [http://twitter.com/omgubuntu/status/9238046677](http://twitter.com/omgubuntu/status/9238046677)

---

### Post by Daveth on 2010-03-12
no joy- same error. Better than the deb package which complains of a huge list of unmet dependencies, and the ppa is only for karmic. I might wait till Lucid. Your swift reply was most appreciated though.

---

### Post by nothingspecial on 2010-03-12
I`m just about to go out.

I`ll have to look into it tommorow.
Cheers.

I`t`ll be worth it when you get it.

---

### Post by Uncle Spellbinder on 2010-03-12
Let's try to keep this thread on the general discussion aspect of Guayadeque and move help/support questions to the [Test Thread](http://ubuntuforums.org/showthread.php?t=1380811).

Just a thought. ;)

---

### Post by Goombie on 2010-03-12
I installed the latest svn of Guayadeque this morning, and the menu bar seems to be missing. :(
Does anyone know how to fix this? I updated from anonbeats's PPA version to the SVN version on an Ubuntu Karmic system.

---

### Post by Uncle Spellbinder on 2010-03-12
@ Goombie. That's an odd error. But you're likely to get quicker help if you post in the Test Thread. See link in my sig.

---

### Post by Goombie on 2010-03-12
Whoops, I thought I was posting in the testing thread. >.<

---

### Post by VastOne on 2010-03-12
> **Uncle Spellbinder said:**
> Let's try to keep this thread on the general discussion aspect of Guayadeque and move help/support questions to the [Test Thread](http://ubuntuforums.org/showthread.php?t=1380811).

Just a thought. ;)

+1

It is very difficult to keep track of the issues with several different places that anonbeat (the developer) has to trace and correct.

Anonbeat has asked for the very same thing on many occasions, it is up to nothingspecial to correct this instead of taking on the developers responsibilities. 

I could see the need for this if there were no development or build going on, but we have one of the best hands on with us now so lets support what he needs.

The easiest solution and most absolute benefit to everyone involved is to merge this thread with the other one

---

### Post by Uncle Spellbinder on 2010-03-12
Anonbeat has created a new Guayadeque Social Group [_[COLOR="SeaGreen"]Here[/COLOR]_]("http://ubuntuforums.org/group.php?groupid=741")

---

### Post by Uncle Spellbinder on 2010-03-12
Thought I'd share this from the [Guayadeque Test Request Thread](http://ubuntuforums.org/showthread.php?p=8957229#post8957229)

> **anonbeat said:**
> **The release 0.2.5 have been published**. Its already in ppa for karmic and for Lucid.

I would like to thank everyone who participated in the Icon development poll at OMG! UK.  Every icon and every artist was appreciated and the resulting artwork and design was fantastic.  The 1800 votes cast was a surprise, but shows how effective a good blog can be.  Mrmotinjo won with his icon creation and will forever be linked to Guayadeque and for this we are grateful and humbled.

Also I would like to thank all your contribution to this project. With your help I could find and fix lot of bugs and add many features.

Stay tuned as there are still lot to come :)

Thank you very much
J.Rios

---

### Post by armageddon08 on 2010-03-13
Does Guayadeque have Magnatune and Jamendo integration?

---

### Post by VastOne on 2010-03-13
> **armageddon08 said:**
> Does Guayadeque have Magnatune and Jamendo integration?

Not yet, anonbeat has mentioned both for future release

You can speak directly to him [_[COLOR="Blue"]Here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by Pifilatakanemu on 2010-03-13
> **anonbeat said:**
> Hello,
   the german translation is in svn now. The guy who did it said it was not complete so if you want to fill the gaps let me know if you need help to start. 

Thanks


Ok, after the latest Update my Guayadeque turned into something between bad German and English.

I surely appreciate the effort of the guy who made it but it's not exactly inviting to use Guayadeque with the German translation at this state. Could you make it available for translation without using it as a standard for the moment?

I know it's not very constructive as I am not able to improve the translation myself but I think most users would prefer the English version instead of a mixture with some serious misspellings.

;)

---

### Post by anonbeat on 2010-03-13
> **flohmann said:**
> Ok, after the latest Update my Guayadeque turned into something between bad German and English.

I surely appreciate the effort of the guy who made it but it's not exactly inviting to use Guayadeque with the German translation at this state. Could you make it available for translation without using it as a standard for the moment?

I know it's not very constructive as I am not able to improve the translation myself but I think most users would prefer the English version instead of a mixture with some serious misspellings.

;)

I dont know about german so I could not evaluate the quality of the translation. The translation is in the po/de dir of the project. If someone want to improve it do it freely and email me the result.

Thanks

---

### Post by Uncle Spellbinder on 2010-03-13
I made a Blogspot Blogger page for Guayadeque!

[http://guayadequemusicplayer.blogspot.com/](http://guayadequemusicplayer.blogspot.com/)


Show your support for Guayadeque by following this blog. Click "follow"

---

### Post by Uncle Spellbinder on 2010-03-13
Does anyone have a large .png (at least 200x200) of the new logo? I'd like to add it to the blog.

---

### Post by anonbeat on 2010-03-13
> **Uncle Spellbinder said:**
> Does anyone have a large .png (at least 200x200) of the new logo? I'd like to add it to the blog.

here. If you need other size or other format let me know.

---

### Post by Uncle Spellbinder on 2010-03-13
> **anonbeat said:**
> here. If you need other size or other format let me know.

Absolutely perfect.Thanks, anonbeat!

---

### Post by Daveth on 2010-03-13
> **Uncle Spellbinder said:**
> Let's try to keep this thread on the general discussion aspect of Guayadeque and move help/support questions to the [Test Thread](http://ubuntuforums.org/showthread.php?t=1380811).

Just a thought. ;)

good idea, but in that instance it ought to say that comments about basic support are welcome there. It currently does not look to be the place to go if you cannot even get the thing running!

---

### Post by Uncle Spellbinder on 2010-03-13
> **Daveth said:**
> good idea, but in that instance it ought to say that comments about basic support are welcome there. It currently does not look to be the place to go if you cannot even get the thing running!

Why not? Support is support.

---

### Post by nothingspecial on 2010-03-14
In this case, I think Daveth posted his question in the correct thread.

The problem is due to the instructions for installation on Jaunty, that I have posted in #1 in this thread.

I agree that any support questions should be asked in the other thread, but if I have made an oopsy we don`t want to bother anon with it.

Looking at it now.

---

### Post by Pifilatakanemu on 2010-03-15
> **Uncle Spellbinder said:**
> I made a Blogspot Blogger page for Guayadeque!

[http://guayadequemusicplayer.blogspot.com/](http://guayadequemusicplayer.blogspot.com/)


Show your support for Guayadeque by following this blog. Click &quot;follow&quot;

  What's your plan for this blog? More than collecting the posts of other blogs about Guayadeque?   Could you please post your signature in HTML? I'd love to use it, too. If it's fine with you? ;)

---

### Post by Uncle Spellbinder on 2010-03-15
> **flohmann said:**
> What's your plan for this blog? More than collecting the posts of other blogs about Guayadeque?   Could you please post your signature in HTML? I'd love to use it, too. If it's fine with you? ;)
Plans for the blog? Never really thought of it like that. More af a review and how-to for installation. I suppose I could add release milestones as they happen.

As far as the signature. My signature is in BBCode as this forum does not support HTML. If you would like it in HTML, just copy the links and have at it. ;)

---

### Post by Mrmotinjo on 2010-03-17
Hello!

I made a prototype for control pictograms using the new Guayadeque icon as style marker. I'm interested in your opinion on these icons- do you think they'd fit in, are they clear and understandable enough etc. 
Any ideas, advice and/or observations are welcome! 
Some icons are still missing ('repeat one', for instance) but I will try and make those, too :)

Cheers
[IMG]http://img.photobucket.com/albums/v653/mrmotinjo/GQctrlp2.png[/IMG]

---

### Post by anonbeat on 2010-03-17
> **Mrmotinjo said:**
> Hello!

I made a prototype for control pictograms using the new Guayadeque icon as style marker. I'm interested in your opinion on these icons- do you think they'd fit in, are they clear and understandable enough etc. 
Any ideas, advice and/or observations are welcome! 
Some icons are still missing ('repeat one', for instance) but I will try and make those, too :)

Cheers
[IMG]http://img.photobucket.com/albums/v653/mrmotinjo/GQctrlp2.png[/IMG]

In my modest opinion they are just awesome!!!

---

### Post by VastOne on 2010-03-17
> **anonbeat said:**
> In my modest opinion they are just awesome!!!

I second that statement

---

### Post by koleoptero on 2010-03-17
> **VastOne said:**
> I second that statement

I third.

---

### Post by nothingspecial on 2010-03-17
fourth!

---

### Post by Pifilatakanemu on 2010-03-17
I like it!

But...
... there is one thing I love about Ubuntu: It's uniform look. All programmes use the same iconset, so you have a homogene (?) "look'n feel".

IMHO there should be no obligation to use any set of symbols -how good they might be! But it would be nice as an option.

Btw: What about a default "cover"-image? It still can be improved a bit...

Another thing:

anonbeat, I think the name "tabs" fit better than "panels" for the radio, browser etc. panel, don't you think?

---

### Post by Pifilatakanemu on 2010-03-18
Although I have the "podcast"-tab/panel deactivated Guayadeque searches for podcasts on every start. 

I'm not sure whether it uses a lot of resources, but if so, it would be nice to be able to  deactivate the podcast, radio etc.

edit:

Has someone already proposed Guayadeque for inclusion in the Ubuntu repo?

---

### Post by pickarooney on 2010-03-18
> **Mrmotinjo said:**
> Hello!

I made a prototype for control pictograms using the new Guayadeque icon as style marker. I'm interested in your opinion on these icons- do you think they'd fit in, are they clear and understandable enough etc. 
Any ideas, advice and/or observations are welcome! 
Some icons are still missing ('repeat one', for instance) but I will try and make those, too :)

Cheers
[IMG]http://img.photobucket.com/albums/v653/mrmotinjo/GQctrlp2.png[/IMG]

They're beautiful! They'll clash with my Aqua theme, but they're beautiful.

---

### Post by Mrmotinjo on 2010-03-18
Thanks for the comments! I've sent the iconset to Anonbeat, and hopefully we'll see how it works out. 

I agree with Flohmann [SIZE="1"][COLOR="DimGray"]even though the 'uniform look' of Ubuntu is in question because of the weird logo redesign, hehe[/COLOR][/SIZE], the choice of how the player looks should be left to the users.
The support for custom skins would definitely be nice in the future (and an option to leave the controls as they are by default in the near future, perhaps?) :)
I would also add that, in my experience, an unique visual identity can only be a good thing, especially in the field of media players :KS

Also, please note that the blue icons should not be blue by default, only when selected/activated.
I've expanded and tweaked the iconset a bit, too, and it should now include all the necessary icons for the player controls.

Here's a preview of the current iconset:
[IMG]http://img.photobucket.com/albums/v653/mrmotinjo/GQ_iconset_preview.png[/IMG]

Cheers

---

### Post by anonbeat on 2010-03-18
> **Mrmotinjo said:**
> Thanks for the comments! I've sent the iconset to Anonbeat, and hopefully we'll see how it works out. 

I agree with Flohmann [SIZE="1"][COLOR="DimGray"]even though the 'uniform look' of Ubuntu is in question because of the weird logo redesign, hehe[/COLOR][/SIZE], the choice of how the player looks should be left to the users.
The support for custom skins would definitely be nice in the future (and an option to leave the controls as they are by default in the near future, perhaps?) :)
I would also add that, in my experience, an unique visual identity can only be a good thing, especially in the field of media players :KS

Also, please note that the blue icons should not be blue by default, only when selected/activated.
I've expanded and tweaked the iconset a bit, too, and it should now include all the necessary icons for the player controls.

Here's a preview of the current iconset:
[IMG]http://img.photobucket.com/albums/v653/mrmotinjo/GQ_iconset_preview.png[/IMG]

Cheers

All i can say about them is WoW

Thanks once more time mrmotinjo.

---

### Post by pickarooney on 2010-03-18
I can't wait to see these in place!

---

### Post by Uncle Spellbinder on 2010-03-18
> **Mrmotinjo said:**
> Thanks for the comments! I've sent the iconset to Anonbeat, and hopefully we'll see how it works out. 

I agree with Flohmann [SIZE="1"][COLOR="DimGray"]even though the 'uniform look' of Ubuntu is in question because of the weird logo redesign, hehe[/COLOR][/SIZE], the choice of how the player looks should be left to the users.
The support for custom skins would definitely be nice in the future (and an option to leave the controls as they are by default in the near future, perhaps?) :)
I would also add that, in my experience, an unique visual identity can only be a good thing, especially in the field of media players :KS

Also, please note that the blue icons should not be blue by default, only when selected/activated.
I've expanded and tweaked the iconset a bit, too, and it should now include all the necessary icons for the player controls.

Here's a preview of the current iconset:
[IMG]http://img.photobucket.com/albums/v653/mrmotinjo/GQ_iconset_preview.png[/IMG]

***Wonderful*** work, Mrmotinjo. I eagerly await anonbeat's implementation of this.

---

### Post by Carlos C on 2010-03-18
The last weeks Guayadeque has had significant improvements and these icons are a real improve. What can I say? every day I like this player even more.

---

### Post by rotwang888 on 2010-03-18
Sweet. Middle row.  Want. Want want want.

---

### Post by Mrmotinjo on 2010-03-19
Hello again!

I had some spare time today, and have tried to make a squareish, single-bar, glass-covered fancy version of my iconset. It kinda fits in the current Guayadeque control layout, and of course it's only at concept level now, just wanted to show the idea to you guys and see what you would think of this option :)

Black may not be the final color, too.

[IMG]http://img.photobucket.com/albums/v653/mrmotinjo/ctrls_small.png[/IMG]

Cheers

---

### Post by aL3xandar on 2010-03-19
Lovely @Mrmotinjo, can wait to see more =)

---

### Post by Uncle Spellbinder on 2010-03-20
> **pickarooney said:**
> I can't wait to see these in place!

The new icon set has landed in SVN. 

[http://guayadequemusicplayer.blogspot.com/](http://guayadequemusicplayer.blogspot.com/)

---

### Post by Ruzbeh on 2010-03-21
Trying it out right now. It's pretty darn impressive! One thing I really don't like at all is that when you mouse-over a cover, you get to see a CD case with the cover. A CD case. Really? Ew.

---

### Post by Uncle Spellbinder on 2010-03-21
> **Ruzbeh said:**
> One thing I really don't like at all is that when you mouse-over a cover, you get to see a CD case with the cover. A CD case. Really? Ew.
I was going to bring that up, but it's a relatively minor issue. I really would rather see just the cover as well (sans the cd case). Perhaps a bit larger image as well.

---

### Post by VastOne on 2010-03-21
> **Ruzbeh said:**
> Trying it out right now. It's pretty darn impressive! One thing I really don't like at all is that when you mouse-over a cover, you get to see a CD case with the cover. A CD case. Really? Ew.

You can change the cover of any song with album browser or editing the song. 

You can also change the default cover by putting any jpg or png file you have in the directory of the music and that will  be the default cover for all songs in that directory.

---

### Post by Uncle Spellbinder on 2010-03-21
> **Ruzbeh said:**
> Trying it out right now. It's pretty darn impressive! One thing I really don't like at all is that when you mouse-over a cover, you get to see a CD case with the cover. A CD case. Really? Ew.[QUOTE=VastOne;9003987]You can change the cover of any song with album browser or editing the song. 

You can also change the default cover by putting any jpg or png file you have in the directory of the music and that will  be the default cover for all songs in that directory.[/QUOTE]

He's talking about the default mouse-over of the album cover. It shows a CD case regardless of the artwork:

---

### Post by koleoptero on 2010-03-21
> **Uncle Spellbinder said:**
> He's talking about the default mouse-over of the album cover. It shows a CD case regardless of the artwork:

I think that's quite nice.

Although I don't use it regularly I believe that as far as the interface goes, those close buttons at the various elements need a change. They are ugly.

---

### Post by Ruzbeh on 2010-03-21
Another thing I like, another minor thing really, is the icon/logo. It's just plain good. Colorful, recognizable. I'm totally impressed with what I've seen so far, that I do want to help with the development (I'll post at the testing thread). There are so many players out there for Linux, I haven't tried many, but this is one of the very few pieces of software that impresses me with it's direction that it's just plain worth it to help out. I'm definitely gonna need iPod support though. If it did have device support, Guayadeque would easily trump Rhythmbox and Banshee, which I think is impressive considering Guayadeque is much younger.

> **koleoptero said:**
> I think that's quite nice.
I can understand why some people would appreciate it. I guess it could be made optional. Or maybe do something cool like, have that jewelcase overlay only for albums that are older than 1990, because in the 60s and 70s and so on it was all vinyl.

Posting another screen for people who wonder what it looks like:

[[img]http://i41.tinypic.com/24nmdz7_th.png[/img]](http://i41.tinypic.com/30tndl3.jpg)

Interface is very solid.

---

### Post by Pifilatakanemu on 2010-03-22
> **koleoptero said:**
> 
Although I don't use it regularly I believe that as far as the interface goes, those close buttons at the various elements need a change. They are ugly.

Vote for it here: [http://sourceforge.net/apps/ideatorrent/guayadeque/ideatorrent/idea/17/](http://sourceforge.net/apps/ideatorrent/guayadeque/ideatorrent/idea/17/)


I totally agree.

---

### Post by Uncle Spellbinder on 2010-03-22
From the [Test and Support thread](http://ubuntuforums.org/showthread.php?p=9008483#post9008483):

> **anonbeat said:**
> As requested by many ppl the close buttons have been changed to something like the player control buttons in svn revision 808

Thanks for your comments and suggestions.

---

### Post by Pifilatakanemu on 2010-03-31
was Guayadeque already proposed for the Ubuntu repositories?

---

### Post by Sale on 2010-04-07
Hi,

Great work, great player - light, quick, great looking... :) I installed it from the PPA yesterday and am still thrilled.

I've been using Listen for quite some time, but I think I'll default to Guayadeque from now on.

There is just one "feature request" that I have - after I search for the song (by name), I'd like to be able to select one of the search results and then automatically play/enqueue the whole album in which the selected song is.

Thanks, and, best of luck to the developer/team :)

---

### Post by Pifilatakanemu on 2010-04-07
> **Sale said:**
> 
There is just one "feature request" that I have - after I search for the song (by name), I'd like to be able to select one of the search results and then automatically play/enqueue the whole album in which the selected song is.

There is a two step solution for your feature. Rightclick the song, select "Select -> Album" (I'm using the german version, it might be another expression) and then you have them all and can easily mark them and add them to your playlist. 
If this is not satisfying feel free to open a feature request in the idea torrent (check signature)

I'd like to have a screenshot of Guayadeque within a dark theme for the german Wiki. It would be nice anyway to have a copuple of screenshots in order to demonstrate the flexibility of our beloved player. There is only one with the new look in the sourceforge gallery.

---

### Post by Sale on 2010-04-07
> **flohmann said:**
> I'd like to have a screenshot of Guayadeque within a dark theme for the german Wiki. It would be nice anyway to have a copuple of screenshots in order to demonstrate the flexibility of our beloved player. There is only one with the new look in the sourceforge gallery.

Thanks for the explanation regarding my feature request. I think what is already available is good enough. And I can't make myself create yet another account (on sourceforge) that I'll probably never use again... :)


Anyway, as for the screenshot...I'm not sure I understand what it is that you want. I know how to change layouts, but what do you mean by "dark theme"? How do i change themes in guayadeqe?

Anyway, I've attached what I have.

---

### Post by northwestuntu on 2010-04-07
just started using the program and like how light it is.  great time to start a new music player since songbird has dropped out of the race.  i don't know about the name though?

---

### Post by Pifilatakanemu on 2010-04-07
> **Sale said:**
> Anyway, as for the screenshot...I'm not sure I understand what it is that you want. I know how to change layouts, but what do you mean by "dark theme"? How do i change themes in guayadeqe?

Anyway, I've attached what I have.

Nice to hear that I could help.

Thanks for the screenshot.
I refered to G-que in dark Ubuntu themes.

---

### Post by ceelo on 2010-04-07
Been using it for a few hours now, this is really a fantastic piece of software. It's so fast! Easpecially for a program that is so feature-rich. Scrolls through my collection like a hot knife through butter, much faster than Rhythmbox/Banshee/Exaile etc. 

Only wish I could listen to music continuously straight from my library, rather than having to add it to the playlist.

I think I just found a new default music player. :)

Also, the Smart Playlist feature is excellent. Once again, very fast! Keep up the great work on this amazing project.

---

### Post by Sale on 2010-04-08
> **flohmann said:**
> Nice to hear that I could help.

Thanks again. It was great to find out that the feature was (more or less) already there. Another "plus" for the developer.

> **flohmann said:**
> Thanks for the screenshot.
I refered to G-que in dark Ubuntu themes.

No problem :) Sadly, I find dark Ubuntu themes not to my liking, to say the least.

BTW, this is probably a "long shot", but since I dual boot with Windows, and spend about the same amount of time in each OS, I must ask: Is there any possibility of a Windows port?

---

### Post by Ruzbeh on 2010-04-08
I use iTunes when I'm in Windows. It's pretty similar.

---

### Post by Sale on 2010-04-08
> **Ruzbeh said:**
> I use iTunes when I'm in Windows. It's pretty similar.

93MB for a media player (just downloading it now)? Thanks, I'd prefer something a little lighter :) I usually use Media Monkey, WMP or just VLC, in that order.

---

### Post by anonbeat on 2010-04-08
> **flohmann said:**
> There is a two step solution for your feature. Rightclick the song, select "Select -> Album" (I'm using the german version, it might be another expression) and then you have them all and can easily mark them and add them to your playlist. 
If this is not satisfying feel free to open a feature request in the idea torrent (check signature)

I'd like to have a screenshot of Guayadeque within a dark theme for the german Wiki. It would be nice anyway to have a copuple of screenshots in order to demonstrate the flexibility of our beloved player. There is only one with the new look in the sourceforge gallery.

There are new screenshots with dark theme in the guayadeque gallery. 
[https://sourceforge.net/apps/gallery/guayadeque/index.php?g2_itemId=94](https://sourceforge.net/apps/gallery/guayadeque/index.php?g2_itemId=94)

---

### Post by motorcity909 on 2010-04-08
Been trying it out over the past couple of days since finding that Songbird development for Linux is ceasing.

Must say I like it very much, especially how it handles album covers, much better than Rhythmbox or Banshee.  It seems faster than Songbird and I like the varied sorting options.  Album browser looks great too.

One question though - how do you delete a track or album from the library?  I've got a bunch of mp3s that I keep but don't want in my library (like podcasts, audio books and radio documentaries).  I've added them as I simply scanned the entire Music folder but now want to remove them.

Anyone?

---

### Post by ubunterooster on 2010-04-08
I'm trying it now...

---

### Post by Pifilatakanemu on 2010-04-09
> **anonbeat said:**
> There are new screenshots with dark theme in the guayadeque gallery. 
[https://sourceforge.net/apps/gallery/guayadeque/index.php?g2_itemId=94](https://sourceforge.net/apps/gallery/guayadeque/index.php?g2_itemId=94)

Ok great, I just updated the article. If somebody wants to have a look at it:
[http://wiki.ubuntuusers.de/Guayadeque](http://wiki.ubuntuusers.de/Guayadeque)

;)

---

### Post by docus on 2010-04-09
Just a quick question - is iPod sync a planned feature of G-Que?  I played around with G-Que a few weeks ago and liked it, but without iPod sync I coudln't give up Rhythmbox or Banshee (although I appreciate that not everyone needs or wants this feature, so maybe I'll just have to accept G-Que isn't for me... :( )

---

### Post by anonbeat on 2010-04-09
> **docus said:**
> Just a quick question - is iPod sync a planned feature of G-Que?  I played around with G-Que a few weeks ago and liked it, but without iPod sync I coudln't give up Rhythmbox or Banshee (although I appreciate that not everyone needs or wants this feature, so maybe I'll just have to accept G-Que isn't for me... :( )

Guess without an ipod to test is hard for me to implement this feature. If i get enought donations I would like to buy one and add support for it.

Thanks

---

### Post by ubunterooster on 2010-04-09
Works well in xubuntu 10-04. Quite speedy. This, however, needs a nickname.

---

### Post by koleoptero on 2010-04-09
This player is doing well. I still prefer cmus for most of my casual listening, but when I need more features I use guayadeque now. Well done developers.

Oh and I met with 0 bugs the past couple of days that I've been using it regularly. I'm using the -svn from the ppa. Also the buttons give it that distinctive feeling. Well done again.

---

### Post by myrnamynkoff on 2010-04-09
wow!

thank you so much! i'm really new at linux and the only thing that I found I didn't like at all so far was the music player I had and I've been trying to find a good one for a long time now! I love this new one! Although I agree the name is quite strange. maybe you can rename it 'Guaya'? :P

---

### Post by Dobbie03 on 2010-04-09
I dont have te menu bar at the top of the player.  Whats happened?

---

### Post by Lysias on 2010-04-09
> **MattDobson said:**
> I dont have te menu bar at the top of the player.  Whats happened?

There's a similar bug report at [_Launchpad_]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/544436").

You can also post in the support thread for Guayadeque here: _[http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)_

---

### Post by apocalypse80 on 2010-04-10
Great work :KS
Mediamonkey is my golden standard for media management and this is as close as I've ever come with a linux app.

Any thoughts on integrating some kind of format conversion?

Just in case anyone is interested, I made a tiny conky script for guayadeque (really, really needs a nickname...).
It uses the resources from [_conky-colors_]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328") and looks like this;

[img]http://ubuntuforums.org/attachment.php?attachmentid=152874&stc=1&d=1270940943[/img]

It's in perl, since I can't write in python and it's not very elegant, since I'm a noob, but it seems to work.
I guess someone more knowledgeable could make a better version.

---

### Post by motorcity909 on 2010-04-11
Quick question.  Am I right in saying that the only way to add a new album(s) to the player is by rescanning the entire library, rather than just pointing it to the new folder or dragging the new tracks onto it?

Rescanning plays havoc with some album covers as in some of my album folders I've got other pictures (back covers, inside booklets, scans of magazine reviews) which the player decides to use as the album cover so I have to go through correcting them.  Again.

Also, as per my earlier post (#217), this re-adds a bunch of mp3s I don't want in the library.  Still can't see a way to delete files other than temporarily move them out of my Music folder, re-scan the library, then move 'em back to Music.

Like the player in all other respects
Dave

---

### Post by Ian dewhurst on 2010-04-11
As far as I am aware you can just update the library rather the do a complete rescan.
I had this problem also but I think it doesn't happen on an update.

---

### Post by Ruzbeh on 2010-04-11
I think you can just use GMP as a short-hand (although it looks a lot like 'GIMP' on first sight). No one says Windows Media Player, 'WMP' is used instead. GMP might work.

---

### Post by Uncle Spellbinder on 2010-04-11
> **Ian dewhurst said:**
> As far as I am aware you can just update the library rather the do a complete rescan.
I had this problem also but I think it doesn't happen on an update.
Yep. Click Library in the upper left for the drop-down. The click "Update Library". Faster than a complete rescan and just as accurate. 

By the way. For anyone needing help and support with Guayadeque, the testing and support thread is in the Multimedia & Video section. Quicker for support as this thread is general discussion and such. See link in my signature.

---

### Post by WiebeS on 2010-04-12
> **apocalypse80 said:**
> Great work :KS
Mediamonkey is my golden standard for media management and this is as close as I've ever come with a linux app.

Any thoughts on integrating some kind of format conversion?

Just in case anyone is interested, I made a tiny conky script for guayadeque (really, really needs a nickname...).
It uses the resources from [_conky-colors_]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328") and looks like this;

[img]http://ubuntuforums.org/attachment.php?attachmentid=152874&stc=1&d=1270940943[/img]

It's in perl, since I can't write in python and it's not very elegant, since I'm a noob, but it seems to work.
I guess someone more knowledgeable could make a better version.
apocolypse80, how do you use the script in conky, what do you have to type in your conkyrc file?, I am new to this all.
Thanks!

---

### Post by northwestuntu on 2010-04-12
how do you keep the tracks playing in the library? it stops after 1 track? do you have to use the playlist to get continues play?

---

### Post by Lysias on 2010-04-12
> **northwestuntu said:**
> how do you keep the tracks playing in the library? it stops after 1 track? do you have to use the playlist to get continues play?

Yes, GMP plays songs only from the playlist. There's also Smart Mode which adds similar songs to the playlist by utilizing Last.FM data. It's quite nice :)

---

### Post by northwestuntu on 2010-04-12
well that's a bummer.  seems like a simple function to allow continuous playback through your library.

---

### Post by rudihawk on 2010-04-12
> **northwestuntu said:**
> well that's a bummer.  seems like a simple function to allow continuous playback through your library.

Thats the thing that annoyed tha hell out of me when using it. 

It wouldn't continue playing through the library. I first had to drag it all into that playlist window beneath the track information before it would work, and then it was a mission to find anything to listen to. 

Dealbreaker for me. 

So I went back to Banshee :D:guitar:

---

### Post by northwestuntu on 2010-04-12
> **rudihawk said:**
> Thats the thing that annoyed tha hell out of me when using it. 

It wouldn't continue playing through the library. I first had to drag it all into that playlist window beneath the track information before it would work, and then it was a mission to find anything to listen to. 

Dealbreaker for me. 

So I went back to Banshee :D:guitar:

well it's still early development of the program so could be something they could add later.  maybe they can work on that program name too :P

---

### Post by apocalypse80 on 2010-04-12
> **WiebeS said:**
> apocolypse80, how do you use the script in conky, what do you have to type in your conkyrc file?, I am new to this all.
Thanks!

I have it placed under the path, so I just add:

```
${execpi 5 guayCover}
```

to .conkyrc, where 5 is the update interval in seconds.
Alternatively replace guayCover with a full path.

I'll repeat that it's pretty rough, using fixed position of the images, so it might not suit you.
You'll also note it *requires* conky-colors, since it uses the cd icons from that.

---

### Post by Lysias on 2010-04-13
Thanks for the conky script, apocalypse80. Though I don't have use for it myself I learned something new from it.

I have a couple of questions for Guayadeque users:

1) do you use labels and if so, for what purpose?

2) what kind of a layout do you use?

As for me, I don't (yet) use labels but if someone posts a good reason for using them, that may change ;)

My current layout is pretty much the default, I've just added the VU meter beneath the now playing area. I keep GMP maximised in order to better utilize the library.

---

### Post by anonbeat on 2010-04-13
> **Lysias said:**
> Thanks for the conky script, apocalypse80. Though I don't have use for it myself I learned something new from it.

I have a couple of questions for Guayadeque users:

1) do you use labels and if so, for what purpose?

2) what kind of a layout do you use?

As for me, I don't (yet) use labels but if someone posts a good reason for using them, that may change ;)

My current layout is pretty much the default, I've just added the VU meter beneath the now playing area. I keep GMP maximised in order to better utilize the library.

I sadly have not much time to use Guayadeque but I can answer a few questions.

About the labels for me is a must! For example I have this labels among others : Ballads, Favourites, Favourites Oldies

For example you can have a track that has genre as Heavy metal but its a ballad and other that is Pop that also is a ballad. If I want to listen slow tracks I select this label and I can find all that tracks. 
Same with the others.
You can put many labels to the same track, this way a track can be Ballad, Favourite, Favourite Oldies, By Female, 80s, etc

About my layout I use default + vumeters like you. Vumeters between player playlist and the player controls.

---

### Post by nothingspecial on 2010-04-13
> **anonbeat said:**
> I sadly have not much time to use Guayadeque but I can answer a few questions.

About the labels for me is a must! For example I have this labels among others : Ballads, Favourites, Favourites Oldies

For example you can have a track that has genre as Heavy metal but its a ballad and other that is Pop that also is a ballad. If I want to listen slow tracks I select this label and I can find all that tracks. 
Same with the others.
You can put many labels to the same track, this way a track can be Ballad, Favourite, Favourite Oldies, By Female, 80s, etc

And this is the whole point - no?

---

### Post by Lysias on 2010-04-14
> **anonbeat said:**
> About the labels for me is a must! For example I have this labels among others : Ballads, Favourites, Favourites Oldies

For example you can have a track that has genre as Heavy metal but its a ballad and other that is Pop that also is a ballad. If I want to listen slow tracks I select this label and I can find all that tracks. 
Same with the others.
You can put many labels to the same track, this way a track can be Ballad, Favourite, Favourite Oldies, By Female, 80s, etc

Thanks, I'm already thinking of some labels I might find useful.

---

### Post by Pifilatakanemu on 2010-04-15
Hey,

wondering why Guayadeque is not in the repositories of Ubuntu? 

YOU can take care of it.

There is procedure on this explained here: [https://wiki.ubuntu.com/MOTU/Contributing#Preparing%20New%20Packages]("https://wiki.ubuntu.com/MOTU/Contributing#Preparing%20New%20Packages")

is there anybody who wants to help guayadeque in order to get more users, reputation and getting more awesome?


is there anybody willing to invest some time into it? anonbeat is busy making the dirty stuff, so he appreciates every support.



edit: hey Mint guys! I'm sure there is a way to include Guayadeque in Mint, too. Check it out!

And what about the other distros? I'm sure there are a lot of users that are still searching the best Linux player. They should find Guayadeque, too!

---

### Post by Lysias on 2010-04-15
Good idea, flohmann.

> **flohmann said:**
> edit: hey Mint guys! I'm sure there is a way to include Guayadeque in Mint, too. Check it out!

Mint uses Ubuntu repositories, so if Guayadeque is added there, it's also available in Mint. But Mint also has a software portal (see [_here_]("http://linuxmint.com/software/?sec=category&id=165&release=6") for a listing of audio players) for some programs.

I made a [_.mint package_]("http://forums.linuxmint.com/viewtopic.php?f=91&t=2827") out of Guayadeque. The package adds the PPA repo and the key temporarily, installs Gdeque and any dependencies, and afterwards removes the repo. I think this .mint package can now be added to the software portal. I'll see about that. Though I'm not sure if I did everything right. But at least the package installed in Mint Fluxbox edition.

---

### Post by domachine on 2010-04-20
Wow great one, really!!
My new favourite :-)

Greetz Domi

---

### Post by Ian dewhurst on 2010-04-20
> **northwestuntu said:**
> how do you keep the tracks playing in the library? it stops after 1 track? do you have to use the playlist to get continues play?

You can get continous playback but you have to play the album so it plays track after tarck

---

### Post by Lysias on 2010-04-20
Hey anonbeat, Guayadeque isn't yet listed on Last.FM's page of Scrobblers: [http://build.last.fm/category/Scrobblers](http://build.last.fm/category/Scrobblers)

On the right hand side there's a link called "Submit yours". You can register yourself as the developer and Guayadeque gets more attention.

---

### Post by anonbeat on 2010-04-20
> **Lysias said:**
> Hey anonbeat, Guayadeque isn't yet listed on Last.FM's page of Scrobblers: [http://build.last.fm/category/Scrobblers](http://build.last.fm/category/Scrobblers)

On the right hand side there's a link called "Submit yours". You can register yourself as the developer and Guayadeque gets more attention.

Thanks. Submited it

---

### Post by hellocatfood on 2010-04-21
When you copy a playlist to a new folder could you have the option to just copy the mp3 files instead of putting them into individual folders?


Also, an issue with last.fm integration. When you enter your information there's no way to know if entering the details was successful. Perhaps it should check and confirm that the details are correct once you've entered them

---

### Post by Pifilatakanemu on 2010-04-21
> **hellocatfood said:**
> When you copy a playlist to a new folder could you have the option to just copy the mp3 files instead of putting them into individual folders?




Of course, just change the file pattern in the settings



btw: this thread is more about general discussion, the other one is for support/bugs and feature requests (even better: create an idea in the torrent!).

---

### Post by hellocatfood on 2010-04-21
Sorry, my mistake! I'll post to there from now on

---

### Post by BoredOutOfMyMind on 2010-04-23
Excellent choice over Exaile, which I liked but it IS buggy.   I listen to online radio streams and streamtheworld provisioning opened on the first time. :)

---

### Post by Spike-X on 2010-04-25
Wow. This is the best music player I've ever used.

I epsecially love the Download Album Cover feature. Saving it as a cover.jpg file in the album folder is perfect, as I can copy the folder straight onto my iPod and have the artwork show up in RockBox.

Thanks everybody for all your hard work!

---

### Post by nothingspecial on 2010-04-26
I want to find a bug!

I`ve been using this for months and everyone else has been finding bugs and getting them fixed .........


........ and my music keeps on playing :P

---

### Post by anonbeat on 2010-04-26
> **nothingspecial said:**
> I want to find a bug!

I`ve been using this for months and everyone else has been finding bugs and getting them fixed .........


........ and my music keeps on playing :P

Thats too bad!! the developer should be fired now!!

---

### Post by BoredOutOfMyMind on 2010-04-28
2 questions-

1- Can there be a date stamp for record function.   Currently the program overwrites what ever is saved in the folder each time record is pressed. 

2- Gstreamer buffers are preventing login to some stations.  The buffering stops at 2-5% and never increase.  How can I tell my system to allowcate more cache?

---

### Post by nothingspecial on 2010-04-28
> **BoredOutOfMyMind said:**
> 2 questions-

1- Can there be a date stamp for record function.   Currently the program overwrites what ever is saved in the folder each time record is pressed. 

2- Gstreamer buffers are preventing login to some stations.  The buffering stops at 2-5% and never increase.  How can I tell my system to allowcate more cache?

Ask [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=9182547#post9182547")

This is a discussion thread.

That is the feature request/bug reporting thread.

Guayadeque is cool, isn`t it.

---

### Post by koleoptero on 2010-04-28
Guayadeque should become the default for xubuntu. It's much ligher than exaile and has less gnome dependencies (at least as far as I'm aware of).

---

### Post by nothingspecial on 2010-04-28
> **koleoptero said:**
> Guayadeque should become the default for xubuntu. It's much ligher than exaile and has less gnome dependencies (at least as far as I'm aware of).

It should be the default linux music player in my opinion.

cmus > mpd > guayadeque

---

### Post by koleoptero on 2010-04-28
> **nothingspecial said:**
> It should be the default linux music player in my opinion.

cmus > mpd > guayadeque

Well it's got to start from somewhere :D

---

### Post by benmoran on 2010-05-04
Let me start by also saying this is the best music player i've ever used. It's hard to find any complaints. 

I understand the meaning and the reasoning behind the name, but I think its too hard for the international community to remember or pronounce. I think if the name was a bit simpler and catchy, the popularity of this player would skyrocket.

---

### Post by Pifilatakanemu on 2010-05-04
I think the name will not hinder the player from getting famous one day.


if you don't know how to pronounce it -who cares? I don't mean this in a negative way. As with other names they get adopted in every language, which is only fair in my opinion. Not everything has to be universally applicable.

there are already a couple of people calling it G-Que -which sounds quite ugly in my opinion but could get used more often if people think the name is to long.

just think about the Eyjafjallajökull - a "strange" name can be promoting, too! :D



btw: you're not the first with this concern and probably not the last ;)

---

### Post by koleoptero on 2010-05-04
is guayadeque supposed to be able of gapless playback or is it a side-effect of being properly written? Cause I don't remember seeing it advertised anywhere. Nevertheless, I just noticed I have flawless gapless playback with it.

P.S.: I love the name.

---

### Post by scouser73 on 2010-05-04
I've just installed Guayadeque on Lucid and I'm pleased that editing song names & titles now sticks to how I wish it to appear; meaning that anything in capital letters only can now appear as **Eagles - Desperado**, as opposed to **EAGLES - DESPERADO**

A fantastic music player, having used Rhythmbox I thought I would have had to accept that tagging couldn't be done properly but now it can.  Thank you.

---

### Post by cgroza on 2010-05-04
I tried this player... It has big chances, keep this work going :popcorn::popcorn:

---

### Post by Spike-X on 2010-05-05
> **koleoptero said:**
> is guayadeque supposed to be able of gapless playback or is it a side-effect of being properly written? Cause I don't remember seeing it advertised anywhere. Nevertheless, I just noticed I have flawless gapless playback with it.

P.S.: I love the name.
There are players without gapless playback?

How quaint.

---

### Post by Carlos C on 2010-05-06
> **benmoran said:**
> Let me start by also saying this is the best music player i've ever used. It's hard to find any complaints. 

I understand the meaning and the reasoning behind the name, but I think its too hard for the international community to remember or pronounce. I think if the name was a bit simpler and catchy, the popularity of this player would skyrocket.

Here you can listen google saying "Guayadeque"

[http://translate.google.cl/translate_t?hl=&ie=UTF-8&text=guayadeque&sl=en&tl=es#](http://translate.google.cl/translate_t?hl=&ie=UTF-8&text=guayadeque&sl=en&tl=es#)

---

### Post by kio_http on 2010-05-06
Prefer Amarok! 

Sorry for the kaffeine overlap in the picture. Supports the same stuff and more.

---

### Post by nothingspecial on 2010-05-06
That just sounds wrong if I try to say it in my accent.

I like the name, but I pronounce 

guy - a - deck

guy (as in Fauwkes)

a (the middle letter of cat)

deck (the floor of a boat)

I know it`s wrong, it just sounds better in broad Mancunian....

---

### Post by nothingspecial on 2010-05-06
> **kio_http said:**
> Prefer Amarok! 

Sorry for the kaffeine overlap in the picture. Supports the same stuff and more.

But this isn`t even beta yet ;)

---

### Post by AnneTanne on 2010-05-07
While browsing the internet looking for some ideas for a hiking-holiday on Gran Canaria ;), I accidently came accross this thread.  A Linux Music player named after a 'Barranca' on a Canarian Island, I really have to check that out!
I can't wait to be at my own computer to try it...

Unfortunatily, I'm not made of the geeky stuff, and it is already years ago (when I was using SuSE) that I've compiled something from source.
Do this instructions also apply for 10.04 Lucid?

> **nothingspecial said:**
> (...)
To install the latest version on 9.10 Karmic open up a terminal and type


```

 sudo apt-get install subversion build-essential cmake gstreamer0.10-plugins-good gstreamer0.10-plugins-base libwxgtk2.8-dev libtagc0-dev libsqlite3-dev libcurl4-openssl-dev libdbus-1-dev libgstreamer0.10-dev libflac-dev
```
```
svn co http://guayadeque.svn.sourceforge.net/svnroot/guayadeque/Trunk guayadeque
```   ```
cd guayadeque/
```
 ```
./build
```
 ```
sudo make install
```



---

### Post by nothingspecial on 2010-05-07
I am a big fan of the smart playlist last fm thingy.

So I kicked off with Depeche Mode

then I got The Cure, Jimmy Eat World and Good Charlotte.

Ok so far.

Then I got Johnny Cash??? :-k

Since then I`ve had Waylon Jennings, Willie Nelson, The Dixie Chicks, Lucinda Williams, Ryan Adams and Nickle Creek wtf

Must be something to do with that Nine Inch Nails cover or something.

I`m not feeling very Country today.

But as usual I`m going with it.

---

### Post by nothingspecial on 2010-05-07
But I have just drawn the line at Kenny Rogers.

---

### Post by nothingspecial on 2010-05-07
> **AnneTanne said:**
> While browsing the internet looking for some ideas for a hiking-holiday on Gran Canaria ;), I accidently came accross this thread.  A Linux Music player named after a 'Barranca' on a Canarian Island, I really have to check that out!
I can't wait to be at my own computer to try it...

Unfortunatily, I'm not made of the geeky stuff, and it is already years ago (when I was using SuSE) that I've compiled something from source.
Do this instructions also apply for 10.04 Lucid?

Yep.

---

### Post by Confuzius on 2010-05-07
I installed from SVN and used "checkinstall" instead of "make install" there was a slight hickup where my cpu usage was maxed and my system ground to a halt while populating the library but other than that it looks nice.

I found the default crossfade length to be too long, especially when skipping though a playlist just to see how everything works, but hey, that's why there's an option to change it.  I'm normally a Rhythmbox guy, but I'll stick with this for a while to see how I like it.

---

### Post by AnneTanne on 2010-05-07
Just installed the player, and for some reason it presented me with a pleasant surprise.
I recently discovered the work 'Déploration sur la mort d'Ockegem' by Josquin Desprez.  I knew I had one version of that work, from a compilation-CD with early music.

So I started Guayadeque for the first time, and let it scan my library.
And guess... on the first and third position in my library list, I found versions of this work... but not the one I knew I had already!

Isn't there another Linux player stating it lets you 'rediscover your music' ;)? Well, certainly Guayadeque does!

Ann

---

### Post by Rasa1111 on 2010-05-08
> **AnneTanne said:**
> Just installed the player, and for some reason it presented me with a pleasant surprise.
I recently discovered the work 'Déploration sur la mort d'Ockegem' by Josquin Desprez.  I knew I had one version of that work, from a compilation-CD with early music.

So I started Guayadeque for the first time, and let it scan my library.
And guess... on the first and third position in my library list, I found versions of this work... but not the one I knew I had already!

Isn't there another Linux player stating it lets you 'rediscover your music' ;)? Well, certainly Guayadeque does!

Ann

So I can install this in Lucid? 
Thanks anon, looks great man!! :KS

---

### Post by nothingspecial on 2010-05-08
> **Rasa1111 said:**
> So I can install this in Lucid? 
Thanks anon, looks great man!! :KS

Yes you can. The instructions at the beginning apply.

Going to edit the 1st post now to say lucid aswell.

---

### Post by Rasa1111 on 2010-05-08
> **nothingspecial said:**
> Yes you can. The instructions at the beginning apply.

Going to edit the 1st post now to say lucid aswell.

Great! thank you!
building now. :) :KS +1

edit: Got it, Adding library now. 
looks great!! got it running now to...
and wow!  Great job!! Niice work!!

Praises! <3

---

### Post by Rasa1111 on 2010-05-09
Just had to post once more to give extra thanks to the creator(s)~
This music player is amazing! 

 I have used pretty much all of them available for Linux/Ubuntu..
and I can honestly say i have not found a better one! 

 Very impressive! and exactly what I wanted/needed! 

Seeing things like this makes people like me want to get into programming. lol

 Awesome job! Thanks a ton. :KS +11  <3

I would, and am recommending this to everyone i know who also uses a real OS. lol :p  :)

 Praises*

---

### Post by Luke has no name on 2010-05-10
Could you add a "No label" label for tracks that have no label? When I'm trying to sort my library into several separate labels, it's tough to do without this function.

---

### Post by BULLIT22 on 2010-05-15
Love the Player. It's Awesome and Thanks. I want to know if you could add support for Samba Shares? I think this would be a great Idea. Saves peeople from setting up Multiple sharing apps. I would like to get away from using DAAP for all my pc's when my Samba shares are always there. Anyway, Thanks.

---

### Post by scouser73 on 2010-05-15
Hi **Luke has no name** & **BULLIT22**, you can post your requests [[COLOR="Red"]**Here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811") which will help anonbeat (the developer of Guayadeque) from having to look in multiple threads.  Thanks.

---

### Post by BULLIT22 on 2010-05-16
Got it Thanks.

---

### Post by MaloS on 2010-05-22
Stumbled across and got the player in a blink.  Having come from Foobar2000, been searching for the player to fill in the lightweight slot with good library management, and this one is perfect so far.

Many thanks, highly recommended especially for people who just came over from foobar2000.

---

### Post by VastOne on 2010-05-22
> **MaloS said:**
> Stumbled across and got the player in a blink.  Having come from Foobar2000, been searching for the player to fill in the lightweight slot with good library management, and this one is perfect so far.

Many thanks, highly recommended especially for people who just came over from foobar2000.

This is the kind of post I look forward to seeing.  :guitar:

Welcome MaloS and whatever you see as improvement post it here or at the idea torrent.

---

### Post by quadrispro on 2010-05-28
Accepted in Debian:

[http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html](http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html)

Guayadeque will be available in Ubuntu from the next 10.10.

---

### Post by SushiR on 2010-05-28
> **quadrispro said:**
> Accepted in Debian:

[http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html](http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html)

Guayadeque will be available in Ubuntu from the next 10.10.

Wow, good news!

---

### Post by nothingspecial on 2010-05-28
Excellent.

---

### Post by VastOne on 2010-05-28
> **quadrispro said:**
> Accepted in Debian:

[http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html](http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html)

Guayadeque will be available in Ubuntu from the next 10.10.

Fantastic news!  :guitar:

---

### Post by northwestuntu on 2010-05-28
> **quadrispro said:**
> Accepted in Debian:

[http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html](http://packages.qa.debian.org/g/guayadeque/news/20100528T170224Z.html)

Guayadeque will be available in Ubuntu from the next 10.10.

alright
:guitar:

---

### Post by deeds on 2010-05-30
i've tried rhytmbox, quodlibet and gmusicbrowser. so far guayadeque is the most satisfying player 4 me, i'll stick to it :) thanks, great job :guitar:

i hope the next guayadeque [COLOR="Red"]**support time tag lyric**[/COLOR] :KS

---

### Post by killabee44 on 2010-05-30
Anonbeat,

I really like your player. Thanks for such a great program...

I have a couple of requests/questions...

When you are hovering the mouse over the edges to resize the window, it's very difficult to do so. The area to resize is too small. 

Shoutcast radio: Is it working? I did a search for a radio station that I know is there because I listen to it regularly on other players. I received no input or results at all.
Is the search working? Can you add some sort of status bar that will tell us that it's searching or updating the radio stations?

Also, I have a .pls file for a shoutcast station. I can stream it fine with VLC. Would it be possible to import it to Guayadeque? Or better yet to make it a default file type for your program. 

Thanks.

---

### Post by nothingspecial on 2010-05-30
> **killabee44 said:**
> Anonbeat,

I really like your player. Thanks for such a great program...

I have a couple of requests/questions...

When you are hovering the mouse over the edges to resize the window, it's very difficult to do so. The area to resize is too small. 

Shoutcast radio: Is it working? I did a search for a radio station that I know is there because I listen to it regularly on other players. I received no input or results at all.
Is the search working? Can you add some sort of status bar that will tell us that it's searching or updating the radio stations?

Also, I have a .pls file for a shoutcast station. I can stream it fine with VLC. Would it be possible to import it to Guayadeque? Or better yet to make it a default file type for your program. 

Thanks.

Bugs and feature requests should go [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

Welcome aboard :)

---

### Post by killabee44 on 2010-05-30
> **nothingspecial said:**
> Bugs and feature requests should go [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1380811")

Welcome aboard :)

Sorry about that.. completely missed that. Never mind though, the software worked fine.

It looks like the main problem for me was that I installed from the ppa, and the dependencies did not get installed for some reason. 

I then went to the first post in this thread and installed:

 ```
sudo apt-get install subversion build-essential cmake gstreamer0.10-plugins-good gstreamer0.10-plugins-base libwxgtk2.8-dev libtagc0-dev libsqlite3-dev libcurl4-openssl-dev libdbus-1-dev libgstreamer0.10-dev libflac-dev
```

so now it works properly. I will post other minor issues at the link you provided.

---

### Post by ivanovnegro on 2010-05-31
Is guayadeque supposed to scobble to Last FM when I listen to radio stations? If so I know that the artist information has to be right at the radio station.

---

### Post by ivanovnegro on 2010-05-31
Sorry Im not right here.

---

### Post by nothingspecial on 2010-05-31
> **ivanovnegro said:**
> Sorry Im not right here.

Thanks for putting your question in the correct place.

This thread is for discussing guayadeque.

---

### Post by JPorter on 2010-06-13
I'm continually amazed by how fast this player is at making update/rescan changes to its library.  I moved about 5,000 tracks from a series of subfolders into a main "Singles" folder, and went to rescan the library to get the updated locations.  

It was near-instantaneous.  It wasn't, "oh wow, that scanned in just a few moments, that was quick," that's what I was expecting in the best case.  No, this was, "wait, did it do anything? I didn't see it respond at all... oh, damn, it already updated everything? wait, really? whoa."  Very impressive.

---

### Post by sasaenator on 2010-06-15
OK,people,I like this player very much.For a long time I couldn´t find a player on Ubuntu that suits my needs.Great work!I have just one question,how can I change a theme,color layout,etc.?Thanx!7

---

### Post by ivanovnegro on 2010-06-15
> **sasaenator said:**
> OK,people,I like this player very much.For a long time I couldn´t find a player on Ubuntu that suits my needs.Great work!I have just one question,how can I change a theme,color layout,etc.?Thanx!7

Good decision to use guayadeque:p. Guayadeque doesnt have layouts or themes like winamp or Songbird, it uses the system colors of your theme in Ubuntu. But you can change the layout if you want with drag the different browsers like library or lastFM panel to the place you want with the mouse and save it with "view"-"save layout".
But if you have more questions or feature requests use this link:  [http://ubuntuforums.org/showthread.php?t=1380811&highlight=guayadeque](http://ubuntuforums.org/showthread.php?t=1380811&highlight=guayadeque). There you will find nice help of the developer and so on.

---

### Post by sasaenator on 2010-06-16
Thank you!:):guitar:

---

### Post by hydrotemplar on 2010-07-01
Is there a way to stack the controls differently to get rid of the left pane?  (ie have the controls on top of the music list like Rhythmbox)  I've got a lot of wasted space on the left, and I'm restricted on space horizontally.

Thanks,
David

---

### Post by Pifilatakanemu on 2010-07-01
you should ask in the other thread (check my signature) or open an idea in the idea torrent.

this is a "general discussion" thread, the developer is more present in the support thread.

---

### Post by anonbeat on 2010-07-01
> **hydrotemplar said:**
> Is there a way to stack the controls differently to get rid of the left pane?  (ie have the controls on top of the music list like Rhythmbox)  I've got a lot of wasted space on the left, and I'm restricted on space horizontally.

Thanks,
David

Right now you cant not rearrange the controls or the current playing album art. You can move around all the other windows. For example look at the attached image.
[IMG]https://sourceforge.net/apps/gallery/guayadeque/main.php?g2_view=core.DownloadItem&g2_itemId=162&g2_serialNumber=1[/IMG]

Thanks for your interest

---

### Post by gemmakaru on 2010-07-01
I just remember my favourite songs and play them in my head.  Sometimes I like to sing along with them too if no one is around to hear me.

---

### Post by Sale on 2010-07-02
Hi,

As I said earlier in this thread, I enjoy using guayadeque very much. Great work, Anon :)

Anyway...I'd enjoy it even more if I could turn the crossfader completely off. Can it be done?

TIA

---

### Post by anonbeat on 2010-07-02
> **Sale said:**
> Hi,

As I said earlier in this thread, I enjoy using guayadeque very much. Great work, Anon :)

Anyway...I'd enjoy it even more if I could turn the crossfader completely off. Can it be done?

TIA

What is the problem when you set the fade out time to 0 ?

Thanks

---

### Post by Sale on 2010-07-02
> **anonbeat said:**
> What is the problem when you set the fade out time to 0 ?

Thanks

If I do that, I have, effectively, a gap between the songs set to 0.

I'd like to have a gap between songs and than, if I so choose, set it to 0 or make some other combination of crossfader options.

---

### Post by anonbeat on 2010-07-02
> **Sale said:**
> If I do that, I have, effectively, a gap between the songs set to 0.

I'd like to have a gap between songs and than, if I so choose, set it to 0 or make some other combination of crossfader options.

If you set the fadeout to 0 then the player acts as how it was before. Once one track finish the next starts inmediatelly.
There is no option to add a gap between tracks. Sorry.

Thanks for your help

---

### Post by Sale on 2010-07-02
> **anonbeat said:**
> There is no option to add a gap between tracks. Sorry.
I know ;) I just think there should be.
> **anonbeat said:**
> Thanks for your help

No problem :) Keep up the great work.

---

### Post by hydrotemplar on 2010-07-02
anonbeat:

Thanks, that's just what I needed!  I didn't realize you could click and drag things around.  It would be nice to get rid of the album cover, but my horizontal space is significantly more important than vertical, so this solves what I needed!

Great player by the way, I've been really happy with what I've seen so far!

---

### Post by Penguin Guy on 2010-07-07
Looks like this is making it into Maverick: [https://launchpad.net/ubuntu/+source/guayadeque/](https://launchpad.net/ubuntu/+source/guayadeque/)

---

### Post by VastOne on 2010-07-07
> **Penguin Guy said:**
> Looks like this is making it into Maverick: [https://launchpad.net/ubuntu/+source/guayadeque/](https://launchpad.net/ubuntu/+source/guayadeque/)

Have already installed it from Ubuntu Software Center on Maverick.

Worked perfectly

---

### Post by Pifilatakanemu on 2010-07-07
This is GREAT news!!!!


Thanks once again for all the good work you're doing, anonbeat!!

---

### Post by discord on 2010-07-09
I keep most of my music on an external USB drive. Whenever I load Guayadeque with the drive unattached, it starts eating resources like crazy and hangs, even my system. This should be easy to reproduce, I'm running 0.2.5

---

### Post by Pifilatakanemu on 2010-07-09
> **discord said:**
> I keep most of my music on an external USB drive. Whenever I load Guayadeque with the drive unattached, it starts eating resources like crazy and hangs, even my system. This should be easy to reproduce, I'm running 0.2.5

You should deactivate the option "Update library on start". This will solve your problem.

---

### Post by surja on 2010-07-10
is there an option to just play songs from a single album folder without adding it to the library?
Btw this is such an awesome player! I said goodbye to Amarok after I started using this.

---

### Post by VastOne on 2010-07-10
> **surja said:**
> is there an option to just play songs from a single album folder without adding it to the library?
Btw this is such an awesome player! I said goodbye to Amarok after I started using this.

From the Files Tab you can look at any files anywhere and play them without them being in the library.

---

### Post by Mattevt on 2010-07-11
Oh man! The auto playlist is spot on! 

I've been getting frustrated trying to find a music player after Songbird dropped Linux, but I really like this! Bravo.

The only issue for me so far is the equalizer is pretty bad (at least the presets are).

---

### Post by VastOne on 2010-07-11
> **Mattevt said:**
> Oh man! The auto playlist is spot on! 

I've been getting frustrated trying to find a music player after Songbird dropped Linux, but I really like this! Bravo.

The only issue for me so far is the equalizer is pretty bad (at least the presets are).

For equalizers, there is nothing better than the system wide PulseAudio Equalizer, info and setup instructions [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1308838"),  and there is a ppa for easy install.

I have used it for several months, it is very robust and creates incredible environments. I have since turned off the one in G-Que

---

### Post by Mattevt on 2010-07-11
> **VastOne said:**
> For equalizers, there is nothing better than the system wide PulseAudio Equalizer, info and setup instructions [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1308838"),  and there is a ppa for easy install.

I have used it for several months, it is very robust and creates incredible environments. I have since turned off the one in G-Que

Great info, thank you!

edit: I've been using it for about 90 seconds and I'm already very impressed. Thanks again for the advice!

---

### Post by SunnyRabbiera on 2010-07-11
> **arnab_das said:**
> looks good. but i think i'll stick to songbird.

Until now that songbird screwed the linux users over

---

### Post by VastOne on 2010-07-11
> **SunnyRabbiera said:**
> Until now that songbird screwed the linux users over

Ye speak thy truth, eloquently...

---

### Post by apocalypse80 on 2010-07-21
I'll post this here in case anyone is interested.

I figured out how to replace the guayadeque tray icon.
So now I have something that looks like this;

[img]http://ubuntuforums.org/attachment.php?attachmentid=164159&stc=1&d=1279737162[/img]

It's not really straightforward, since it has a folder full of images but they aren't used, instead it uses hex dumps of those png files.

You need:
a) the guayadeque svn source and the instructions to build it; [http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)
b) some replacement icon, this one is pretty nice: [http://ubuntuforums.org/showpost.php?p=9581388&postcount=3722](http://ubuntuforums.org/showpost.php?p=9581388&postcount=3722)
c) assuming you have transparency issues, a copy of your panel's background
d) my script that does the format conversion

Process:
- Open the icon in gimp, resize it (we need a 24x24 icon) and save it as a png (optionally: put your panel's background as the background of the icon)
- Use the script to convert the png image to a hex dump with the right format 
```
./png2gque.pl image.png > text.txt
```
- open the text file and delete the final comma, then open the file "guayadeque/src/images/guayadeque_taskbar.h" and replace the hex numbers in it with the hex numbers you just created
- compile and install quayadeque

Yes, it's pretty convoluted, but it will do until the player gets a customizable icon option.

---

### Post by a02dami on 2010-07-26
Hi @ all!! :D 

I love this player and it is fantastic!! Very great!! But I'd like to know if there is a possibility that Guayadeque in future will have the option to rename and rebuilt the music collection (I mean the folders and the name file) using the info on the tag.. such as iTunes or Banshee.

I make an example:

i have an mp3 of U2, where on Guayadeque is displayed the Album (Ruttle And Hum), the title (Desire) and the number of track (03)

but on nautilis there is the folder "U2", inside there is the folder album "Unknown album", and into there is the file "desire.mp3"

How can I make the structure like tag info? => U2 -> Ruttle And Hum -> 03. Desire.mp3

Thanks a lot for any reply!! Sorry for my bad english :D

---

### Post by Pifilatakanemu on 2010-07-26
I'd recommend Picard for this purpose.

It's perfect for such tasks!

---

### Post by oldsoundguy on 2010-07-26
REMOVED by poster.

---

### Post by frombenny on 2010-07-27
To [a02dami]("http://ubuntuforums.org/member.php?u=1068013")

You can copy what you want. In the library select one or more songs (shift + arrows for example) and right clic on them. You'll have a "copy to" option. Select a destination and it's done.

If you want other options than the default ones, go to "Library/preferences/Copy to" and define the way you want them to be copied.

Sorry for my english too because I'm French.

---

### Post by a02dami on 2010-07-27
> **frombenny said:**
> To [a02dami]("http://ubuntuforums.org/member.php?u=1068013")

You can copy what you want. In the library select one or more songs (shift + arrows for example) and right clic on them. You'll have a "copy to" option. Select a destination and it's done.

If you want other options than the default ones, go to "Library/preferences/Copy to" and define the way you want them to be copied.

Sorry for my english too because I'm French.

WOOOOWWW Great!! :popcorn: Thanks a lot! This is another BIG point for Guayadeque !!

---

### Post by mamamia88 on 2010-07-27
seems cool but i like rhythmbox layout better

---

### Post by ivanovnegro on 2010-07-27
> **mamamia88 said:**
> seems cool but i like rhythmbox layout better

Its your personal taste but I prefer functionality and performance and after using g-deque for a long time I really like the interface.

---

### Post by Spike-X on 2010-07-27
> **ivanovnegro said:**
> Its your personal taste but I prefer functionality and performance and after using g-deque for a long time I really like the interface.
I just want to reiterate that Guayadeque is, hands-down, THE best music player I've ever used. 

Just add CD ripping support and it would be perfect!

---

### Post by mamamia88 on 2010-07-27
is there a way to stop it from reinstating deleted tabs with every restart?

---

### Post by ivanovnegro on 2010-07-27
> **mamamia88 said:**
> is there a way to stop it from reinstating deleted tabs with every restart?

Yes, save your layout in "views"-"save layout" and next time the deleted tabs wont appear again.

---

### Post by mamamia88 on 2010-07-27
allright thanks.  might use it from time to time.  i like how i can have files right next to the lyrics tab.  also is it just me or does old song continue to play slightly after selecting next song?  kind of annoying

---

### Post by Spike-X on 2010-07-27
> **Spike-X said:**
> I just want to reiterate that Guayadeque is, hands-down, THE best music player I've ever used. 

Just add CD ripping support and it would be perfect!
Oh, and Watch Folders. kthx!

---

### Post by Spike-X on 2010-07-27
> **mamamia88 said:**
> allright thanks.  might use it from time to time.  i like how i can have files right next to the lyrics tab.  also is it just me or does old song continue to play slightly after selecting next song?  kind of annoying

That's the cross-fader. Just turn it off (or adjust it) in Preferences.

---

### Post by ivanovnegro on 2010-07-27
> **mamamia88 said:**
> allright thanks.  might use it from time to time.  i like how i can have files right next to the lyrics tab.  also is it just me or does old song continue to play slightly after selecting next song?  kind of annoying

Yes thats right, its the crossfading engine. You can change it in preferences "crossfader".

---

### Post by mamamia88 on 2010-07-27
> **ivanovnegro said:**
> Yes thats right, its the crossfading engine. You can change it in preferences "crossfader".

allright thanks again

---

### Post by ivanovnegro on 2010-07-28
> **VastOne said:**
> For equalizers, there is nothing better than the system wide PulseAudio Equalizer, info and setup instructions [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1308838"),  and there is a ppa for easy install.

I have used it for several months, it is very robust and creates incredible environments. I have since turned off the one in G-Que

Oh it rocks really!!! I use it now about 2 days and it works so great. Now g-deque is a music bomb on my machine:p.

---

### Post by a02dami on 2010-07-31
Hi to all, i have to report a bug .. i don't know if this is the right place..

Situation:
I have many songs without "year" tag .. so i selected all of them and create a new static playlist called "without year"

BUT when I go in playlist and I click on the playlist "without year", Guayadeque turn off quickly
Now, also, I can't remove the playlist because if I make right click.. Guayadeque turn off again

:( :( is it a bug?!

Do u know how to remove wrong playlist from player? I tryed to go in /.guayadeque .. but I don't know which is the file where are stored playlist

THANKS TO ALL and have a nice WeekEnd :D - sorry for my bad language - 
Guayadeque remains the BEST player :) :)

---

### Post by VastOne on 2010-07-31
> **a02dami said:**
> Hi to all, i have to report a bug .. i don't know if this is the right place..

Situation:
I have many songs without "year" tag .. so i selected all of them and create a new static playlist called "without year"

BUT when I go in playlist and I click on the playlist "without year", Guayadeque turn off quickly
Now, also, I can't remove the playlist because if I make right click.. Guayadeque turn off again

:( :( is it a bug?!

Do u know how to remove wrong playlist from player? I tryed to go in /.guayadeque .. but I don't know which is the file where are stored playlist

THANKS TO ALL and have a nice WeekEnd :D - sorry for my bad language - 
Guayadeque remains the BEST player :) :)


Hi

The correct place for bug reporting is 
[_[COLOR="SeaGreen"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by Muskegman on 2010-08-03
This is exactly what i have been looking for! Its Great and handles my large song database brilliantly. A big thankyou to everyone involved :D

I was using songbird until they stopped supporting linux and rythmbox decided to remove all my songlist for some strange reason.

This is exactly what we needed for ubuntu Thanks again:D

---

### Post by VastOne on 2010-08-03
> **Muskegman said:**
> This is exactly what i have been looking for! Its Great and handles my large song database brilliantly. A big thankyou to everyone involved :D

I was using songbird until they stopped supporting linux and rythmbox decided to remove all my songlist for some strange reason.

This is exactly what we needed for ubuntu Thanks again:D


Welcome!

There is a monster thread of support and howto's over 
[_[COLOR="SeaGreen"][COLOR="Red"][U]here_[/COLOR][/COLOR][/U]]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by Rubicon421 on 2010-08-03
How do you set it so that tracks are added to the playlist by track # when you add a whole folder or album at once? I made sure random is not on. Sometimes it seems like it adds tracks alphabetically by the tags, and other times by the track names but not ever by the track numbers like they should be for the album.

---

### Post by ivanovnegro on 2010-08-03
> **Rubicon421 said:**
> How do you set it so that tracks are added to the playlist by track # when you add a whole folder or album at once? I made sure random is not on. Sometimes it seems like it adds tracks alphabetically by the tags, and other times by the track names but not ever by the track numbers like they should be for the album.

If you want help, better post it [here]("http://ubuntuforums.org/showthread.php?t=1380811"), like VastOne said it before, in the monster thread of support and howto's.

---

### Post by VastOne on 2010-08-03
Conky G-Que users - [_[COLOR="Red"]check this out[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=9668167")

The PPA is in, and I have loaded this via Option one.

Once it installs

You have to run 

```
conky -c /usr/share/conkyguayadeque/example/conkyrc &
```

to start the session of conky with the script.

Of course from there you can manipulate it the way you want.

From here and now on though, we need to keep the conky issues we have either [[COLOR="Red"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=9668167") where we got the script from for installation problems or from [_[COLOR="Lime"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865") which is a massive Conky help thread or you can ask questions about it here.

Remember, once anon gets back he will have to add some calls from G-Que to dbus that will add even more options..

And along with that, this is development too so be patient as it evolves.  And please post anything you find or do that helps this.

One other thing, while at Conky Guayadeque Python Script site, give a great BIG thanks to Kaivalagi who 4 days ago did not know G-que was "a major player". He did this in a short period of time after he initially said it was too much to ask of him because of time restraints....

---

### Post by Spike-X on 2010-08-04
> **VastOne said:**
> Conky G-Que users - [_[COLOR="Red"]check this out[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=9668167")

Excellent! I've been looking for something like this.

> **VastOne said:**
> One other thing, while at Conky Guayadeque Python Script site, give a great BIG thanks to Kaivalagi who 4 days ago did not know G-que was "a major player". He did this in a short period of time after he initially said it was too much to ask of him because of time restraints....

Well done, that man!

---

### Post by ATA0311 on 2010-08-13
Can anyone direct me on how to uninstall Guayadeque from Ubuntu 10.04?

---

### Post by nothingspecial on 2010-08-16
> **ATA0311 said:**
> Can anyone direct me on how to uninstall Guayadeque from Ubuntu 10.04?
```

cd guayadeque
sudo make uninstall
```

---

### Post by mullens101 on 2010-08-19
Hi, been using Guayadeque (What's the proper pronunciation and where'd the name come from?) for a week or so now, in general I'm really happy with it, thanks a ton!  Here are 2 things I believe are missing:

1.  Sorting of "static" playlists.  Yes, I know what "static" means but really, you should be able to sort any playlist if you want/need to.

2.  The ability to easily add songs from the library to any static playlist. (I see the "save to playlist' on right click which would probably be OK if it was just right click-hover on SaveToPlaylist-submenu of available playlists pops out.  The small popup window seems like more steps/work than is necessary.)

---

### Post by VastOne on 2010-08-19
> **mullens101 said:**
> Hi, been using Guayadeque (What's the proper pronunciation and where'd the name come from?) for a week or so now, in general I'm really happy with it, thanks a ton!  Here are 2 things I believe are missing:

1.  Sorting of "static" playlists.  Yes, I know what "static" means but really, you should be able to sort any playlist if you want/need to.

2.  The ability to easily add songs from the library to any static playlist. (I see the "save to playlist' on right click which would probably be OK if it was just right click-hover on SaveToPlaylist-submenu of available playlists pops out.  The small popup window seems like more steps/work than is necessary.)

[[COLOR="Lime"]_Here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=9740005#post9740005")  is where to get these answers from.

---

### Post by Austin25 on 2010-08-20
Don't we have enough music players?

---

### Post by VastOne on 2010-08-20
> **Austin25 said:**
> Don't we have enough music players?

Yes, but only one that is worth keeping...

Is that a constructive question? Or are you taking a poll?

---

### Post by ivanovnegro on 2010-08-20
> **Austin25 said:**
> Don't we have enough music players?

Maybe but why not have a variety of music players like Linux distributions too for everyone with different needs and tastes?
And one thing, this player is really good, just try it and post again your opinion if you want about g-deque. Would be happy to hear the opinion of people that are using another player. 
And second, this one is for me THE player.
Personal taste and preferences.

Regards

---

### Post by Spike-X on 2010-08-22
> **Austin25 said:**
> Don't we have enough music players?
We do now!

---

### Post by Rinzwind on 2010-08-25
> **Austin25 said:**
> Don't we have enough music players?

NEVER!
We can never have enough open source :=)

---

### Post by Rinzwind on 2010-08-25
> **Spike-X said:**
> I just want to reiterate that Guayadeque is, hands-down, THE best music player I've ever used. 

Just add CD ripping support and it would be perfect!

...and on the fly converting :D 
Let soundconverter hook into Guayadeque and convert on the fly to a preset conversion if the added song is not said preset :D
I want all my music to be ogg :)

---

### Post by Linye on 2010-08-25
> **ivanovnegro said:**
> 
this one is for me THE player.


QFT


Before Guayadeque , I'd only used itunes, WMP and Rhythmbox after the switch. You can imagine how amaze I was after using it. The smart playlist and dynamic playlist were something that I didn't know it could exist. lol

Also, to see how easy I could download album covers and see the lyrics, just awesome.

The only thing that I miss is ipod syncing and that will come someday.

---

### Post by Spike-X on 2010-08-26
> **Rinzwind said:**
> 
I want all my music to be ogg :)

Not if you're converting from MP3 or another lossy codec you don't.

---

### Post by Rinzwind on 2010-08-29
> **Spike-X said:**
> Not if you're converting from MP3 or another lossy codec you don't.
Mostly directly from cd. Sometimes from flac and if downloaded from wav :)



Anon! There is 1 thing that would make Guayadeque even better than it is now: MTP support. I never get that to work with RB and Amarok is kde :+)

---

### Post by PC_load_letter on 2010-08-31
Just updated to 0.2.7 under Karmic, and I'm very impressed w/ the new features. Big thanx to the devs.

---

### Post by ivanovnegro on 2010-08-31
> **PC_load_letter said:**
> Big thanx to the devs.

Its mostly a big one man show of anonbeat.:D
And this app is so amazing in comparison with others and they have for what I know more devs.

---

### Post by PC_load_letter on 2010-08-31
> **ivanovnegro said:**
> Its mostly a big one man show of anonbeat.:D


:shock::shock::shock: Even more impressive! And this is more of a reason to donate to this wonderful project.

---

### Post by ubuntoide on 2010-09-06
hi guys, is there a way to have it run on Maverick?? the 0.27 deb reports an unknown error.. 

Anyway, that's the best player available, dynamic and smart playlist seems to read my thoughts sometimes.. :p

---

### Post by VastOne on 2010-09-06
> **ubuntoide said:**
> hi guys, is there a way to have it run on Maverick?? the 0.27 deb reports an unknown error.. 

Anyway, that's the best player available, dynamic and smart playlist seems to read my thoughts sometimes.. :p

I run it on Maverick, you have to install it from Synaptic or Software Center and that installs 0.2.5 then run the svn process that is described on the first page of the Guayadeque support thread [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1380811")

---

### Post by ubuntoide on 2010-09-07
ok nice, I was looking for a .deb but I understand that have it running now on Maverick is a bit premature.. I'll go with the svn, thank you

---

### Post by jonohull on 2010-09-08
Just here to say thanks for this! Most of the other programs I've used were frankly not that good. Either too resource-intensive or just clunky to use. This is great. I know it goes in another thread, but I voice my support for playing striaght from the library as well.

---

### Post by VastOne on 2010-09-23
Guayadeque now has a [[COLOR="Red"]_wiki_[/COLOR]]("http://guayadeque.wikidot.com")

The wiki is pretty much completed, with the one exception of [_[COLOR="Teal"]this area[/COLOR]_]("http://guayadeque.wikidot.com/managing-playlists-and-filters") on managing playlists and filters.  I do not use either of those but they are very important.  If anyone wants to fill it in feel free to do it or send me the info and I can add it.

I want to thank Camaron1, Sector11, Anonbeat, Garthhh, Mr_Hangman,Ivanonvegro, David Beardsley, bcammo and Rob Elliot for the work and contributions on the [[COLOR="Teal"]_Guayadeque Wiki_[/COLOR]]("http://guayadeque.wikidot.com/").

The Wiki also has a forum there now specifically for Wiki related issues so use it for questions about the Wiki.

Guess you missed all this nothingspecial

---

### Post by nothingspecial on 2010-09-24
I`ve got a lot on at the moment.

Don`t worry, I`m still spreading the word

```
15:54 < glaucous> Anyone know of a good music player which features a good file browser - OR is able to sort
                  artists/songs by directory (in a tree)?
15:55 < nothingspecial> glaucous: try guayadeque
15:56 < glaucous> nothingspecial: Love the name, checking it out, thanks
```

---

### Post by VastOne on 2010-09-24
> **nothingspecial said:**
> I`ve got a lot on at the moment.

Don`t worry, I`m still spreading the word



I have no doubt of that... ;)

---

### Post by khoa on 2010-09-28
instructions add the radio station in Vietnam
  example:radio VInh Long

---

### Post by Rinzwind on 2010-09-28
> **nothingspecial said:**
> I`ve got a lot on at the moment.

Don`t worry, I`m still spreading the word

```
15:54 < glaucous> Anyone know of a good music player which features a good file browser - OR is able to sort
                  artists/songs by directory (in a tree)?
15:55 < nothingspecial> glaucous: try guayadeque
15:56 < glaucous> nothingspecial: Love the name, checking it out, thanks
```


me too!

[http://forum.fok.nl/topic/1533903/2/100](http://forum.fok.nl/topic/1533903/2/100)

Someone asking for a player with support for itunes O-)

---

### Post by Repgahroll on 2010-10-15
Imho, Guayadeque is the best music player to fetch Lyrics besides Songbird.

The most important feature imho is that it can read and save them directly from/to the music file.

Some feature that are much needed imho is the ability to search multiple sources automatically until it finds the lyric, detect incomplete lyrics due copyright restriction and try another source, batch fetch the lyrics for offline use (and also in case someone want to fetch lyrics for his entire album fearing that the sources may now allow fetching in future). Also, fonts options for lyrics display would be useful.

Maybe it would be better to use external plugins to fetch the lyrics, so the community would be able to write better fetchers in python/shellscript using traditional methods and apps like curl, wget, lynx, and the player only takes the output of these scripts. Like scripts that you can run on terminal with something like```
./fetchwikilyric -a Artist Name -s Song Name
```and they return only the lyric.
So pretty much *anyone* would be able to write a lyric fetcher. And note that by using this method, it will always be possible to fetch lyrics from any source.

Other random features are:

The ability to play the library like an playlist. Maybe merge them...

Smooth shutdown. Like amarok 1.4, when you shut down the player the song fade out.

My main concern is the lyrics fetching though.

Thank you. I wish i could join the development, but c++ demands much time, and i'd need to re-learn codeblocks also, because i use netbeans for c/c++ development.

Who cares that Songbird dropped the Linux support when you have billions of better music players emerging from community? Songbird sucks and i don't bet on Nightingale also. The only feature that were better now are outdated and doesn't work very well.

Thanks.

---

### Post by ivanovnegro on 2010-10-15
> **Repgahroll said:**
>  Also, fonts options for lyrics display would be useful.


I know its not the same but if you change your default fonts for applications for example like me to droid sans what I prefer or whatever you prefer there will be a better integration in Guayadeque displaying the lyrics.
For the rest, go to vote on the [IdeaTorrent]("http://sourceforge.net/apps/ideatorrent/guayadeque/").

---

### Post by anonbeat on 2010-10-16
> **Repgahroll said:**
> Imho, Guayadeque is the best music player to fetch Lyrics besides Songbird.

The most important feature imho is that it can read and save them directly from/to the music file.

Some feature that are much needed imho is the ability to search multiple sources automatically until it finds the lyric, detect incomplete lyrics due copyright restriction and try another source, batch fetch the lyrics for offline use (and also in case someone want to fetch lyrics for his entire album fearing that the sources may now allow fetching in future). Also, fonts options for lyrics display would be useful.

Maybe it would be better to use external plugins to fetch the lyrics, so the community would be able to write better fetchers in python/shellscript using traditional methods and apps like curl, wget, lynx, and the player only takes the output of these scripts. Like scripts that you can run on terminal with something like```
./fetchwikilyric -a Artist Name -s Song Name
```and they return only the lyric.
So pretty much *anyone* would be able to write a lyric fetcher. And note that by using this method, it will always be possible to fetch lyrics from any source.

Other random features are:

The ability to play the library like an playlist. Maybe merge them...

Smooth shutdown. Like amarok 1.4, when you shut down the player the song fade out.

My main concern is the lyrics fetching though.

Thank you. I wish i could join the development, but c++ demands much time, and i'd need to re-learn codeblocks also, because i use netbeans for c/c++ development.

Who cares that Songbird dropped the Linux support when you have billions of better music players emerging from community? Songbird sucks and i don't bet on Nightingale also. The only feature that were better now are outdated and doesn't work very well.

Thanks.

> **ivanovnegro said:**
> I know its not the same but if you change your default fonts for applications for example like me to droid sans what I prefer or whatever you prefer there will be a better integration in Guayadeque displaying the lyrics.
For the rest, go to vote on the [IdeaTorrent]("http://sourceforge.net/apps/ideatorrent/guayadeque/").

Once I finish the portable device support I want to work on most voted features and others that even when its not too much voted are interesting and seems not a big change in the program and of course as even it has no impact in the application performance

Thanks for your help

---

### Post by Repgahroll on 2010-10-18
Thanks for your kind reply guys.
Also, I think it would be nice to make a poll here in this topic with the ideas on the IdeaTorrent of Guayadeque, because the votation there isn't very substantial. And few people are going to register on sourceforge just to vote.
Anyways, lyrics fetching is a feature that MUST (imho) be "outsourced", it's not a good idea to keep it an internal feature, as pretty much any lyric fetching method only works for an limited period of time.

Thanks.

---

### Post by ivanovnegro on 2010-10-18
> **Repgahroll said:**
> Thanks for your kind reply guys.
Also, I think it would be nice to make a poll here in this topic with the ideas on the IdeaTorrent of Guayadeque, because the votation there isn't very substantial. And few people are going to register on sourceforge just to vote.
Anyways, lyrics fetching is a feature that MUST (imho) be "outsourced", it's not a good idea to keep it an internal feature, as pretty much any lyric fetching method only works for an limited period of time.

Thanks.

What do you mean with outsourcing the lyric fetching, I thought you was happy with it in G-deque?

---

### Post by Repgahroll on 2010-10-18
> **ivanovnegro said:**
> What do you mean with outsourcing the lyric fetching, I thought you was happy with it in G-deque?
External scripts / programs that Guayadeque call with arguments and they return the lyric. I'm happy with the actual lyric system, however, it's an internal feature, so, only the developers are able to program it, and this kind of feature should be easily programmed by pretty much anyone imho. Lots of people has the knowledge to easily make a shell/python script that uses programs like wget/curl/lynx to get lyrics from pretty much any website. Guadayeque MUST allow them to participate without much effort, so we'll soon have a lyrics fetching system much better than Ultimate (for Amarok, the best nowadays). We would be able even to easily port the Ultimate to Guayadeque.

OFF: I'm impressed on how wxWidgets looks ultimately native on pretty much *every* desktop manager. I think it would perform well on other OSs also. I thought Qt was better, but now i've changed my mind... Qt is more powerfult o'course, but when such kind of "power" (and features) aren't needed, wxWidgets fits perfectly well. And looks much more better.

---

### Post by ivanovnegro on 2010-10-18
> **Repgahroll said:**
> External scripts / programs that Guayadeque call with arguments and they return the lyric. I'm happy with the actual lyric system, however, it's an internal feature, so, only the developers are able to program it, and this kind of feature should be easily programmed by pretty much anyone imho. Lots of people has the knowledge to easily make a shell/python script that uses programs like wget/curl/lynx to get lyrics from pretty much any website. Guadayeque MUST allow them to participate without much effort, so we'll soon have a lyrics fetching system much better than Ultimate (for Amarok, the best nowadays). We would be able even to easily port the Ultimate to Guayadeque.



Now I understand what you wanted to say with the lyric system, dont know, I like it and have no more expectations how it would be better as I dont use the lyric fetching always.
But why not participate, this thing you have to ask the developer Anonbeat but he is the only one.

---

### Post by swirlcore on 2010-10-20
OK. I have been using this player for a while. Everything seems great. I just want to make it look like mediamonkey.

For instance:

I don't want a seperate album tab. I want the album to be displayed under artist name in a tree format (like in mediamonkey and amarok). Is that possible?


I'm just need this thing and I'll be happy.

Also, kudos to the developers. Probably the best media player on Linux at the moment.

Thanks guys.

---

### Post by ivanovnegro on 2010-10-20
> **swirlcore said:**
> OK. I have been using this player for a while. Everything seems great. I just want to make it look like mediamonkey.

For instance:

I don't want a seperate album tab. I want the album to be displayed under artist name in a tree format (like in mediamonkey and amarok). Is that possible?


I'm just need this thing and I'll be happy.

Also, kudos to the developers. Probably the best media player on Linux at the moment.

Thanks guys.

I think that is not possible as this kind of view does not exist in G-deque.

---

### Post by nxmehta on 2010-10-22
Can anyone tell me how to enqueue songs via the command line?  I can't seem to figure it out.

Also, if a song is playing, and I try to play a new song via the command line or via nautilus, it does not play and guayadeque subsequently freezes.  Anyone else seeing this?  It makes playing things via any method other than the library impossible.

I'm running 0.2.7-1227 on Ubuntu 10.04.

---

### Post by anonbeat on 2010-10-22
> **nxmehta said:**
> Can anyone tell me how to enqueue songs via the command line?  I can't seem to figure it out.

Also, if a song is playing, and I try to play a new song via the command line or via nautilus, it does not play and guayadeque subsequently freezes.  Anyone else seeing this?  It makes playing things via any method other than the library impossible.

I'm running 0.2.7-1227 on Ubuntu 10.04.

If you want to enqueue a track to the playlist without interrupt the one playing you can use the mpris interface.
```

dbus-send --print-reply --type=method_call --dest=org.mpris.guayadeque /TrackList org.freedesktop.MediaPlayer.AddTrack string:"Complete_Path_To_enqueued_track" boolean:false

```

if you want to play inmediatelly and clean the current playlist you can change the last **false** to **true**

Thanks for your help

btw: Please I appreciate if you keep support questions in the [guayadeque.org]("http://guayadeque.org") forums.

---

### Post by VastOne on 2010-11-03
Guayadeque Wiki is now a Featured site on Wikidot!

[[COLOR="Blue"]_Here on the Community site at Wikidot!_[/COLOR]]("http://community.wikidot.com/featured:guayadeque")

Guayadeque Wiki in these languages:

English
Espanol
German
Russian
Simplified Chinese

---

### Post by BoredOutOfMyMind on 2010-11-09
New Tray app for Maverick 10.10  panflute-applet

Supports Guayadeque.

---

### Post by VastOne on 2010-11-09
> **BoredOutOfMyMind said:**
> New Tray app for Maverick 10.10  panflute-applet

Supports Guayadeque.

I saw this and checked it out.. It is great that G-Que is supported.

But I am sure grateful for Conky and K's Guayadeque script...

---

### Post by BoredOutOfMyMind on 2010-11-12
> **VastOne said:**
> I saw this and checked it out.. It is great that G-Que is supported.

But I am sure grateful for Conky and K's Guayadeque script...

I had errors at the last Guayadeque update (1342) as with panflute the system thought it was opened.  I removed the app, killing the link and the update worked. 

If only we could get the icon to render correctly in the status bar. 

Until then, I am thankful for the conky script as well.

---

### Post by Rubicon421 on 2010-11-12
Is there any way to make G-que ignore casing of text? I know that's more of a ext file system thing than a problem with G-que but my music library is stored on an NTFS partition. I have a lot of multiple entries for the same band because of upper and lower case differences in words like "of", "the", "a", etc...

I know I could just rename them all but if there is a way to make G-que ignore casing in one step that would be a lot easier than fixing each mp3 tag individually.

---

### Post by VastOne on 2010-11-13
> **Rubicon421 said:**
> Is there any way to make G-que ignore casing of text? I know that's more of a ext file system thing than a problem with G-que but my music library is stored on an NTFS partition. I have a lot of multiple entries for the same band because of upper and lower case differences in words like "of", "the", "a", etc...

I know I could just rename them all but if there is a way to make G-que ignore casing in one step that would be a lot easier than fixing each mp3 tag individually.

This has been requested many many times and has been been promised for future releases but as of now, no...

---

### Post by VastOne on 2010-11-13
> **BoredOutOfMyMind said:**
> I had errors at the last Guayadeque update (1342) as with panflute the system thought it was opened.  I removed the app, killing the link and the update worked. 

If only we could get the icon to render correctly in the status bar. 

Until then, I am thankful for the conky script as well.

I agree...  I get the icon to render correctly by starting another tray app like VLC or Grsync.

---

### Post by ivanovnegro on 2010-11-13
> **VastOne said:**
> I agree...  I get the icon to render correctly by starting another tray app like VLC or Grsync.

Me too. But depends which app you open first in my case. 
Everyday I begin to open the first app, in my case Guayadeque and the icon is in white shape, then I open another application and G-deque has a normal icon and later I open another app what uses the tray and the G-deque icon gets a white line what is more ugly as to be totally white and it will stay this way.
For now its the normality but really it does not look professional.

---

### Post by BoredOutOfMyMind on 2010-11-14
I am having some serious issues with Shoutcast streaming.  It sounds like it is in a $10 AM radio. I tested on multiple streams.   I installed Exaile, and the 128 K streams are crystal clear. :(

---

### Post by koleoptero on 2010-11-14
> **BoredOutOfMyMind said:**
> I am having some serious issues with Shoutcast streaming.  It sounds like it is in a $10 AM radio. I tested on multiple streams.   I installed Exaile, and the 128 K streams are crystal clear. :(

|
|
|
v

> **anonbeat said:**
> btw: Please I appreciate if you keep support questions in the [guayadeque.org]("http://guayadeque.org") forums.

---

### Post by VastOne on 2010-11-16
> **BoredOutOfMyMind said:**
> I am having some serious issues with Shoutcast streaming.  It sounds like it is in a $10 AM radio. I tested on multiple streams.   I installed Exaile, and the 128 K streams are crystal clear. :(

> **koleoptero said:**
> |
|
|
v

BOOMM...  I have seen this same thing on 128 streams and use the PulseAudio Equalizer to correct it with gain settings.

Koleoptero, this thread and many others are available to users for help.  There is a choice for open forums and open sites

---

### Post by BoredOutOfMyMind on 2010-11-16
> **VastOne said:**
> BOOMM...  I have seen this same thing on 128 streams and use the PulseAudio Equalizer to correct it with gain settings.

Koleoptero, this thread and many others are available to users for help.  There is a choice for open forums and open sites

Thanks VastOne, in that Anonbeat has chosen to not offer help here, I choose to install Exaile again. :(

Koleoptero, my postings on Guayadeque.org Forums were censored, or not answered for days.  My s/n there is the same as here.:confused:

---

### Post by VastOne on 2010-11-16
> **BoredOutOfMyMind said:**
> Thanks VastOne, in that Anonbeat has chosen to not offer help here, I choose to install Exaile again. :(

Koleoptero, my postings on Guayadeque.org Forums were censored, or not answered for days.  My s/n there is the same as here.:confused:

I am doing the same thing. I got Exaile to post in Conky the same way and really the only advantage G-Que has over Exaile is the edit capabilities, but EasyTag steps in there.  I used Exaile way before G-Que and it is a comfortable fit.  I also like that it is written in python and that it is open for plugin development.

---

### Post by inigo48 on 2010-11-23
I have a strange problem: I can't turn off the randomise button. so if i start any album it will be randomised, if i press the button again it'll be re-randomised. I have the feeling there is some very simple solution but i cant find it :o

one more thing. the background of the tray icon isnt invisible, can i fix it somehow?

thx in advance

---

### Post by ivanovnegro on 2010-11-23
> **inigo48 said:**
> I have a strange problem: I can't turn off the randomise button. so if i start any album it will be randomised, if i press the button again it'll be re-randomised. I have the feeling there is some very simple solution but i cant find it :o

one more thing. the background of the tray icon isnt invisible, can i fix it somehow?

thx in advance

The invisible icon is a known issue for a long time now, there is no really fix in my opinion, the developer has to fix it, I hope so. There are some existing workarounds but I think at the end they didnt work as well.
The randomize button, I think you are right, once clicked you cannot disable it. You have to populate the playlist again.

---

### Post by inigo48 on 2010-11-23
> **ivanovnegro said:**
> The randomize button, I think you are right, once clicked you cannot disable it. You have to populate the playlist again.

sry i was wrong. i thought that when i start an album from the browser it is randomised(i just saw that it isnt in the order in it should be), but it isnt. it is just played in abc order. so my real problem is that how to play the albums with the real track order.(the randomiser still strange though. i prefer the way how audacious handle it. you can turn it on and off and it doesn't reorder the list)

the icon is strange though, sometimes it is fine then it isnt invisible again. it isnt a big problem though.

---

### Post by ivanovnegro on 2010-11-23
> **inigo48 said:**
> sry i was wrong. i thought that when i start an album from the browser it is randomised(i just saw that it isnt in the order in it should be), but it isnt. it is just played in abc order. so my real problem is that how to play the albums with track order.(the randomiser still strange though. i prefer the way how audacious handle it. you can turn it on and off and it doesn't reorder the list)

the icon is strange though, sometimes it is fine then it isnt invisible again. it isnt a big problem though.

Some people noticed yet that the randomize function is not working well, me included. I agree with you.
The damned icon, its not bothering me as I dont need eyecandy at all but its strange that all apps are working fine on the panel except G-deque, I dont undestand it and some younger players like Clementine (I think its younger) just integrated MPRIS2 and G-deque not. In some apects G-deque has very good features but in others its behind and isolated, just like the development, there is one guy and thats all.

---

### Post by inigo48 on 2010-11-23
> **ivanovnegro said:**
> In some apects G-deque has very good features but in others its behind and isolated, just like the development, there is one guy and thats all.

I find the most potential in this player. I usually don't like these kind of players with media library(rhythmbox, banshee etc), so it is a big thing i really like this one :p I have the feeling, one day this'll be the default audio player in ubuntu :D

do you have any idea how should I play an album from the browser tab(album view) in the correct track order and not in abc order?

---

### Post by ivanovnegro on 2010-11-23
> **inigo48 said:**
> I find the most potential in this player. I usually don't like these kind of players with media library(rhythmbox, banshee etc), so it is a big thing i really like this one :p I have the feeling, one day this'll be the default audio player in ubuntu :D

do you have any idea how should I play an album from the browser tab(album view) in the correct track order and not in abc order?

Yes, go to the pane under the columns and sort by number. Then you will be able to play the tracks in the right order. You can sort it from there how you prefer.

---

### Post by inigo48 on 2010-11-24
> **ivanovnegro said:**
> Yes, go to the pane under the columns and sort by number. Then you will be able to play the tracks in the right order. You can sort it from there how you prefer.

thx, it worked! :P i thought that the library tab and the browser tab are independent.

---

### Post by nixie21 on 2010-12-07
I installed yesterday from the Mint Debian repositories.  Can I install the SVN over it?

Thanks

---

### Post by challapradyumna on 2010-12-20
the player is not minimising to the notification area but into an icon below the start button and it would be nice to integrate it like the amarok and rhythmbox with the volume icon.
i really like the player but my major upset was not minimising to notification area

---

### Post by camaron1 on 2010-12-22
> **challapradyumna said:**
> the player is not minimising to the notification area but into an icon below the start button and it would be nice to integrate it like the amarok and rhythmbox with the volume icon.
i really like the player but my major upset was not minimising to notification area

Integration with sound menu has just been implemented. If you have been building guayadeque from svn then you have to install **libindicate-dev** as new dependenty and rebuild. If you don't know how to build svn follow this link:
[http://guayadeque.org/forums/index.php?p=/page/installing#InstallSVN](http://guayadeque.org/forums/index.php?p=/page/installing#InstallSVN)

---

### Post by cometdog on 2011-01-03
Thanks for this great music player!  It's the first one I have tried that I am completely happy with.

Here's a random thought / suggestion.  I didn't see any mention of this in the thread, but I could have missed it as it's pretty long.  Have you ever considered making some kind of remote control interface for this that could be run on Android?  It would be pretty amazing to have some kind of (slimmed-down?) guayadeque interface that would control the copy of guayadeque running on my desktop computer.  Nice multitouch interface to filter by genre / artist / album / whatever, drag songs over to the playlist with my finger, skip, change volume, etc.

I imagine that would be quite a bit of work, and unfortunately I can't offer to help.  I also don't really know how many people have an android device and would find this useful.  But I couldn't resist making the suggestion.

---

### Post by hyperAura on 2011-05-01
I recently installed Ubuntu 11.04 and guayadeque crashes every single time.. When I try to install it with "sudo apt-get install guayadeque", at some point the installer reports an error and quits..

Has anyone else had this issue?

---

### Post by yooozy on 2011-09-20
I tried it on ubuntu 11.10 it works fine 

it's very flexible but it's kinda like too much at your face for noobs

please contact me I'd like to participate
yooozy1(aaat)gmail.com

---

### Post by nothingspecial on 2011-09-20
You can contact the project here.

[http://guayadeque.org/forums/index.php?p=/wiki/page/home](http://guayadeque.org/forums/index.php?p=/wiki/page/home)

Now I must put this old thread back to bed.

Closed

---

