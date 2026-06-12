---
title: "Rethink Ubuntu's &quot;music management&quot;"
date: 2007-11-12
forum: Ubuntu Brainstorm
---

### Post by pengu on 2007-11-12
[SIZE="4"]It has come to my attention that Ubuntu still lacks a feature complete Audio Program.

I say "Audio Program" as music players have gone through a recent (r)evolution. With the rise of portable audio players, so called "mp3 players", especially Apple's Ipod/Itunes, people have moved from wanting there computers to simply play their music files, to wanting something more.

The general public,  including myself, now expects their computers to not only play there music, but also to be able to: 

1) play their music
2) organize their music
3) **synchronize** their music
4) get them new music to play, organize, and synchronize

_Naturally, Ubuntu should provide them with the software capable to do this._

Now, Rhythmbox is a very nice piece of software. It does what it was designed to quickly, easily, and reliably. However, it was not written to accommodate the needs of current day users. 

Rhythmbox falls short in several areas 

1) synchronization
     a) able to copy files to device, will not mirror library to device
     b) purely plug in based (i believe, correct me if I'm wrong)
2) "get new music"
     a) does not have the high integration of last.fm found in amaroK, Banshee, etc
     b) lacks the integrated import/burn cd features found in Banshee, Itunes, etc
3) although stable, the project lacks the implementation of several new (in demand) features

For the previously mentioned reasons, I suggest that we re-think music management for Ubuntu. I'm not saying that we should simply rip out Rhythmbox, and slap in *(insert someones favorite media player)* I'm suggesting that something needs to be done. As I see it, we have the following options.

[B]1) improve Rhythmbox until it meeds/exceeds the needs of current users
2) replace Rhythmbox with a newer program developed with users current needs in mind
3) develop a new media player for Ubuntu (what Novell did with Banshee for Suse)
4) do nothing, ignore the situation, and loose users to bad first impressions[/B]

[I]---Other things to note---
music is very important especially to todays youth, getting todays youth to use linux means much more widespread adoption of linux in the future

there is **lots** of money in media players. Look at what Ipod/Itunes did for apple, and how much Microsoft is investing in Windows Media Player and Windows Media Center

it is important to remember that practically all of the software needed to overcome this problem has **already been written**, all we need to do is support and include it.

many users who care about the future of Ubuntu have enabled the "popularity contest" using this data, we can get a pretty good idea of how many people use Rhythmbox,  what other music players they use, what they use for their main music player, and how much people rely on music players in general. (where is this data!!!)

Linux is way behind on the media side, this must be changed. While Linux now has decent programs for **music** management and synchronization, Apple and Microsoft have this for **video**  also. Already, people are being forced to use windows to get video on their Ipods. Linux/Ubuntu has a LOT of catching up to do![/I][/SIZE]

---

### Post by smartboyathome on 2007-11-12
We can't include a way to get new music with Rythmbox because of how its liscensed. So cross that one off your list. :(

---

### Post by hyperair on 2007-11-13
Amarok's pretty feature complete, but that's for KDE. However, there's Exaile for GNOME and that's gaining ground rather rapidly though I wouldn't think it's stable enough to be the default. 

Rhythmbox is the best choice as the default music app in GNOME, for now, I reckon.

---

### Post by Turgon on 2007-11-13
Music devices and syncronization might in the future (maby hardy + 1) be handled by conduit. I have started a thread about this already:
[http://ubuntuforums.org/showthread.php?t=586839&highlight=conduit](http://ubuntuforums.org/showthread.php?t=586839&highlight=conduit)
 (I have written a spec too, but there is a more official one from the conduit/opensync guys).

Hope the devs can work this out soon, because it is really needed!

---

### Post by hyperair on 2007-11-13
That is rather fascinating. I like the idea of Conduit, although I'd hardly use it. One of the screenshots indicated downloading Youtube videos though. That could be handy feature.

---

### Post by Turgon on 2007-11-13
> **hyperair said:**
> That is rather fascinating. I like the idea of Conduit, although I'd hardly use it. One of the screenshots indicated downloading Youtube videos though. That could be handy feature.

Conduit won't be truly handy until it can sync with most pim/ multimedia devices and over the network (which isn't that far away). When it can do all that it might and should be included in gnome and be an essential part (it should handle all the syncing, instead of a one syncengine per app system (like toboy does now).

---

### Post by Mark C on 2007-11-13
Also make the media player play movie files! They are media too right?

---

### Post by meindian523 on 2007-11-13
> **smartboyathome said:**
> We can't include a way to get new music with Rythmbox because of how its liscensed. So cross that one off your list. :(

The OP is talking buying music,NOT piracy!amaroK includes the Magnatune store......I guess that can be implemented,eh??

---

### Post by Turgon on 2007-11-13
> **meindian523 said:**
> The OP is talking buying music,NOT piracy!amaroK includes the Magnatune store......I guess that can be implemented,eh??

Magnatune is included in rhythmbox as well (as a plugin).

---

### Post by Turgon on 2007-11-13
> **Mark C said:**
> Also make the media player play movie files! They are media too right?

The point of a music player is a player that manages music very well and adding video will clutter things. We already have a "good" app for video (totem) (and music).

---

### Post by hyperair on 2007-11-13
Yeah I use Totem for playing music too when it's just standalone files. There's of course the DragDropPlay screenlet which uses MPlayer. You should try that too =P

---

### Post by Siph0n on 2007-11-13
> **pengu said:**
> 
**4) do nothing, ignore the situation, and loose users to bad first impressions**


It's lose, not loose :)....

---

### Post by Perpetual on 2007-11-13
I am using Banshee with Ubuntu and it Syncs fine with my Ipod.  Only things I don't like about it are...

1.  You have to import the music folder every time you update it.  As far as I can tell it doesn't rescan the folder at startup.

2.  I do not like how it displays the collection, meaning there is no way to collapse the display so that it shows only the album rather than every song in the collection.

I am going to work with Exaile when I get some time to see if it works as well as Amarok.  Amarok has seemed to be the best although it does not sync.

---

### Post by Ub1476 on 2007-11-13
Get a music store in Rhythmbox!:popcorn:

---

### Post by Roger Mudd on 2007-11-13
> **Ub1476 said:**
> Get a music store in Rhythmbox!:popcorn:

That functionality is already there.

"Browse, preview, and download albums from Magnatune  and Jamendo"

[http://www.gnome.org/projects/rhythmbox/](http://www.gnome.org/projects/rhythmbox/)

---

### Post by meindian523 on 2007-11-13
One of the OP's grouses IS that Rhythmbox is all plugins!It should have been built-in in the OP's opinion(and mine too!)

---

### Post by CarpKing on 2007-11-13
What exactly is wrong with plugins?  They make adding new features a lot easier, especially for people who aren't the main developers of the program.

---

### Post by teasum on 2007-11-13
I would add my support to the general notion that music players need to be worked on and improved in Ubuntu.  I like aspects of Exaile and Rythmbox, but there is no one music player in Gnome that works seamlessly for me.  

For instance, I like the ability to display album art; however, in both Exaile and Rythmbox, I get the correct album art only some of the time, and more often, nothing comes up.  I would like a way to search and then 'pin' an image to a song or a collection of songs (i.e. an album).  I've tried this in Listen as well (another promising app). but the selections I make for the album art don't 'stick'.  

As for plugins, I have no problem with them, though the interface to install or select/deselect plugins could be made more upfront for newbies.  Also, I feel like there are a LOT of plugins between the music players available--perhaps a select few could be put up front as integral options, and others could be listed under an 'advanced' plugin mode?  For example, Jamendo and Magnatune, as well as Last.fm should be upfront, while LIRC or other tweaks might be more advanced.  Just a thought.

A final note of agreement would be Last.fm support.  I like last.fm, but I can't really use any of the audio players available in gnome to play last.fm stations.  Uploading of tracks works fine in all the players I have installed--Banshee, Listen, Exaile, and Rythmbox--but not a one works well to play the radio stations (it tends to stall and occasionally freeze the program).  Last.fm integration should be improved in Gnome music players.

That's my opinion.

---

### Post by meindian523 on 2007-11-14
Well,the "sticky" album art exists in Amarok.....plugins are ok for adding functionality when you aren't the main developer,but even the "main  developed" version of Rhythmbox which comes pre-packaged with Ubuntu is very "plugged-in",if I may use a term,not built-in.....

+1 for the separation of built-in features and "advanced" features...

---

### Post by tubasoldier on 2007-11-14
Perhaps as far as "getting more music" would be concerned, there could be a plugin for Jamendo made. It is all creative commons and downloadable freely anyways.

---

### Post by qamelian on 2007-11-14
> **tubasoldier said:**
> Perhaps as far as "getting more music" would be concerned, there could be a plugin for Jamendo made. It is all creative commons and downloadable freely anyways.

There already is. You just need to select it in the the list of plugins to activate.

---

### Post by teasum on 2007-11-14
> **qamelian said:**
> There already is. You just need to select it in the the list of plugins to activate.

Indeed.  And, on top of that, I have a ton of Jamendo music in my library because of this plugin!  I wish there was a way to automatically use the artwork provided by Jamendo as the album art in Rythmbox.  In general, I don't like the way Gnome music players handle Album Art--too many errors in the automatic searching, and once I manually search for the correct cover, the program 'forgets' it by the next startup.

There is another point that comes up in connection with Jamendo files, however.  There are text files included in every Jamendo download (license information, I believe), and I can't stand the way Rythmbox handles 'import errors'.  Perhaps there's an option somewhere to simply tell Rythmbox to ignore certain files?  If not, there should be.  For instance, I don't want to see import errors for .txt files, or, for instance, unplayable files left over form my pre-Ubuntu iTunes days.  

Just another suggestion.

---

### Post by Opticon on 2007-11-15
> **hyperair said:**
> Amarok's pretty feature complete, but that's for KDE. However, there's Exaile for GNOME and that's gaining ground rather rapidly though I wouldn't think it's stable enough to be the default. 

Rhythmbox is the best choice as the default music app in GNOME, for now, I reckon.

I think Amarok and Exaile are both good choices for music apps, but I also think Listen is going to be a better choice in the long run. Listen is currently in development stages, so its still fairly buggy. However, it does work with Last.fm and has features that search for lyrics and information about bands. I don't know if they've worked on syncing with ipods and stuff yet. For anyone interested they're site is:
[http://www.listen-project.org/wiki](http://www.listen-project.org/wiki)

---

### Post by meindian523 on 2007-11-15
+1 for Amarok.

---

### Post by Turgon on 2007-11-15
> **meindian523 said:**
> +1 for Amarok.

Amarok in its current form can never be the default music application og ubuntu (gnome) because it depends on some kde libs which both will clutter the system and take up more space on the cd. Amarok doesn't integrate well with gnome either.

---

### Post by bobbybobington on 2007-11-15
I think rhythmbox is an awesome app as far as its interface goes. One music store possibility that really needs to be looked at is the Amazon.com music store. I don't think it would be hard to do. I also agree that Cd burning is another must.

---

### Post by smartboyathome on 2007-11-15
> **bobbybobington said:**
> I think rhythmbox is an awesome app as far as its interface goes. One music store possibility that really needs to be looked at is the Amazon.com music store. I don't think it would be hard to do. I also agree that Cd burning is another must.

You can already burn CDs with Nautilus and Serpentine. What more is needed?

---

### Post by zombiepig on 2007-11-15
Actually you can burn cds in rhythmbox too - you just need to create a playlist of the tracks first, then in the playlist view there's a toolbar icon for 'create audio cd'. :)

---

### Post by CarpKing on 2007-11-16
> **zombiepig said:**
> Actually you can burn cds in rhythmbox too - you just need to create a playlist of the tracks first, then in the playlist view there's a toolbar icon for 'create audio cd'. :)

A lot of people who don't like Rhythmbox seem to assume that it lacks a great deal of functionality that it actually does have.  That's not to say this functionality couldn't be mad easier to discover, though.

---

### Post by meindian523 on 2007-11-16
> **Turgon said:**
> Amarok in its current form can never be the default music application og ubuntu (gnome) because it depends on some kde libs which both will clutter the system and take up more space on the cd. Amarok doesn't integrate well with gnome either.

True,but if you look at the popularity ratings,that doesn't prevent a lot many people from installing it.....if it's not default,atleast it can be set as an example for whatever the default player is decided to be.....

---

### Post by qamelian on 2007-11-16
> **CarpKing said:**
> A lot of people who don't like Rhythmbox seem to assume that it lacks a great deal of functionality that it actually does have.  That's not to say this functionality couldn't be mad easier to discover, though.

Agreed. Although I wasn't a big fan of Rhythmbox originally, it has certainly come along way. It has finally reached the point where I'm not even tempted to search out replacements / substitutes for it any more. The only thing I can think of that I would still like to see improved is the speed at which it rebuilds large collections. Other than than it more than meets my needs as a player / organizer / interface to both my iPod and my Zen.

---

### Post by tretle on 2007-11-16
I think the rhythmbox developers should be given alot more love in this thread... So far its just people complaining about features which are there already... Rhythmbox development was a bit quiet for awhile but for the last year they have gotten a huge amount of things done.. Lyric support is there, lastfm support is there, theres support for two music stores, they added visualizations, They restructured the code to improve performance... Numerous bug fixes... Rhythmbox in my view performs much better than banshee atm.. 

What I think needs to be done is have the website restructured... The Screenshots section has not been updated in a long time, Rhythmbox looks a hell of allot nicer now so people that are looking for a linux music player should know this as it is important even though its just aesthetics. Rhythmbox has finally reached the stage where it runs very well and they can concentrate on new features.. More stores being supported would be nice but I didn't see anyone mention features which would actually be useful which are missing like support for embedding album art into the .mp3/.ogg file instead of adding the album art to the corresponding folder. 

To be honest I haven't looked up much on rhythmbox's development in ages now but this was always a big issue for me because most music orientated features of consumer electronics these days that display album art get the album art which is embedded into the music file itself, had a debate on it in #rhythmbox some months ago and was told that the current method is much nicer and its how things should be done... Cant say I completely agree with this statement as I doubt Sony Ericsson will start using a different method to grab album art or the ps3 also. It annoys me sometimes that apple continues to be supported no matter what but when you ask for other standardized features which may be used along a whole host of different electronic devices you get told where to jump.

Back on the good things about Rhythmbox, I have some bare knowledge on developing appz, in c, c++ and now doing java at college.. It is in my opinion that the rhythmbox developers have made the right choice when it comes to plugins... developing new features through plugins helps keep the code for rhythmbox neat and tidy so that future bug fixing and restructuring of the code will be much easier... This means that you the user will have a better app, one that's growing in features and growing in terms of performance ever day.

As for device support, I once had the same complaints as you.. but device support has little to do with rhythmbox itself.. Its using HAL or the linux hardware abstraction layer to support devices... If hal supports it then rhythmbox will.. Why have the rhythmbox team worry about device support when there has been a dedicated way of supporting devices for years with lots of very cool people trying as hard as they can to support the devices you have. And if you have a problem then you can submit the information of your device to the hal team and they can then go about supporting it... You have to understand that they dot own every device known to man... they are normal guys like you and me, they need the information that your device sends to your computer to begin with.... From what i can remember you can get this by using the lsusb command into the terminal....

Now saying that I think the website definitely needs to be updated to reflect this, make it easier for people to send their device info to the hal team if there device isn't supported.. 

I also had a conversation on this before and was told that epople can go to the hal site to do that, but if you common users to be able to use use app well then you need to make it easy for them, its not like they know what hal is or want to know what it is. And they sure as hell shouldn't have to.. 

You could track the amount of people that are trying to get a device working so it would help the hal guys prioritize there work.
And why have rhythmbox play video, this would bloat it up, why dont you go to try and get more features in totem like a video library, dvd cover grabber, subtitle grabber, movie/tvshow info grabber.

So in my honest opinion, rhythmbox shouldn't be replaced as default music player, hell its only really getting good now that development has sparked up again.

---

### Post by pengu on 2007-11-17
> Also make the media player play movie files! They are media too right?

yes, as noted at the bottom of my post, although we can play movie files we have no app to organize them!

look at windows media player. allright, i know we all hate windows, but they have actually done a decent job here... Windows users can organize **and sync** all their media files [music and video]. The same goes for apple users.

---

### Post by tretle on 2007-11-17
its not a media player.... rhythmbox music player.... totem movie player.... maybe you should just as for a better video player... having one app to play and organizev music and movies is bloated and decreases performance... theres no reason why we cant surpass windows media player but the thing we should be looking at is totem not rhythmbox... rhythmbox works great for music management... now lets do the same for totem.... having a library plugin would be nice... with dcd covers pulled from imdb... maybe the ability to seperate your media into categories, movies + tvshows then subcatagories, documenteries, comedy, series, year, actors.

---

### Post by pengu on 2007-11-18
i never said it had to be one progam, I also said nothing about rhythmbox...

i dont know where your getting this from, but remember this thread is about music management so lets try to keep on track

Im kinda new to the ubuntu "community" so if anyone could tell me the best way to get this spec heard by the devs id really appreciate it.. Thanks

---

### Post by tretle on 2007-11-19
> **pengu said:**
> yes, as noted at the bottom of my post, although we can play movie files we have no app to organize them!

look at windows media player. allright, i know we all hate windows, but they have actually done a decent job here... Windows users can organize **and sync** all their media files [music and video]. The same goes for apple users.

music player - music
media player - video+music

windows media player - music, photos and video.
You compared the current situation to windows MEDIA player. Which is a bloated piece of crap. So thats where I came to the conclusion that you meant one app does all. So before you post a reply at least read your previous post and try to figure out where someone could have came to the conclusion in the first place.

---

### Post by hyperair on 2007-11-19
Now, now, tretle, I believe this thread was meant for discussion, not for heated debate and bitter, spiteful posts.

@Pengu: I believe what tretle said is right. Totem is a media player (even if it calls itself a movie player), but Rhythmbox is just a music player. If Totem could exapnd its capabilities to something which can organize the files, I think that would be great. Like tretle said, a library plugin.

---

### Post by meindian523 on 2007-11-21
dead thread??

---

